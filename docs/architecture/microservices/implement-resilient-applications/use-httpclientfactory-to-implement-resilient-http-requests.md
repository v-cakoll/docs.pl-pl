---
title: Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP
description: Dowiedz się, jak korzystać z HttpClientFactory, dostępnego od platformy .NET Core 2,1, do tworzenia wystąpień `HttpClient`, ułatwiając korzystanie z nich w aplikacjach.
ms.date: 08/08/2019
ms.openlocfilehash: 1a6d65509d669166e73ad907b506bae7fa26536d
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900324"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP

`HttpClientFactory` jest fabryką ceniona, dostępną od platformy .NET Core 2,1 do tworzenia wystąpień <xref:System.Net.Http.HttpClient>, które mają być używane w aplikacjach.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemy z oryginalną klasą HttpClient dostępną w programie .NET Core

Oryginalna i dobrze znana Klasa <xref:System.Net.Http.HttpClient> może być łatwo używana, ale w niektórych przypadkach nie jest ona prawidłowo używana przez wielu deweloperów.

Podczas pierwszego problemu, gdy ta klasa jest używana, używanie jej z instrukcją `using` nie jest najlepszym wyborem, ponieważ nawet w przypadku usuwania `HttpClient` obiektu, bazowe gniazdo nie zostanie natychmiast wydane i może spowodować poważny problem o nazwie "wyczerpania gniazd". Aby uzyskać więcej informacji o tym problemie, zobacz, [czy używasz programu HttpCliente, i destabilizująco wpis w blogu na oprogramowanie](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) .

W związku z tym `HttpClient` jest przeznaczony do tworzenia wystąpień jednokrotnie i ponownie używane przez cały czas życia aplikacji. Utworzenie wystąpienia klasy `HttpClient` dla każdego żądania spowoduje wyczerpanie liczby gniazd dostępnych w ramach dużych obciążeń. Ten problem spowoduje błędy `SocketException`. Możliwe podejścia do rozwiązania tego problemu opierają się na tworzeniu obiektu `HttpClient` jako singleton lub static, jak wyjaśniono w tym [artykule firmy Microsoft w sprawie użycia HttpClient](../../../csharp/tutorials/console-webapiclient.md).

