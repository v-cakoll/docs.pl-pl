---
title: Tworzenie prostego mikrousługi CRUD opartych na danych
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Tworzenie prostego mikrousługi CRUD opartych na danych
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 85694cbfe8c30b8430200f0ffbd01379f11b3f9d
ms.sourcegitcommit: c03eef711abe961a85db2b4d0715257d1524aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33848505"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="1b305-103">Tworzenie prostego mikrousługi CRUD opartych na danych</span><span class="sxs-lookup"><span data-stu-id="1b305-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="1b305-104">Tej sekcji przedstawiono, jak utworzyć prostą mikrousługi, który wykonuje tworzenia, odczytu, aktualizacji i operacji usuwania (CRUD) w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="1b305-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="1b305-105">Projektowanie proste mikrousługi CRUD</span><span class="sxs-lookup"><span data-stu-id="1b305-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="1b305-106">Z punktu widzenia projektu tego rodzaju konteneryzowanych mikrousługi jest bardzo prosty.</span><span class="sxs-lookup"><span data-stu-id="1b305-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="1b305-107">Prawdopodobnie jest prosty problem do rozwiązania lub prawdopodobnie implementacja jest tylko weryfikacji koncepcji.</span><span class="sxs-lookup"><span data-stu-id="1b305-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="1b305-108">**Rysunek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="1b305-108">**Figure 8-4**.</span></span> <span data-ttu-id="1b305-109">Wewnętrzny projektu dla prostego mikrousług CRUD</span><span class="sxs-lookup"><span data-stu-id="1b305-109">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="1b305-110">Przykładem tego rodzaju usługi simple dysk danych jest mikrousługi katalogu z eShopOnContainers przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b305-110">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="1b305-111">Ten typ usługi implementuje jej funkcji w jednym projekcie interfejsu API platformy ASP.NET Core sieci Web, które zawiera klasy dla swojego modelu danych, jej logiki biznesowej i jego kod dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="1b305-111">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="1b305-112">On również przechowuje powiązane dane w bazie danych uruchomione w programie SQL Server (jako innego kontenera do celów tworzenie/testowanie oprogramowania), ale może być również regularne dowolnego hosta programu SQL Server, jak pokazano na rysunku 8-5.</span><span class="sxs-lookup"><span data-stu-id="1b305-112">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="1b305-113">**Rysunek 8-5**.</span><span class="sxs-lookup"><span data-stu-id="1b305-113">**Figure 8-5**.</span></span> <span data-ttu-id="1b305-114">Proste mikrousługi data-driven/CRUD projektu</span><span class="sxs-lookup"><span data-stu-id="1b305-114">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="1b305-115">Podczas tworzenia tego rodzaju usługi, wystarczy [platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/) i ORM lub dostępu do danych interfejsu API, takich jak [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="1b305-115">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="1b305-116">Można także wygenerować [Swagger](https://swagger.io/) metadanych automatycznie za pomocą [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) aby opisać co oferty usługi, zgodnie z objaśnieniem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1b305-116">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="1b305-117">Należy pamiętać, że uruchomiona bez konieczności obsługi administracyjnej bazy danych w chmurze lub lokalnie z serwera bazy danych, takich jak SQL Server w kontenerze Docker jest doskonały dla środowisk deweloperskich, ponieważ wszystkie zależności może zawierać maksymalnie i.</span><span class="sxs-lookup"><span data-stu-id="1b305-117">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="1b305-118">Jest to bardzo wygodne, gdy uruchamianie integracji testów.</span><span class="sxs-lookup"><span data-stu-id="1b305-118">This is very convenient when running integration tests.</span></span> <span data-ttu-id="1b305-119">Jednak dla środowisk produkcyjnych uruchomione w kontenerze serwer bazy danych nie jest zalecane, ponieważ zwykle nie uzyskasz wysokiej dostępności z tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="1b305-119">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="1b305-120">W środowisku produkcyjnym na platformie Azure zaleca się korzystanie z bazy danych SQL Azure lub innych technologii bazy danych, która może zapewnić wysoką dostępność i wysoką skalowalność.</span><span class="sxs-lookup"><span data-stu-id="1b305-120">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="1b305-121">Na przykład podejścia NoSQL, możesz wybrać usługi DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="1b305-121">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="1b305-122">Na koniec, edytując plik Dockerfile i docker-compose.yml plików metadanych, można skonfigurować tworzenia obrazu tego kontenera — jakie podstawowy obraz będzie używać plus projektowania ustawień, takich jak nazwy wewnętrznych i zewnętrznych i portów TCP.</span><span class="sxs-lookup"><span data-stu-id="1b305-122">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="1b305-123">Implementowanie prostego mikrousługi CRUD z platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1b305-123">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="1b305-124">Aby wdrożyć prosty mikrousługi CRUD przy użyciu platformy .NET Core i Visual Studio, możesz uruchomić tworzenie prostego projektu interfejsu API platformy ASP.NET Core sieci Web (uruchomiona .NET Core, można uruchomić na hoście systemu Linux Docker), jak pokazano na rysunku 8-6.</span><span class="sxs-lookup"><span data-stu-id="1b305-124">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="1b305-125">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="1b305-125">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="1b305-126">**Rysunek 8-6**.</span><span class="sxs-lookup"><span data-stu-id="1b305-126">**Figure 8-6**.</span></span> <span data-ttu-id="1b305-127">Tworzenie projektu interfejsu API platformy ASP.NET Core sieci Web w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b305-127">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="1b305-128">Po utworzeniu projektu, można zaimplementować kontrolerów MVC, tak jak w innych projektów interfejsu API sieci Web, przy użyciu interfejsu API programu Entity Framework lub innego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="1b305-128">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="1b305-129">W nowym projekcie interfejsu API sieci Web widać, że tylko zależności masz w tym mikrousługi znajduje się na platformy ASP.NET Core, sam.</span><span class="sxs-lookup"><span data-stu-id="1b305-129">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="1b305-130">Wewnętrznie, w ramach `Microsoft.AspNetCore.All` zależności, odwołuje się ona do programu Entity Framework i wiele innych pakietów Nuget programu .NET Core, jak pokazano w rysunek 8-7.</span><span class="sxs-lookup"><span data-stu-id="1b305-130">Internally, within the `Microsoft.AspNetCore.All` dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="1b305-131">**Rysunek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="1b305-131">**Figure 8-7**.</span></span> <span data-ttu-id="1b305-132">Zależności w prosty mikrousługi CRUD interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="1b305-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="1b305-133">Implementowanie usług interfejsu API sieci Web CRUD z programu Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1b305-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="1b305-134">Program Entity Framework (EF) Core to lekkie, rozszerzalny, i technologii dostępu do wersji i platform popularnych danych programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1b305-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="1b305-135">Podstawowe EF jest obiektów relacyjnych mapowania (ORM), który umożliwia deweloperom platformy .NET do pracy z bazą danych przy użyciu obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1b305-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="1b305-136">Mikrousługi katalogu wykorzystuje EF i dostawcy programu SQL Server, ponieważ jego baz danych jest uruchomione w kontenerze z programem SQL Server dla systemu Linux Docker obrazu.</span><span class="sxs-lookup"><span data-stu-id="1b305-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="1b305-137">Niemniej jednak bazy danych mogą być wdrożone do programu SQL Server, takich jak Windows lokalnymi lub bazy danych SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="1b305-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="1b305-138">Jedyną operacją, której należy zmienić to ciąg połączenia w mikrousługi interfejsu API sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1b305-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>


