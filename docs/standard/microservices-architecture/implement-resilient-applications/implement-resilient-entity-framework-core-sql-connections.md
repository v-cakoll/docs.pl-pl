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
ms.openlocfilehash: 8600625c2022d69ebaa2645c2a8159a848b12ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>Implementowanie odporność połączeń Entity Framework Core SQL

Dla bazy danych SQL Azure programu Entity Framework Core zawiera już logiki odporności i ponów próbę połączenia wewnętrznej bazy danych. Jednak należy włączyć strategia wykonywania programu Entity Framework dla każdego połączenia DbContext, jeśli chcesz, aby [odporność połączeń EF Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

Na przykład następujący kod na poziomie połączenia EF Core umożliwia elastyczne połączeń z serwerem SQL, które są zwalniane, jeśli połączenie nie powiedzie się.

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie wykonywania i jawnych transakcji przy użyciu BeginTransaction i wielu DbContexts

Po włączeniu ponownych prób w połączeniach EF Core każdej operacji wykonywanych przy użyciu EF Core staje się działania można spróbować ponownie. Jeśli wystąpi błąd przejściowy, każdego zapytania i każde wywołanie metody SaveChanges zostanie ponowiona jako jednostka.

Jednak jeśli kod inicjuje transakcji za pomocą BeginTransaction, definiowania grupy działań, które muszą być traktowane jako jednostka — wszystkie elementy wewnątrz transakcji została wycofana, jeśli wystąpi błąd. Jeśli próba wykonania tej transakcji, używając strategii wykonywania EF (zasady ponawiania) i obejmują kilka wywołania metody SaveChanges z wielu DbContexts w transakcji, zostanie wyświetlony następujący wyjątek.

> System.InvalidOperationException: Skonfigurowana strategia wykonywania "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji inicjowanych przez użytkownika. Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostki można spróbować ponownie.

Rozwiązanie to ręczne wywoływanie strategia wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana. Jeśli wystąpi błąd przejściowy, strategia wykonywania zostaną wywołane delegat ponownie. Na przykład następujący kod pokazać, jak jest implementowane w eShopOnContainers przy użyciu dwóch wielu DbContexts (\_catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania Obiekt ProductPriceChangedIntegrationEvent musi używać innego typu DbContext.

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

Jest first DbContext \_catalogContext, a drugi DbContext znajduje się w \_integrationEventLogService obiektu. Akcja zatwierdzenia jest wykonywane przez wiele DbContexts przy użyciu EF strategia wykonywania.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Elastyczność połączenia i przechwytywaniu polecenia Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Torre de la Cesarowi. Za pomocą połączeń z serwerem Sql Core Framework jednostki odporne i transakcji**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[Poprzednie] (wdrożenie-ponownych prób wykładniczej backoff.md) [dalej] (implement-custom-http-call-retries-exponential-backoff.md)
