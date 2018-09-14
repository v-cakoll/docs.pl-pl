---
title: Tworzenie prostego mikrousługi CRUD na podstawie danych
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Tworzenie prostego mikrousługi CRUD na podstawie danych
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: b443f1b066d3c8ef0e798206510616aace32b377
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617146"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="17b93-103">Tworzenie prostego mikrousługi CRUD na podstawie danych</span><span class="sxs-lookup"><span data-stu-id="17b93-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="17b93-104">Tej sekcji przedstawiono sposób w celu utworzenia prostej mikrousługi, który wykonuje tworzenia, odczytu, aktualizacji i operacje usuwania (CRUD) w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="17b93-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="17b93-105">Projektowanie proste mikrousługi CRUD</span><span class="sxs-lookup"><span data-stu-id="17b93-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="17b93-106">Z punktu widzenia projektowania tego rodzaju konteneryzowanych mikrousług jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="17b93-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="17b93-107">Być może rozwiązać ten problem jest proste lub prawdopodobnie implementacja jest tylko weryfikacji koncepcji.</span><span class="sxs-lookup"><span data-stu-id="17b93-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="17b93-108">**Rysunek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="17b93-108">**Figure 8-4**.</span></span> <span data-ttu-id="17b93-109">Wewnętrzny projektowanie pod kątem prostego mikrousługi CRUD</span><span class="sxs-lookup"><span data-stu-id="17b93-109">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="17b93-110">Przykładem tego rodzaju usługi simple dysk danych jest mikrousług katalogu w ramach aplikacji eShopOnContainers przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17b93-110">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="17b93-111">Tego rodzaju usługi implementuje wszystkie jej funkcje w jednym projekcie internetowego interfejsu API platformy ASP.NET Core, która zawiera klasy służące do jej modelu danych, jej logiki biznesowej i jego kod dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="17b93-111">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="17b93-112">Jest również przechowuje swoje powiązane dane w bazie danych, uruchomione w programie SQL Server (zgodnie z innego kontenera do celów deweloperskich i testowych), ale może być również regularne dowolnego hosta programu SQL Server, jak pokazano na rysunku 8-5.</span><span class="sxs-lookup"><span data-stu-id="17b93-112">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="17b93-113">**Rysunek 8-5**.</span><span class="sxs-lookup"><span data-stu-id="17b93-113">**Figure 8-5**.</span></span> <span data-ttu-id="17b93-114">Proste data-driven/CRUD mikrousługi projektowania</span><span class="sxs-lookup"><span data-stu-id="17b93-114">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="17b93-115">Podczas tworzenia tego rodzaju usługi wystarczy [platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/) i ORM lub interfejs API dostępu do danych, takich jak [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="17b93-115">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="17b93-116">Można również wygenerować [Swagger](https://swagger.io/) automatycznie za pomocą metadanych [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) można podać opis co oferuje usługi, jak wyjaśniono w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="17b93-116">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="17b93-117">Należy pamiętać, że używany jest serwer bazy danych, takich jak SQL Server w kontenerze platformy Docker to idealne narzędzie do środowiska programowania, ponieważ wszystkie zależności może zawierać maksymalnie i uruchamiania bez konieczności aprowizowania bazy danych w chmurze lub lokalnie.</span><span class="sxs-lookup"><span data-stu-id="17b93-117">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="17b93-118">Może to być bardzo wygodne, gdy integracji Uruchamianie testów.</span><span class="sxs-lookup"><span data-stu-id="17b93-118">This is very convenient when running integration tests.</span></span> <span data-ttu-id="17b93-119">Jednak w środowiskach produkcyjnych, uruchamianie serwera bazy danych w kontenerze nie jest zalecane, ponieważ zwykle nie uzyskasz wysokiej dostępności za pomocą tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="17b93-119">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="17b93-120">W środowisku produkcyjnym na platformie Azure zaleca się korzystanie z bazy danych SQL Azure lub innych technologii baz danych, zapewniające wysoką dostępność i wysoką skalowalność.</span><span class="sxs-lookup"><span data-stu-id="17b93-120">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="17b93-121">Na przykład aby podejściu NoSQL, możesz wybrać bazy danych DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="17b93-121">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="17b93-122">Na koniec, edytując plik Dockerfile i docker-compose.yml plików metadanych, możesz skonfigurować sposób tworzenia obrazu tego kontenera — podstawowego obrazu będzie używać oraz projektowania ustawienia, takie jak nazwy wewnętrzne i zewnętrzne i portów TCP.</span><span class="sxs-lookup"><span data-stu-id="17b93-122">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="17b93-123">Implementowanie prostego mikrousługi CRUD za pomocą programu ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="17b93-123">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="17b93-124">Aby zaimplementować prosty mikrousługi CRUD przy użyciu platformy .NET Core i Visual Studio, możesz rozpocząć od utworzenia prostego projektu internetowego interfejsu API platformy ASP.NET Core (uruchomionej na platformie .NET Core, dzięki czemu może działać na hosta platformy Docker w systemie Linux), jak pokazano na rysunku 8-6.</span><span class="sxs-lookup"><span data-stu-id="17b93-124">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="17b93-125">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="17b93-125">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="17b93-126">**Rysunek 8 – 6**.</span><span class="sxs-lookup"><span data-stu-id="17b93-126">**Figure 8-6**.</span></span> <span data-ttu-id="17b93-127">Tworzenie projektu internetowego interfejsu API platformy ASP.NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="17b93-127">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="17b93-128">Po utworzeniu projektu, można zaimplementować kontrolerach MVC, tak jak w innych projektów interfejsu API sieci Web, przy użyciu interfejsu API programu Entity Framework lub innym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="17b93-128">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="17b93-129">W nowym projekcie interfejsu API sieci Web widać, zależności tylko że w tym mikrousług jest programu ASP.NET Core, sam.</span><span class="sxs-lookup"><span data-stu-id="17b93-129">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="17b93-130">Wewnętrznie, w ramach `Microsoft.AspNetCore.All` zależności, odwołuje się ona do programu Entity Framework i wiele innych pakietów .NET Core Nuget, jak pokazano w rysunek 8 – 7.</span><span class="sxs-lookup"><span data-stu-id="17b93-130">Internally, within the `Microsoft.AspNetCore.All` dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="17b93-131">**Rysunek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="17b93-131">**Figure 8-7**.</span></span> <span data-ttu-id="17b93-132">Zależności w prostych mikrousługi CRUD internetowego interfejsu API</span><span class="sxs-lookup"><span data-stu-id="17b93-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="17b93-133">Implementowanie usług interfejsu API sieci Web CRUD przy użyciu platformy Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="17b93-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="17b93-134">Entity Framework (EF) Core to lekkie, rozszerzalne, i technologii dostępu do popularnych danych Entity Framework w wersji dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="17b93-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="17b93-135">EF Core to maper obiektowo relacyjny (ORM), który umożliwia deweloperom platformy .NET do pracy z bazą danych, używając obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="17b93-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="17b93-136">Mikrousługi katalogu korzysta EF i dostawcy programu SQL Server, ponieważ jego bazy danych jest uruchomiona w kontenerze za pomocą programu SQL Server dla obrazu platformy Docker w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="17b93-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="17b93-137">Jednak bazy danych można wdrożyć do dowolnego programu SQL Server, takich jak Windows w środowisku lokalnym lub bazy danych SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="17b93-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="17b93-138">Jedyną czynnością, którą trzeba zmienić to parametry połączenia w mikrousługach interfejsu API sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="17b93-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>


