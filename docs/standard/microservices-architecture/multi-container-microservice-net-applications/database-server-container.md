---
title: Za pomocą serwera bazy danych z uruchomionym jako kontener
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Za pomocą serwera bazy danych z uruchomionym jako kontener
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: 42b0bf43ace00b1eb4b48c39604b89ea76c99220
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106152"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="3b2ab-103">Za pomocą serwera bazy danych z uruchomionym jako kontener</span><span class="sxs-lookup"><span data-stu-id="3b2ab-103">Using a database server running as a container</span></span>

<span data-ttu-id="3b2ab-104">Masz baz danych (SQL Server, PostgreSQL, MySQL itp.) na serwerach autonomicznych regularne w klastrach lokalnie lub w usługach PaaS w chmurze, takich jak bazy danych SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-104">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="3b2ab-105">Jednak dla środowisk projektowania i testowania, uruchomione jako kontenery baz danych jest wygodne, ponieważ nie ma żadnych zależności zewnętrznych i po prostu działa rozwiązania docker compose polecenie uruchamia całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-105">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency, and simply running the docker-compose command starts the whole application.</span></span> <span data-ttu-id="3b2ab-106">O tych baz danych jako kontenery jest również doskonałe rozwiązanie dla testów integracji, ponieważ baza danych jest uruchomiona w kontenerze i jest zawsze wypełniane przy użyciu tego samego przykładowych danych, więc testów może być bardziej przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-106">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="3b2ab-107">Program SQL Server uruchomiony jako kontener z bazą danych związanych z mikrousługi</span><span class="sxs-lookup"><span data-stu-id="3b2ab-107">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="3b2ab-108">W eShopOnContainers, ma kontenera o nazwie sql.data zdefiniowane w [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) pliku z programem SQL Server dla systemu Linux w przypadku wszystkich baz danych programu SQL Server wymagane dla mikrousług.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-108">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="3b2ab-109">(Można również mieć jeden kontener programu SQL Server dla każdej bazy danych, ale która wymaga więcej pamięci przypisana do Docker). Istotne w mikrousług jest czy każdego mikrousługi właścicielem jego danych powiązanych w związku z tym pokrewne bazę danych SQL w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-109">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="3b2ab-110">Jednak bazy danych może być dowolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-110">But the databases can be anywhere.</span></span>

