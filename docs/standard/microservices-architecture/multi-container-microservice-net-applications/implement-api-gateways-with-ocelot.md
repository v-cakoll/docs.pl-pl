---
title: Wdrażanie bram interfejsu API za pomocą rozwiązania Ocelot
description: Dowiedz się, jak zaimplementować bramy interfejsu API za pomocą Ocelot i sposobu użycia Ocelot w środowiskach opartych na kontenerach.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 5d4f2a3b2551f8da83359b26578d45559721f7df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776457"
---
# <a name="implement-api-gateways-with-ocelot"></a>Implementowanie bramy interfejsu API za pomocą Ocelot

Aplikacja mikrousług referencyjna [ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) używa [Ocelot](https://github.com/ThreeMammals/Ocelot), prosty i lekkie bramy interfejsu API, które można wdrożyć dowolne miejsce wraz z mikrousług/kontenerów, takich jak w dowolne z następujących środowisk, które są używane w ramach aplikacji eShopOnContainers.

- Hosta platformy docker, dev lokalnym komputerze, lokalnie lub w chmurze.
- Klaster Kubernetes w środowisku lokalnym lub w chmurze zarządzanych, takich jak Azure Kubernetes Service (AKS).
- Klaster usługi Service Fabric w środowisku lokalnym lub w chmurze.
- Usługa Service Fabric siatki jako PaaS/aplikacje niewymagające użycia serwera na platformie Azure.

## <a name="architect-and-design-your-api-gateways"></a>Architektury i projektowania usługi bramy interfejsu API

Poniższy diagram architektury pokazuje, jak bramy interfejsu API są implementowane za pomocą Ocelot w ramach aplikacji eShopOnContainers.

![diagram architektury ramach aplikacji eShopOnContainers przedstawiający klienta aplikacji, mikrousługi i bramy interfejsu API między](./media/image28.png)

**Rysunek 6-28**. Architektura ramach aplikacji eShopOnContainers z bramy interfejsu API

Ten diagram przedstawia, jak cała aplikacja jest wdrażana do jednego hosta platformy Docker lub rozwoju PC "Docker for Windows" lub "Docker dla komputerów Mac". Jednak wdrażanie do dowolnego programu orchestrator mogą być bardzo podobne, ale żaden kontener w diagramie może być skalowanych w poziomie w programie orchestrator.

Ponadto zasobów infrastruktury, takich jak bazy danych, pamięci podręcznej i brokerami powinna być przenoszona z koordynatora i wdrożone do wysokiej dostępności systemów infrastruktury, takich jak Azure SQL Database, Azure Cosmos DB, Azure redis cache, usługa Azure Service Bus lub dowolnego HA klastrowanie rozwiązanie dla środowisk lokalnych.

Jak można również Zwróć uwagę na diagramie, masz kilka bramy interfejsu API umożliwia wielu zespołów programistycznych jako autonomiczny (sprzedaż w tym przypadku funkcje programu vs. Zakupy funkcji) podczas opracowywania i wdrażania ich mikrousługi oraz ich powiązane bramy interfejsu API.

Jeśli masz pojedynczą monolityczne bramą interfejsu API, która oznacza pojedynczy punkt zostać zaktualizowane przez kilka zespołów deweloperskich, które można połączyć wszystkie mikrousługi przy użyciu jednej części aplikacji.

Możesz to zrobić jeszcze więcej możliwości w projekt, czasami szczegółowych bramy interfejsu API można także ograniczona do mikrousług biznesowej, w zależności od wybranej architektury. O granicach bramy interfejsu API definiowane przez firmę lub domeny pomogą uzyskać lepsze projektu.

Na przykład zapewniającym dużą szczegółowość w warstwie bramy interfejsu API może być szczególnie przydatne w przypadku bardziej zaawansowanych aplikacji interfejsu użytkownika złożonych, które są oparte na mikrousługach, ponieważ koncepcji szczegółowych bramy interfejsu API jest podobny do usługi kompozycji interfejsu użytkownika.

Firma Microsoft delve bardziej szczegółowe informacje w poprzedniej sekcji [Tworzenie złożonego interfejsu użytkownika opartego na mikrousługach](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).

Jako kluczowym wnioskiem w przypadku wielu aplikacji i dużych średniego przy użyciu niestandardowej produktu bramy interfejsu API zazwyczaj to dobra metoda, ale nie jako pojedynczy agregatora monolityczne lub unikatowy centralnej interfejsu API bram o ile nie zezwala na wiele niezależnych od tej bramy interfejsu API Konfiguracja obszarów dla kilku zespołów deweloperskich, Tworzenie autonomicznego mikrousług.

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a>Przykładowe mikrousług/kontenerów, aby ponownie rozesłać za pośrednictwem bramy interfejsu API

Na przykład w ramach aplikacji eShopOnContainers ma około sześciu mikrousługi — typy wewnętrzne, które mają być opublikowane za pośrednictwem bramy interfejsu API, jak pokazano na poniższej ilustracji.

![Tylko mikrousług koszyka, katalog, lokalizacji, Marketing, porządkowanie i płatności są publikowane za pośrednictwem bramy interfejsu API.](./media/image29.png)

**Rysunek 6-29**. Mikrousługi folderów w ramach aplikacji eShopOnContainers rozwiązania w programie Visual Studio

O usłudze tożsamości w projekcie pozostaje ona poza bramy interfejsu API, routing jest jedyna kwestią przekrojowe w systemie, mimo że z Ocelot istnieje również możliwość dołączyć go jako część listy przekierowania.

Wszystkie te usługi aktualnie są implementowane jako usługi internetowego interfejsu API platformy ASP.NET Core, jak można stwierdzić, z kodu. Skupmy się na jednym z mikrousług, podobnie jak kod mikrousług katalogu.

![Widok Eksploratora rozwiązania Catalog.API projektu.](./media/image30.png)

**Rysunek 6 – 30**. Przykładowy internetowy interfejs API mikrousług (mikrousług katalogu)

Widać, że mikrousługa wykazu jest typowym projekcie internetowego interfejsu API platformy ASP.NET Core za pomocą kilku kontrolerów i metod, takich jak w poniższym kodzie.

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

Żądanie HTTP zostaną uruchomione, który rodzaj C# uzyskiwanie dostępu do bazy danych mikrousług i wszelkie dodatkowe wymagane działania kodu.

Dotyczące adresu URL mikrousług, gdy kontenery są wdrażane Tworzenie lokalnego komputera (lokalnego hosta platformy Docker), każda mikrousługa kontener ma zawsze to port wewnętrzny (zwykle jest to port 80) określona w pliku dockerfile i tak jak w poniższym pliku dockerfile:

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

Port 80, jak pokazano w kodzie jest wewnętrzny w ramach hosta platformy Docker, więc nie można nawiązać połączenia przez aplikacje klienckie.

Aplikacje klienckie mogą uzyskiwać dostęp tylko zewnętrzne porty (jeśli istnieje), gdy wdrażanie przy użyciu `docker-compose`.

Nie należy można opublikować tych portów zewnętrznych, w przypadku wdrażania w środowisku produkcyjnym. Jest to dokładnie, dlaczego chcesz używać bramy interfejsu API, aby uniknąć bezpośrednia komunikacja między aplikacjami klienta i mikrousług.

Jednak podczas opracowywania, ma bezpośredni dostęp mikrousług/kontenera i uruchom je za pośrednictwem struktury Swagger. Właśnie w ramach aplikacji eShopOnContainers portów zewnętrznych są nadal zaznaczone nawet wtedy, gdy nie będą używane przez bramę interfejsów API lub aplikacje klienckie.

Oto przykład `docker-compose.override.yml` pliku dla mikrousług katalogu:

```yml
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

Możesz zobaczyć, jak w konfiguracji platformy docker-compose.override.yml wewnętrzny port kontenera wykazu jest port 80, ale numer portu na potrzeby dostępu zewnętrznego to 5101. Jednak ten port nie powinien używanych przez aplikację, za pomocą bramy interfejsu API tylko debugowanie, uruchamianie i testowanie po prostu mikrousług katalogu.

Zwykle nie można wdrożyć za pomocą platformy docker-compose w środowisku produkcyjnym, ponieważ środowisko wdrażania produkcyjnym mikrousług jest koordynatora Kubernetes lub usługi Service Fabric. Podczas wdrażania tych środowisk użyjesz różnymi plikami konfiguracji gdzie nie będzie publikować bezpośrednio dowolnym porcie zewnętrznym mikrousług, ale, będzie zawsze używać zwrotny serwer proxy z bramy interfejsu API.

Uruchamianie mikrousług wykazu w lokalnego hosta platformy Docker, uruchamiając rozwiązania pełnego w ramach aplikacji eShopOnContainers z programu Visual Studio (go uruchomić wszystkie usługi na platformie docker-tworzą pliki) lub po prostu uruchamianie mikrousług katalogu za pomocą następujących platformy docker-compose polecenia w pliku polecenia lub programu PowerShell umieszczony w folderze gdzie `docker-compose.yml` i są umieszczane docker-compose.override.yml.

```console
docker-compose run --service-ports catalog.api
```

To polecenie uruchamia tylko catalog.api usługi kontenera, a także zależności, które są określone w docker-compose.yml. W takim kontenera programu SQL Server i oprogramowania RabbitMQ kontenera.

Następnie można również bezpośrednio dostęp do mikrousług katalogu a jego metod za pośrednictwem interfejsu użytkownika programu Swagger bezpośrednio za pomocą dostęp, czy "external" portu, w tym przypadku `http://localhost:5101/swagger`:

![Widok przeglądarki wieku interfejs użytkownika struktury Swagger dla interfejsu API REST Catalog.API.](./media/image31.png)

**Rysunek 6-31**. Testowanie mikrousług katalogu za pomocą jego interfejsu użytkownika programu Swagger

W tym momencie można ustawić punkt przerwania w kodzie języka C# w programie Visual Studio, testowanie mikrousług za pomocą metod udostępnianych w interfejs użytkownika struktury Swagger i na koniec oczyszczania wszystkiego za pomocą `docker-compose down` polecenia.

Jednak dostęp bezpośredni komunikacja z mikrousług, w tym przypadku za pośrednictwem portu zewnętrznego 5101 jest dokładnie chce się uniknąć w aplikacji. I można uniknąć, ustawiając dodatkowy poziom pośredni bramy interfejsu API (w tym przypadku Ocelot). Dzięki temu aplikacja kliencka nie uzyskać bezpośredni dostęp do mikrousług.

## <a name="implementing-your-api-gateways-with-ocelot"></a>Wdrażanie usługi bramy interfejsu API za pomocą Ocelot

Ocelot jest zasadniczo zbiorem middlewares, które można zastosować w określonej kolejności.

Ocelot jest przeznaczona do pracy z platformą ASP.NET Core tylko. Jest ono przeznaczone dla netstandard2.0, dzięki czemu może służyć wszędzie tam, gdzie .NET Standard 2.0 jest obsługiwane, w tym środowiska uruchomieniowego .NET Core 2.0 i środowiska uruchomieniowego .NET Framework 4.6.1 oraz jego nowszymi wersjami.

Zainstaluj Ocelot i jego zależności w projekcie platformy ASP.NET Core za pomocą [pakietu NuGet w Ocelot](https://www.nuget.org/packages/Ocelot/), z programu Visual Studio.

```powershell
Install-Package Ocelot
```

W ramach aplikacji eShopOnContainers jego implementacja bramy interfejsu API jest prosty projekt hostem sieci Web platformy ASP.NET Core i middlewares firmy Ocelot obsługi wszystkie funkcje bramy interfejsu API, jak pokazano na poniższej ilustracji:

![Widok Eksploratora rozwiązania projekt bramy interfejsu API Ocelot.](./media/image32.png)

**Rysunek 6 – 32**. Podstawowy projekt OcelotApiGw w ramach aplikacji eShopOnContainers

Ten projekt hostem sieci Web platformy ASP.NET Core zasadniczo został utworzony za pomocą dwóch prostych plików: `Program.cs` i `Startup.cs`.

Plik Program.cs musi jedynie tworzyć i konfigurować typowe BuildWebHost Core ASP.NET.

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

Należy koniecznie zwrócić uwagę na Ocelot jest `configuration.json` pliku, który należy podać do konstruktora za pośrednictwem `AddJsonFile()` metody. Czy `configuration.json` służy do określania wszystkich interfejsu API bramy ReRoutes, co oznacza, zewnętrzne punkty końcowe o określonych portów i skorelowane wewnętrznych punktów końcowych, zazwyczaj przy użyciu różnych portów.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Istnieją dwie sekcje w konfiguracji. Tablica przekieruje i GlobalConfiguration. Przekieruje to obiekty, które Ocelot stwierdzić, jak ma traktować żądania nadrzędnego. Jego konfigurację globalną umożliwia zastąpienia przekierowuje określone ustawienia. Jest to przydatne, jeśli nie chcesz zarządzać mnóstwo przekierowuje określone ustawienia.

Oto uproszczony przykład [pliku konfiguracji przekierowania](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jednego z bramy interfejsu API w ramach aplikacji eShopOnContainers.

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

Główne funkcje bramy interfejsu API Ocelot jest przychodzących żądań HTTP i przekazują je do podrzędnego usługa, obecnie jako innego protokołu HTTP żądania. Firmy ocelot Opisuje routing jedno żądanie do innego jako ponownie rozesłać.

Na przykład Skupmy się na jednym z przekieruje w configuration.json powyższej konfiguracji dla mikrousług koszyka.

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

DownstreamPathTemplate, schemat i DownstreamHostAndPorts należy mikrousług wewnętrzny adres URL, z którego to żądanie, które zostaną przekazane do.

Numer portu to port wewnętrzny używany przez usługę. Podczas korzystania z kontenerów, port określony w odpowiednim plikiem dockerfile.

`Host` Jest nazwą usługi, która jest zależna od usługi rozpoznawania nazw, używasz. Korzystając z platformy docker-compose usług nazwy są dostarczane przez hosta platformy Docker, który używa nazwy usługi udostępniane na platformie docker-tworzą pliki. Jeśli używasz programu orchestrator, takich jak Kubernetes lub usługi Service Fabric, tej nazwy powinny być rozpoznawane przez DNS lub rozpoznawania nazw, dostarczone przez poszczególnych koordynatorów.

DownstreamHostAndPorts jest tablica zawierająca hosta i portu usługami podrzędnymi, które chcesz przekazywać żądania do. Zwykle to po prostu zawiera jeden wpis, ale czasami możesz chcieć równoważenia obciążenia żądań kierowanych do usługi transmisji i Ocelot pozwala dodać więcej niż jeden wpis, a następnie wybierz moduł równoważenia obciążenia. Ale jeśli za pomocą platformy Azure i wszelkie orchestrator jest prawdopodobnie lepiej zrozumieć równoważenia obciążenia za pomocą infrastruktury chmury i programu orchestrator.

UpstreamPathTemplate jest adres URL, który Ocelot będzie używany do identyfikowania które DownstreamPathTemplate do użycia dla danego żądania od klienta. Na koniec UpstreamHttpMethod jest używana, więc Ocelot można odróżnić różne żądania (POST, GET PUT) do tego samego adresu URL.

W tym momencie może mieć jednej bramy interfejsu API Ocelot (ASP.NET Core WebHost) przy użyciu jednej lub [wielu scalić pliki configuration.json](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) lub można również przechowywać [konfiguracji w magazynie KV Konsul](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).

Ale wprowadzoną w sekcjach architektury i projektu, jeśli na pewno chcesz mieć autonomicznego mikrousług, może być lepszym rozwiązaniem podzielić tego jednego monolityczne bramy interfejsu API na wiele bramy interfejsu API i/lub BFF (zaplecze dla frontonu). W tym celu Zobaczmy, jak zaimplementować podejście z kontenerami aparatu Docker.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Przy użyciu jednego obrazu kontenera platformy Docker w celu uruchamiania wielu różnych bramy interfejsu API / BFF typy kontenera

W ramach aplikacji eShopOnContainers firma Microsoft korzysta z jednego obrazu kontenera platformy Docker przy użyciu bramy interfejsu API Ocelot, ale następnie w czasie wykonywania, tworzymy różnych usług/kontenerów dla każdego typu interfejsu API — bramy/BFF, zapewniając configuration.json innego pliku, za pomocą woluminu platformy docker dostęp do innego folderu PC dla każdej usługi.

![Pojedynczy obraz platformy Docker dla interfejsu API Ocelot bramy jest używany dla wszystkich czterech bramy interfejsu API](./media/image33.png)

**Rysunek 6-33**. Ponownie za pomocą pojedynczego obrazu platformy Docker Ocelot wielu typów bramy interfejsu API

W ramach aplikacji eShopOnContainers, "Ogólnego Ocelot interfejsu API bramy obrazu platformy Docker" jest tworzony za pomocą projektu o nazwie "OcelotApiGw" i obrazu nazwę "eshop/ocelotapigw", oznacza to określone w pliku docker-compose.yml. Następnie podczas wdrażania do platformy Docker, nastąpi cztery kontenery bramy interfejsu API utworzonego na podstawie tego samego obrazu Docker, jak pokazano w poniższym wyodrębnione z pliku docker-compose.yml.

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

Ponadto, jak pokazano w następującym pliku docker-compose.override.yml, jedyną różnicą między tymi kontenerów bramy interfejsu API jest Ocelot pliku konfiguracji, który jest inny dla każdego kontenera usługi i jest określony w czasie wykonywania za pomocą Wolumin platformy docker.

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

W związku z tym poprzedni kod i zgodnie z informacjami w Eksploratorze programu Visual Studio poniżej to jedyny plik niezbędnej do zdefiniowania każdego określonego firm/BFF bramy interfejsu API jest po prostu plikiem configuration.json, ponieważ cztery bramy interfejsu API są oparte na ten sam obraz platformy Docker.

![Jedyną różnicą między wszystkimi bramami interfejsu API jest plikiem configuration.json na każdym z nich.](./media/image34.png)

**Rysunek 6-34**. To jedyny plik niezbędnej do zdefiniowania każdej bramy interfejsu API / BFF z Ocelot to plik konfiguracji

Dzieląc bramy interfejsu API na wiele bram interfejsu API, zespoły deweloperów różnych, skupiając się na różne podzbiory mikrousług można zarządzać własne bramy interfejsu API za pomocą niezależnych plikach konfiguracji Ocelot. Ponadto w tym samym czasie można wykorzystać ten sam obraz platformy Docker Ocelot.

Teraz po uruchomieniu ramach aplikacji eShopOnContainers przy użyciu bramy interfejsu API (domyślnie włączone w programie VS podczas otwierania rozwiązania w ramach aplikacji eShopOnContainers ServicesAndWebApps.sln, czy działa "docker-compose up"), zostaną wykonane następujące trasy próbki.

Na przykład podczas odwiedzania adresu URL połączenia nadrzędnego `http://localhost:5202/api/v1/c/catalog/items/2/` obsługiwanej przez webshoppingapigw bramy interfejsu API, otrzymasz ten sam wynik z wewnętrznego adresu URL podrzędne `http://catalog.api/api/v1/2` w ramach hosta platformy Docker, tak jak w poniższym przeglądarki.

![Widok w przeglądarce odpowiedź z Catalog.api przechodzenia przez bramy interfejsu API.](./media/image35.png)

**Rysunek 6 – 35**. Uzyskiwanie dostępu do mikrousług przy użyciu adresu URL podany przez bramę interfejsu API

Ze względu na testowania i debugowania ze względu na, jeśli chce się uzyskać bezpośredni dostęp do kontenera Docker katalogu (tylko w środowisku programistycznym), bez przekazywania przez bramę interfejsu API, ponieważ "catalog.api" jest wewnętrznym hosta platformy Docker (usługa rozpoznawania nazw DNS Odnajdywanie obsługiwane przez docker-compose nazw usług), jedynym sposobem uzyskiwania bezpośredniego dostępu do kontenera jest za pośrednictwem portu zewnętrznego, opublikowane w docker-compose.override.yml, która jest dostępna tylko w przypadku tworzenia testów, takich jak `http://localhost:5101/api/v1/Catalog/items/1` poniżej Przeglądarka.

![Widok w przeglądarce odpowiedź z Catalog.api, przechodząc bezpośrednio do Catalog.api, identyczne z za pośrednictwem bramy interfejsu API.](./media/image36.png)

**Rysunek 6-36**. Bezpośredni dostęp do mikrousług do celów testowych

Ale gdy aplikacja jest skonfigurowana, dzięki czemu uzyskuje dostęp wszystkie mikrousługi za pośrednictwem bramy interfejsu API nie jest jednak przeniesiony bezpośrednio "skróty".

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>Wzorzec agregacji za pomocą bramy w ramach aplikacji eShopOnContainers

Jak wprowadzone wcześniej, elastyczny sposób implementacji agregacji żądania jest za pomocą niestandardowych usług przez kod. Można również wdrożyć Agregacja żądania z [funkcji agregacji żądania w Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale może nie być tak elastyczne, ilu potrzebujesz. Dlatego wybrane sposobem realizowania agregacji w ramach aplikacji eShopOnContainers jest jawne usługi internetowego interfejsu API platformy ASP.NET Core dla każdego agregatora.

Zgodnie z tego podejścia diagram składu bramę interfejsu API jest w rzeczywistości nieco bardziej rozszerzone podczas wybierania usługi agregatora, które nie są wyświetlane na diagramie uproszczona architektura globalnego przedstawionego wcześniej.

Na poniższym diagramie widać również jak usług agregatora odnoszą się do ich powiązane bramy interfejsu API.

![Architektura ramach aplikacji eShopOnContainers przedstawiająca usługi agregatora.](./media/image37.png)

**Rysunek 6-37**. Architektura ramach aplikacji eShopOnContainers z usługami agregatora

Ponadto powiększanie obszar działalności "Zakupów" na poniższej ilustracji widać, że liczby operacji między aplikacjami klienta i mikrousług jest obniżona podczas korzystania z usług agregator w bramy interfejsu API.

![ramach aplikacji eShopOnContainers architektury Powiększ, przedstawiający usług agregator, który "składa" odpowiedź "łączenie" odpowiedź z wielu mikrousług, co umożliwia ograniczenie liczby operacji za pomocą klienta końcowego.](./media/image38.png)

**Rysunek 6-38**. Powiększ wizji usług agregatora

Można zauważyć, jak podczas na diagramie przedstawiono możliwe żądania pochodzące z bramy interfejsu API go uzyskać dość złożony. Mimo że można zobaczyć, jak strzałki w kolorze niebieskim będzie można uprościć, z punktu widzenia aplikacji klienta podczas używania wzorca agregatora, zmniejszając liczbę operacji i opóźnień w komunikacji, ostatecznie znacznego poprawienia użytkownika środowisko (aplikacje zdalne aplikacje mobilne i SPA), szczególnie.

W przypadku "Marketing" obszar działalności i mikrousług jest bardzo prosty przypadek użycia, więc nie istniała potrzeba, aby użyć agregatora, ale może być również możliwe, jeśli to konieczne.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Uwierzytelnianie i autoryzacja w Ocelot bramy interfejsu API

W przypadku bramy interfejsu API Ocelot może się znajdować usługi uwierzytelniania, na przykład usługi internetowego interfejsu API platformy ASP.NET Core przy użyciu [IdentityServer](https://identityserver.io/) dostarczanie token uwierzytelniania, w poziomie lub w ramach bramy interfejsu API.

Ponieważ jest w ramach aplikacji eShopOnContainers przy użyciu wielu bramy interfejsu API z granicami oparte na BFF i obszarów działalności, usługa tożsamości/Auth pozostanie poza bramy interfejsu API, jak podkreślono na żółto na poniższym diagramie.

![diagram architektury w ramach aplikacji eShopOnContainers przedstawiający mikrousług tożsamości poniżej bramy interfejsu API.](./media/image39.png)

**Rysunek 6-39**. Pozycja Usługa zarządzania tożsamościami w ramach aplikacji eShopOnContainers

Jednak Ocelot obsługuje również, znajdują się mikrousług tożsamości/uwierzytelnianie w ramach bramy interfejsu API, tak jak ten inny diagram.

![Uwierzytelnianie przy użyciu mikrousług tożsamości poniżej bramy interfejsu API (AG): (1) AG żąda tokenu uwierzytelniania z mikrousług tożsamości, mikrousługi tożsamości (2) zwraca toke do grupy dostępności, AG żądań 3 - 4) z mikrousług przy użyciu tokenu uwierzytelniania.](./media/image40.png)

**Rysunek 6-40**. Uwierzytelnianie w Ocelot

Ponieważ aplikacji w ramach aplikacji eShopOnContainers została podzielona bramy interfejsu API na wiele BFF (zaplecze dla serwera sieci Web) i obszarów działalności bramy interfejsu API i inną opcją będzie była do utworzenia dodatkowych bramy interfejsu API dla odciąż przekrojowe zagadnienia. Wybór będzie podejście w bardziej złożonych mikrousług na podstawie architektury z wielu mikrousług odciąż przekrojowe zagadnienia. Ponieważ istnieje tylko jeden kwestią przekrojowe w ramach aplikacji eShopOnContainers, zdecydowano tylko obsługi usługi zabezpieczeń z obszaru bramy interfejsu API dla uproszczenia firmy sake.

W każdym przypadku jeśli aplikacja jest zabezpieczona na poziomie bramy interfejsu API, moduł uwierzytelniania bramy interfejsu API Ocelot odwiedzeniu na początku podczas próby użycia wszystkie mikrousługi zabezpieczone. Który ponownie kieruje żądania HTTP, aby odwiedzić tożsamości lub uwierzytelniania mikrousługi można pobrać tokenu dostępu, dzięki czemu użytkownik może odwiedzić usługami chronionymi za pomocą access_token.

Metodą zabezpieczanie przy użyciu uwierzytelniania dowolnej usługi na poziomie bramy interfejsu API jest ustawienie AuthenticationProviderKey w powiązanych ustawieniami configuration.json.

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

Po uruchomieniu Ocelot go odczyta AuthenticationOptions.AuthenticationProviderKey przekieruje i sprawdź, czy dostawcę uwierzytelniania, zarejestrowanych z danym kluczem. Jeśli nie istnieje, następnie Ocelot nie zostanie uruchomiony. Jeśli, następnie przekierowanie użyje tego dostawcy, podczas wykonywania.

Ponieważ skonfigurowano Ocelot WebHost `authenticationProviderKey = "IdentityApiKey"`, mogą one wymagać uwierzytelniania zawsze wtedy, gdy tej usługi zawiera wszystkich żądań bez żadnych tokenu uwierzytelniania.

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

Następnie również należy ustawić autoryzacji za pomocą atrybutu [Authorize] na żaden zasób były dostępne takich jak mikrousługi, takie jak w następującym kontrolerem mikrousług koszyka.

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

ValidAudiences, takie jak "koszyka" są powiązane z odbiorcami zdefiniowane w poszczególne mikrousługi przy użyciu `AddJwtBearer()` na ConfigureServices() klasy uruchamiania, taki jak poniższy kod.

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

Jeśli zostanie podjęta próba dostępu do żadnych zabezpieczonej mikrousług, takich jak koszyka mikrousług przy użyciu adresu URL przekierowuje na podstawie bramy interfejsu API, takich jak `http://localhost:5202/api/v1/b/basket/1`, a następnie otrzymasz 401 Brak autoryzacji, chyba że należy podać prawidłowy token. Z drugiej strony Jeśli adres URL przekierowuje jest uwierzytelniony, Ocelot wywoła, niezależnie od transmisji schemat jest skojarzony z nim (adres URL wewnętrznej mikrousług).

**Autoryzacja w warstwie ReRoutes Ocelot firmy.**  Ocelot obsługuje autoryzacji opartej na oświadczeniach, ocenione po uwierzytelniania. Autoryzacja jest ustawiona na poziomie trasy, dodając następujące wiersze do konfiguracji przekierowania.

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

W tym przykładzie wywołanego oprogramowania pośredniczącego autoryzacji Ocelot znajdzie Jeśli użytkownik ma typ oświadczenia "UserType" w tokenie, a wartość to roszczenie "pracownik". Jeśli nie, użytkownik nie będzie autoryzowany, a odpowiedź będzie miała 403 — Dostęp zabroniony.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Przy użyciu transferu danych przychodzących rozwiązania Kubernetes, a także Ocelot interfejsu API bramy

Korzystając z rozwiązania Kubernetes (na przykład w klastrze usługi Azure Kubernetes Service), zwykle ujednolicenie żądań HTTP za pośrednictwem [warstwy transferu danych przychodzących rozwiązania Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) na podstawie *Nginx*.

W usłudze Kubernetes Jeśli nie używasz jakiejkolwiek metody transferu danych przychodzących, następnie zasobników i usług mają adresy IP tylko routing przez sieć klastra.

Jednak jeśli używasz metody transferu danych przychodzących, będziesz mieć warstwy środkowej między Internetem a usługi (łącznie z bram Twojego interfejsu API), działający jako zwrotny serwer proxy.

Definicja ruchu przychodzącego to zbiór reguł zezwalających na połączenia przychodzące do uzyskania dostępu do usług klastrowania. Ruch przychodzący zazwyczaj jest skonfigurowany do Podaj dostępny zewnętrznie adresów URL usług, obciążenia równoważenia ruchu, kończenie żądań SSL i nie tylko. Użytkownicy żądanie transferu danych przychodzących, publikując zasobów transferu danych przychodzących do serwera interfejsu API.

W ramach aplikacji eShopOnContainers, podczas opracowywania lokalnie i za pomocą tylko maszynie deweloperskiej jako hosta platformy Docker nie używasz dowolnego ruchu przychodzącego, ale tylko wielu bramy interfejsu API.

Jednak gdy przeznaczonych dla środowiska "produkcyjne", oparte na platformie Kubernetes, ramach aplikacji eShopOnContainers korzysta z transferu danych przychodzących przed bramy interfejsu API. Dzięki temu klienci wciąż wywołać tego samego podstawowego adresu URL, ale żądania są kierowane do wielu bram API lub BFF.

Należy pamiętać, że bramy interfejsu API są Frontony lub elewacje, dzięki czemu są ujawniane tylko usług, ale nie aplikacje sieci web, które są zazwyczaj poza ich zakresem. Ponadto bramy interfejsu API może ukryć niektórych wewnętrznych mikrousług.

Ruch przychodzący, jednak jest po prostu Przekierowywanie żądań HTTP, ale nie próbuje ukryć wszystkie mikrousługi lub aplikacji sieci web.

Posiadanie warstwą Nginx ruch przychodzący w usłudze Kubernetes przed aplikacji sieci web, a także kilka bramy interfejsu API Ocelot / BFF jest idealnym rozwiązaniem architektury, jak pokazano na poniższym diagramie.

![Przychodzący Kubernetes działa jako zwrotny serwer proxy dla całego ruchu do aplikacji, w tym aplikacje sieci web, które zazwyczaj są poza zakresem bramy interfejsu Api.](./media/image41.png)

**Rysunek 6-41**. Warstwa danych przychodzących w ramach aplikacji eShopOnContainers podczas wdrażania do rozwiązania Kubernetes

Gdy wdrażasz ramach aplikacji eShopOnContainers do rozwiązania Kubernetes, udostępnia kilka usług lub punktów końcowych za pośrednictwem _ruch przychodzący_, po prostu poniżej postfixes na adresy URL:

- `/` SPA klienta aplikacji sieci web
- `/webmvc` dla klienta aplikacji sieci web MVC
- `/webstatus` Wyświetlanie stanu/healthchecks aplikacji sieci web klienta
- `/webshoppingapigw` dla sieci web BFF i zakupów procesów biznesowych
- `/webmarketingapigw` dla sieci web BFF i marketingu procesów biznesowych
- `/mobileshoppingapigw` dla mobilnych BFF i zakupów procesów biznesowych
- `/mobilemarketingapigw` przenośne BFF i marketingowych procesów biznesowych

Podczas wdrażania usługi Kubernetes, każdej bramy interfejsu API Ocelot jest używany plik różnych "configuration.json" dla każdego _zasobnika_ uruchamianie bramy interfejsu API. Te pliki "configuration.json" są dostarczane przez zainstalowanie (pierwotnie ze skryptem deploy.ps1) wolumin utworzony w oparciu o usługi Kubernetes _mapy config_ o nazwie "ocelot". Każdy kontener instaluje jego pliku konfiguracji powiązane w folderze kontenera o nazwie `/app/configuration`.

W ramach aplikacji eShopOnContainers plików kodu źródłowego oryginalnych plików "configuration.json" znajdują się w obrębie `k8s/ocelot/` folderu. Istnieje jeden plik dla każdego BFF/APIGateway.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Dodatkowe funkcje przekrojowe bramy interfejsu API Ocelot

Istnieją inne ważne funkcje zbadaniu i użyć w przypadku użycia Ocelot bramy interfejsu API, opisane w poniższych łączy.

- **Odnajdowanie usługi integracji Ocelot z Konsul lub Eureka po stronie klienta** \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **Pamięć podręczna w warstwie bramy interfejsu API** \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **Rejestrowanie na poziomie warstwy bramy interfejsu API** \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **Jakość usług (ponownych prób i wyłączniki) w warstwie bramy interfejsu API** \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **Ograniczanie szybkości** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Poprzednie](background-tasks-with-ihostedservice.md)
> [dalej](../microservice-ddd-cqrs-patterns/index.md)
