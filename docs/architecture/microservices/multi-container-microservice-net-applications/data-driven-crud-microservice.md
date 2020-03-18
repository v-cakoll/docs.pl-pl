---
title: Tworzenie prostej mikrousługi CRUD na podstawie danych
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zrozumienie tworzenia prostych crud (opartych na danych) mikrousługi w kontekście aplikacji mikrousług.
ms.date: 01/30/2020
ms.openlocfilehash: b72d7defed81e57e2971c5e2b53df2d86b2dc947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502352"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="67fb1-103">Tworzenie prostej mikrousługi CRUD na podstawie danych</span><span class="sxs-lookup"><span data-stu-id="67fb1-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="67fb1-104">W tej sekcji opisano sposób tworzenia prostej mikrousługi, która wykonuje operacje tworzenia, odczytu, aktualizacji i usuwania (CRUD) w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="67fb1-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="67fb1-105">Projektowanie prostej mikrousługi CRUD</span><span class="sxs-lookup"><span data-stu-id="67fb1-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="67fb1-106">Z punktu widzenia projektowania tego typu konteneryzowanych mikrousług jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="67fb1-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="67fb1-107">Być może problem do rozwiązania jest prosty, a może implementacja jest tylko dowodem koncepcji.</span><span class="sxs-lookup"><span data-stu-id="67fb1-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Diagram przedstawiający prosty wzorzec projektu wewnętrznego crud mikrousługi.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

<span data-ttu-id="67fb1-109">**Rysunek 6-4**.</span><span class="sxs-lookup"><span data-stu-id="67fb1-109">**Figure 6-4**.</span></span> <span data-ttu-id="67fb1-110">Projekt wewnętrzny dla prostych mikrousług CRUD</span><span class="sxs-lookup"><span data-stu-id="67fb1-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="67fb1-111">Przykładem tego rodzaju usługi prostego dysku danych jest mikrousługi katalogu z eShopOnContainers przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67fb1-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="67fb1-112">Ten typ usługi implementuje wszystkie swoje funkcje w jednym projekcie interfejsu API sieci Web ASP.NET, który zawiera klasy dla swojego modelu danych, jego logiki biznesowej i jego kodu dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="67fb1-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="67fb1-113">Przechowuje również powiązane dane w bazie danych działającej w programie SQL Server (jako inny kontener do celów deweloperskich/testowych), ale może być również zwykłym hostem programu SQL Server, jak pokazano na rysunku 6-5.</span><span class="sxs-lookup"><span data-stu-id="67fb1-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Diagram przedstawiający kontener mikrousług opartych na danych/CRUD.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

