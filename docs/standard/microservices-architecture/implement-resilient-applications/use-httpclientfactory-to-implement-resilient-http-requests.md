---
title: Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP
description: Dowiedz się, jak używać HttpClientFactory dostępne od platformy .NET Core 2.1, do tworzenia `HttpClient` wystąpień, dzięki czemu można korzystać w aplikacjach.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: a55181e787b5c94e13d3945a5d97a12fed61e927
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020221"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP

`HttpClientFactory` to ceniona fabryki, dostępne od platformy .NET Core 2.1, do tworzenia <xref:System.Net.Http.HttpClient> wystąpienia ma być używany w aplikacjach.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemy związane z oryginalnej klasy HttpClient dostępnych w programie .NET Core

Oryginalne i dobrze znane [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) klasy mogą być łatwo używane, ale w niektórych przypadkach nie jest prawidłowo używane przez wielu deweloperów. 

Jako pierwszego wydania tej klasy jest możliwe do rozporządzania, korzystania z niego przy użyciu `using` instrukcja nie jest najlepszym rozwiązaniem, ponieważ nawet wtedy, gdy użytkownik dispose `HttpClient` obiektu bazowego gniazda nie jest od razu zwolniony i może spowodować poważne zagrożenie o nazwie "gniazda wyczerpanie ". Aby uzyskać więcej informacji na temat tego problemu, zobacz [używasz problem HttpClient i jest on destabilizing oprogramowania](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) wpis w blogu.

W związku z tym `HttpClient` jest przeznaczony do jednorazowego utworzenia ich i ponownie używane w całym cyklu życia aplikacji. Utworzenie wystąpienia `HttpClient` klasy dla każdego żądania będą wyczerpać liczbę gniazd, które są dostępne pod dużym obciążeniem. Czy problem spowoduje `SocketException` błędy. Możliwe sposoby rozwiązania tego problemu są oparte na tworzeniu `HttpClient` obiektu jako pojedyncze lub statyczna, zgodnie z opisem w tym [artykule firmy Microsoft dotyczących użycia HttpClient](/dotnet/csharp/tutorials/console-webapiclient). 

