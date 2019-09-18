---
title: Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP
description: Dowiedz się, jak używać usługi HttpClientFactory, dostępnej od platformy .NET Core `HttpClient` 2,1, do tworzenia wystąpień, co ułatwia korzystanie z niej w aplikacjach.
ms.date: 08/08/2019
ms.openlocfilehash: 6c862171ee6b5eda6f95694878bfa43518a9bdfa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039975"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP

`HttpClientFactory`jest fabryką ceniona, dostępną od platformy .NET Core 2,1 do <xref:System.Net.Http.HttpClient> tworzenia wystąpień, które mają być używane w aplikacjach.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemy z oryginalną klasą HttpClient dostępną w programie .NET Core

Oryginalna i dobrze znana <xref:System.Net.Http.HttpClient> Klasa może być łatwo używana, ale w niektórych przypadkach nie jest ona prawidłowo używana przez wielu deweloperów.

Podczas pierwszego problemu, gdy ta klasa jest dostępna, używanie jej z `using` instrukcją nie jest najlepszym wyborem, ponieważ nawet w przypadku usuwania `HttpClient` obiektu, bazowe gniazdo nie jest natychmiast uwalniane i może spowodować poważne wystąpienie problemu o nazwie "Sockets" wyczerpanie. Aby uzyskać więcej informacji o tym problemie, zobacz, [czy używasz programu HttpCliente, i destabilizująco wpis w blogu na oprogramowanie](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) .

W związku `HttpClient` z tym, jest przeznaczony do tworzenia wystąpień i ponownie używany przez cały czas życia aplikacji. `HttpClient` Wystąpienie klasy dla każdego żądania spowoduje wyczerpanie liczby gniazd dostępnych w ramach dużych obciążeń. Ten problem spowoduje `SocketException` błędy. Możliwe podejścia do rozwiązania tego problemu są oparte na tworzeniu `HttpClient` obiektu jako singleton lub statyczny, jak wyjaśniono w tym [artykule firmy Microsoft w sprawie użycia HttpClient](../../../csharp/tutorials/console-webapiclient.md).