<span data-ttu-id="67fb1-115">**Rysunek 6-5**.</span><span class="sxs-lookup"><span data-stu-id="67fb1-115">**Figure 6-5**.</span></span> <span data-ttu-id="67fb1-116">Prosta konstrukcja mikrousług opartych na danych/CRUD</span><span class="sxs-lookup"><span data-stu-id="67fb1-116">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="67fb1-117">Poprzedni diagram przedstawia mikrousługę wykazu logicznego, która zawiera jego bazy danych wykazu, który może być lub nie w tym samym hoście platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="67fb1-117">The previous diagram shows the logical Catalog microservice, that includes its Catalog database, which can be or not in the same Docker host.</span></span> <span data-ttu-id="67fb1-118">Posiadanie bazy danych w tym samym hoście platformy Docker może być dobre dla rozwoju, ale nie dla produkcji.</span><span class="sxs-lookup"><span data-stu-id="67fb1-118">Having the database in the same Docker host might be good for development, but not for production.</span></span> <span data-ttu-id="67fb1-119">Podczas opracowywania tego rodzaju usługi, należy tylko [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) i interfejsu API dostępu do danych lub ORM jak Entity [Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="67fb1-119">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="67fb1-120">Można również wygenerować metadane [Swagger](https://swagger.io/) automatycznie za pośrednictwem [Swashbuckle,](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) aby podać opis tego, co oferuje usługa, jak wyjaśniono w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="67fb1-120">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="67fb1-121">Należy zauważyć, że uruchomienie serwera bazy danych, takiego jak SQL Server w kontenerze platformy Docker, jest idealne dla środowisk programistycznych, ponieważ wszystkie zależności mogą być uruchamiane bez konieczności aprowizacji bazy danych w chmurze lub lokalnie.</span><span class="sxs-lookup"><span data-stu-id="67fb1-121">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="67fb1-122">Jest to bardzo wygodne podczas uruchamiania testów integracji.</span><span class="sxs-lookup"><span data-stu-id="67fb1-122">This is very convenient when running integration tests.</span></span> <span data-ttu-id="67fb1-123">Jednak w środowiskach produkcyjnych uruchomienie serwera bazy danych w kontenerze nie jest zalecane, ponieważ zwykle nie uotrzymasz wysokiej dostępności przy takim podejściu.</span><span class="sxs-lookup"><span data-stu-id="67fb1-123">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="67fb1-124">W środowisku produkcyjnym na platformie Azure zaleca się używanie usługi Azure SQL DB lub dowolnej innej technologii bazy danych, która może zapewnić wysoką dostępność i wysoką skalowalność.</span><span class="sxs-lookup"><span data-stu-id="67fb1-124">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="67fb1-125">Na przykład dla podejścia NoSQL można wybrać CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="67fb1-125">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="67fb1-126">Na koniec edytując pliki metadanych Dockerfile i docker-compose.yml, można skonfigurować sposób tworzenia obrazu tego kontenera — jaki obraz podstawowy będzie używany, a także ustawienia projektu, takie jak nazwy wewnętrzne i zewnętrzne oraz porty TCP.</span><span class="sxs-lookup"><span data-stu-id="67fb1-126">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="67fb1-127">Implementowanie prostej mikrousługi CRUD z ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67fb1-127">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="67fb1-128">Aby zaimplementować prostą mikrousługę CRUD przy użyciu .NET Core i Visual Studio, należy rozpocząć od utworzenia prostego ASP.NET projektu interfejsu API podstawowego interfejsu API sieci Web (uruchomionego na platformie .NET Core, aby można go było uruchomić na hoście platformy Docker systemu Linux), jak pokazano na rysunku 6-6.</span><span class="sxs-lookup"><span data-stu-id="67fb1-128">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Zrzut ekranu przedstawiający program Visual Studios przedstawiający konfigurację projektu.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

<span data-ttu-id="67fb1-130">**Rysunek 6-6**.</span><span class="sxs-lookup"><span data-stu-id="67fb1-130">**Figure 6-6**.</span></span> <span data-ttu-id="67fb1-131">Tworzenie ASP.NET projektu podstawowego interfejsu API sieci Web w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="67fb1-131">Creating an ASP.NET Core Web API project in Visual Studio 2019</span></span>

<span data-ttu-id="67fb1-132">Aby utworzyć ASP.NET core Web API Project, najpierw wybierz ASP.NET podstawową aplikację sieci Web, a następnie wybierz typ interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-132">To create an ASP.NET Core Web API Project, first select an ASP.NET Core Web Application and then select the API type.</span></span> <span data-ttu-id="67fb1-133">Po utworzeniu projektu można zaimplementować kontrolery MVC, tak jak w każdym innym projekcie interfejsu API sieci Web, przy użyciu interfejsu API struktury jednostki lub innego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-133">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="67fb1-134">W nowym projekcie interfejsu API sieci Web widać, że jedyną zależnością, którą masz w tej mikrousługi, jest sama ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="67fb1-134">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="67fb1-135">Wewnętrznie w ramach *zależności Microsoft.AspNetCore.All* odwołuje się do struktury jednostek i wielu innych pakietów NuGet .NET Core, jak pokazano na rysunku 6-7.</span><span class="sxs-lookup"><span data-stu-id="67fb1-135">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core NuGet packages, as shown in Figure 6-7.</span></span>

![Zrzut ekranu przedstawiający zależności NuGet interfejsu Catalog.Api.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

<span data-ttu-id="67fb1-137">**Rysunek 6-7**.</span><span class="sxs-lookup"><span data-stu-id="67fb1-137">**Figure 6-7**.</span></span> <span data-ttu-id="67fb1-138">Zależności w prostej mikrousłudze interfejsu API sieci Web CRUD</span><span class="sxs-lookup"><span data-stu-id="67fb1-138">Dependencies in a simple CRUD Web API microservice</span></span>

<span data-ttu-id="67fb1-139">Projekt interfejsu API zawiera odwołania do pakietu NuGet Microsoft.AspNetCore.App, który zawiera odwołania do wszystkich podstawowych pakietów.</span><span class="sxs-lookup"><span data-stu-id="67fb1-139">The API project includes references to the Microsoft.AspNetCore.App NuGet package, that includes references to all essential packages.</span></span> <span data-ttu-id="67fb1-140">Może zawierać również inne pakiety.</span><span class="sxs-lookup"><span data-stu-id="67fb1-140">It could include some other packages as well.</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="67fb1-141">Wdrażanie usług interfejsu API sieci Web CRUD z rdzeniem frameworku jednostek</span><span class="sxs-lookup"><span data-stu-id="67fb1-141">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="67fb1-142">Entity Framework (EF) Core jest lekką, rozszerzalne i międzyplatformowej wersji popularnej technologii dostępu do danych entity framework.</span><span class="sxs-lookup"><span data-stu-id="67fb1-142">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="67fb1-143">EF Core jest obiekt-relacyjne mapper (ORM), który umożliwia deweloperom .NET do pracy z bazą danych przy użyciu obiektów .NET.</span><span class="sxs-lookup"><span data-stu-id="67fb1-143">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="67fb1-144">Mikrousługi wykazu używa EF i dostawcy programu SQL Server, ponieważ jego baza danych jest uruchomiona w kontenerze z sql Server dla linux docker obrazu.</span><span class="sxs-lookup"><span data-stu-id="67fb1-144">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="67fb1-145">Jednak baza danych może zostać wdrożona w dowolnym programie SQL Server, takim jak lokalny system Windows lub usługa Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="67fb1-145">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="67fb1-146">Jedyną rzeczą, którą należy zmienić, jest ciąg połączenia w mikrousłudze interfejsu ASP.NET interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="67fb1-146">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="67fb1-147">Model danych</span><span class="sxs-lookup"><span data-stu-id="67fb1-147">The data model</span></span>

<span data-ttu-id="67fb1-148">Z EF Core, dostęp do danych odbywa się przy użyciu modelu.</span><span class="sxs-lookup"><span data-stu-id="67fb1-148">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="67fb1-149">Model składa się z klas jednostek (model domeny) i kontekstu pochodnego (DbContext), który reprezentuje sesję z bazą danych, umożliwiając wykonywanie zapytań i zapisywanie danych.</span><span class="sxs-lookup"><span data-stu-id="67fb1-149">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="67fb1-150">Można wygenerować model z istniejącej bazy danych, ręcznie kodmodelu, aby dopasować bazę danych lub użyć migracji EF do utworzenia bazy danych z modelu, przy użyciu podejścia opartego na kodzie (co ułatwia rozwijanie bazy danych, jak model zmienia się wraz z uchwadnianiem).</span><span class="sxs-lookup"><span data-stu-id="67fb1-150">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="67fb1-151">Dla mikrousługi katalogu używamy ostatniego podejścia.</span><span class="sxs-lookup"><span data-stu-id="67fb1-151">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="67fb1-152">Przykład klasy jednostki CatalogItem można wyświetlić w poniższym przykładzie kodu, który jest prostą klasą jednostki Zwykły stary obiekt CLR[(POCO).](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)</span><span class="sxs-lookup"><span data-stu-id="67fb1-152">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="67fb1-153">Potrzebny jest również DbContext, który reprezentuje sesję z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="67fb1-153">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="67fb1-154">W przypadku mikrousługi katalogu klasa CatalogContext pochodzi z klasy podstawowej DbContext, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="67fb1-154">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    { }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...
}
```

<span data-ttu-id="67fb1-155">Możesz mieć `DbContext` dodatkowe implementacje.</span><span class="sxs-lookup"><span data-stu-id="67fb1-155">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="67fb1-156">Na przykład w przykładowej mikrousługi Catalog.API istnieje `DbContext` `CatalogContextSeed` druga nazwa, gdzie automatycznie wypełnia przykładowe dane przy pierwszej próbie uzyskania dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="67fb1-156">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="67fb1-157">Ta metoda jest przydatna dla danych demonstracyjnych i scenariuszy testowania automatycznego, jak również.</span><span class="sxs-lookup"><span data-stu-id="67fb1-157">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="67fb1-158">W `DbContext`ramach programu `OnModelCreating` , można użyć metody, aby dostosować mapowania jednostek obiektu/bazy danych i innych [punktów rozszerzalności EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="67fb1-158">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="67fb1-159">Wykonywanie zapytań dotyczących danych z kontrolerów interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="67fb1-159">Querying data from Web API controllers</span></span>

<span data-ttu-id="67fb1-160">Wystąpienia klas jednostek są zazwyczaj pobierane z bazy danych przy użyciu language Integrated Query (LINQ), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="67fb1-160">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(
        CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService
            ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        context.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("items")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType(typeof(IEnumerable<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType((int)HttpStatusCode.BadRequest)]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery]int pageSize = 10,
        [FromQuery]int pageIndex = 0,
        string ids = null)
    {
        if (!string.IsNullOrEmpty(ids))
        {
            var items = await GetItemsByIdsAsync(ids);

            if (!items.Any())
            {
                return BadRequest("ids value invalid. Must be comma-separated list of numbers");
            }

            return Ok(items);
        }

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

##### <a name="saving-data"></a><span data-ttu-id="67fb1-161">Zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="67fb1-161">Saving data</span></span>

<span data-ttu-id="67fb1-162">Dane są tworzone, usuwane i modyfikowane w bazie danych przy użyciu wystąpień klas jednostek.</span><span class="sxs-lookup"><span data-stu-id="67fb1-162">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="67fb1-163">Można dodać kod, taki jak w poniższym zakodowanym przykładzie (w tym przypadku makiety danych) do kontrolerów interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="67fb1-163">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="67fb1-164">Wstrzykiwanie zależności w kontrolerach interfejsu API ASP.NET Core i Web</span><span class="sxs-lookup"><span data-stu-id="67fb1-164">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="67fb1-165">W ASP.NET Core można użyć iniekcji zależności (DI) po wyjęciu z pudełka.</span><span class="sxs-lookup"><span data-stu-id="67fb1-165">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="67fb1-166">Nie trzeba konfigurować kontenera inwersji formantu (IoC) innej firmy, chociaż w razie potrzeby można podłączyć preferowany kontener IoC do infrastruktury ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="67fb1-166">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="67fb1-167">W takim przypadku oznacza to, że można bezpośrednio wstrzyknąć wymagane EF DBContext lub dodatkowe repozytoria za pośrednictwem konstruktora kontrolera.</span><span class="sxs-lookup"><span data-stu-id="67fb1-167">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="67fb1-168">W powyższym przykładzie `CatalogController` klasy wstrzykujemy `CatalogContext` obiekt typu oraz `CatalogController()` inne obiekty za pośrednictwem konstruktora.</span><span class="sxs-lookup"><span data-stu-id="67fb1-168">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="67fb1-169">Ważną konfiguracją do skonfigurowania w projekcie interfejsu API sieci Web jest rejestracja klasy DbContext do kontenera IoC usługi.</span><span class="sxs-lookup"><span data-stu-id="67fb1-169">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="67fb1-170">Zazwyczaj należy to zrobić `Startup` w klasie, `services.AddDbContext<DbContext>()` wywołując `ConfigureServices()` metodę wewnątrz metody, jak pokazano w poniższym **uproszczonym** przykładzie:</span><span class="sxs-lookup"><span data-stu-id="67fb1-170">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following **simplified** example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.MigrationsAssembly(
                typeof(Startup).GetTypeInfo().Assembly.GetName().Name);

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

### <a name="additional-resources"></a><span data-ttu-id="67fb1-171">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="67fb1-171">Additional resources</span></span>

- <span data-ttu-id="67fb1-172">**Wykonywanie zapytań dotyczących danych** </span><span class="sxs-lookup"><span data-stu-id="67fb1-172">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="67fb1-173">**Zapisywanie danych** </span><span class="sxs-lookup"><span data-stu-id="67fb1-173">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="67fb1-174">Parametry połączenia bazy danych i zmienne środowiskowe używane przez kontenery platformy Docker</span><span class="sxs-lookup"><span data-stu-id="67fb1-174">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="67fb1-175">Można użyć ASP.NET ustawień core i dodać ConnectionString właściwości do pliku settings.json, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="67fb1-175">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="67fb1-176">Plik settings.json może mieć wartości domyślne dla ConnectionString właściwości lub dla innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="67fb1-176">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="67fb1-177">Jednak te właściwości zostaną zastąpione przez wartości zmiennych środowiskowych, które określisz w pliku docker-compose.override.yml, podczas korzystania z platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="67fb1-177">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="67fb1-178">Z plików docker-compose.yml lub docker-compose.override.yml można zainicjować te zmienne środowiskowe, aby platforma Docker skonfigurować je jako zmienne środowiskowe systemu operacyjnego, jak pokazano w następującym pliku docker-compose.override.yml (połączenie ciąg i inne linie zawijają się w tym przykładzie, ale nie będą zawijane we własnym pliku).</span><span class="sxs-lookup"><span data-stu-id="67fb1-178">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog-api:
  environment:
    - ConnectionString=Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

<span data-ttu-id="67fb1-179">Pliki docker-compose.yml na poziomie rozwiązania są nie tylko bardziej elastyczne niż pliki konfiguracyjne na poziomie projektu lub mikrousługi, ale także bardziej bezpieczne, jeśli zastąpisz zmienne środowiskowe zadeklarowane w plikach docker-compose z wartościami ustawionymi z narzędzia wdrażania, takie jak zadania wdrażania platformy Azure DevOps Services Docker.</span><span class="sxs-lookup"><span data-stu-id="67fb1-179">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="67fb1-180">Na koniec można uzyskać tę wartość z\[kodu przy\]użyciu konfiguracji "ConnectionString", jak pokazano w ConfigureServices metody w przykładzie wcześniejszego kodu.</span><span class="sxs-lookup"><span data-stu-id="67fb1-180">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="67fb1-181">Jednak w środowiskach produkcyjnych można zbadać dodatkowe sposoby przechowywania kluczy tajnych, takich jak parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="67fb1-181">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="67fb1-182">Doskonałym sposobem zarządzania kluczami tajnymi aplikacji jest użycie [usługi Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="67fb1-182">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="67fb1-183">Usługa Azure Key Vault pomaga przechowywać i chronić klucze kryptograficzne i klucze tajne używane przez aplikacje i usługi w chmurze.</span><span class="sxs-lookup"><span data-stu-id="67fb1-183">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="67fb1-184">Sekret jest wszystko, co chcesz zachować ścisłą kontrolę, jak klucze API, parametry połączenia, hasła, itp i ścisła kontrola obejmuje rejestrowanie użytkowania, ustawienie wygaśnięcia, zarządzanie dostępem, *między innymi*.</span><span class="sxs-lookup"><span data-stu-id="67fb1-184">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="67fb1-185">Usługa Azure Key Vault umożliwia bardzo szczegółowy poziom kontroli użycia kluczy tajnych aplikacji bez konieczności informowania kogokolwiek o nich.</span><span class="sxs-lookup"><span data-stu-id="67fb1-185">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="67fb1-186">Klucze tajne można nawet obracać w celu zwiększenia bezpieczeństwa bez zakłócania rozwoju lub operacji.</span><span class="sxs-lookup"><span data-stu-id="67fb1-186">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="67fb1-187">Aplikacje muszą być rejestrowane w usłudze Active Directory organizacji, aby mogły korzystać z magazynu kluczy.</span><span class="sxs-lookup"><span data-stu-id="67fb1-187">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="67fb1-188">Aby uzyskać więcej informacji, można zapoznać się z *dokumentacją pojęć magazynu kluczy.*</span><span class="sxs-lookup"><span data-stu-id="67fb1-188">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="67fb1-189">Implementowanie wersji w interfejsach API sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="67fb1-189">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="67fb1-190">W miarę zmiany wymagań biznesowych można dodać nowe kolekcje zasobów, relacje między zasobami mogą ulec zmianie, a struktura danych w zasobach może zostać zmieniona.</span><span class="sxs-lookup"><span data-stu-id="67fb1-190">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="67fb1-191">Aktualizowanie interfejsu API sieci Web do obsługi nowych wymagań jest stosunkowo prosty proces, ale należy wziąć pod uwagę skutki, jakie takie zmiany będą miały na aplikacje klienckie korzystających z interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="67fb1-191">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="67fb1-192">Mimo że deweloper projektowania i wdrażania interfejsu API sieci Web ma pełną kontrolę nad tym interfejsem API, deweloper nie ma takiego samego stopnia kontroli nad aplikacjami klienckimi, które mogą być tworzone przez organizacje innych firm działających zdalnie.</span><span class="sxs-lookup"><span data-stu-id="67fb1-192">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="67fb1-193">Przechowywanie wersji umożliwia interfejs owi api sieci Web, aby wskazać funkcje i zasoby, które udostępnia.</span><span class="sxs-lookup"><span data-stu-id="67fb1-193">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="67fb1-194">Aplikacja kliencka może następnie przesyłać żądania do określonej wersji funkcji lub zasobu.</span><span class="sxs-lookup"><span data-stu-id="67fb1-194">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="67fb1-195">Istnieje kilka podejść do wdrożenia wersji:</span><span class="sxs-lookup"><span data-stu-id="67fb1-195">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="67fb1-196">Obsługa wersji za pomocą identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="67fb1-196">URI versioning</span></span>

- <span data-ttu-id="67fb1-197">Obsługa wersji za pomocą ciągu zapytania</span><span class="sxs-lookup"><span data-stu-id="67fb1-197">Query string versioning</span></span>

- <span data-ttu-id="67fb1-198">Obsługa wersji za pomocą nagłówka</span><span class="sxs-lookup"><span data-stu-id="67fb1-198">Header versioning</span></span>

<span data-ttu-id="67fb1-199">Ciąg zapytania i przechowywanie wersji identyfikatorów URI są najprostsze do zaimplementowania.</span><span class="sxs-lookup"><span data-stu-id="67fb1-199">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="67fb1-200">Przechowywanie wersji nagłówka jest dobrym podejściem.</span><span class="sxs-lookup"><span data-stu-id="67fb1-200">Header versioning is a good approach.</span></span> <span data-ttu-id="67fb1-201">Jednak przechowywanie wersji nagłówka nie jest tak jawne i proste, jak przechowywanie wersji identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="67fb1-201">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="67fb1-202">Ponieważ przechowywanie adresów URL jest najprostsze i najbardziej jawne, przykładowa aplikacja eShopOnContainers używa przechowywania wersji identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="67fb1-202">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="67fb1-203">W przypadku przechowywania wersji URI, tak jak w przykładowej aplikacji eShopOnContainers, za każdym razem, gdy modyfikujesz interfejs API sieci Web lub zmieniasz schemat zasobów, należy dodać numer wersji do identyfikatora URI dla każdego zasobu.</span><span class="sxs-lookup"><span data-stu-id="67fb1-203">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="67fb1-204">Istniejące identyfikatory URI powinny nadal działać tak, jak poprzednio, zwracając zasoby, które są zgodne ze schematem, który pasuje do żądanej wersji.</span><span class="sxs-lookup"><span data-stu-id="67fb1-204">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="67fb1-205">Jak pokazano w poniższym przykładzie kodu, wersję można ustawić przy użyciu route atrybutu w kontrolerze interfejsu API sieci Web, co sprawia, że wersja jawne w identyfikatorze URI (v1 w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="67fb1-205">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="67fb1-206">Ten mechanizm przechowywanie wersji jest prosty i zależy od serwera routingu żądania do odpowiedniego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="67fb1-206">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="67fb1-207">Jednak w przypadku bardziej zaawansowanego tworzenia wersji i najlepszej metody przy użyciu rest, należy użyć hypermedia i zaimplementować [HATEOAS (Hypertext jako aparat stanu aplikacji).](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)</span><span class="sxs-lookup"><span data-stu-id="67fb1-207">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="67fb1-208">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="67fb1-208">Additional resources</span></span>

- <span data-ttu-id="67fb1-209">**Scott Hanselman. ASP.NET Core RESTful Web API przechowywanie wersji łatwe** </span><span class="sxs-lookup"><span data-stu-id="67fb1-209">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="67fb1-210">**Przechowywanie wersji internetowego interfejsu API RESTful** </span><span class="sxs-lookup"><span data-stu-id="67fb1-210">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="67fb1-211">**Roy Fielding. Przechowywanie wersji, hypermedia i REST** </span><span class="sxs-lookup"><span data-stu-id="67fb1-211">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="67fb1-212">Generowanie metadanych opisu Swaggera z ASP.NET core Web API</span><span class="sxs-lookup"><span data-stu-id="67fb1-212">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="67fb1-213">[Swagger](https://swagger.io/) jest często używanym open source framework wspierane przez duży ekosystem narzędzi, który pomaga projektowania, tworzenia, dokumentowania i zużycia restful interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-213">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="67fb1-214">Staje się standardem dla domeny metadanych opisu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-214">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="67fb1-215">Należy dołączyć metadane opisu Swaggera z dowolnego rodzaju mikrousług, mikrousług opartych na danych lub bardziej zaawansowanych mikrousług opartych na domenie (jak wyjaśniono w poniższej sekcji).</span><span class="sxs-lookup"><span data-stu-id="67fb1-215">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="67fb1-216">Sercem Swaggera jest specyfikacja Swaggera, która jest metadanymi opisu Interfejsu API w pliku JSON lub YAML.</span><span class="sxs-lookup"><span data-stu-id="67fb1-216">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="67fb1-217">Specyfikacja tworzy restful umowy dla interfejsu API, szczegółowo wszystkie jego zasoby i operacje w formacie człowieka i maszyny czytelne dla łatwego rozwoju, odnajdywania i integracji.</span><span class="sxs-lookup"><span data-stu-id="67fb1-217">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="67fb1-218">Specyfikacja jest podstawą specyfikacji OpenAPI (OAS) i jest rozwijana w otwartej, przejrzystej i współpracy społeczności w celu standaryzacji sposobu definiowania interfejsów RESTful.</span><span class="sxs-lookup"><span data-stu-id="67fb1-218">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="67fb1-219">Specyfikacja definiuje strukturę sposobu odnalezić usługę i jak jej możliwości rozumiane.</span><span class="sxs-lookup"><span data-stu-id="67fb1-219">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="67fb1-220">Aby uzyskać więcej informacji, w tym edytor a także przykłady specyfikacji Swagger a firmy takie jak Spotify, Uber, Slack i Microsoft, zobacz witrynę Swagger (<https://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="67fb1-220">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="67fb1-221">Dlaczego warto skorzystać z Swagger?</span><span class="sxs-lookup"><span data-stu-id="67fb1-221">Why use Swagger?</span></span>

<span data-ttu-id="67fb1-222">Główne przyczyny generowania metadanych Swagger dla interfejsów API są następujące.</span><span class="sxs-lookup"><span data-stu-id="67fb1-222">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="67fb1-223">**Możliwość automatycznego konsumowania i integrowania interfejsów API przez inne produkty.**</span><span class="sxs-lookup"><span data-stu-id="67fb1-223">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="67fb1-224">Dziesiątki produktów i [narzędzi komercyjnych](https://swagger.io/commercial-tools/) oraz wiele bibliotek [i struktur](https://swagger.io/open-source-integrations/) obsługuje Firmę Swagger.</span><span class="sxs-lookup"><span data-stu-id="67fb1-224">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="67fb1-225">Firma Microsoft ma produkty wysokiego poziomu i narzędzia, które mogą automatycznie korzystać z interfejsów API opartych na swagger, takich jak następujące:</span><span class="sxs-lookup"><span data-stu-id="67fb1-225">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="67fb1-226">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="67fb1-226">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="67fb1-227">Klasy klienta .NET można automatycznie generować dla wywoływania swagger.</span><span class="sxs-lookup"><span data-stu-id="67fb1-227">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="67fb1-228">To narzędzie może być używane z interfejsu użytkownika, a także integruje się z visual studio do łatwego użycia za pośrednictwem gui.</span><span class="sxs-lookup"><span data-stu-id="67fb1-228">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="67fb1-229">[Usługa Microsoft Flow](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="67fb1-229">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="67fb1-230">Możesz automatycznie [używać interfejsu API i integrować go](https://flow.microsoft.com/blog/integrating-custom-api/) z obiegiem pracy usługi Microsoft Flow na wysokim poziomie, bez konieczności programowania.</span><span class="sxs-lookup"><span data-stu-id="67fb1-230">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="67fb1-231">[Usługa Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="67fb1-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="67fb1-232">Możesz automatycznie korzystać z interfejsu API z [aplikacji mobilnych usługi PowerApps utworzonych](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) za pomocą [usługi PowerApps Studio,](https://powerapps.microsoft.com/build-powerapps/)bez konieczności programowania.</span><span class="sxs-lookup"><span data-stu-id="67fb1-232">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="67fb1-233">[Aplikacje logiki usługi Azure App Service](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="67fb1-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="67fb1-234">Możesz automatycznie [używać interfejsu API i integrować go z aplikacją logiki usługi Azure App Service,](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)bez konieczności programowania.</span><span class="sxs-lookup"><span data-stu-id="67fb1-234">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="67fb1-235">**Możliwość automatycznego generowania dokumentacji interfejsu API**.</span><span class="sxs-lookup"><span data-stu-id="67fb1-235">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="67fb1-236">Podczas tworzenia dużych interfejsów API RESTful, takich jak złożone aplikacje oparte na mikrousługach, należy obsługiwać wiele punktów końcowych z różnych modeli danych używanych w ładunku żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="67fb1-236">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="67fb1-237">Posiadanie odpowiedniej dokumentacji i posiadanie solidnego eksploratora interfejsu API, jak masz z Swagger, jest kluczem do sukcesu interfejsu API i przyjęcia przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="67fb1-237">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="67fb1-238">Metadane swaggera są używane przez program Microsoft Flow, usługi PowerApps i usługi Azure Logic Apps, aby zrozumieć, jak używać interfejsów API i łączyć się z nimi.</span><span class="sxs-lookup"><span data-stu-id="67fb1-238">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="67fb1-239">Istnieje kilka opcji automatyzacji generowania metadanych Swagger dla ASP.NET podstawowych aplikacji Interfejsu API REST, w postaci funkcjonalnych stron pomocy interfejsu API, opartych na *swagger-ui*.</span><span class="sxs-lookup"><span data-stu-id="67fb1-239">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="67fb1-240">Prawdopodobnie najlepiej wiedzieć jest [Swashbuckle,](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) który jest obecnie używany w [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) i omówimy w niektórych szczegółach w tym przewodniku, ale\# istnieje również możliwość korzystania\# [z NSwag](https://github.com/RSuter/NSwag), który może generować maszynopis i C API klientów, a także kontrolerów C, ze specyfikacji Swagger lub OpenAPI, a nawet poprzez skanowanie .dll, który zawiera kontrolery, za pomocą [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="67fb1-240">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), which can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="67fb1-241">Jak zautomatyzować generowanie metadanych API Swagger za pomocą pakietu Swashbuckle NuGet</span><span class="sxs-lookup"><span data-stu-id="67fb1-241">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="67fb1-242">Ręczne generowanie metadanych Swaggera (w pliku JSON lub YAML) może być żmudną pracą.</span><span class="sxs-lookup"><span data-stu-id="67fb1-242">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="67fb1-243">Można jednak zautomatyzować odnajdowanie interfejsu API ASP.NET usług interfejsu API sieci Web przy użyciu [pakietu Swashbuckle NuGet](https://aka.ms/swashbuckledotnetcore) do dynamicznego generowania metadanych interfejsu API Swaggera.</span><span class="sxs-lookup"><span data-stu-id="67fb1-243">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="67fb1-244">Swashbuckle automatycznie generuje metadane Swagger dla projektów interfejsu ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-244">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="67fb1-245">Obsługuje ASP.NET podstawowych projektów interfejsu API sieci Web i tradycyjnego interfejsu API sieci Web ASP.NET i dowolnego innego smaku, takiego jak aplikacja Azure API, aplikacja azure mobile app, mikrousługi sieci Web sieci Web platformy Azure na podstawie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="67fb1-245">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="67fb1-246">Obsługuje również zwykły interfejs API sieci Web wdrożony na kontenerach, tak jak w przypadku aplikacji referencyjnej.</span><span class="sxs-lookup"><span data-stu-id="67fb1-246">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="67fb1-247">Swashbuckle łączy api Explorer i Swagger lub [swagger-ui,](https://github.com/swagger-api/swagger-ui) aby zapewnić bogate doświadczenie wykrywania i dokumentacji dla konsumentów interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-247">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="67fb1-248">Oprócz silnika generatora metadanych Swaggera, Swashbuckle zawiera również wbudowaną wersję swagger-ui, którą automatycznie poda po zainstalowaniu Swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="67fb1-248">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="67fb1-249">Oznacza to, że można uzupełnić interfejsu API z ładnym interfejsu użytkownika odnajdywania, aby ułatwić deweloperom korzystanie z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-249">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="67fb1-250">Wymaga to bardzo małej ilości kodu i konserwacji, ponieważ jest generowany automatycznie, co pozwala skupić się na tworzeniu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-250">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="67fb1-251">Wynik dla Eksploratora interfejsu API wygląda jak rysunek 6-8.</span><span class="sxs-lookup"><span data-stu-id="67fb1-251">The result for the API Explorer looks like Figure 6-8.</span></span>

![Zrzut ekranu przedstawiający eksploratora interfejsu API Swaggera wyświetlającego interfejs API eShopOContainers.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

<span data-ttu-id="67fb1-253">**Rysunek 6-8**.</span><span class="sxs-lookup"><span data-stu-id="67fb1-253">**Figure 6-8**.</span></span> <span data-ttu-id="67fb1-254">Swashbuckle API Explorer na podstawie metadanych Swagger — mikrousługi katalogu eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="67fb1-254">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="67fb1-255">Swashbuckle generowane Swagger UI Dokumentacja interfejsu API zawiera wszystkie opublikowane akcje.</span><span class="sxs-lookup"><span data-stu-id="67fb1-255">The Swashbuckle generated Swagger UI API documentation includes all published actions.</span></span> <span data-ttu-id="67fb1-256">Eksplorator interfejsu API nie jest tutaj najważniejszą rzeczą.</span><span class="sxs-lookup"><span data-stu-id="67fb1-256">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="67fb1-257">Gdy masz interfejs API sieci Web, który może opisywać się w metadanych Swagger, interfejs API może być używany bezproblemowo z narzędzi opartych na swagger, w tym generatory kodu klasy proxy klienta, które mogą być przeznaczone dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="67fb1-257">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="67fb1-258">Na przykład, jak wspomniano, [AutoRest](https://github.com/Azure/AutoRest) automatycznie generuje klasy klientów .NET.</span><span class="sxs-lookup"><span data-stu-id="67fb1-258">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="67fb1-259">Ale dodatkowe narzędzia, takie jak [swagger-codegen](https://github.com/swagger-api/swagger-codegen) są również dostępne, które umożliwiają generowanie kodu bibliotek klienta interfejsu API, wycinki serwera i dokumentacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="67fb1-259">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="67fb1-260">Obecnie Swashbuckle składa się z pięciu wewnętrznych pakietów NuGet w ramach wysokiego poziomu meta-pakiet [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) dla ASP.NET aplikacji Core.</span><span class="sxs-lookup"><span data-stu-id="67fb1-260">Currently, Swashbuckle consists of five internal NuGet packages under the high-level meta- package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="67fb1-261">Po zainstalowaniu tych pakietów NuGet w projekcie interfejsu API sieci Web należy skonfigurować swagger w klasie Start, jak w **następującym uproszczonym** kodzie:</span><span class="sxs-lookup"><span data-stu-id="67fb1-261">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following **simplified** code:</span></span>

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
            options.SwaggerDoc("v1", new OpenApiInfo
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample"
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

<span data-ttu-id="67fb1-262">Gdy to zrobisz, można uruchomić aplikację i przeglądać następujące punkty końcowe Swagger JSON i interfejsu użytkownika przy użyciu adresów URL, takich jak te:</span><span class="sxs-lookup"><span data-stu-id="67fb1-262">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="67fb1-263">Wcześniej widziałeś wygenerowany ui utworzony przez Swashbuckle `http://<your-root-url>/swagger`dla adresu URL, takiego jak .</span><span class="sxs-lookup"><span data-stu-id="67fb1-263">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="67fb1-264">Na rysunku 6-9 można również zobaczyć, jak można przetestować dowolną metodę interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-264">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Zrzut ekranu przedstawiający interfejsu firmy Swagger z dostępnymi narzędziami do testowania.](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

<span data-ttu-id="67fb1-266">**Rysunek 6-9**.</span><span class="sxs-lookup"><span data-stu-id="67fb1-266">**Figure 6-9**.</span></span> <span data-ttu-id="67fb1-267">Swashbuckle UI testowania katalogu/elementów Metody Interfejsu API</span><span class="sxs-lookup"><span data-stu-id="67fb1-267">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="67fb1-268">Swagger szczegóły interfejsu api interfejsu ze stawiana pokazuje przykład odpowiedzi i może służyć do wykonywania rzeczywistego interfejsu API, który jest doskonały do odnajdywania deweloperów.</span><span class="sxs-lookup"><span data-stu-id="67fb1-268">The Swagger UI API detail shows a sample of the response and can be used to execute the real API, which is great for developer discovery.</span></span> <span data-ttu-id="67fb1-269">Rysunek 6-10 pokazuje swagger JSON metadanych generowanych z mikrousługi eShopOnContainers (co jest, `http://<your-root-url>/swagger/v1/swagger.json` co narzędzia używane pod spodem) podczas żądania przy użyciu [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="67fb1-269">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Zrzut ekranu przedstawiający przykładowy ui listonosza z metadanymi Swagger JSON.](./media/data-driven-crud-microservice/swagger-json-metadata.png)

<span data-ttu-id="67fb1-271">**Rysunek 6-10**.</span><span class="sxs-lookup"><span data-stu-id="67fb1-271">**Figure 6-10**.</span></span> <span data-ttu-id="67fb1-272">Swagger JSON metadane</span><span class="sxs-lookup"><span data-stu-id="67fb1-272">Swagger JSON metadata</span></span>

<span data-ttu-id="67fb1-273">To takie proste.</span><span class="sxs-lookup"><span data-stu-id="67fb1-273">It is that simple.</span></span> <span data-ttu-id="67fb1-274">A ponieważ jest generowany automatycznie, metadane Swagger wzrośnie po dodaniu więcej funkcji do interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="67fb1-274">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="67fb1-275">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="67fb1-275">Additional resources</span></span>

- <span data-ttu-id="67fb1-276">**ASP.NET stron pomocy interfejsu API sieci Web przy użyciu programu Swagger** </span><span class="sxs-lookup"><span data-stu-id="67fb1-276">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="67fb1-277">**Zacznij korzystać z swashbuckle i ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="67fb1-277">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="67fb1-278">**Wprowadzenie do NSwag i ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="67fb1-278">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="67fb1-279">[Poprzedni](microservice-application-design.md)
> [następny](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="67fb1-279">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
