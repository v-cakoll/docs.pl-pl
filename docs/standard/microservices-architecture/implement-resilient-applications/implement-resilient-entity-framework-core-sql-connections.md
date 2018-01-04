---
title: "Implementowanie odporność połączeń Entity Framework Core SQL"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie odporność połączeń Entity Framework Core SQL"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b37d2c5683aff44165d0330c8d42fc881effbb76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="cf2bf-104">Implementowanie odporność połączeń Entity Framework Core SQL</span><span class="sxs-lookup"><span data-stu-id="cf2bf-104">Implementing resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="cf2bf-105">Dla bazy danych SQL Azure programu Entity Framework Core zawiera już logiki odporności i ponów próbę połączenia wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="cf2bf-106">Jednak należy włączyć strategia wykonywania programu Entity Framework dla każdego połączenia DbContext, jeśli chcesz, aby [odporność połączeń EF Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="cf2bf-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="cf2bf-107">Na przykład następujący kod na poziomie połączenia EF Core umożliwia elastyczne połączeń z serwerem SQL, które są zwalniane, jeśli połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 5,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="cf2bf-108">Strategie wykonywania i jawnych transakcji przy użyciu BeginTransaction i wielu DbContexts</span><span class="sxs-lookup"><span data-stu-id="cf2bf-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="cf2bf-109">Po włączeniu ponownych prób w połączeniach EF Core każdej operacji wykonywanych przy użyciu EF Core staje się działania można spróbować ponownie.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="cf2bf-110">Jeśli wystąpi błąd przejściowy, każdego zapytania i każde wywołanie metody SaveChanges zostanie ponowiona jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="cf2bf-111">Jednak jeśli kod inicjuje transakcji za pomocą BeginTransaction, definiowania grupy działań, które muszą być traktowane jako jednostka — wszystkie elementy wewnątrz transakcji została wycofana, jeśli wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="cf2bf-112">Jeśli próba wykonania tej transakcji, używając strategii wykonywania EF (zasady ponawiania) i obejmują kilka wywołania metody SaveChanges z wielu DbContexts w transakcji, zostanie wyświetlony następujący wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="cf2bf-113">System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="cf2bf-114">Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostki można spróbować ponownie.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="cf2bf-115">Rozwiązanie to ręczne wywoływanie strategia wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="cf2bf-116">Jeśli wystąpi błąd przejściowy, strategia wykonywania zostaną wywołane delegat ponownie.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="cf2bf-117">Na przykład następujący kod pokazać, jak jest implementowane w eShopOnContainers przy użyciu dwóch wielu DbContexts (\_catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania Obiekt ProductPriceChangedIntegrationEvent musi używać innego typu DbContext.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

<span data-ttu-id="cf2bf-118">Jest first DbContext \_catalogContext, a drugi DbContext znajduje się w \_integrationEventLogService obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="cf2bf-119">Akcja zatwierdzenia jest wykonywane przez wiele DbContexts przy użyciu EF strategia wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cf2bf-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cf2bf-120">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="cf2bf-120">Additional resources</span></span>

-   <span data-ttu-id="cf2bf-121">**Elastyczność połączenia i przechwytywaniu polecenia Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="cf2bf-121">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="cf2bf-122">**Torre de la Cesarowi. Za pomocą połączeń z serwerem Sql Core Framework jednostki odporne i transakcji**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="cf2bf-122">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="cf2bf-123">[Poprzednie] (wdrożenie-ponownych prób wykładniczej backoff.md) [dalej] (implement-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="cf2bf-123">[Previous] (implement-retries-exponential-backoff.md) [Next] (implement-custom-http-call-retries-exponential-backoff.md)</span></span>
