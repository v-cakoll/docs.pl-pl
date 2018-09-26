---
title: Implementowanie odpornych na błędy połączeń Entity Framework Core SQL
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie odpornych na błędy połączeń Entity Framework Core SQL. Ta technika jest szczególnie ważne w przypadku korzystania z usługi Azure SQL Database w chmurze.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 59db9cdb894f76f54e77732be47dc6140a594121
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231417"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="05f3a-104">Implementowanie odpornych na błędy połączeń Entity Framework Core SQL</span><span class="sxs-lookup"><span data-stu-id="05f3a-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="05f3a-105">Dla bazy danych SQL Azure platformy Entity Framework Core już zawiera logikę ponawiania prób i odporności połączenia wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="05f3a-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="05f3a-106">Jednak należy włączyć strategii wykonywania programu Entity Framework, dla każdego typu DbContext połączenia, jeśli chcesz mieć [odporne na błędy połączeń z programem EF Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="05f3a-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="05f3a-107">Na przykład następujący kod na poziomie połączenia platformy EF Core umożliwia odporne na błędy połączeń SQL, które są zwalniane, jeśli połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="05f3a-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="05f3a-108">Strategii wykonywania i jawnego transakcji za pomocą BeginTransaction i wiele DbContexts</span><span class="sxs-lookup"><span data-stu-id="05f3a-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="05f3a-109">Po włączeniu ponownych prób w połączeniach programu EF Core każdej operacji, które możesz wykonać przy użyciu programu EF Core staje się własną umożliwiający ponowienie próby operacji.</span><span class="sxs-lookup"><span data-stu-id="05f3a-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="05f3a-110">Jeśli wystąpi błąd przejściowy, każde zapytanie i każde wywołanie funkcji SaveChanges zostanie ponowiona jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="05f3a-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="05f3a-111">Jednak jeśli Twój kod inicjuje transakcji za pomocą BeginTransaction, definiujesz własną grupę działań, które muszą być traktowane jako jednostka — wszystko wewnątrz transakcja została wycofana, ponownie, jeśli wystąpi awaria.</span><span class="sxs-lookup"><span data-stu-id="05f3a-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="05f3a-112">Jeśli próba wykonania tej transakcji, korzystając z programów EF strategii wykonywania (zasady ponawiania) i obejmują kilka wywołań funkcji SaveChanges z wielu DbContexts w transakcji, zostanie wyświetlone wyjątek, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="05f3a-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="05f3a-113">System.InvalidOperationException: Strategia wykonywania skonfigurowany "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji zainicjowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="05f3a-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="05f3a-114">Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostka z możliwością ponowienia próby.</span><span class="sxs-lookup"><span data-stu-id="05f3a-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="05f3a-115">To rozwiązanie jest ręcznie wywołać strategii wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="05f3a-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="05f3a-116">Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła delegata ponownie.</span><span class="sxs-lookup"><span data-stu-id="05f3a-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="05f3a-117">Na przykład, poniższy kod pokazują, jak jest zaimplementowane w ramach aplikacji eShopOnContainers przy użyciu dwóch wielu DbContexts (\_catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania Obiekt ProductPriceChangedIntegrationEvent musi używać innego typu DbContext.</span><span class="sxs-lookup"><span data-stu-id="05f3a-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="05f3a-118">Jest pierwszym DbContext \_catalogContext, a druga DbContext mieści się w \_integrationEventLogService obiektu.</span><span class="sxs-lookup"><span data-stu-id="05f3a-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="05f3a-119">Akcja zatwierdzenia odbywa się w wielu DbContexts za pomocą strategii wykonywania EF.</span><span class="sxs-lookup"><span data-stu-id="05f3a-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="05f3a-120">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="05f3a-120">Additional resources</span></span>

-   <span data-ttu-id="05f3a-121">**Połączenia platformy EF** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="05f3a-121">**EF Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="05f3a-122">**Elastyczność połączeń i przejmowanie poleceń za pomocą programu Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="05f3a-122">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="05f3a-123">**Torre'a de la Cesarowi. Za pomocą odporne na błędy Entity Framework Core połączeń z serwerem Sql i transakcji**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="05f3a-123">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="05f3a-124">[Poprzednie](implement-retries-exponential-backoff.md)
[dalej](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="05f3a-124">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>