Ale występuje drugi problem `HttpClient` , który może być używany w przypadku używania go jako obiektu pojedynczego lub statycznego. W takim przypadku pojedyncze lub statyczne `HttpClient` nie respektują zmian DNS, jak wyjaśniono w tym [problemie](https://github.com/dotnet/corefx/issues/11224) w repozytorium GitHub/corefx. 

Aby rozwiązać te problemy i ułatwić zarządzanie `HttpClient` wystąpieniami, w programie .NET Core 2,1 wprowadzono nowy `HttpClientFactory` , który może być również używany do implementowania odpornych wywołań http przez integrację z Polly.

[Polly](http://www.thepollyproject.org/) jest biblioteką obsługi błędów przejściowych, która ułatwia deweloperom Dodawanie odporności do aplikacji przy użyciu wstępnie zdefiniowanych zasad w sposób bezpieczny dla bezpieczeństwa i bezpiecznego wątkowo.

## <a name="what-is-httpclientfactory"></a>Co to jest HttpClientFactory

`HttpClientFactory`zaprojektowano w celu:

- Podaj centralną lokalizację do nazywania i konfigurowania `HttpClient` obiektów logicznych. Można na przykład skonfigurować klienta (agenta usługi), który jest wstępnie skonfigurowany w celu uzyskania dostępu do konkretnej mikrousługi.
- Codify koncepcję wychodzącego oprogramowania pośredniczącego przez delegowanie programów `HttpClient` obsługi w programie i implementację oprogramowania pośredniczącego opartego na Polly, aby wykorzystać zasady dotyczące odporności Polly.
- Klasa `HttpClient` ma już pojęcie delegowania programów obsługi, które można połączyć ze sobą dla wychodzących żądań HTTP. Klienci HTTP są rejestrowani w fabryce i można użyć procedury obsługi Polly, aby używać zasad Polly do ponawiania, CircuitBreakers itd.
- Zarządzaj okresem istnienia `HttpClientMessageHandlers` , aby uniknąć wspomnianych problemów i problemów, które mogą `HttpClient` wystąpić podczas samodzielnego zarządzania okresami istnienia.

## <a name="multiple-ways-to-use-httpclientfactory"></a>Wiele sposobów używania HttpClientFactory

Istnieje kilka sposobów, których można używać `HttpClientFactory` w aplikacji:

- Użyj `HttpClientFactory` bezpośrednio
- Użyj nazwanych klientów
- Używaj wpisanych klientów
- Korzystanie z wygenerowanych klientów

Ze względu na zwięzłości te wskazówki przedstawiają najbardziej strukturalny sposób użycia `HttpClientFactory`, który jest używany jako klienci z określonym typem (wzorzec agenta usługi). Wszystkie opcje są jednak udokumentowane i są obecnie wymienione w tym [artykule dotyczące użycia HttpClientFactory](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Jak używać klientów z określonym programem HttpClientFactory

Co to jest "klient z określonym typem"? Jest to tylko `HttpClient` te, które zostały skonfigurowane podczas wstrzykiwania `DefaultHttpClientFactory`przez.

Na poniższym diagramie pokazano, w jaki sposób typy klientów `HttpClientFactory`są używane w programie:

![ClientService (używany przez kontroler lub kod klienta) używa HttpClient utworzonego przez zarejestrowany IHttpClientFactory. Ta fabryka przypisuje HttpClient HttpMessageHandler z puli, którą zarządza. HttpClient można skonfigurować przy użyciu zasad Polly podczas rejestrowania IHttpClientFactory w kontenerze DI z metodą rozszerzenia AddHttpClient.](./media/image3.5.png)

**Rysunek 8-4**. Korzystanie z HttpClientFactory z klasami klienta z typem.

Najpierw Instalatora `HttpClientFactory` w aplikacji, `Microsoft.Extensions.Http` instalując pakiet `AddHttpClient()` NuGet, który zawiera metodę rozszerzenia dla `IServiceCollection`. Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory` do użycia jako pojedynczy dla interfejsu. `IHttpClientFactory` Definiuje konfigurację przejściową dla `HttpMessageHandlerBuilder`. Ta procedura obsługi komunikatów`HttpMessageHandler` (obiekt) pobierana z puli jest używana `HttpClient` przez zwracaną z fabryki.

W następnym kodzie można zobaczyć, jak `AddHttpClient()` można użyć do rejestrowania klientów typu (agentów usług), których należy użyć. `HttpClient`

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Zarejestrowanie usług klienta, jak pokazano w poprzednim kodzie, `DefaultClientFactory` tworzy standard `HttpClient` dla każdej usługi.

Można również dodać konfigurację specyficzną dla wystąpienia w ramach rejestracji do programu, na przykład skonfigurować adres podstawowy i dodać zasady odporności, jak pokazano w poniższym kodzie:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"])
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

Za każdym razem `IHttpClientFactory`, gdy `HttpClient` otrzymujesz obiekt z, zostanie zwrócone nowe wystąpienie. Ale każdy `HttpClient` z nich `HttpMessageHandler` używa puli `IHttpClientFactory` i ponownie używanej przez program w celu `HttpMessageHandler`zmniejszenia zużycia zasobów, o ile okres istnienia nie wygasł.

Buforowanie programów obsługi jest pożądane, ponieważ każdy program obsługi zazwyczaj zarządza własnymi połączeniami HTTP; Utworzenie większej liczby programów obsługi niż to konieczne może skutkować opóźnieniami połączeń. Niektóre programy obsługi powodują również, że połączenia są otwarte w nieskończoność, co może uniemożliwić obsłużenie zmian DNS przez program obsługi.

W obiektach w puli jest używany okres istnienia, który to czas, przez `HttpMessageHandler` który wystąpienie w puli może być ponownie używane. `HttpMessageHandler` Wartość domyślna to dwie minuty, ale można ją przesłonić dla poszczególnych klientów. Aby przesłonić ten `SetHandlerLifetime()` element, `IHttpClientBuilder` Wywołaj to, który jest zwracany podczas tworzenia klienta, jak pokazano w poniższym kodzie:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Każdy klient z określonym typem może mieć własną skonfigurowaną wartość okresu istnienia programu obsługi. Ustaw okres istnienia `InfiniteTimeSpan` w celu wyłączenia procedury obsługi.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Zaimplementuj wpisane klasy klienta korzystające z wstrzykniętych i skonfigurowanych HttpClient

W poprzednim kroku należy określić zdefiniowane klasy klienta, takie jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itp. — typ klienta jest klasą akceptującą `HttpClient` obiekt (wstrzykiwanym przez Konstruktor) i używa go do wywoływania pewnej zdalnej usługi HTTP. Na przykład:

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

Klient z określonym typem to, efektywnie, obiekt przejściowy, co oznacza, że nowe wystąpienie jest tworzone za każdym razem, gdy jest to konieczne, `HttpClient` i otrzyma nowe wystąpienie, gdy zostanie ono skonstruowane. Jednak obiekty HttpMessageHandler w puli są obiektami, które są ponownie używane przez wiele żądań HTTP.

### <a name="use-your-typed-client-classes"></a>Korzystanie z wpisanych klas klienta

Na koniec po zaimplementowaniu klas wpisanych i zarejestrowaniu ich w `AddHttpClient()`programie można używać ich wszędzie tam, gdzie można korzystać z usług wstrzykiwanych przez di. Na przykład w kodzie lub kontrolerze strony Razor w aplikacji sieci Web MVC, jak w poniższym kodzie z eShopOnContainers:

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

Do tego momentu pokazany kod jest tylko wykonywanie zwykłych żądań HTTP, ale "Magic" znajduje się w następujących sekcjach, w których po prostu przez dodanie zasad i delegowanie programów obsługi do zarejestrowanych klientów z określonym typem, wszystkie żądania HTTP, które mają `HttpClient` być wykonywane przez program, będą zachowywać się w celu uwzględnienia odpornych zasad, takich jak ponowne próby przy użyciu wykładniczej wycofywania, wyłączników lub wszelkich innych niestandardowych procedur delegowania do implementowania dodatkowych funkcji zabezpieczeń, takich jak tokeny uwierzytelniania lub jakakolwiek inna funkcja niestandardowa.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Używanie HttpClientFactory w programie .NET Core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Repozytorium GitHub HttpClientFactory** \
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

- **Polly (odporność platformy .NET i Biblioteka obsługi błędów przejściowych)**  \
  <http://www.thepollyproject.org/>

>[!div class="step-by-step"]
>[Poprzedni](explore-custom-http-call-retries-exponential-backoff.md)Następny
>[](implement-http-call-retries-exponential-backoff-polly.md)
