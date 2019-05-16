---
title: Korzystanie z serwera bazy danych uruchomionego jako kontener
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Za pomocą serwera bazy danych uruchomionego jako kontener? tylko w celach deweloperskich! Dowiedz się, dlaczego.
ms.date: 10/02/2018
ms.openlocfilehash: 5fd92a28a09cab041225c4c817a10f5ecfedc038
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639733"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="b0e67-104">Korzystanie z serwera bazy danych uruchomionego jako kontener</span><span class="sxs-lookup"><span data-stu-id="b0e67-104">Using a database server running as a container</span></span>

<span data-ttu-id="b0e67-105">Bazy danych (SQL Server, PostgreSQL, MySQL itp.) mogą mieć na regularne autonomicznymi serwerami lokalnymi klastrami lub usługi PaaS w chmurze, takich jak bazy danych SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="b0e67-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="b0e67-106">Jednak w przypadku środowiska deweloperskie i testowe, o bazy danych zainstalowany jako kontenerów jest wygodne, ponieważ nie masz wszelkich zależności zewnętrznych, a po prostu `docker-compose up` polecenie uruchamia całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0e67-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="b0e67-107">Tych baz danych w postaci kontenerów jest również bardzo przydatne na potrzeby testów integracji, ponieważ baza danych jest uruchomiona w kontenerze i zawsze jest wypełniana przy użyciu tych samych danych przykładowych, aby testy mogą być bardziej przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="b0e67-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="b0e67-108">Program SQL Server uruchomionego jako kontener z bazą danych związanych z mikrousług</span><span class="sxs-lookup"><span data-stu-id="b0e67-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="b0e67-109">W ramach aplikacji eShopOnContainers, to kontener o nazwie sql.data zdefiniowane w [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) pliku z programem SQL Server dla systemu Linux przy użyciu wszystkich baz danych programu SQL Server służące do mikrousług.</span><span class="sxs-lookup"><span data-stu-id="b0e67-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="b0e67-110">(Może również mieć jeden kontener programu SQL Server dla każdej bazy danych, ale która wymaga większej ilości pamięci przypisana do platformy Docker). Istotną kwestią w mikrousługach to, czy każda mikrousługa jest właścicielem jego powiązanych danych, w związku z tym powiązanej bazie danych SQL w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="b0e67-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="b0e67-111">Ale bazy danych może być dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="b0e67-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="b0e67-112">Kontener w przykładowej aplikacji dla programu SQL Server jest skonfigurowany przy użyciu poniższego kodu YAML w pliku docker-compose.yml, który zostanie wykonany po uruchomieniu `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="b0e67-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="b0e67-113">Należy pamiętać, że kodu YAML ma skonsolidowanych informacji o konfiguracji z pliku docker-compose.yml ogólny i pliku docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="b0e67-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="b0e67-114">(Zazwyczaj będzie oddzielne ustawienia środowiska z podstawowej lub statyczna informacje związane z obrazu programu SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="b0e67-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="b0e67-115">W podobny sposób, zamiast `docker-compose`, następujące `docker run` polecenia można uruchomić tego kontenera:</span><span class="sxs-lookup"><span data-stu-id="b0e67-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="b0e67-116">Jednakże, Jeżeli wdrażasz aplikację obsługującą wiele kontenerów, takich jak ramach aplikacji eShopOnContainers jest bardziej wygodne do użycia `docker-compose up` polecenia, aby go służy do wdrażania wszystkich wymaganych kontenerów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0e67-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="b0e67-117">Po uruchomieniu tego kontenera programu SQL Server po raz pierwszy kontener inicjuje programu SQL Server przy użyciu hasła, które należy podać.</span><span class="sxs-lookup"><span data-stu-id="b0e67-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="b0e67-118">Gdy program SQL Server działa jako kontener, można zaktualizować bazy danych, nawiązując połączenie za pomocą dowolnego regularne połączenia SQL, takich jak SQL Server Management Studio, Visual Studio lub C\# kodu.</span><span class="sxs-lookup"><span data-stu-id="b0e67-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="b0e67-119">Aplikacja w ramach aplikacji eShopOnContainers inicjuje każdej mikrousługi bazy danych, z przykładowymi danymi rozmieszczania je z danymi podczas uruchamiania, zgodnie z opisem w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b0e67-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="b0e67-120">O programu SQL Server uruchomionego jako kontener nie jest po prostu użyteczne pokaz których możesz nie mieć dostępu do wystąpienia programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b0e67-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="b0e67-121">Jak wspomniano to również doskonałe rozwiązanie dla środowisk programowania i testowania, aby łatwo można uruchamiać testy integracji, zaczynając od czysty obraz programu SQL Server i znane dane przez wstępne wypełnienie nowe dane przykładowe.</span><span class="sxs-lookup"><span data-stu-id="b0e67-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b0e67-122">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="b0e67-122">Additional resources</span></span>

- <span data-ttu-id="b0e67-123">**Uruchamianie obrazu platformy Docker programu SQL Server w systemie Linux, Mac lub Windows** \\</span><span class="sxs-lookup"><span data-stu-id="b0e67-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** \\</span></span>
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="b0e67-124">**Połączenie i wykonywać zapytania programu SQL Server w systemie Linux przy użyciu narzędzia sqlcmd** \\</span><span class="sxs-lookup"><span data-stu-id="b0e67-124">**Connect and query SQL Server on Linux with sqlcmd** \\</span></span>
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="b0e67-125">Rozmieszczanie za pomocą danych testowych podczas uruchamiania aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="b0e67-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="b0e67-126">Aby dodać dane do bazy danych, podczas uruchamiania aplikacji, można dodać kod, podobnie do następującej metody Konfiguruj w klasie uruchamiania projektu interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="b0e67-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

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

<span data-ttu-id="b0e67-127">Poniższy kod w niestandardowej klasy CatalogContextSeed zostaną wyświetlone wszystkie dane.</span><span class="sxs-lookup"><span data-stu-id="b0e67-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="b0e67-128">Kiedy uruchamiasz testy integracji, sposób, aby wygenerować dane spójne z testów integracji jest przydatne.</span><span class="sxs-lookup"><span data-stu-id="b0e67-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="b0e67-129">Możliwość tworzenia wszystkiego, od początku, w tym wystąpienia programu SQL Server działającego w kontenerze, to doskonałe rozwiązanie dla środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="b0e67-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="b0e67-130">EF Core InMemory Database a baza danych programu SQL Server uruchomionego jako kontener</span><span class="sxs-lookup"><span data-stu-id="b0e67-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="b0e67-131">Innym dobrym wyborem podczas przeprowadzania testów polega na użyciu dostawca bazy danych programu Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="b0e67-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="b0e67-132">Tę konfigurację można określić w metodzie ConfigureServices klasy uruchamiania w projekcie interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="b0e67-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="b0e67-133">Istnieje jednak ważne catch.</span><span class="sxs-lookup"><span data-stu-id="b0e67-133">There is an important catch, though.</span></span> <span data-ttu-id="b0e67-134">Bazy danych w pamięci nie obsługuje wiele ograniczeń, które są specyficzne dla konkretnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b0e67-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="b0e67-135">Na przykład możesz dodać unikatowego indeksu dla kolumny w modelu platformy EF Core i napisać test względem bazy danych w pamięci w celu sprawdzenia, czy on nie zezwala na dodawanie zduplikowane wartości.</span><span class="sxs-lookup"><span data-stu-id="b0e67-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="b0e67-136">Jednak podczas korzystania z bazy danych w pamięci nie może obsługiwać indeksy unikatowe dla kolumny.</span><span class="sxs-lookup"><span data-stu-id="b0e67-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="b0e67-137">W związku z tym, bazy danych w pamięci nie zachowywać się tak samo jak rzeczywista baza danych programu SQL Server — nie nie emulować ograniczeń określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b0e67-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="b0e67-138">Nawet w takim przypadku baza danych w pamięci nadal jest użyteczne do testowania i tworzenia prototypów.</span><span class="sxs-lookup"><span data-stu-id="b0e67-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="b0e67-139">Ale jeśli chcesz utworzyć testy integracji dokładne, które weź pod uwagę zachowanie wykonania konkretnej bazy danych, należy użyć rzeczywistego bazy danych, takich jak program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b0e67-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="b0e67-140">W tym celu programem SQL Server w kontenerze jest doskonały wybór i bardziej precyzyjne niż dostawca bazy danych programu EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="b0e67-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="b0e67-141">Za pomocą usługi pamięć podręczna Redis uruchomionej w kontenerze</span><span class="sxs-lookup"><span data-stu-id="b0e67-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="b0e67-142">Możesz uruchomić pamięci podręcznej Redis w kontenerze, szczególnie w przypadku tworzenia i testowania oraz scenariuszy weryfikacji koncepcji.</span><span class="sxs-lookup"><span data-stu-id="b0e67-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="b0e67-143">Ten scenariusz jest wygodne, ponieważ masz wszystkie zależności systemem kontenerów — nie tylko dla maszyn lokalnych rozwoju, ale dla środowisk testowych w potoków ciągłej integracji/ciągłego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="b0e67-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="b0e67-144">Po uruchomieniu usługi Redis w środowisku produkcyjnym zaleca się wyszukać rozwiązanie o wysokiej dostępności, takich jak Redis platformy Microsoft Azure, która jest uruchamiana jako usługi PaaS (platforma jako usługa).</span><span class="sxs-lookup"><span data-stu-id="b0e67-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="b0e67-145">W kodzie wystarczy zmienić parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="b0e67-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="b0e67-146">Usługa redis zapewnia obrazu platformy Docker przy użyciu usługi Redis.</span><span class="sxs-lookup"><span data-stu-id="b0e67-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="b0e67-147">Ten obraz jest dostępny z usługi Docker Hub pod tym adresem URL:</span><span class="sxs-lookup"><span data-stu-id="b0e67-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/\_/redis/>

<span data-ttu-id="b0e67-148">Można bezpośrednio uruchomić kontener platformy Docker, Redis, wykonując następujące polecenie interfejsu wiersza polecenia platformy Docker w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="b0e67-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="b0e67-149">Obraz usługi Redis zawiera udostępniają: 6379 (port używany przez usługi Redis), więc standardowa łączenie kontenera udostępnienie jej automatycznie do połączonego kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b0e67-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="b0e67-150">W ramach aplikacji eShopOnContainers mikrousługi basket.api korzysta z pamięci podręcznej Redis uruchomionego jako kontener.</span><span class="sxs-lookup"><span data-stu-id="b0e67-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="b0e67-151">Ten kontener basket.data jest zdefiniowana jako części pliku z obsługą wielu kontenerów platformy docker-compose.yml, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b0e67-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="b0e67-152">Ten kod w docker-compose.yml definiuje kontener o nazwie basket.data na podstawie obrazu usługi redis i publikowania port 6379 wewnętrznie, co oznacza, że będą dostępne tylko z innych kontenerów w ramach hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b0e67-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="b0e67-153">Na koniec w pliku docker-compose.override.yml mikrousług basket.api dla przykładu w ramach aplikacji eShopOnContainers definiuje parametry połączenia do użycia dla tego kontenera Redis:</span><span class="sxs-lookup"><span data-stu-id="b0e67-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="b0e67-154">Jak wspomniano wcześniej, nazwa mikrousług "basket.data" został rozwiązany przez firmy docker wewnętrznej sieci DNS.</span><span class="sxs-lookup"><span data-stu-id="b0e67-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b0e67-155">[Poprzednie](multi-container-applications-docker-compose.md)
>[dalej](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="b0e67-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