#### <a name="the-data-model"></a><span data-ttu-id="1b305-139">Model danych</span><span class="sxs-lookup"><span data-stu-id="1b305-139">The data model</span></span>

<span data-ttu-id="1b305-140">Podstawowych EF dostęp do danych odbywa się za pomocą modelu.</span><span class="sxs-lookup"><span data-stu-id="1b305-140">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="1b305-141">Model składa się z klas jednostek i pochodne kontekst reprezentujący sesji z bazy danych, umożliwiając zapytania i zapisać dane.</span><span class="sxs-lookup"><span data-stu-id="1b305-141">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="1b305-142">Generowanie modelu z istniejącej bazy danych, ręcznie kod modelu do dopasowania bazy danych lub użyj EF migracji do tworzenia bazy danych z modelu (i rozwijać go zgodnie z modelem zmienia się wraz z upływem czasu).</span><span class="sxs-lookup"><span data-stu-id="1b305-142">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="1b305-143">W katalogu mikrousługi użyto ostatniego podejście.</span><span class="sxs-lookup"><span data-stu-id="1b305-143">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="1b305-144">Widać przykład klasy jednostki CatalogItem w poniższym przykładzie kodu, który jest prosty zwykły stary obiekt CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) klasy jednostka.</span><span class="sxs-lookup"><span data-stu-id="1b305-144">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="1b305-145">Należy również DbContext, reprezentujący sesji z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="1b305-145">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="1b305-146">Dla mikrousługi katalogu klasa CatalogContext pochodzi od klasy podstawowej typu DbContext, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1b305-146">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="1b305-147">Mogą mieć dodatkowe `DbContext` implementacji.</span><span class="sxs-lookup"><span data-stu-id="1b305-147">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="1b305-148">Na przykład w mikrousługi Catalog.API próbki, istnieje drugi `DbContext` o nazwie `CatalogContextSeed` gdzie automatycznie wypełni przykładowych danych po raz pierwszy próbuje uzyskać dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="1b305-148">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="1b305-149">Ta metoda jest przydatna, dane demonstracyjne i automatyczne scenariuszy testowych, jak również.</span><span class="sxs-lookup"><span data-stu-id="1b305-149">This method is useful for demo data and for automated testing scenarios, as well.</span></span> <span data-ttu-id="1b305-150">W ramach `DbContext`, możesz użyć `OnModelCreating` metodę w celu dostosowania mapowania jednostek w bazie danych i obiektów z i inne [punkty rozszerzeń EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="1b305-150">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings with and other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="1b305-151">Wykonywanie zapytania na danych z kontrolerów interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="1b305-151">Querying data from Web API controllers</span></span>

