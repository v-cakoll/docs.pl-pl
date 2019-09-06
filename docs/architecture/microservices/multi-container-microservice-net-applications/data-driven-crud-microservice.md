---
title: Tworzenie prostej mikrousługi CRUD na podstawie danych
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z tworzeniem prostej mikrousługi CRUD (opartej na danych) w kontekście aplikacji mikrousług.
ms.date: 01/07/2019
ms.openlocfilehash: 53aba727c8dae35df8b34bc1558c0cc390fe2014
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296663"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="76b2b-103">Tworzenie prostej mikrousługi CRUD na podstawie danych</span><span class="sxs-lookup"><span data-stu-id="76b2b-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="76b2b-104">W tej części przedstawiono sposób tworzenia prostej mikrousługi, która wykonuje operacje tworzenia, odczytu, aktualizacji i usuwania (CRUD) w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="76b2b-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="76b2b-105">Projektowanie prostej mikrousługi CRUD</span><span class="sxs-lookup"><span data-stu-id="76b2b-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="76b2b-106">Z punktu widzenia projektu ten typ mikrousługi kontenera jest bardzo prosty.</span><span class="sxs-lookup"><span data-stu-id="76b2b-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="76b2b-107">Prawdopodobnie problem, który należy rozwiązać, jest prosty lub że implementacja jest tylko dowodem koncepcji.</span><span class="sxs-lookup"><span data-stu-id="76b2b-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Prosta CRUD mikrousługa jest wewnętrznym wzorcem projektu.](./media/image4.png)

<span data-ttu-id="76b2b-109">**Rysunek 6-4**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-109">**Figure 6-4**.</span></span> <span data-ttu-id="76b2b-110">Wewnętrzny projekt dla prostych mikrousług CRUD</span><span class="sxs-lookup"><span data-stu-id="76b2b-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="76b2b-111">Przykładem tego rodzaju prostej usługi dysków danych jest mikrousługa katalogu z przykładowej aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="76b2b-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="76b2b-112">Ten typ usługi implementuje wszystkie jej funkcje w jednym ASP.NET Core projekcie interfejsu API sieci Web, który zawiera klasy dla modelu danych, jego logiki biznesowej i kod dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="76b2b-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="76b2b-113">Przechowuje także powiązane z nią dane w bazie danych działającej w SQL Server (jako inny kontener do celów deweloperskich/testowych), ale może to być również dowolny zwykły SQL Server hosta, jak pokazano na rysunku 6-5.</span><span class="sxs-lookup"><span data-stu-id="76b2b-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Mikrousługa wykazu logicznego obejmuje swoją bazę danych wykazu, która może być lub nie znajduje się na tym samym hoście platformy Docker.](./media/image5.png)

<span data-ttu-id="76b2b-116">**Rysunek 6-5**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-116">**Figure 6-5**.</span></span> <span data-ttu-id="76b2b-117">Prosty projekt mikrousług oparty na danych/CRUD</span><span class="sxs-lookup"><span data-stu-id="76b2b-117">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="76b2b-118">Podczas opracowywania tego rodzaju usługi wymagany jest tylko [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) i interfejs API dostępu do danych lub ORM, jak [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="76b2b-118">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="76b2b-119">Możesz również generować metadane [struktury Swagger](https://swagger.io/) automatycznie za pomocą [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) , aby podać opis oferty usługi, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="76b2b-119">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="76b2b-120">Należy pamiętać, że uruchamianie serwera bazy danych, takiego jak SQL Server w kontenerze platformy Docker, jest doskonałe dla środowisk programistycznych, ponieważ wszystkie Twoje zależności mogą działać bez konieczności aprowizacji bazy danych w chmurze lub lokalnie.</span><span class="sxs-lookup"><span data-stu-id="76b2b-120">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="76b2b-121">Jest to bardzo wygodne w przypadku uruchamiania testów integracji.</span><span class="sxs-lookup"><span data-stu-id="76b2b-121">This is very convenient when running integration tests.</span></span> <span data-ttu-id="76b2b-122">Jednak w przypadku środowisk produkcyjnych nie zaleca się korzystania z serwera bazy danych w kontenerze, ponieważ zazwyczaj nie ma wysokiej dostępności.</span><span class="sxs-lookup"><span data-stu-id="76b2b-122">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="76b2b-123">W środowisku produkcyjnym na platformie Azure zaleca się użycie usługi Azure SQL DB lub innej technologii bazy danych, która zapewnia wysoką dostępność i wysoką skalowalność.</span><span class="sxs-lookup"><span data-stu-id="76b2b-123">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="76b2b-124">Na przykład w przypadku podejścia NoSQL można wybrać pozycję CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="76b2b-124">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="76b2b-125">Na koniec edytując pliki metadanych pliku dockerfile i Docker-Compose. yml, można skonfigurować sposób tworzenia obrazu tego kontenera — na podstawie obrazu podstawowego, który będzie używany, a także ustawień projektowania, takich jak nazwy wewnętrzne i zewnętrzne oraz porty TCP.</span><span class="sxs-lookup"><span data-stu-id="76b2b-125">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="76b2b-126">Implementowanie prostej mikrousługi CRUD z ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="76b2b-126">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="76b2b-127">Aby zaimplementować prostą CRUD mikrousługi przy użyciu platformy .NET Core i programu Visual Studio, Zacznij od utworzenia prostego projektu interfejsu API sieci Web ASP.NET Core (działającego na platformie .NET Core, aby można go było uruchomić na hoście Docker systemu Linux), jak pokazano na rysunku 6-6.</span><span class="sxs-lookup"><span data-stu-id="76b2b-127">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Aby utworzyć projekt interfejsu API sieci Web ASP.NET Core, najpierw wybierz aplikację sieci Web ASP.NET Core, a następnie wybierz typ interfejsu API.](./media/image6.png)

