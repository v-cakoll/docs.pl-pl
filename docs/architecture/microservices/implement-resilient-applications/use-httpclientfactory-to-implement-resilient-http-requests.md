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
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="281ce-103">Zaimplementowanie odpornych żądań HTTP za pomocą iHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="281ce-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="281ce-104"><xref:System.Net.Http.IHttpClientFactory>jest kontraktem wdrożonym przez `DefaultHttpClientFactory`, uparty fabryki, dostępne od .NET <xref:System.Net.Http.HttpClient> Core 2.1, do tworzenia wystąpień, które mają być używane w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="281ce-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="281ce-105">Problemy z oryginalną klasą HttpClient dostępną w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="281ce-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="281ce-106">Oryginalna i dobrze <xref:System.Net.Http.HttpClient> znana klasa może być łatwo używana, ale w niektórych przypadkach nie jest właściwie używana przez wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="281ce-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="281ce-107">Podczas gdy ta `IDisposable`klasa implementuje , deklarowanie `using` i tworzenie wystąpienia w `HttpClient` instrukcji nie jest preferowane, ponieważ gdy obiekt zostanie usunięty, podstawowe gniazdo nie jest natychmiast zwalniany, co może prowadzić do problemu _wyczerpania gniazda._</span><span class="sxs-lookup"><span data-stu-id="281ce-107">While this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="281ce-108">Aby uzyskać więcej informacji na temat tego problemu, zobacz wpis w blogu [Używasz HttpClient źle i destabilizuje oprogramowanie](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="281ce-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="281ce-109">W `HttpClient` związku z tym, jest przeznaczony do wystąpienia raz i ponownie przez cały okres trwania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="281ce-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="281ce-110">Wystąpienie `HttpClient` klasy dla każdego żądania wyczerpie liczbę gniazd dostępnych przy dużych obciążeniach.</span><span class="sxs-lookup"><span data-stu-id="281ce-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="281ce-111">Ten problem spowoduje `SocketException` błędy.</span><span class="sxs-lookup"><span data-stu-id="281ce-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="281ce-112">Możliwe podejścia do rozwiązania tego problemu są `HttpClient` oparte na tworzeniu obiektu jako singleton lub statyczne, jak wyjaśniono w tym [artykule firmy Microsoft na httpclient użytkowania](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="281ce-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="281ce-113">Może to być dobre rozwiązanie dla krótkotrwałych aplikacji konsoli lub podobnych, które są uruchamiane kilka razy dziennie.</span><span class="sxs-lookup"><span data-stu-id="281ce-113">This can be a good solution for short-lived console apps or similar that are run a few times a day.</span></span>

<span data-ttu-id="281ce-114">Innym problemem, który deweloperzy uruchomić jest `HttpClient` podczas korzystania z udostępnionego wystąpienia w długotrwałych procesów.</span><span class="sxs-lookup"><span data-stu-id="281ce-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long running processes.</span></span> <span data-ttu-id="281ce-115">W sytuacji, gdy HttpClient jest tworzony jako pojedynczy lub obiekt statyczny, nie może obsłużyć zmiany DNS, jak opisano w tym [wydaniu](https://github.com/dotnet/corefx/issues/11224) repozytorium Github dotnet/corefx.</span><span class="sxs-lookup"><span data-stu-id="281ce-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/corefx/issues/11224) of the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="281ce-116">Jednak problem nie jest tak `HttpClient` naprawdę z per se, ale z [domyślnym konstruktorem dla HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), ponieważ tworzy nowe konkretne wystąpienie <xref:System.Net.Http.HttpMessageHandler>, który jest ten, który ma *wyczerpanie gniazd* i DNS zmiany problemów wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="281ce-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="281ce-117">Aby rozwiązać powyższe problemy i `HttpClient` ułatwić zarządzanie wystąpieniami, program .NET <xref:System.Net.Http.IHttpClientFactory> Core 2.1 wprowadził `HttpClient` interfejs, który może służyć do konfigurowania i tworzenia wystąpień w aplikacji za pomocą wstrzykiwania zależności (DI).</span><span class="sxs-lookup"><span data-stu-id="281ce-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="281ce-118">Udostępnia również rozszerzenia dla polly oparte pośredniczenia, aby skorzystać z delegowania programów obsługi w HttpClient.</span><span class="sxs-lookup"><span data-stu-id="281ce-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="281ce-119">[Polly](http://www.thepollyproject.org/) jest biblioteki obsługi błędów przejściowych, który pomaga deweloperom dodać odporność do swoich aplikacji, przy użyciu niektórych wstępnie zdefiniowanych zasad w sposób płynny i bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="281ce-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="281ce-120">Zalety korzystania z iHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="281ce-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="281ce-121">Obecne wdrożenie <xref:System.Net.Http.IHttpClientFactory>, który również <xref:System.Net.Http.IHttpMessageHandlerFactory>wdraża, oferuje następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="281ce-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="281ce-122">Zapewnia centralną lokalizację nazewnictwa i `HttpClient` konfigurowania obiektów logicznych.</span><span class="sxs-lookup"><span data-stu-id="281ce-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="281ce-123">Na przykład można skonfigurować klienta (agenta usługi), który jest wstępnie skonfigurowany do uzyskiwania dostępu do określonej mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="281ce-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="281ce-124">Kodyfikuj koncepcję wychodzącego środka pośredniczącego `HttpClient` poprzez delegowanie programów obsługi i wdrażanie pośrednień opartych na Polly, aby skorzystać z zasad Polly w zakresie odporności.</span><span class="sxs-lookup"><span data-stu-id="281ce-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="281ce-125">`HttpClient`ma już pojęcie delegowania programów obsługi, które mogą być połączone ze sobą dla wychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="281ce-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="281ce-126">Klientów HTTP można zarejestrować w fabryce i można użyć polly obsługi do korzystania z zasad Polly dla Ponów, CircuitBreakers i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="281ce-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="281ce-127">Zarządzaj okresem istnienia, <xref:System.Net.Http.HttpMessageHandler> aby uniknąć wymienionych problemów/problemów, które mogą wystąpić podczas samodzielnego zarządzania `HttpClient` okresami istnienia.</span><span class="sxs-lookup"><span data-stu-id="281ce-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="281ce-128">Wystąpienia `HttpClient` wstrzykiwane przez DI, można bezpiecznie usunąć, ponieważ `HttpMessageHandler` skojarzone jest zarządzane przez fabrykę.</span><span class="sxs-lookup"><span data-stu-id="281ce-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="281ce-129">W rzeczywistości wstrzykuje wystąpienia `HttpClient` są *Scoped* z punktu widzenia DI.</span><span class="sxs-lookup"><span data-stu-id="281ce-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="281ce-130">Implementacja `IHttpClientFactory` (`DefaultHttpClientFactory`) jest ściśle powiązana z `Microsoft.Extensions.DependencyInjection` implementacją DI w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="281ce-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="281ce-131">Aby uzyskać więcej informacji na temat korzystania z innych kontenerów DI, zobacz tę [dyskusję github](https://github.com/dotnet/extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="281ce-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="281ce-132">Wiele sposobów używania iHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="281ce-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="281ce-133">Istnieje kilka sposobów, których `IHttpClientFactory` można użyć w aplikacji:</span><span class="sxs-lookup"><span data-stu-id="281ce-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="281ce-134">Podstawowy sposób użycia</span><span class="sxs-lookup"><span data-stu-id="281ce-134">Basic usage</span></span>
- <span data-ttu-id="281ce-135">Korzystanie z nazwanych klientów</span><span class="sxs-lookup"><span data-stu-id="281ce-135">Use Named Clients</span></span>
- <span data-ttu-id="281ce-136">Korzystanie z klientów wpisywanych</span><span class="sxs-lookup"><span data-stu-id="281ce-136">Use Typed Clients</span></span>
- <span data-ttu-id="281ce-137">Korzystanie z wygenerowanych klientów</span><span class="sxs-lookup"><span data-stu-id="281ce-137">Use Generated Clients</span></span>

<span data-ttu-id="281ce-138">Ze względu na zwięzłość, niniejsze wskazówki `IHttpClientFactory`pokazuje najbardziej zorganizowany sposób użycia , który jest użycie klientów wpisanych (wzorzec agenta usługi).</span><span class="sxs-lookup"><span data-stu-id="281ce-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="281ce-139">Jednak wszystkie opcje są udokumentowane i są obecnie wymienione w tym [artykule obejmującym `IHttpClientFactory` użycie](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="281ce-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="281ce-140">Jak używać klientów wpisywanych z iHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="281ce-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="281ce-141">Więc, co to jest "Wpisany klient"?</span><span class="sxs-lookup"><span data-stu-id="281ce-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="281ce-142">To `HttpClient` tylko, że jest wstępnie skonfigurowany do określonego użytku.</span><span class="sxs-lookup"><span data-stu-id="281ce-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="281ce-143">Ta konfiguracja może zawierać określone wartości, takie jak serwer podstawowy, nagłówki HTTP lub out czasu.</span><span class="sxs-lookup"><span data-stu-id="281ce-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="281ce-144">Na poniższym diagramie pokazano, `IHttpClientFactory`jak klienci maszynowi są używane z:</span><span class="sxs-lookup"><span data-stu-id="281ce-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![Diagram przedstawiający sposób pisania klientów są używane z IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="281ce-146">**Rysunek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="281ce-146">**Figure 8-4**.</span></span> <span data-ttu-id="281ce-147">Korzystanie `IHttpClientFactory` z wpisanych klas klienta.</span><span class="sxs-lookup"><span data-stu-id="281ce-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="281ce-148">Na powyższym obrazie `ClientService` (używany przez kontroler lub `HttpClient` kod klienta) `IHttpClientFactory`używa utworzonego przez zarejestrowanego .</span><span class="sxs-lookup"><span data-stu-id="281ce-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="281ce-149">Ta fabryka `HttpMessageHandler` przypisuje z puli `HttpClient`do pliku .</span><span class="sxs-lookup"><span data-stu-id="281ce-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="281ce-150">Można `HttpClient` skonfigurować za pomocą zasad Polly podczas `IHttpClientFactory` rejestrowania w kontenerze DI za pomocą metody <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>rozszerzenia .</span><span class="sxs-lookup"><span data-stu-id="281ce-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>.</span></span>

<span data-ttu-id="281ce-151">Aby skonfigurować powyższą <xref:System.Net.Http.IHttpClientFactory> strukturę, dodaj w `Microsoft.Extensions.Http` aplikacji, instalując pakiet NuGet, który zawiera metodę <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> rozszerzenia dla programu <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span><span class="sxs-lookup"><span data-stu-id="281ce-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="281ce-152">Ta metoda rozszerzenia rejestruje `DefaultHttpClientFactory` wewnętrzną klasę, która ma `IHttpClientFactory`być używana jako pojedynczy ton dla interfejsu .</span><span class="sxs-lookup"><span data-stu-id="281ce-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="281ce-153">Definiuje konfigurację przejściową dla <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>pliku .</span><span class="sxs-lookup"><span data-stu-id="281ce-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="281ce-154">Ten program<xref:System.Net.Http.HttpMessageHandler> obsługi komunikatów (obiekt), zaczerpnięte `HttpClient` z puli, jest używany przez zwrócone z fabryki.</span><span class="sxs-lookup"><span data-stu-id="281ce-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="281ce-155">W następnym kodzie można `AddHttpClient()` zobaczyć, jak można zarejestrować klientów wpisywanych `HttpClient`(agentów usług), które muszą być używane .</span><span class="sxs-lookup"><span data-stu-id="281ce-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="281ce-156">Rejestrowanie usług klienta, jak pokazano w `DefaultClientFactory` poprzednim `HttpClient` kodzie, tworzy standard dla każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="281ce-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="281ce-157">Można również dodać konfigurację specyficzne dla wystąpienia w rejestracji, na przykład skonfigurować adres podstawowy i dodać niektóre zasady odporności, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="281ce-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="281ce-158">Tylko dla przykładu, można zobaczyć jedną z powyższych zasad w następnym kodzie:</span><span class="sxs-lookup"><span data-stu-id="281ce-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="281ce-159">Więcej szczegółów na temat korzystania z Polly można znaleźć w [następnym artykule](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="281ce-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="281ce-160">Okresy istnienia klienta http</span><span class="sxs-lookup"><span data-stu-id="281ce-160">HttpClient lifetimes</span></span>

<span data-ttu-id="281ce-161">Za każdym razem, gdy otrzymasz obiekt `HttpClient` z `IHttpClientFactory`, zwracane jest nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="281ce-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="281ce-162">Ale `HttpClient` każdy `HttpMessageHandler` używa, który jest w puli `IHttpClientFactory` i ponownie wykorzystywane przez `HttpMessageHandler`w celu zmniejszenia zużycia zasobów, tak długo, jak okres istnienia nie wygasł.</span><span class="sxs-lookup"><span data-stu-id="281ce-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="281ce-163">Buforowanie programów obsługi jest pożądane, ponieważ każdy program obsługi zazwyczaj zarządza własnymi podstawowymi połączeniami HTTP; tworzenie większej liczby programów obsługi niż jest to konieczne może spowodować opóźnienia połączenia.</span><span class="sxs-lookup"><span data-stu-id="281ce-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="281ce-164">Niektóre programy obsługi również zachować połączenia otwarte przez czas nieokreślony, co może uniemożliwić programowi obsługi reagowanie na zmiany DNS.</span><span class="sxs-lookup"><span data-stu-id="281ce-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="281ce-165">Obiekty `HttpMessageHandler` w puli mają okres istnienia, który jest `HttpMessageHandler` czas, który wystąpienie w puli mogą być ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="281ce-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="281ce-166">Wartość domyślna wynosi dwie minuty, ale można ją zastąpić na klienta wpisana.</span><span class="sxs-lookup"><span data-stu-id="281ce-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="281ce-167">Aby go zastąpić, `SetHandlerLifetime()` wywołaj, <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> który jest zwracany podczas tworzenia klienta, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="281ce-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="281ce-168">Każdy wpisany klient może mieć własną skonfigurowaną wartość okresu istnienia programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="281ce-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="281ce-169">Ustaw okres `InfiniteTimeSpan` istnienia, aby wyłączyć wygaśnięcie programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="281ce-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="281ce-170">Implementowanie klas klienta wpisanych, które używają wstrzykuje i skonfigurowany HttpClient</span><span class="sxs-lookup"><span data-stu-id="281ce-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="281ce-171">W poprzednim kroku należy zdefiniować klasy klienta wpisane, takie jak klasy w przykładowym kodzie, takie jak "BasketService", "CatalogService", "OrderingService" itp. `HttpClient`</span><span class="sxs-lookup"><span data-stu-id="281ce-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="281ce-172">Przykład:</span><span class="sxs-lookup"><span data-stu-id="281ce-172">For example:</span></span>

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

<span data-ttu-id="281ce-173">Wpisany klient`CatalogService` (w przykładzie) jest aktywowany przez DI (Dependency Injection), co oznacza, że może `HttpClient`akceptować dowolną zarejestrowaną usługę w swoim konstruktorze, oprócz .</span><span class="sxs-lookup"><span data-stu-id="281ce-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="281ce-174">Klienta wpisanego jest, skutecznie, obiekt przejściowy, co oznacza, że nowe wystąpienie jest tworzony za `HttpClient` każdym razem, gdy jest potrzebne i otrzyma nowe wystąpienie za każdym razem, gdy jest skonstruowany.</span><span class="sxs-lookup"><span data-stu-id="281ce-174">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="281ce-175">Jednak `HttpMessageHandler` obiekty w puli są obiekty, które są `HttpClient` ponownie używane przez wiele wystąpień.</span><span class="sxs-lookup"><span data-stu-id="281ce-175">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="281ce-176">Korzystanie z klas klienta wpisanych</span><span class="sxs-lookup"><span data-stu-id="281ce-176">Use your Typed Client classes</span></span>

<span data-ttu-id="281ce-177">Na koniec po zaimplementowaniu klas wpisanych i zarejestrowaniu ich i skonfigurowaniu `AddHttpClient()`z nimi, można ich używać wszędzie tam, gdzie można mieć usługi wstrzykiwane przez DI.</span><span class="sxs-lookup"><span data-stu-id="281ce-177">Finally, once you have your typed classes implemented and have them registered and configured with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="281ce-178">Na przykład w kod strony Razor lub kontroler aplikacji sieci Web MVC, jak w następującym kodzie z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="281ce-178">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="281ce-179">Do tego momentu wyświetlany kod jest po prostu wykonywanie regularnych żądań Http, ale "magia" jest w następujących sekcjach, gdzie po prostu dodając `HttpClient` zasady i delegowanie programów obsługi do zarejestrowanych klientów wpisywanych, wszystkie żądania HTTP do wykonania przez będzie zachowywać się z uwzględnieniem odpornych zasad, takich jak ponownych prób z wykładniczego wycofywania, wyłączniki lub inne niestandardowe programy obsługi delegating do zaimplementowania dodatkowych funkcji zabezpieczeń, takich jak przy użyciu tokenów auth lub innych funkcji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="281ce-179">Up to this point, the code shown is just performing regular Http requests, but the 'magic' comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="281ce-180">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="281ce-180">Additional resources</span></span>

- <span data-ttu-id="281ce-181">**Korzystanie z httpclientfactory w programie .NET Core**</span><span class="sxs-lookup"><span data-stu-id="281ce-181">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="281ce-182">**HttpClientFactory kod źródłowy w `dotnet/extensions` repozytorium GitHub**</span><span class="sxs-lookup"><span data-stu-id="281ce-182">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="281ce-183">**Polly (odporność.NET i biblioteka obsługi błędów przejściowych)**</span><span class="sxs-lookup"><span data-stu-id="281ce-183">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="281ce-184">**Przy użyciu IHttpClientFactory bez iniekcji zależności (problem gitHub)**</span><span class="sxs-lookup"><span data-stu-id="281ce-184">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="281ce-185">[Poprzedni](implement-resilient-entity-framework-core-sql-connections.md)
>[następny](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="281ce-185">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
