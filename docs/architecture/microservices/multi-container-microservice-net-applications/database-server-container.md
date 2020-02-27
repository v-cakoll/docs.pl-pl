---
title: Korzystanie z serwera bazy danych działającego jako kontener
description: Zapoznaj się z ważnością korzystania z serwera bazy danych działającego jako kontener tylko do celów deweloperskich. Nigdy nie do produkcji.
ms.date: 01/30/2020
ms.openlocfilehash: 0cbc933003aac10970814378c27e88b5cb0ddbe5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628530"
---
# <a name="use-a-database-server-running-as-a-container"></a>Korzystanie z serwera bazy danych działającego jako kontener

Możesz mieć bazy danych (SQL Server, PostgreSQL, MySQL itp.) na zwykłych serwerach autonomicznych, w klastrach lokalnych lub w usługach PaaS Services w chmurze, takich jak Azure SQL DB. Jednak w środowiskach deweloperskich i testowych, które bazy danych działają jako kontenery są wygodne, ponieważ nie istnieje żadna zależność zewnętrzna i po prostu uruchomienie `docker-compose up` polecenie uruchamia całą aplikację. Posiadanie tych baz danych jako kontenerów jest również doskonałe dla testów integracji, ponieważ baza danych została uruchomiona w kontenerze i jest zawsze wypełniana tymi samymi przykładowymi danymi, dzięki czemu testy mogą być bardziej przewidywalne.

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server działa jako kontener z bazą danych z mikrousługą

