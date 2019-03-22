---
title: Użyj HttpClientFactory do zaimplementowania odporne na błędy żądań HTTP
description: Dowiedz się, jak używać HttpClientFactory dostępne od platformy .NET Core 2.1, do tworzenia `HttpClient` wystąpień, dzięki czemu można korzystać w aplikacjach.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 679de8577d1ce876823954cb7917c50daae9e230
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348716"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="d26c5-103">Użyj HttpClientFactory do zaimplementowania odporne na błędy żądań HTTP</span><span class="sxs-lookup"><span data-stu-id="d26c5-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="d26c5-104">`HttpClientFactory` to ceniona fabryki, dostępne od platformy .NET Core 2.1, do tworzenia <xref:System.Net.Http.HttpClient> wystąpienia ma być używany w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="d26c5-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="d26c5-105">Problemy związane z oryginalnej klasy HttpClient dostępnych w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="d26c5-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="d26c5-106">Oryginalne i dobrze znane [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) klasy mogą być łatwo używane, ale w niektórych przypadkach nie jest prawidłowo używane przez wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="d26c5-106">The original and well-known [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span> 

<span data-ttu-id="d26c5-107">Jako pierwszego wydania tej klasy jest możliwe do rozporządzania, korzystania z niego przy użyciu `using` instrukcja nie jest najlepszym rozwiązaniem, ponieważ nawet wtedy, gdy użytkownik dispose `HttpClient` obiektu bazowego gniazda nie jest od razu zwolniony i może spowodować poważne zagrożenie o nazwie "gniazda wyczerpanie ".</span><span class="sxs-lookup"><span data-stu-id="d26c5-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="d26c5-108">Aby uzyskać więcej informacji na temat tego problemu, zobacz [używasz problem HttpClient i jest on destabilizing oprogramowania](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) wpis w blogu.</span><span class="sxs-lookup"><span data-stu-id="d26c5-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="d26c5-109">W związku z tym `HttpClient` jest przeznaczony do jednorazowego utworzenia ich i ponownie używane w całym cyklu życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d26c5-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="d26c5-110">Utworzenie wystąpienia `HttpClient` klasy dla każdego żądania będą wyczerpać liczbę gniazd, które są dostępne pod dużym obciążeniem.</span><span class="sxs-lookup"><span data-stu-id="d26c5-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="d26c5-111">Czy problem spowoduje `SocketException` błędy.</span><span class="sxs-lookup"><span data-stu-id="d26c5-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="d26c5-112">Możliwe sposoby rozwiązania tego problemu są oparte na tworzeniu `HttpClient` obiektu jako pojedyncze lub statyczna, zgodnie z opisem w tym [artykule firmy Microsoft dotyczących użycia HttpClient](/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="d26c5-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="d26c5-113">Ale drugi problem ze `HttpClient` , może mieć w przypadku użycia jej jako pojedyncze lub obiektu statycznego.</span><span class="sxs-lookup"><span data-stu-id="d26c5-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="d26c5-114">W tej sprawy, pojedyncze lub statyczna `HttpClient` zmian systemu DNS nie jest zgodny z zgodnie z opisem w tym [problemu w repozytorium .NET Core w usłudze GitHub](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="d26c5-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="d26c5-115">Do rozwiązania tych problemów wymienionych i zarządzania `HttpClient` przypadkach łatwiejsze platformy .NET Core 2.1 wprowadzono nową `HttpClientFactory` , można również zaimplementować odporne na błędy połączeń HTTP, integrując Polly z nim.</span><span class="sxs-lookup"><span data-stu-id="d26c5-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="d26c5-116">Co to jest HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="d26c5-116">What is HttpClientFactory</span></span>

<span data-ttu-id="d26c5-117">`HttpClientFactory` została zaprojektowana w celu:</span><span class="sxs-lookup"><span data-stu-id="d26c5-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="d26c5-118">Podaj centralną lokalizację do nazywania i konfigurowanie HttpClients logiczne.</span><span class="sxs-lookup"><span data-stu-id="d26c5-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="d26c5-119">Na przykład może skonfigurować klienta (usługi agenta), który jest wstępnie skonfigurowana do dostępu do określonych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="d26c5-119">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="d26c5-120">Skodyfikowanie koncepcji wychodzących oprogramowania pośredniczącego za pośrednictwem Delegowanie obsługi w `HttpClient` i wdrażanie na podstawie Polly oprogramowaniu pośredniczącym, aby korzystać z zasad firmy Polly pod kątem odporności.</span><span class="sxs-lookup"><span data-stu-id="d26c5-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="d26c5-121">Klasa `HttpClient` ma już pojęcie delegowania programów obsługi, które można połączyć ze sobą dla wychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="d26c5-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="d26c5-122">Rejestrowanie klientów http do fabryki, a także można użyć procedury obsługi Polly, umożliwiająca Polly zasady służący do ponawiania, CircuitBreakers itp.</span><span class="sxs-lookup"><span data-stu-id="d26c5-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="d26c5-123">Zarządzanie okresem istnienia HttpClientMessageHandlers, aby uniknąć wymienionych problemów/problemy, które mogą wystąpić podczas zarządzania `HttpClient` okresy istnienia samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="d26c5-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="d26c5-124">Wiele sposobów, aby użyć HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="d26c5-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="d26c5-125">Istnieje kilka metod, których można użyć `HttpClientFactory` w Twojej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d26c5-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="d26c5-126">Użyj `HttpClientFactory` bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="d26c5-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="d26c5-127">Użyj o nazwie klientów</span><span class="sxs-lookup"><span data-stu-id="d26c5-127">Use Named Clients</span></span>
- <span data-ttu-id="d26c5-128">Korzystać z kontrolą typów klientów</span><span class="sxs-lookup"><span data-stu-id="d26c5-128">Use Typed Clients</span></span>
- <span data-ttu-id="d26c5-129">Użyj wygenerowanych klientów</span><span class="sxs-lookup"><span data-stu-id="d26c5-129">Use Generated Clients</span></span>

<span data-ttu-id="d26c5-130">W celu skrócenia wskazówki te przedstawiają najbardziej ze strukturą sposób używania `HttpClientFactory` to korzystać z kontrolą typów klientów (Agent usługi wzorzec), ale wszystkie opcje są udokumentowane i obecnie są wymienione w tym [artykułu obejmujących użycie HttpClientFactory ](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="d26c5-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that's to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="d26c5-131">Jak używać wpisane klientów z HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="d26c5-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="d26c5-132">Tak co to jest "klient z typowaniem"?</span><span class="sxs-lookup"><span data-stu-id="d26c5-132">So, what's a "Typed Client"?</span></span> <span data-ttu-id="d26c5-133">Jest po prostu `HttpClient` skonfigurowanego na iniekcji przez `DefaultHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="d26c5-133">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="d26c5-134">Na poniższym diagramie przedstawiono, jak wpisane klientów są używane z `HttpClientFactory`:</span><span class="sxs-lookup"><span data-stu-id="d26c5-134">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![ClientService (używane przez kod kontrolera lub klienta) używa HttpClient utworzone przez IHttpClientFactory zarejestrowane.](./media/image3.5.png)

<span data-ttu-id="d26c5-138">**Rysunek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="d26c5-138">**Figure 8-4**.</span></span> <span data-ttu-id="d26c5-139">Przy użyciu HttpClientFactory z klasami wpisane klienta.</span><span class="sxs-lookup"><span data-stu-id="d26c5-139">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="d26c5-140">Najpierw należy skonfigurować `HttpClientFactory` w aplikacji, należy dodać odwołanie do `Microsoft.Extensions.Http` pakiet, który zawiera `AddHttpClient()` metody rozszerzenia dla `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="d26c5-140">First, setup `HttpClientFactory` in your application, adding a reference to the `Microsoft.Extensions.Http` package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="d26c5-141">Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory` ma być używany jako pojedynczego interfejsu `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="d26c5-141">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="d26c5-142">Definiuje konfigurację przejściowy `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="d26c5-142">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="d26c5-143">Ten program obsługi komunikatów (`HttpMessageHandler` obiektu), to wykonana z puli, jest używany przez `HttpClient` zwrócony z fabryki.</span><span class="sxs-lookup"><span data-stu-id="d26c5-143">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="d26c5-144">W następnym kodu, można zobaczyć jak `AddHttpClient()` może służyć do rejestrowania klientów wpisane (agenci usługi), które muszą korzystać `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="d26c5-144">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="d26c5-145">Rejestrowanie usługi klienta, jak pokazano w poprzednim kodzie sprawia, że `DefaultClientFactory` tworzenie `HttpClient` skonfigurowane specjalnie dla każdej usługi, ponieważ wyjaśnimy następnego akapitu.</span><span class="sxs-lookup"><span data-stu-id="d26c5-145">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create an `HttpClient` configured specifically for each service, as we'll explain in the next paragraph.</span></span>

<span data-ttu-id="d26c5-146">Po prostu rejestrując klasy usługi klienta za pomocą `AddHttpClient()`, `HttpClient` obiekt, który zostanie dodany do swojej klasy użyje konfiguracji i zasad podany podczas rejestracji.</span><span class="sxs-lookup"><span data-stu-id="d26c5-146">Just by registering your client service class with `AddHttpClient()`, the `HttpClient` object that will be injected into your class will use the configuration and policies provided upon registration.</span></span> <span data-ttu-id="d26c5-147">W kolejnych sekcjach zobaczysz tych zasad, takich jak ponownych prób lub wyłączniki Polly firmy.</span><span class="sxs-lookup"><span data-stu-id="d26c5-147">In the next sections, you'll see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="d26c5-148">Okresy istnienia HttpClient</span><span class="sxs-lookup"><span data-stu-id="d26c5-148">HttpClient lifetimes</span></span>

<span data-ttu-id="d26c5-149">Zawsze możesz uzyskać `HttpClient` obiektu z `IHttpClientFactory`, zwracany jest nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d26c5-149">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="d26c5-150">Ale każdy `HttpClient` używa `HttpMessageHandler` który ma w puli i ponownie używane przez `IHttpClientFactory` można zmniejszać zużycie zasobów, tak długo, jak `HttpMessageHandler`firmy nie upłynął okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="d26c5-150">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="d26c5-151">Buforowanie obsługi jest pożądane, ponieważ każdy program obsługi zwykle zarządza własną podstawowego połączenia HTTP; Tworzenie więcej obsługi niż jest to konieczne może spowodować opóźnienia w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="d26c5-151">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="d26c5-152">Niektóre procedury obsługi również nie zamykaj połączeń przez czas nieokreślony, co może uniemożliwić obsługi reagowanie na zmiany DNS.</span><span class="sxs-lookup"><span data-stu-id="d26c5-152">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="d26c5-153">`HttpMessageHandler` Obiekty w puli mają okres istnienia, który jest czas, który `HttpMessageHandler` wystąpień w puli mogą być ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="d26c5-153">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="d26c5-154">Wartość domyślna to dwie minuty, ale może zostać przesłonięta na wpisane klienta.</span><span class="sxs-lookup"><span data-stu-id="d26c5-154">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="d26c5-155">Aby zastąpić go, należy wywołać `SetHandlerLifetime()` na `IHttpClientBuilder` , jest zwracana podczas tworzenia klienta, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="d26c5-155">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="d26c5-156">Każdy klient wpisane może mieć własną wartość okresu istnienia skonfigurowany program obsługi.</span><span class="sxs-lookup"><span data-stu-id="d26c5-156">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="d26c5-157">Ustaw okres istnienia `InfiniteTimeSpan` można wyłączyć obsługi wygaśnięcia.</span><span class="sxs-lookup"><span data-stu-id="d26c5-157">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="d26c5-158">Implementowanie klas klienta wpisana używających HttpClient wprowadzonego kodu i jest skonfigurowany</span><span class="sxs-lookup"><span data-stu-id="d26c5-158">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="d26c5-159">W poprzednim kroku musisz mieć Twoich zajęciach klienta wpisana zdefiniowane, takich jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itd. — klienta wpisana to klasa, która akceptuje `HttpClient` obiektu (wprowadzony przez jego Konstruktor) i używa go do wywołania niektórych zdalnej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="d26c5-159">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="d26c5-160">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d26c5-160">For example:</span></span>

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

<span data-ttu-id="d26c5-161">Klient wpisane (CatalogService w przykładzie) jest aktywowana za DI (iniekcji zależności), co oznacza może akceptować żadnych zarejestrowanej usługi w jego konstruktorze, oprócz HttpClient.</span><span class="sxs-lookup"><span data-stu-id="d26c5-161">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="d26c5-162">Wpisane klient jest, efektywnie, przejściowego obiektu, co oznacza, że nowe wystąpienie jest tworzone za każdym razem, jest ono wymagane i zostanie wyświetlony nowy `HttpClient` wystąpienia zawsze jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="d26c5-162">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="d26c5-163">Klasa HttpMessageHandler obiekty w puli są jednak obiekty, które są ponownie używane przez wiele żądań Http.</span><span class="sxs-lookup"><span data-stu-id="d26c5-163">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="d26c5-164">Użyj swojej klasy wpisane klienta</span><span class="sxs-lookup"><span data-stu-id="d26c5-164">Use your Typed Client classes</span></span>

<span data-ttu-id="d26c5-165">Na koniec po swojej klasy typów zaimplementowane i je zarejestrowane w usłudze AddHttpClient(), umożliwia dowolnym masz wstrzyknięte przez DI, na przykład w każdy kod strony Razor lub dowolny kontroler aplikacji internetowej MVC, podobnie jak w poniższym kodzie z usług ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="d26c5-165">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="d26c5-166">Do tej pory kod przedstawiony jest po prostu wykonując regularne żądań Http, ale "magii" jest dostępna w poniższych sekcjach, po prostu przez dodanie zasady i delegowanie obsługi zarejestrowanych klientom wpisane, żądania protokołu HTTP, wykonać `HttpClient` będzie zachowują się z uwzględnieniem odporne na błędy zasady kont, takich jak ponawiają próby z wykorzystaniem wykładniczego wycofywania, wyłączniki lub innych niestandardowych obsługi delegowania do zaimplementowania dodatkowe funkcje zabezpieczeń, takimi jak wymaganie użycia tokenów uwierzytelniania lub innych niestandardowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="d26c5-166">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="d26c5-167">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="d26c5-167">Additional resources</span></span>

- <span data-ttu-id="d26c5-168">**Za pomocą HttpClientFactory w programie .NET Core**\\</span><span class="sxs-lookup"><span data-stu-id="d26c5-168">**Using HttpClientFactory in .NET Core**\\</span></span>
  [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- <span data-ttu-id="d26c5-169">**Repozytorium HttpClientFactory GitHub**\\</span><span class="sxs-lookup"><span data-stu-id="d26c5-169">**HttpClientFactory GitHub repo**\\</span></span>
  [*https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory*](https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory)

>[!div class="step-by-step"]
><span data-ttu-id="d26c5-170">[Poprzednie](explore-custom-http-call-retries-exponential-backoff.md)
>[dalej](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="d26c5-170">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
