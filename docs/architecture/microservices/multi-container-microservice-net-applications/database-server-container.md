---
title: Używanie serwera bazy danych działającego jako kontener
description: Zrozumienie znaczenia korzystania z serwera bazy danych działającego jako kontener tylko do tworzenia aplikacji. Nigdy do produkcji.
ms.date: 01/30/2020
ms.openlocfilehash: 0cbc933003aac10970814378c27e88b5cb0ddbe5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628530"
---
# <a name="use-a-database-server-running-as-a-container"></a>Używanie serwera bazy danych działającego jako kontener

Bazy danych (SQL Server, PostgreSQL, MySQL itp.) można mieć na zwykłych serwerach autonomicznych, w klastrach lokalnych lub w usługach PaaS w chmurze, takich jak usługa Azure SQL DB. Jednak w środowiskach deweloperskich i testowych posiadanie baz danych uruchomionych jako kontenery jest wygodne, `docker-compose up` ponieważ nie masz żadnych zależności zewnętrznych i po prostu uruchomienie polecenia uruchamia całą aplikację. Posiadanie tych baz danych jako kontenerów jest również idealne do testów integracji, ponieważ baza danych jest uruchamiana w kontenerze i jest zawsze wypełniona tymi samymi przykładowymi danymi, dzięki czemu testy mogą być bardziej przewidywalne.

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Program SQL Server uruchomiony jako kontener z bazą danych związaną z mikrousługami

W eShopOnContainers istnieje kontener o `sqldata`nazwie , zgodnie z definicją w pliku [docker-compose.yml,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) który uruchamia SQL Server dla systemu Linux wystąpienia z bazami danych SQL dla wszystkich mikrousług, które potrzebują jednego.

Kluczowym punktem w mikrousługach jest, że każda mikrousługa jest właścicielem powiązanych danych, więc powinien mieć własną bazę danych. Jednak bazy danych mogą być wszędzie. W takim przypadku wszystkie one znajdują się w tym samym kontenerze, aby zachować wymagania dotyczące pamięci platformy Docker tak niskie, jak to możliwe. Należy pamiętać, że jest to wystarczające rozwiązanie do tworzenia i, być może, testowania, ale nie dla produkcji.

Kontener programu SQL Server w przykładowej aplikacji jest skonfigurowany z następującym kodem YAML w pliku `docker-compose up`docker-compose.yml, który jest wykonywany po uruchomieniu . Należy zauważyć, że kod YAML ma skonsolidowane informacje o konfiguracji z ogólnego pliku docker-compose.yml i pliku docker-compose.override.yml. (Zazwyczaj należy oddzielić ustawienia środowiska od informacji podstawowych lub statycznych związanych z obrazem programu SQL Server).

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

W podobny sposób zamiast `docker-compose`używać `docker run` następującego polecenia można uruchomić ten kontener:

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

Jednak jeśli wdrażasz aplikację wielokontenerową, taką jak eShopOnContainers, `docker-compose up` wygodniej jest używać polecenia, aby wdrożyć wszystkie wymagane kontenery dla aplikacji.

Po pierwszym uruchomieniu tego kontenera programu SQL Server kontener inicjuje program SQL Server przy użyciu podanych hasła. Gdy sql Server jest uruchomiony jako kontener, można zaktualizować bazę danych, łącząc się za pośrednictwem dowolnego\# zwykłego połączenia SQL, takich jak z SQL Server Management Studio, Visual Studio lub kod C.

Aplikacja eShopOnContainers inicjuje każdą bazę danych mikrousług z przykładowymi danymi, rozmieszając ją danymi podczas uruchamiania, jak wyjaśniono w poniższej sekcji.

Po SQL Server uruchomiony jako kontener jest nie tylko przydatne dla wersji demonstracyjnej, gdzie nie może mieć dostępu do wystąpienia programu SQL Server. Jak wspomniano, jest również wielki dla środowisk deweloperskich i testowych, dzięki czemu można łatwo uruchomić testy integracji, począwszy od czystego obrazu programu SQL Server i znanych danych przez rozmieszczanie nowych przykładowych danych.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Uruchamianie obrazu platformy Docker programu SQL Server w systemach Linux, Mac lub Windows** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- **Łączenie i wykonywanie zapytań do programu SQL Server w systemie Linux za pomocą sqlcmd** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a>Wysiew z danymi testowymi podczas uruchamiania aplikacji sieci Web

Aby dodać dane do bazy danych podczas uruchamiania aplikacji, można `Main` dodać `Program` kod podobny do metody w klasie projektu interfejsu API sieci Web:

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