<span data-ttu-id="1b305-152">Wystąpienia klas jednostek zwykle są pobierane z bazy danych przy użyciu języka zintegrowane zapytania (LINQ), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1b305-152">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="1b305-153">Zapisywanie danych</span><span class="sxs-lookup"><span data-stu-id="1b305-153">Saving data</span></span>

<span data-ttu-id="1b305-154">Dane są tworzone, usunięte i zmodyfikowane w bazie danych za pomocą wystąpień klas jednostek.</span><span class="sxs-lookup"><span data-stu-id="1b305-154">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="1b305-155">Możesz dodać kod, jak w następującym ustalony przykładzie (danych testowych, w tym przypadku) z kontrolerami interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1b305-155">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="1b305-156">Iniekcji zależności w kontrolery ASP.NET Core i interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="1b305-156">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="1b305-157">W ASP.NET Core można użyć zależności Iniekcja poza pole.</span><span class="sxs-lookup"><span data-stu-id="1b305-157">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="1b305-158">Nie trzeba skonfigurować kontener Inwersja kontroli (IoC) innej firmy, chociaż z preferowanych kontenera IoC można podłączyć do infrastruktury platformy ASP.NET Core, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="1b305-158">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="1b305-159">W takim przypadku oznacza to, że użytkownik bezpośrednio wstrzyknąć wymagane DBContext EF lub dodatkowe repozytoria za pośrednictwem konstruktora kontrolera.</span><span class="sxs-lookup"><span data-stu-id="1b305-159">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="1b305-160">W powyższym przykładzie `CatalogController` klasy, możemy są wstrzyknięcie obiektu `CatalogContext` wpisz oraz innych obiektów za pomocą `CatalogController()` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1b305-160">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="1b305-161">Ważne konfiguracji, aby skonfigurować w projekcie interfejsu API sieci Web jest rejestrowanie klasy DbContext do kontenera IoC usługi.</span><span class="sxs-lookup"><span data-stu-id="1b305-161">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="1b305-162">Zwykle jest to ustalane dlatego w `Startup` klasy przez wywołanie metody `services.AddDbContext<DbContext>()` metody w ramach `ConfigureServices()` metody, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1b305-162">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="1b305-163">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="1b305-163">Additional resources</span></span>