<span data-ttu-id="76b2b-129">**Rysunek 6-6**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-129">**Figure 6-6**.</span></span> <span data-ttu-id="76b2b-130">Tworzenie projektu interfejsu API sieci Web ASP.NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76b2b-130">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="76b2b-131">Po utworzeniu projektu można zaimplementować kontrolery MVC w taki sam sposób jak w każdym innym projekcie interfejsu API sieci Web przy użyciu interfejsu API Entity Framework lub innego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="76b2b-131">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="76b2b-132">W nowym projekcie interfejsu API sieci Web można zobaczyć, że jedyną zależnością w tej mikrousłudze jest ASP.NET Core samej.</span><span class="sxs-lookup"><span data-stu-id="76b2b-132">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="76b2b-133">Wewnętrznie w ramach zależności *Microsoft. AspNetCore. All* odwołuje się do Entity Framework i wielu innych pakietów NuGet platformy .NET Core, jak pokazano na rysunku 6-7.</span><span class="sxs-lookup"><span data-stu-id="76b2b-133">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 6-7.</span></span>

![Projekt interfejsu API zawiera odwołania do pakietu NuGet Microsoft. AspNetCore. app, który zawiera odwołania do wszystkich najważniejszych pakietów.](./media/image8.png)

<span data-ttu-id="76b2b-136">**Rysunek 6-7**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-136">**Figure 6-7**.</span></span> <span data-ttu-id="76b2b-137">Zależności w prostej mikrousłudze CRUD Web API</span><span class="sxs-lookup"><span data-stu-id="76b2b-137">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="76b2b-138">Implementowanie usług interfejsu API sieci Web CRUD za pomocą Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="76b2b-138">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="76b2b-139">Entity Framework (EF) Core to lekka, rozszerzalna i wieloplatformowa wersja popularnej technologii dostępu do danych — Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="76b2b-139">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="76b2b-140">EF Core to Mapowanie obiektowo-relacyjne (ORM), które umożliwia deweloperom platformy .NET współdziałanie z bazą danych przy użyciu obiektów .NET.</span><span class="sxs-lookup"><span data-stu-id="76b2b-140">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="76b2b-141">Mikrousługa katalogu używa EF i dostawcy SQL Server, ponieważ jego baza danych działa w kontenerze z SQL Server dla obrazu platformy Docker systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="76b2b-141">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="76b2b-142">Jednak bazę danych można wdrożyć w dowolnym SQL Server, na przykład lokalnie lub w usłudze Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="76b2b-142">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="76b2b-143">Jedyną czynnością, którą należy zmienić, są parametry połączenia w mikrousłudze ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="76b2b-143">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="76b2b-144">Model danych</span><span class="sxs-lookup"><span data-stu-id="76b2b-144">The data model</span></span>

