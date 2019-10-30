---
title: Zaimplementuj odporne Entity Framework Core połączenia SQL
description: Dowiedz się, jak zaimplementować odporne Entity Framework Core połączenia SQL. Ta technika jest szczególnie ważna w przypadku korzystania z Azure SQL Database w chmurze.
ms.date: 10/16/2018
ms.openlocfilehash: 3128cf1be7f2dc8804a002556db232f4e0fc8c33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094051"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="aaf50-104">Zaimplementuj odporne Entity Framework Core połączenia SQL</span><span class="sxs-lookup"><span data-stu-id="aaf50-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="aaf50-105">W przypadku usługi Azure SQL DB Entity Framework (EF) Core udostępnia już wewnętrzną odporność połączenia z bazą danych i logikę ponowień.</span><span class="sxs-lookup"><span data-stu-id="aaf50-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="aaf50-106">Należy jednak włączyć strategię wykonywania Entity Framework dla każdego połączenia <xref:Microsoft.EntityFrameworkCore.DbContext>, jeśli chcesz mieć [odporne EF Core połączenia](/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="aaf50-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="aaf50-107">Na przykład poniższy kod na poziomie połączenia EF Core włącza odporne połączenia SQL, które są ponawiane, jeśli połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="aaf50-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="aaf50-108">Strategie wykonywania i jawne transakcje przy użyciu BeginTransaction i wielu dbcontexts</span><span class="sxs-lookup"><span data-stu-id="aaf50-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="aaf50-109">Po włączeniu ponownych prób w EF Core połączeniach każda operacja wykonywana przy użyciu EF Core będzie własną operacją wywołały.</span><span class="sxs-lookup"><span data-stu-id="aaf50-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="aaf50-110">Każde zapytanie i każde wywołanie `SaveChanges` zostanie ponowione w przypadku wystąpienia błędu przejściowego.</span><span class="sxs-lookup"><span data-stu-id="aaf50-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="aaf50-111">Jeśli jednak kod inicjuje transakcję przy użyciu `BeginTransaction`, definiujesz własną grupę operacji, która musi być traktowana jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="aaf50-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="aaf50-112">Jeśli wystąpi awaria, wszystkie elementy wewnątrz transakcji należy wycofać.</span><span class="sxs-lookup"><span data-stu-id="aaf50-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="aaf50-113">Jeśli spróbujesz wykonać tę transakcję przy użyciu strategii wykonywania EF (zasady ponawiania) i wywołajesz `SaveChanges` z wielu kontekstów DbContext, uzyskasz wyjątek podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="aaf50-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="aaf50-114">System. InvalidOperationException: skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="aaf50-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="aaf50-115">Użyj strategii wykonywania zwróconej przez obiekt "DbContext. Database. CreateExecutionStrategy ()", aby wykonać wszystkie operacje w transakcji jako jednostkę wywołały.</span><span class="sxs-lookup"><span data-stu-id="aaf50-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="aaf50-116">Rozwiązaniem jest ręczne Wywołaj strategię wykonywania EF z delegatem reprezentującym wszystkie elementy, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="aaf50-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="aaf50-117">Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła ponownie delegata.</span><span class="sxs-lookup"><span data-stu-id="aaf50-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="aaf50-118">Na przykład poniższy kod pokazuje, w jaki sposób jest zaimplementowany w eShopOnContainers z dwoma wieloma atrybutami DbContext (\_catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania ProductPriceChangedIntegrationEvent Obiekt, który musi używać innego kontekstu DbContext.</span><span class="sxs-lookup"><span data-stu-id="aaf50-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="aaf50-119">Pierwszy <xref:Microsoft.EntityFrameworkCore.DbContext> jest `_catalogContext`, a drugi `DbContext` znajduje się w obrębie obiektu `_integrationEventLogService`.</span><span class="sxs-lookup"><span data-stu-id="aaf50-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_integrationEventLogService` object.</span></span> <span data-ttu-id="aaf50-120">Akcja zatwierdzania jest wykonywana dla wszystkich `DbContext` obiektów przy użyciu strategii wykonywania EF.</span><span class="sxs-lookup"><span data-stu-id="aaf50-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="aaf50-121">Aby osiągnąć tę wiele `DbContext` zatwierdzenia, `SaveEventAndCatalogContextChangesAsync` używa klasy `ResilientTransaction`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="aaf50-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

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

<span data-ttu-id="aaf50-122">Metoda `ResilientTransaction.ExecuteAsync` zasadniczo rozpoczyna transakcję od zakończono `DbContext` (`_catalogContext`), a następnie `EventLogService` używa tej transakcji do zapisywania zmian z `IntegrationEventLogContext`, a następnie zatwierdza całą transakcję.</span><span class="sxs-lookup"><span data-stu-id="aaf50-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="aaf50-123">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="aaf50-123">Additional resources</span></span>

- <span data-ttu-id="aaf50-124">**Odporność połączeń i przechwycenie poleceń z EF w aplikacji ASP.NET MVC** </span><span class="sxs-lookup"><span data-stu-id="aaf50-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** </span></span>\
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="aaf50-125">**Cesar de La Torre. Korzystanie z odpornych Entity Framework Core połączeń i transakcji SQL** </span><span class="sxs-lookup"><span data-stu-id="aaf50-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
><span data-ttu-id="aaf50-126">[Poprzedni](implement-retries-exponential-backoff.md)
>[Następny](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="aaf50-126">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>