#### <a name="the-data-model"></a><span data-ttu-id="17b93-139">Model danych</span><span class="sxs-lookup"><span data-stu-id="17b93-139">The data model</span></span>

<span data-ttu-id="17b93-140">Z programem EF Core dostęp do danych odbywa się przy użyciu modelu.</span><span class="sxs-lookup"><span data-stu-id="17b93-140">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="17b93-141">Model składa się z klas jednostek i pochodnej kontekstu, który reprezentuje sesję z bazą danych, dzięki czemu zapytania i zapisywać dane.</span><span class="sxs-lookup"><span data-stu-id="17b93-141">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="17b93-142">Możesz wygenerować model z istniejącej bazy danych, ręcznie code model, aby dopasować bazy danych lub użyć migracje EF utworzyć bazę danych z modelu (i rozwój go jak model zmienia się wraz z upływem czasu).</span><span class="sxs-lookup"><span data-stu-id="17b93-142">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="17b93-143">Dla mikrousług katalogu używamy najnowsze podejście.</span><span class="sxs-lookup"><span data-stu-id="17b93-143">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="17b93-144">Widać przykład klasy CatalogItem jednostki w poniższym przykładzie kodu jest proste zwykłe stare obiektu CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) Klasa jednostki.</span><span class="sxs-lookup"><span data-stu-id="17b93-144">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