<span data-ttu-id="76b2b-145">W przypadku EF Core dostęp do danych odbywa się przy użyciu modelu.</span><span class="sxs-lookup"><span data-stu-id="76b2b-145">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="76b2b-146">Model składa się z klas jednostek jednostki i kontekstu pochodnego (DbContext) reprezentujących sesję z bazą danych, co pozwala na wykonywanie zapytań i zapisywanie danych.</span><span class="sxs-lookup"><span data-stu-id="76b2b-146">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="76b2b-147">Można wygenerować model z istniejącej bazy danych, ręcznie nakodować model w celu dopasowania do bazy danych lub użyć migracji EF do utworzenia bazy danych z modelu przy użyciu podejścia pierwszego kodu (ułatwiającego rozwijanie bazy danych w miarę zmiany modelu w czasie).</span><span class="sxs-lookup"><span data-stu-id="76b2b-147">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="76b2b-148">W przypadku mikrousługi katalogu używamy ostatniej metody.</span><span class="sxs-lookup"><span data-stu-id="76b2b-148">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="76b2b-149">Przykład klasy jednostki CatalogItem można zobaczyć w poniższym przykładzie kodu, który jest prostą, niedawną klasą obiektu CLR ([poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)).</span><span class="sxs-lookup"><span data-stu-id="76b2b-149">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="76b2b-150">Wymagany jest również DbContext, który reprezentuje sesję z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="76b2b-150">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="76b2b-151">W przypadku mikrousługi katalogowej Klasa CatalogContext dziedziczy z klasy podstawowej DbContext, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="76b2b-151">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="76b2b-152">Możesz mieć dodatkowe `DbContext` implementacje.</span><span class="sxs-lookup"><span data-stu-id="76b2b-152">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="76b2b-153">Przykładowo w przypadku mikrousługi przykładowej katalogu. API istnieje druga `DbContext` nazwa `CatalogContextSeed` , gdzie automatycznie wypełnia przykładowe dane podczas pierwszego próby dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="76b2b-153">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="76b2b-154">Ta metoda jest przydatna w przypadku danych demonstracyjnych i scenariuszy zautomatyzowanych testów.</span><span class="sxs-lookup"><span data-stu-id="76b2b-154">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="76b2b-155">W programie można `OnModelCreating` użyć metody ,abydostosowaćmapowaniajednostekobiektów/bazdanychorazinnepunktyrozszerzalnościEF.`DbContext` [](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)</span><span class="sxs-lookup"><span data-stu-id="76b2b-155">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="76b2b-156">Wykonywanie zapytań dotyczących danych z kontrolerów interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="76b2b-156">Querying data from Web API controllers</span></span>

<span data-ttu-id="76b2b-157">Wystąpienia klas jednostek są zwykle pobierane z bazy danych przy użyciu programu Query Integrated Language (LINQ), jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="76b2b-157">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="76b2b-158">Zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="76b2b-158">Saving data</span></span>