Istnieje ważne zastrzeżenie podczas stosowania migracji i rozmieszczania bazy danych podczas uruchamiania kontenera. Ponieważ serwer bazy danych może nie być dostępny z jakiegokolwiek powodu, należy obsługiwać ponownych prób podczas oczekiwania na serwer, który ma być dostępny. Ta logika ponawiania jest obsługiwana przez metodę `MigrateDbContext()` rozszerzenia, jak pokazano w następującym kodzie:

```cs
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

Następujący kod w niestandardowej klasie CatalogContextSeed wypełnia dane.

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

Po uruchomieniu testów integracji, o sposób generowania danych zgodnych z testów integracji jest przydatne. Możliwość tworzenia wszystkiego od podstaw, w tym wystąpienia programu SQL Server uruchomionego w kontenerze, jest świetna dla środowisk testowych.

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>Baza danych EF Core InMemory kontra SQL Server uruchomiony jako kontener

Innym dobrym wyborem podczas uruchamiania testów jest użycie dostawcy bazy danych Jednostki InMemory. Tę konfigurację można określić w metodzie ConfigureServices klasy Startup w projekcie interfejsu API sieci Web:

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }

    // Other Startup code ...
}
```

Jest jednak ważny haczyk. Baza danych w pamięci nie obsługuje wiele ograniczeń, które są specyficzne dla określonej bazy danych. Na przykład można dodać unikatowy indeks w kolumnie w modelu EF Core i napisać test względem bazy danych w pamięci, aby sprawdzić, czy nie pozwala dodać zduplikowaną wartość. Ale podczas korzystania z bazy danych w pamięci, nie można obsłużyć unikatowe indeksy w kolumnie. W związku z tym baza danych w pamięci nie zachowuje się dokładnie tak samo jak rzeczywista baza danych programu SQL Server — nie emuluje ograniczeń specyficznych dla bazy danych.

Mimo to baza danych w pamięci jest nadal przydatna do testowania i tworzenia prototypów. Ale jeśli chcesz utworzyć dokładne testy integracji, które uwzględniają zachowanie implementacji określonej bazy danych, należy użyć prawdziwej bazy danych, takich jak SQL Server. W tym celu uruchomienie programu SQL Server w kontenerze jest doskonałym wyborem i bardziej dokładne niż dostawca bazy danych EF Core InMemory.

## <a name="using-a-redis-cache-service-running-in-a-container"></a>Korzystanie z usługi redis pamięci podręcznej uruchomionej w kontenerze

Można uruchomić Redis na kontenerze, szczególnie dla programowania i testowania i scenariuszy proof-of-concept. Ten scenariusz jest wygodny, ponieważ wszystkie zależności mogą być uruchomione na kontenerach — nie tylko dla lokalnych maszyn deweloperskich, ale także dla środowisk testowych w potokach ciągłej integracji/ciągłego rozwoju.

Jednak po uruchomieniu Redis w środowisku produkcyjnym, lepiej jest szukać rozwiązania o wysokiej dostępności, takich jak Redis Microsoft Azure, który działa jako PaaS (Platforma jako usługa). W kodzie wystarczy zmienić parametry połączenia.

Redis udostępnia obraz platformy Docker z redis. Ten obraz jest dostępny w centrum docker pod tym adresem URL:

<https://hub.docker.com/_/redis/>

Kontener Docker Redis można bezpośrednio uruchomić, wykonując w wierszu polecenia następujące polecenie wiersza polecenia wiersza polecenia platformy Docker:

```console
docker run --name some-redis -d redis
```

Obraz Redis zawiera expose:6379 (port używany przez Redis), więc standardowe łączenie kontenerów sprawi, że będzie automatycznie dostępny dla połączonych kontenerów.

W eShopOnContainers `basket-api` mikrousługi używa redis pamięci podręcznej uruchomionej jako kontener. Ten `basketdata` kontener jest zdefiniowany jako część pliku *docker-compose.yml* z wieloma kontenerami, jak pokazano w poniższym przykładzie:

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

Ten kod w pliku docker-compose.yml `basketdata` definiuje kontener o nazwie na podstawie obrazu redis i publikowania portu 6379 wewnętrznie. Oznacza to, że będzie dostępny tylko z innych kontenerów działających w obrębie hosta platformy Docker.

Na koniec w pliku *docker-compose.override.yml* `basket-api` mikrousługi dla eShopOnContainers próbki definiuje parametry połączenia do użycia dla tego kontenera Redis:

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

Jak wspomniano wcześniej, nazwa mikrousługi `basketdata` jest rozpoznawana przez wewnętrzną sieć DNS platformy Docker.

>[!div class="step-by-step"]
>[Poprzedni](multi-container-applications-docker-compose.md)
>[następny](integration-event-based-microservice-communications.md)
