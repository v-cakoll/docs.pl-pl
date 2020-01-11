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
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="cca89-103">Używanie elementu HttpClientFactory do implementowania odpornych na błędy żądań HTTP</span><span class="sxs-lookup"><span data-stu-id="cca89-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="cca89-104">`HttpClientFactory` jest fabryką ceniona, dostępną od platformy .NET Core 2,1 do tworzenia wystąpień <xref:System.Net.Http.HttpClient>, które mają być używane w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="cca89-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="cca89-105">Problemy z oryginalną klasą HttpClient dostępną w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="cca89-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="cca89-106">Oryginalna i dobrze znana Klasa <xref:System.Net.Http.HttpClient> może być łatwo używana, ale w niektórych przypadkach nie jest ona prawidłowo używana przez wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="cca89-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="cca89-107">Podczas pierwszego problemu, gdy ta klasa jest używana, używanie jej z instrukcją `using` nie jest najlepszym wyborem, ponieważ nawet w przypadku usuwania `HttpClient` obiektu, bazowe gniazdo nie zostanie natychmiast wydane i może spowodować poważny problem o nazwie "wyczerpania gniazd".</span><span class="sxs-lookup"><span data-stu-id="cca89-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="cca89-108">Aby uzyskać więcej informacji o tym problemie, zobacz, [czy używasz programu HttpCliente, i destabilizująco wpis w blogu na oprogramowanie](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) .</span><span class="sxs-lookup"><span data-stu-id="cca89-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="cca89-109">W związku z tym `HttpClient` jest przeznaczony do tworzenia wystąpień jednokrotnie i ponownie używane przez cały czas życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cca89-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="cca89-110">Utworzenie wystąpienia klasy `HttpClient` dla każdego żądania spowoduje wyczerpanie liczby gniazd dostępnych w ramach dużych obciążeń.</span><span class="sxs-lookup"><span data-stu-id="cca89-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="cca89-111">Ten problem spowoduje błędy `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="cca89-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="cca89-112">Możliwe podejścia do rozwiązania tego problemu opierają się na tworzeniu obiektu `HttpClient` jako singleton lub static, jak wyjaśniono w tym [artykule firmy Microsoft w sprawie użycia HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="cca89-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span>

<span data-ttu-id="cca89-113">Jednak występuje drugi problem z `HttpClient`, który można mieć, gdy jest używany jako obiekt pojedynczy lub statyczny.</span><span class="sxs-lookup"><span data-stu-id="cca89-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="cca89-114">W takim przypadku pojedyncze lub statyczne `HttpClient` nie respektują zmian DNS, jak wyjaśniono w tym [problemie](https://github.com/dotnet/corefx/issues/11224) w repozytorium GitHub/corefx.</span><span class="sxs-lookup"><span data-stu-id="cca89-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue](https://github.com/dotnet/corefx/issues/11224) at the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="cca89-115">Aby rozwiązać wspomniane problemy i ułatwić zarządzanie wystąpieniami `HttpClient`, w środowisku .NET Core 2,1 wprowadzono nowy `HttpClientFactory`, który może być również używany do implementowania odpornych wywołań HTTP przez integrację z nią Polly.</span><span class="sxs-lookup"><span data-stu-id="cca89-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>

<span data-ttu-id="cca89-116">[Polly](http://www.thepollyproject.org/) jest biblioteką obsługi błędów przejściowych, która ułatwia deweloperom Dodawanie odporności do aplikacji przy użyciu wstępnie zdefiniowanych zasad w sposób bezpieczny dla bezpieczeństwa i bezpiecznego wątkowo.</span><span class="sxs-lookup"><span data-stu-id="cca89-116">[Polly](http://www.thepollyproject.org/) is transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="cca89-117">Co to jest HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="cca89-117">What is HttpClientFactory</span></span>

<span data-ttu-id="cca89-118">`HttpClientFactory` jest zaprojektowana tak, aby:</span><span class="sxs-lookup"><span data-stu-id="cca89-118">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="cca89-119">Podaj centralną lokalizację do nazywania i konfigurowania obiektów `HttpClient` logicznych.</span><span class="sxs-lookup"><span data-stu-id="cca89-119">Provide a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="cca89-120">Można na przykład skonfigurować klienta (agenta usługi), który jest wstępnie skonfigurowany w celu uzyskania dostępu do konkretnej mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="cca89-120">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="cca89-121">Codify koncepcji wychodzącego oprogramowania pośredniczącego przez delegowanie programów obsługi w `HttpClient` i implementowanie oprogramowania pośredniczącego opartego na Pollyach, aby wykorzystać zasady dotyczące odporności Polly.</span><span class="sxs-lookup"><span data-stu-id="cca89-121">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="cca89-122">Klasa `HttpClient` ma już pojęcie delegowania programów obsługi, które można połączyć ze sobą dla wychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="cca89-122">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="cca89-123">Klienci HTTP są rejestrowani w fabryce i można użyć procedury obsługi Polly, aby używać zasad Polly do ponawiania, CircuitBreakers itd.</span><span class="sxs-lookup"><span data-stu-id="cca89-123">You register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="cca89-124">Zarządzaj okresem istnienia `HttpClientMessageHandlers`, aby uniknąć wspomnianych problemów i problemów, które mogą wystąpić podczas samodzielnego zarządzania `HttpClient` okresów istnienia.</span><span class="sxs-lookup"><span data-stu-id="cca89-124">Manage the lifetime of `HttpClientMessageHandlers` to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="cca89-125">`HttpClientFactory` jest ściśle powiązany z implementacją iniekcji zależności w pakiecie `Microsoft.Extensions.DependencyInjection` NuGet.</span><span class="sxs-lookup"><span data-stu-id="cca89-125">`HttpClientFactory` is tightly tied to the dependency injection (DI) implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="cca89-126">Aby uzyskać więcej informacji na temat korzystania z innych kontenerów iniekcji zależności, zobacz tę [dyskusję](https://github.com/dotnet/extensions/issues/1345)w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="cca89-126">For more information about using other dependency injection containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="cca89-127">Wiele sposobów używania HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="cca89-127">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="cca89-128">Istnieje kilka sposobów używania `HttpClientFactory` w aplikacji:</span><span class="sxs-lookup"><span data-stu-id="cca89-128">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="cca89-129">Użyj `HttpClientFactory` bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="cca89-129">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="cca89-130">Użyj nazwanych klientów</span><span class="sxs-lookup"><span data-stu-id="cca89-130">Use Named Clients</span></span>
- <span data-ttu-id="cca89-131">Używaj wpisanych klientów</span><span class="sxs-lookup"><span data-stu-id="cca89-131">Use Typed Clients</span></span>
- <span data-ttu-id="cca89-132">Korzystanie z wygenerowanych klientów</span><span class="sxs-lookup"><span data-stu-id="cca89-132">Use Generated Clients</span></span>

<span data-ttu-id="cca89-133">Ze względu na zwięzłości, te wskazówki przedstawiają najbardziej strukturalny sposób używania `HttpClientFactory`, który jest używany jako klienci z określonym typem (wzorzec agenta usługi).</span><span class="sxs-lookup"><span data-stu-id="cca89-133">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="cca89-134">Wszystkie opcje są jednak udokumentowane i są obecnie wymienione w tym [artykule dotyczące użycia HttpClientFactory](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="cca89-134">However, all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="cca89-135">Jak używać klientów z określonym programem HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="cca89-135">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="cca89-136">Co to jest "klient z określonym typem"?</span><span class="sxs-lookup"><span data-stu-id="cca89-136">So, what's a "Typed Client"?</span></span> <span data-ttu-id="cca89-137">Jest to tylko `HttpClient`, który jest konfigurowany podczas iniekcji przez `DefaultHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="cca89-137">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="cca89-138">Na poniższym diagramie pokazano, w jaki sposób typy klientów są używane z `HttpClientFactory`:</span><span class="sxs-lookup"><span data-stu-id="cca89-138">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![Diagram przedstawiający sposób używania z HttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="cca89-140">**Rysunek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="cca89-140">**Figure 8-4**.</span></span> <span data-ttu-id="cca89-141">Korzystanie z HttpClientFactory z klasami klienta z typem.</span><span class="sxs-lookup"><span data-stu-id="cca89-141">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="cca89-142">Na powyższym obrazie ClientService (używany przez kontroler lub kod klienta) używa `HttpClient` utworzonego przez zarejestrowany `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="cca89-142">In the above image, a ClientService (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="cca89-143">Ta fabryka przypisuje `HttpClient` `HttpMessageHandler` z puli, którą zarządza.</span><span class="sxs-lookup"><span data-stu-id="cca89-143">This factory assigns the `HttpClient` an `HttpMessageHandler` from a pool it manages.</span></span> <span data-ttu-id="cca89-144">`HttpClient` można skonfigurować przy użyciu zasad Polly podczas rejestrowania `IHttpClientFactory` w kontenerze DI z metodą rozszerzenia `AddHttpClient`.</span><span class="sxs-lookup"><span data-stu-id="cca89-144">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method `AddHttpClient`.</span></span>

<span data-ttu-id="cca89-145">Aby skonfigurować powyższą strukturę, Dodaj `HttpClientFactory` w aplikacji, instalując pakiet NuGet `Microsoft.Extensions.Http`, który zawiera metodę rozszerzenia `AddHttpClient()` dla `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="cca89-145">To configure the above structure, add `HttpClientFactory` in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="cca89-146">Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory`, które mają być używane jako pojedyncze dla `IHttpClientFactory`interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cca89-146">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="cca89-147">Definiuje ona przejściową konfigurację dla `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="cca89-147">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="cca89-148">Ten program obsługi komunikatów (`HttpMessageHandler` Object), pobrany z puli, jest używany przez `HttpClient` zwracaną z fabryki.</span><span class="sxs-lookup"><span data-stu-id="cca89-148">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="cca89-149">W następnym kodzie można zobaczyć, jak `AddHttpClient()` może służyć do rejestrowania klientów typu (agenci usługi), którzy muszą korzystać z `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="cca89-149">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="cca89-150">Zarejestrowanie usług klienta, jak pokazano w poprzednim kodzie, sprawia, że `DefaultClientFactory` utworzyć `HttpClient` standardowego dla każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="cca89-150">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="cca89-151">Można również dodać konfigurację specyficzną dla wystąpienia w ramach rejestracji do programu, na przykład skonfigurować adres podstawowy i dodać zasady odporności, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="cca89-151">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="cca89-152">Tylko w przypadku przykładu można zobaczyć jedną z powyższych zasad w następnym kodzie:</span><span class="sxs-lookup"><span data-stu-id="cca89-152">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="cca89-153">Więcej informacji o używaniu programu Polly można znaleźć w [następnym artykule](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="cca89-153">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="cca89-154">HttpClient okresy istnienia</span><span class="sxs-lookup"><span data-stu-id="cca89-154">HttpClient lifetimes</span></span>

<span data-ttu-id="cca89-155">Za każdym razem, gdy otrzymujesz obiekt `HttpClient` z `IHttpClientFactory`, zostanie zwrócone nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="cca89-155">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="cca89-156">Jednak każdy `HttpClient` używa `HttpMessageHandler`, który jest w puli i ponownie używany przez `IHttpClientFactory` w celu zmniejszenia zużycia zasobów, o ile okres istnienia `HttpMessageHandler`nie wygasł.</span><span class="sxs-lookup"><span data-stu-id="cca89-156">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="cca89-157">Buforowanie programów obsługi jest pożądane, ponieważ każdy program obsługi zazwyczaj zarządza własnymi połączeniami HTTP; Utworzenie większej liczby programów obsługi niż to konieczne może skutkować opóźnieniami połączeń.</span><span class="sxs-lookup"><span data-stu-id="cca89-157">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="cca89-158">Niektóre programy obsługi powodują również, że połączenia są otwarte w nieskończoność, co może uniemożliwić obsłużenie zmian DNS przez program obsługi.</span><span class="sxs-lookup"><span data-stu-id="cca89-158">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="cca89-159">`HttpMessageHandler` obiektów w puli ma okres istnienia równy czasowi, w którym można ponownie użyć wystąpienia `HttpMessageHandler` w puli.</span><span class="sxs-lookup"><span data-stu-id="cca89-159">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="cca89-160">Wartość domyślna to dwie minuty, ale można ją przesłonić dla poszczególnych klientów.</span><span class="sxs-lookup"><span data-stu-id="cca89-160">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="cca89-161">Aby zastąpić ten element, wywołaj `SetHandlerLifetime()` na `IHttpClientBuilder`, który jest zwracany podczas tworzenia klienta, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="cca89-161">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="cca89-162">Każdy klient z określonym typem może mieć własną skonfigurowaną wartość okresu istnienia programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="cca89-162">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="cca89-163">Ustaw okres istnienia `InfiniteTimeSpan`, aby wyłączyć procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="cca89-163">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="cca89-164">Zaimplementuj wpisane klasy klienta korzystające z wstrzykniętych i skonfigurowanych HttpClient</span><span class="sxs-lookup"><span data-stu-id="cca89-164">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="cca89-165">W poprzednim kroku należy określić zdefiniowane klasy klienta, takie jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itd. — typ klienta jest klasą akceptującą obiekt `HttpClient` (wstrzyknięty za pomocą jego konstruktora) i używa go do wywołania pewnej zdalnej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="cca89-165">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="cca89-166">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cca89-166">For example:</span></span>

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

<span data-ttu-id="cca89-167">Typ klienta (CatalogService w tym przykładzie) jest uaktywniany przez DI (iniekcja zależności), co oznacza, że może akceptować wszelkie zarejestrowane usługi w swoim konstruktorze, oprócz HttpClient.</span><span class="sxs-lookup"><span data-stu-id="cca89-167">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="cca89-168">Klient z określonym typem to, efektywnie, obiekt przejściowy, co oznacza, że nowe wystąpienie jest tworzone za każdym razem, gdy jest to konieczne, i otrzyma nowe wystąpienie `HttpClient` za każdym razem, gdy zostanie ono skonstruowane.</span><span class="sxs-lookup"><span data-stu-id="cca89-168">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="cca89-169">Jednak obiekty HttpMessageHandler w puli są obiektami, które są ponownie używane przez wiele żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="cca89-169">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="cca89-170">Korzystanie z wpisanych klas klienta</span><span class="sxs-lookup"><span data-stu-id="cca89-170">Use your Typed Client classes</span></span>

<span data-ttu-id="cca89-171">Na koniec po zaimplementowaniu klas wpisanych i zarejestrowaniu ich przy użyciu `AddHttpClient()`można ich używać wszędzie tam, gdzie można korzystać z usług wstrzykiwanych przez DI.</span><span class="sxs-lookup"><span data-stu-id="cca89-171">Finally, once you have your typed classes implemented and have them registered with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="cca89-172">Na przykład w kodzie lub kontrolerze strony Razor w aplikacji sieci Web MVC, jak w poniższym kodzie z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="cca89-172">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="cca89-173">Do tego momentu pokazany kod właśnie wykonuje zwykłe żądania HTTP, ale "Magic" znajduje się w następujących sekcjach, gdzie, bezpośrednio przez dodanie zasad i delegowanie programów obsługi do zarejestrowanych klientów z określonym typem, wszystkie żądania HTTP, które mają zostać wykonane przez `HttpClient` będą zachowywać się w celu uwzględnienia odpornych zasad, takich jak ponowne próby z użyciem wykładniczych wycofywania, wyłączników lub innych niestandardowych funkcji delegowania do implementowania dodatkowych funkcji zabezpieczeń, takich jak tokeny uwierzytelniania lub jakakolwiek inna funkcja niestandardowa.</span><span class="sxs-lookup"><span data-stu-id="cca89-173">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cca89-174">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="cca89-174">Additional resources</span></span>

- <span data-ttu-id="cca89-175">**Używanie HttpClientFactory w programie .NET Core**</span><span class="sxs-lookup"><span data-stu-id="cca89-175">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="cca89-176">**Kod źródłowy HttpClientFactory w repozytorium GitHub `dotnet/extensions`**</span><span class="sxs-lookup"><span data-stu-id="cca89-176">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="cca89-177">**Polly (odporność platformy .NET i Biblioteka obsługi błędów przejściowych)**</span><span class="sxs-lookup"><span data-stu-id="cca89-177">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="cca89-178">**Korzystanie z HttpClientFactory bez iniekcji zależności (problem z usługą GitHub)**</span><span class="sxs-lookup"><span data-stu-id="cca89-178">**Using HttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="cca89-179">[Poprzedni](explore-custom-http-call-retries-exponential-backoff.md)
>[Następny](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="cca89-179">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
