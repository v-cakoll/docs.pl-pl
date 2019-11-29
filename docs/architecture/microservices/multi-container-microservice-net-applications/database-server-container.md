---
title: Korzystanie z serwera bazy danych uruchomionego jako kontener
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Korzystasz z serwera bazy danych działającego jako kontener? tylko na potrzeby programowania! Dowiedz się, dlaczego.
ms.date: 10/02/2018
ms.openlocfilehash: 371d622dc39681edb0b52e723faccbf611b7797c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568429"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="9f2b6-104">Korzystanie z serwera bazy danych uruchomionego jako kontener</span><span class="sxs-lookup"><span data-stu-id="9f2b6-104">Using a database server running as a container</span></span>

<span data-ttu-id="9f2b6-105">Możesz mieć bazy danych (SQL Server, PostgreSQL, MySQL itp.) na zwykłych serwerach autonomicznych, w klastrach lokalnych lub w usługach PaaS Services w chmurze, takich jak Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="9f2b6-106">Jednak w środowiskach deweloperskich i testowych, które bazy danych działają jako kontenery są wygodne, ponieważ nie istnieje żadna zależność zewnętrzna i po prostu uruchomienie `docker-compose up` polecenie uruchamia całą aplikację.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="9f2b6-107">Posiadanie tych baz danych jako kontenerów jest również doskonałe dla testów integracji, ponieważ baza danych została uruchomiona w kontenerze i jest zawsze wypełniana tymi samymi przykładowymi danymi, dzięki czemu testy mogą być bardziej przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="9f2b6-108">SQL Server działa jako kontener z bazą danych z mikrousługą</span><span class="sxs-lookup"><span data-stu-id="9f2b6-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="9f2b6-109">W eShopOnContainers istnieje kontener o nazwie SQL. dane zdefiniowane w pliku [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , który działa SQL Server dla systemu Linux ze wszystkimi bazami danych SQL Server, które są zbędne dla mikrousług.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="9f2b6-110">(Możliwe jest również posiadanie jednego kontenera SQL Server dla każdej bazy danych, ale może to wymagać większej ilości pamięci przypisanej do platformy Docker). Ważnym punktem w mikrousług jest to, że każda mikrousługa jest właścicielem powiązanych danych, w związku z czym w tym przypadku jest związana z nią baza danych SQL.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="9f2b6-111">Jednak bazy danych mogą znajdować się w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="9f2b6-112">Kontener SQL Server w przykładowej aplikacji jest skonfigurowany przy użyciu następującego kodu YAML w pliku Docker-Compose. yml, który jest wykonywany podczas uruchamiania `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="9f2b6-113">Należy pamiętać, że kod YAML ma skonsolidowane informacje o konfiguracji z pliku Generic Docker-Compose. yml oraz pliku Docker-Compose. override. yml.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="9f2b6-114">(Zazwyczaj należy oddzielić ustawienia środowiska od podstawowej lub statycznej informacji powiązanej z obrazem SQL Server).</span><span class="sxs-lookup"><span data-stu-id="9f2b6-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="9f2b6-115">W podobny sposób, zamiast używać `docker-compose`, następujące polecenie `docker run` może uruchomić ten kontener:</span><span class="sxs-lookup"><span data-stu-id="9f2b6-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```console
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="9f2b6-116">Jednak w przypadku wdrażania aplikacji z wieloma kontenerami, takich jak eShopOnContainers, wygodniejsze jest użycie polecenia `docker-compose up`, aby wdrożyć wszystkie wymagane kontenery dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="9f2b6-117">Po pierwszym uruchomieniu tego kontenera SQL Server Kontener inicjuje SQL Server przy użyciu podania hasła.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="9f2b6-118">Gdy SQL Server jest uruchomiony jako kontener, możesz zaktualizować bazę danych, łącząc się za pośrednictwem dowolnego zwykłego połączenia SQL, takiego jak z SQL Server Management Studio, Visual Studio lub C\# Code.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="9f2b6-119">Aplikacja eShopOnContainers inicjuje każdą mikrousługą bazę danych z przykładowymi danymi, umieszczając je w danych podczas uruchamiania, jak wyjaśniono w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="9f2b6-120">Posiadanie SQL Server działającego jako kontenera nie jest samo przydatne w przypadku pokazu, w którym może nie mieć dostępu do wystąpienia SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="9f2b6-121">Jak zauważono, jest to również idealne rozwiązanie w środowiskach deweloperskich i testowych, dzięki czemu można łatwo uruchomić testy integracji zaczynające się od czystego obrazu SQL Server i znanych danych, umieszczając nowe przykładowe dane.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="9f2b6-122">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="9f2b6-122">Additional resources</span></span>

- <span data-ttu-id="9f2b6-123">**Uruchamianie obrazu SQL Server Docker w systemie Linux, Mac lub Windows** </span><span class="sxs-lookup"><span data-stu-id="9f2b6-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="9f2b6-124">**Łączenie i SQL Server on Linux zapytań przy użyciu narzędzia sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="9f2b6-124">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="9f2b6-125">Umieszczanie danych testowych przy uruchamianiu aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="9f2b6-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="9f2b6-126">Aby dodać dane do bazy danych podczas uruchamiania aplikacji, można dodać kod podobny do poniższego do metody Configure w klasie startowej projektu interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="9f2b6-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

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