-   <span data-ttu-id="1b305-164">**Wykonywanie zapytania na danych**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="1b305-164">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="1b305-165">**Zapisywanie danych**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="1b305-165">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="1b305-166">Zmienne string i środowiska połączenia bazy danych używanych przez kontenery Docker</span><span class="sxs-lookup"><span data-stu-id="1b305-166">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="1b305-167">Można użyć ustawień platformy ASP.NET Core i Dodaj właściwości ConnectionString do pliku settings.json, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1b305-167">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="1b305-168">Plik settings.json może mieć wartości domyślnej dla właściwości ConnectionString lub inne właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b305-168">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="1b305-169">Jednak te właściwości zostaną zastąpione przez wartości zmiennych środowiskowych, które określisz w pliku docker compose.override.yml przy użyciu rozwiązania Docker.</span><span class="sxs-lookup"><span data-stu-id="1b305-169">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="1b305-170">Od plików docker-compose.yml lub docker compose.override.yml można inicjowania tych zmiennych środowiskowych, tym Docker skonfiguruje je jako zmiennych środowiskowych systemu operacyjnego, jak pokazano w następującym pliku docker compose.override.yml (połączenia ciąg i innych wierszy opakowywania w tym przykładzie, ale nie będzie zawijany w pliku kodu).</span><span class="sxs-lookup"><span data-stu-id="1b305-170">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own code file).</span></span>

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

<span data-ttu-id="1b305-171">Plik docker-compose.yml na poziomie rozwiązania nie są tylko bardziej elastyczne niż pliki konfiguracji na poziomie projektu lub mikrousługi, ale również wyższy poziom bezpieczeństwa w razie przesłonięcia zmienne środowiskowe zadeklarowane na pliki docker-compose z wartości ustawione na narzędziami wdrażania, takie jak z zadania wdrażania programu VSTS Docker.</span><span class="sxs-lookup"><span data-stu-id="1b305-171">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from VSTS Docker deployment tasks.</span></span> 

