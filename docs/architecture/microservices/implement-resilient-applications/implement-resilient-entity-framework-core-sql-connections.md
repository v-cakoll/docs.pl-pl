---
title: Zaimplementuj odporne Entity Framework Core połączenia SQL
description: Dowiedz się, jak zaimplementować odporne Entity Framework Core połączenia SQL. Ta technika jest szczególnie ważna w przypadku korzystania z Azure SQL Database w chmurze.
ms.date: 10/16/2018
ms.openlocfilehash: 3bf5c1827cee1da69aeccdc9f15573c301fc9363
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296070"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Zaimplementuj odporne Entity Framework Core połączenia SQL

W przypadku usługi Azure SQL DB Entity Framework (EF) Core udostępnia już wewnętrzną odporność połączenia z bazą danych i logikę ponowień. Należy jednak włączyć strategię wykonywania Entity Framework dla każdego <xref:Microsoft.EntityFrameworkCore.DbContext> połączenia, jeśli chcesz mieć [odporne EF Core połączenia](/ef/core/miscellaneous/connection-resiliency).

Na przykład poniższy kod na poziomie połączenia EF Core włącza odporne połączenia SQL, które są ponawiane, jeśli połączenie nie powiedzie się.

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie wykonywania i jawne transakcje przy użyciu BeginTransaction i wielu dbcontexts

Po włączeniu ponownych prób w EF Core połączeniach każda operacja wykonywana przy użyciu EF Core będzie własną operacją wywołały. Każde zapytanie i każde wywołanie `SaveChanges` zostanie ponowione w przypadku wystąpienia błędu przejściowego.

Jeśli jednak kod inicjuje transakcję przy użyciu `BeginTransaction`, definiujesz własną grupę operacji, która musi być traktowana jako jednostka. Jeśli wystąpi awaria, wszystkie elementy wewnątrz transakcji należy wycofać.

Jeśli spróbujesz wykonać tę transakcję w przypadku korzystania z strategii wykonywania EF (zasady ponawiania) i `SaveChanges` wywołaniu wielu dbcontexts, uzyskasz wyjątek podobny do tego:

> System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika. Użyj strategii wykonywania zwróconej przez obiekt "DbContext. Database. CreateExecutionStrategy ()", aby wykonać wszystkie operacje w transakcji jako jednostkę wywołały.

Rozwiązaniem jest ręczne Wywołaj strategię wykonywania EF z delegatem reprezentującym wszystkie elementy, które należy wykonać. Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła ponownie delegata. Na przykład poniższy kod pokazuje, w jaki sposób jest zaimplementowany w eShopOnContainers z dwoma wieloma atrybutami DbContext\_(catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania Obiekt ProductPriceChangedIntegrationEvent, który musi używać innego kontekstu DbContext.

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

Pierwszy <xref:Microsoft.EntityFrameworkCore.DbContext> to `_catalogContext` , a drugi `DbContext` znajduje się w `_integrationEventLogService` obiekcie. Akcja zatwierdzania jest wykonywana dla wszystkich `DbContext` obiektów przy użyciu strategii wykonywania EF.

Aby osiągnąć tę wiele `DbContext` zatwierdzeń `SaveEventAndCatalogContextChangesAsync` , używa `ResilientTransaction` klasy, jak pokazano w poniższym kodzie:

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

`_catalogContext` `DbContext` `IntegrationEventLogContext` `EventLogService` Metoda zasadniczo rozpoczyna transakcję z przekazaną (), a następnie wykonuje tę transakcję, aby zapisać zmiany z i następnie zatwierdzić całą transakcję. `ResilientTransaction.ExecuteAsync`

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

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Odporność połączeń i przechwycenie poleceń z EF w aplikacji ASP.NET MVC** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de La Torre. Korzystanie z odpornych Entity Framework Core połączeń i transakcji SQL** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Poprzedni](implement-retries-exponential-backoff.md)Następny
>[](explore-custom-http-call-retries-exponential-backoff.md)