<span data-ttu-id="17b93-145">Należy również DbContext, który reprezentuje sesję z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="17b93-145">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="17b93-146">Dla mikrousług wykazu klasa CatalogContext pochodzi z klasy bazowej typu DbContext, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="17b93-146">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

<span data-ttu-id="17b93-147">Masz dodatkowe `DbContext` implementacji.</span><span class="sxs-lookup"><span data-stu-id="17b93-147">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="17b93-148">Na przykład w mikrousługach Catalog.API próbki, istnieje sekundy `DbContext` o nazwie `CatalogContextSeed` gdzie automatycznie wypełnia przykładowe dane po raz pierwszy próbuje dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="17b93-148">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="17b93-149">Ta metoda jest przydatna, dane demonstracyjne i automatyczne scenariuszy testowych, jak również.</span><span class="sxs-lookup"><span data-stu-id="17b93-149">This method is useful for demo data and for automated testing scenarios, as well.</span></span> <span data-ttu-id="17b93-150">W ramach `DbContext`, możesz użyć `OnModelCreating` metodę w celu dostosowania mapowania jednostek w bazie danych i obiektów przy użyciu i innych [punkty rozszerzeń EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="17b93-150">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings with and other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="17b93-151">Wykonywanie zapytania o dane z kontrolerów interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="17b93-151">Querying data from Web API controllers</span></span>

<span data-ttu-id="17b93-152">Wystąpienia klas jednostek zwykle są pobierane z bazy danych przy użyciu Language Integrated Query (LINQ), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="17b93-152">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context, 
                             IOptionsSnapshot<CatalogSettings> settings,
                             ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10, 
                                           [FromQuery]int pageIndex = 0)

    {
        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    } 
    //...
}
```

##### <a name="saving-data"></a><span data-ttu-id="17b93-153">Zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="17b93-153">Saving data</span></span>

<span data-ttu-id="17b93-154">Dane są tworzone, usunięte i zmodyfikowane w bazie danych za pomocą wystąpień klas jednostek.</span><span class="sxs-lookup"><span data-stu-id="17b93-154">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="17b93-155">Można dodać kod, takich jak ustaloną następująco (danych testowych, w tym przypadku) z kontrolerami interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="17b93-155">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="17b93-156">Wstrzykiwanie zależności w kontrolerów platformy ASP.NET Core i interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="17b93-156">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="17b93-157">W programie ASP.NET Core można użyć wstrzykiwanie zależności (DI) poza pole.</span><span class="sxs-lookup"><span data-stu-id="17b93-157">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="17b93-158">Nie należy skonfigurować kontener Inwersja kontroli (IoC) innych firm, mimo że preferowanego kontenera IoC można podłączyć do infrastruktury platformy ASP.NET Core, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="17b93-158">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="17b93-159">W takim przypadku oznacza to, że należy bezpośrednio wstrzyknąć wymagane DBContext EF lub dodatkowe przechowalnie za pośrednictwem konstruktora kontrolera.</span><span class="sxs-lookup"><span data-stu-id="17b93-159">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="17b93-160">W przykładzie powyżej `CatalogController` klasy, firma Microsoft jest wstawianie obiektu `CatalogContext` wpisz oraz innych obiektów za pomocą `CatalogController()` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="17b93-160">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="17b93-161">Ważne konfiguracji, aby skonfigurować w projekcie interfejsu API sieci Web jest rejestrowanie klasy DbContext do kontenera IoC tej usługi.</span><span class="sxs-lookup"><span data-stu-id="17b93-161">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="17b93-162">Zwykle są zatem w `Startup` klasy przez wywołanie metody `services.AddDbContext<DbContext>()` metody w ramach `ConfigureServices()` metodzie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="17b93-162">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
                   typeof(Startup).
                    GetTypeInfo().
                     Assembly.
                      GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...

}
```