Jednak występuje drugi problem z `HttpClient`, który można mieć, gdy jest używany jako obiekt pojedynczy lub statyczny. W takim przypadku pojedyncze lub statyczne `HttpClient` nie respektują zmian DNS, jak wyjaśniono w tym [problemie](https://github.com/dotnet/corefx/issues/11224) w repozytorium GitHub/corefx.

Aby rozwiązać wspomniane problemy i ułatwić zarządzanie wystąpieniami `HttpClient`, w środowisku .NET Core 2,1 wprowadzono nowy `HttpClientFactory`, który może być również używany do implementowania odpornych wywołań HTTP przez integrację z nią Polly.

[Polly](http://www.thepollyproject.org/) jest biblioteką obsługi błędów przejściowych, która ułatwia deweloperom Dodawanie odporności do aplikacji przy użyciu wstępnie zdefiniowanych zasad w sposób bezpieczny dla bezpieczeństwa i bezpiecznego wątkowo.

## <a name="what-is-httpclientfactory"></a>Co to jest HttpClientFactory

`HttpClientFactory` jest zaprojektowana tak, aby:

- Podaj centralną lokalizację do nazywania i konfigurowania obiektów `HttpClient` logicznych. Można na przykład skonfigurować klienta (agenta usługi), który jest wstępnie skonfigurowany w celu uzyskania dostępu do konkretnej mikrousługi.
- Codify koncepcji wychodzącego oprogramowania pośredniczącego przez delegowanie programów obsługi w `HttpClient` i implementowanie oprogramowania pośredniczącego opartego na Pollyach, aby wykorzystać zasady dotyczące odporności Polly.
- Klasa `HttpClient` ma już pojęcie delegowania programów obsługi, które można połączyć ze sobą dla wychodzących żądań HTTP. Klienci HTTP są rejestrowani w fabryce i można użyć procedury obsługi Polly, aby używać zasad Polly do ponawiania, CircuitBreakers itd.
- Zarządzaj okresem istnienia `HttpClientMessageHandlers`, aby uniknąć wspomnianych problemów i problemów, które mogą wystąpić podczas samodzielnego zarządzania `HttpClient` okresów istnienia.

> [!NOTE]
> `HttpClientFactory` jest ściśle powiązany z implementacją iniekcji zależności w pakiecie `Microsoft.Extensions.DependencyInjection` NuGet. Aby uzyskać więcej informacji na temat korzystania z innych kontenerów iniekcji zależności, zobacz tę [dyskusję](https://github.com/dotnet/extensions/issues/1345)w witrynie GitHub.

## <a name="multiple-ways-to-use-httpclientfactory"></a>Wiele sposobów używania HttpClientFactory

Istnieje kilka sposobów używania `HttpClientFactory` w aplikacji:

- Użyj `HttpClientFactory` bezpośrednio
- Użyj nazwanych klientów
- Używaj wpisanych klientów
- Korzystanie z wygenerowanych klientów

Ze względu na zwięzłości, te wskazówki przedstawiają najbardziej strukturalny sposób używania `HttpClientFactory`, który jest używany jako klienci z określonym typem (wzorzec agenta usługi). Wszystkie opcje są jednak udokumentowane i są obecnie wymienione w tym [artykule dotyczące użycia HttpClientFactory](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Jak używać klientów z określonym programem HttpClientFactory

Co to jest "klient z określonym typem"? Jest to tylko `HttpClient`, który jest konfigurowany podczas iniekcji przez `DefaultHttpClientFactory`.

Na poniższym diagramie pokazano, w jaki sposób typy klientów są używane z `HttpClientFactory`:

![Diagram przedstawiający sposób używania z HttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Rysunek 8-4**. Korzystanie z HttpClientFactory z klasami klienta z typem.

Na powyższym obrazie ClientService (używany przez kontroler lub kod klienta) używa `HttpClient` utworzonego przez zarejestrowany `IHttpClientFactory`. Ta fabryka przypisuje `HttpClient` `HttpMessageHandler` z puli, którą zarządza. `HttpClient` można skonfigurować przy użyciu zasad Polly podczas rejestrowania `IHttpClientFactory` w kontenerze DI z metodą rozszerzenia `AddHttpClient`.

Aby skonfigurować powyższą strukturę, Dodaj `HttpClientFactory` w aplikacji, instalując pakiet NuGet `Microsoft.Extensions.Http`, który zawiera metodę rozszerzenia `AddHttpClient()` dla `IServiceCollection`. Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory`, które mają być używane jako pojedyncze dla `IHttpClientFactory`interfejsu. Definiuje ona przejściową konfigurację dla `HttpMessageHandlerBuilder`. Ten program obsługi komunikatów (`HttpMessageHandler` Object), pobrany z puli, jest używany przez `HttpClient` zwracaną z fabryki.

W następnym kodzie można zobaczyć, jak `AddHttpClient()` może służyć do rejestrowania klientów typu (agenci usługi), którzy muszą korzystać z `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Zarejestrowanie usług klienta, jak pokazano w poprzednim kodzie, sprawia, że `DefaultClientFactory` utworzyć `HttpClient` standardowego dla każdej usługi.

Można również dodać konfigurację specyficzną dla wystąpienia w ramach rejestracji do programu, na przykład skonfigurować adres podstawowy i dodać zasady odporności, jak pokazano w poniższym kodzie:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Tylko w przypadku przykładu można zobaczyć jedną z powyższych zasad w następnym kodzie:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

Więcej informacji o używaniu programu Polly można znaleźć w [następnym artykule](implement-http-call-retries-exponential-backoff-polly.md).

### <a name="httpclient-lifetimes"></a>HttpClient okresy istnienia

Za każdym razem, gdy otrzymujesz obiekt `HttpClient` z `IHttpClientFactory`, zostanie zwrócone nowe wystąpienie. Jednak każdy `HttpClient` używa `HttpMessageHandler`, który jest w puli i ponownie używany przez `IHttpClientFactory` w celu zmniejszenia zużycia zasobów, o ile okres istnienia `HttpMessageHandler`nie wygasł.

Buforowanie programów obsługi jest pożądane, ponieważ każdy program obsługi zazwyczaj zarządza własnymi połączeniami HTTP; Utworzenie większej liczby programów obsługi niż to konieczne może skutkować opóźnieniami połączeń. Niektóre programy obsługi powodują również, że połączenia są otwarte w nieskończoność, co może uniemożliwić obsłużenie zmian DNS przez program obsługi.

`HttpMessageHandler` obiektów w puli ma okres istnienia równy czasowi, w którym można ponownie użyć wystąpienia `HttpMessageHandler` w puli. Wartość domyślna to dwie minuty, ale można ją przesłonić dla poszczególnych klientów. Aby zastąpić ten element, wywołaj `SetHandlerLifetime()` na `IHttpClientBuilder`, który jest zwracany podczas tworzenia klienta, jak pokazano w poniższym kodzie:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Każdy klient z określonym typem może mieć własną skonfigurowaną wartość okresu istnienia programu obsługi. Ustaw okres istnienia `InfiniteTimeSpan`, aby wyłączyć procedurę obsługi.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Zaimplementuj wpisane klasy klienta korzystające z wstrzykniętych i skonfigurowanych HttpClient

W poprzednim kroku należy określić zdefiniowane klasy klienta, takie jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itd. — typ klienta jest klasą akceptującą obiekt `HttpClient` (wstrzyknięty za pomocą jego konstruktora) i używa go do wywołania pewnej zdalnej usługi HTTP. Na przykład:

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

Typ klienta (CatalogService w tym przykładzie) jest uaktywniany przez DI (iniekcja zależności), co oznacza, że może akceptować wszelkie zarejestrowane usługi w swoim konstruktorze, oprócz HttpClient.

Klient z określonym typem to, efektywnie, obiekt przejściowy, co oznacza, że nowe wystąpienie jest tworzone za każdym razem, gdy jest to konieczne, i otrzyma nowe wystąpienie `HttpClient` za każdym razem, gdy zostanie ono skonstruowane. Jednak obiekty HttpMessageHandler w puli są obiektami, które są ponownie używane przez wiele żądań HTTP.

### <a name="use-your-typed-client-classes"></a>Korzystanie z wpisanych klas klienta

Na koniec po zaimplementowaniu klas wpisanych i zarejestrowaniu ich przy użyciu `AddHttpClient()`można ich używać wszędzie tam, gdzie można korzystać z usług wstrzykiwanych przez DI. Na przykład w kodzie lub kontrolerze strony Razor w aplikacji sieci Web MVC, jak w poniższym kodzie z eShopOnContainers:

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

Do tego momentu pokazany kod właśnie wykonuje zwykłe żądania HTTP, ale "Magic" znajduje się w następujących sekcjach, gdzie, bezpośrednio przez dodanie zasad i delegowanie programów obsługi do zarejestrowanych klientów z określonym typem, wszystkie żądania HTTP, które mają zostać wykonane przez `HttpClient` będą zachowywać się w celu uwzględnienia odpornych zasad, takich jak ponowne próby z użyciem wykładniczych wycofywania, wyłączników lub innych niestandardowych funkcji delegowania do implementowania dodatkowych funkcji zabezpieczeń, takich jak tokeny uwierzytelniania lub jakakolwiek inna funkcja niestandardowa.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Używanie HttpClientFactory w programie .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Kod źródłowy HttpClientFactory w repozytorium GitHub `dotnet/extensions`**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (odporność platformy .NET i Biblioteka obsługi błędów przejściowych)**  
  <http://www.thepollyproject.org/>
  
- **Korzystanie z HttpClientFactory bez iniekcji zależności (problem z usługą GitHub)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Poprzedni](explore-custom-http-call-retries-exponential-backoff.md)
>[Następny](implement-http-call-retries-exponential-backoff-polly.md)
