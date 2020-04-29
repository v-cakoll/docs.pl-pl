---
title: Używanie elementu IHttpClientFactory do implementowania odpornych na błędy żądań HTTP
description: Dowiedz się, jak używać usługi IHttpClientFactory, dostępnej od platformy .NET Core `HttpClient` 2,1, do tworzenia wystąpień, co ułatwia korzystanie z niej w aplikacjach.
ms.date: 03/03/2020
ms.openlocfilehash: ade26208a931faa456c8e267def2caef7a3f32de
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507302"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Używanie elementu IHttpClientFactory do implementowania odpornych na błędy żądań HTTP

<xref:System.Net.Http.IHttpClientFactory>jest umową zaimplementowaną przez `DefaultHttpClientFactory`, ceniona fabrykę, dostępną od platformy .net core <xref:System.Net.Http.HttpClient> 2,1, do tworzenia wystąpień, które mają być używane w aplikacjach.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemy z oryginalną klasą HttpClient dostępną w programie .NET Core

Oryginalna i dobrze znana <xref:System.Net.Http.HttpClient> Klasa może być łatwo używana, ale w niektórych przypadkach nie jest ona prawidłowo używana przez wielu deweloperów.

Chociaż ta klasa implementuje `IDisposable`, deklaruje i tworzy wystąpienie w `using` instrukcji nie jest preferowana, ponieważ gdy `HttpClient` obiekt jest usuwany, podstawowe gniazdo nie jest natychmiast zwalniane, co może prowadzić do problemu z _wyczerpaniem gniazda_ . Aby uzyskać więcej informacji o tym problemie, zapoznaj się z wpisem w blogu, [który jest używany HttpClient, i zastąp go destabilizacja oprogramowania](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

W związku `HttpClient` z tym, jest przeznaczony do tworzenia wystąpień i ponownie używany przez cały czas życia aplikacji. Wystąpienie `HttpClient` klasy dla każdego żądania spowoduje wyczerpanie liczby gniazd dostępnych w ramach dużych obciążeń. Ten problem spowoduje `SocketException` błędy. Możliwe podejścia do rozwiązania tego problemu są oparte na tworzeniu `HttpClient` obiektu jako singleton lub statyczny, jak wyjaśniono w tym [artykule firmy Microsoft w sprawie użycia HttpClient](../../../csharp/tutorials/console-webapiclient.md). Może to być dobre rozwiązanie dla krótkich aplikacji konsolowych lub podobnych, które są uruchamiane kilka razy dziennie.

Innym problemem, z którym deweloperzy pracują usługi, jest użycie udostępnionego `HttpClient` wystąpienia programu w długotrwałych procesach. W sytuacji, gdy HttpClient jest tworzona jako obiekt pojedynczy lub statyczny, nie może obsłużyć zmian DNS zgodnie z opisem w tym [zagadnieniu](https://github.com/dotnet/runtime/issues/18348) dotyczącego repozytorium dotnet/Runtime.

`HttpClient` Problem nie dotyczy jednak na SE, ale z [domyślnym konstruktorem dla HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), ponieważ tworzy nowe konkretne wystąpienie <xref:System.Net.Http.HttpMessageHandler>, które jest takie, które ma problemy z *wyczerpaniem gniazd* i zmiany systemu DNS wymienione powyżej.

Aby rozwiązać problemy wymienione powyżej i umożliwić `HttpClient` Zarządzanie wystąpieniami, w programie .net Core 2,1 wprowadzono <xref:System.Net.Http.IHttpClientFactory> interfejs, którego można użyć do konfigurowania i tworzenia `HttpClient` wystąpień w aplikacji za pomocą iniekcji zależności (di). Udostępnia również rozszerzenia dla oprogramowania pośredniczącego opartego na Polly, które umożliwiają delegowanie programów obsługi w HttpClient.

[Polly](http://www.thepollyproject.org/) jest biblioteką obsługi błędów przejściowych, która ułatwia deweloperom Dodawanie odporności do aplikacji przy użyciu wstępnie zdefiniowanych zasad w sposób bezpieczny dla bezpieczeństwa i bezpiecznego wątkowo.

## <a name="benefits-of-using-ihttpclientfactory"></a>Zalety korzystania z usługi IHttpClientFactory

Bieżąca implementacja <xref:System.Net.Http.IHttpClientFactory>, która również implementuje <xref:System.Net.Http.IHttpMessageHandlerFactory>program, oferuje następujące korzyści:

- Zapewnia centralną lokalizację do nazywania i konfigurowania `HttpClient` obiektów logicznych. Można na przykład skonfigurować klienta (agenta usługi), który jest wstępnie skonfigurowany w celu uzyskania dostępu do konkretnej mikrousługi.
- Codify koncepcję wychodzącego oprogramowania pośredniczącego przez delegowanie programów `HttpClient` obsługi w programie i implementację oprogramowania pośredniczącego opartego na Polly, aby wykorzystać zasady dotyczące odporności Polly.
- `HttpClient`ma już koncepcję delegowania programów obsługi, które mogą być połączone ze sobą w przypadku wychodzących żądań HTTP. Klientów HTTP można zarejestrować do fabryki i można użyć procedury obsługi Polly, aby użyć zasad Polly do ponawiania, CircuitBreakers itd.
- Zarządzaj okresem istnienia, <xref:System.Net.Http.HttpMessageHandler> aby uniknąć wspomnianych problemów i problemów, które mogą `HttpClient` wystąpić podczas samodzielnego zarządzania okresami istnienia.

> [!TIP]
> `HttpClient` Wystąpienia wstrzykiwane przez di mogą zostać bezpiecznie usunięte, ponieważ skojarzona z nim `HttpMessageHandler` zarządza fabryka. W rzeczywistości `HttpClient` wystąpienia wstrzykiwane są *objęte zakresem* od di perspektywy.

> [!NOTE]
> Implementacja programu `IHttpClientFactory` (`DefaultHttpClientFactory`) jest ściśle związana z implementacją di w pakiecie `Microsoft.Extensions.DependencyInjection` NuGet. Aby uzyskać więcej informacji na temat używania innych kontenerów, zobacz tę [dyskusję](https://github.com/dotnet/extensions/issues/1345)w witrynie GitHub.

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Wiele sposobów używania IHttpClientFactory

Istnieje kilka sposobów, których można używać `IHttpClientFactory` w aplikacji:

- Podstawowy sposób użycia
- Użyj nazwanych klientów
- Używaj wpisanych klientów
- Korzystanie z wygenerowanych klientów

Ze względu na zwięzłości te wskazówki przedstawiają najbardziej strukturalny sposób użycia `IHttpClientFactory`, który jest używany jako klienci z określonym typem (wzorzec agenta usługi). Wszystkie opcje są jednak udokumentowane i są obecnie wymienione w tym [artykule `IHttpClientFactory` dotyczące użycia](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Jak używać klientów z określonym programem IHttpClientFactory

Co to jest "klient z określonym typem"? Jest to tylko `HttpClient` wstępnie skonfigurowane do określonego użytku. Ta konfiguracja może obejmować określone wartości, takie jak serwer podstawowy, nagłówki HTTP lub limity czasu.

Na poniższym diagramie pokazano, w jaki sposób typy klientów `IHttpClientFactory`są używane w programie:

![Diagram przedstawiający sposób używania z IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Rysunek 8-4**. Używanie `IHttpClientFactory` z typami klas klienta.

Na powyższym obrazie `ClientService` (używanym przez kontroler lub kod klienta) jest używana `HttpClient` wartość utworzona przez zarejestrowany `IHttpClientFactory`. Ta fabryka przypisuje `HttpMessageHandler` z puli do programu `HttpClient`. Konfigurację `HttpClient` można skonfigurować przy użyciu zasad Polly podczas rejestrowania `IHttpClientFactory` w kontenerze di z metodą <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>rozszerzenia.

Aby skonfigurować powyższą strukturę, Dodaj <xref:System.Net.Http.IHttpClientFactory> do aplikacji, instalując pakiet `Microsoft.Extensions.Http` NuGet, który zawiera metodę <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> rozszerzenia dla. <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> Ta metoda rozszerzenia rejestruje klasę wewnętrzną `DefaultHttpClientFactory` , która ma być używana jako Klasa pojedyncza `IHttpClientFactory`dla interfejsu. Definiuje konfigurację przejściową dla <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>. Ta procedura obsługi komunikatów<xref:System.Net.Http.HttpMessageHandler> (obiekt) pobierana z puli jest używana przez `HttpClient` zwracaną z fabryki.

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

Za każdym razem `IHttpClientFactory`, gdy `HttpClient` otrzymujesz obiekt z, zostanie zwrócone nowe wystąpienie. Ale każdy `HttpClient` z nich `HttpMessageHandler` używa puli i ponownie używanej przez program `IHttpClientFactory` w celu zmniejszenia zużycia zasobów, `HttpMessageHandler`o ile okres istnienia nie wygasł.

Buforowanie programów obsługi jest pożądane, ponieważ każdy program obsługi zazwyczaj zarządza własnymi połączeniami HTTP; Utworzenie większej liczby programów obsługi niż to konieczne może skutkować opóźnieniami połączeń. Niektóre programy obsługi powodują również, że połączenia są otwarte w nieskończoność, co może uniemożliwić obsłużenie zmian DNS przez program obsługi.

W `HttpMessageHandler` obiektach w puli jest używany okres istnienia, który to czas, przez `HttpMessageHandler` który wystąpienie w puli może być ponownie używane. Wartość domyślna to dwie minuty, ale można ją przesłonić dla poszczególnych klientów. Aby przesłonić ten `SetHandlerLifetime()` element, <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> Wywołaj to, który jest zwracany podczas tworzenia klienta, jak pokazano w poniższym kodzie:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Każdy klient z określonym typem może mieć własną skonfigurowaną wartość okresu istnienia programu obsługi. Ustaw okres istnienia `InfiniteTimeSpan` w celu wyłączenia procedury obsługi.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Zaimplementuj wpisane klasy klienta korzystające z wstrzykniętych i skonfigurowanych HttpClient

W poprzednim kroku należy określić zdefiniowane klasy klienta, takie jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itp. — typ klienta jest klasą akceptującą `HttpClient` obiekt (wstrzykiwaną za pośrednictwem jego konstruktora) i używa go do wywołania pewnej zdalnej usługi http. Przykład:

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

Określony klient (`CatalogService` w tym przykładzie) jest uaktywniany przez di (iniekcja zależności), co oznacza, że może akceptować wszystkie zarejestrowane usługi w swoim konstruktorze `HttpClient`, oprócz.

Klient z określonym typem to, efektywnie, obiekt przejściowy, co oznacza, że nowe wystąpienie jest tworzone za każdym razem, gdy jest to konieczne, `HttpClient` i otrzyma nowe wystąpienie, gdy zostanie ono skonstruowane. Jednak `HttpMessageHandler` obiekty w puli są obiektami, które są ponownie używane przez wiele `HttpClient` wystąpień.

### <a name="use-your-typed-client-classes"></a>Korzystanie z wpisanych klas klienta

Na koniec po zaimplementowaniu klas wpisanych i ich zarejestrowaniu i skonfigurowaniu `AddHttpClient()`można używać ich wszędzie tam, gdzie można korzystać z usług wstrzykiwanych przez di. Na przykład w kodzie lub kontrolerze strony Razor w aplikacji sieci Web MVC, jak w poniższym kodzie z eShopOnContainers:

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

Do tego momentu pokazany kod właśnie wykonuje zwykłe żądania HTTP, ale "Magic" znajduje się w następujących sekcjach, gdzie, bezpośrednio przez dodanie zasad i delegowanie programów obsługi do zarejestrowanych klientów z określonym typem, wszystkie żądania HTTP, które mają zostać wykonane `HttpClient` przez program, zachowywać się w celu uwzględnienia odpornych zasad, takich jak ponowne próby z wycofywania wykładniczych, wyłączników lub wszelkich innych niestandardowych funkcji delegowania do implementowania dodatkowych funkcji zabezpieczeń, takich jak tokeny uwierzytelniania lub jakakolwiek inna funkcja niestandardowa.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Używanie HttpClientFactory w programie .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Kod źródłowy HttpClientFactory w repozytorium `dotnet/extensions` GitHub**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (odporność platformy .NET i Biblioteka obsługi błędów przejściowych)**  
  <http://www.thepollyproject.org/>
  
- **Korzystanie z IHttpClientFactory bez iniekcji zależności (problem z usługą GitHub)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Poprzedni](implement-resilient-entity-framework-core-sql-connections.md)
>[Następny](implement-http-call-retries-exponential-backoff-polly.md)