### <a name="additional-resources"></a><span data-ttu-id="17b93-163">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="17b93-163">Additional resources</span></span>

-   <span data-ttu-id="17b93-164">**Wykonywanie zapytania o dane**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="17b93-164">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="17b93-165">**Zapisywanie danych**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="17b93-165">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="17b93-166">Zmienne ciągów i środowisko połączenia bazy danych używanych przez kontenery platformy Docker</span><span class="sxs-lookup"><span data-stu-id="17b93-166">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="17b93-167">Można użyć ustawień platformy ASP.NET Core i Dodaj właściwość ConnectionString do pliku settings.json, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="17b93-167">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```csharp
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

<span data-ttu-id="17b93-168">Plik settings.json może mieć wartości domyślnych dla właściwości ConnectionString lub dla wszystkich innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="17b93-168">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="17b93-169">Jednak te właściwości zostaną zastąpione przez wartości zmiennych środowiskowych, które są określone w pliku docker-compose.override.yml, korzystając z platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="17b93-169">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="17b93-170">Na podstawie własnych plików docker-compose.yml i docker-compose.override.yml można zainicjować tych zmiennych środowiskowych, że platforma Docker skonfiguruje je jako zmienne środowiskowe systemu operacyjnego, jak pokazano w następującym pliku docker-compose.override.yml (połączenia ciąg i innych wierszy opakowywać w tym przykładzie, ale nie będzie zawijany w pliku kodu).</span><span class="sxs-lookup"><span data-stu-id="17b93-170">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own code file).</span></span>

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

<span data-ttu-id="17b93-171">Pliki docker-compose.yml na poziomie rozwiązania nie są tylko bardziej elastyczny niż pliki konfiguracji na poziomie projektu lub mikrousług, ale również bardziej bezpieczne, jeśli zastąpisz zmienne środowiskowe zadeklarowane na pliki docker-compose przy użyciu wartości ustawione na Twoje narzędzia wdrażania, np. z zadania związane z wdrażaniem usługi Azure DevOps usługi Docker.</span><span class="sxs-lookup"><span data-stu-id="17b93-171">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span> 

<span data-ttu-id="17b93-172">Na koniec można uzyskać tę wartość w kodzie za pomocą konfiguracji\["ConnectionString"\], jak pokazano w metodzie ConfigureServices w wcześniejszym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="17b93-172">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="17b93-173">W środowiskach produkcyjnych, może być poznać dodatkowe sposoby na temat przechowywania wpisów tajnych, takich jak parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="17b93-173">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="17b93-174">Zwykle, będą zarządzane przez wybranego koordynatora, jak za pomocą [Docker Swarm zarządzania wpisami tajnymi](https://docs.docker.com/engine/swarm/secrets/).</span><span class="sxs-lookup"><span data-stu-id="17b93-174">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="17b93-175">Implementowanie przechowywania wersji interfejsów API sieci Web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="17b93-175">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="17b93-176">Po zmianie wymagań biznesowych, mogą być dodawane nowe kolekcji zasobów może się zmieniać relacje między zasobami i struktury danych w obszarze zasoby mogą zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="17b93-176">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="17b93-177">Aktualizowanie interfejsu API sieci Web, do obsługi nowych wymagań jest stosunkowo prosta, ale należy wziąć pod uwagę wpływ, mających takie zmiany na aplikacje klienckie korzystające z interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="17b93-177">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="17b93-178">Mimo że dla deweloperów, projektowania i implementowania internetowego interfejsu API ma pełną kontrolę nad tym Interfejsem, deweloper nie ma tego samego stopnia kontroli nad aplikacji klienckich, które może być kompilowany przez inne podmioty.</span><span class="sxs-lookup"><span data-stu-id="17b93-178">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="17b93-179">Kontrola wersji umożliwia wskazanie funkcji i zasobów udostępnianych internetowego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="17b93-179">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="17b93-180">Aplikacja kliencka można przesłać żądania do określonej wersji funkcji lub zasobu.</span><span class="sxs-lookup"><span data-stu-id="17b93-180">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="17b93-181">Istnieją różne podejścia do implementowania obsługi wersji:</span><span class="sxs-lookup"><span data-stu-id="17b93-181">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="17b93-182">Identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="17b93-182">URI versioning</span></span>

-   <span data-ttu-id="17b93-183">Przechowywanie wersji parametrów zapytania</span><span class="sxs-lookup"><span data-stu-id="17b93-183">Query string versioning</span></span>

-   <span data-ttu-id="17b93-184">Nagłówka</span><span class="sxs-lookup"><span data-stu-id="17b93-184">Header versioning</span></span>

<span data-ttu-id="17b93-185">Ciąg zapytania i identyfikatora URI są najprostszej implementacji.</span><span class="sxs-lookup"><span data-stu-id="17b93-185">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="17b93-186">Nagłówek wersji to dobra metoda.</span><span class="sxs-lookup"><span data-stu-id="17b93-186">Header versioning is a good approach.</span></span> <span data-ttu-id="17b93-187">Jednak wersji nagłówka nie jako jawne i prostego jako identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="17b93-187">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="17b93-188">Ponieważ adres URL wersji najprostszy i najbardziej jawne, przykładowej aplikacji w ramach aplikacji eShopOnContainers używa identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="17b93-188">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="17b93-189">Za pomocą identyfikatora URI do przechowywania wersji, tak jak w ramach aplikacji eShopOnContainers przykładowej aplikacji za każdym razem zmodyfikować internetowego interfejsu API lub zmianie schematu zasobów, należy dodać numer wersji do identyfikatorów URI poszczególnych zasobów.</span><span class="sxs-lookup"><span data-stu-id="17b93-189">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="17b93-190">Istniejące identyfikatory URI powinny nadal działać jak wcześniej, zwracając zasoby, które są zgodne ze schematem, który odpowiada żądanej wersji.</span><span class="sxs-lookup"><span data-stu-id="17b93-190">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="17b93-191">Jak pokazano w poniższym przykładzie kodu, można ustawić wersję za pomocą atrybutu tras w interfejsie API sieci Web, co sprawia, że wersja jest jawne w identyfikatorze URI (wersja 1, w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="17b93-191">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="17b93-192">Opisany mechanizm kontroli wersji jest prosty i zależy od serwera kieruje żądania do odpowiednich punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="17b93-192">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="17b93-193">Jednak dla bardziej zaawansowanych wersji i najlepszą metodę, gdy przy użyciu usługi REST, należy użyć hipermediach i zaimplementować [HATEOAS (Hypertext as Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="17b93-193">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="17b93-194">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="17b93-194">Additional resources</span></span>

-   <span data-ttu-id="17b93-195">**Scott Hanselman. Przechowywanie wersji internetowy interfejs API RESTful platformy ASP.NET Core łatwe**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="17b93-195">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="17b93-196">**Przechowywanie wersji internetowego interfejsu API RESTful**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span><span class="sxs-lookup"><span data-stu-id="17b93-196">**Versioning a RESTful web API**
[*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span></span>

-   <span data-ttu-id="17b93-197">**Roy Fielding. Przechowywanie wersji, Hipermediach i REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="17b93-197">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="17b93-198">Generowanie metadanych opis struktury Swagger z internetowego interfejsu API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="17b93-198">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="17b93-199">[Struktury swagger](https://swagger.io/) jest framework powszechnie używane typu open source objęte dużego ekosystemu narzędzi, które ułatwia projektowanie, kompilowanie, dokument i używanie interfejsów API RESTful.</span><span class="sxs-lookup"><span data-stu-id="17b93-199">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="17b93-200">Staje się standardu dla domeny metadane opisu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="17b93-200">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="17b93-201">Powinny zawierać metadane struktury Swagger z dowolnego rodzaju mikrousłudze oraz mikrousług opartego na danych lub bardziej zaawansowane mikrousług opartego na domenach (jak wyjaśniono w poniższej sekcji).</span><span class="sxs-lookup"><span data-stu-id="17b93-201">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="17b93-202">Serce struktury Swagger jest specyfikacją struktury Swagger, czyli metadane opisu interfejsu API w pliku JSON lub YAML.</span><span class="sxs-lookup"><span data-stu-id="17b93-202">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="17b93-203">Specyfikacja tworzy RESTful kontrakt interfejsu API, szczegółowych informacji na temat wszystkich jej zasobów i operacji w obu readable człowieka i machine formacie umożliwiające łatwe projektowanie, odnajdywania i integracji.</span><span class="sxs-lookup"><span data-stu-id="17b93-203">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="17b93-204">Specyfikacja to podstawa specyfikację OpenAPI (OAS) i jest tworzone w otwarte, przejrzyste i współpracy społeczności, aby ustandaryzować sposób, w jaki zdefiniowano interfejsów RESTful.</span><span class="sxs-lookup"><span data-stu-id="17b93-204">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="17b93-205">Specyfikacja definiuje strukturę jak usługi mogą być wykrywane i jak zrozumieć jej możliwości.</span><span class="sxs-lookup"><span data-stu-id="17b93-205">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="17b93-206">Aby uzyskać więcej informacji, w tym edytora sieci web i przykłady specyfikacji Swagger z firm, takich jak Spotify, Uber, Slack i firmy Microsoft, w witrynie programu Swagger (<https://swagger.io/>).</span><span class="sxs-lookup"><span data-stu-id="17b93-206">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io/>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="17b93-207">Dlaczego warto używać struktury Swagger?</span><span class="sxs-lookup"><span data-stu-id="17b93-207">Why use Swagger?</span></span>

<span data-ttu-id="17b93-208">Poniżej przedstawiono główne powody generować metadane programu Swagger dla interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="17b93-208">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="17b93-209">**Możliwości dla innych produktów, automatycznie korzystać i integracja interfejsów API**.</span><span class="sxs-lookup"><span data-stu-id="17b93-209">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="17b93-210">Wielu produktów i [narzędzi komercyjnych](https://swagger.io/commercial-tools/) i wielu [bibliotek i platform](https://swagger.io/open-source-integrations/) obsługują strukturę Swagger.</span><span class="sxs-lookup"><span data-stu-id="17b93-210">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="17b93-211">Firma Microsoft ma wysokiego poziomu produktów i narzędzi, które automatycznie mogą wykorzystywać struktury Swagger interfejsy API oparte na, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="17b93-211">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="17b93-212">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="17b93-212">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="17b93-213">Możesz automatycznie wygenerować klasy klienta platformy .NET do wywoływania struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="17b93-213">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="17b93-214">To narzędzie można używać z interfejsu wiersza polecenia i integruje się również z programem Visual Studio dla łatwą w użyciu przy użyciu graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="17b93-214">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="17b93-215">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="17b93-215">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="17b93-216">Można automatycznie [użycia i integracji interfejsu API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) do ogólny przepływ pracy Microsoft Flow bez umiejętności programowania wymagane.</span><span class="sxs-lookup"><span data-stu-id="17b93-216">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="17b93-217">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="17b93-217">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="17b93-218">Będzie można korzystać z interfejsu API automatycznie [aplikacji mobilnych w usłudze PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) utworzonych za pomocą [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), nawet bez znajomości programowania wymagane.</span><span class="sxs-lookup"><span data-stu-id="17b93-218">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="17b93-219">[Usługa Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="17b93-219">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="17b93-220">Można automatycznie [użycia i integracji interfejsu API w aplikacji usługi Azure App Service Logic](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), nawet bez znajomości programowania wymagane.</span><span class="sxs-lookup"><span data-stu-id="17b93-220">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="17b93-221">**Możliwość automatycznego generowania dokumentacji interfejsu API**.</span><span class="sxs-lookup"><span data-stu-id="17b93-221">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="17b93-222">Po utworzeniu na dużą skalę interfejsów API RESTful, takie jak złożone aplikacje oparte na mikrousługach, będzie konieczna Obsługa wielu punktów końcowych przy użyciu różne modele danych używane w ładunkami żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="17b93-222">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="17b93-223">O prawidłowa dokumentacja, posiadanie solid Eksplorator interfejsu API, jak można uzyskać w strukturze Swagger, jest kluczem do sukcesu interfejsu API i przyjęcia rozwiązania przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="17b93-223">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="17b93-224">Metadane programu swagger w to, co Microsoft Flow, PowerApps i Azure Logic Apps umożliwia zrozumienie, jak używać interfejsów API i połączyć się z nimi.</span><span class="sxs-lookup"><span data-stu-id="17b93-224">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="17b93-225">Jak zautomatyzować struktury Swagger interfejsu API generowania metadanych przy użyciu pakietu Swashbuckle NuGet</span><span class="sxs-lookup"><span data-stu-id="17b93-225">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="17b93-226">Generowanie metadanych struktury Swagger ręcznie (w pliku JSON lub YAML) może być uciążliwe pracy.</span><span class="sxs-lookup"><span data-stu-id="17b93-226">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="17b93-227">Jednak można zautomatyzować odnajdywania interfejsu API usług interfejsu API sieci Web platformy ASP.NET przy użyciu [pakietu Swashbuckle NuGet](https://aka.ms/swashbuckledotnetcore) do dynamicznego generowania metadanych interfejsu API struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="17b93-227">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="17b93-228">Pakiet Swashbuckle generuje automatycznie metadanych struktury Swagger dla projektów ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="17b93-228">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="17b93-229">Obsługuje projekty ASP.NET Core Web API i tradycyjne ASP.NET Web API i innych wersji, takich jak aplikacji interfejsu API platformy Azure, aplikacji mobilnej platformy Azure, Azure Service Fabric mikrousług oparte na programie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="17b93-229">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="17b93-230">Obsługuje ona również zwykły wdrożonych kontenerów, podobnie jak w aplikacji odwołanie do interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="17b93-230">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="17b93-231">Pakiet Swashbuckle łączy Eksplorator interfejsu API i struktury Swagger lub [interfejs użytkownika struktury swagger](https://github.com/swagger-api/swagger-ui) zapewnia zaawansowane odnajdywania i dokumentacji komfort klientom interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="17b93-231">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="17b93-232">Oprócz silnik generator metadanych struktury Swagger Swashbuckle zawiera osadzony wersję struktury swagger interfejsu użytkownika, który go automatycznie posłużą się po zainstalowaniu pakietu Swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="17b93-232">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="17b93-233">Oznacza to, że mogą uzupełniać interfejsu API dzięki nieuprzywilejowany odnajdywania interfejsu użytkownika, aby pomóc deweloperom korzystanie z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="17b93-233">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="17b93-234">Wymaga niewielką ilość kodu i obsługi, ponieważ jest automatycznie generowany, co pozwala skupić się na tworzeniu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="17b93-234">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="17b93-235">Wynik dla Eksplorator interfejsu API będzie wyglądać jak rysunek 8-8.</span><span class="sxs-lookup"><span data-stu-id="17b93-235">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="17b93-236">**Rysunek 8-8**.</span><span class="sxs-lookup"><span data-stu-id="17b93-236">**Figure 8-8**.</span></span> <span data-ttu-id="17b93-237">Eksplorator interfejsu API narzędzia Swashbuckle oparte na metadanych struktury Swagger — w ramach aplikacji eShopOnContainers katalogu mikrousług</span><span class="sxs-lookup"><span data-stu-id="17b93-237">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="17b93-238">Eksplorator interfejsu API nie jest najważniejsza rzecz, w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="17b93-238">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="17b93-239">Po utworzeniu internetowego interfejsu API, który można opisania siebie w metadanych struktury Swagger, interfejsu API można bezproblemowo z narzędzi opartych na strukturze Swagger, takich jak generatorów kodu klasy serwera proxy klienta, które mogą współpracować z wieloma platformami.</span><span class="sxs-lookup"><span data-stu-id="17b93-239">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="17b93-240">Na przykład, jak wspomniano [AutoRest](https://github.com/Azure/AutoRest) automatycznie wygeneruje klasy klienta platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="17b93-240">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="17b93-241">Ale dodatkowe narzędzia, takie jak [generowanie kodu struktury swagger](https://github.com/swagger-api/swagger-codegen) są również dostępne, która zezwala na generowanie kodu klienta interfejsu API biblioteki, serwera wycinków i dokumentacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="17b93-241">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="17b93-242">Obecnie narzędzia Swashbuckle składa się z kilku wewnętrznych pakietów NuGet w obszarze wysokiego poziomu meta-package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) wersji 1.0.0 lub nowszym w przypadku aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="17b93-242">Currently, Swashbuckle consists of several internal NuGet packages under the high-level meta-package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) version 1.0.0 or later for ASP.NET Core applications.</span></span>

<span data-ttu-id="17b93-243">Po zainstalowaniu tych pakietów NuGet w projekcie interfejsu API sieci Web, należy skonfigurować struktury Swagger w klasie uruchamiania zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="17b93-243">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new Swashbuckle.AspNetCore.Swagger.Info
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample",
                TermsOfService = "Terms Of Service"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

<span data-ttu-id="17b93-244">Po zakończeniu tej operacji możesz uruchomić aplikację, a następnie Przeglądaj następujących JSON programu Swagger i interfejs użytkownika punktów końcowych przy użyciu adresów URL, takie jak te:</span><span class="sxs-lookup"><span data-stu-id="17b93-244">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

<span data-ttu-id="17b93-245">Widać wcześniej wygenerowany interfejsu użytkownika tworzone przez pakiet Swashbuckle dla adresu URL typu http://&lt;adres url katalogu głównego &gt; /swagger/interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="17b93-245">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="17b93-246">W rysunek 8 – 9 widać również sposób testowania dowolnej metody interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="17b93-246">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="17b93-247">**Rysunek 8 – 9**.</span><span class="sxs-lookup"><span data-stu-id="17b93-247">**Figure 8-9**.</span></span> <span data-ttu-id="17b93-248">Interfejs użytkownika Swashbuckle testowania metody interfejsu API elementów/katalogu</span><span class="sxs-lookup"><span data-stu-id="17b93-248">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="17b93-249">Rysunek 8 – 10 Wyświetla metadane JSON programu Swagger generowane na podstawie mikrousług w ramach aplikacji eShopOnContainers (czyli narzędzia korzystają poniżej) na żądanie &lt;adres url katalogu głównego&gt;przy użyciu /swagger/v1/swagger.json [NarzędziaPostman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="17b93-249">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="17b93-250">**Rysunek 8 – 10**.</span><span class="sxs-lookup"><span data-stu-id="17b93-250">**Figure 8-10**.</span></span> <span data-ttu-id="17b93-251">Metadane JSON programu swagger</span><span class="sxs-lookup"><span data-stu-id="17b93-251">Swagger JSON metadata</span></span>

<span data-ttu-id="17b93-252">Jest to proste.</span><span class="sxs-lookup"><span data-stu-id="17b93-252">It is that simple.</span></span> <span data-ttu-id="17b93-253">A ponieważ automatycznie jest generowany, po dodaniu więcej funkcji do interfejsu API będzie się zwiększać metadanych struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="17b93-253">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="17b93-254">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="17b93-254">Additional resources</span></span>

-   <span data-ttu-id="17b93-255">**Strony sieci Web ASP.NET API pomocy korzystające z programu Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="17b93-255">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="17b93-256">[Poprzednie](microservice-application-design.md)
[dalej](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="17b93-256">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