Ale drugi problem ze `HttpClient` , może mieć w przypadku użycia jej jako pojedyncze lub obiektu statycznego. W tej sprawy, pojedyncze lub statyczna `HttpClient` zmian systemu DNS nie jest zgodny z zgodnie z opisem w tym [problemu w repozytorium .NET Core w usłudze GitHub](https://github.com/dotnet/corefx/issues/11224). 

Do rozwiązania tych problemów wymienionych i zarządzania `HttpClient` przypadkach łatwiejsze platformy .NET Core 2.1 wprowadzono nową `HttpClientFactory` , można również zaimplementować odporne na błędy połączeń HTTP, integrując Polly z nim.   

## <a name="what-is-httpclientfactory"></a>Co to jest HttpClientFactory

`HttpClientFactory` została zaprojektowana w celu:

- Podaj centralną lokalizację do nazywania i konfigurowanie HttpClients logiczne. Na przykład może skonfigurować klienta (usługi agenta), który jest wstępnie skonfigurowana do dostępu do określonych mikrousług.
- Skodyfikowanie koncepcji wychodzących oprogramowania pośredniczącego za pośrednictwem Delegowanie obsługi w `HttpClient` i wdrażanie na podstawie Polly oprogramowaniu pośredniczącym, aby korzystać z zasad firmy Polly pod kątem odporności.
- Klasa `HttpClient` ma już pojęcie delegowania programów obsługi, które można połączyć ze sobą dla wychodzących żądań HTTP. Rejestrowanie klientów http do fabryki, a także można użyć procedury obsługi Polly, umożliwiająca Polly zasady służący do ponawiania, CircuitBreakers itp.
- Zarządzanie okresem istnienia HttpClientMessageHandlers, aby uniknąć wymienionych problemów/problemy, które mogą wystąpić podczas zarządzania `HttpClient` okresy istnienia samodzielnie. 

## <a name="multiple-ways-to-use-httpclientfactory"></a>Wiele sposobów, aby użyć HttpClientFactory

Istnieje kilka metod, których można użyć `HttpClientFactory` w Twojej aplikacji:

- Użyj `HttpClientFactory` bezpośrednio
- Użyj o nazwie klientów
- Korzystać z kontrolą typów klientów
- Użyj wygenerowanych klientów

W celu skrócenia wskazówki te przedstawiają najbardziej ze strukturą sposób używania `HttpClientFactory` to korzystać z kontrolą typów klientów (Agent usługi wzorzec), ale wszystkie opcje są udokumentowane i obecnie są wymienione w tym [artykułu obejmujących użycie HttpClientFactory ](/aspnet/core/fundamentals/http-requests?#consumption-patterns).  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Jak używać wpisane klientów z HttpClientFactory

Tak co to jest "klient z typowaniem"? Jest po prostu `HttpClient` skonfigurowanego na iniekcji przez `DefaultHttpClientFactory`.

Na poniższym diagramie przedstawiono, jak wpisane klientów są używane z `HttpClientFactory`:

![ClientService (używane przez kod kontrolera lub klienta) używa HttpClient utworzone przez IHttpClientFactory zarejestrowane. Ta fabryka przypisuje HttpClient klasa HttpMessageHandler z puli, którymi zarządza. Podczas rejestrowania IHttpClientFactory w kontenerze DI w metodzie rozszerzenia AddHttpClient HttpClient można skonfigurować przy użyciu zasad firmy Polly.](./media/image3.5.png)

**Rysunek 8-4**. Przy użyciu HttpClientFactory z klasami wpisane klienta.

Najpierw należy skonfigurować `HttpClientFactory` w aplikacji, należy dodać odwołanie do `Microsoft.Extensions.Http` pakiet, który zawiera `AddHttpClient()` metody rozszerzenia dla `IServiceCollection`. Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory` ma być używany jako pojedynczego interfejsu `IHttpClientFactory`. Definiuje konfigurację przejściowy `HttpMessageHandlerBuilder`. Ten program obsługi komunikatów (`HttpMessageHandler` obiektu), to wykonana z puli, jest używany przez `HttpClient` zwrócony z fabryki.

W następnym kodu, można zobaczyć jak `AddHttpClient()` może służyć do rejestrowania klientów wpisane (agenci usługi), które muszą korzystać `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Rejestrowanie usługi klienta, jak pokazano w poprzednim kodzie sprawia, że `DefaultClientFactory` tworzenie `HttpClient` skonfigurowane specjalnie dla każdej usługi, ponieważ wyjaśnimy następnego akapitu.

Po prostu rejestrując klasy usługi klienta za pomocą `AddHttpClient()`, `HttpClient` obiekt, który zostanie dodany do swojej klasy użyje konfiguracji i zasad podany podczas rejestracji. W kolejnych sekcjach zobaczysz tych zasad, takich jak ponownych prób lub wyłączniki Polly firmy.

### <a name="httpclient-lifetimes"></a>Okresy istnienia HttpClient

Zawsze możesz uzyskać `HttpClient` obiektu z `IHttpClientFactory`, zwracany jest nowe wystąpienie. Ale każdy `HttpClient` używa `HttpMessageHandler` który ma w puli i ponownie używane przez `IHttpClientFactory` można zmniejszać zużycie zasobów, tak długo, jak `HttpMessageHandler`firmy nie upłynął okres istnienia.

Buforowanie obsługi jest pożądane, ponieważ każdy program obsługi zwykle zarządza własną podstawowego połączenia HTTP; Tworzenie więcej obsługi niż jest to konieczne może spowodować opóźnienia w połączeniu. Niektóre procedury obsługi również nie zamykaj połączeń przez czas nieokreślony, co może uniemożliwić obsługi reagowanie na zmiany DNS.

`HttpMessageHandler` Obiekty w puli mają okres istnienia, który jest czas, który `HttpMessageHandler` wystąpień w puli mogą być ponownie używane. Wartość domyślna to dwie minuty, ale może zostać przesłonięta na wpisane klienta. Aby zastąpić go, należy wywołać `SetHandlerLifetime()` na `IHttpClientBuilder` , jest zwracana podczas tworzenia klienta, jak pokazano w poniższym kodzie:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

Każdy klient wpisane może mieć własną wartość okresu istnienia skonfigurowany program obsługi. Ustaw okres istnienia `InfiniteTimeSpan` można wyłączyć obsługi wygaśnięcia.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementowanie klas klienta wpisana używających HttpClient wprowadzonego kodu i jest skonfigurowany

W poprzednim kroku musisz mieć Twoich zajęciach klienta wpisana zdefiniowane, takich jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itd. — klienta wpisana to klasa, która akceptuje `HttpClient` obiektu (wprowadzony przez jego Konstruktor) i używa go do wywołania niektórych zdalnej usługi HTTP. Na przykład:

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take, 
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl, 
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

Klient wpisane (CatalogService w przykładzie) jest aktywowana za DI (iniekcji zależności), co oznacza może akceptować żadnych zarejestrowanej usługi w jego konstruktorze, oprócz HttpClient.

Wpisane klient jest, efektywnie, przejściowego obiektu, co oznacza, że nowe wystąpienie jest tworzone za każdym razem, jest ono wymagane i zostanie wyświetlony nowy `HttpClient` wystąpienia zawsze jest tworzony. Klasa HttpMessageHandler obiekty w puli są jednak obiekty, które są ponownie używane przez wiele żądań Http.

### <a name="use-your-typed-client-classes"></a>Użyj swojej klasy wpisane klienta

Na koniec po swojej klasy typów zaimplementowane i je zarejestrowane w usłudze AddHttpClient(), umożliwia dowolnym masz wstrzyknięte przez DI, na przykład w każdy kod strony Razor lub dowolny kontroler aplikacji internetowej MVC, podobnie jak w poniższym kodzie z usług ramach aplikacji eShopOnContainers.

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) => 
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied, 
                                               int? TypesFilterApplied, 
                                               int? page, 
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0, 
                                                            itemsPage, 
                                                            BrandFilterApplied, 
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

Do tej pory kod przedstawiony jest po prostu wykonując regularne żądań Http, ale "magii" jest dostępna w poniższych sekcjach, po prostu przez dodanie zasady i delegowanie obsługi zarejestrowanych klientom wpisane, żądania protokołu HTTP, wykonać `HttpClient` będzie zachowują się z uwzględnieniem odporne na błędy zasady kont, takich jak ponawiają próby z wykorzystaniem wykładniczego wycofywania, wyłączniki lub innych niestandardowych obsługi delegowania do zaimplementowania dodatkowe funkcje zabezpieczeń, takimi jak wymaganie użycia tokenów uwierzytelniania lub innych niestandardowych funkcji. 

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Za pomocą HttpClientFactory w programie .NET Core**\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- **Repozytorium HttpClientFactory GitHub**\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
>[Poprzednie](explore-custom-http-call-retries-exponential-backoff.md)
>[dalej](implement-http-call-retries-exponential-backoff-polly.md)