<span data-ttu-id="76b2b-159">Dane są tworzone, usuwane i modyfikowane w bazie danych za pomocą wystąpień klas jednostek.</span><span class="sxs-lookup"><span data-stu-id="76b2b-159">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="76b2b-160">Do kontrolerów interfejsu API sieci Web można dodać kod podobny do poniższego zakodowanego przykładu (w tym przypadku dane są w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="76b2b-160">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="76b2b-161">Wstrzykiwanie zależności w kontrolerach ASP.NET Core i interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="76b2b-161">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="76b2b-162">W ASP.NET Core można użyć iniekcji zależności (DI) poza ramką.</span><span class="sxs-lookup"><span data-stu-id="76b2b-162">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="76b2b-163">Nie jest konieczne skonfigurowanie kontenera kontroli (IoC) innej firmy, ale w razie potrzeby można podłączyć preferowany kontener IoC do infrastruktury ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="76b2b-163">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="76b2b-164">W takim przypadku oznacza to, że można bezpośrednio wstrzyknąć wymagane, EF DbContext lub dodatkowe repozytoria za pośrednictwem konstruktora kontrolera.</span><span class="sxs-lookup"><span data-stu-id="76b2b-164">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="76b2b-165">W powyższym `CatalogController` przykładzie klasy wprowadzamy `CatalogContext` obiekt typu `CatalogController()` plus inne obiekty za pomocą konstruktora.</span><span class="sxs-lookup"><span data-stu-id="76b2b-165">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="76b2b-166">Ważną konfiguracją skonfigurowaną w projekcie interfejsu API sieci Web jest rejestracja klasy DbContext w kontenerze IoC usługi.</span><span class="sxs-lookup"><span data-stu-id="76b2b-166">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="76b2b-167">Zwykle jest to wykonywane w `Startup` klasie przez `services.AddDbContext<DbContext>()` wywołanie metody wewnątrz `ConfigureServices()` metody, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="76b2b-167">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="76b2b-168">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="76b2b-168">Additional resources</span></span>

- <span data-ttu-id="76b2b-169">**Wykonywanie zapytania dotyczącego danych** </span><span class="sxs-lookup"><span data-stu-id="76b2b-169">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="76b2b-170">**Zapisywanie danych** </span><span class="sxs-lookup"><span data-stu-id="76b2b-170">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="76b2b-171">Parametry połączenia bazy danych i zmienne środowiskowe używane przez kontenery platformy Docker</span><span class="sxs-lookup"><span data-stu-id="76b2b-171">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="76b2b-172">Możesz użyć ustawień ASP.NET Core i dodać Właściwość ConnectionString do pliku Settings. JSON, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="76b2b-172">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```json
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

<span data-ttu-id="76b2b-173">Plik Settings. JSON może mieć wartości domyślne dla właściwości ConnectionString lub dla każdej innej właściwości.</span><span class="sxs-lookup"><span data-stu-id="76b2b-173">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="76b2b-174">Jednak te właściwości zostaną przesłonięte przez wartości zmiennych środowiskowych określonych w pliku Docker-Compose. override. yml podczas korzystania z platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="76b2b-174">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="76b2b-175">Z plików Docker-Compose. yml lub Docker-Compose. override. yml można inicjować te zmienne środowiskowe, aby platforma Docker ustawi jako zmienne środowiskowe systemu operacyjnego, jak pokazano w następującym pliku Docker-Compose. override. yml (połączenie ciąg i inne wiersze są zawijane w tym przykładzie, ale nie będą zawijane we własnym pliku.</span><span class="sxs-lookup"><span data-stu-id="76b2b-175">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="76b2b-176">Pliki Docker-Compose. yml na poziomie rozwiązania nie są bardziej elastyczne niż pliki konfiguracyjne na poziomie projektu lub mikrousług, ale również bezpieczniej, jeśli zastąpisz zmienne środowiskowe zadeklarowane w plikach tworzenia platformy Docker z wartościami ustawionymi z narzędzia do wdrażania, takie jak Azure DevOps Services zadań wdrażania platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="76b2b-176">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="76b2b-177">Na koniec można uzyskać tę wartość z kodu za pomocą konfiguracji\["ConnectionString"\], jak pokazano w metodzie ConfigureServices w poprzednim przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="76b2b-177">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="76b2b-178">Jednak w przypadku środowisk produkcyjnych warto zapoznać się z dodatkowymi sposobami przechowywania wpisów tajnych, takich jak parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="76b2b-178">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="76b2b-179">Doskonałym sposobem na zarządzanie wpisami tajnymi aplikacji jest użycie [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="76b2b-179">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="76b2b-180">Azure Key Vault pomaga przechowywać i chronić klucze kryptograficzne i wpisy tajne używane przez aplikacje i usługi w chmurze.</span><span class="sxs-lookup"><span data-stu-id="76b2b-180">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="76b2b-181">Wpis tajny to wszystko, co chcesz zachować ścisłą kontrolę, podobnie jak klucze interfejsu API, parametry połączeń, hasła itp., a ścisła kontrola obejmuje rejestrowanie użycia, Ustawianie wygaśnięcia, zarządzanie dostępem *między innymi*.</span><span class="sxs-lookup"><span data-stu-id="76b2b-181">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="76b2b-182">Azure Key Vault pozwala na bardzo szczegółowy poziom kontroli użycia wpisów tajnych aplikacji bez konieczności poinformowania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="76b2b-182">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="76b2b-183">Wpisy tajne można nawet obrócić, aby zwiększyć bezpieczeństwo bez zakłócania programowania lub operacji.</span><span class="sxs-lookup"><span data-stu-id="76b2b-183">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="76b2b-184">Aplikacje muszą być zarejestrowane w Active Directory organizacji, aby mogły korzystać z Key Vault.</span><span class="sxs-lookup"><span data-stu-id="76b2b-184">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="76b2b-185">Więcej informacji można znaleźć w *dokumentacji dotyczącej pojęć Key Vault* .</span><span class="sxs-lookup"><span data-stu-id="76b2b-185">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="76b2b-186">Implementowanie obsługi wersji w interfejsach API sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="76b2b-186">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="76b2b-187">W miarę zmiany wymagań firmy nowe kolekcje zasobów mogą zostać dodane, relacje między zasobami mogą ulec zmianie, a struktura danych w zasobach może zostać zmieniona.</span><span class="sxs-lookup"><span data-stu-id="76b2b-187">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="76b2b-188">Aktualizacja internetowego interfejsu API do obsługi nowych wymagań jest stosunkowo prosta, ale należy wziąć pod uwagę wpływ takich zmian na aplikacje klienckie korzystające z internetowego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="76b2b-188">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="76b2b-189">Chociaż deweloper projektowanie i implementowanie internetowego interfejsu API ma pełną kontrolę nad tym interfejsem API, Deweloper nie ma takiego samego stopnia kontroli nad aplikacjami klienckimi, które mogą być kompilowane przez organizacje innych firm.</span><span class="sxs-lookup"><span data-stu-id="76b2b-189">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="76b2b-190">Obsługa wersji umożliwia korzystanie z interfejsu API sieci Web w celu wskazania dostępnych funkcji i zasobów.</span><span class="sxs-lookup"><span data-stu-id="76b2b-190">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="76b2b-191">Aplikacja kliencka może przesyłać żądania do określonej wersji funkcji lub zasobu.</span><span class="sxs-lookup"><span data-stu-id="76b2b-191">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="76b2b-192">Istnieje kilka sposobów implementacji wersji:</span><span class="sxs-lookup"><span data-stu-id="76b2b-192">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="76b2b-193">Przechowywanie wersji identyfikatorów URI</span><span class="sxs-lookup"><span data-stu-id="76b2b-193">URI versioning</span></span>

- <span data-ttu-id="76b2b-194">Przechowywanie wersji ciągu zapytania</span><span class="sxs-lookup"><span data-stu-id="76b2b-194">Query string versioning</span></span>

- <span data-ttu-id="76b2b-195">Przechowywanie wersji nagłówka</span><span class="sxs-lookup"><span data-stu-id="76b2b-195">Header versioning</span></span>

<span data-ttu-id="76b2b-196">Jest to najprostszy do zaimplementowania ciąg zapytania i wersja identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="76b2b-196">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="76b2b-197">Przechowywanie wersji nagłówka jest dobrym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="76b2b-197">Header versioning is a good approach.</span></span> <span data-ttu-id="76b2b-198">Jednak wersja nagłówka nie jest jawna i prosta jako wersja identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="76b2b-198">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="76b2b-199">Ponieważ przechowywanie wersji adresów URL jest najprostszym i najbardziej jawnym, przykładowa aplikacja eShopOnContainers korzysta z obsługi wersji identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="76b2b-199">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="76b2b-200">W przypadku obsługi wersji identyfikatorów URI, podobnie jak w przypadku przykładowej aplikacji eShopOnContainers, przy każdej modyfikacji internetowego interfejsu API lub zmianie schematu zasobów należy dodać numer wersji do identyfikatora URI dla każdego zasobu.</span><span class="sxs-lookup"><span data-stu-id="76b2b-200">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="76b2b-201">Istniejące identyfikatory URI powinny nadal działać jak poprzednio, zwracając zasoby zgodne ze schematem, który jest zgodny z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="76b2b-201">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="76b2b-202">Jak pokazano w poniższym przykładzie kodu, można ustawić wersję przy użyciu atrybutu trasy w kontrolerze internetowego interfejsu API, co spowoduje, że wersja jawnie w identyfikatorze URI (v1 w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="76b2b-202">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="76b2b-203">Ten mechanizm przechowywania wersji jest prosty i zależy od serwera routingu żądania do odpowiedniego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="76b2b-203">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="76b2b-204">Jednak w celu uzyskania bardziej zaawansowanej wersji i najlepszej metody w przypadku korzystania z usługi REST należy użyć narzędzia z nośnika i zaimplementować [HATEOAS (hipertekst jako aparat stanu aplikacji)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="76b2b-204">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="76b2b-205">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="76b2b-205">Additional resources</span></span>

- <span data-ttu-id="76b2b-206">**Scott Hanselman. Łatwość ASP.NET Core RESTful internetowego interfejsu API** </span><span class="sxs-lookup"><span data-stu-id="76b2b-206">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="76b2b-207">**Przechowywanie wersji interfejsu API sieci Web RESTful** </span><span class="sxs-lookup"><span data-stu-id="76b2b-207">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="76b2b-208">**Roy. Przechowywanie wersji, nośniki i REST** </span><span class="sxs-lookup"><span data-stu-id="76b2b-208">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="76b2b-209">Generowanie metadanych opisu struktury Swagger z internetowego interfejsu API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="76b2b-209">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="76b2b-210">[Swagger](https://swagger.io/) to powszechnie używana platforma typu "open source" obsługiwana przez duży ekosystem narzędzi, które ułatwiają projektowanie, kompilowanie, dokumentowanie i Używanie interfejsów API RESTful.</span><span class="sxs-lookup"><span data-stu-id="76b2b-210">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="76b2b-211">Staje się standardem dla domeny metadanych opisu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="76b2b-211">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="76b2b-212">Należy uwzględnić metadane opisu struktury Swagger przy użyciu dowolnego rodzaju mikrousług, mikrousług opartych na danych lub bardziej zaawansowanych mikrousług opartych na domenie (jak wyjaśniono w poniższej sekcji).</span><span class="sxs-lookup"><span data-stu-id="76b2b-212">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="76b2b-213">Sercem struktury Swagger jest specyfikacja struktury Swagger, która jest metadanymi opisu interfejsu API w pliku JSON lub YAML.</span><span class="sxs-lookup"><span data-stu-id="76b2b-213">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="76b2b-214">Specyfikacja tworzy kontrakt RESTful dla interfejsu API, szczegóły wszystkich zasobów i operacji zarówno w formacie czytelnym dla człowieka, jak i na komputerze umożliwiającym łatwe programowanie, odnajdywanie i integrację.</span><span class="sxs-lookup"><span data-stu-id="76b2b-214">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="76b2b-215">Specyfikacja jest podstawą specyfikacji OpenAPI (OAS) i jest opracowana w postaci otwartej, przejrzystej i współpracy ze współpracownikami w celu standaryzacji sposobu definiowania interfejsów RESTful.</span><span class="sxs-lookup"><span data-stu-id="76b2b-215">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="76b2b-216">Specyfikacja definiuje strukturę sposobu odnajdowania usługi i sposobu jej zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="76b2b-216">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="76b2b-217">Aby uzyskać więcej informacji, w tym Edytor sieci Web i przykłady specyfikacji struktury Swagger z firm takich jak Spotify, Uber, zapasy i Microsoft, zobacz witrynę<https://swagger.io>programu Swagger ().</span><span class="sxs-lookup"><span data-stu-id="76b2b-217">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="76b2b-218">Dlaczego warto używać struktury Swagger?</span><span class="sxs-lookup"><span data-stu-id="76b2b-218">Why use Swagger?</span></span>

<span data-ttu-id="76b2b-219">Główne przyczyny generowania metadanych struktury Swagger dla interfejsów API są następujące.</span><span class="sxs-lookup"><span data-stu-id="76b2b-219">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="76b2b-220">**Możliwość automatycznego wykorzystywania i integrowania interfejsów API przez inne produkty**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-220">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="76b2b-221">Liczne produkty i [Narzędzia komercyjne](https://swagger.io/commercial-tools/) oraz wiele [bibliotek i struktur obsługują strukturę](https://swagger.io/open-source-integrations/) Swagger.</span><span class="sxs-lookup"><span data-stu-id="76b2b-221">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="76b2b-222">Firma Microsoft oferuje produkty i narzędzia wysokiego poziomu, które mogą automatycznie korzystać z interfejsów API opartych na strukturze Swagger, takich jak następujące:</span><span class="sxs-lookup"><span data-stu-id="76b2b-222">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="76b2b-223">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="76b2b-223">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="76b2b-224">Można automatycznie generować klasy klienckie platformy .NET do wywoływania struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="76b2b-224">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="76b2b-225">To narzędzie może być używane z poziomu interfejsu wiersza polecenia i integruje się z programem Visual Studio, aby ułatwić korzystanie z interfejsu GUI.</span><span class="sxs-lookup"><span data-stu-id="76b2b-225">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="76b2b-226">[Microsoft Flow](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="76b2b-226">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="76b2b-227">Możesz automatycznie [użyć i zintegrować interfejs API](https://flow.microsoft.com/blog/integrating-custom-api/) w przepływie pracy Microsoft Flow wysokiego poziomu, bez konieczności korzystania z umiejętności programistycznych.</span><span class="sxs-lookup"><span data-stu-id="76b2b-227">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="76b2b-228">[Microsoft powerapps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="76b2b-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="76b2b-229">Możesz automatycznie korzystać z interfejsu API z [aplikacji mobilnych powerapps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) utworzonych przy użyciu [powerapps Studio](https://powerapps.microsoft.com/build-powerapps/), bez konieczności umiejętności programistycznych.</span><span class="sxs-lookup"><span data-stu-id="76b2b-229">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="76b2b-230">[Logic Apps Azure App Service](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="76b2b-230">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="76b2b-231">Możesz automatycznie [używać interfejsu API i zintegrować go z aplikacją logiki Azure App Service](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), bez wymaganych umiejętności programistycznych.</span><span class="sxs-lookup"><span data-stu-id="76b2b-231">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="76b2b-232">**Możliwość automatycznego generowania dokumentacji interfejsu API**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-232">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="76b2b-233">Podczas tworzenia interfejsów API RESTful o dużej skali, takich jak złożone aplikacje oparte na mikrousługach, należy obsługiwać wiele punktów końcowych z różnymi modelami danych używanymi w ładunku żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="76b2b-233">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="76b2b-234">Posiadanie odpowiedniej dokumentacji i posiadanie pełnego Eksploratora interfejsów API, jak w przypadku programu Swagger, jest kluczem dla sukcesu interfejsu API i wdrażania przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="76b2b-234">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="76b2b-235">Metadane struktury Swagger to Microsoft Flow, PowerApps i Azure Logic Apps używane do zrozumienia, jak używać interfejsów API i łączyć się z nimi.</span><span class="sxs-lookup"><span data-stu-id="76b2b-235">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="76b2b-236">Istnieje kilka opcji automatyzowania generowania metadanych struktury Swagger dla ASP.NET Core aplikacji interfejsu API REST, w formie stron pomocy interfejsu API funkcji, opartych na strukturze *Swagger-UI*.</span><span class="sxs-lookup"><span data-stu-id="76b2b-236">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="76b2b-237">Prawdopodobnie najlepszą wiedzą, że jest to [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) , która jest obecnie używana w [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) i w tym przewodniku zajmiemy się bardziej szczegółowo, ale jest również dostępna opcja użycia [NSwag](https://github.com/RSuter/NSwag), która może generować\# klientów interfejsu API języka TypeScript i języka C, tak jak Podobnie jak w\# przypadku kontrolerów języka C, ze specyfikacją Swagger lub openapi, a nawet przez skanowanie pliku DLL zawierającego kontrolery przy użyciu [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="76b2b-237">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), that can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="76b2b-238">Jak zautomatyzować generowanie metadanych struktury Swagger interfejsu API za pomocą pakietu NuGet Swashbuckle</span><span class="sxs-lookup"><span data-stu-id="76b2b-238">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="76b2b-239">Ręczne generowanie metadanych struktury Swagger (w pliku JSON lub YAML) może być żmudnym pracy.</span><span class="sxs-lookup"><span data-stu-id="76b2b-239">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="76b2b-240">Można jednak zautomatyzować odnajdywanie interfejsów API ASP.NET usług interfejsu API sieci Web za pomocą [pakietu NuGet Swashbuckle](https://aka.ms/swashbuckledotnetcore) do dynamicznego generowania metadanych interfejsu API struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="76b2b-240">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="76b2b-241">Swashbuckle automatycznie generuje metadanych struktury Swagger dla projektów internetowego interfejsu API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="76b2b-241">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="76b2b-242">Obsługuje ona ASP.NET Core projekty interfejsu API sieci Web oraz tradycyjnego interfejsu API sieci Web ASP.NET oraz innych typów, takich jak aplikacja interfejsu API platformy Azure, aplikacja mobilna platformy Azure, platforma Azure Service Fabric na podstawie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="76b2b-242">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="76b2b-243">Obsługuje ona również zwykły internetowy interfejs API wdrożony w kontenerach, jak w przypadku aplikacji referencyjnej.</span><span class="sxs-lookup"><span data-stu-id="76b2b-243">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="76b2b-244">Swashbuckle łączy Eksploratora interfejsu API i struktury Swagger lub [Swagger-interfejs użytkownika](https://github.com/swagger-api/swagger-ui) , aby zapewnić bogate środowisko odnajdywania i dokumentacji dla odbiorców interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="76b2b-244">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="76b2b-245">Oprócz aparatu generatora metadanych struktury Swagger Swashbuckle zawiera również osadzoną wersję programu Swagger-UI, która będzie automatycznie działać po zainstalowaniu Swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="76b2b-245">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="76b2b-246">Oznacza to, że możesz uzupełnić interfejs API za pomocą interfejsu użytkownika, aby ułatwić deweloperom korzystanie z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="76b2b-246">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="76b2b-247">Wymaga bardzo małej ilości kodu i konserwacji, ponieważ jest automatycznie generowana, co pozwala skupić się na tworzeniu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="76b2b-247">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="76b2b-248">Wynik dla Eksploratora interfejsu API wygląda jak rysunek 6-8.</span><span class="sxs-lookup"><span data-stu-id="76b2b-248">The result for the API Explorer looks like Figure 6-8.</span></span>

![Dokumentacja interfejsu API interfejsu użytkownika programu Swagger wygenerowanego przez Swashbuckle obejmuje wszystkie opublikowane akcje.](./media/image9.png)

<span data-ttu-id="76b2b-250">**Rysunek 6-8**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-250">**Figure 6-8**.</span></span> <span data-ttu-id="76b2b-251">Eksplorator interfejsu API Swashbuckle na podstawie metadanych struktury Swagger — mikrousługa eShopOnContainers Catalog</span><span class="sxs-lookup"><span data-stu-id="76b2b-251">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="76b2b-252">Eksplorator interfejsów API nie jest najważniejszym elementem w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="76b2b-252">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="76b2b-253">Gdy dysponujesz interfejsem API sieci Web, który można opisać w metadanych struktury Swagger, interfejs API może być bezproblemowo używany z narzędzi opartych na strukturze Swagger, w tym generatory kodu klasy serwera proxy klienta, które mogą kierować wiele platform.</span><span class="sxs-lookup"><span data-stu-id="76b2b-253">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="76b2b-254">Na przykład, jak wspomniano, [AutoRest](https://github.com/Azure/AutoRest) automatycznie generuje klasy klienckie platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="76b2b-254">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="76b2b-255">Jednak dostępne są również dodatkowe narzędzia, takie jak [Swagger-codegen](https://github.com/swagger-api/swagger-codegen) , które umożliwiają automatyczne generowanie kodu bibliotek klienckich interfejsu API, wycinków serwerów i dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="76b2b-255">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="76b2b-256">Obecnie Swashbuckle składa się z pięciu wewnętrznych pakietów NuGet w pakiecie meta-Package [Swashbuckle. AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) dla aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="76b2b-256">Currently, Swashbuckle consists of five internal NuGet packages under the high-level meta- package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="76b2b-257">Po zainstalowaniu tych pakietów NuGet w projekcie interfejsu API sieci Web należy skonfigurować strukturę Swagger w klasie startowej, jak w poniższym kodzie (uproszczony):</span><span class="sxs-lookup"><span data-stu-id="76b2b-257">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code (simplified):</span></span>

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

<span data-ttu-id="76b2b-258">Po wykonaniu tej czynności możesz uruchomić aplikację i przeglądać następujące dane JSON programu Swagger i punkty końcowe interfejsu użytkownika przy użyciu adresów URL takich jak:</span><span class="sxs-lookup"><span data-stu-id="76b2b-258">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```url
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="76b2b-259">Wygenerowany interfejs użytkownika utworzony przez Swashbuckle został wcześniej wyświetlony dla adresu URL, `http://<your-root-url>/swagger`takiego jak.</span><span class="sxs-lookup"><span data-stu-id="76b2b-259">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="76b2b-260">Na rysunku 6-9 można także sprawdzić, jak można testować dowolną metodę interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="76b2b-260">In Figure 6-9 you can also see how you can test any API method.</span></span>

![W szczegółach interfejsu API interfejsu użytkownika programu Swagger przedstawiono przykład odpowiedzi i można go użyć do wykonania rzeczywistego interfejsu API, który jest doskonałym rozwiązaniem do odnajdywania deweloperów.](./media/image10.png)

<span data-ttu-id="76b2b-262">**Rysunek 6-9**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-262">**Figure 6-9**.</span></span> <span data-ttu-id="76b2b-263">Swashbuckle interfejs użytkownika testowania metody katalogu/elementów interfejsu API</span><span class="sxs-lookup"><span data-stu-id="76b2b-263">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="76b2b-264">Na rysunku 6-10 przedstawiono metadane JSON programu Swagger wygenerowane z mikrousługi eShopOnContainers (która jest używana przez narzędzia poniżej) podczas żądania `http://<your-root-url>/swagger/v1/swagger.json` przy użyciu programu [Poster](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="76b2b-264">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Przykładowy interfejs użytkownika programu Poster przedstawiający metadane JSON programu Swagger](./media/image11.png)

<span data-ttu-id="76b2b-266">**Rysunek 6-10**.</span><span class="sxs-lookup"><span data-stu-id="76b2b-266">**Figure 6-10**.</span></span> <span data-ttu-id="76b2b-267">Metadane JSON programu Swagger</span><span class="sxs-lookup"><span data-stu-id="76b2b-267">Swagger JSON metadata</span></span>

<span data-ttu-id="76b2b-268">Jest to proste.</span><span class="sxs-lookup"><span data-stu-id="76b2b-268">It is that simple.</span></span> <span data-ttu-id="76b2b-269">I ponieważ jest generowany automatycznie, podczas dodawania większej funkcjonalności do interfejsu API zostaną powiększone metadane programu Swagger.</span><span class="sxs-lookup"><span data-stu-id="76b2b-269">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="76b2b-270">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="76b2b-270">Additional resources</span></span>

- <span data-ttu-id="76b2b-271">**Strony pomocy interfejsu API sieci Web ASP.NET korzystające z programu Swagger** </span><span class="sxs-lookup"><span data-stu-id="76b2b-271">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="76b2b-272">**Wprowadzenie do Swashbuckle i ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="76b2b-272">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="76b2b-273">**Wprowadzenie do NSwag i ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="76b2b-273">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="76b2b-274">[Poprzedni](microservice-application-design.md)Następny
> [](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="76b2b-274">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
