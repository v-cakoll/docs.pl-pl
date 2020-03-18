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
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Tworzenie prostej mikrousługi CRUD na podstawie danych

W tej sekcji opisano sposób tworzenia prostej mikrousługi, która wykonuje operacje tworzenia, odczytu, aktualizacji i usuwania (CRUD) w źródle danych.

## <a name="designing-a-simple-crud-microservice"></a>Projektowanie prostej mikrousługi CRUD

Z punktu widzenia projektowania tego typu konteneryzowanych mikrousług jest bardzo proste. Być może problem do rozwiązania jest prosty, a może implementacja jest tylko dowodem koncepcji.

![Diagram przedstawiający prosty wzorzec projektu wewnętrznego crud mikrousługi.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

**Rysunek 6-4**. Projekt wewnętrzny dla prostych mikrousług CRUD

Przykładem tego rodzaju usługi prostego dysku danych jest mikrousługi katalogu z eShopOnContainers przykładowej aplikacji. Ten typ usługi implementuje wszystkie swoje funkcje w jednym projekcie interfejsu API sieci Web ASP.NET, który zawiera klasy dla swojego modelu danych, jego logiki biznesowej i jego kodu dostępu do danych. Przechowuje również powiązane dane w bazie danych działającej w programie SQL Server (jako inny kontener do celów deweloperskich/testowych), ale może być również zwykłym hostem programu SQL Server, jak pokazano na rysunku 6-5.

![Diagram przedstawiający kontener mikrousług opartych na danych/CRUD.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

**Rysunek 6-5**. Prosta konstrukcja mikrousług opartych na danych/CRUD

Poprzedni diagram przedstawia mikrousługę wykazu logicznego, która zawiera jego bazy danych wykazu, który może być lub nie w tym samym hoście platformy Docker. Posiadanie bazy danych w tym samym hoście platformy Docker może być dobre dla rozwoju, ale nie dla produkcji. Podczas opracowywania tego rodzaju usługi, należy tylko [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) i interfejsu API dostępu do danych lub ORM jak Entity [Framework Core](https://docs.microsoft.com/ef/core/index). Można również wygenerować metadane [Swagger](https://swagger.io/) automatycznie za pośrednictwem [Swashbuckle,](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) aby podać opis tego, co oferuje usługa, jak wyjaśniono w następnej sekcji.

Należy zauważyć, że uruchomienie serwera bazy danych, takiego jak SQL Server w kontenerze platformy Docker, jest idealne dla środowisk programistycznych, ponieważ wszystkie zależności mogą być uruchamiane bez konieczności aprowizacji bazy danych w chmurze lub lokalnie. Jest to bardzo wygodne podczas uruchamiania testów integracji. Jednak w środowiskach produkcyjnych uruchomienie serwera bazy danych w kontenerze nie jest zalecane, ponieważ zwykle nie uotrzymasz wysokiej dostępności przy takim podejściu. W środowisku produkcyjnym na platformie Azure zaleca się używanie usługi Azure SQL DB lub dowolnej innej technologii bazy danych, która może zapewnić wysoką dostępność i wysoką skalowalność. Na przykład dla podejścia NoSQL można wybrać CosmosDB.

Na koniec edytując pliki metadanych Dockerfile i docker-compose.yml, można skonfigurować sposób tworzenia obrazu tego kontenera — jaki obraz podstawowy będzie używany, a także ustawienia projektu, takie jak nazwy wewnętrzne i zewnętrzne oraz porty TCP.

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementowanie prostej mikrousługi CRUD z ASP.NET Core

Aby zaimplementować prostą mikrousługę CRUD przy użyciu .NET Core i Visual Studio, należy rozpocząć od utworzenia prostego ASP.NET projektu interfejsu API podstawowego interfejsu API sieci Web (uruchomionego na platformie .NET Core, aby można go było uruchomić na hoście platformy Docker systemu Linux), jak pokazano na rysunku 6-6.

![Zrzut ekranu przedstawiający program Visual Studios przedstawiający konfigurację projektu.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

**Rysunek 6-6**. Tworzenie ASP.NET projektu podstawowego interfejsu API sieci Web w programie Visual Studio 2019

Aby utworzyć ASP.NET core Web API Project, najpierw wybierz ASP.NET podstawową aplikację sieci Web, a następnie wybierz typ interfejsu API. Po utworzeniu projektu można zaimplementować kontrolery MVC, tak jak w każdym innym projekcie interfejsu API sieci Web, przy użyciu interfejsu API struktury jednostki lub innego interfejsu API. W nowym projekcie interfejsu API sieci Web widać, że jedyną zależnością, którą masz w tej mikrousługi, jest sama ASP.NET Core. Wewnętrznie w ramach *zależności Microsoft.AspNetCore.All* odwołuje się do struktury jednostek i wielu innych pakietów NuGet .NET Core, jak pokazano na rysunku 6-7.

![Zrzut ekranu przedstawiający zależności NuGet interfejsu Catalog.Api.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

**Rysunek 6-7**. Zależności w prostej mikrousłudze interfejsu API sieci Web CRUD

Projekt interfejsu API zawiera odwołania do pakietu NuGet Microsoft.AspNetCore.App, który zawiera odwołania do wszystkich podstawowych pakietów. Może zawierać również inne pakiety.

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Wdrażanie usług interfejsu API sieci Web CRUD z rdzeniem frameworku jednostek

Entity Framework (EF) Core jest lekką, rozszerzalne i międzyplatformowej wersji popularnej technologii dostępu do danych entity framework. EF Core jest obiekt-relacyjne mapper (ORM), który umożliwia deweloperom .NET do pracy z bazą danych przy użyciu obiektów .NET.

Mikrousługi wykazu używa EF i dostawcy programu SQL Server, ponieważ jego baza danych jest uruchomiona w kontenerze z sql Server dla linux docker obrazu. Jednak baza danych może zostać wdrożona w dowolnym programie SQL Server, takim jak lokalny system Windows lub usługa Azure SQL DB. Jedyną rzeczą, którą należy zmienić, jest ciąg połączenia w mikrousłudze interfejsu ASP.NET interfejsu API sieci Web.

#### <a name="the-data-model"></a>Model danych

Z EF Core, dostęp do danych odbywa się przy użyciu modelu. Model składa się z klas jednostek (model domeny) i kontekstu pochodnego (DbContext), który reprezentuje sesję z bazą danych, umożliwiając wykonywanie zapytań i zapisywanie danych. Można wygenerować model z istniejącej bazy danych, ręcznie kodmodelu, aby dopasować bazę danych lub użyć migracji EF do utworzenia bazy danych z modelu, przy użyciu podejścia opartego na kodzie (co ułatwia rozwijanie bazy danych, jak model zmienia się wraz z uchwadnianiem). Dla mikrousługi katalogu używamy ostatniego podejścia. Przykład klasy jednostki CatalogItem można wyświetlić w poniższym przykładzie kodu, który jest prostą klasą jednostki Zwykły stary obiekt CLR[(POCO).](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)

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

Potrzebny jest również DbContext, który reprezentuje sesję z bazą danych. W przypadku mikrousługi katalogu klasa CatalogContext pochodzi z klasy podstawowej DbContext, jak pokazano w poniższym przykładzie:

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

Możesz mieć `DbContext` dodatkowe implementacje. Na przykład w przykładowej mikrousługi Catalog.API istnieje `DbContext` `CatalogContextSeed` druga nazwa, gdzie automatycznie wypełnia przykładowe dane przy pierwszej próbie uzyskania dostępu do bazy danych. Ta metoda jest przydatna dla danych demonstracyjnych i scenariuszy testowania automatycznego, jak również.

W `DbContext`ramach programu `OnModelCreating` , można użyć metody, aby dostosować mapowania jednostek obiektu/bazy danych i innych [punktów rozszerzalności EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Wykonywanie zapytań dotyczących danych z kontrolerów interfejsu API sieci Web

Wystąpienia klas jednostek są zazwyczaj pobierane z bazy danych przy użyciu language Integrated Query (LINQ), jak pokazano w poniższym przykładzie:

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

##### <a name="saving-data"></a>Zapisywanie danych

Dane są tworzone, usuwane i modyfikowane w bazie danych przy użyciu wystąpień klas jednostek. Można dodać kod, taki jak w poniższym zakodowanym przykładzie (w tym przypadku makiety danych) do kontrolerów interfejsu API sieci Web.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Wstrzykiwanie zależności w kontrolerach interfejsu API ASP.NET Core i Web

W ASP.NET Core można użyć iniekcji zależności (DI) po wyjęciu z pudełka. Nie trzeba konfigurować kontenera inwersji formantu (IoC) innej firmy, chociaż w razie potrzeby można podłączyć preferowany kontener IoC do infrastruktury ASP.NET Core. W takim przypadku oznacza to, że można bezpośrednio wstrzyknąć wymagane EF DBContext lub dodatkowe repozytoria za pośrednictwem konstruktora kontrolera.

W powyższym przykładzie `CatalogController` klasy wstrzykujemy `CatalogContext` obiekt typu oraz `CatalogController()` inne obiekty za pośrednictwem konstruktora.

Ważną konfiguracją do skonfigurowania w projekcie interfejsu API sieci Web jest rejestracja klasy DbContext do kontenera IoC usługi. Zazwyczaj należy to zrobić `Startup` w klasie, `services.AddDbContext<DbContext>()` wywołując `ConfigureServices()` metodę wewnątrz metody, jak pokazano w poniższym **uproszczonym** przykładzie:

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

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wykonywanie zapytań dotyczących danych** \
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- **Zapisywanie danych** \
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Parametry połączenia bazy danych i zmienne środowiskowe używane przez kontenery platformy Docker

Można użyć ASP.NET ustawień core i dodać ConnectionString właściwości do pliku settings.json, jak pokazano w poniższym przykładzie:

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

Plik settings.json może mieć wartości domyślne dla ConnectionString właściwości lub dla innych właściwości. Jednak te właściwości zostaną zastąpione przez wartości zmiennych środowiskowych, które określisz w pliku docker-compose.override.yml, podczas korzystania z platformy Docker.

Z plików docker-compose.yml lub docker-compose.override.yml można zainicjować te zmienne środowiskowe, aby platforma Docker skonfigurować je jako zmienne środowiskowe systemu operacyjnego, jak pokazano w następującym pliku docker-compose.override.yml (połączenie ciąg i inne linie zawijają się w tym przykładzie, ale nie będą zawijane we własnym pliku).

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

Pliki docker-compose.yml na poziomie rozwiązania są nie tylko bardziej elastyczne niż pliki konfiguracyjne na poziomie projektu lub mikrousługi, ale także bardziej bezpieczne, jeśli zastąpisz zmienne środowiskowe zadeklarowane w plikach docker-compose z wartościami ustawionymi z narzędzia wdrażania, takie jak zadania wdrażania platformy Azure DevOps Services Docker.

Na koniec można uzyskać tę wartość z\[kodu przy\]użyciu konfiguracji "ConnectionString", jak pokazano w ConfigureServices metody w przykładzie wcześniejszego kodu.

Jednak w środowiskach produkcyjnych można zbadać dodatkowe sposoby przechowywania kluczy tajnych, takich jak parametry połączenia. Doskonałym sposobem zarządzania kluczami tajnymi aplikacji jest użycie [usługi Azure Key Vault](https://azure.microsoft.com/services/key-vault/).

Usługa Azure Key Vault pomaga przechowywać i chronić klucze kryptograficzne i klucze tajne używane przez aplikacje i usługi w chmurze. Sekret jest wszystko, co chcesz zachować ścisłą kontrolę, jak klucze API, parametry połączenia, hasła, itp i ścisła kontrola obejmuje rejestrowanie użytkowania, ustawienie wygaśnięcia, zarządzanie dostępem, *między innymi*.

Usługa Azure Key Vault umożliwia bardzo szczegółowy poziom kontroli użycia kluczy tajnych aplikacji bez konieczności informowania kogokolwiek o nich. Klucze tajne można nawet obracać w celu zwiększenia bezpieczeństwa bez zakłócania rozwoju lub operacji.

Aplikacje muszą być rejestrowane w usłudze Active Directory organizacji, aby mogły korzystać z magazynu kluczy.

Aby uzyskać więcej informacji, można zapoznać się z *dokumentacją pojęć magazynu kluczy.*

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementowanie wersji w interfejsach API sieci Web ASP.NET

W miarę zmiany wymagań biznesowych można dodać nowe kolekcje zasobów, relacje między zasobami mogą ulec zmianie, a struktura danych w zasobach może zostać zmieniona. Aktualizowanie interfejsu API sieci Web do obsługi nowych wymagań jest stosunkowo prosty proces, ale należy wziąć pod uwagę skutki, jakie takie zmiany będą miały na aplikacje klienckie korzystających z interfejsu API sieci Web. Mimo że deweloper projektowania i wdrażania interfejsu API sieci Web ma pełną kontrolę nad tym interfejsem API, deweloper nie ma takiego samego stopnia kontroli nad aplikacjami klienckimi, które mogą być tworzone przez organizacje innych firm działających zdalnie.

Przechowywanie wersji umożliwia interfejs owi api sieci Web, aby wskazać funkcje i zasoby, które udostępnia. Aplikacja kliencka może następnie przesyłać żądania do określonej wersji funkcji lub zasobu. Istnieje kilka podejść do wdrożenia wersji:

- Obsługa wersji za pomocą identyfikatora URI

- Obsługa wersji za pomocą ciągu zapytania

- Obsługa wersji za pomocą nagłówka

Ciąg zapytania i przechowywanie wersji identyfikatorów URI są najprostsze do zaimplementowania. Przechowywanie wersji nagłówka jest dobrym podejściem. Jednak przechowywanie wersji nagłówka nie jest tak jawne i proste, jak przechowywanie wersji identyfikatora URI. Ponieważ przechowywanie adresów URL jest najprostsze i najbardziej jawne, przykładowa aplikacja eShopOnContainers używa przechowywania wersji identyfikatorów URI.

W przypadku przechowywania wersji URI, tak jak w przykładowej aplikacji eShopOnContainers, za każdym razem, gdy modyfikujesz interfejs API sieci Web lub zmieniasz schemat zasobów, należy dodać numer wersji do identyfikatora URI dla każdego zasobu. Istniejące identyfikatory URI powinny nadal działać tak, jak poprzednio, zwracając zasoby, które są zgodne ze schematem, który pasuje do żądanej wersji.

Jak pokazano w poniższym przykładzie kodu, wersję można ustawić przy użyciu route atrybutu w kontrolerze interfejsu API sieci Web, co sprawia, że wersja jawne w identyfikatorze URI (v1 w tym przypadku).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Ten mechanizm przechowywanie wersji jest prosty i zależy od serwera routingu żądania do odpowiedniego punktu końcowego. Jednak w przypadku bardziej zaawansowanego tworzenia wersji i najlepszej metody przy użyciu rest, należy użyć hypermedia i zaimplementować [HATEOAS (Hypertext jako aparat stanu aplikacji).](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Scott Hanselman. ASP.NET Core RESTful Web API przechowywanie wersji łatwe** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Przechowywanie wersji internetowego interfejsu API RESTful** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy Fielding. Przechowywanie wersji, hypermedia i REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Generowanie metadanych opisu Swaggera z ASP.NET core Web API

[Swagger](https://swagger.io/) jest często używanym open source framework wspierane przez duży ekosystem narzędzi, który pomaga projektowania, tworzenia, dokumentowania i zużycia restful interfejsów API. Staje się standardem dla domeny metadanych opisu interfejsów API. Należy dołączyć metadane opisu Swaggera z dowolnego rodzaju mikrousług, mikrousług opartych na danych lub bardziej zaawansowanych mikrousług opartych na domenie (jak wyjaśniono w poniższej sekcji).

Sercem Swaggera jest specyfikacja Swaggera, która jest metadanymi opisu Interfejsu API w pliku JSON lub YAML. Specyfikacja tworzy restful umowy dla interfejsu API, szczegółowo wszystkie jego zasoby i operacje w formacie człowieka i maszyny czytelne dla łatwego rozwoju, odnajdywania i integracji.

Specyfikacja jest podstawą specyfikacji OpenAPI (OAS) i jest rozwijana w otwartej, przejrzystej i współpracy społeczności w celu standaryzacji sposobu definiowania interfejsów RESTful.

Specyfikacja definiuje strukturę sposobu odnalezić usługę i jak jej możliwości rozumiane. Aby uzyskać więcej informacji, w tym edytor a także przykłady specyfikacji Swagger a firmy takie jak Spotify, Uber, Slack i Microsoft, zobacz witrynę Swagger (<https://swagger.io>).

### <a name="why-use-swagger"></a>Dlaczego warto skorzystać z Swagger?

Główne przyczyny generowania metadanych Swagger dla interfejsów API są następujące.

**Możliwość automatycznego konsumowania i integrowania interfejsów API przez inne produkty.** Dziesiątki produktów i [narzędzi komercyjnych](https://swagger.io/commercial-tools/) oraz wiele bibliotek [i struktur](https://swagger.io/open-source-integrations/) obsługuje Firmę Swagger. Firma Microsoft ma produkty wysokiego poziomu i narzędzia, które mogą automatycznie korzystać z interfejsów API opartych na swagger, takich jak następujące:

- [AutoRest](https://github.com/Azure/AutoRest). Klasy klienta .NET można automatycznie generować dla wywoływania swagger. To narzędzie może być używane z interfejsu użytkownika, a także integruje się z visual studio do łatwego użycia za pośrednictwem gui.

- [Usługa Microsoft Flow](https://flow.microsoft.com/). Możesz automatycznie [używać interfejsu API i integrować go](https://flow.microsoft.com/blog/integrating-custom-api/) z obiegiem pracy usługi Microsoft Flow na wysokim poziomie, bez konieczności programowania.

- [Usługa Microsoft PowerApps](https://powerapps.microsoft.com/). Możesz automatycznie korzystać z interfejsu API z [aplikacji mobilnych usługi PowerApps utworzonych](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) za pomocą [usługi PowerApps Studio,](https://powerapps.microsoft.com/build-powerapps/)bez konieczności programowania.

- [Aplikacje logiki usługi Azure App Service](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Możesz automatycznie [używać interfejsu API i integrować go z aplikacją logiki usługi Azure App Service,](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)bez konieczności programowania.

**Możliwość automatycznego generowania dokumentacji interfejsu API**. Podczas tworzenia dużych interfejsów API RESTful, takich jak złożone aplikacje oparte na mikrousługach, należy obsługiwać wiele punktów końcowych z różnych modeli danych używanych w ładunku żądania i odpowiedzi. Posiadanie odpowiedniej dokumentacji i posiadanie solidnego eksploratora interfejsu API, jak masz z Swagger, jest kluczem do sukcesu interfejsu API i przyjęcia przez deweloperów.

Metadane swaggera są używane przez program Microsoft Flow, usługi PowerApps i usługi Azure Logic Apps, aby zrozumieć, jak używać interfejsów API i łączyć się z nimi.

Istnieje kilka opcji automatyzacji generowania metadanych Swagger dla ASP.NET podstawowych aplikacji Interfejsu API REST, w postaci funkcjonalnych stron pomocy interfejsu API, opartych na *swagger-ui*.

Prawdopodobnie najlepiej wiedzieć jest [Swashbuckle,](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) który jest obecnie używany w [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) i omówimy w niektórych szczegółach w tym przewodniku, ale\# istnieje również możliwość korzystania\# [z NSwag](https://github.com/RSuter/NSwag), który może generować maszynopis i C API klientów, a także kontrolerów C, ze specyfikacji Swagger lub OpenAPI, a nawet poprzez skanowanie .dll, który zawiera kontrolery, za pomocą [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Jak zautomatyzować generowanie metadanych API Swagger za pomocą pakietu Swashbuckle NuGet

Ręczne generowanie metadanych Swaggera (w pliku JSON lub YAML) może być żmudną pracą. Można jednak zautomatyzować odnajdowanie interfejsu API ASP.NET usług interfejsu API sieci Web przy użyciu [pakietu Swashbuckle NuGet](https://aka.ms/swashbuckledotnetcore) do dynamicznego generowania metadanych interfejsu API Swaggera.

Swashbuckle automatycznie generuje metadane Swagger dla projektów interfejsu ASP.NET Web API. Obsługuje ASP.NET podstawowych projektów interfejsu API sieci Web i tradycyjnego interfejsu API sieci Web ASP.NET i dowolnego innego smaku, takiego jak aplikacja Azure API, aplikacja azure mobile app, mikrousługi sieci Web sieci Web platformy Azure na podstawie ASP.NET. Obsługuje również zwykły interfejs API sieci Web wdrożony na kontenerach, tak jak w przypadku aplikacji referencyjnej.

Swashbuckle łączy api Explorer i Swagger lub [swagger-ui,](https://github.com/swagger-api/swagger-ui) aby zapewnić bogate doświadczenie wykrywania i dokumentacji dla konsumentów interfejsu API. Oprócz silnika generatora metadanych Swaggera, Swashbuckle zawiera również wbudowaną wersję swagger-ui, którą automatycznie poda po zainstalowaniu Swashbuckle.

Oznacza to, że można uzupełnić interfejsu API z ładnym interfejsu użytkownika odnajdywania, aby ułatwić deweloperom korzystanie z interfejsu API. Wymaga to bardzo małej ilości kodu i konserwacji, ponieważ jest generowany automatycznie, co pozwala skupić się na tworzeniu interfejsu API. Wynik dla Eksploratora interfejsu API wygląda jak rysunek 6-8.

![Zrzut ekranu przedstawiający eksploratora interfejsu API Swaggera wyświetlającego interfejs API eShopOContainers.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

**Rysunek 6-8**. Swashbuckle API Explorer na podstawie metadanych Swagger — mikrousługi katalogu eShopOnContainers

Swashbuckle generowane Swagger UI Dokumentacja interfejsu API zawiera wszystkie opublikowane akcje. Eksplorator interfejsu API nie jest tutaj najważniejszą rzeczą. Gdy masz interfejs API sieci Web, który może opisywać się w metadanych Swagger, interfejs API może być używany bezproblemowo z narzędzi opartych na swagger, w tym generatory kodu klasy proxy klienta, które mogą być przeznaczone dla wielu platform. Na przykład, jak wspomniano, [AutoRest](https://github.com/Azure/AutoRest) automatycznie generuje klasy klientów .NET. Ale dodatkowe narzędzia, takie jak [swagger-codegen](https://github.com/swagger-api/swagger-codegen) są również dostępne, które umożliwiają generowanie kodu bibliotek klienta interfejsu API, wycinki serwera i dokumentacji automatycznie.

Obecnie Swashbuckle składa się z pięciu wewnętrznych pakietów NuGet w ramach wysokiego poziomu meta-pakiet [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) dla ASP.NET aplikacji Core.

Po zainstalowaniu tych pakietów NuGet w projekcie interfejsu API sieci Web należy skonfigurować swagger w klasie Start, jak w **następującym uproszczonym** kodzie:

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

Gdy to zrobisz, można uruchomić aplikację i przeglądać następujące punkty końcowe Swagger JSON i interfejsu użytkownika przy użyciu adresów URL, takich jak te:

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

Wcześniej widziałeś wygenerowany ui utworzony przez Swashbuckle `http://<your-root-url>/swagger`dla adresu URL, takiego jak . Na rysunku 6-9 można również zobaczyć, jak można przetestować dowolną metodę interfejsu API.

![Zrzut ekranu przedstawiający interfejsu firmy Swagger z dostępnymi narzędziami do testowania.](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

**Rysunek 6-9**. Swashbuckle UI testowania katalogu/elementów Metody Interfejsu API

Swagger szczegóły interfejsu api interfejsu ze stawiana pokazuje przykład odpowiedzi i może służyć do wykonywania rzeczywistego interfejsu API, który jest doskonały do odnajdywania deweloperów. Rysunek 6-10 pokazuje swagger JSON metadanych generowanych z mikrousługi eShopOnContainers (co jest, `http://<your-root-url>/swagger/v1/swagger.json` co narzędzia używane pod spodem) podczas żądania przy użyciu [Postman](https://www.getpostman.com/).

![Zrzut ekranu przedstawiający przykładowy ui listonosza z metadanymi Swagger JSON.](./media/data-driven-crud-microservice/swagger-json-metadata.png)

**Rysunek 6-10**. Swagger JSON metadane

To takie proste. A ponieważ jest generowany automatycznie, metadane Swagger wzrośnie po dodaniu więcej funkcji do interfejsu API.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **ASP.NET stron pomocy interfejsu API sieci Web przy użyciu programu Swagger** \
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- **Zacznij korzystać z swashbuckle i ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- **Wprowadzenie do NSwag i ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> [Poprzedni](microservice-application-design.md)
> [następny](multi-container-applications-docker-compose.md)
