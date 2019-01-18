---
title: Implementowanie odpornych na błędy połączeń Entity Framework Core SQL
description: Dowiedz się, jak zaimplementować odporne na błędy połączeń Entity Framework Core SQL. Ta technika jest szczególnie ważne w przypadku korzystania z usługi Azure SQL Database w chmurze.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 28428654ea3176aea960e2711c83499a16d2dd4b
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362681"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="73485-104">Implementowanie odpornych na błędy połączeń Entity Framework Core SQL</span><span class="sxs-lookup"><span data-stu-id="73485-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="73485-105">Dla bazy danych SQL Azure Core Entity Framework (EF) już zawiera logikę ponawiania prób i odporności połączenia wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="73485-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="73485-106">Jednak należy włączyć strategii wykonywania programu Entity Framework, dla każdego <xref:Microsoft.EntityFrameworkCore.DbContext> połączenie, jeśli chcesz mieć [odporne na błędy połączeń z programem EF Core](/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="73485-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="73485-107">Na przykład następujący kod na poziomie połączenia platformy EF Core umożliwia odporne na błędy połączeń SQL, które są zwalniane, jeśli połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="73485-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="73485-108">Strategii wykonywania i jawnego transakcji za pomocą BeginTransaction i wiele DbContexts</span><span class="sxs-lookup"><span data-stu-id="73485-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="73485-109">Po włączeniu ponownych prób w połączeniach programu EF Core każdej operacji, które możesz wykonać przy użyciu programu EF Core staje się własną wywołały operacji.</span><span class="sxs-lookup"><span data-stu-id="73485-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="73485-110">Każde zapytanie i każde wywołanie `SaveChanges` zostanie ponowiona jako jednostki, jeśli wystąpi błąd przejściowy.</span><span class="sxs-lookup"><span data-stu-id="73485-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="73485-111">Jednak jeśli Twój kod inicjuje transakcji przy użyciu `BeginTransaction`, które definiujesz własną grupę działań, które muszą być traktowane jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="73485-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="73485-112">Wszystko wewnątrz transakcji musi zostać wycofana ponownie, jeśli wystąpi awaria.</span><span class="sxs-lookup"><span data-stu-id="73485-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="73485-113">Jeśli przy próbie wykonania danej transakcji, gdy za pomocą strategii wykonywania EF (zasady ponawiania), należy wywołać `SaveChanges` z wielu DbContexts otrzymasz wyjątek podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="73485-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="73485-114">System.InvalidOperationException: Strategia wykonywania skonfigurowany "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji zainicjowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="73485-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="73485-115">Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostka z możliwością ponowienia próby.</span><span class="sxs-lookup"><span data-stu-id="73485-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="73485-116">To rozwiązanie jest ręcznie wywołać strategii wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="73485-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="73485-117">Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła delegata ponownie.</span><span class="sxs-lookup"><span data-stu-id="73485-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="73485-118">Na przykład, poniższy kod pokazują, jak go została zaimplementowana w ramach aplikacji eShopOnContainers przy użyciu dwóch wielu DbContexts (\_catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania Obiekt ProductPriceChangedIntegrationEvent musi używać innego typu DbContext.</span><span class="sxs-lookup"><span data-stu-id="73485-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

<span data-ttu-id="73485-119">Pierwszy <xref:Microsoft.EntityFrameworkCore.DbContext> jest `_catalogContext` , a druga `DbContext` znajduje się w `_integrationEventLogService` obiektu.</span><span class="sxs-lookup"><span data-stu-id="73485-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_integrationEventLogService` object.</span></span> <span data-ttu-id="73485-120">Akcja zatwierdzenia jest wykonywana we wszystkich `DbContext` obiektów za pomocą strategii wykonywania EF.</span><span class="sxs-lookup"><span data-stu-id="73485-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="73485-121">Aby osiągnąć ten wielu `DbContext` zatwierdzenia `SaveEventAndCatalogContextChangesAsync` używa `ResilientTransaction` klasy, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="73485-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database 
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

<span data-ttu-id="73485-122">`ResilientTransaction.ExecuteAsync` Metoda po prostu rozpoczyna transakcji z przekazanych `DbContext` (`_catalogContext`), a następnie udostępnia `EventLogService` użyć danej transakcji, aby zapisać zmiany w porównaniu z `IntegrationEventLogContext` i zatwierdzenia, cała transakcja.</span><span class="sxs-lookup"><span data-stu-id="73485-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts 
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            using (var transaction = _context.Database.BeginTransaction())
            {
                await action();
                transaction.Commit();
            }
        });
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="73485-123">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="73485-123">Additional resources</span></span>

- <span data-ttu-id="73485-124">**Elastyczność połączeń i przejmowanie poleceń przy użyciu programu EF w aplikacji ASP.NET MVC** \\</span><span class="sxs-lookup"><span data-stu-id="73485-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** \\</span></span>
  [*https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application*](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="73485-125">**Torre'a de la Cesarowi. Za pomocą odporne na błędy Entity Framework Core połączeń z serwerem SQL i transakcji** \\</span><span class="sxs-lookup"><span data-stu-id="73485-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** \\</span></span>
  [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/)

>[!div class="step-by-step"]
><span data-ttu-id="73485-126">[Poprzednie](implement-retries-exponential-backoff.md)
>[dalej](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="73485-126">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>