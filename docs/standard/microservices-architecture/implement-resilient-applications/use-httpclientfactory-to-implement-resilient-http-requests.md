---
title: Użyj HttpClientFactory do zaimplementowania odporne na błędy żądań HTTP
description: HttpClientFactory to ceniona fabryki, dostępne od platformy .NET Core 2.1, do tworzenia `HttpClient` wystąpienia ma być używany w aplikacjach.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 0ae4dadd6921a71217b50757ede19b8d54910185
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611038"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="0c4ea-103">Użyj HttpClientFactory do zaimplementowania odporne na błędy żądań HTTP</span><span class="sxs-lookup"><span data-stu-id="0c4ea-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="0c4ea-104">`HttpClientFactory` to ceniona fabryki, dostępne od platformy .NET Core 2.1, do tworzenia `HttpClient` wystąpienia ma być używany w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating `HttpClient` instances to be used in your applications.</span></span> 

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="0c4ea-105">Problemy związane z oryginalnej klasy HttpClient dostępnych w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="0c4ea-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="0c4ea-106">Oryginalne i dobrze znane [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) klasy mogą być łatwo używane, ale w niektórych przypadkach go nie jest prawidłowo używany przez wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-106">The original and well-known [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it is not being properly used by many developers.</span></span> 

<span data-ttu-id="0c4ea-107">Jako pierwszego wydania tej klasy jest możliwe do rozporządzania, korzystania z niego przy użyciu `using` instrukcja nie jest najlepszym rozwiązaniem, ponieważ nawet wtedy, gdy użytkownik dispose `HttpClient` obiektu bazowego gniazda nie jest od razu zwolniony i może spowodować poważne zagrożenie o nazwie "gniazda wyczerpanie ".</span><span class="sxs-lookup"><span data-stu-id="0c4ea-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="0c4ea-108">Aby uzyskać więcej informacji na temat tego problemu, zobacz [używasz problem HttpClient i jest on destabilizing oprogramowania](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) wpis w blogu.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-108">For more information about this issue, see [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="0c4ea-109">W związku z tym `HttpClient` jest przeznaczony do jednorazowego utworzenia ich i ponownie używane w całym cyklu życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="0c4ea-110">Utworzenie wystąpienia `HttpClient` klasy dla każdego żądania będą wyczerpać liczbę gniazd, które są dostępne pod dużym obciążeniem.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="0c4ea-111">Czy problem spowoduje `SocketException` błędy.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="0c4ea-112">Możliwe sposoby rozwiązania tego problemu są oparte na tworzeniu `HttpClient` obiektu jako pojedyncze lub statyczna, zgodnie z opisem w tym [artykule firmy Microsoft dotyczących użycia HttpClient](https://docs.microsoft.com/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="0c4ea-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](https://docs.microsoft.com/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="0c4ea-113">Ale drugi problem ze `HttpClient` , może mieć w przypadku użycia jej jako pojedyncze lub obiektu statycznego.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="0c4ea-114">W tej sprawy, pojedyncze lub statyczna `HttpClient` zmian systemu DNS nie jest zgodny z zgodnie z opisem w tym [problemu w repozytorium .NET Core w usłudze GitHub](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="0c4ea-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="0c4ea-115">Do rozwiązania tych problemów wymienionych i zarządzania `HttpClient` przypadkach łatwiejsze platformy .NET Core 2.1 oferuje nową `HttpClientFactory` , można również zaimplementować odporne na błędy połączeń HTTP, integrując Polly z nim.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 offers a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="0c4ea-116">Co to jest HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="0c4ea-116">What is HttpClientFactory</span></span>

<span data-ttu-id="0c4ea-117">`HttpClientFactory` została zaprojektowana w celu:</span><span class="sxs-lookup"><span data-stu-id="0c4ea-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="0c4ea-118">Podaj centralną lokalizację do nazywania i konfigurowanie HttpClients logiczne.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="0c4ea-119">Na przykład może skonfigurować klienta (usługi agenta), który jest wstępnie skonfigurowana pod kątem dostępu do określonych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-119">For example, you may configure a client (Service Agent) that is pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="0c4ea-120">Skodyfikowanie koncepcji wychodzących oprogramowania pośredniczącego za pośrednictwem Delegowanie obsługi w `HttpClient` i wdrażanie na podstawie Polly oprogramowaniu pośredniczącym, aby korzystać z zasad firmy Polly pod kątem odporności.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="0c4ea-121">Klasa `HttpClient` ma już pojęcie delegowania programów obsługi, które można połączyć ze sobą dla wychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="0c4ea-122">Rejestrowanie klientów http do fabryki, a także można użyć procedury obsługi Polly, umożliwiająca Polly zasady służący do ponawiania, CircuitBreakers itp.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="0c4ea-123">Zarządzanie okresem istnienia HttpClientMessageHandlers, aby uniknąć wymienionych problemów/problemy, które mogą wystąpić podczas zarządzania `HttpClient` okresy istnienia samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="0c4ea-124">Wiele sposobów, aby użyć HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="0c4ea-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="0c4ea-125">Istnieje kilka metod, których można użyć `HttpClientFactory` w Twojej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="0c4ea-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="0c4ea-126">Użyj `HttpClientFactory` bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="0c4ea-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="0c4ea-127">Użyj o nazwie klientów</span><span class="sxs-lookup"><span data-stu-id="0c4ea-127">Use Named Clients</span></span>
- <span data-ttu-id="0c4ea-128">Korzystać z kontrolą typów klientów</span><span class="sxs-lookup"><span data-stu-id="0c4ea-128">Use Typed Clients</span></span>
- <span data-ttu-id="0c4ea-129">Użyj wygenerowanych klientów</span><span class="sxs-lookup"><span data-stu-id="0c4ea-129">Use Generated Clients</span></span>

<span data-ttu-id="0c4ea-130">W celu skrócenia wskazówki te przedstawiają najbardziej ze strukturą sposób używania `HttpClientFactory` to korzystać z kontrolą typów klientów (Agent usługi wzorzec), ale wszystkie opcje są udokumentowane i obecnie są wymienione w tym [artykułu obejmujących użycie HttpClientFactory ](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="0c4ea-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that is to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="0c4ea-131">Jak używać wpisane klientów z HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="0c4ea-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="0c4ea-132">Na poniższym diagramie przedstawiono, jak klienci z kontrolą typów są używane z HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-132">The following diagram shows how Typed Clients are used with HttpClientFactory.</span></span>

![Diagram z kontrolera MVC, za pomocą wprowadzonego ClientService używającą wewnętrznie HttpClient skonfigurowany przy użyciu zasad HttpClientFactory i jego Polly](./media/image3.5.png)

<span data-ttu-id="0c4ea-134">**Rysunek 10-4**.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-134">**Figure 10-4**.</span></span> <span data-ttu-id="0c4ea-135">Za pomocą `HttpClientFactory`z klasami wpisane klienta.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-135">Using `HttpClientFactory`with Typed Client classes.</span></span>

<span data-ttu-id="0c4ea-136">Najpierw należy skonfigurować `HttpClientFactory` w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-136">First, setup `HttpClientFactory` in your application.</span></span> <span data-ttu-id="0c4ea-137">Dodaj odwołanie do `Microsoft.Extensions.Http` pakiet, który zawiera `AddHttpClient()` metody rozszerzenia dla `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-137">Add a reference to the `Microsoft.Extensions.Http` package which includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="0c4ea-138">Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory` ma być używany jako pojedynczego interfejsu `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-138">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="0c4ea-139">Definiuje konfigurację przejściowy `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-139">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="0c4ea-140">Ten program obsługi komunikatów (`HttpMessageHandler` obiektu), to wykonana z puli, jest używany przez `HttpClient` zwrócony z fabryki.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-140">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="0c4ea-141">W następnym kodu, można zobaczyć jak `AddHttpClient()` może służyć do rejestrowania klientów wpisane (agenci usługi), które muszą korzystać `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-141">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="0c4ea-142">Po prostu dodając Twoich zajęciach klient z typowaniem z AddHttpClient(), zawsze, gdy używana `HttpClient` obiekt, który zostanie dodany do klasy za pośrednictwem jej konstruktora, który `HttpClient` obiektu będzie można korzystać ze wszystkich konfiguracji i zasady dostarczane.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-142">Just by adding your typed client classes with AddHttpClient(), whenever you use the `HttpClient` object that will be injected to your class through its constructor, that `HttpClient` object will be using all the configuration and policies provided.</span></span> <span data-ttu-id="0c4ea-143">W kolejnych sekcjach zobaczysz tych zasad, takich jak ponownych prób lub wyłączniki Polly firmy.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-143">In the next sections, you will see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="0c4ea-144">Okresy istnienia HttpClient</span><span class="sxs-lookup"><span data-stu-id="0c4ea-144">HttpClient lifetimes</span></span>

<span data-ttu-id="0c4ea-145">Zawsze możesz uzyskać `HttpClient` obiekt z IHttpClientFactory, nowe wystąpienie klasy `HttpClient` jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-145">Each time you get an `HttpClient` object from IHttpClientFactory, a new instance of an `HttpClient` is returned.</span></span> <span data-ttu-id="0c4ea-146">Będzie **klasa HttpMessageHandler** na o nazwie wpisane klienta.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-146">There will be an **HttpMessageHandler** per named of typed client.</span></span> <span data-ttu-id="0c4ea-147">`IHttpClientFactory` będzie puli wystąpień klasa HttpMessageHandler utworzone przez fabryki, aby zmniejszyć wykorzystanie zasobów.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-147">`IHttpClientFactory` will pool the HttpMessageHandler instances created by the factory to reduce resource consumption.</span></span> <span data-ttu-id="0c4ea-148">Klasa HttpMessageHandler wystąpienia może być ponownie używane z puli podczas tworzenia nowego `HttpClient` wystąpienia, jeśli nie upłynął jego okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-148">An HttpMessageHandler instance may be reused from the pool when creating a new `HttpClient` instance if its lifetime hasn't expired.</span></span>

<span data-ttu-id="0c4ea-149">Buforowanie obsługi jest pożądane, ponieważ każdy program obsługi zwykle zarządza własną podstawowego połączenia HTTP; Tworzenie więcej obsługi niż jest to konieczne może spowodować opóźnienia w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-149">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="0c4ea-150">Niektóre procedury obsługi również nie zamykaj połączeń przez czas nieokreślony, co może uniemożliwić obsługi reagowanie na zmiany DNS.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-150">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="0c4ea-151">Klasa HttpMessageHandler obiekty w puli mają okres istnienia to długość czasu, przez jaki wystąpienie klasa HttpMessageHandler w puli mogą być ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-151">The HttpMessageHandler objects in the pool have a lifetime that is the length of time that an HttpMessageHandler instance in the pool can be reused.</span></span> <span data-ttu-id="0c4ea-152">Wartość domyślna to dwie minuty, ale może zostać przesłonięta poszczególnych nazwany i typizowany klienta.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-152">The default value is two minutes, but it can be overridden per named or typed client basis.</span></span> <span data-ttu-id="0c4ea-153">Czy chcesz go zastąpić, należy wywołać SetHandlerLifetime() w IHttpClientBuilder, która jest zwracana podczas tworzenia klienta, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-153">To override it, call SetHandlerLifetime() on the IHttpClientBuilder that is returned when creating the client, as shown in the following code.</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="0c4ea-154">Każdy klient z typowaniem lub klient może mieć własną wartość okresu istnienia skonfigurowany program obsługi.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-154">Each typed client or named client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="0c4ea-155">Ustawianie okresu istnienia, aby InfiniteTimeSpan można wyłączyć obsługi wygaśnięcia.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-155">Set the lifetime to InfiniteTimeSpan to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="0c4ea-156">Implementowanie klas klienta wpisana używających HttpClient wprowadzonego kodu i jest skonfigurowany</span><span class="sxs-lookup"><span data-stu-id="0c4ea-156">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="0c4ea-157">W poprzednim kroku musisz mieć Twoich zajęciach klienta wpisana zdefiniowane, takich jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itd. — klient z typowaniem to klasa, która akceptuje `HttpClient` obiektu (wprowadzony przez jego Konstruktor) i używa go do wywołania niektórych zdalnej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-157">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A typed client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="0c4ea-158">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0c4ea-158">For example:</span></span>

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

<span data-ttu-id="0c4ea-159">Klient z typowaniem (CatalogService w przykładzie) jest aktywowana za DI (iniekcji zależności), co oznacza może akceptować żadnych zarejestrowanej usługi w jego konstruktorze, oprócz HttpClient.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-159">The typed client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="0c4ea-160">Klient z typowaniem jest, efektywnie, przejściowego obiektu, co oznacza, że nowe wystąpienie jest tworzone za każdym razem, jest ono wymagane i zostanie wyświetlony nowy `HttpClient` wystąpienia zawsze jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-160">A typed client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it is constructed.</span></span> <span data-ttu-id="0c4ea-161">Klasa HttpMessageHandler obiekty w puli są jednak obiekty, które są ponownie używane przez wiele żądań Http.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-161">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="0c4ea-162">Użyj swojej klasy wpisane klienta</span><span class="sxs-lookup"><span data-stu-id="0c4ea-162">Use your Typed Client classes</span></span>

<span data-ttu-id="0c4ea-163">Na koniec po swojej klasy typów zaimplementowane i je zarejestrowane w usłudze AddHttpClient(), umożliwia dowolnym masz wstrzyknięte przez DI, na przykład w każdy kod strony Razor lub dowolny kontroler aplikacji internetowej MVC, podobnie jak w poniższym kodzie z usług ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-163">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="0c4ea-164">Do tej pory kod przedstawiony jest po prostu wykonując regularne żądań Http, ale "magii" jest dostępna w poniższych sekcjach, w której, po prostu przez dodanie zasady i delegowanie obsługi do Twojego zarejestrowanego wpisany klientów, żądania protokołu Http odbywać się przy `HttpClient` będzie zachowują się z uwzględnieniem odporne na błędy zasady kont, takich jak ponawiają próby z wykorzystaniem wykładniczego wycofywania, wyłączniki lub innych niestandardowych obsługi delegowania do zaimplementowania dodatkowe funkcje zabezpieczeń, takimi jak wymaganie użycia tokenów uwierzytelniania lub innych niestandardowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="0c4ea-164">Until this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered typed clients, all the Http requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 


## <a name="additional-resources"></a><span data-ttu-id="0c4ea-165">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="0c4ea-165">Additional resources</span></span>

-   <span data-ttu-id="0c4ea-166">**Za pomocą HttpClientFactory w programie .NET Core 2.1**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)</span><span class="sxs-lookup"><span data-stu-id="0c4ea-166">**Using HttpClientFactory in .NET Core 2.1**
[*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)</span></span>


-   <span data-ttu-id="0c4ea-167">**Repozytorium HttpClientFactory GitHub**</span><span class="sxs-lookup"><span data-stu-id="0c4ea-167">**HttpClientFactory GitHub repo**</span></span>

    [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)

>[!div class="step-by-step"]
><span data-ttu-id="0c4ea-168">[Poprzednie](explore-custom-http-call-retries-exponential-backoff.md)
>[dalej](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="0c4ea-168">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
