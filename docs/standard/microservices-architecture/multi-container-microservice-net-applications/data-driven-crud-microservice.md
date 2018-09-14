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
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Tworzenie prostego mikrousługi CRUD na podstawie danych

Tej sekcji przedstawiono sposób w celu utworzenia prostej mikrousługi, który wykonuje tworzenia, odczytu, aktualizacji i operacje usuwania (CRUD) w źródle danych.

## <a name="designing-a-simple-crud-microservice"></a>Projektowanie proste mikrousługi CRUD

Z punktu widzenia projektowania tego rodzaju konteneryzowanych mikrousług jest bardzo proste. Być może rozwiązać ten problem jest proste lub prawdopodobnie implementacja jest tylko weryfikacji koncepcji.

![](./media/image4.png)

**Rysunek 8-4**. Wewnętrzny projektowanie pod kątem prostego mikrousługi CRUD

Przykładem tego rodzaju usługi simple dysk danych jest mikrousług katalogu w ramach aplikacji eShopOnContainers przykładowej aplikacji. Tego rodzaju usługi implementuje wszystkie jej funkcje w jednym projekcie internetowego interfejsu API platformy ASP.NET Core, która zawiera klasy służące do jej modelu danych, jej logiki biznesowej i jego kod dostępu do danych. Jest również przechowuje swoje powiązane dane w bazie danych, uruchomione w programie SQL Server (zgodnie z innego kontenera do celów deweloperskich i testowych), ale może być również regularne dowolnego hosta programu SQL Server, jak pokazano na rysunku 8-5.

![](./media/image5.png)

**Rysunek 8-5**. Proste data-driven/CRUD mikrousługi projektowania

