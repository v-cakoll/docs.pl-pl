---
title: Zaimplementowanie odpornych żądań HTTP za pomocą iHttpClientFactory
description: Dowiedz się, jak używać iHttpClientFactory, dostępne od .NET Core 2.1, do tworzenia `HttpClient` wystąpień, co ułatwia korzystanie z niego w aplikacjach.
ms.date: 03/03/2020
ms.openlocfilehash: 088fb6c7e10ad656247ee4065da5c13d383b2cf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847222"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Zaimplementowanie odpornych żądań HTTP za pomocą iHttpClientFactory

<xref:System.Net.Http.IHttpClientFactory>jest kontraktem wdrożonym przez `DefaultHttpClientFactory`, uparty fabryki, dostępne od .NET <xref:System.Net.Http.HttpClient> Core 2.1, do tworzenia wystąpień, które mają być używane w aplikacjach.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problemy z oryginalną klasą HttpClient dostępną w programie .NET Core

Oryginalna i dobrze <xref:System.Net.Http.HttpClient> znana klasa może być łatwo używana, ale w niektórych przypadkach nie jest właściwie używana przez wielu deweloperów.

Podczas gdy ta `IDisposable`klasa implementuje , deklarowanie `using` i tworzenie wystąpienia w `HttpClient` instrukcji nie jest preferowane, ponieważ gdy obiekt zostanie usunięty, podstawowe gniazdo nie jest natychmiast zwalniany, co może prowadzić do problemu _wyczerpania gniazda._ Aby uzyskać więcej informacji na temat tego problemu, zobacz wpis w blogu [Używasz HttpClient źle i destabilizuje oprogramowanie](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

W `HttpClient` związku z tym, jest przeznaczony do wystąpienia raz i ponownie przez cały okres trwania aplikacji. Wystąpienie `HttpClient` klasy dla każdego żądania wyczerpie liczbę gniazd dostępnych przy dużych obciążeniach. Ten problem spowoduje `SocketException` błędy. Możliwe podejścia do rozwiązania tego problemu są `HttpClient` oparte na tworzeniu obiektu jako singleton lub statyczne, jak wyjaśniono w tym [artykule firmy Microsoft na httpclient użytkowania](../../../csharp/tutorials/console-webapiclient.md). Może to być dobre rozwiązanie dla krótkotrwałych aplikacji konsoli lub podobnych, które są uruchamiane kilka razy dziennie.

Innym problemem, który deweloperzy uruchomić jest `HttpClient` podczas korzystania z udostępnionego wystąpienia w długotrwałych procesów. W sytuacji, gdy HttpClient jest tworzony jako pojedynczy lub obiekt statyczny, nie może obsłużyć zmiany DNS, jak opisano w tym [wydaniu](https://github.com/dotnet/corefx/issues/11224) repozytorium Github dotnet/corefx.

Jednak problem nie jest tak `HttpClient` naprawdę z per se, ale z [domyślnym konstruktorem dla HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), ponieważ tworzy nowe konkretne wystąpienie <xref:System.Net.Http.HttpMessageHandler>, który jest ten, który ma *wyczerpanie gniazd* i DNS zmiany problemów wymienionych powyżej.

Aby rozwiązać powyższe problemy i `HttpClient` ułatwić zarządzanie wystąpieniami, program .NET <xref:System.Net.Http.IHttpClientFactory> Core 2.1 wprowadził `HttpClient` interfejs, który może służyć do konfigurowania i tworzenia wystąpień w aplikacji za pomocą wstrzykiwania zależności (DI). Udostępnia również rozszerzenia dla polly oparte pośredniczenia, aby skorzystać z delegowania programów obsługi w HttpClient.

[Polly](http://www.thepollyproject.org/) jest biblioteki obsługi błędów przejściowych, który pomaga deweloperom dodać odporność do swoich aplikacji, przy użyciu niektórych wstępnie zdefiniowanych zasad w sposób płynny i bezpieczny dla wątków.

## <a name="benefits-of-using-ihttpclientfactory"></a>Zalety korzystania z iHttpClientFactory

Obecne wdrożenie <xref:System.Net.Http.IHttpClientFactory>, który również <xref:System.Net.Http.IHttpMessageHandlerFactory>wdraża, oferuje następujące korzyści:

- Zapewnia centralną lokalizację nazewnictwa i `HttpClient` konfigurowania obiektów logicznych. Na przykład można skonfigurować klienta (agenta usługi), który jest wstępnie skonfigurowany do uzyskiwania dostępu do określonej mikrousługi.
- Kodyfikuj koncepcję wychodzącego środka pośredniczącego `HttpClient` poprzez delegowanie programów obsługi i wdrażanie pośrednień opartych na Polly, aby skorzystać z zasad Polly w zakresie odporności.
- `HttpClient`ma już pojęcie delegowania programów obsługi, które mogą być połączone ze sobą dla wychodzących żądań HTTP. Klientów HTTP można zarejestrować w fabryce i można użyć polly obsługi do korzystania z zasad Polly dla Ponów, CircuitBreakers i tak dalej.
- Zarządzaj okresem istnienia, <xref:System.Net.Http.HttpMessageHandler> aby uniknąć wymienionych problemów/problemów, które mogą wystąpić podczas samodzielnego zarządzania `HttpClient` okresami istnienia.

> [!TIP]
> Wystąpienia `HttpClient` wstrzykiwane przez DI, można bezpiecznie usunąć, ponieważ `HttpMessageHandler` skojarzone jest zarządzane przez fabrykę. W rzeczywistości wstrzykuje wystąpienia `HttpClient` są *Scoped* z punktu widzenia DI.

> [!NOTE]
> Implementacja `IHttpClientFactory` (`DefaultHttpClientFactory`) jest ściśle powiązana z `Microsoft.Extensions.DependencyInjection` implementacją DI w pakiecie NuGet. Aby uzyskać więcej informacji na temat korzystania z innych kontenerów DI, zobacz tę [dyskusję github](https://github.com/dotnet/extensions/issues/1345).

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Wiele sposobów używania iHttpClientFactory

Istnieje kilka sposobów, których `IHttpClientFactory` można użyć w aplikacji:

- Podstawowy sposób użycia
- Korzystanie z nazwanych klientów
- Korzystanie z klientów wpisywanych
- Korzystanie z wygenerowanych klientów

Ze względu na zwięzłość, niniejsze wskazówki `IHttpClientFactory`pokazuje najbardziej zorganizowany sposób użycia , który jest użycie klientów wpisanych (wzorzec agenta usługi). Jednak wszystkie opcje są udokumentowane i są obecnie wymienione w tym [artykule obejmującym `IHttpClientFactory` użycie](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Jak używać klientów wpisywanych z iHttpClientFactory

Więc, co to jest "Wpisany klient"? To `HttpClient` tylko, że jest wstępnie skonfigurowany do określonego użytku. Ta konfiguracja może zawierać określone wartości, takie jak serwer podstawowy, nagłówki HTTP lub out czasu.

Na poniższym diagramie pokazano, `IHttpClientFactory`jak klienci maszynowi są używane z:

![Diagram przedstawiający sposób pisania klientów są używane z IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Rysunek 8-4**. Korzystanie `IHttpClientFactory` z wpisanych klas klienta.

Na powyższym obrazie `ClientService` (używany przez kontroler lub `HttpClient` kod klienta) `IHttpClientFactory`używa utworzonego przez zarejestrowanego . Ta fabryka `HttpMessageHandler` przypisuje z puli `HttpClient`do pliku . Można `HttpClient` skonfigurować za pomocą zasad Polly podczas `IHttpClientFactory` rejestrowania w kontenerze DI za pomocą metody <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>rozszerzenia .

Aby skonfigurować powyższą <xref:System.Net.Http.IHttpClientFactory> strukturę, dodaj w `Microsoft.Extensions.Http` aplikacji, instalując pakiet NuGet, który zawiera metodę <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> rozszerzenia dla programu <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>. Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory` wewnętrzną klasę, która ma `IHttpClientFactory`być używana jako pojedynczy ton dla interfejsu . Definiuje konfigurację przejściową dla <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>pliku . Ten program<xref:System.Net.Http.HttpMessageHandler> obsługi komunikatów (obiekt), zaczerpnięte `HttpClient` z puli, jest używany przez zwrócone z fabryki.

W następnym kodzie można `AddHttpClient()` zobaczyć, jak można zarejestrować klientów wpisywanych `HttpClient`(agentów usług), które muszą być używane .

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Rejestrowanie usług klienta, jak pokazano w `DefaultClientFactory` poprzednim `HttpClient` kodzie, tworzy standard dla każdej usługi.

Można również dodać konfigurację specyficzne dla wystąpienia w rejestracji, na przykład skonfigurować adres podstawowy i dodać niektóre zasady odporności, jak pokazano w poniższym kodzie:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Tylko dla przykładu, można zobaczyć jedną z powyższych zasad w następnym kodzie:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

Więcej szczegółów na temat korzystania z Polly można znaleźć w [następnym artykule](implement-http-call-retries-exponential-backoff-polly.md).

### <a name="httpclient-lifetimes"></a>Okresy istnienia klienta http

Za każdym razem, gdy otrzymasz obiekt `HttpClient` z `IHttpClientFactory`, zwracane jest nowe wystąpienie. Ale `HttpClient` każdy `HttpMessageHandler` używa, który jest w puli `IHttpClientFactory` i ponownie wykorzystywane przez `HttpMessageHandler`w celu zmniejszenia zużycia zasobów, tak długo, jak okres istnienia nie wygasł.

Buforowanie programów obsługi jest pożądane, ponieważ każdy program obsługi zazwyczaj zarządza własnymi podstawowymi połączeniami HTTP; tworzenie większej liczby programów obsługi niż jest to konieczne może spowodować opóźnienia połączenia. Niektóre programy obsługi również zachować połączenia otwarte przez czas nieokreślony, co może uniemożliwić programowi obsługi reagowanie na zmiany DNS.

Obiekty `HttpMessageHandler` w puli mają okres istnienia, który jest `HttpMessageHandler` czas, który wystąpienie w puli mogą być ponownie używane. Wartość domyślna wynosi dwie minuty, ale można ją zastąpić na klienta wpisana. Aby go zastąpić, `SetHandlerLifetime()` wywołaj, <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> który jest zwracany podczas tworzenia klienta, jak pokazano w następującym kodzie:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Każdy wpisany klient może mieć własną skonfigurowaną wartość okresu istnienia programu obsługi. Ustaw okres `InfiniteTimeSpan` istnienia, aby wyłączyć wygaśnięcie programu obsługi.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementowanie klas klienta wpisanych, które używają wstrzykuje i skonfigurowany HttpClient

W poprzednim kroku należy zdefiniować klasy klienta wpisane, takie jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itp. `HttpClient` Przykład:

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

Wpisany klient`CatalogService` (w przykładzie) jest aktywowany przez DI (Dependency Injection), co oznacza, że może `HttpClient`akceptować dowolną zarejestrowaną usługę w swoim konstruktorze, oprócz .

Klienta wpisanego jest, skutecznie, obiekt przejściowy, co oznacza, że nowe wystąpienie jest tworzony za `HttpClient` każdym razem, gdy jest potrzebne i otrzyma nowe wystąpienie za każdym razem, gdy jest skonstruowany. Jednak `HttpMessageHandler` obiekty w puli są obiekty, które są `HttpClient` ponownie używane przez wiele wystąpień.

### <a name="use-your-typed-client-classes"></a>Korzystanie z klas klienta wpisanych

Na koniec po zaimplementowaniu klas wpisanych i zarejestrowaniu ich i skonfigurowaniu `AddHttpClient()`z nimi, można ich używać wszędzie tam, gdzie można mieć usługi wstrzykiwane przez DI. Na przykład w kod strony Razor lub kontroler aplikacji sieci Web MVC, jak w następującym kodzie z eShopOnContainers:

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

Do tego momentu wyświetlany kod jest po prostu wykonywanie regularnych żądań Http, ale "magia" jest w następujących sekcjach, gdzie po prostu dodając `HttpClient` zasady i delegowanie programów obsługi do zarejestrowanych klientów wpisywanych, wszystkie żądania HTTP do wykonania przez będzie zachowywać się z uwzględnieniem odpornych zasad, takich jak ponownych prób z wykładniczego wycofywania, wyłączniki lub inne niestandardowe programy obsługi delegating do zaimplementowania dodatkowych funkcji zabezpieczeń, takich jak przy użyciu tokenów auth lub innych funkcji niestandardowej.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Korzystanie z httpclientfactory w programie .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **HttpClientFactory kod źródłowy w `dotnet/extensions` repozytorium GitHub**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (odporność.NET i biblioteka obsługi błędów przejściowych)**  
  <http://www.thepollyproject.org/>
  
- **Przy użyciu IHttpClientFactory bez iniekcji zależności (problem gitHub)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Poprzedni](implement-resilient-entity-framework-core-sql-connections.md)
>[następny](implement-http-call-retries-exponential-backoff-polly.md)
