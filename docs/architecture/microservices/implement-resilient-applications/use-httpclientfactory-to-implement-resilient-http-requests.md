---
title: Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP
description: Dowiedz się, jak używać usługi HttpClientFactory, dostępnej od platformy .NET Core `HttpClient` 2,1, do tworzenia wystąpień, co ułatwia korzystanie z niej w aplikacjach.
ms.date: 01/07/2019
ms.openlocfilehash: 68c841a6ba69a94eff420233124cf00fec506502
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296039"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="22560-103">Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP</span><span class="sxs-lookup"><span data-stu-id="22560-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="22560-104">`HttpClientFactory`jest fabryką ceniona, dostępną od platformy .NET Core 2,1 do <xref:System.Net.Http.HttpClient> tworzenia wystąpień, które mają być używane w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="22560-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="22560-105">Problemy z oryginalną klasą HttpClient dostępną w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="22560-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="22560-106">Oryginalna i dobrze znana Klasa [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) można łatwo używać, ale w niektórych przypadkach nie jest ona prawidłowo używana przez wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="22560-106">The original and well-known [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span> 

<span data-ttu-id="22560-107">Podczas pierwszego problemu, gdy ta klasa jest dostępna, używanie jej z `using` instrukcją nie jest najlepszym wyborem, ponieważ nawet w przypadku usuwania `HttpClient` obiektu, bazowe gniazdo nie jest natychmiast uwalniane i może spowodować poważne wystąpienie problemu o nazwie "Sockets" wyczerpanie.</span><span class="sxs-lookup"><span data-stu-id="22560-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="22560-108">Aby uzyskać więcej informacji o tym problemie, zobacz, [czy używasz programu HttpCliente, i destabilizująco wpis w blogu na oprogramowanie](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) .</span><span class="sxs-lookup"><span data-stu-id="22560-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="22560-109">W związku `HttpClient` z tym, jest przeznaczony do tworzenia wystąpień i ponownie używany przez cały czas życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22560-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="22560-110">`HttpClient` Wystąpienie klasy dla każdego żądania spowoduje wyczerpanie liczby gniazd dostępnych w ramach dużych obciążeń.</span><span class="sxs-lookup"><span data-stu-id="22560-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="22560-111">Ten problem spowoduje `SocketException` błędy.</span><span class="sxs-lookup"><span data-stu-id="22560-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="22560-112">Możliwe podejścia do rozwiązania tego problemu są oparte na tworzeniu `HttpClient` obiektu jako singleton lub statyczny, jak wyjaśniono w tym [artykule firmy Microsoft w sprawie użycia HttpClient](/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="22560-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="22560-113">Ale występuje drugi problem `HttpClient` , który może być używany w przypadku używania go jako obiektu pojedynczego lub statycznego.</span><span class="sxs-lookup"><span data-stu-id="22560-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="22560-114">W takim przypadku pojedyncze lub statyczne `HttpClient` nie respektują zmian DNS, jak wyjaśniono w tym [problemie w repozytorium GitHub platformy .NET Core](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="22560-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="22560-115">Aby rozwiązać te problemy i ułatwić zarządzanie `HttpClient` wystąpieniami, w programie .NET Core 2,1 wprowadzono nowy `HttpClientFactory` , który może być również używany do implementowania odpornych wywołań http przez integrację z Polly.</span><span class="sxs-lookup"><span data-stu-id="22560-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="22560-116">Co to jest HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="22560-116">What is HttpClientFactory</span></span>

<span data-ttu-id="22560-117">`HttpClientFactory`zaprojektowano w celu:</span><span class="sxs-lookup"><span data-stu-id="22560-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="22560-118">Podaj centralną lokalizację do nazywania i konfigurowania HttpClients logicznego.</span><span class="sxs-lookup"><span data-stu-id="22560-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="22560-119">Można na przykład skonfigurować klienta (agenta usługi), który jest wstępnie skonfigurowany w celu uzyskania dostępu do konkretnej mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="22560-119">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="22560-120">Codify koncepcję wychodzącego oprogramowania pośredniczącego przez delegowanie programów `HttpClient` obsługi w programie i implementację oprogramowania pośredniczącego opartego na Polly, aby wykorzystać zasady dotyczące odporności Polly.</span><span class="sxs-lookup"><span data-stu-id="22560-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="22560-121">Klasa `HttpClient` ma już pojęcie delegowania programów obsługi, które można połączyć ze sobą dla wychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="22560-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="22560-122">Klienci protokołu HTTP można rejestrować do fabryki oraz korzystać z procedury obsługi Polly, która umożliwia używanie zasad Pollyymi do ponawiania prób, CircuitBreakers itd.</span><span class="sxs-lookup"><span data-stu-id="22560-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="22560-123">Zarządzaj okresem istnienia HttpClientMessageHandlers, aby uniknąć wspomnianych problemów lub problemów, które mogą `HttpClient` wystąpić w przypadku samodzielnego zarządzania okresami istnienia.</span><span class="sxs-lookup"><span data-stu-id="22560-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="22560-124">Wiele sposobów używania HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="22560-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="22560-125">Istnieje kilka sposobów, których można używać `HttpClientFactory` w aplikacji:</span><span class="sxs-lookup"><span data-stu-id="22560-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="22560-126">Użyj `HttpClientFactory` bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="22560-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="22560-127">Użyj nazwanych klientów</span><span class="sxs-lookup"><span data-stu-id="22560-127">Use Named Clients</span></span>
- <span data-ttu-id="22560-128">Używaj wpisanych klientów</span><span class="sxs-lookup"><span data-stu-id="22560-128">Use Typed Clients</span></span>
- <span data-ttu-id="22560-129">Korzystanie z wygenerowanych klientów</span><span class="sxs-lookup"><span data-stu-id="22560-129">Use Generated Clients</span></span>

<span data-ttu-id="22560-130">Ze względu na zwięzłości, te wskazówki przedstawiają najbardziej strukturalny sposób `HttpClientFactory` korzystania z tego typu klientów (wzorzec agenta usługi), ale wszystkie opcje są udokumentowane i są obecnie wymienione w tym artykule dotyczące [użycia HttpClientFactory](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="22560-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that's to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="22560-131">Jak używać klientów z określonym programem HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="22560-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="22560-132">Co to jest "klient z określonym typem"?</span><span class="sxs-lookup"><span data-stu-id="22560-132">So, what's a "Typed Client"?</span></span> <span data-ttu-id="22560-133">Jest to tylko `HttpClient` te, które zostały skonfigurowane podczas wstrzykiwania `DefaultHttpClientFactory`przez.</span><span class="sxs-lookup"><span data-stu-id="22560-133">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="22560-134">Na poniższym diagramie pokazano, w jaki sposób typy klientów `HttpClientFactory`są używane w programie:</span><span class="sxs-lookup"><span data-stu-id="22560-134">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![ClientService (używany przez kontroler lub kod klienta) używa HttpClient utworzonego przez zarejestrowany IHttpClientFactory.](./media/image3.5.png)

<span data-ttu-id="22560-138">**Rysunek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="22560-138">**Figure 8-4**.</span></span> <span data-ttu-id="22560-139">Korzystanie z HttpClientFactory z klasami klienta z typem.</span><span class="sxs-lookup"><span data-stu-id="22560-139">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="22560-140">Najpierw Instalatora `HttpClientFactory` w aplikacji, dodając odwołanie `Microsoft.Extensions.Http` do pakietu `AddHttpClient()` zawierającego metodę rozszerzenia dla `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="22560-140">First, setup `HttpClientFactory` in your application, adding a reference to the `Microsoft.Extensions.Http` package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="22560-141">Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory` do użycia jako pojedynczy dla interfejsu. `IHttpClientFactory`</span><span class="sxs-lookup"><span data-stu-id="22560-141">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="22560-142">Definiuje konfigurację przejściową dla `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="22560-142">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="22560-143">Ta procedura obsługi komunikatów`HttpMessageHandler` (obiekt) pobierana z puli jest używana `HttpClient` przez zwracaną z fabryki.</span><span class="sxs-lookup"><span data-stu-id="22560-143">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="22560-144">W następnym kodzie można zobaczyć, jak `AddHttpClient()` można użyć do rejestrowania klientów typu (agentów usług), których należy użyć. `HttpClient`</span><span class="sxs-lookup"><span data-stu-id="22560-144">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="22560-145">Zarejestrowanie usług klienta, jak pokazano w poprzednim kodzie, sprawia `DefaultClientFactory` , że `HttpClient` tworzenie skonfigurowane dla każdej usługi w sposób opisany w następnym akapicie.</span><span class="sxs-lookup"><span data-stu-id="22560-145">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create an `HttpClient` configured specifically for each service, as we'll explain in the next paragraph.</span></span>

<span data-ttu-id="22560-146">Bezpośrednio przez zarejestrowanie klasy usługi klienta w `AddHttpClient()`programie `HttpClient` , obiekt, który zostanie dodany do klasy, będzie używać konfiguracji i zasad dostarczonych podczas rejestracji.</span><span class="sxs-lookup"><span data-stu-id="22560-146">Just by registering your client service class with `AddHttpClient()`, the `HttpClient` object that will be injected into your class will use the configuration and policies provided upon registration.</span></span> <span data-ttu-id="22560-147">W następnych sekcjach zostaną wyświetlone te zasady, takie jak ponowne próby Polly lub wyłączniki.</span><span class="sxs-lookup"><span data-stu-id="22560-147">In the next sections, you'll see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="22560-148">HttpClient okresy istnienia</span><span class="sxs-lookup"><span data-stu-id="22560-148">HttpClient lifetimes</span></span>

<span data-ttu-id="22560-149">Za każdym razem `IHttpClientFactory`, gdy `HttpClient` otrzymujesz obiekt z, zostanie zwrócone nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="22560-149">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="22560-150">Ale każdy `HttpClient` z nich `HttpMessageHandler` używa puli `IHttpClientFactory` i ponownie używanej przez program w celu `HttpMessageHandler`zmniejszenia zużycia zasobów, o ile okres istnienia nie wygasł.</span><span class="sxs-lookup"><span data-stu-id="22560-150">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="22560-151">Buforowanie programów obsługi jest pożądane, ponieważ każdy program obsługi zazwyczaj zarządza własnymi połączeniami HTTP; Utworzenie większej liczby programów obsługi niż to konieczne może skutkować opóźnieniami połączeń.</span><span class="sxs-lookup"><span data-stu-id="22560-151">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="22560-152">Niektóre programy obsługi powodują również, że połączenia są otwarte w nieskończoność, co może uniemożliwić obsłużenie zmian DNS przez program obsługi.</span><span class="sxs-lookup"><span data-stu-id="22560-152">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="22560-153">W obiektach w puli jest używany okres istnienia, który to czas, przez `HttpMessageHandler` który wystąpienie w puli może być ponownie używane. `HttpMessageHandler`</span><span class="sxs-lookup"><span data-stu-id="22560-153">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="22560-154">Wartość domyślna to dwie minuty, ale można ją przesłonić dla poszczególnych klientów.</span><span class="sxs-lookup"><span data-stu-id="22560-154">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="22560-155">Aby przesłonić ten `SetHandlerLifetime()` element, `IHttpClientBuilder` Wywołaj to, który jest zwracany podczas tworzenia klienta, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="22560-155">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="22560-156">Każdy klient z określonym typem może mieć własną skonfigurowaną wartość okresu istnienia programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="22560-156">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="22560-157">Ustaw okres istnienia `InfiniteTimeSpan` w celu wyłączenia procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="22560-157">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="22560-158">Zaimplementuj wpisane klasy klienta korzystające z wstrzykniętych i skonfigurowanych HttpClient</span><span class="sxs-lookup"><span data-stu-id="22560-158">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="22560-159">W poprzednim kroku należy określić zdefiniowane klasy klienta, takie jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itp. — typ klienta jest klasą akceptującą `HttpClient` obiekt (wstrzykiwanym przez Konstruktor) i używa go do wywoływania pewnej zdalnej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="22560-159">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="22560-160">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="22560-160">For example:</span></span>

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

<span data-ttu-id="22560-161">Typ klienta (CatalogService w tym przykładzie) jest uaktywniany przez DI (iniekcja zależności), co oznacza, że może akceptować wszelkie zarejestrowane usługi w swoim konstruktorze, oprócz HttpClient.</span><span class="sxs-lookup"><span data-stu-id="22560-161">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="22560-162">Klient z określonym typem to, efektywnie, obiekt przejściowy, co oznacza, że nowe wystąpienie jest tworzone za każdym razem, gdy jest to konieczne, `HttpClient` i otrzyma nowe wystąpienie, gdy zostanie ono skonstruowane.</span><span class="sxs-lookup"><span data-stu-id="22560-162">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="22560-163">Jednak obiekty HttpMessageHandler w puli są obiektami, które są ponownie używane przez wiele żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="22560-163">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="22560-164">Korzystanie z wpisanych klas klienta</span><span class="sxs-lookup"><span data-stu-id="22560-164">Use your Typed Client classes</span></span>

<span data-ttu-id="22560-165">Na koniec po zaimplementowaniu klas typów i zarejestrowaniu ich przy użyciu AddHttpClient () można używać go wszędzie tam, gdzie można uzyskać usługi przez DI, na przykład w dowolnym kodzie strony Razor lub dowolnym kontrolerze aplikacji sieci Web MVC, jak w poniższym kodzie z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="22560-165">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="22560-166">Do tego momentu pokazany kod jest tylko wykonywanie zwykłych żądań HTTP, ale "Magic" znajduje się w następujących sekcjach, w których po prostu przez dodanie zasad i delegowanie programów obsługi do zarejestrowanych klientów z określonym typem, wszystkie żądania HTTP, które mają `HttpClient` być wykonywane przez program, będą zachowywać się w celu uwzględnienia odpornych zasad, takich jak ponowne próby przy użyciu wykładniczej wycofywania, wyłączników lub wszelkich innych niestandardowych procedur delegowania do implementowania dodatkowych funkcji zabezpieczeń, takich jak tokeny uwierzytelniania lub jakakolwiek inna funkcja niestandardowa.</span><span class="sxs-lookup"><span data-stu-id="22560-166">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="22560-167">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="22560-167">Additional resources</span></span>

- <span data-ttu-id="22560-168">**Używanie HttpClientFactory w programie .NET Core**</span><span class="sxs-lookup"><span data-stu-id="22560-168">**Using HttpClientFactory in .NET Core**</span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- <span data-ttu-id="22560-169">**Repozytorium GitHub HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="22560-169">**HttpClientFactory GitHub repo**</span></span>\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
><span data-ttu-id="22560-170">[Poprzedni](explore-custom-http-call-retries-exponential-backoff.md)Następny
>[](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="22560-170">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
