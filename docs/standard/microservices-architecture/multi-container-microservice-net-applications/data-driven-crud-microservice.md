---
title: "Tworzenie prostego mikrousługi CRUD opartych na danych"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Tworzenie prostego mikrousługi CRUD opartych na danych"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b814d344f2c78e7cf57f9e2896cf1d6b52db38d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Tworzenie prostego mikrousługi CRUD opartych na danych

Tej sekcji przedstawiono, jak utworzyć prostą mikrousługi, który wykonuje tworzenia, odczytu, aktualizacji i operacji usuwania (CRUD) w źródle danych.

## <a name="designing-a-simple-crud-microservice"></a>Projektowanie proste mikrousługi CRUD

Z punktu widzenia projektu tego rodzaju konteneryzowanych mikrousługi jest bardzo prosty. Prawdopodobnie jest prosty problem do rozwiązania lub prawdopodobnie implementacja jest tylko weryfikacji koncepcji.

![](./media/image4.png)

**Rysunek 8-4**. Wewnętrzny projektu dla prostego mikrousług CRUD

Przykładem tego rodzaju usługi simple dysk danych jest mikrousługi katalogu z eShopOnContainers przykładowej aplikacji. Ten typ usługi implementuje jej funkcji w jednym projekcie interfejsu API platformy ASP.NET Core sieci Web, które zawiera klasy dla swojego modelu danych, jej logiki biznesowej i jego kod dostępu do danych. On również przechowuje powiązane dane w bazie danych uruchomione w programie SQL Server (jako innego kontenera do celów tworzenie/testowanie oprogramowania), ale może być również regularne dowolnego hosta programu SQL Server, jak pokazano na rysunku 8-5.

![](./media/image5.png)

**Rysunek 8-5**. Proste mikrousługi data-driven/CRUD projektu