<span data-ttu-id="1b305-172">Ponadto można uzyskać tę wartość w kodzie za pomocą konfiguracji\["ConnectionString"\], jak pokazano w metodzie ConfigureServices w wcześniejszego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="1b305-172">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="1b305-173">Jednak dla środowisk produkcyjnych, możesz rozpocząć eksplorowanie dodatkowe sposoby na jak przechowywać hasła, takie jak parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="1b305-173">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="1b305-174">Zazwyczaj które będą zarządzane przez z wybranym orchestrator, jak można zrobić za pomocą [Docker Swarm zarządzania kluczy tajnych](https://docs.docker.com/engine/swarm/secrets/).</span><span class="sxs-lookup"><span data-stu-id="1b305-174">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="1b305-175">Implementowanie przechowywania wersji w interfejsów API sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1b305-175">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="1b305-176">Po zmianie wymagań biznesowych, nowej kolekcji zasobów, które mogą zostać dodane, może spowodować zmianę relacje między zasobami i struktury danych w zasoby mogą zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="1b305-176">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="1b305-177">Aktualizowanie interfejsu API sieci Web, do obsługi nowych wymagań w zakresie jest stosunkowo prosta proces, ale należy wziąć pod uwagę wpływ, mające takie zmiany w aplikacji klienckich korzystających z interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1b305-177">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="1b305-178">Mimo że developer projektowanie i implementowanie interfejs API sieci Web ma pełną kontrolę nad tego interfejsu API, deweloper nie ma ten sam stopień kontroli nad aplikacji klienckich, które mogą zostać utworzone przez organizacje innej operacyjnego zdalnie.</span><span class="sxs-lookup"><span data-stu-id="1b305-178">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="1b305-179">Przechowywanie wersji umożliwia interfejsu API sieci Web wskazać, funkcje i zasoby, które ujawnia on.</span><span class="sxs-lookup"><span data-stu-id="1b305-179">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="1b305-180">Aplikacja kliencka następnie do przesyłania żądań do określonej wersji funkcji lub zasobu.</span><span class="sxs-lookup"><span data-stu-id="1b305-180">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="1b305-181">Istnieją różne podejścia do implementacji przechowywania wersji:</span><span class="sxs-lookup"><span data-stu-id="1b305-181">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="1b305-182">Przechowywanie wersji identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="1b305-182">URI versioning</span></span>

-   <span data-ttu-id="1b305-183">Przechowywanie wersji ciąg zapytania</span><span class="sxs-lookup"><span data-stu-id="1b305-183">Query string versioning</span></span>

-   <span data-ttu-id="1b305-184">Przechowywanie wersji nagłówka</span><span class="sxs-lookup"><span data-stu-id="1b305-184">Header versioning</span></span>

<span data-ttu-id="1b305-185">Ciąg zapytania i przechowywanie wersji identyfikatora URI są najprostszym do zaimplementowania.</span><span class="sxs-lookup"><span data-stu-id="1b305-185">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="1b305-186">Przechowywanie wersji nagłówka jest dobre rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="1b305-186">Header versioning is a good approach.</span></span> <span data-ttu-id="1b305-187">Jednak wersji nagłówka nie jako jawne i prostego jako versioning identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="1b305-187">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="1b305-188">Ponieważ versioning adres URL jest najprostsza i najbardziej jawne, eShopOnContainers Przykładowa aplikacja korzysta z wersji identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="1b305-188">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="1b305-189">Zarządzanie wersjami identyfikatora URI, tak jak eShopOnContainers przykładowej aplikacji za każdym razem zmodyfikować interfejsu API sieci Web lub zmienić schemat zasobów, możesz dodać numer wersji do identyfikatora URI dla każdego zasobu.</span><span class="sxs-lookup"><span data-stu-id="1b305-189">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="1b305-190">Istniejące identyfikatory URI powinno być kontynuowane do działania jako przed, zwracanie zasoby, które są zgodne ze schematem odpowiadający żądanej wersji.</span><span class="sxs-lookup"><span data-stu-id="1b305-190">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="1b305-191">Jak pokazano w poniższym przykładzie kodu, wersja można ustawić za pomocą atrybutu trasy w interfejsie API sieci Web, co sprawia, że wersja jawne w identyfikatorze URI (v1, w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="1b305-191">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="1b305-192">Ten mechanizm versioning jest prosta i zależy od serwera routingu żądania do odpowiedniego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1b305-192">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="1b305-193">Jednak bardziej zaawansowanych wersji i najlepszą metodę przy użyciu REST, należy użyć hipermedialnych i implementować [HATEOAS (Hypertext jako stan aparatu aplikacji)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="1b305-193">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1b305-194">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="1b305-194">Additional resources</span></span>

-   <span data-ttu-id="1b305-195">**Scott Hanselman. Przechowywanie wersji interfejsu API RESTful sieci Web platformy ASP.NET Core prosty**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="1b305-195">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="1b305-196">**Przechowywanie wersji interfejs API RESTful sieci web**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span><span class="sxs-lookup"><span data-stu-id="1b305-196">**Versioning a RESTful web API**
[*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span></span>

-   <span data-ttu-id="1b305-197">**Fielding Royowi. Przechowywanie wersji, hipermedialnych i REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="1b305-197">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="1b305-198">Generowanie metadanych struktury Swagger opis interfejsu API platformy ASP.NET Core sieci Web</span><span class="sxs-lookup"><span data-stu-id="1b305-198">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="1b305-199">[Swagger](https://swagger.io/) jest framework często używane typu open source zabezpieczona przy dużych ekosystemu narzędzia ułatwiające projektu, kompilacji, dokumentów i korzystanie z API RESTful.</span><span class="sxs-lookup"><span data-stu-id="1b305-199">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="1b305-200">Staje się coraz standardowego dla interfejsów API opis metadanych domeny.</span><span class="sxs-lookup"><span data-stu-id="1b305-200">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="1b305-201">Powinny zawierać metadane programu Swagger z dowolnego rodzaju mikrousługi, opartych na danych mikrousług lub bardziej zaawansowane mikrousług oparte na domenie (zgodnie z objaśnieniem w następnej sekcji).</span><span class="sxs-lookup"><span data-stu-id="1b305-201">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="1b305-202">Struktury Swagger to specyfikację struktury Swagger jest metadanych opis interfejsu API w pliku JSON lub yaml programu.</span><span class="sxs-lookup"><span data-stu-id="1b305-202">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="1b305-203">Specyfikacja tworzy RESTful kontrakt interfejsu API, określające wszystkich jej zasobów i operacji w obu readable człowieka i machine formacie ułatwiający projektowanie, odnajdywania i integracji.</span><span class="sxs-lookup"><span data-stu-id="1b305-203">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="1b305-204">Specyfikacja stanowi podstawę specyfikacji OpenAPI (amerykańskich) i został napisany w otwarte, przejrzyste i współpracy społeczności normalizacji sposób zdefiniowanych interfejsów RESTful.</span><span class="sxs-lookup"><span data-stu-id="1b305-204">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="1b305-205">Specyfikacja definiuje strukturę jak usługi mogą być wykrywane i jak zrozumienie możliwości.</span><span class="sxs-lookup"><span data-stu-id="1b305-205">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="1b305-206">Aby uzyskać więcej informacji, w tym edytorze sieci web i przykłady specyfikacji Swagger firm, takich jak serwis Spotify, pełny zapas czasu i firmy Microsoft, zobacz witrynę programu Swagger (<https://swagger.io/>).</span><span class="sxs-lookup"><span data-stu-id="1b305-206">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io/>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="1b305-207">Dlaczego warto używać struktury Swagger?</span><span class="sxs-lookup"><span data-stu-id="1b305-207">Why use Swagger?</span></span>

<span data-ttu-id="1b305-208">Poniżej są główne powody generować metadane programu Swagger dla interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="1b305-208">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="1b305-209">**Możliwość dla innych produktów automatycznie używać i integrować swoje interfejsy API**.</span><span class="sxs-lookup"><span data-stu-id="1b305-209">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="1b305-210">Dziesiątki produktów i [narzędzia komercyjnego](https://swagger.io/commercial-tools/) i wiele [bibliotek i platform](https://swagger.io/open-source-integrations/) obsługuje struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="1b305-210">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="1b305-211">Firma Microsoft ma wysokiego poziomu produktów i narzędzi, które mogą automatycznie używać API podstawie struktury Swagger, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="1b305-211">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="1b305-212">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="1b305-212">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="1b305-213">Można automatycznie generować klasy klienta .NET wywoływania struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="1b305-213">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="1b305-214">To narzędzie może być używane z poziomu interfejsu wiersza polecenia i integruje się również z programu Visual Studio dla łatwe za pośrednictwem graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1b305-214">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="1b305-215">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="1b305-215">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="1b305-216">Można automatycznie [użycia i integracja z interfejsem API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) do wysokiego poziomu przepływu pracy Microsoft Flow bez umiejętności programowania wymagane.</span><span class="sxs-lookup"><span data-stu-id="1b305-216">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="1b305-217">[Rozwiązanie Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="1b305-217">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="1b305-218">Można automatycznie korzystać z interfejsu API [aplikacji mobilnych w rozwiązaniu PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) skompilowanej za pomocą [Studio rozwiązania PowerApps](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), nie umiejętności programowania wymagane.</span><span class="sxs-lookup"><span data-stu-id="1b305-218">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="1b305-219">[Usługa aplikacji Azure Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="1b305-219">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="1b305-220">Można automatycznie [użycia i integrowanie interfejsu API Azure aplikację usługi aplikacji logiki](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), nie umiejętności programowania wymagane.</span><span class="sxs-lookup"><span data-stu-id="1b305-220">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="1b305-221">**Możliwość automatycznego generowania dokumentacji interfejsu API**.</span><span class="sxs-lookup"><span data-stu-id="1b305-221">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="1b305-222">Podczas tworzenia dużych interfejsy API RESTful, takich jak złożonych aplikacji opartych na mikrousługi należy obsługiwać wiele punktów końcowych z modelami danych używania w ładunkach żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1b305-222">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="1b305-223">Posiadanie odpowiednich dokumentacji i o stałych explorer interfejsu API, jak pobrać z programu Swagger, jest klucza w przypadku powodzenia interfejsu API i przyjęcia przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="1b305-223">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="1b305-224">Metadane programu swagger dla jest Flow firmy Microsoft, PowerApps i usługi Azure Logic Apps Użyj zrozumienie, jak używać interfejsów API i nawiązywania z nimi.</span><span class="sxs-lookup"><span data-stu-id="1b305-224">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="1b305-225">Jak zautomatyzować interfejsu API programu Swagger Generowanie metadanych przy użyciu pakietu Swashbuckle NuGet</span><span class="sxs-lookup"><span data-stu-id="1b305-225">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="1b305-226">Generowanie metadanych struktury Swagger ręcznie (w pliku JSON lub yaml programu) może być konieczność.</span><span class="sxs-lookup"><span data-stu-id="1b305-226">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="1b305-227">Jednak można automatyzować odnajdywanie interfejsów API, usług interfejsu API sieci Web ASP.NET przy użyciu [pakietu Swashbuckle NuGet](http://aka.ms/swashbuckledotnetcore) do dynamicznego generowania metadanych interfejsu API programu Swagger.</span><span class="sxs-lookup"><span data-stu-id="1b305-227">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="1b305-228">Pakiet Swashbuckle automatycznie generuje metadane programu Swagger dla projektów ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="1b305-228">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="1b305-229">Obsługuje on projekty interfejsu API platformy ASP.NET Core sieci Web i tradycyjnego interfejsu API sieci Web ASP.NET i innych wersji, takie jak aplikacji interfejsu API platformy Azure, aplikacji mobilnej Azure, sieć szkieletowa usług Azure mikrousług opartych na programie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1b305-229">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="1b305-230">Obsługuje ona również zwykły wdrożone na kontenery, podobnie jak w aplikacji odwołanie do interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1b305-230">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="1b305-231">Pakiet Swashbuckle łączy Explorer interfejsu API i struktury Swagger lub [interfejsu użytkownika programu swagger](https://github.com/swagger-api/swagger-ui) zapewnienie sformatowanego odnajdywania i dokumentacji wystąpić przez użytkowników interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="1b305-231">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="1b305-232">Oprócz jego generator aparat metadanych struktury Swagger Swashbuckle zawiera osadzony wersji struktury swagger interfejsu użytkownika, który go automatycznie posłuży się po zainstalowaniu pakietu Swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="1b305-232">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="1b305-233">Oznacza to, że można rozszerzyć interfejsu API z odnajdywaniem nieuprzywilejowany interfejsu użytkownika, aby pomóc deweloperom korzystanie z interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="1b305-233">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="1b305-234">Wymaga niewielką ilość kodu i konserwacji, ponieważ jest ona generowana automatycznie, co pozwala skupić się na tworzeniu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="1b305-234">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="1b305-235">Wynik dla interfejsu API Explorer wygląda podobnie jak rysunek 8-8.</span><span class="sxs-lookup"><span data-stu-id="1b305-235">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="1b305-236">**Rysunek 8-8**.</span><span class="sxs-lookup"><span data-stu-id="1b305-236">**Figure 8-8**.</span></span> <span data-ttu-id="1b305-237">Pakiet Swashbuckle interfejsu API Eksploratora oparte na metadanych struktury Swagger — eShopOnContainers katalogu mikrousługi</span><span class="sxs-lookup"><span data-stu-id="1b305-237">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="1b305-238">W Eksploratorze interfejsu API nie jest ważne jest, w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="1b305-238">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="1b305-239">Po utworzeniu interfejsu API sieci Web, który można opisania siebie w metadanych struktury Swagger interfejsu API można bezproblemowo z narzędzi na podstawie struktury Swagger, w tym generatory kodu klasy serwera proxy klienta, które mogą współpracować z wielu platform.</span><span class="sxs-lookup"><span data-stu-id="1b305-239">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="1b305-240">Na przykład, jak wspomniano [AutoRest](https://github.com/Azure/AutoRest) automatycznie wygeneruje klasy klienta .NET.</span><span class="sxs-lookup"><span data-stu-id="1b305-240">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="1b305-241">Ale dodatkowych narzędzi, takich jak [swagger codegen](https://github.com/swagger-api/swagger-codegen) są również dostępne, która zezwala na generowanie kodu klienta interfejsu API biblioteki klas zastępczych serwera i dokumentacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="1b305-241">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="1b305-242">Obecnie Swashbuckle składa się z dwóch kilka pakietów NuGet wewnętrznego w obszarze wysokiego poziomu metapakiet [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) w wersji 1.0.0 lub nowszej dla aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1b305-242">Currently, Swashbuckle consists of two several internal NuGet packages under the high-level meta- package [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) version 1.0.0 or later for ASP.NET Core applications.</span></span>

<span data-ttu-id="1b305-243">Po zainstalowaniu tych pakietów NuGet w projekcie interfejsu API sieci Web, należy skonfigurować struktury Swagger w klasie uruchamiania zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="1b305-243">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

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

<span data-ttu-id="1b305-244">Po zakończeniu możesz uruchomić aplikację i Przeglądaj następujących interfejsu użytkownika i JSON programu Swagger punktów końcowych przy użyciu adresów URL, takich jak te:</span><span class="sxs-lookup"><span data-stu-id="1b305-244">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

<span data-ttu-id="1b305-245">Widać wcześniej wygenerowany interfejsu użytkownika utworzone przez pakiet Swashbuckle dla danego adresu URL, takie jak http://&lt;adres url katalogu głównego &gt; /swagger/interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1b305-245">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="1b305-246">W rysunek 8-9 widoczny jest także jak można przetestować dowolnej metody interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="1b305-246">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="1b305-247">**Rysunek 8-9**.</span><span class="sxs-lookup"><span data-stu-id="1b305-247">**Figure 8-9**.</span></span> <span data-ttu-id="1b305-248">Interfejs użytkownika Swashbuckle testowania metody interfejsu API/wszystkich elementów katalogu</span><span class="sxs-lookup"><span data-stu-id="1b305-248">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="1b305-249">Rysunek 8-10 przedstawia metadanych JSON programu Swagger generowane na podstawie mikrousługi eShopOnContainers (czyli narzędzia Użyj poniżej) na żądanie &lt;adres url katalogu głównego&gt;/swagger/v1/swagger.json przy użyciu [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="1b305-249">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="1b305-250">**Rysunek 8-10**.</span><span class="sxs-lookup"><span data-stu-id="1b305-250">**Figure 8-10**.</span></span> <span data-ttu-id="1b305-251">Metadane JSON programu swagger</span><span class="sxs-lookup"><span data-stu-id="1b305-251">Swagger JSON metadata</span></span>

<span data-ttu-id="1b305-252">Jest to proste.</span><span class="sxs-lookup"><span data-stu-id="1b305-252">It is that simple.</span></span> <span data-ttu-id="1b305-253">A ponieważ jest ona generowana automatycznie, metadane programu Swagger wzrośnie po dodaniu więcej funkcji do interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="1b305-253">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1b305-254">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="1b305-254">Additional resources</span></span>

-   <span data-ttu-id="1b305-255">**Strony sieci Web ASP.NET interfejsu API pomocy przy użyciu programu Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="1b305-255">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1b305-256">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="1b305-256">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span></span>
