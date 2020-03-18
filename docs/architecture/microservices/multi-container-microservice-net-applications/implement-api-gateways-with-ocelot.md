---
title: Wdrażanie bram interfejsu API za pomocą rozwiązania Ocelot
description: Dowiedz się, jak implementować bramy interfejsu API za pomocą ocelota i jak używać Ocelota w środowisku opartym na kontenerach.
ms.date: 03/02/2020
ms.openlocfilehash: 28b9ca22d232baf3545d71b876cecf72fea05c92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846949"
---
# <a name="implement-api-gateways-with-ocelot"></a>Implementowanie bram interfejsu API za pomocą ocelota

> [!IMPORTANT]
> Aplikacja mikrousług referencyjnych [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) używa obecnie funkcji dostarczonych przez [wysłannika](https://www.envoyproxy.io/) do zaimplementowania bramy interfejsu API zamiast wcześniejszego odwołania [Ocelot](https://github.com/ThreeMammals/Ocelot).
> Dokonaliśmy tego wyboru projektu ze względu na wbudowaną obsługę protokołu WebSocket firmy Envoy, wymaganą przez nową komunikację międzyserwisową gRPC zaimplementowane w eShopOnContainers.
> Jednak zachowaliśmy tę sekcję w przewodniku, dzięki czemu można rozważyć Ocelot jako prostą, zdolną i lekką bramę interfejsu API odpowiednią dla scenariuszy klasy produkcyjnej.

## <a name="architect-and-design-your-api-gateways"></a>Projektowanie i projektowanie bram interfejsu API

Na poniższym diagramie architektury pokazano, jak bramy interfejsu API zostały zaimplementowane za pomocą Ocelot w eShopOnContainers.

![Diagram przedstawiający architekturę eShopOnContainers.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

**Rysunek 6-28**. Architektura eShopOnContainers z bramami interfejsu API

Ten diagram pokazuje, jak cała aplikacja jest wdrażana w jednym hoście platformy Docker lub komputerze deweloperscym z "Docker for Windows" lub "Docker for Mac". Jednak wdrażanie w dowolnym koordynatorem będzie podobny, ale każdy kontener na diagramie może być skalowany w sposób skalowany w koordynatorze.

Ponadto zasoby infrastruktury, takie jak bazy danych, pamięć podręczna i brokerzy komunikatów, powinny zostać odciążone od koordynatora i wdrożone w wysoko dostępnych systemach infrastruktury, takich jak baza danych SQL Azure, usługa Azure Cosmos DB, usługa Azure Redis, usługa Azure Service Bus, lub dowolnego rozwiązania klastrowania ha w środowisku lokalnym.

Jak można również zauważyć na diagramie, mając kilka bram interfejsu API umożliwia wiele zespołów programistycznych być autonomiczne (w tym przypadku funkcje marketingu vs. funkcje zakupów) podczas opracowywania i wdrażania ich mikrousług oraz własnych powiązanych bram interfejsu API.

Jeśli masz jedną monolityczną bramę interfejsu API, co oznaczałoby jeden punkt do aktualizacji przez kilka zespołów programistycznych, które mogą łączyć wszystkie mikrousługi z jednej części aplikacji.

Idąc znacznie dalej w projekcie, czasami szczegółowe bramy interfejsu API może być również ograniczona do mikrousługi pojedynczej firmy w zależności od wybranej architektury. Posiadanie granic bramy interfejsu API podyktowanych przez firmę lub domenę pomoże Ci uzyskać lepszy projekt.

Na przykład szczegółowość w warstwie bramy interfejsu API może być szczególnie przydatne w przypadku bardziej zaawansowanych złożonych aplikacji interfejsu i zestawienia, które są oparte na mikrousługach, ponieważ pojęcie szczegółowej bramy interfejsu API jest podobny do usługi kompozycji interfejsu interfejsu i informacji.

Zagłębiamy się w więcej szczegółów w poprzedniej sekcji [Tworzenie złożonego interfejsu opartego na mikrousługach](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).

Jako klucz na wynos, dla wielu średnich i dużych aplikacji, przy użyciu niestandardowego produktu Bramy interfejsu API jest zwykle dobrym podejściem, ale nie jako jeden monolityczny agregator lub unikatowa centralna niestandardowa brama interfejsu API, chyba że brama interfejsu API umożliwia wiele niezależnych obszary konfiguracji dla kilku zespołów programistycznych tworzących autonomiczne mikrousługi.

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>Przykładowe mikrousługi/kontenery do przekierowania za pośrednictwem bram interfejsu API

Na przykład eShopOnContainers ma około sześciu wewnętrznych typów mikrousług, które muszą zostać opublikowane za pośrednictwem bram interfejsu API, jak pokazano na poniższej ilustracji.

![Zrzut ekranu przedstawiający folder Usługi z jego podfolderami.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

**Rysunek 6-29**. Foldery mikrousług w rozwiązaniu eShopOnContainers w programie Visual Studio

Jeśli chodzi o usługę Identity, w projekcie jest ona pozostawiona z routingu bramy interfejsu API, ponieważ jest to jedyny problem przekrojowy w systemie, chociaż w ocelot jest również możliwe dołączenie go jako część list przekierowowania.

Wszystkie te usługi są obecnie implementowane jako ASP.NET podstawowych usług interfejsu API sieci Web, jak można powiedzieć z kodu. Skupmy się na jednej z mikrousług, takich jak kod mikrousługi katalogu.

![Zrzut ekranu przedstawiający Eksploratora rozwiązań z zawartością projektu Catalog.API.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

**Rysunek 6-30**. Przykładowa mikrousługa interfejsu API sieci Web (mikrousługa katalogu)

Widać, że mikrousługi katalogu jest typowym ASP.NET core web api projektu z kilku kontrolerów i metod, takich jak w poniższym kodzie.

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

Żądanie HTTP zakończy się uruchomienietego tego rodzaju kodu C# dostępu do bazy danych mikrousług i wszelkie dodatkowe wymagane działania.

Jeśli chodzi o adres URL mikrousługi, gdy kontenery są wdrażane na komputerze deweloperskim lokalnego (lokalny host platformy Docker), każdy kontener mikrousługi ma zawsze port wewnętrzny (zwykle port 80) określony w pliku dockerfile, jak w następującym pliku dockerfile:

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

Port 80 wyświetlany w kodzie jest wewnętrzny w hoście platformy Docker, więc nie można do niego dotrzeć przez aplikacje klienckie.

Aplikacje klienckie mogą uzyskiwać dostęp tylko do `docker-compose`portów zewnętrznych (jeśli istnieją) opublikowanych podczas wdrażania z .

Te porty zewnętrzne nie powinny być publikowane podczas wdrażania w środowisku produkcyjnym. Właśnie dlatego chcesz użyć bramy interfejsu API, aby uniknąć bezpośredniej komunikacji między aplikacjami klienckimi a mikrousługami.

Jednak podczas opracowywania chcesz uzyskać dostęp do mikrousługi/kontenera bezpośrednio i uruchomić go za pośrednictwem Swagger. Dlatego w eShopOnContainers porty zewnętrzne są nadal określone, nawet jeśli nie będą używane przez bramę interfejsu API lub aplikacje klienckie.

Oto przykład `docker-compose.override.yml` pliku mikrousługi katalogu:

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

W konfiguracji pliku docker-compose.yml można zobaczyć, jak w konfiguracji docker-compose.override.yml port wewnętrzny kontenera wykazu to port 80, ale port dostępu zewnętrznego to 5101. Ale ten port nie powinien być używany przez aplikację podczas korzystania z bramy interfejsu API, tylko do debugowania, uruchamiania i testowania tylko mikrousługi katalogu.

Zwykle nie będzie wdrażać z docker-compose w środowisku produkcyjnym, ponieważ odpowiednie środowisko wdrażania produkcyjnego dla mikrousług jest koordynatorem, takich jak Kubernetes lub sieci szkieletowej usług. Podczas wdrażania w tych środowiskach używasz różnych plików konfiguracyjnych, gdzie nie będzie publikować bezpośrednio żadnego portu zewnętrznego dla mikrousług, ale zawsze będziesz używać zwrotnego serwera proxy z bramy interfejsu API.

Uruchom mikrousługę katalogu w lokalnym hoście platformy Docker. Uruchom pełne rozwiązanie eShopOnContainers z programu Visual Studio (uruchamia wszystkie usługi w plikach docker-compose) lub uruchom mikrousługę catalogu za pomocą następującego `docker-compose.yml` polecenia `docker-compose.override.yml` docker-compose w cmd lub powershell umieszczonyw folderze, w którym są umieszczone i są umieszczone.

```console
docker-compose run --service-ports catalog-api
```

To polecenie uruchamia tylko kontener usługi catalog-api plus zależności, które są określone w pliku docker-compose.yml. W takim przypadku kontener programu SQL Server i kontener RabbitMQ.

Następnie można bezpośrednio uzyskać dostęp do mikrousługi katalogu i zobaczyć jego metody za pośrednictwem interfejsu użytkownika Swagger dostęp bezpośrednio za pośrednictwem tego portu "zewnętrzne", w tym przypadku: `http://localhost:5101/swagger`

![Zrzut ekranu przedstawiający interfejs firmy Swagger przedstawiający interfejs API REST catalog.api.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

**Rysunek 6-31**. Testowanie mikrousługi katalogu za pomocą interfejsu interfejsu swagger

W tym momencie można ustawić punkt przerwania w kodzie Języka C# w programie Visual Studio, przetestować mikrousługi z `docker-compose down` metodami uwidocznionym w swagger interfejsu i wreszcie oczyścić wszystko za pomocą polecenia.

Jednak bezpośredni dostęp do mikrousługi, w tym przypadku za pośrednictwem portu zewnętrznego 5101, jest dokładnie to, czego chcesz uniknąć w aplikacji. I można tego uniknąć, ustawiając dodatkowy poziom pośredni bramy interfejsu API (Ocelot, w tym przypadku). W ten sposób aplikacja klienckinie nie będzie bezpośrednio uzyskać dostępu do mikrousługi.

## <a name="implementing-your-api-gateways-with-ocelot"></a>Implementowanie bram interfejsu API za pomocą ocelota

Ocelot to w zasadzie zestaw pośrednień, które można zastosować w określonej kolejności.

Ocelot jest przeznaczony do pracy tylko z ASP.NET Core. Najnowsza wersja pakietu `.NETCoreApp 3.1` dotyczy, a tym samym nie jest odpowiedni dla aplikacji .NET Framework.

Instalujesz Ocelot i jego zależności w projekcie ASP.NET Core z [pakietem NuGet Ocelota](https://www.nuget.org/packages/Ocelot/)z programu Visual Studio.

```powershell
Install-Package Ocelot
```

W eShopOnContainers jego implementacja bramy interfejsu API jest prostym ASP.NET core webhost projektu i pośredniczenie Ocelot obsługuje wszystkie funkcje bramy interfejsu API, jak pokazano na poniższej ilustracji:

![Zrzut ekranu przedstawiający Eksploratora rozwiązań z projektem bramy interfejsu API Ocelot.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

**Rysunek 6-32**. Projekt podstawowy OcelotApiGw w eShopOnContainers

Ten ASP.NET Core WebHost projekt jest w `Program.cs` zasadzie `Startup.cs`zbudowany z dwóch prostych plików: i .

Program.cs po prostu musi utworzyć i skonfigurować typowy ASP.NET Core BuildWebHost.

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

Ważnym punktem tutaj dla Ocelot jest `configuration.json` plik, który należy `AddJsonFile()` podać do konstruktora za pomocą metody. W `configuration.json` tym miejscu można określić wszystkie retrasy bramy interfejsu API, co oznacza zewnętrzne punkty końcowe z określonymi portami i skorelowanymi wewnętrznymi punktami końcowymi, zwykle przy użyciu różnych portów.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Istnieją dwie sekcje do konfiguracji. Tablica reroutes i GlobalConfiguration. ReRoutes są obiekty, które mówią Ocelot jak traktować żądanie nadrzędnego. Konfiguracja globalna umożliwia zastępowanie określonych ustawień reroute. Jest to przydatne, jeśli nie chcesz zarządzać wieloma ustawieniami określonymi w reroute.

Oto uproszczony przykład [pliku konfiguracyjnego ReRoute](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jednej z bram interfejsu API z eShopOnContainers.

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
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
          "Host": "basket-api",
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

Główną funkcjonalnością bramy interfejsu API Ocelot jest podjęcie przychodzących żądań HTTP i przekazywanie ich do usługi podrzędnej, obecnie jako inne żądanie HTTP. Ocelot opisuje routing jednego żądania do drugiego jako ReRoute.

Na przykład skupmy się na jednym z ReRoutes w configuration.json z góry, konfiguracji mikrousługi koszyka.

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

DownstreamPathTemplate, Scheme i DownstreamHostAndPorts tworzą wewnętrzny adres URL mikrousługi, do których zostanie przekazane to żądanie.

Port jest portem wewnętrznym używanym przez usługę. Podczas korzystania z kontenerów, port określony w jego dockerfile.

Jest `Host` to nazwa usługi, która zależy od rozpoznawania nazw usługi, których używasz. Podczas korzystania z docker-compose, nazwy usług są dostarczane przez Host platformy Docker, który używa nazw usług podanych w plikach docker-compose. Jeśli używasz koordynatora, takiego jak Kubernetes lub Sieć szkieletowa usług, ta nazwa powinna być rozpoznawana przez dns lub rozpoznawanie nazw dostarczone przez każdego koordynatora.

DownstreamHostAndPorts to tablica, która zawiera hosta i port wszelkich usług podrzędnych, do których chcesz przesyłać dalej żądania. Zazwyczaj będzie to tylko zawierać jeden wpis, ale czasami można załadować żądania równoważenia do usług niższego rzędu i Ocelot pozwala dodać więcej niż jeden wpis, a następnie wybrać moduł równoważenia obciążenia. Ale jeśli za pomocą platformy Azure i dowolnego koordynatora jest prawdopodobnie lepszym pomysłem, aby zrównoważyć obciążenia z chmury i infrastruktury koordynatora.

UpstreamPathTemplate jest adres URL, który Ocelot będzie używany do identyfikowania, które DownstreamPathTemplate do użycia dla danego żądania od klienta. Na koniec UpstreamHttpMetoda jest używana, więc Ocelot można odróżnić różne żądania (GET, POST, PUT) do tego samego adresu URL.

W tym momencie możesz mieć jedną bramę interfejsu API Ocelot (ASP.NET Core WebHost) przy użyciu jednego lub [wielu scalonych plików configuration.json](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) lub możesz również przechowywać [konfigurację w sklepie KV konsula](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).

Ale jak wprowadzono w architekturze i sekcji projektowania, jeśli naprawdę chcesz mieć autonomiczne mikrousług, może być lepiej podzielić tej pojedynczej bramy interfejsu API monolityczne do wielu bram interfejsu API i/lub BFF (backend dla frontonu). W tym celu zobaczmy, jak zaimplementować to podejście za pomocą kontenerów platformy Docker.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Używanie pojedynczego obrazu kontenera platformy Docker do uruchamiania wielu różnych typów kontenerów bramy interfejsu API / BFF

W eShopOnContainers używamy pojedynczego obrazu kontenera platformy Docker z bramą interfejsu API Ocelot, ale następnie w czasie wykonywania tworzymy różne usługi/kontenery dla każdego typu bramy interfejsu API/BFF, udostępniając inny plik configuration.json, używając woluminu docker, aby uzyskać dostęp do innego folderu komputera dla każdej usługi.

![Diagram pojedynczego obrazu platformy Docker bramy Ocelot dla wszystkich bram interfejsu API.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

**Rysunek 6-33**. Ponowne użycie pojedynczego obrazu platformy Docker ocelot dla wielu typów bramy interfejsu API

W eShopOnContainers "Generic Ocelot API Gateway Docker Image" jest tworzony z projektem o nazwie "OcelotApiGw" i nazwą obrazu "eshop/ocelotapigw", która jest określona w pliku docker-compose.yml. Następnie podczas wdrażania do platformy Docker, będą cztery kontenery bramy interfejsu API utworzone z tego samego obrazu platformy Docker, jak pokazano w poniższym wyjściu z pliku docker-compose.yml.

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

Ponadto, jak widać w następującym pliku docker-compose.override.yml, jedyną różnicą między tymi kontenerami bramy interfejsu API jest plik konfiguracyjny Ocelot, który jest inny dla każdego kontenera usługi i jest określony w czasie wykonywania za pośrednictwem Wolumin platformy Docker.

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

Ze względu na ten poprzedni kod i jak pokazano w Eksploratorze Visual Studio poniżej, jedynym plikiem potrzebnym do zdefiniowania każdej określonej bramy interfejsu API biznesowej/BFF jest tylko plik configuration.json, ponieważ cztery bramy interfejsu API są oparte na tym samym obrazie platformy Docker.

![Zrzut ekranu przedstawiający wszystkie bramy interfejsu API z plikami configuration.json.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

**Rysunek 6-34**. Jedynym plikiem potrzebnym do zdefiniowania każdej bramy API / BFF za pomocą Ocelota jest plik konfiguracyjny

Dzieląc bramę interfejsu API na wiele bram interfejsu API, różne zespoły programistyczne koncentrujące się na różnych podzbiorach mikrousług mogą zarządzać własnymi bramami interfejsu API przy użyciu niezależnych plików konfiguracyjnych Ocelot. Ponadto w tym samym czasie mogą ponownie użyć tego samego obrazu docker Ocelot.

Teraz, jeśli uruchomisz eShopOnContainers z bramami interfejsu API (zawarte domyślnie w VS podczas otwierania eShopOnContainers-ServicesAndWebApps.sln rozwiązanie lub jeśli używasz "docker-compose up"), następujące przykładowe trasy zostaną wykonane.

Na przykład podczas odwiedzania `http://localhost:5202/api/v1/c/catalog/items/2/` nadrzędnego adresu URL obsługiwanego przez webshoppingapigw API Gateway, `http://catalog-api/api/v1/2` otrzymasz ten sam wynik z wewnętrznego adresu URL downstream w hoście platformy Docker, jak w następującej przeglądarce.

![Zrzut ekranu przedstawiający przeglądarkę pokazującą odpowiedź przechodzącą przez bramę interfejsu API.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

**Rysunek 6-35**. Uzyskiwanie dostępu do mikrousługi za pośrednictwem adresu URL dostarczonego przez bramę interfejsu API

Ze względu na testowanie lub debugowanie jeśli chcesz uzyskać bezpośredni dostęp do kontenera docker wykazu (tylko w środowisku programistycznym) bez przechodzenia przez bramę interfejsu API, ponieważ "catalog-api" jest rozpoznawaniem DNS wewnętrznym hostem platformy Docker (odnajdywanie usług obsługiwane przez nazwy usług docker-compose), jedynym sposobem bezpośredniego dostępu do kontenera jest port zewnętrzny opublikowany w pliku docker-compose.override.yml, który jest dostępny tylko dla testów programistycznych, takich jak `http://localhost:5101/api/v1/Catalog/items/1` w następującej przeglądarce.

![Zrzut ekranu przedstawiający przeglądarkę z bezpośrednią odpowiedzią na interfejs Catalog.api.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

**Rysunek 6-36**. Bezpośredni dostęp do mikrousługi do celów testowych

Ale aplikacja jest skonfigurowana tak, aby uzyskać dostęp do wszystkich mikrousług za pośrednictwem bram interfejsu API, a nie przez port bezpośredni "skróty".

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>Wzorzec agregacji bramy w eShopOnContainers

Jak wprowadzono wcześniej elastyczny sposób implementowania agregacji żądań jest z usług niestandardowych, według kodu. Można również zaimplementować agregację żądań za pomocą [funkcji Agregacji żądań w Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale może nie być tak elastyczna, jak potrzebujesz. W związku z tym wybrany sposób implementacji agregacji w eShopOnContainers jest z jawną ASP.NET podstawową usługą interfejsu API sieci Web dla każdego agregatora.

Zgodnie z tym podejściem diagram kompozycji bramy interfejsu API jest w rzeczywistości nieco bardziej rozszerzony, gdy rozważa się usługi agregatora, które nie są wyświetlane na diagramie uproszczonej architektury globalnej pokazanego wcześniej.

Na poniższym diagramie można również zobaczyć, jak usługi agregatora działają z powiązanymi bramami interfejsu API.

![Diagram architektury eShopOnContainers przedstawiający usługi agregatora.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

**Rysunek 6-37**. Architektura eShopOnContainers z usługami agregatora

Powiększanie dalej w obszarze działalności "Zakupy" na poniższej ilustracji, można zobaczyć, że chattiness między aplikacjami klienckimi i mikrousług jest zmniejszona podczas korzystania z usług agregatora w bramach interfejsu API.

![Diagram przedstawiający architekturę eShopOnContainers powiększanie.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

**Rysunek 6-38**. Powiększanie wizji usług agregatora

Można zauważyć, jak, gdy diagram pokazuje możliwe żądania pochodzące z bram interfejsu API może uzyskać złożone. Chociaż można zobaczyć, jak strzałki na niebiesko zostaną uproszczone, z punktu widzenia aplikacji klienckich, podczas korzystania z wzorca agregatora poprzez zmniejszenie chattiness i opóźnienia w komunikacji, ostatecznie znacznie poprawiając środowisko użytkownika dla aplikacji zdalnych ( aplikacje mobilne i SPA), zwłaszcza.

W przypadku "Marketing" obszar działalności i mikrousług jest to prosty przypadek użycia, więc nie było potrzeby używania agregatorów, ale może być również możliwe, jeśli to konieczne.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Uwierzytelnianie i autoryzacja w bramkach interfejsu API Ocelot

W bramie interfejsu API Ocelot można siedzieć usługi uwierzytelniania, takich jak ASP.NET core usługi interfejsu API sieci Web przy użyciu [IdentityServer](https://identityserver.io/) dostarczanie tokenu uwierzytelniania, na zewnątrz lub wewnątrz bramy interfejsu API.

Ponieważ eShopOnContainers używa wielu bram interfejsu API z granicami opartymi na BFF i obszarach biznesowych, usługa Identity/Auth jest pomijana w bramkach interfejsu API, jak podkreślono na żółto na poniższym diagramie.

![Diagram przedstawiający mikrousługi tożsamości pod bramą interfejsu API.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

**Rysunek 6-39**. Stanowisko usługi Tożsamości w eShopOnContainers

Jednak Ocelot obsługuje również siedzi identity/Auth mikrousługi w granicach bramy interfejsu API, jak w tym innym diagramie.

![Diagram przedstawiający uwierzytelnianie w bramie interfejsu API Ocelot.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

**Rysunek 6-40**. Uwierzytelnianie w Ocelot

Jak pokazano na poprzednim diagramie, gdy mikrousługi tożsamości znajduje się pod bramą interfejsu API (AG): 1) AG żąda tokenu auth z mikrousługi tożsamości, 2) Mikrousługi tożsamości zwraca token ag, 3-4) żądania AG z mikrousług przy użyciu tokenu auth. Ponieważ aplikacja eShopOnContainers podzieliła bramę interfejsu API na wiele bff (backend for Frontend) i bramy interfejsu API obszarów biznesowych, inną opcją byłoby utworzenie dodatkowej bramy interfejsu API dla problemów przekrojowych. Ten wybór będzie sprawiedliwy w bardziej złożonej architekturze opartej na mikrousługach z wieloma przecięciami dotyczy mikrousług. Ponieważ istnieje tylko jeden problem przekrojowy w eShopOnContainers, zdecydowano się po prostu obsługiwać usługę zabezpieczeń z królestwa bramy interfejsu API, dla uproszczenia.

W każdym przypadku, jeśli aplikacja jest zabezpieczona na poziomie bramy interfejsu API, moduł uwierzytelniania bramy interfejsu API Ocelot jest odwiedzany na początku podczas próby użycia dowolnej zabezpieczonej mikrousługi. To przekierowuje żądanie HTTP do odwiedzenia tożsamości lub mikrousługi auth, aby uzyskać token dostępu, dzięki czemu można odwiedzić chronione usługi z access_token.

Sposób, w jaki można zabezpieczyć za pomocą uwierzytelniania dowolnej usługi na poziomie bramy interfejsu API jest ustawienie AuthenticationProviderKey w powiązanych ustawień w configuration.json.

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

Po uruchomieniu ocelot, będzie patrzeć na ReRoutes AuthenticationOptions.AuthenticationProviderKey i sprawdzić, czy istnieje dostawca uwierzytelniania zarejestrowany przy dany klucz. Jeśli nie, to Ocelot nie uruchomi się. Jeśli istnieje, a następnie ReRoute użyje tego dostawcy podczas wykonywania.

Ponieważ Ocelot WebHost jest skonfigurowany z `authenticationProviderKey = "IdentityApiKey"`, który będzie wymagał uwierzytelniania, gdy ta usługa ma żadnych żądań bez tokenu uwierzytelniania.

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

Następnie należy również ustawić autoryzację z [Authorize] atrybut dla dowolnego zasobu, który ma być dostępny, takich jak mikrousług, takich jak w następującym kontrolerze mikrousługi koszyka.

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

ValidAudiences takich jak "koszyk" są skorelowane z odbiorców `AddJwtBearer()` zdefiniowanych w każdej mikrousługi z w ConfigureServices() startup klasy, takich jak w poniższym kodzie.

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

Jeśli spróbujesz uzyskać dostęp do dowolnej zabezpieczonej mikrousługi, takiej jak mikrousługa Koszyka z adresem URL reroute opartym na bramie interfejsu API, takiej jak `http://localhost:5202/api/v1/b/basket/1`, otrzymasz 401 Unauthorized, chyba że podasz prawidłowy token. Z drugiej strony, jeśli adres URL ReRoute jest uwierzytelniony, Ocelot wywoła niezależnie od schematu podrzędnego jest skojarzony z nim (wewnętrzny adres URL mikrousługi).

**Autoryzacja w warstwie ReRoutes ocelota.**  Ocelot obsługuje autoryzację opartą na oświadczeniach ocenianą po uwierzytelnieniu. Autoryzację można ustawić na poziomie trasy, dodając następujące wiersze do konfiguracji ReRoute.

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

W tym przykładzie, gdy przywołuje się zagęszanie autoryzacji, Ocelot znajdzie, czy użytkownik ma typ oświadczenia "UserType" w tokenie i czy wartość tego oświadczenia jest "pracownik". Jeśli tak nie jest, użytkownik nie będzie autoryzowany, a odpowiedź będzie zabroniona 403.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Korzystanie z bram interfejsu API Kubernetes a także ocelot

Korzystając z programu Kubernetes (na przykład w klastrze usługi Azure Kubernetes), zwykle unieruchomić wszystkie żądania HTTP za pośrednictwem [warstwy Usługi Kubernetes Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) opartej na *nginx*.

W kubernetes, jeśli nie używasz żadnego podejścia przychodzących, a następnie usług i zasobników mają adresów IP tylko routingu przez sieć klastra.

Jeśli jednak używasz metody danych ruchomych, będziesz mieć warstwę środkową między Internetem a usługami (w tym bramami interfejsu API), działając jako zwrotny serwer proxy.

Jako definicja ingress jest zbiorem reguł, które umożliwiają połączenia przychodzące, aby dotrzeć do usług klastrowania. Ruch ingress jest zwykle skonfigurowany do świadczenia usług adresów URL dostępnych zewnętrznie, ruchu równoważenia obciążenia, zakończenia SSL i innych. Użytkownicy żądają wciągania przez posting zasobu usługi Ingress do serwera interfejsu API.

W eShopOnContainers podczas tworzenia lokalnie i przy użyciu tylko maszyny deweloperskiej jako hosta platformy Docker, nie używasz żadnych przychodzących, ale tylko wiele bram interfejsu API.

Jednak podczas określania wartości docelowej środowiska "produkcyjnego" opartego na programach Kubernetes eShopOnContainers używa usługi ingress przed bramami interfejsu API. W ten sposób klienci nadal wywołać ten sam podstawowy adres URL, ale żądania są kierowane do wielu bram interfejsu API lub BFF.

Bramy interfejsu API są frontonami lub fasadami, które napawają się tylko usługami, ale nie aplikacjami sieci web, które zwykle znajdują się poza ich zakresem. Ponadto bramy interfejsu API może ukryć niektórych mikrousług wewnętrznych.

Ruch wchodzący, jednak jest po prostu przekierowanie żądań HTTP, ale nie próbuje ukryć żadnych mikrousług lub aplikacji sieci web.

Posiadanie warstwy Nginx w kubernetes przed aplikacjami sieci web oraz kilka bram interfejsu API Ocelot / BFF jest idealną architekturą, jak pokazano na poniższym diagramie.

![Diagram przedstawiający, jak warstwa ruchu wingres pasuje do środowiska AKS.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

**Rysunek 6-41**. Warstwa ingress w eShopOnContainers po wdrożeniu w Kubernetes

A Kubernetes Ingress działa jako zwrotny serwer proxy dla całego ruchu do aplikacji, w tym aplikacji sieci web, które są zwykle poza zakresem bramy interfejsu Api. Podczas wdrażania eShopOnContainers w Kubernetes, udostępnia tylko kilka usług lub punktów końcowych za pośrednictwem _ingress_, w zasadzie poniższą listę postfixów na adresy URL:

- `/`dla aplikacji internetowej spa klienta
- `/webmvc`dla aplikacji internetowej klienta MVC
- `/webstatus`dla aplikacji sieci web klienta z wyświetlonymi kontrolami stanu/kondycji
- `/webshoppingapigw`dla internetowych BFF i procesów biznesowych na zakupy
- `/webmarketingapigw`dla internetowych BFF i marketingowych procesów biznesowych
- `/mobileshoppingapigw`dla mobilnych BFF i procesów biznesowych na zakupy
- `/mobilemarketingapigw`dla mobilnych BFF i procesów marketingowych

Podczas wdrażania w programie Kubernetes każda brama interfejsu API Ocelot używa innego pliku "configuration.json" dla każdego _zasobnika_ z uruchomionymi bramami interfejsu API. Te pliki "configuration.json" są dostarczane przez zamontowanie (pierwotnie ze skryptem deploy.ps1) woluminu utworzonego na podstawie _mapy konfiguracji_ Kubernetes o nazwie "ocelot". Każdy kontener montuje powiązany plik konfiguracyjny `/app/configuration`w folderze kontenera o nazwie .

W plikach kodu źródłowego eShopOnContainers oryginalne pliki "configuration.json" `k8s/ocelot/` można znaleźć w folderze. Dla każdego pliku BFF/APIGateway jest jeden plik.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Dodatkowe funkcje przekrojowe w bramie Interfejsu API Ocelot

Istnieją inne ważne funkcje do badania i używania, podczas korzystania z bramy interfejsu API Ocelot, opisane w poniższych łączach.

- **Odkrycie usługi po stronie klienta integrujące Ocelot z konsulem lub Eureką** \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **Buforowanie w warstwie bramy interfejsu API** \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **Rejestrowanie w warstwie Bramy interfejsu API** \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **Jakość usługi (ponownych prób i wyłączników) w warstwie Bramy interfejsu API** \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **Ograniczanie szybkości** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Poprzedni](background-tasks-with-ihostedservice.md)
> [następny](../microservice-ddd-cqrs-patterns/index.md)