Podczas tworzenia tego rodzaju usługi, wystarczy [platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/) i ORM lub dostępu do danych interfejsu API, takich jak [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Można także wygenerować [Swagger](http://swagger.io/) metadanych automatycznie za pomocą [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) aby opisać co oferty usługi, zgodnie z objaśnieniem w następnej sekcji.

Należy pamiętać, że uruchomiona bez konieczności obsługi administracyjnej bazy danych w chmurze lub lokalnie z serwera bazy danych, takich jak SQL Server w kontenerze Docker jest doskonały dla środowisk deweloperskich, ponieważ wszystkie zależności może zawierać maksymalnie i. Jest to bardzo wygodne, gdy uruchamianie integracji testów. Jednak dla środowisk produkcyjnych uruchomione w kontenerze serwer bazy danych nie jest zalecane, ponieważ zwykle nie uzyskasz wysokiej dostępności z tego podejścia. W środowisku produkcyjnym na platformie Azure zaleca się korzystanie z bazy danych SQL Azure lub innych technologii bazy danych, która może zapewnić wysoką dostępność i wysoką skalowalność. Na przykład podejścia NoSQL, możesz wybrać usługi DocumentDB.

Na koniec, edytując plik Dockerfile i docker-compose.yml plików metadanych, można skonfigurować tworzenia obrazu tego kontenera — jakie podstawowy obraz będzie używać plus projektowania ustawień, takich jak nazwy wewnętrznych i zewnętrznych i portów TCP. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementowanie prostego mikrousługi CRUD z platformy ASP.NET Core

Aby wdrożyć prosty mikrousługi CRUD przy użyciu platformy .NET Core i Visual Studio, możesz uruchomić tworzenie prostego projektu interfejsu API platformy ASP.NET Core sieci Web (uruchomiona .NET Core, można uruchomić na hoście systemu Linux Docker), jak pokazano na rysunku 8-6.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Rysunek 8-6**. Tworzenie projektu interfejsu API platformy ASP.NET Core sieci Web w programie Visual Studio

Po utworzeniu projektu, można zaimplementować kontrolerów MVC, tak jak w innych projektów interfejsu API sieci Web, przy użyciu interfejsu API programu Entity Framework lub innego interfejsu API. W projekcie eShopOnContainers.Catalog.API widoczny czy głównego zależności dla tego mikrousługi są tylko platformy ASP.NET Core, samego programu Entity Framework i Swashbuckle, jak pokazano w rysunek 8-7.

![](./media/image8.PNG)

**Rysunek 8-7**. Zależności w prosty mikrousługi CRUD interfejsu API sieci Web

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implementowanie usług interfejsu API sieci Web CRUD z programu Entity Framework Core

Program Entity Framework (EF) Core to lekkie, rozszerzalny, i technologii dostępu do wersji i platform popularnych danych programu Entity Framework. Podstawowe EF jest obiektów relacyjnych mapowania (ORM), który umożliwia deweloperom platformy .NET do pracy z bazą danych przy użyciu obiektów platformy .NET.

Mikrousługi katalogu wykorzystuje EF i dostawcy programu SQL Server, ponieważ jego baz danych jest uruchomione w kontenerze z programem SQL Server dla systemu Linux Docker obrazu. Niemniej jednak bazy danych mogą być wdrożone do programu SQL Server, takich jak Windows lokalnymi lub bazy danych SQL Azure. Jedyną operacją, której należy zmienić to ciąg połączenia w mikrousługi interfejsu API sieci Web platformy ASP.NET.

#### <a name="add-entity-framework-core-to-your-dependencies"></a>Dodaj Entity Framework Core do zależności

Można zainstalować pakietu NuGet dla dostawcy bazy danych, którego chcesz użyć, w tym przypadku serwera SQL z wewnątrz środowiska IDE programu Visual Studio lub z konsoli programu NuGet. Użyj następującego polecenia:

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a>Model danych

Podstawowych EF dostęp do danych odbywa się za pomocą modelu. Model składa się z klas jednostek i pochodne kontekst reprezentujący sesji z bazy danych, umożliwiając zapytania i zapisać dane. Generowanie modelu z istniejącej bazy danych, ręcznie kod modelu do dopasowania bazy danych lub użyj EF migracji do tworzenia bazy danych z modelu (i rozwijać go zgodnie z modelem zmienia się wraz z upływem czasu). W katalogu mikrousługi użyto ostatniego podejście. Widać przykład klasy jednostki CatalogItem w poniższym przykładzie kodu, który jest prosty zwykły stary obiekt CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) klasy jednostka.

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public CatalogItem() { }
}
```

Należy również DbContext, reprezentujący sesji z bazą danych. Dla mikrousługi katalogu klasa CatalogContext pochodzi od klasy podstawowej typu DbContext, jak pokazano w poniższym przykładzie:

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

Masz dodatkowy kod w celu wykonania DbContext. Na przykład w aplikacji przykładowej mamy metody OnModelCreating w klasie CatalogContext automatycznie wypełni przykładowych danych po raz pierwszy próbuje uzyskać dostępu do bazy danych. Ta metoda jest przydatna do danych demonstracyjnych. Umożliwia także metody OnModelCreating dostosować mapowania jednostek bazie danych i obiektów z wielu innych [punkty rozszerzeń EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

Można można zobaczyć więcej informacji o OnModelCreating w [implementacja warstwa trwałości infrastruktury z programu Entity Framework Core](#implementing_infrastructure_persistence) sekcji dalej w tej sekcji.

##### <a name="querying-data-from-web-api-controllers"></a>Wykonywanie zapytania na danych z kontrolerów interfejsu API sieci Web

Wystąpienia klas jednostek zwykle są pobierane z bazy danych przy użyciu języka zintegrowane zapytania (LINQ), jak pokazano w poniższym przykładzie:

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
        _catalogIntegrationEventService = catalogIntegrationEventService ??
           throw new ArgumentNullException(nameof(catalogIntegrationEventService));
        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
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

##### <a name="saving-data"></a>Zapisywanie danych

Dane są tworzone, usunięte i zmodyfikowane w bazie danych za pomocą wystąpień klas jednostek. Możesz dodać kod, jak w następującym ustalony przykładzie (danych testowych, w tym przypadku) z kontrolerami interfejsu API sieci Web.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Iniekcji zależności w kontrolery ASP.NET Core i interfejsu API sieci Web

W ASP.NET Core można użyć zależności Iniekcja poza pole. Nie trzeba skonfigurować kontener Inwersja kontroli (IoC) innej firmy, chociaż z preferowanych kontenera IoC można podłączyć do infrastruktury platformy ASP.NET Core, jeśli chcesz. W takim przypadku oznacza to, że użytkownik bezpośrednio wstrzyknąć wymagane DBContext EF lub dodatkowe repozytoria za pośrednictwem konstruktora kontrolera. W powyższym przykładzie klasy CatalogController możemy są wstrzyknięcie CatalogContext typu obiektu oraz innych obiektów za pomocą konstruktora CatalogController.

Ważne konfiguracji, aby skonfigurować w projekcie interfejsu API sieci Web jest rejestrowanie klasy DbContext do kontenera IoC usługi. Zwykle w tym Klasa początkowa poprzez wywołanie usługi. Metoda AddDbContext wewnątrz metody ConfigureServices, jak pokazano w poniższym przykładzie:

```csharp
public void ConfigureServices(IServiceCollection services)
{
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

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wykonywanie zapytania na danych**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **Zapisywanie danych**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Zmienne string i środowiska połączenia bazy danych używanych przez kontenery Docker

Można użyć ustawień platformy ASP.NET Core i Dodaj właściwości ConnectionString do pliku settings.json, jak pokazano w poniższym przykładzie:

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

Plik settings.json może mieć wartości domyślnej dla właściwości ConnectionString lub inne właściwości. Jednak te właściwości zostaną zastąpione przez wartości zmiennych środowiskowych, które można określić w pliku docker compose.override.yml.

Od plików docker-compose.yml lub docker compose.override.yml można inicjowania tych zmiennych środowiskowych, tym Docker skonfiguruje je jako zmiennych środowiskowych systemu operacyjnego, jak pokazano w następującym pliku docker compose.override.yml (połączenia ciąg i innych wierszy opakowywania w tym przykładzie, ale nie będzie zawijany w własny plik).

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    - ExternalCatalogBaseUrl=http://10.0.75.1:5101
    #- ExternalCatalogBaseUrl=http://dockerhoststaging.westus.cloudapp.azure.com:5101
  
  ports:
    - "5101:5101"
```

Pliki docker-compose.yml na poziomie rozwiązania nie są tylko bardziej elastyczne niż pliki konfiguracji na poziomie projektu lub mikrousługi, ale także bardziej bezpieczne. Należy wziąć pod uwagę obrazy Docker kompilacji na mikrousługi nie zawierają docker-compose.yml pliki tylko pliki binarne i pliki konfiguracji dla każdego mikrousługi, w tym plik Dockerfile. Jednak plik docker-compose.yml nie są wdrażane wraz z aplikacji; jest używany tylko w czasie wdrażania. W związku z tym wprowadzenie wartości zmiennych środowiskowych w tych plikach docker-compose.yml (nawet bez szyfrowania wartości) jest bezpieczniejsza niż umieszczenie tych wartości w regularnych .NET pliki konfiguracyjne, które zostały wdrożone za pomocą kodu.

Ponadto można uzyskać tę wartość w kodzie za pomocą konfiguracji\["ConnectionString"\], jak pokazano w metodzie ConfigureServices w wcześniejszego przykładu kodu.

Jednak dla środowisk produkcyjnych, możesz chcieć explorer dodatkowe sposoby na jak przechowywać hasła, takie jak parametry połączenia. Zazwyczaj które będą zarządzane przez z wybranym orchestrator, jak można zrobić za pomocą [Docker Swarm zarządzania kluczy tajnych](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementowanie przechowywania wersji w interfejsów API sieci Web ASP.NET

Po zmianie wymagań biznesowych, nowej kolekcji zasobów, które mogą zostać dodane, może spowodować zmianę relacje między zasobami i struktury danych w zasoby mogą zostać zmienione. Aktualizowanie interfejsu API sieci Web, do obsługi nowych wymagań w zakresie jest stosunkowo prosta proces, ale należy wziąć pod uwagę wpływ, mające takie zmiany w aplikacji klienckich korzystających z interfejsu API sieci Web. Mimo że developer projektowanie i implementowanie interfejs API sieci Web ma pełną kontrolę nad tego interfejsu API, deweloper nie ma ten sam stopień kontroli nad aplikacji klienckich, które mogą zostać utworzone przez organizacje innej operacyjnego zdalnie.

Przechowywanie wersji umożliwia interfejsu API sieci Web wskazać, funkcje i zasoby, które ujawnia on. Aplikacja kliencka następnie do przesyłania żądań do określonej wersji funkcji lub zasobu. Istnieją różne podejścia do implementacji przechowywania wersji:

-   Przechowywanie wersji identyfikatora URI

-   Przechowywanie wersji ciąg zapytania

-   Przechowywanie wersji nagłówka

Ciąg zapytania i przechowywanie wersji identyfikatora URI są najprostszym do zaimplementowania. Przechowywanie wersji nagłówka jest dobre rozwiązanie. Jednak wersji nagłówka nie jako jawne i prostego jako versioning identyfikatora URI. Ponieważ versioning adres URL jest najprostsza i najbardziej jawne, eShopOnContainers Przykładowa aplikacja korzysta z wersji identyfikatora URI.

Zarządzanie wersjami identyfikatora URI, tak jak eShopOnContainers przykładowej aplikacji za każdym razem zmodyfikować interfejsu API sieci Web lub zmienić schemat zasobów, możesz dodać numer wersji do identyfikatora URI dla każdego zasobu. Istniejące identyfikatory URI powinno być kontynuowane do działania jako przed, zwracanie zasoby, które są zgodne ze schematem odpowiadający żądanej wersji.

Jak pokazano w poniższym przykładzie kodu, wersja można ustawić za pomocą atrybutu trasy w interfejsie API sieci Web, co sprawia, że wersja jawne w identyfikatorze URI (v1, w tym przypadku).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Ten mechanizm versioning jest prosta i zależy od serwera routingu żądania do odpowiedniego punktu końcowego. Jednak bardziej zaawansowanych wersji i najlepszą metodę przy użyciu REST, należy użyć hipermedialnych i implementować [HATEOAS (Hypertext jako stan aparatu aplikacji)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Scott Hanselman. Przechowywanie wersji interfejsu API sieci Web RESTful Core ASP.NET łatwe**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Przechowywanie wersji interfejs API RESTful sieci web**

    [*https://docs.microsoft.com/Azure/Architecture/Best-Practices/API-Design#Versioning-a-restful-Web-API*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Fielding Royowi. Przechowywanie wersji, hipermedialnych i REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Generowanie metadanych struktury Swagger opis interfejsu API platformy ASP.NET Core sieci Web 

[Swagger](http://swagger.io/) jest framework często używane typu open source zabezpieczona przy dużych ekosystemu narzędzia ułatwiające projektu, kompilacji, dokumentów i korzystanie z API RESTful. Staje się coraz standardowego dla interfejsów API opis metadanych domeny. Powinny zawierać metadane programu Swagger z dowolnego rodzaju mikrousługi, opartych na danych mikrousług lub bardziej zaawansowane mikrousług oparte na domenie (zgodnie z objaśnieniem w następnej sekcji).

Struktury Swagger to specyfikację struktury Swagger jest metadanych opis interfejsu API w pliku JSON lub yaml programu. Specyfikacja tworzy RESTful kontrakt interfejsu API, określające wszystkich jej zasobów i operacji w obu readable człowieka i machine formacie ułatwiający projektowanie, odnajdywania i integracji.

Specyfikacja stanowi podstawę specyfikacji OpenAPI (amerykańskich) i został napisany w otwarte, przejrzyste i współpracy społeczności normalizacji sposób zdefiniowanych interfejsów RESTful.

Specyfikacja definiuje strukturę jak usługi mogą być wykrywane i jak zrozumienie możliwości. Aby uzyskać więcej informacji, w tym edytorze sieci web i przykłady specyfikacji Swagger firm, takich jak serwis Spotify, pełny zapas czasu i firmy Microsoft, zobacz witrynę programu Swagger (<http://swagger.io>).

### <a name="why-use-swagger"></a>Dlaczego warto używać struktury Swagger?

Poniżej są główne powody generować metadane programu Swagger dla interfejsów API.

**Możliwość dla innych produktów automatycznie używać i integrować swoje interfejsy API**. Dziesiątki produktów i [narzędzia komercyjnego](http://swagger.io/commercial-tools/) i wiele [bibliotek i platform](http://swagger.io/open-source-integrations/) obsługuje struktury Swagger. Firma Microsoft ma wysokiego poziomu produktów i narzędzi, które mogą automatycznie używać API podstawie struktury Swagger, takie jak następujące:

-   [AutoRest](https://github.com/Azure/AutoRest). Można automatycznie generować klasy klienta .NET wywoływania struktury Swagger. To

-   Narzędzie może być używane z poziomu interfejsu wiersza polecenia i integruje się również z programu Visual Studio dla łatwe za pośrednictwem graficznego interfejsu użytkownika.

-   [Przepływ Microsoft](https://flow.microsoft.com/en-us/). Można automatycznie [użycia i integracja z interfejsem API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) do wysokiego poziomu przepływu pracy Microsoft Flow bez umiejętności programowania wymagane.

-   [Rozwiązanie Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). Można automatycznie korzystać z interfejsu API [aplikacji mobilnych w rozwiązaniu PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) skompilowanej za pomocą [Studio rozwiązania PowerApps](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), nie umiejętności programowania wymagane.

-   [Usługa aplikacji Azure Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Można automatycznie [użycia i integrowanie interfejsu API Azure aplikację usługi aplikacji logiki](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), nie umiejętności programowania wymagane.

**Możliwość automatycznego generowania dokumentacji interfejsu API**. Podczas tworzenia dużych interfejsy API RESTful, takich jak złożonych aplikacji opartych na mikrousługi należy obsługiwać wiele punktów końcowych z modelami danych używania w ładunkach żądań i odpowiedzi. Posiadanie odpowiednich dokumentacji i o stałych explorer interfejsu API, jak pobrać z programu Swagger, jest klucza w przypadku powodzenia interfejsu API i przyjęcia przez deweloperów.

Metadane programu swagger dla jest Flow firmy Microsoft, PowerApps i usługi Azure Logic Apps Użyj zrozumienie, jak używać interfejsów API i nawiązywania z nimi.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Jak zautomatyzować interfejsu API programu Swagger Generowanie metadanych przy użyciu pakietu Swashbuckle NuGet

Generowanie metadanych struktury Swagger ręcznie (w pliku JSON lub yaml programu) może być konieczność. Jednak można automatyzować odnajdywanie interfejsów API, usług interfejsu API sieci Web ASP.NET przy użyciu [pakietu Swashbuckle NuGet](http://aka.ms/swashbuckledotnetcore) do dynamicznego generowania metadanych interfejsu API programu Swagger.

Pakiet Swashbuckle automatycznie generuje metadane programu Swagger dla projektów ASP.NET Web API. Obsługuje on projekty interfejsu API platformy ASP.NET Core sieci Web i tradycyjnego interfejsu API sieci Web ASP.NET i innych wersji, takie jak aplikacji interfejsu API platformy Azure, aplikacji mobilnej Azure, sieć szkieletowa usług Azure mikrousług opartych na programie ASP.NET. Obsługuje ona również zwykły wdrożone na kontenery, podobnie jak w aplikacji odwołanie do interfejsu API sieci Web.

Pakiet Swashbuckle łączy Explorer interfejsu API i struktury Swagger lub [interfejsu użytkownika programu swagger](https://github.com/swagger-api/swagger-ui) zapewnienie sformatowanego odnajdywania i dokumentacji wystąpić przez użytkowników interfejsu API. Oprócz jego generator aparat metadanych struktury Swagger Swashbuckle zawiera osadzony wersji struktury swagger interfejsu użytkownika, który go automatycznie posłuży się po zainstalowaniu pakietu Swashbuckle.

Oznacza to, że można rozszerzyć interfejsu API z odnajdywaniem nieuprzywilejowany interfejsu użytkownika, aby pomóc deweloperom korzystanie z interfejsu API. Wymaga niewielką ilość kodu i konserwacji, ponieważ jest ona generowana automatycznie, co pozwala skupić się na tworzeniu interfejsu API. Wynik dla interfejsu API Explorer wygląda podobnie jak rysunek 8-8.

![](./media/image9.png)

**Rysunek 8-8**. Pakiet Swashbuckle interfejsu API Eksploratora oparte na metadanych struktury Swagger — eShopOnContainers katalogu mikrousługi

W Eksploratorze interfejsu API nie jest ważne jest, w tym miejscu. Po utworzeniu interfejsu API sieci Web, który można opisania siebie w metadanych struktury Swagger interfejsu API można bezproblemowo z narzędzi na podstawie struktury Swagger, w tym generatory kodu klasy serwera proxy klienta, które mogą współpracować z wielu platform. Na przykład, jak wspomniano [AutoRest](https://github.com/Azure/AutoRest) automatycznie wygeneruje klasy klienta .NET. Ale dodatkowych narzędzi, takich jak [swagger codegen](https://github.com/swagger-api/swagger-codegen) są również dostępne, która zezwala na generowanie kodu klienta interfejsu API biblioteki klas zastępczych serwera i dokumentacji automatycznie.

Obecnie Swashbuckle składa się z dwóch pakietów NuGet: Swashbuckle.SwaggerGen i Swashbuckle.SwaggerUi. Pierwsza zapewnia funkcje do generowania co najmniej jednego dokumentu Swagger bezpośrednio z implementacji interfejsu API i ujawniać je jako punkty końcowe JSON. Drugie zawiera osadzony wersji narzędzia interfejsu użytkownika programu swagger, który może zostać obsłużone przez aplikację i obsługiwane przez generowane dokumenty programu Swagger do opisu interfejsu API. Jednak najnowsze wersje pakietu Swashbuckle zawijany, należy je Swashbuckle.AspNetCore metapackage.

Należy pamiętać, że dla projektów interfejsu API sieci Web programu .NET Core, musisz użyć [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) w wersji 1.0.0 lub nowszej.

Po zainstalowaniu tych pakietów NuGet w projekcie interfejsu API sieci Web, należy skonfigurować struktury Swagger w klasie uruchamiania zgodnie z poniższym kodem:

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...
        services.AddSwaggerGen();
        services.ConfigureSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SingleApiVersion(new Swashbuckle.Swagger.Model.Info()
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API",
                TermsOfService = "eShopOnContainers terms of service"
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
            .UseSwaggerUi();
    }
}
```

Po zakończeniu możesz uruchomić aplikację i Przeglądaj następujących interfejsu użytkownika i JSON programu Swagger punktów końcowych przy użyciu adresów URL, takich jak te:

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

Widać wcześniej wygenerowany interfejsu użytkownika utworzone przez pakiet Swashbuckle dla danego adresu URL, takie jak http://&lt;adres url katalogu głównego &gt; /swagger/interfejsu użytkownika. W rysunek 8-9 widoczny jest także jak można przetestować dowolnej metody interfejsu API.

![](./media/image10.png)

**Rysunek 8-9**. Interfejs użytkownika Swashbuckle testowania metody interfejsu API/wszystkich elementów katalogu

Rysunek 8-10 przedstawia metadanych JSON programu Swagger generowane na podstawie mikrousługi eShopOnContainers (czyli narzędzia Użyj poniżej) na żądanie &lt;adres url katalogu głównego&gt;/swagger/v1/swagger.json przy użyciu [Postman](https://www.getpostman.com/).

![](./media/image11.png)

**Rysunek 8-10**. Metadane JSON programu swagger

Jest to proste. A ponieważ jest ona generowana automatycznie, metadane programu Swagger wzrośnie po dodaniu więcej funkcji do interfejsu API.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Strony sieci Web ASP.NET interfejsu API pomocy przy użyciu programu Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Poprzednie] (mikrousługi aplikacji design.md) [dalej] (kilku-container — aplikacje — docker-compose.md)
