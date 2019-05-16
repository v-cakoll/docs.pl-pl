---
title: Implementowanie odpornych na błędy połączeń Entity Framework Core SQL
description: Dowiedz się, jak zaimplementować odporne na błędy połączeń Entity Framework Core SQL. Ta technika jest szczególnie ważne w przypadku korzystania z usługi Azure SQL Database w chmurze.
ms.date: 10/16/2018
ms.openlocfilehash: 3bf5c1827cee1da69aeccdc9f15573c301fc9363
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639896"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementowanie odpornych na błędy połączeń Entity Framework Core SQL

Dla bazy danych SQL Azure Core Entity Framework (EF) już zawiera logikę ponawiania prób i odporności połączenia wewnętrznej bazy danych. Jednak należy włączyć strategii wykonywania programu Entity Framework, dla każdego <xref:Microsoft.EntityFrameworkCore.DbContext> połączenie, jeśli chcesz mieć [odporne na błędy połączeń z programem EF Core](/ef/core/miscellaneous/connection-resiliency).

Na przykład następujący kod na poziomie połączenia platformy EF Core umożliwia odporne na błędy połączeń SQL, które są zwalniane, jeśli połączenie nie powiedzie się.

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategii wykonywania i jawnego transakcji za pomocą BeginTransaction i wiele DbContexts

Po włączeniu ponownych prób w połączeniach programu EF Core każdej operacji, które możesz wykonać przy użyciu programu EF Core staje się własną wywołały operacji. Każde zapytanie i każde wywołanie `SaveChanges` zostanie ponowiona jako jednostki, jeśli wystąpi błąd przejściowy.

Jednak jeśli Twój kod inicjuje transakcji przy użyciu `BeginTransaction`, które definiujesz własną grupę działań, które muszą być traktowane jako jednostka. Wszystko wewnątrz transakcji musi zostać wycofana ponownie, jeśli wystąpi awaria.

Jeśli przy próbie wykonania danej transakcji, gdy za pomocą strategii wykonywania EF (zasady ponawiania), należy wywołać `SaveChanges` z wielu DbContexts otrzymasz wyjątek podobny do poniższego:

> System.InvalidOperationException: Strategia wykonywania skonfigurowany "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji zainicjowanej przez użytkownika. Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostka z możliwością ponowienia próby.

To rozwiązanie jest ręcznie wywołać strategii wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana. Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła delegata ponownie. Na przykład, poniższy kod pokazują, jak go została zaimplementowana w ramach aplikacji eShopOnContainers przy użyciu dwóch wielu DbContexts (\_catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania Obiekt ProductPriceChangedIntegrationEvent musi używać innego typu DbContext.

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

Pierwszy <xref:Microsoft.EntityFrameworkCore.DbContext> jest `_catalogContext` , a druga `DbContext` znajduje się w `_integrationEventLogService` obiektu. Akcja zatwierdzenia jest wykonywana we wszystkich `DbContext` obiektów za pomocą strategii wykonywania EF.

Aby osiągnąć ten wielu `DbContext` zatwierdzenia `SaveEventAndCatalogContextChangesAsync` używa `ResilientTransaction` klasy, jak pokazano w poniższym kodzie:

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

`ResilientTransaction.ExecuteAsync` Metoda po prostu rozpoczyna transakcji z przekazanych `DbContext` (`_catalogContext`), a następnie udostępnia `EventLogService` użyć danej transakcji, aby zapisać zmiany w porównaniu z `IntegrationEventLogContext` i zatwierdzenia, cała transakcja.

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

- **Elastyczność połączeń i przejmowanie poleceń przy użyciu programu EF w aplikacji ASP.NET MVC** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Torre'a de la Cesarowi. Za pomocą odporne na błędy Entity Framework Core połączeń z serwerem SQL i transakcji** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Poprzednie](implement-retries-exponential-backoff.md)
>[dalej](explore-custom-http-call-retries-exponential-backoff.md)
