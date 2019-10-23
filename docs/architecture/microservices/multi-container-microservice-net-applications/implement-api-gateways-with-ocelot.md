---
title: Wdrażanie bram interfejsu API za pomocą rozwiązania Ocelot
description: Dowiedz się, jak zaimplementować bramy interfejsu API za pomocą Ocelot oraz jak używać Ocelot w środowisku opartym na kontenerach.
ms.date: 10/02/2018
ms.openlocfilehash: cb452c330712ecf536cdf09f41fdbf828a4e9314
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771185"
---
# <a name="implement-api-gateways-with-ocelot"></a>Implementowanie bram interfejsu API za pomocą Ocelot

Aplikacja mikrousługi referencyjnej [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) korzysta z [Ocelot](https://github.com/ThreeMammals/Ocelot), prostej i uproszczonej bramy interfejsu API, którą można wdrożyć w dowolnym miejscu wraz z mikrousługami/kontenerami, takimi jak w przypadku dowolnego z następujących środowisk używanych przez program eShopOnContainers.

- Host platformy Docker na lokalnym komputerze deweloperskim, lokalnie lub w chmurze.
- Klaster Kubernetes, lokalny lub w chmurze zarządzanej, taki jak usługa Azure Kubernetes Service (AKS).
- Service Fabric klastra, lokalnie lub w chmurze.
- Service Fabric mesh, jako niePaaSy/serwer na platformie Azure.

## <a name="architect-and-design-your-api-gateways"></a>Architekt i projektowanie bram interfejsu API

Na poniższym diagramie architektury pokazano, w jaki sposób bramy interfejsu API są implementowane za pomocą Ocelot w eShopOnContainers.

![diagram architektury eShopOnContainers pokazujący aplikacje klienckie, mikrousługi i bramy interfejsu API między](./media/image28.png)

**Rysunek 6-28**. Architektura eShopOnContainers z bramami interfejsu API

Ten diagram pokazuje, w jaki sposób cała aplikacja jest wdrażana na jednym hoście platformy Docker lub na komputerze deweloperskim z "Docker for Windows" lub "Docker for Mac". Jednak wdrażanie w dowolnym programie Orchestrator byłoby bardzo podobne, ale wszystkie kontenery na diagramie mogą być skalowane w programie Orchestrator.

Ponadto zasoby infrastruktury, takie jak bazy danych, pamięci podręcznej i brokerów komunikatów, powinny być oddzielone od programu Orchestrator i wdrożone w systemach o wysokiej dostępności na potrzeby infrastruktury, takich jak Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus lub dowolne rozwiązanie klastra HA w środowisku lokalnym.

Podobnie jak można zauważyć, że na diagramie istnieje kilka bram interfejsu API, dzięki czemu wiele zespołów programistycznych może być autonomiczne (w tym przypadku funkcje marketingu a funkcje zakupów) podczas opracowywania i wdrażania mikrousług oraz własnych powiązanych bram interfejsu API.

Jeśli masz pojedynczą, monolityczną bramę interfejsu API, która oznacza, że jeden punkt będzie aktualizowany przez kilka zespołów programistycznych, które mogą dołączać wszystkie mikrousługi do jednej części aplikacji.

Znacznie dokładniej w projekcie, czasem niekiedy Szczegółowa Brama interfejsu API może być również ograniczona do pojedynczej mikrousługi biznesowej, w zależności od wybranej architektury. Posiadanie granic bramy interfejsu API, które są określone przez firmę lub domenę, pomoże Ci uzyskać lepszy projekt.

Na przykład, szczegółowy stopień szczegółowości warstwy bramy API może być szczególnie przydatny w przypadku bardziej zaawansowanych aplikacji interfejsu użytkownika złożonego, które są oparte na mikrousługach, ponieważ pojęcie szczegółowej bramy interfejsu API jest podobne do usługi kompozycji interfejsu użytkownika.

W poprzedniej sekcji omówiono [Tworzenie złożonych interfejsów użytkownika opartych na mikrousługach](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).

Jako usługi Key wnioskiem, w przypadku wielu aplikacji średniej i o dużej wielkości, korzystanie z produktu bramy interfejsu API opracowanego przez użytkownika jest zwykle dobrym podejściem, ale nie jako jednym agregatorem monolitycznym lub unikatowym centralną bramą interfejsu API, chyba że brama interfejsu API zezwala na wiele niezależnych obszary konfiguracji dla kilku zespołów programistycznych tworzących autonomiczne mikrousługi.

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a>Przykładowe mikrousługi/kontenery do ponownej trasy przez bramy interfejsu API

Na przykład eShopOnContainers ma około sześć wewnętrznych typów mikrousług, które muszą być publikowane za pomocą bram interfejsu API, jak pokazano na poniższej ilustracji.

![Za pomocą bramy interfejsu API są publikowane tylko usługi koszyk, katalog, lokalizacja, Marketing, porządkowanie i płatności.](./media/image29.png)

**Rysunek 6-29**. Foldery mikrousług w rozwiązaniu eShopOnContainers w programie Visual Studio

Informacje o usłudze tożsamości — w projekcie, który jest pozostawiony do routingu bramy interfejsu API, ponieważ jest to jedyne zagadnienie związane z wycinaniem w systemie, chociaż z Ocelot jest również możliwe dołączenie go jako części list reroutingu.

Wszystkie te usługi są obecnie implementowane jako ASP.NET Core usług interfejsu API sieci Web, co umożliwia poinformowanie o kodzie. Skupmy się na jednym z mikrousług, takimi jak kod mikrousług katalogu.

![Widok Eksploratora rozwiązań w projekcie katalogu. API.](./media/image30.png)

**Rysunek 6-30**. Przykładowa usługa interfejsu API sieci Web (mikrousługa katalogu)

Można sprawdzić, czy katalog jest typowym ASP.NET Core projektem interfejsu API sieci Web z kilkoma kontrolerami i metodami, takimi jak w poniższym kodzie.

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

Żądanie HTTP spowoduje zakończenie działania tego rodzaju C# kodu, który uzyskuje dostęp do bazy danych mikrousług i wszelkie dodatkowe wymagane akcje.

W przypadku adresu URL mikrousług, gdy kontenery są wdrażane na lokalnym komputerze deweloperskim (lokalny Host platformy Docker), każdy kontener mikrousług ma zawsze port wewnętrzny (zazwyczaj port 80) określony w pliku dockerfile, jak w poniższym pliku dockerfile:

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

Port 80 wyświetlany w kodzie jest wewnętrzny w ramach hosta platformy Docker, więc nie można go połączyć z aplikacjami klienckimi.

Aplikacje klienckie mogą uzyskiwać dostęp tylko do portów zewnętrznych (jeśli istnieją) opublikowanych podczas wdrażania przy użyciu `docker-compose`.

Tych portów zewnętrznych nie należy publikować podczas wdrażania w środowisku produkcyjnym. Jest to dokładnie dlatego, że chcesz użyć bramy interfejsu API, aby uniknąć bezpośredniej komunikacji między aplikacjami klienckimi i mikrousługami.

Jednak podczas tworzenia programu chcesz bezpośrednio uzyskać dostęp do mikrousługi/kontenera i uruchomić go za pomocą struktury Swagger. Dlatego w eShopOnContainers, porty zewnętrzne są nadal określone nawet wtedy, gdy nie będą używane przez bramę interfejsu API ani aplikacje klienckie.

Oto przykład pliku `docker-compose.override.yml` dla mikrousługi katalogu:

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

Można zobaczyć, jak w konfiguracji Docker-Compose. override. yml port wewnętrzny dla kontenera wykazu jest portem 80, ale Port dostępu zewnętrznego to 5101. Jednak ten port nie powinien być używany przez aplikację podczas korzystania z bramy interfejsu API, tylko do debugowania, uruchamiania i testowania tylko mikrousługi katalogu.

Zwykle nie jest wdrażana przy użyciu platformy Docker — tworzenie w środowisku produkcyjnym, ponieważ odpowiednie środowisko wdrażania w środowisku produkcyjnym dla mikrousług jest koordynatorem, takim jak Kubernetes lub Service Fabric. W przypadku wdrażania w środowiskach korzystających z różnych plików konfiguracji, w których nie można publikować bezpośrednio żadnych portów zewnętrznych dla mikrousług, ale zawsze będziesz używać zwrotnego serwera proxy z bramy interfejsu API.

Uruchom mikrousługę katalogu na lokalnym hoście platformy Docker, uruchamiając pełne rozwiązanie eShopOnContainers z programu Visual Studio (uruchamia wszystkie usługi w plikach do redagowania w systemie Docker) lub po prostu uruchamiając mikrousługę w katalogu przy użyciu poniższego narzędzia Docker-Zredaguj polecenie w CMD lub PowerShell jest umieszczone w folderze, w którym umieszczane są `docker-compose.yml` i Docker-Compose. override. yml.

```console
docker-compose run --service-ports catalog.api
```

To polecenie uruchamia tylko wykaz. kontener usługi API i zależności, które są określone w Docker-Compose. yml. W tym przypadku kontener SQL Server i kontener RabbitMQ.

Następnie można bezpośrednio uzyskać dostęp do mikrousługi katalogu i wyświetlić jej metody za pomocą interfejsu użytkownika programu Swagger, uzyskując dostęp bezpośrednio przez ten port "zewnętrzny", w tym przypadku `http://localhost:5101/swagger`:

![Widok wieku interfejsu użytkownika struktury Swagger dla interfejsu API REST katalogu. API.](./media/image31.png)

**Rysunek 6-31**. Testowanie mikrousługi katalogu za pomocą interfejsu użytkownika struktury Swagger

W tym momencie można ustawić punkt przerwania w C# kodzie w programie Visual Studio, przetestować mikrousługę przy użyciu metod udostępnianych w interfejsie użytkownika struktury Swagger, a wreszcie wyczyścić wszystkie elementy przy użyciu polecenia `docker-compose down`.

Jednak bezpośredni dostęp do mikrousługi, w tym przypadku przez port zewnętrzny 5101, jest dokładnie to, co chcesz uniknąć w aplikacji. Można uniknąć tego przez ustawienie dodatkowego poziomu pośredniego dla bramy interfejsu API (w tym przypadku Ocelot). Dzięki temu aplikacja kliencka nie będzie bezpośrednio uzyskiwać dostępu do mikrousługi.

## <a name="implementing-your-api-gateways-with-ocelot"></a>Implementowanie bram interfejsu API za pomocą usługi Ocelot

Ocelot jest zasadniczo zestawem middlewares, który można zastosować w określonej kolejności.

Ocelot jest przeznaczona do pracy tylko z ASP.NET Core. Jest on przeznaczony dla programu .NET Standard 2.0, dzięki czemu można go używać wszędzie .NET Standard 2,0 jest obsługiwane, w tym środowisko uruchomieniowe .NET Core 2,0 i środowisko uruchomieniowe i .NET Framework 4.6.1.

Program Visual Studio umożliwia zainstalowanie Ocelot i jego zależności w projekcie ASP.NET Core z [pakietem NuGet Ocelot](https://www.nuget.org/packages/Ocelot/).

```powershell
Install-Package Ocelot
```

W eShopOnContainers, jej implementacja bramy interfejsu API to ASP.NET Core prosty projekt usługi WebHost, a middlewares Ocelot obsługują wszystkie funkcje bramy interfejsu API, jak pokazano na poniższej ilustracji:

![Widok Eksplorator rozwiązań projektu bramy interfejsu API Ocelot.](./media/image32.png)

**Rysunek 6-32**. Projekt podstawowy OcelotApiGw w eShopOnContainers

Ten ASP.NET Core Project WebHost jest w zasadzie zbudowany przy użyciu dwóch prostych plików: `Program.cs` i `Startup.cs`.

Program.cs musi utworzyć i skonfigurować typowe ASP.NET Core BuildWebHost.

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

Ważną kwestią dla Ocelot jest plik `configuration.json`, który należy dostarczyć konstruktorowi za pomocą metody `AddJsonFile()`. @No__t_0 to miejsce, w którym należy określić wszystkie przekierowania bramy interfejsu API, co oznacza, że zewnętrzne punkty końcowe z określonymi portami i skorelowane wewnętrzne punkty końcowe zwykle korzystają z różnych portów.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Do konfiguracji należą dwie sekcje. Tablica ponownych tras i GlobalConfiguration. Ponowne trasy są obiektami, które informują Ocelot o sposobie traktowania żądania nadrzędnego. Konfiguracja globalna umożliwia zastępowanie konkretnych ustawień. Jest to przydatne, jeśli nie chcesz zarządzać wieloma zmianami poszczególnych ustawień.

Poniżej przedstawiono uproszczony przykład [retrasy pliku konfiguracji](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jednej z bram interfejsu API z eShopOnContainers.

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

Główną funkcją bramy interfejsu API Ocelot jest przejęcie przychodzących żądań HTTP i przekazanie ich do usługi podrzędnej, obecnie jako innego żądania HTTP. Ocelot opisuje Routing jednego żądania do innego w ramach ponownej trasy.

Na przykład skupmy się na jednej z ponownych tras w pliku Configuration. JSON z powyższych, konfiguracji mikrousługi koszyka.

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

DownstreamPathTemplate, schemat i DownstreamHostAndPorts tworzą wewnętrzny adres URL mikrousług, do którego zostanie przesłane żądanie.

Port jest portem wewnętrznym używanym przez usługę. W przypadku korzystania z kontenerów port określony w pliku dockerfile.

@No__t_0 to nazwa usługi, która zależy od używanego rozwiązania nazwy usługi. W przypadku korzystania z platformy Docker — Tworzenie nazw usług są udostępniane przez hosta platformy Docker, który korzysta z nazw usług udostępnianych w plikach tworzenia platformy Docker. W przypadku korzystania z programu Orchestrator, takiego jak Kubernetes lub Service Fabric, ta nazwa powinna być rozpoznawana przez system DNS lub rozpoznawanie nazw dostarczone przez każdego koordynatora.

DownstreamHostAndPorts to tablica zawierająca hosta i port wszystkich usług podrzędnych, do których mają być przekazywane żądania. Zwykle zawiera on tylko jeden wpis, ale czasami może zajść potrzeba zrównoważenia obciążenia żądaniami do usług podrzędnych i Ocelot umożliwia dodanie więcej niż jednego wpisu, a następnie wybranie modułu równoważenia obciążenia. Ale jeśli korzystasz z platformy Azure i dowolnego programu Orchestrator, prawdopodobnie lepszym rozwiązaniem jest zrównoważenie równoważenia obciążenia za pomocą infrastruktury chmury i programu Orchestrator.

UpstreamPathTemplate to adres URL, który będzie używany przez Ocelot do identyfikowania DownstreamPathTemplate do użycia dla danego żądania od klienta. Na koniec UpstreamHttpMethod jest używany, więc Ocelot może rozróżnić różne żądania (GET, POST, PUT) na ten sam adres URL.

W tym momencie można mieć jedną bramę interfejsu API Ocelot (ASP.NET Core WebHost) przy użyciu jednego lub [wielu scalonych plików Configuration. JSON](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) lub można ją również zapisać [w magazynie Consul KV](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).

Jeśli jednak na pewno chcesz mieć autonomiczne mikrousługi, jak zostało to opisane w sekcji architektura i projekt, lepiej jest podzielić tę jednolite bramy interfejsu API na wiele bram interfejsu API i/lub BFF (zaplecza dla frontonu). W tym celu Zobaczmy, jak zaimplementować to podejście przy użyciu kontenerów platformy Docker.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Używanie pojedynczego obrazu kontenera Docker do uruchamiania wielu różnych typów kontenerów bramy interfejsu API/BFF

W eShopOnContainers korzystamy z jednego obrazu kontenera Docker z bramą interfejsu API Ocelot, a następnie w czasie wykonywania tworzymy różne usługi/kontenery dla każdego typu interfejsu API-Gateway/BFF, dostarczając inny plik Configuration. JSON przy użyciu woluminu Docker do Uzyskaj dostęp do innego folderu komputera dla każdej usługi.

![Pojedynczy obraz platformy Docker dla bramy interfejsu API Ocelot jest używany dla wszystkich czterech bram interfejsu API](./media/image33.png)

**Rysunek 6-33**. Ponowne używanie pojedynczego obrazu platformy Docker Ocelot w wielu typach bram interfejsu API

W eShopOnContainers "ogólny obraz bramy interfejsu API Docker" jest tworzony przy użyciu projektu o nazwie "OcelotApiGw" i nazwy obrazu "eshop/OcelotApiGw", która jest określona w pliku Docker-Compose. yml. Po wdrożeniu do platformy Docker dostępne są cztery kontenery usługi API-Gateway utworzone na podstawie tego samego obrazu platformy Docker, jak pokazano w poniższym wyodrębnieniu z pliku Docker-Compose. yml.

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

Ponadto, jak widać w poniższym pliku Docker-Compose. override. yml, jedyną różnicą między tymi kontenerami interfejsu API jest plik konfiguracji Ocelot, który jest inny dla każdego kontenera usługi i został określony w czasie wykonywania za pomocą Wolumin platformy Docker.

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

Ze względu na ten poprzedni kod, jak pokazano w Eksploratorze programu Visual Studio, jedynym plikiem potrzebnym do zdefiniowania każdej konkretnej bramy interfejsu API Business/BFF jest tylko plik Configuration. JSON, ponieważ cztery bramy interfejsu API są oparte na tym samym obrazie platformy Docker.

![Jedyną różnicą między wszystkimi bramami interfejsu API jest plik Configuration. JSON na każdym z nich.](./media/image34.png)

**Rysunek 6-34**. Jedynym plikiem wymaganym do zdefiniowania każdej usługi API Gateway/BFF z Ocelot jest plik konfiguracji

Dzieląc bramę interfejsu API na wiele bram interfejsu API, różne zespoły programistyczne skupiające się na różnych podzestawach mikrousług mogą zarządzać własnymi bramami interfejsu API za pomocą niezależnych plików konfiguracji Ocelot. Dodatkowo, w tym samym czasie mogą ponownie użyć tego samego obrazu platformy Docker Ocelot.

Teraz, jeśli uruchomisz eShopOnContainers z bramami interfejsu API (zawartymi domyślnie w programie VS podczas otwierania rozwiązania eShopOnContainers-ServicesAndWebApps. sln lub w przypadku uruchamiania funkcji "Docker-Zredaguj up"), zostaną wykonane następujące przykładowe trasy.

Na przykład podczas odwiedzania adresu URL nadrzędnego `http://localhost:5202/api/v1/c/catalog/items/2/` obsługiwanego przez bramę interfejsu API webshoppingapigw można uzyskać ten sam wynik z wewnętrznego podrzędnego adresu URL `http://catalog.api/api/v1/2` na hoście platformy Docker, jak w poniższej przeglądarce.

![Widok przeglądarki odpowiedzi z katalogu. interfejs API przechodzenia przez bramę interfejsu API.](./media/image35.png)

**Rysunek 6-35**. Uzyskiwanie dostępu do mikrousługi za pomocą adresu URL dostarczonego przez bramę interfejsu API

Ze względu na testowanie lub debugowanie, jeśli chcesz uzyskać bezpośredni dostęp do kontenera Docker katalogu (tylko w środowisku programistycznym) bez przechodzenia przez bramę interfejsu API, ponieważ "katalog. API" jest wewnętrznym rozpoznawaniem nazw DNS dla hosta platformy Docker (usługa Odnajdywanie obsługiwane przez usługi platformy Docker — Tworzenie nazw usług — jedynym sposobem bezpośredniego dostępu do kontenera jest użycie portu zewnętrznego opublikowanego w Docker-Compose. override. yml, który jest dostępny tylko dla testów programistycznych, takich jak `http://localhost:5101/api/v1/Catalog/items/1` w poniższej przeglądarce.

![Widok przeglądarki odpowiedzi z katalogu. interfejs API przechodzi bezpośrednio do katalogu Catalog. API, identyczne z tym, za pośrednictwem bramy interfejsu API.](./media/image36.png)

**Rysunek 6-36**. Bezpośredni dostęp do mikrousługi na potrzeby testowania

Jednak aplikacja jest skonfigurowana, aby uzyskiwać dostęp do wszystkich mikrousług za pośrednictwem bram interfejsu API, a nie za pomocą portu bezpośredniego "skróty".

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>Wzorzec agregacji bramy w eShopOnContainers

Jak wprowadzono wcześniej, elastyczny sposób implementacji agregacji żądań jest z usługami niestandardowymi, przez kod. Można również zaimplementować agregację żądań za pomocą [funkcji agregacji żądań w Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale może to być niepotrzebne. W związku z tym wybrany sposób implementacji agregacji w eShopOnContainers jest z jawną ASP.NET Core usługami interfejsu API sieci Web dla każdego agregatora.

Zgodnie z tym podejściem diagram kompozycji bramy interfejsu API jest w rzeczywistości bardziej rozszerzony podczas rozważania usług agregatora, które nie są wyświetlane w uproszczonym, globalnym diagramie architektury.

Na poniższym diagramie można także zobaczyć, jak usługi agregatora współpracują z odpowiednimi bramami interfejsu API.

![Architektura eShopOnContainers, pokazująca usługi agregatora.](./media/image37.png)

**Rysunek 6-37**. Architektura eShopOnContainers z usługami agregatora

Dalsze powiększanie, w obszarze roboczym "zakupy" na poniższej ilustracji widać, że chattiness między aplikacjami klienckimi i mikrousługami zostanie zredukowany w przypadku korzystania z usług agregatora w bramach interfejsu API.

![Powiększ architekturę eShopOnContainers, pokazując usługi agregatora, które "" łączy "odpowiedź z kilku mikrousług, aby zredukować chattiness z klientem końcowym.](./media/image38.png)

**Rysunek 6-38**. Powiększ zalety usług agregatora

Można zauważyć, jak gdy diagram pokazuje możliwe żądania pochodzące z bram interfejsu API, które mogą być dość skomplikowane. Mimo że można zobaczyć, jak strzałki w kolorze niebieskim byłyby uproszczone, z perspektywy aplikacji klienckich przy użyciu wzorca agregatora poprzez zmniejszenie chattiness i opóźnień komunikacji, ostatecznie znacząco ulepszanie środowiska użytkownika dla aplikacji zdalnych ( aplikacje mobilne i SPA), szczególnie.

W przypadku obszaru biznesowego "Marketing" i mikrousług jest to bardzo proste przypadek użycia, dlatego nie ma potrzeby korzystania z agregatorów, ale może również być możliwe, jeśli jest to konieczne.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Uwierzytelnianie i autoryzacja w bramach interfejsu API Ocelot

W bramie interfejsu API Ocelot można korzystać z usługi uwierzytelniania, takiej jak usługa interfejsu API sieci Web ASP.NET Core przy użyciu [IdentityServer](https://identityserver.io/) , dostarczając token uwierzytelniania lub wewnątrz bramy interfejsu API.

Ponieważ eShopOnContainers korzysta z wielu bram interfejsu API z granicami opartymi na obszarach BFF i firmowych, Usługa tożsamość/uwierzytelnianie pozostaje poza bramami interfejsu API, jak zostało to wyróżnione na żółto na poniższym diagramie.

![diagram architektury eShopOnContainers pokazujący mikrousługę tożsamości poniżej bramy interfejsu API.](./media/image39.png)

**Rysunek 6-39**. Pozycja usługi tożsamości w eShopOnContainers

Jednak Ocelot obsługuje także rolę mikrousługi tożsamości/uwierzytelniania w ramach granicy bramy interfejsu API, tak jak w przypadku tego innego diagramu.

![Uwierzytelnianie przy użyciu mikrousługi tożsamości pod węzłem API Gateway (AG): 1) AG żąda tokenu uwierzytelniania od mikrousługi tożsamości, 2) usługa tożsamości zwraca Toke do AG, 3-4), a następnie przesyła żądania od mikrousług przy użyciu tokenu uwierzytelniania.](./media/image40.png)

**Rysunek 6-40**. Uwierzytelnianie w Ocelot

Ze względu na to, że aplikacja eShopOnContainers podzieliła bramę interfejsu API na wiele BFF (zaplecza dla frontonu) i firmowych bram interfejsu API, kolejną opcją jest utworzenie dodatkowej bramy interfejsu API dla zagadnień związanych z wycinaniem. Wybór ten byłby atrakcyjny w bardziej złożonej architekturze opartej na mikrousługach z wieloma usługami. Ponieważ w eShopOnContainers występuje tylko jeden problem z wycinaniem, to zdecydowano o prostu obsłużyć usługę zabezpieczeń z obszaru bramy interfejsu API w celu uproszczenia.

W każdym przypadku, jeśli aplikacja jest zabezpieczona na poziomie bramy interfejsu API, moduł uwierzytelniania bramy interfejsu API Ocelot jest najpierw odwiedzany przy próbie użycia dowolnej zabezpieczonej mikrousługi. Spowoduje to ponowne skierowanie żądania HTTP do odwiedzania tożsamości lub mikrousługi uwierzytelniania w celu uzyskania tokenu dostępu, aby można było odwiedzić chronione usługi za pomocą access_token.

Sposób zabezpieczania przy użyciu uwierzytelniania każdej usługi na poziomie bramy interfejsu API polega na ustawieniu AuthenticationProviderKey w ustawieniach pokrewnych w pliku Configuration. JSON.

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

Po uruchomieniu Ocelot zostanie wyświetlona ponowna trasa AuthenticationOptions. AuthenticationProviderKey i sprawdź, czy istnieje dostawca uwierzytelniania zarejestrowany dla danego klucza. Jeśli nie, to Ocelot nie zostanie uruchomiony. Jeśli istnieje, wówczas retrasa użyje tego dostawcy, gdy zostanie on wykonany.

Ponieważ Ocelot WebHost jest skonfigurowany przy użyciu `authenticationProviderKey = "IdentityApiKey"`, które będą wymagały uwierzytelniania zawsze, gdy ta usługa ma jakiekolwiek żądania bez tokenu uwierzytelniania.

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

Następnie należy ustawić autoryzację z atrybutem [autoryzuje] dla dowolnego zasobu, aby uzyskać do niego dostęp, taki jak mikrousługi, na przykład w następującym kontrolerze mikrousług koszyka.

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

ValidAudiences, takie jak "koszyk", są skorelowane z odbiorcami zdefiniowanymi w każdej mikrousłudze za pomocą `AddJwtBearer()` w ConfigureServices () klasy startowej, na przykład w poniższym kodzie.

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

Jeśli spróbujesz uzyskać dostęp do dowolnej zabezpieczonej mikrousługi, na przykład mikrousługi koszyka z adresem URL ponownej trasy na podstawie bramy interfejsu API, takiej jak `http://localhost:5202/api/v1/b/basket/1`, otrzymasz 401 autoryzacji, chyba że podasz prawidłowy token. Z drugiej strony, jeśli adres URL ponownej trasy zostanie uwierzytelniony, Ocelot wywoła każdy schemat podrzędny jest skojarzony z nim (wewnętrzny adres URL mikrousługi).

**Autoryzacja w warstwie reroutes w usłudze Ocelot.**  Ocelot obsługuje autoryzację opartą na oświadczeniach, która jest obliczana po uwierzytelnieniu. Autoryzację można ustawić na poziomie trasy, dodając następujące wiersze do konfiguracji Reroute.

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

W tym przykładzie, gdy zostanie wywołane oprogramowanie pośredniczące autoryzacji, Ocelot będzie wiedzieć, czy użytkownik ma typ "UserType" w tokenie i czy wartość tego żądania to "Employee". Jeśli tak nie jest, użytkownik nie będzie autoryzowany, a odpowiedź 403 będzie niedostępna.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Korzystanie z bram interfejsu API Kubernetes i Ocelot

W przypadku korzystania z Kubernetes (podobnie jak w przypadku klastra usługi Azure Kubernetes) zazwyczaj wszystkie żądania HTTP są tworzone za pośrednictwem [warstwy danych wejściowych Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) na podstawie *Nginx*.

W Kubernetes, jeśli nie korzystasz z metody transferu danych przychodzących, usługi i mają tylko adresy IP do routingu przez sieć klastra.

Jeśli jednak korzystasz z metody transferu danych przychodzących, będziesz mieć warstwę środkową między Internetem a usługami (w tym bramami interfejsu API) działającą jako zwrotny serwer proxy.

Jako definicja, ruch przychodzący jest kolekcją reguł, które zezwalają na połączenia przychodzące do usług klastra. Ruch przychodzący jest zwykle konfigurowany pod kątem zapewniania usług adresów URL, które są dostępne z zewnątrz, równoważenia obciążenia, zakończenia protokołu SSL i nie tylko. Użytkownicy żądają transferu danych przychodzących, publikując zasób transferu danych przychodzących na serwerze interfejsu API.

W eShopOnContainers, podczas tworzenia lokalnie i korzystania tylko z komputera deweloperskiego jako hosta platformy Docker, nie są używane żadne przychodzące, ale tylko bramy interfejsu API.

Jednak w przypadku określania środowiska "produkcyjnego" w oparciu o Kubernetes, eShopOnContainers korzysta z ruchu przychodzącego przed bramami interfejsu API. Dzięki temu klienci nadal będą wywoływać ten sam podstawowy adres URL, ale żądania są kierowane do wielu bram interfejsu API lub BFF.

Należy pamiętać, że bramy interfejsu API są frontony lub fasady są podkreślać tylko te usługi, ale nie aplikacje sieci Web, które zwykle znajdują się poza zakresem. Ponadto bramy interfejsu API mogą ukrywać niektóre mikrousługi wewnętrzne.

Ruch przychodzący polega jednak jedynie na przekierowaniu żądań HTTP, ale nie próbie ukrycia żadnej mikrousługi lub aplikacji sieci Web.

Posiadanie warstwy Nginx w Kubernetes przed aplikacjami sieci Web, a kilka bram interfejsu API Ocelot/BFF jest idealną architekturą, jak pokazano na poniższym diagramie.

![Ruch przychodzący Kubernetes działa jako zwrotny serwer proxy dla całego ruchu do aplikacji, w tym aplikacji sieci Web, które zwykle znajdują się poza zakresem bramy interfejsu API.](./media/image41.png)

**Rysunek 6-41**. Warstwa transferu danych przychodzących w eShopOnContainers po wdrożeniu w Kubernetes

Gdy wdrażasz eShopOnContainers w usłudze _Kubernetes,_ uwidaczniamy tylko kilka usług lub punktów końcowych za pośrednictwem transferu danych przychodzących, zasadniczo Poniższa lista przyrostów adresów URL:

- `/` aplikacji sieci Web SPA klienta
- `/webmvc` aplikacji sieci Web Client MVC
- `/webstatus` aplikacji sieci Web klienta pokazującej stan/healthchecks
- `/webshoppingapigw` dla procesów roboczych BFF i zakupów w sieci Web
- `/webmarketingapigw` dla procesów biznesowych BFF i marketingowych
- `/mobileshoppingapigw` dla procesów roboczych BFF i zakupów mobilnych
- `/mobilemarketingapigw` dla procesów biznesowych Mobile BFF i marketingowych

Podczas wdrażania programu do Kubernetes każda Brama interfejsu API Ocelot korzysta z innego pliku "Configuration. JSON" dla każdego _z nich,_ na którym działają bramy interfejsu API. Pliki "Configuration. JSON" są udostępniane przez zainstalowanie (początkowo ze skryptem Deploy. ps1) wolumin utworzony w oparciu o _mapę konfiguracji_ Kubernetes o nazwie "Ocelot". Każdy kontener instaluje związany z nim plik konfiguracji w folderze kontenera o nazwie `/app/configuration`.

W pliku z kodem źródłowym eShopOnContainers oryginalny plik "Configuration. JSON" można znaleźć w folderze `k8s/ocelot/`. Dla każdego BFF/APIGateway istnieje jeden plik.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Dodatkowe funkcje wycinania krzyżowego w bramie interfejsu API Ocelot

W przypadku korzystania z bramy interfejsu API Ocelot, która została opisana w poniższych linkach, istnieją inne ważne funkcje do badania i używania.

- **Odnajdowanie usług po stronie klienta integrując Ocelot z Consul lub Eureka**  \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **Buforowanie w warstwie bramy interfejsu API**  \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **Rejestrowanie w warstwie bramy interfejsu API**  \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **Quality of Service (ponownych prób i wyłączników) w warstwie bramy interfejsu API**  \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **Ograniczanie szybkości**  \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Poprzedni](background-tasks-with-ihostedservice.md)
> [Następny](../microservice-ddd-cqrs-patterns/index.md)
