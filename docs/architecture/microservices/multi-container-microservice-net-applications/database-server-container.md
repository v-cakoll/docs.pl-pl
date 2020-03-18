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
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="d88b8-104">Używanie serwera bazy danych działającego jako kontener</span><span class="sxs-lookup"><span data-stu-id="d88b8-104">Use a database server running as a container</span></span>

<span data-ttu-id="d88b8-105">Bazy danych (SQL Server, PostgreSQL, MySQL itp.) można mieć na zwykłych serwerach autonomicznych, w klastrach lokalnych lub w usługach PaaS w chmurze, takich jak usługa Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="d88b8-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="d88b8-106">Jednak w środowiskach deweloperskich i testowych posiadanie baz danych uruchomionych jako kontenery jest wygodne, `docker-compose up` ponieważ nie masz żadnych zależności zewnętrznych i po prostu uruchomienie polecenia uruchamia całą aplikację.</span><span class="sxs-lookup"><span data-stu-id="d88b8-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="d88b8-107">Posiadanie tych baz danych jako kontenerów jest również idealne do testów integracji, ponieważ baza danych jest uruchamiana w kontenerze i jest zawsze wypełniona tymi samymi przykładowymi danymi, dzięki czemu testy mogą być bardziej przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="d88b8-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="d88b8-108">Program SQL Server uruchomiony jako kontener z bazą danych związaną z mikrousługami</span><span class="sxs-lookup"><span data-stu-id="d88b8-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="d88b8-109">W eShopOnContainers istnieje kontener o `sqldata`nazwie , zgodnie z definicją w pliku [docker-compose.yml,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) który uruchamia SQL Server dla systemu Linux wystąpienia z bazami danych SQL dla wszystkich mikrousług, które potrzebują jednego.</span><span class="sxs-lookup"><span data-stu-id="d88b8-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="d88b8-110">Kluczowym punktem w mikrousługach jest, że każda mikrousługa jest właścicielem powiązanych danych, więc powinien mieć własną bazę danych.</span><span class="sxs-lookup"><span data-stu-id="d88b8-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="d88b8-111">Jednak bazy danych mogą być wszędzie.</span><span class="sxs-lookup"><span data-stu-id="d88b8-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="d88b8-112">W takim przypadku wszystkie one znajdują się w tym samym kontenerze, aby zachować wymagania dotyczące pamięci platformy Docker tak niskie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="d88b8-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="d88b8-113">Należy pamiętać, że jest to wystarczające rozwiązanie do tworzenia i, być może, testowania, ale nie dla produkcji.</span><span class="sxs-lookup"><span data-stu-id="d88b8-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="d88b8-114">Kontener programu SQL Server w przykładowej aplikacji jest skonfigurowany z następującym kodem YAML w pliku `docker-compose up`docker-compose.yml, który jest wykonywany po uruchomieniu .</span><span class="sxs-lookup"><span data-stu-id="d88b8-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="d88b8-115">Należy zauważyć, że kod YAML ma skonsolidowane informacje o konfiguracji z ogólnego pliku docker-compose.yml i pliku docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="d88b8-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="d88b8-116">(Zazwyczaj należy oddzielić ustawienia środowiska od informacji podstawowych lub statycznych związanych z obrazem programu SQL Server).</span><span class="sxs-lookup"><span data-stu-id="d88b8-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="d88b8-117">W podobny sposób zamiast `docker-compose`używać `docker run` następującego polecenia można uruchomić ten kontener:</span><span class="sxs-lookup"><span data-stu-id="d88b8-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="d88b8-118">Jednak jeśli wdrażasz aplikację wielokontenerową, taką jak eShopOnContainers, `docker-compose up` wygodniej jest używać polecenia, aby wdrożyć wszystkie wymagane kontenery dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d88b8-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="d88b8-119">Po pierwszym uruchomieniu tego kontenera programu SQL Server kontener inicjuje program SQL Server przy użyciu podanych hasła.</span><span class="sxs-lookup"><span data-stu-id="d88b8-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="d88b8-120">Gdy sql Server jest uruchomiony jako kontener, można zaktualizować bazę danych, łącząc się za pośrednictwem dowolnego\# zwykłego połączenia SQL, takich jak z SQL Server Management Studio, Visual Studio lub kod C.</span><span class="sxs-lookup"><span data-stu-id="d88b8-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="d88b8-121">Aplikacja eShopOnContainers inicjuje każdą bazę danych mikrousług z przykładowymi danymi, rozmieszając ją danymi podczas uruchamiania, jak wyjaśniono w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d88b8-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="d88b8-122">Po SQL Server uruchomiony jako kontener jest nie tylko przydatne dla wersji demonstracyjnej, gdzie nie może mieć dostępu do wystąpienia programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d88b8-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="d88b8-123">Jak wspomniano, jest również wielki dla środowisk deweloperskich i testowych, dzięki czemu można łatwo uruchomić testy integracji, począwszy od czystego obrazu programu SQL Server i znanych danych przez rozmieszczanie nowych przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="d88b8-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d88b8-124">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="d88b8-124">Additional resources</span></span>

