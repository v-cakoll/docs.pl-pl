---
title: Implementowanie odpornych na błędy połączeń Entity Framework Core SQL
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie odpornych na błędy połączeń Entity Framework Core SQL. Ta technika jest szczególnie ważne w przypadku korzystania z usługi Azure SQL Database w chmurze.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 59db9cdb894f76f54e77732be47dc6140a594121
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323276"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementowanie odpornych na błędy połączeń Entity Framework Core SQL

Dla bazy danych SQL Azure platformy Entity Framework Core już zawiera logikę ponawiania prób i odporności połączenia wewnętrznej bazy danych. Jednak należy włączyć strategii wykonywania programu Entity Framework, dla każdego typu DbContext połączenia, jeśli chcesz mieć [odporne na błędy połączeń z programem EF Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

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

Po włączeniu ponownych prób w połączeniach programu EF Core każdej operacji, które możesz wykonać przy użyciu programu EF Core staje się własną umożliwiający ponowienie próby operacji. Jeśli wystąpi błąd przejściowy, każde zapytanie i każde wywołanie funkcji SaveChanges zostanie ponowiona jako jednostka.

Jednak jeśli Twój kod inicjuje transakcji za pomocą BeginTransaction, definiujesz własną grupę działań, które muszą być traktowane jako jednostka — wszystko wewnątrz transakcja została wycofana, ponownie, jeśli wystąpi awaria. Jeśli próba wykonania tej transakcji, korzystając z programów EF strategii wykonywania (zasady ponawiania) i obejmują kilka wywołań funkcji SaveChanges z wielu DbContexts w transakcji, zostanie wyświetlone wyjątek, jak pokazano poniżej.

> System.InvalidOperationException: Strategia wykonywania skonfigurowany "SqlServerRetryingExecutionStrategy" nie obsługuje transakcji zainicjowanej przez użytkownika. Strategia wykonywania zwróconych przez "DbContext.Database.CreateExecutionStrategy()" umożliwia wykonywanie wszystkich operacji w transakcji jako jednostka z możliwością ponowienia próby.

To rozwiązanie jest ręcznie wywołać strategii wykonywania EF z delegatem reprezentujący wszystko, co ma zostać wykonana. Jeśli wystąpi błąd przejściowy, strategia wykonywania wywoła delegata ponownie. Na przykład, poniższy kod pokazują, jak jest zaimplementowane w ramach aplikacji eShopOnContainers przy użyciu dwóch wielu DbContexts (\_catalogContext i IntegrationEventLogContext) podczas aktualizowania produktu, a następnie zapisywania Obiekt ProductPriceChangedIntegrationEvent musi używać innego typu DbContext.

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

Jest pierwszym DbContext \_catalogContext, a druga DbContext mieści się w \_integrationEventLogService obiektu. Akcja zatwierdzenia odbywa się w wielu DbContexts za pomocą strategii wykonywania EF.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Połączenia platformy EF** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Elastyczność połączeń i przejmowanie poleceń za pomocą programu Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Torre'a de la Cesarowi. Za pomocą odporne na błędy Entity Framework Core połączeń z serwerem Sql i transakcji**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
[Poprzednie](implement-retries-exponential-backoff.md)
[dalej](explore-custom-http-call-retries-exponential-backoff.md)