W eShopOnContainers istnieje kontener o nazwie `sqldata`, zgodnie z definicją w pliku [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , który uruchamia wystąpienie SQL Server dla systemu Linux z bazami danych SQL dla wszystkich mikrousług, które potrzebują.

Kluczowy punkt w mikrousługach polega na tym, że każda mikrousługa jest właścicielem powiązanych danych, dlatego powinna mieć własną bazę danych. Jednak bazy danych mogą znajdować się w dowolnym miejscu. W tym przypadku są one wszystkie w tym samym kontenerze, aby zachować wymagania dotyczące pamięci platformy Docker jak najmniejszej ilości. Należy pamiętać, że jest to dobre, wystarczające rozwiązanie do programowania i, na przykład, testowania, ale nie w środowisku produkcyjnym.

Kontener SQL Server w przykładowej aplikacji jest skonfigurowany przy użyciu następującego kodu YAML w pliku Docker-Compose. yml, który jest wykonywany podczas uruchamiania `docker-compose up`. Należy pamiętać, że kod YAML ma skonsolidowane informacje o konfiguracji z pliku Generic Docker-Compose. yml oraz pliku Docker-Compose. override. yml. (Zazwyczaj należy oddzielić ustawienia środowiska od podstawowej lub statycznej informacji powiązanej z obrazem SQL Server).

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

W podobny sposób, zamiast używać `docker-compose`, następujące polecenie `docker run` może uruchomić ten kontener:

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

Jednak w przypadku wdrażania aplikacji z wieloma kontenerami, takich jak eShopOnContainers, wygodniejsze jest użycie polecenia `docker-compose up`, aby wdrożyć wszystkie wymagane kontenery dla aplikacji.

Po pierwszym uruchomieniu tego kontenera SQL Server Kontener inicjuje SQL Server przy użyciu podania hasła. Gdy SQL Server jest uruchomiony jako kontener, możesz zaktualizować bazę danych, łącząc się za pośrednictwem dowolnego zwykłego połączenia SQL, takiego jak z SQL Server Management Studio, Visual Studio lub C\# Code.

Aplikacja eShopOnContainers inicjuje każdą mikrousługą bazę danych z przykładowymi danymi, umieszczając je w danych podczas uruchamiania, jak wyjaśniono w poniższej sekcji.

Posiadanie SQL Server działającego jako kontenera nie jest samo przydatne w przypadku pokazu, w którym może nie mieć dostępu do wystąpienia SQL Server. Jak zauważono, jest to również idealne rozwiązanie w środowiskach deweloperskich i testowych, dzięki czemu można łatwo uruchomić testy integracji zaczynające się od czystego obrazu SQL Server i znanych danych, umieszczając nowe przykładowe dane.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Uruchamianie obrazu SQL Server Docker w systemie Linux, Mac lub Windows** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- **Łączenie i SQL Server on Linux zapytań przy użyciu narzędzia sqlcmd** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a>Umieszczanie danych testowych przy uruchamianiu aplikacji sieci Web

Aby dodać dane do bazy danych podczas uruchamiania aplikacji, można dodać kod podobny do poniższego do metody `Main` w klasie `Program` projektu interfejsu API sieci Web:

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

Podczas stosowania migracji i wypełniania bazy danych podczas uruchamiania kontenera istnieje ważne zastrzeżenie. Ponieważ serwer bazy danych może nie być dostępny z jakiegokolwiek powodu, należy obsłużyć ponawianie prób podczas oczekiwania na udostępnienie serwera. Ta logika ponawiania jest obsługiwana przez metodę rozszerzenia `MigrateDbContext()`, jak pokazano w poniższym kodzie:

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

Poniższy kod w niestandardowej klasie CatalogContextSeed wypełnia dane.

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

Po uruchomieniu testów integracji istnieje możliwość generowania danych spójnych z testami integracji. Możliwość tworzenia wszystkiego od podstaw, w tym wystąpienia SQL Server działającego w kontenerze, doskonale sprawdza się w środowiskach testowych.

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core bazę danych inMemory, a SQL Server działa jako kontener

Innym dobrym wyborem w przypadku uruchamiania testów jest użycie dostawcy bazy danych inMemory Entity Framework. Możesz określić tę konfigurację w metodzie ConfigureServices klasy Start w projekcie interfejsu API sieci Web:

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

Istnieje ważna połowa, chociaż. Baza danych w pamięci nie obsługuje wielu ograniczeń, które są specyficzne dla konkretnej bazy danych. Na przykład możesz dodać unikatowy indeks do kolumny w modelu EF Core i napisać test do bazy danych w pamięci, aby sprawdzić, czy nie zezwala na dodanie zduplikowanej wartości. Ale w przypadku korzystania z bazy danych w pamięci nie można obsłużyć unikatowych indeksów w kolumnie. W związku z tym baza danych znajdująca się w pamięci nie zachowuje się dokładnie tak samo jak rzeczywista SQL Server baza danych — nie emuluje ograniczeń specyficznych dla bazy danych.

Nawet w takim przypadku baza danych znajdująca się w pamięci jest nadal przydatna do testowania i tworzenia prototypów. Jeśli jednak chcesz utworzyć dokładne testy integracji, które uwzględniają zachowanie określonej implementacji bazy danych, musisz użyć prawdziwej bazy danych, takiej jak SQL Server. W tym celu uruchomienie SQL Server w kontenerze jest doskonałym wyborem i jest bardziej dokładne niż dostawca bazy danych inMemory EF Core.

## <a name="using-a-redis-cache-service-running-in-a-container"></a>Używanie usługi pamięci podręcznej Redis działającej w kontenerze

Można uruchamiać Redis w kontenerze, szczególnie w przypadku projektowania i testowania oraz dla scenariuszy weryfikacji koncepcji. Ten scenariusz jest wygodny, ponieważ możesz mieć wszystkie zależności działające w kontenerach — nie tylko dla lokalnych maszyn deweloperskich, ale dla środowisk testowych w potokach ciągłej integracji/ciągłego dostarczania.

Jednak po uruchomieniu Redis w środowisku produkcyjnym lepiej jest wyszukać rozwiązanie wysokiej dostępności, takie jak Redis Microsoft Azure, które działa jako PaaS (platforma jako usługa). W kodzie należy jedynie zmienić parametry połączenia.

Redis udostępnia obraz platformy Docker z Redis. Ten obraz jest dostępny z poziomu usługi Docker Hub pod tym adresem URL:

<https://hub.docker.com/_/redis/>

Można bezpośrednio uruchomić kontener Docker Redis, wykonując następujące polecenie Docker CLI w wierszu polecenia:

```console
docker run --name some-redis -d redis
```

Obraz Redis obejmuje Uwidacznianie: 6379 (port używany przez Redis), więc łączenie kontenerów standardowych będzie automatycznie dostępne dla połączonych kontenerów.

W `basket-api` eShopOnContainers mikrousługa korzysta z pamięci podręcznej Redis działającej jako kontener. Kontener `basketdata` jest zdefiniowany jako część pliku *Docker-Compose. yml* z wielokontenerem, jak pokazano w następującym przykładzie:

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

Ten kod w Docker-Compose. yml definiuje kontener o nazwie `basketdata` w oparciu o obraz Redis i publikuje wewnętrznie port 6379. Oznacza to, że będzie dostępny tylko z innych kontenerów uruchomionych w ramach hosta platformy Docker.

Na koniec w pliku *Docker-Compose. override. yml* , `basket-api` mikrousługa dla próbki eShopOnContainers definiuje parametry połączenia do użycia dla tego kontenera Redis:

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

Jak wspomniano wcześniej, nazwa `basketdata` mikrousług jest rozpoznawana przez system DNS w sieci wewnętrznej platformy Docker.

>[!div class="step-by-step"]
>[Poprzednie](multi-container-applications-docker-compose.md)
>[dalej](integration-event-based-microservice-communications.md)
