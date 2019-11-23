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
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Zaimplementuj odporne Entity Framework Core połączenia SQL

W przypadku usługi Azure SQL DB Entity Framework (EF) Core udostępnia już wewnętrzną odporność połączenia z bazą danych i logikę ponowień. Należy jednak włączyć strategię wykonywania Entity Framework dla każdego połączenia <xref:Microsoft.EntityFrameworkCore.DbContext>, jeśli chcesz mieć [odporne EF Core połączenia](/ef/core/miscellaneous/connection-resiliency).

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

Jeśli spróbujesz wykonać tę transakcję przy użyciu strategii wykonywania EF (zasady ponawiania) i wywołajesz `SaveChanges` z wielu kontekstów DbContext, uzyskasz wyjątek podobny do tego:

> System. InvalidOperationException: skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika. Użyj strategii wykonywania zwróconej przez obiekt "DbContext. Database. CreateExecutionStrategy ()", aby wykonać wszystkie operacje w transakcji jako jednostkę wywołały.

Rozwiązaniem jest ręczne Wywołaj strategię wykonywania EF z delegatem reprezentującym wszystkie elementy, które należy wykonać. Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła ponownie delegata. Na przykład poniższy kod pokazuje, w jaki sposób jest implementowany w eShopOnContainers przy użyciu dwóch wielu dbcontexts (\_catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania obiektu ProductPriceChangedIntegrationEvent, który musi korzystać z innego DbContext.

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

Pierwszy <xref:Microsoft.EntityFrameworkCore.DbContext> jest `_catalogContext`, a drugi `DbContext` znajduje się w obrębie obiektu `_integrationEventLogService`. Akcja zatwierdzania jest wykonywana dla wszystkich `DbContext` obiektów przy użyciu strategii wykonywania EF.

Aby osiągnąć tę wiele `DbContext` zatwierdzenia, `SaveEventAndCatalogContextChangesAsync` używa klasy `ResilientTransaction`, jak pokazano w poniższym kodzie:

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

Metoda `ResilientTransaction.ExecuteAsync` zasadniczo rozpoczyna transakcję od zakończono `DbContext` (`_catalogContext`), a następnie `EventLogService` używa tej transakcji do zapisywania zmian z `IntegrationEventLogContext`, a następnie zatwierdza całą transakcję.

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
>[Poprzedni](implement-retries-exponential-backoff.md)
>[Następny](explore-custom-http-call-retries-exponential-backoff.md)
