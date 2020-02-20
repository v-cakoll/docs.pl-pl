---
title: Korzystanie z serwera bazy danych działającego jako kontener
description: Zapoznaj się z ważnością korzystania z serwera bazy danych działającego jako kontener tylko do celów deweloperskich. Nigdy nie do produkcji.
ms.date: 01/30/2020
ms.openlocfilehash: 816ac196636f78a368a9f20e8eedcc6a22567fa7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502291"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="a1f01-104">Korzystanie z serwera bazy danych działającego jako kontener</span><span class="sxs-lookup"><span data-stu-id="a1f01-104">Use a database server running as a container</span></span>

<span data-ttu-id="a1f01-105">Możesz mieć bazy danych (SQL Server, PostgreSQL, MySQL itp.) na zwykłych serwerach autonomicznych, w klastrach lokalnych lub w usługach PaaS Services w chmurze, takich jak Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="a1f01-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="a1f01-106">Jednak w środowiskach deweloperskich i testowych, które bazy danych działają jako kontenery są wygodne, ponieważ nie istnieje żadna zależność zewnętrzna i po prostu uruchomienie `docker-compose up` polecenie uruchamia całą aplikację.</span><span class="sxs-lookup"><span data-stu-id="a1f01-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="a1f01-107">Posiadanie tych baz danych jako kontenerów jest również doskonałe dla testów integracji, ponieważ baza danych została uruchomiona w kontenerze i jest zawsze wypełniana tymi samymi przykładowymi danymi, dzięki czemu testy mogą być bardziej przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="a1f01-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="a1f01-108">SQL Server działa jako kontener z bazą danych z mikrousługą</span><span class="sxs-lookup"><span data-stu-id="a1f01-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="a1f01-109">W eShopOnContainers istnieje kontener o nazwie `sqldata`, zgodnie z definicją w pliku [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , który uruchamia wystąpienie SQL Server dla systemu Linux z bazami danych SQL dla wszystkich mikrousług, które potrzebują.</span><span class="sxs-lookup"><span data-stu-id="a1f01-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="a1f01-110">Kluczowy punkt w mikrousługach polega na tym, że każda mikrousługa jest właścicielem powiązanych danych, dlatego powinna mieć własną bazę danych.</span><span class="sxs-lookup"><span data-stu-id="a1f01-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="a1f01-111">Jednak bazy danych mogą znajdować się w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="a1f01-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="a1f01-112">W tym przypadku są one wszystkie w tym samym kontenerze, aby zachować wymagania dotyczące pamięci platformy Docker jak najmniejszej ilości.</span><span class="sxs-lookup"><span data-stu-id="a1f01-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="a1f01-113">Należy pamiętać, że jest to dobre, wystarczające rozwiązanie do programowania i, na przykład, testowania, ale nie w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="a1f01-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="a1f01-114">Kontener SQL Server w przykładowej aplikacji jest skonfigurowany przy użyciu następującego kodu YAML w pliku Docker-Compose. yml, który jest wykonywany podczas uruchamiania `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="a1f01-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="a1f01-115">Należy pamiętać, że kod YAML ma skonsolidowane informacje o konfiguracji z pliku Generic Docker-Compose. yml oraz pliku Docker-Compose. override. yml.</span><span class="sxs-lookup"><span data-stu-id="a1f01-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="a1f01-116">(Zazwyczaj należy oddzielić ustawienia środowiska od podstawowej lub statycznej informacji powiązanej z obrazem SQL Server).</span><span class="sxs-lookup"><span data-stu-id="a1f01-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="a1f01-117">W podobny sposób, zamiast używać `docker-compose`, następujące polecenie `docker run` może uruchomić ten kontener:</span><span class="sxs-lookup"><span data-stu-id="a1f01-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="a1f01-118">Jednak w przypadku wdrażania aplikacji z wieloma kontenerami, takich jak eShopOnContainers, wygodniejsze jest użycie polecenia `docker-compose up`, aby wdrożyć wszystkie wymagane kontenery dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1f01-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="a1f01-119">Po pierwszym uruchomieniu tego kontenera SQL Server Kontener inicjuje SQL Server przy użyciu podania hasła.</span><span class="sxs-lookup"><span data-stu-id="a1f01-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="a1f01-120">Gdy SQL Server jest uruchomiony jako kontener, możesz zaktualizować bazę danych, łącząc się za pośrednictwem dowolnego zwykłego połączenia SQL, takiego jak z SQL Server Management Studio, Visual Studio lub C\# Code.</span><span class="sxs-lookup"><span data-stu-id="a1f01-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="a1f01-121">Aplikacja eShopOnContainers inicjuje każdą mikrousługą bazę danych z przykładowymi danymi, umieszczając je w danych podczas uruchamiania, jak wyjaśniono w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a1f01-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="a1f01-122">Posiadanie SQL Server działającego jako kontenera nie jest samo przydatne w przypadku pokazu, w którym może nie mieć dostępu do wystąpienia SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a1f01-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="a1f01-123">Jak zauważono, jest to również idealne rozwiązanie w środowiskach deweloperskich i testowych, dzięki czemu można łatwo uruchomić testy integracji zaczynające się od czystego obrazu SQL Server i znanych danych, umieszczając nowe przykładowe dane.</span><span class="sxs-lookup"><span data-stu-id="a1f01-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1f01-124">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="a1f01-124">Additional resources</span></span>

- <span data-ttu-id="a1f01-125">**Uruchamianie obrazu SQL Server Docker w systemie Linux, Mac lub Windows** </span><span class="sxs-lookup"><span data-stu-id="a1f01-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
    <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="a1f01-126">**Łączenie i SQL Server on Linux zapytań przy użyciu narzędzia sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="a1f01-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
    <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="a1f01-127">Umieszczanie danych testowych przy uruchamianiu aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="a1f01-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="a1f01-128">Aby dodać dane do bazy danych podczas uruchamiania aplikacji, można dodać kod podobny do poniższego do metody `Main` w klasie `Program` projektu interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="a1f01-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

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

<span data-ttu-id="a1f01-129">Podczas stosowania migracji i wypełniania bazy danych podczas uruchamiania kontenera istnieje ważne zastrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="a1f01-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="a1f01-130">Ponieważ serwer bazy danych może nie być dostępny z jakiegokolwiek powodu, należy obsłużyć ponawianie prób podczas oczekiwania na udostępnienie serwera.</span><span class="sxs-lookup"><span data-stu-id="a1f01-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="a1f01-131">Ta logika ponawiania jest obsługiwana przez metodę rozszerzenia `MigrateDbContext()`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="a1f01-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

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

<span data-ttu-id="a1f01-132">Poniższy kod w niestandardowej klasie CatalogContextSeed wypełnia dane.</span><span class="sxs-lookup"><span data-stu-id="a1f01-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="a1f01-133">Po uruchomieniu testów integracji istnieje możliwość generowania danych spójnych z testami integracji.</span><span class="sxs-lookup"><span data-stu-id="a1f01-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="a1f01-134">Możliwość tworzenia wszystkiego od podstaw, w tym wystąpienia SQL Server działającego w kontenerze, doskonale sprawdza się w środowiskach testowych.</span><span class="sxs-lookup"><span data-stu-id="a1f01-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="a1f01-135">EF Core bazę danych inMemory, a SQL Server działa jako kontener</span><span class="sxs-lookup"><span data-stu-id="a1f01-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="a1f01-136">Innym dobrym wyborem w przypadku uruchamiania testów jest użycie dostawcy bazy danych inMemory Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a1f01-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="a1f01-137">Możesz określić tę konfigurację w metodzie ConfigureServices klasy Start w projekcie interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="a1f01-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="a1f01-138">Istnieje ważna połowa, chociaż.</span><span class="sxs-lookup"><span data-stu-id="a1f01-138">There is an important catch, though.</span></span> <span data-ttu-id="a1f01-139">Baza danych w pamięci nie obsługuje wielu ograniczeń, które są specyficzne dla konkretnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a1f01-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="a1f01-140">Na przykład możesz dodać unikatowy indeks do kolumny w modelu EF Core i napisać test do bazy danych w pamięci, aby sprawdzić, czy nie zezwala na dodanie zduplikowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="a1f01-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="a1f01-141">Ale w przypadku korzystania z bazy danych w pamięci nie można obsłużyć unikatowych indeksów w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="a1f01-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="a1f01-142">W związku z tym baza danych znajdująca się w pamięci nie zachowuje się dokładnie tak samo jak rzeczywista SQL Server baza danych — nie emuluje ograniczeń specyficznych dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a1f01-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="a1f01-143">Nawet w takim przypadku baza danych znajdująca się w pamięci jest nadal przydatna do testowania i tworzenia prototypów.</span><span class="sxs-lookup"><span data-stu-id="a1f01-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="a1f01-144">Jeśli jednak chcesz utworzyć dokładne testy integracji, które uwzględniają zachowanie określonej implementacji bazy danych, musisz użyć prawdziwej bazy danych, takiej jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a1f01-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="a1f01-145">W tym celu uruchomienie SQL Server w kontenerze jest doskonałym wyborem i jest bardziej dokładne niż dostawca bazy danych inMemory EF Core.</span><span class="sxs-lookup"><span data-stu-id="a1f01-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="a1f01-146">Używanie usługi pamięci podręcznej Redis działającej w kontenerze</span><span class="sxs-lookup"><span data-stu-id="a1f01-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="a1f01-147">Można uruchamiać Redis w kontenerze, szczególnie w przypadku projektowania i testowania oraz dla scenariuszy weryfikacji koncepcji.</span><span class="sxs-lookup"><span data-stu-id="a1f01-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="a1f01-148">Ten scenariusz jest wygodny, ponieważ możesz mieć wszystkie zależności działające w kontenerach — nie tylko dla lokalnych maszyn deweloperskich, ale dla środowisk testowych w potokach ciągłej integracji/ciągłego dostarczania.</span><span class="sxs-lookup"><span data-stu-id="a1f01-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="a1f01-149">Jednak po uruchomieniu Redis w środowisku produkcyjnym lepiej jest wyszukać rozwiązanie wysokiej dostępności, takie jak Redis Microsoft Azure, które działa jako PaaS (platforma jako usługa).</span><span class="sxs-lookup"><span data-stu-id="a1f01-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="a1f01-150">W kodzie należy jedynie zmienić parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="a1f01-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="a1f01-151">Redis udostępnia obraz platformy Docker z Redis.</span><span class="sxs-lookup"><span data-stu-id="a1f01-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="a1f01-152">Ten obraz jest dostępny z poziomu usługi Docker Hub pod tym adresem URL:</span><span class="sxs-lookup"><span data-stu-id="a1f01-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="a1f01-153">Można bezpośrednio uruchomić kontener Docker Redis, wykonując następujące polecenie Docker CLI w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="a1f01-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="a1f01-154">Obraz Redis obejmuje Uwidacznianie: 6379 (port używany przez Redis), więc łączenie kontenerów standardowych będzie automatycznie dostępne dla połączonych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a1f01-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="a1f01-155">W `basket-api` eShopOnContainers mikrousługa korzysta z pamięci podręcznej Redis działającej jako kontener.</span><span class="sxs-lookup"><span data-stu-id="a1f01-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="a1f01-156">Kontener `basketdata` jest zdefiniowany jako część pliku *Docker-Compose. yml* z wielokontenerem, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a1f01-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="a1f01-157">Ten kod w Docker-Compose. yml definiuje kontener o nazwie `basketdata` w oparciu o obraz Redis i publikuje wewnętrznie port 6379.</span><span class="sxs-lookup"><span data-stu-id="a1f01-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="a1f01-158">Oznacza to, że będzie dostępny tylko z innych kontenerów uruchomionych w ramach hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="a1f01-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="a1f01-159">Na koniec w pliku *Docker-Compose. override. yml* , `basket-api` mikrousługa dla próbki eShopOnContainers definiuje parametry połączenia do użycia dla tego kontenera Redis:</span><span class="sxs-lookup"><span data-stu-id="a1f01-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="a1f01-160">Jak wspomniano wcześniej, nazwa `basketdata` mikrousług jest rozpoznawana przez system DNS w sieci wewnętrznej platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="a1f01-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a1f01-161">[Poprzednie](multi-container-applications-docker-compose.md)
>[dalej](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="a1f01-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