<span data-ttu-id="9f2b6-127">Poniższy kod w niestandardowej klasie CatalogContextSeed wypełnia dane.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="9f2b6-128">Po uruchomieniu testów integracji istnieje możliwość generowania danych spójnych z testami integracji.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="9f2b6-129">Możliwość tworzenia wszystkiego od podstaw, w tym wystąpienia SQL Server działającego w kontenerze, doskonale sprawdza się w środowiskach testowych.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="9f2b6-130">EF Core bazę danych inMemory, a SQL Server działa jako kontener</span><span class="sxs-lookup"><span data-stu-id="9f2b6-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="9f2b6-131">Innym dobrym wyborem w przypadku uruchamiania testów jest użycie dostawcy bazy danych inMemory Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="9f2b6-132">Możesz określić tę konfigurację w metodzie ConfigureServices klasy Start w projekcie interfejsu API sieci Web:</span><span class="sxs-lookup"><span data-stu-id="9f2b6-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="9f2b6-133">Istnieje ważna połowa, chociaż.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-133">There is an important catch, though.</span></span> <span data-ttu-id="9f2b6-134">Baza danych w pamięci nie obsługuje wielu ograniczeń, które są specyficzne dla konkretnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="9f2b6-135">Na przykład możesz dodać unikatowy indeks do kolumny w modelu EF Core i napisać test do bazy danych w pamięci, aby sprawdzić, czy nie zezwala na dodanie zduplikowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="9f2b6-136">Ale w przypadku korzystania z bazy danych w pamięci nie można obsłużyć unikatowych indeksów w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="9f2b6-137">W związku z tym baza danych znajdująca się w pamięci nie zachowuje się dokładnie tak samo jak rzeczywista SQL Server baza danych — nie emuluje ograniczeń specyficznych dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="9f2b6-138">Nawet w takim przypadku baza danych znajdująca się w pamięci jest nadal przydatna do testowania i tworzenia prototypów.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="9f2b6-139">Jeśli jednak chcesz utworzyć dokładne testy integracji, które uwzględniają zachowanie określonej implementacji bazy danych, musisz użyć prawdziwej bazy danych, takiej jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="9f2b6-140">W tym celu uruchomienie SQL Server w kontenerze jest doskonałym wyborem i jest bardziej dokładne niż dostawca bazy danych inMemory EF Core.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="9f2b6-141">Używanie usługi pamięci podręcznej Redis działającej w kontenerze</span><span class="sxs-lookup"><span data-stu-id="9f2b6-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="9f2b6-142">Można uruchamiać Redis w kontenerze, szczególnie w przypadku projektowania i testowania oraz dla scenariuszy weryfikacji koncepcji.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="9f2b6-143">Ten scenariusz jest wygodny, ponieważ możesz mieć wszystkie zależności działające w kontenerach — nie tylko dla lokalnych maszyn deweloperskich, ale dla środowisk testowych w potokach ciągłej integracji/ciągłego dostarczania.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="9f2b6-144">Jednak po uruchomieniu Redis w środowisku produkcyjnym lepiej jest wyszukać rozwiązanie wysokiej dostępności, takie jak Redis Microsoft Azure, które działa jako PaaS (platforma jako usługa).</span><span class="sxs-lookup"><span data-stu-id="9f2b6-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="9f2b6-145">W kodzie należy jedynie zmienić parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="9f2b6-146">Redis udostępnia obraz platformy Docker z Redis.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="9f2b6-147">Ten obraz jest dostępny z poziomu usługi Docker Hub pod tym adresem URL:</span><span class="sxs-lookup"><span data-stu-id="9f2b6-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="9f2b6-148">Można bezpośrednio uruchomić kontener Docker Redis, wykonując następujące polecenie Docker CLI w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="9f2b6-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="9f2b6-149">Obraz Redis obejmuje Uwidacznianie: 6379 (port używany przez Redis), więc łączenie kontenerów standardowych będzie automatycznie dostępne dla połączonych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="9f2b6-150">W programie eShopOnContainers Usługa Service w koszyku. API używa pamięci podręcznej Redis działającej jako kontener.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="9f2b6-151">Ten koszyk. kontener danych jest definiowany jako część pliku Docker-Compose. yml z wielokontenerem, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9f2b6-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="9f2b6-152">Ten kod w Docker-Compose. yml definiuje kontener o nazwie koszyk. dane oparte na obrazie Redis i publikują port 6379 wewnętrznie, co oznacza, że będzie dostępny tylko z innych kontenerów uruchomionych w ramach hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="9f2b6-153">Na koniec w pliku Docker-Compose. override. yml, The koszyk. API mikrousługi dla przykładu eShopOnContainers definiuje parametry połączenia do użycia dla tego kontenera Redis:</span><span class="sxs-lookup"><span data-stu-id="9f2b6-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="9f2b6-154">Jak wspomniano wcześniej, nazwa "koszyka mikrousług" jest rozpoznawana przez system DNS w sieci wewnętrznej platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="9f2b6-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9f2b6-155">[Poprzednie](multi-container-applications-docker-compose.md)
>[dalej](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="9f2b6-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