- <span data-ttu-id="d88b8-125">**Uruchamianie obrazu platformy Docker programu SQL Server w systemach Linux, Mac lub Windows** </span><span class="sxs-lookup"><span data-stu-id="d88b8-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="d88b8-126">**Łączenie i wykonywanie zapytań do programu SQL Server w systemie Linux za pomocą sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="d88b8-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="d88b8-127">Wysiew z danymi testowymi podczas uruchamiania aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="d88b8-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="d88b8-128">Aby dodać dane do bazy danych podczas uruchamiania aplikacji, można `Main` dodać `Program` kod podobny do metody w klasie projektu interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="d88b8-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

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

<span data-ttu-id="d88b8-129">Istnieje ważne zastrzeżenie podczas stosowania migracji i rozmieszczania bazy danych podczas uruchamiania kontenera.</span><span class="sxs-lookup"><span data-stu-id="d88b8-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="d88b8-130">Ponieważ serwer bazy danych może nie być dostępny z jakiegokolwiek powodu, należy obsługiwać ponownych prób podczas oczekiwania na serwer, który ma być dostępny.</span><span class="sxs-lookup"><span data-stu-id="d88b8-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="d88b8-131">Ta logika ponawiania jest obsługiwana przez metodę `MigrateDbContext()` rozszerzenia, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="d88b8-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

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

