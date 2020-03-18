---
title: Implementowanie połączeń core SQL platformy odpornej jednostki
description: Dowiedz się, jak zaimplementować połączenia SQL platformy core platformy odporna. Ta technika jest szczególnie ważne podczas korzystania z usługi Azure SQL Database w chmurze.
ms.date: 10/16/2018
ms.openlocfilehash: 7a047edca21d63a451e90f407b23f3358d461330
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78241068"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementowanie połączeń core SQL platformy odpornej jednostki

W przypadku usługi Azure SQL DB, entity framework (EF) Core już zapewnia odporność połączenia wewnętrznej bazy danych i logikę ponawiania próby. Należy jednak włączyć strategię wykonywania <xref:Microsoft.EntityFrameworkCore.DbContext> struktury jednostek dla każdego połączenia, jeśli chcesz mieć [odporne połączenia EF Core](/ef/core/miscellaneous/connection-resiliency).

Na przykład następujący kod na poziomie połączenia EF Core umożliwia odporne połączenia SQL, które są ponowione w przypadku niepowodzenia połączenia.

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie realizacji i jawne transakcje przy użyciu BeginTransaction i wielu DbContexts

Po włączeniu ponownych prób w połączeniach EF Core każda operacja wykonywana przy użyciu EF Core staje się własną operacją ponawiania prób. Każde zapytanie i `SaveChanges` każde wywołanie zostanie ponowione jako jednostka, jeśli wystąpi błąd przejściowy.

Jeśli jednak kod inicjuje `BeginTransaction`transakcję przy użyciu , definiujesz własną grupę operacji, które muszą być traktowane jako jednostka. Wszystko wewnątrz transakcji musi zostać wycofana w przypadku wystąpienia awarii.

Jeśli spróbujesz wykonać tę transakcję podczas korzystania ze strategii `SaveChanges` wykonywania EF (zasady ponawiania próby) i wywołać z wielu DbContexts, otrzymasz wyjątek, taki jak ten:

> System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika. Użyj strategii wykonywania zwracanej przez "DbContext.Database.CreateExecutionStrategy()", aby wykonać wszystkie operacje w transakcji jako jednostkę podlegającą zwrotowi.

Rozwiązaniem jest ręczne wywołanie strategii wykonywania EF z delegata reprezentujących wszystko, co musi zostać wykonane. Jeśli wystąpi błąd przejściowy, strategia wykonywania ponownie wywoła delegata. Na przykład poniższy kod pokazuje, jak jest zaimplementowany w eShopOnContainers\_z dwoma wieloma DbContexts (catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania ProductPriceChangedIntegrationEvent obiektu, który musi używać innego DbContext.

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

Pierwszy <xref:Microsoft.EntityFrameworkCore.DbContext> `_catalogContext` jest, a `DbContext` drugi `_catalogIntegrationEventService` znajduje się w obiekcie. Akcja zatwierdzania jest wykonywana we wszystkich `DbContext` obiektach przy użyciu strategii wykonywania EF.

Aby osiągnąć `DbContext` to zatwierdzenie `SaveEventAndCatalogContextChangesAsync` wielokrotności, używa `ResilientTransaction` klasy, jak pokazano w następującym kodzie:

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

Metoda `ResilientTransaction.ExecuteAsync` zasadniczo rozpoczyna transakcję z `DbContext` przekazany`_catalogContext`( ), `EventLogService` a następnie sprawia, że `IntegrationEventLogContext` użycie tej transakcji, aby zapisać zmiany z, a następnie zatwierdza całą transakcję.

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

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Odporność połączeń i przechwytywanie poleceń za pomocą EF w ASP.NET aplikacji MVC** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre. Korzystanie z platformy stabilnej jednostki Core SQL połączenia i transakcje** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Poprzedni](implement-retries-exponential-backoff.md)
>[następny](use-httpclientfactory-to-implement-resilient-http-requests.md)
