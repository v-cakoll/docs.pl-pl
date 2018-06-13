---
title: Implementowanie ponawia próbę połączenia HTTP z wykładniczego wycofywania z Polly
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie ponawia próbę połączenia HTTP z wykładniczego wycofywania z Polly
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 66ac57fc824e01f96d6584ab86bb95ba1b0174a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576984"
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="bfcb4-103">Implementowanie ponawia próbę połączenia HTTP z wykładniczego wycofywania z Polly</span><span class="sxs-lookup"><span data-stu-id="bfcb4-103">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="bfcb4-104">Zalecane podejście do ponownych prób z wykładniczego wycofywania jest mógł korzystać z bardziej zaawansowanych bibliotek .NET, jak typu open source [Polly](https://github.com/App-vNext/Polly) biblioteki.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="bfcb4-105">Polly jest biblioteki .NET, która zapewnia odporność i możliwości obsługi przejściowy błąd.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="bfcb4-106">Te funkcje można zaimplementować łatwe, stosując zasady Polly, np. Ponów próbę, wyłącznika grodziowego izolacji, limit czasu i powrotu.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-106">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="bfcb4-107">Polly jest przeznaczony dla platformy .NET 4.x i Standard .NET w wersji 1.0 (który obsługuje .NET Core).</span><span class="sxs-lookup"><span data-stu-id="bfcb4-107">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="bfcb4-108">Zasady ponawiania w Polly jest to rozwiązanie używane w eShopOnContainers podczas implementowania HTTP ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-108">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="bfcb4-109">Można zaimplementować interfejsu, więc można wstrzyknąć standardowych funkcji HttpClient lub refs wersji HttpClient przy użyciu Polly, w zależności od konfiguracji zasad ponawiania, z którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-109">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="bfcb4-110">W poniższym przykładzie przedstawiono interfejs implementowany w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-110">The following example shows the interface implemented in eShopOnContainers.</span></span>

```csharp
public interface IHttpClient
{
    Task<string> GetStringAsync(string uri, string authorizationToken = null,
        string authorizationMethod = "Bearer");
        Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    Task<HttpResponseMessage> DeleteAsync(string uri,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    // Other methods ...
}
```

<span data-ttu-id="bfcb4-111">Jeśli nie chcesz używać mechanizm odporność jako podczas tworzenia i testowania prostsze podejścia, można użyć standardowego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-111">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="bfcb4-112">Poniższy kod przedstawia standardowych żądań możliwość wykonania w HttpClient z tokenami uwierzytelniania w przypadku opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-112">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

```csharp
public class StandardHttpClient : IHttpClient
{
    private HttpClient _client;
    private ILogger<StandardHttpClient> _logger;

    public StandardHttpClient(ILogger<StandardHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
    }

    public async Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
        if (authorizationToken != null)
        {
            requestMessage.Headers.Authorization =
                new AuthenticationHeaderValue(authorizationMethod, authorizationToken);
        }
        var response = await _client.SendAsync(requestMessage);
        return await response.Content.ReadAsStringAsync();
    }

    public async Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer")
    {
        // Rest of the code and other Http methods ...
```

<span data-ttu-id="bfcb4-113">Implementacja interesujące jest kodu klasy inny, podobny, ale przy użyciu Polly wdrożyć mechanizmy elastyczne, którego chcesz użyć — w poniższym przykładzie ponownych prób z wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-113">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

```csharp
public class ResilientHttpClient : IHttpClient
{
    private HttpClient _client;
    private PolicyWrap _policyWrapper;
    private ILogger<ResilientHttpClient> _logger;

    public ResilientHttpClient(Policy[] policies,
        ILogger<ResilientHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
        // Add Policies to be applied
        _policyWrapper = Policy.WrapAsync(policies);
    }

    private Task<T> HttpInvoker<T>(Func<Task<T>> action)
    {
        // Executes the action applying all
        // the policies defined in the wrapper
        return _policyWrapper.ExecuteAsync(() => action());
    }

    public Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        return HttpInvoker(async () =>
        {
            var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
            // The Token's related code eliminated for clarity in code snippet
            var response = await _client.SendAsync(requestMessage);
            return await response.Content.ReadAsStringAsync();
        });
    }
    // Other Http methods executed through HttpInvoker so it applies Polly policies
    // ...
}
```

<span data-ttu-id="bfcb4-114">Korzystając z Polly można określić zasady ponawiania z liczbą ponownych prób, konfiguracji wykładniczego wycofywania i działania w sytuacji, gdy występuje wyjątek HTTP, takich jak rejestrowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-114">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="bfcb4-115">W takim przypadku zasada jest skonfigurowana tak spróbuje liczba powtórzeń podczas rejestrowania typów w kontenerze Inwersja kontroli.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-115">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="bfcb4-116">Ze względu na konfigurację wykładniczego wycofywania zawsze, gdy kod wykrywa wyjątek HttpRequest ponowną żądania Http po odczekaniu ilość czasu, który znacznie zwiększa się w zależności od konfiguracji zasad.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-116">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="bfcb4-117">Metody ważne jest HttpInvoker, czyli, co sprawia, że żądania HTTP przez tę klasę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-117">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="bfcb4-118">Czy metoda wewnętrznie wykonuje żądanie HTTP o \_policyWrapper.ExecuteAsync, który uwzględnia zasady ponawiania.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-118">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="bfcb4-119">W eShopOnContainers należy określić zasady Polly, gdy rejestrowanie typów w kontenerze Inwersja kontroli, jak w poniższym kodzie z [aplikację sieci web MVC w pliku startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) klasy.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-119">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

```csharp
// Startup.cs class
if (Configuration.GetValue<string>("UseResilientHttp") == bool.TrueString)
{
    services.AddTransient<IResilientHttpClientFactory,
        ResilientHttpClientFactory>();
    services.AddSingleton<IHttpClient,
        ResilientHttpClient>(sp =>
            sp.GetService<IResilientHttpClientFactory>().
            CreateResilientHttpClient());
}
else
{
    services.AddSingleton<IHttpClient, StandardHttpClient>();
}
```

<span data-ttu-id="bfcb4-120">Należy pamiętać, obiekty IHttpClient wystąpienia są tworzone jako pojedyncze zamiast jako przejściowy, dzięki czemu połączeń TCP są wydajnie używane przez usługę i [problem z gniazda](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) nie nastąpi.</span><span class="sxs-lookup"><span data-stu-id="bfcb4-120">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="bfcb4-121">Jednak istotne dotyczące odporności jest stosowanie zasad Polly WaitAndRetryAsync w ResilientHttpClientFactory w metodzie CreateResilientHttpClient, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bfcb4-121">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

// Other code
private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
        // number of retries
        6,
        // exponential backoff
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
        // on retry
        (exception, timeSpan, retryCount, context) =>
        {
            var msg = $"Retry {retryCount} implemented with Pollys RetryPolicy " +
            $"of {context.PolicyKey} " +
            $"at {context.ExecutionKey}, " +
            $"due to: {exception}.";
            _logger.LogWarning(msg);
            _logger.LogDebug(msg);
        }),
    }
```


>[!div class="step-by-step"]
<span data-ttu-id="bfcb4-122">[Poprzednie] (implement-custom-http-call-retries-exponential-backoff.md) [dalej] (wdrożenie obwodu-dzielącego wyrazy pattern.md)</span><span class="sxs-lookup"><span data-stu-id="bfcb4-122">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>