<span data-ttu-id="d88b8-132">Następujący kod w niestandardowej klasie CatalogContextSeed wypełnia dane.</span><span class="sxs-lookup"><span data-stu-id="d88b8-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="d88b8-133">Po uruchomieniu testów integracji, o sposób generowania danych zgodnych z testów integracji jest przydatne.</span><span class="sxs-lookup"><span data-stu-id="d88b8-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="d88b8-134">Możliwość tworzenia wszystkiego od podstaw, w tym wystąpienia programu SQL Server uruchomionego w kontenerze, jest świetna dla środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="d88b8-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="d88b8-135">Baza danych EF Core InMemory kontra SQL Server uruchomiony jako kontener</span><span class="sxs-lookup"><span data-stu-id="d88b8-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="d88b8-136">Innym dobrym wyborem podczas uruchamiania testów jest użycie dostawcy bazy danych Jednostki InMemory.</span><span class="sxs-lookup"><span data-stu-id="d88b8-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="d88b8-137">Tę konfigurację można określić w metodzie ConfigureServices klasy Startup w projekcie interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="d88b8-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="d88b8-138">Jest jednak ważny haczyk.</span><span class="sxs-lookup"><span data-stu-id="d88b8-138">There is an important catch, though.</span></span> <span data-ttu-id="d88b8-139">Baza danych w pamięci nie obsługuje wiele ograniczeń, które są specyficzne dla określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d88b8-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="d88b8-140">Na przykład można dodać unikatowy indeks w kolumnie w modelu EF Core i napisać test względem bazy danych w pamięci, aby sprawdzić, czy nie pozwala dodać zduplikowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="d88b8-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="d88b8-141">Ale podczas korzystania z bazy danych w pamięci, nie można obsłużyć unikatowe indeksy w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="d88b8-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="d88b8-142">W związku z tym baza danych w pamięci nie zachowuje się dokładnie tak samo jak rzeczywista baza danych programu SQL Server — nie emuluje ograniczeń specyficznych dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d88b8-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="d88b8-143">Mimo to baza danych w pamięci jest nadal przydatna do testowania i tworzenia prototypów.</span><span class="sxs-lookup"><span data-stu-id="d88b8-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="d88b8-144">Ale jeśli chcesz utworzyć dokładne testy integracji, które uwzględniają zachowanie implementacji określonej bazy danych, należy użyć prawdziwej bazy danych, takich jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d88b8-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="d88b8-145">W tym celu uruchomienie programu SQL Server w kontenerze jest doskonałym wyborem i bardziej dokładne niż dostawca bazy danych EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="d88b8-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="d88b8-146">Korzystanie z usługi redis pamięci podręcznej uruchomionej w kontenerze</span><span class="sxs-lookup"><span data-stu-id="d88b8-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="d88b8-147">Można uruchomić Redis na kontenerze, szczególnie dla programowania i testowania i scenariuszy proof-of-concept.</span><span class="sxs-lookup"><span data-stu-id="d88b8-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="d88b8-148">Ten scenariusz jest wygodny, ponieważ wszystkie zależności mogą być uruchomione na kontenerach — nie tylko dla lokalnych maszyn deweloperskich, ale także dla środowisk testowych w potokach ciągłej integracji/ciągłego rozwoju.</span><span class="sxs-lookup"><span data-stu-id="d88b8-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="d88b8-149">Jednak po uruchomieniu Redis w środowisku produkcyjnym, lepiej jest szukać rozwiązania o wysokiej dostępności, takich jak Redis Microsoft Azure, który działa jako PaaS (Platforma jako usługa).</span><span class="sxs-lookup"><span data-stu-id="d88b8-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="d88b8-150">W kodzie wystarczy zmienić parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="d88b8-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="d88b8-151">Redis udostępnia obraz platformy Docker z redis.</span><span class="sxs-lookup"><span data-stu-id="d88b8-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="d88b8-152">Ten obraz jest dostępny w centrum docker pod tym adresem URL:</span><span class="sxs-lookup"><span data-stu-id="d88b8-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="d88b8-153">Kontener Docker Redis można bezpośrednio uruchomić, wykonując w wierszu polecenia następujące polecenie wiersza polecenia wiersza polecenia platformy Docker:</span><span class="sxs-lookup"><span data-stu-id="d88b8-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="d88b8-154">Obraz Redis zawiera expose:6379 (port używany przez Redis), więc standardowe łączenie kontenerów sprawi, że będzie automatycznie dostępny dla połączonych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="d88b8-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="d88b8-155">W eShopOnContainers `basket-api` mikrousługi używa redis pamięci podręcznej uruchomionej jako kontener.</span><span class="sxs-lookup"><span data-stu-id="d88b8-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="d88b8-156">Ten `basketdata` kontener jest zdefiniowany jako część pliku *docker-compose.yml* z wieloma kontenerami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d88b8-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="d88b8-157">Ten kod w pliku docker-compose.yml `basketdata` definiuje kontener o nazwie na podstawie obrazu redis i publikowania portu 6379 wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d88b8-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="d88b8-158">Oznacza to, że będzie dostępny tylko z innych kontenerów działających w obrębie hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="d88b8-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="d88b8-159">Na koniec w pliku *docker-compose.override.yml* `basket-api` mikrousługi dla eShopOnContainers próbki definiuje parametry połączenia do użycia dla tego kontenera Redis:</span><span class="sxs-lookup"><span data-stu-id="d88b8-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="d88b8-160">Jak wspomniano wcześniej, nazwa mikrousługi `basketdata` jest rozpoznawana przez wewnętrzną sieć DNS platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="d88b8-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d88b8-161">[Poprzedni](multi-container-applications-docker-compose.md)
>[następny](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="d88b8-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