<span data-ttu-id="3b2ab-111">SQL Server, kontenera w przykładowej aplikacji jest skonfigurowana z następującym kodem yaml programu w pliku docker-compose.yml, który zostanie wykonany po uruchomieniu rozwiązania docker-compose się.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-111">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run docker-compose up.</span></span> <span data-ttu-id="3b2ab-112">Należy pamiętać, że kod yaml programu ma skonsolidowane informacje o konfiguracji z pliku ogólnego docker-compose.yml i pliku docker compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-112">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="3b2ab-113">(Zazwyczaj będzie odrębnych ustawień środowiska z podstawowej lub statycznej informacje związane z obrazu programu SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="3b2ab-113">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
    ports:
      - "5434:1433"
```

<span data-ttu-id="3b2ab-114">W podobny sposób, zamiast `docker-compose`, następujące `docker run` polecenie można uruchomić tego kontenera:</span><span class="sxs-lookup"><span data-stu-id="3b2ab-114">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

<span data-ttu-id="3b2ab-115">Jednak jeśli wdrażasz aplikacji kontenera usługi takie jak eShopOnContainers jest bardziej wygodne docker tworzą się polecenie, aby go wdraża wszystkich kontenerów wymagane dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-115">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the docker-compose up command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="3b2ab-116">Po uruchomieniu tego kontenera programu SQL Server po raz pierwszy kontenera inicjuje programu SQL Server z musisz podać hasło.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-116">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="3b2ab-117">Gdy program SQL Server działa jako kontener, można zaktualizować bazy danych, nawiązując połączenie za pomocą dowolnego regularne połączenia SQL, takich jak SQL Server Management Studio, Visual Studio lub C\# kodu.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-117">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="3b2ab-118">Aplikacji eShopOnContainers inicjuje każda baza danych mikrousługi z przykładowymi danymi przez wstępne wypełnienie go z danymi podczas uruchamiania, jak wyjaśniono w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-118">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="3b2ab-119">O programu SQL Server uruchomionego jako kontener nie jest po prostu ułatwia pokaz gdzie możesz utracić dostęp do wystąpienia programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-119">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="3b2ab-120">Jakie zostały zanotowane jest również doskonałe rozwiązanie dla środowisk projektowych i testowych, aby łatwo można uruchamiać testy integracji, zaczynając od czystego obrazu programu SQL Server i znane dane przez wstępne wypełnienie nowego przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-120">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3b2ab-121">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="3b2ab-121">Additional resources</span></span>

-   <span data-ttu-id="3b2ab-122">**Uruchom obrazu programu SQL Server Docker na systemie Linux, Mac lub Windows**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span><span class="sxs-lookup"><span data-stu-id="3b2ab-122">**Run the SQL Server Docker image on Linux, Mac, or Windows**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span></span>

-   <span data-ttu-id="3b2ab-123">**Połącz i zapytania programu SQL Server w systemie Linux przy użyciu narzędzia sqlcmd**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="3b2ab-123">**Connect and query SQL Server on Linux with sqlcmd**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span></span>

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="3b2ab-124">Wstępne wypełnianie danymi testu podczas uruchamiania aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="3b2ab-124">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="3b2ab-125">Aby dodać dane do bazy danych podczas uruchamiania aplikacji, można dodać kod podobnie do następującej metody konfiguracji w klasie uruchomienia projektu interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="3b2ab-125">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

<span data-ttu-id="3b2ab-126">Następujący kod w klasie CatalogContextSeed niestandardowe wypełnienie danych.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-126">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="3b2ab-127">Po uruchomieniu testów integracji sposób generowania danych zgodne z testów integracji jest użyteczne.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-127">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="3b2ab-128">Możliwość tworzenia wszystko od początku, w tym wystąpienia programu SQL Server działające w kontenerze, jest doskonały dla środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-128">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="3b2ab-129">Baza danych Core InMemory EF i na serwerze SQL działa jako kontener</span><span class="sxs-lookup"><span data-stu-id="3b2ab-129">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="3b2ab-130">Inny dobry wybór w przypadku uruchamiania testów jest używanie dostawcy bazy danych programu Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-130">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="3b2ab-131">Tę konfigurację można określić w metodzie ConfigureServices Klasa początkowa w projekcie interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="3b2ab-131">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="3b2ab-132">Istnieje jednak ważne catch.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-132">There is an important catch, though.</span></span> <span data-ttu-id="3b2ab-133">Bazy danych w pamięci nie obsługuje wiele ograniczeń, które są specyficzne dla określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-133">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="3b2ab-134">Może na przykład Dodaj unikatowy indeks dla kolumny w modelu podstawowej EF i zapisu testu bazy danych w pamięci do sprawdzenia, czy jego nie zezwala na dodawanie zduplikowane wartości.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-134">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="3b2ab-135">Jednak podczas korzystania z bazy danych w pamięci nie może obsłużyć unikatowe indeksy w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-135">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="3b2ab-136">W związku z tym bazy danych w pamięci nie zachowują się tak samo jak rzeczywistych bazy danych SQL Server — nie nie emulować ograniczenia dotyczące bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-136">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="3b2ab-137">Mimo tego bazy danych w pamięci jest nadal przydatne w przypadku testowania i tworzenia prototypów.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-137">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="3b2ab-138">Ale jeśli chcesz utworzyć integracji dokładne testy, które wziąć pod uwagę zachowanie wykonania określonej bazy danych, należy użyć rzeczywistych bazy danych, takich jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-138">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="3b2ab-139">W tym celu programem SQL Server w kontenerze jest doskonałym wyborem i dokładność niż EF Core InMemory dostawcy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-139">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="3b2ab-140">Przy użyciu usługi pamięć podręczna Redis uruchomione w kontenerze</span><span class="sxs-lookup"><span data-stu-id="3b2ab-140">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="3b2ab-141">Możesz uruchomić Redis w kontenerze, szczególnie w przypadku projektowania i testowania i weryfikacja koncepcji.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-141">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="3b2ab-142">Ten scenariusz jest wygodne, ponieważ może mieć wszystkie zależności uruchomionych na kontenery — nie tylko maszyn rozwoju lokalnego, ale dla środowiska testowego w potokach użytkownika elementu konfiguracji/CD.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-142">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="3b2ab-143">Po uruchomieniu Redis w środowisku produkcyjnym zaleca się poszukaj rozwiązania wysokiej dostępności, takich jak Redis Microsoft Azure, w którym jest uruchomiona jako PaaS (platforma jako usługa).</span><span class="sxs-lookup"><span data-stu-id="3b2ab-143">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="3b2ab-144">W kodzie wystarczy zmienić parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-144">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="3b2ab-145">Redis zawiera obraz Docker z pamięci podręcznej Redis.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-145">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="3b2ab-146">Ten obraz jest dostępny z Centrum Docker pod tym adresem URL:</span><span class="sxs-lookup"><span data-stu-id="3b2ab-146">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="3b2ab-147">Kontener Docker Redis można uruchomić bezpośrednio, wykonując następujące polecenie Docker interfejsu wiersza polecenia z wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="3b2ab-147">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="3b2ab-148">Obraz Redis obejmuje Uwidacznianie: 6379 (port używany przez Redis), więc standardowe łączenie kontenera udostępnienie jej automatycznie do połączonego kontenerów.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-148">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="3b2ab-149">W eShopOnContainers mikrousługi basket.api korzysta z pamięci podręcznej Redis uruchomione jako kontener.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-149">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="3b2ab-150">Tego kontenera basket.data jest określony jako część pliku wielu kontenera docker-compose.yml, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3b2ab-150">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="3b2ab-151">Ten kod w docker-compose.yml definiuje kontener o nazwie basket.data na podstawie obrazu redis i publikowania portu 6379 wewnętrznie, co oznacza, że będzie on dostępny tylko w innych kontenery uruchomiony w ramach hosta Docker.</span><span class="sxs-lookup"><span data-stu-id="3b2ab-151">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="3b2ab-152">Ponadto w pliku docker compose.override.yml mikrousługi basket.api przykładowej eShopOnContainers definiuje parametry połączenia do użycia dla tego kontenera Redis:</span><span class="sxs-lookup"><span data-stu-id="3b2ab-152">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
<span data-ttu-id="3b2ab-153">[Poprzednie](multi-container-applications-docker-compose.md)
[dalej](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="3b2ab-153">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