Podczas tworzenia tego rodzaju usługi wystarczy [platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/) i ORM lub interfejs API dostępu do danych, takich jak [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Można również wygenerować [Swagger](https://swagger.io/) automatycznie za pomocą metadanych [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) można podać opis co oferuje usługi, jak wyjaśniono w następnej sekcji.

Należy pamiętać, że używany jest serwer bazy danych, takich jak SQL Server w kontenerze platformy Docker to idealne narzędzie do środowiska programowania, ponieważ wszystkie zależności może zawierać maksymalnie i uruchamiania bez konieczności aprowizowania bazy danych w chmurze lub lokalnie. Może to być bardzo wygodne, gdy integracji Uruchamianie testów. Jednak w środowiskach produkcyjnych, uruchamianie serwera bazy danych w kontenerze nie jest zalecane, ponieważ zwykle nie uzyskasz wysokiej dostępności za pomocą tego podejścia. W środowisku produkcyjnym na platformie Azure zaleca się korzystanie z bazy danych SQL Azure lub innych technologii baz danych, zapewniające wysoką dostępność i wysoką skalowalność. Na przykład aby podejściu NoSQL, możesz wybrać bazy danych DocumentDB.

Na koniec, edytując plik Dockerfile i docker-compose.yml plików metadanych, możesz skonfigurować sposób tworzenia obrazu tego kontenera — podstawowego obrazu będzie używać oraz projektowania ustawienia, takie jak nazwy wewnętrzne i zewnętrzne i portów TCP. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementowanie prostego mikrousługi CRUD za pomocą programu ASP.NET Core

Aby zaimplementować prosty mikrousługi CRUD przy użyciu platformy .NET Core i Visual Studio, możesz rozpocząć od utworzenia prostego projektu internetowego interfejsu API platformy ASP.NET Core (uruchomionej na platformie .NET Core, dzięki czemu może działać na hosta platformy Docker w systemie Linux), jak pokazano na rysunku 8-6.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Rysunek 8 – 6**. Tworzenie projektu internetowego interfejsu API platformy ASP.NET Core w programie Visual Studio

Po utworzeniu projektu, można zaimplementować kontrolerach MVC, tak jak w innych projektów interfejsu API sieci Web, przy użyciu interfejsu API programu Entity Framework lub innym interfejsie API. W nowym projekcie interfejsu API sieci Web widać, zależności tylko że w tym mikrousług jest programu ASP.NET Core, sam. Wewnętrznie, w ramach `Microsoft.AspNetCore.All` zależności, odwołuje się ona do programu Entity Framework i wiele innych pakietów .NET Core Nuget, jak pokazano w rysunek 8 – 7.

![](./media/image8.PNG)

**Rysunek 8-7**. Zależności w prostych mikrousługi CRUD internetowego interfejsu API

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implementowanie usług interfejsu API sieci Web CRUD przy użyciu platformy Entity Framework Core

Entity Framework (EF) Core to lekkie, rozszerzalne, i technologii dostępu do popularnych danych Entity Framework w wersji dla wielu platform. EF Core to maper obiektowo relacyjny (ORM), który umożliwia deweloperom platformy .NET do pracy z bazą danych, używając obiektów platformy .NET.

Mikrousługi katalogu korzysta EF i dostawcy programu SQL Server, ponieważ jego bazy danych jest uruchomiona w kontenerze za pomocą programu SQL Server dla obrazu platformy Docker w systemie Linux. Jednak bazy danych można wdrożyć do dowolnego programu SQL Server, takich jak Windows w środowisku lokalnym lub bazy danych SQL Azure. Jedyną czynnością, którą trzeba zmienić to parametry połączenia w mikrousługach interfejsu API sieci Web platformy ASP.NET.


#### <a name="the-data-model"></a>Model danych

Z programem EF Core dostęp do danych odbywa się przy użyciu modelu. Model składa się z klas jednostek i pochodnej kontekstu, który reprezentuje sesję z bazą danych, dzięki czemu zapytania i zapisywać dane. Możesz wygenerować model z istniejącej bazy danych, ręcznie code model, aby dopasować bazy danych lub użyć migracje EF utworzyć bazę danych z modelu (i rozwój go jak model zmienia się wraz z upływem czasu). Dla mikrousług katalogu używamy najnowsze podejście. Widać przykład klasy CatalogItem jednostki w poniższym przykładzie kodu jest proste zwykłe stare obiektu CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) Klasa jednostki.

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

Należy również DbContext, który reprezentuje sesję z bazą danych. Dla mikrousług wykazu klasa CatalogContext pochodzi z klasy bazowej typu DbContext, jak pokazano w poniższym przykładzie:

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

Masz dodatkowe `DbContext` implementacji. Na przykład w mikrousługach Catalog.API próbki, istnieje sekundy `DbContext` o nazwie `CatalogContextSeed` gdzie automatycznie wypełnia przykładowe dane po raz pierwszy próbuje dostęp do bazy danych. Ta metoda jest przydatna, dane demonstracyjne i automatyczne scenariuszy testowych, jak również. W ramach `DbContext`, możesz użyć `OnModelCreating` metodę w celu dostosowania mapowania jednostek w bazie danych i obiektów przy użyciu i innych [punkty rozszerzeń EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Wykonywanie zapytania o dane z kontrolerów interfejsu API sieci Web

Wystąpienia klas jednostek zwykle są pobierane z bazy danych przy użyciu Language Integrated Query (LINQ), jak pokazano w poniższym przykładzie:

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

##### <a name="saving-data"></a>Zapisywanie danych

Dane są tworzone, usunięte i zmodyfikowane w bazie danych za pomocą wystąpień klas jednostek. Można dodać kod, takich jak ustaloną następująco (danych testowych, w tym przypadku) z kontrolerami interfejsu API sieci Web.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Wstrzykiwanie zależności w kontrolerów platformy ASP.NET Core i interfejsu API sieci Web

W programie ASP.NET Core można użyć wstrzykiwanie zależności (DI) poza pole. Nie należy skonfigurować kontener Inwersja kontroli (IoC) innych firm, mimo że preferowanego kontenera IoC można podłączyć do infrastruktury platformy ASP.NET Core, jeśli chcesz. W takim przypadku oznacza to, że należy bezpośrednio wstrzyknąć wymagane DBContext EF lub dodatkowe przechowalnie za pośrednictwem konstruktora kontrolera. W przykładzie powyżej `CatalogController` klasy, firma Microsoft jest wstawianie obiektu `CatalogContext` wpisz oraz innych obiektów za pomocą `CatalogController()` konstruktora.

Ważne konfiguracji, aby skonfigurować w projekcie interfejsu API sieci Web jest rejestrowanie klasy DbContext do kontenera IoC tej usługi. Zwykle są zatem w `Startup` klasy przez wywołanie metody `services.AddDbContext<DbContext>()` metody w ramach `ConfigureServices()` metodzie, jak pokazano w poniższym przykładzie:

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

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wykonywanie zapytania o dane**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **Zapisywanie danych**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Zmienne ciągów i środowisko połączenia bazy danych używanych przez kontenery platformy Docker

Można użyć ustawień platformy ASP.NET Core i Dodaj właściwość ConnectionString do pliku settings.json, jak pokazano w poniższym przykładzie:

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

Plik settings.json może mieć wartości domyślnych dla właściwości ConnectionString lub dla wszystkich innych właściwości. Jednak te właściwości zostaną zastąpione przez wartości zmiennych środowiskowych, które są określone w pliku docker-compose.override.yml, korzystając z platformy Docker.

Na podstawie własnych plików docker-compose.yml i docker-compose.override.yml można zainicjować tych zmiennych środowiskowych, że platforma Docker skonfiguruje je jako zmienne środowiskowe systemu operacyjnego, jak pokazano w następującym pliku docker-compose.override.yml (połączenia ciąg i innych wierszy opakowywać w tym przykładzie, ale nie będzie zawijany w pliku kodu).

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

Pliki docker-compose.yml na poziomie rozwiązania nie są tylko bardziej elastyczny niż pliki konfiguracji na poziomie projektu lub mikrousług, ale również bardziej bezpieczne, jeśli zastąpisz zmienne środowiskowe zadeklarowane na pliki docker-compose przy użyciu wartości ustawione na Twoje narzędzia wdrażania, np. z zadania związane z wdrażaniem usługi Azure DevOps usługi Docker. 

Na koniec można uzyskać tę wartość w kodzie za pomocą konfiguracji\["ConnectionString"\], jak pokazano w metodzie ConfigureServices w wcześniejszym przykładzie kodu.

W środowiskach produkcyjnych, może być poznać dodatkowe sposoby na temat przechowywania wpisów tajnych, takich jak parametry połączenia. Zwykle, będą zarządzane przez wybranego koordynatora, jak za pomocą [Docker Swarm zarządzania wpisami tajnymi](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementowanie przechowywania wersji interfejsów API sieci Web platformy ASP.NET

Po zmianie wymagań biznesowych, mogą być dodawane nowe kolekcji zasobów może się zmieniać relacje między zasobami i struktury danych w obszarze zasoby mogą zostać zmienione. Aktualizowanie interfejsu API sieci Web, do obsługi nowych wymagań jest stosunkowo prosta, ale należy wziąć pod uwagę wpływ, mających takie zmiany na aplikacje klienckie korzystające z interfejsu API sieci Web. Mimo że dla deweloperów, projektowania i implementowania internetowego interfejsu API ma pełną kontrolę nad tym Interfejsem, deweloper nie ma tego samego stopnia kontroli nad aplikacji klienckich, które może być kompilowany przez inne podmioty.

Kontrola wersji umożliwia wskazanie funkcji i zasobów udostępnianych internetowego interfejsu API. Aplikacja kliencka można przesłać żądania do określonej wersji funkcji lub zasobu. Istnieją różne podejścia do implementowania obsługi wersji:

-   Identyfikatora URI

-   Przechowywanie wersji parametrów zapytania

-   Nagłówka

Ciąg zapytania i identyfikatora URI są najprostszej implementacji. Nagłówek wersji to dobra metoda. Jednak wersji nagłówka nie jako jawne i prostego jako identyfikatora URI. Ponieważ adres URL wersji najprostszy i najbardziej jawne, przykładowej aplikacji w ramach aplikacji eShopOnContainers używa identyfikatora URI.

Za pomocą identyfikatora URI do przechowywania wersji, tak jak w ramach aplikacji eShopOnContainers przykładowej aplikacji za każdym razem zmodyfikować internetowego interfejsu API lub zmianie schematu zasobów, należy dodać numer wersji do identyfikatorów URI poszczególnych zasobów. Istniejące identyfikatory URI powinny nadal działać jak wcześniej, zwracając zasoby, które są zgodne ze schematem, który odpowiada żądanej wersji.

Jak pokazano w poniższym przykładzie kodu, można ustawić wersję za pomocą atrybutu tras w interfejsie API sieci Web, co sprawia, że wersja jest jawne w identyfikatorze URI (wersja 1, w tym przypadku).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Opisany mechanizm kontroli wersji jest prosty i zależy od serwera kieruje żądania do odpowiednich punktów końcowych. Jednak dla bardziej zaawansowanych wersji i najlepszą metodę, gdy przy użyciu usługi REST, należy użyć hipermediach i zaimplementować [HATEOAS (Hypertext as Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Scott Hanselman. Przechowywanie wersji internetowy interfejs API RESTful platformy ASP.NET Core łatwe**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Przechowywanie wersji internetowego interfejsu API RESTful**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Przechowywanie wersji, Hipermediach i REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Generowanie metadanych opis struktury Swagger z internetowego interfejsu API platformy ASP.NET Core 

[Struktury swagger](https://swagger.io/) jest framework powszechnie używane typu open source objęte dużego ekosystemu narzędzi, które ułatwia projektowanie, kompilowanie, dokument i używanie interfejsów API RESTful. Staje się standardu dla domeny metadane opisu interfejsów API. Powinny zawierać metadane struktury Swagger z dowolnego rodzaju mikrousłudze oraz mikrousług opartego na danych lub bardziej zaawansowane mikrousług opartego na domenach (jak wyjaśniono w poniższej sekcji).

Serce struktury Swagger jest specyfikacją struktury Swagger, czyli metadane opisu interfejsu API w pliku JSON lub YAML. Specyfikacja tworzy RESTful kontrakt interfejsu API, szczegółowych informacji na temat wszystkich jej zasobów i operacji w obu readable człowieka i machine formacie umożliwiające łatwe projektowanie, odnajdywania i integracji.

Specyfikacja to podstawa specyfikację OpenAPI (OAS) i jest tworzone w otwarte, przejrzyste i współpracy społeczności, aby ustandaryzować sposób, w jaki zdefiniowano interfejsów RESTful.

Specyfikacja definiuje strukturę jak usługi mogą być wykrywane i jak zrozumieć jej możliwości. Aby uzyskać więcej informacji, w tym edytora sieci web i przykłady specyfikacji Swagger z firm, takich jak Spotify, Uber, Slack i firmy Microsoft, w witrynie programu Swagger (<https://swagger.io/>).

### <a name="why-use-swagger"></a>Dlaczego warto używać struktury Swagger?

Poniżej przedstawiono główne powody generować metadane programu Swagger dla interfejsów API.

**Możliwości dla innych produktów, automatycznie korzystać i integracja interfejsów API**. Wielu produktów i [narzędzi komercyjnych](https://swagger.io/commercial-tools/) i wielu [bibliotek i platform](https://swagger.io/open-source-integrations/) obsługują strukturę Swagger. Firma Microsoft ma wysokiego poziomu produktów i narzędzi, które automatycznie mogą wykorzystywać struktury Swagger interfejsy API oparte na, takie jak następujące:

-   [AutoRest](https://github.com/Azure/AutoRest). Możesz automatycznie wygenerować klasy klienta platformy .NET do wywoływania struktury Swagger. To narzędzie można używać z interfejsu wiersza polecenia i integruje się również z programem Visual Studio dla łatwą w użyciu przy użyciu graficznego interfejsu użytkownika.

-   [Microsoft Flow](https://flow.microsoft.com/en-us/). Można automatycznie [użycia i integracji interfejsu API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) do ogólny przepływ pracy Microsoft Flow bez umiejętności programowania wymagane.

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). Będzie można korzystać z interfejsu API automatycznie [aplikacji mobilnych w usłudze PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) utworzonych za pomocą [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), nawet bez znajomości programowania wymagane.

-   [Usługa Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Można automatycznie [użycia i integracji interfejsu API w aplikacji usługi Azure App Service Logic](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), nawet bez znajomości programowania wymagane.

**Możliwość automatycznego generowania dokumentacji interfejsu API**. Po utworzeniu na dużą skalę interfejsów API RESTful, takie jak złożone aplikacje oparte na mikrousługach, będzie konieczna Obsługa wielu punktów końcowych przy użyciu różne modele danych używane w ładunkami żądań i odpowiedzi. O prawidłowa dokumentacja, posiadanie solid Eksplorator interfejsu API, jak można uzyskać w strukturze Swagger, jest kluczem do sukcesu interfejsu API i przyjęcia rozwiązania przez deweloperów.

Metadane programu swagger w to, co Microsoft Flow, PowerApps i Azure Logic Apps umożliwia zrozumienie, jak używać interfejsów API i połączyć się z nimi.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Jak zautomatyzować struktury Swagger interfejsu API generowania metadanych przy użyciu pakietu Swashbuckle NuGet

Generowanie metadanych struktury Swagger ręcznie (w pliku JSON lub YAML) może być uciążliwe pracy. Jednak można zautomatyzować odnajdywania interfejsu API usług interfejsu API sieci Web platformy ASP.NET przy użyciu [pakietu Swashbuckle NuGet](https://aka.ms/swashbuckledotnetcore) do dynamicznego generowania metadanych interfejsu API struktury Swagger.

Pakiet Swashbuckle generuje automatycznie metadanych struktury Swagger dla projektów ASP.NET Web API. Obsługuje projekty ASP.NET Core Web API i tradycyjne ASP.NET Web API i innych wersji, takich jak aplikacji interfejsu API platformy Azure, aplikacji mobilnej platformy Azure, Azure Service Fabric mikrousług oparte na programie ASP.NET. Obsługuje ona również zwykły wdrożonych kontenerów, podobnie jak w aplikacji odwołanie do interfejsu API sieci Web.

Pakiet Swashbuckle łączy Eksplorator interfejsu API i struktury Swagger lub [interfejs użytkownika struktury swagger](https://github.com/swagger-api/swagger-ui) zapewnia zaawansowane odnajdywania i dokumentacji komfort klientom interfejsu API. Oprócz silnik generator metadanych struktury Swagger Swashbuckle zawiera osadzony wersję struktury swagger interfejsu użytkownika, który go automatycznie posłużą się po zainstalowaniu pakietu Swashbuckle.

Oznacza to, że mogą uzupełniać interfejsu API dzięki nieuprzywilejowany odnajdywania interfejsu użytkownika, aby pomóc deweloperom korzystanie z interfejsu API. Wymaga niewielką ilość kodu i obsługi, ponieważ jest automatycznie generowany, co pozwala skupić się na tworzeniu interfejsu API. Wynik dla Eksplorator interfejsu API będzie wyglądać jak rysunek 8-8.

![](./media/image9.png)

**Rysunek 8-8**. Eksplorator interfejsu API narzędzia Swashbuckle oparte na metadanych struktury Swagger — w ramach aplikacji eShopOnContainers katalogu mikrousług

Eksplorator interfejsu API nie jest najważniejsza rzecz, w tym miejscu. Po utworzeniu internetowego interfejsu API, który można opisania siebie w metadanych struktury Swagger, interfejsu API można bezproblemowo z narzędzi opartych na strukturze Swagger, takich jak generatorów kodu klasy serwera proxy klienta, które mogą współpracować z wieloma platformami. Na przykład, jak wspomniano [AutoRest](https://github.com/Azure/AutoRest) automatycznie wygeneruje klasy klienta platformy .NET. Ale dodatkowe narzędzia, takie jak [generowanie kodu struktury swagger](https://github.com/swagger-api/swagger-codegen) są również dostępne, która zezwala na generowanie kodu klienta interfejsu API biblioteki, serwera wycinków i dokumentacji automatycznie.

Obecnie narzędzia Swashbuckle składa się z kilku wewnętrznych pakietów NuGet w obszarze wysokiego poziomu meta-package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) wersji 1.0.0 lub nowszym w przypadku aplikacji platformy ASP.NET Core.

Po zainstalowaniu tych pakietów NuGet w projekcie interfejsu API sieci Web, należy skonfigurować struktury Swagger w klasie uruchamiania zgodnie z poniższym kodem:

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

Po zakończeniu tej operacji możesz uruchomić aplikację, a następnie Przeglądaj następujących JSON programu Swagger i interfejs użytkownika punktów końcowych przy użyciu adresów URL, takie jak te:

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

Widać wcześniej wygenerowany interfejsu użytkownika tworzone przez pakiet Swashbuckle dla adresu URL typu http://&lt;adres url katalogu głównego &gt; /swagger/interfejsu użytkownika. W rysunek 8 – 9 widać również sposób testowania dowolnej metody interfejsu API.

![](./media/image10.png)

**Rysunek 8 – 9**. Interfejs użytkownika Swashbuckle testowania metody interfejsu API elementów/katalogu

Rysunek 8 – 10 Wyświetla metadane JSON programu Swagger generowane na podstawie mikrousług w ramach aplikacji eShopOnContainers (czyli narzędzia korzystają poniżej) na żądanie &lt;adres url katalogu głównego&gt;przy użyciu /swagger/v1/swagger.json [NarzędziaPostman](https://www.getpostman.com/).

![](./media/image11.png)

**Rysunek 8 – 10**. Metadane JSON programu swagger

Jest to proste. A ponieważ automatycznie jest generowany, po dodaniu więcej funkcji do interfejsu API będzie się zwiększać metadanych struktury Swagger.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Strony sieci Web ASP.NET API pomocy korzystające z programu Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Poprzednie](microservice-application-design.md)
[dalej](multi-container-applications-docker-compose.md)
