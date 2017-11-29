---
title: "Implementowanie ponawia próbę połączenia HTTP z wykładniczego wycofywania z Polly"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie ponawia próbę połączenia HTTP z wykładniczego wycofywania z Polly"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1ed48142546403ea710f4c132e038521232c20ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="df14c-104">Implementowanie ponawia próbę połączenia HTTP z wykładniczego wycofywania z Polly</span><span class="sxs-lookup"><span data-stu-id="df14c-104">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="df14c-105">Zalecane podejście do ponownych prób z wykładniczego wycofywania jest mógł korzystać z bardziej zaawansowanych bibliotek .NET, jak typu open source [Polly](https://github.com/App-vNext/Polly) biblioteki.</span><span class="sxs-lookup"><span data-stu-id="df14c-105">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="df14c-106">Polly jest biblioteki .NET, która zapewnia odporność i możliwości obsługi przejściowy błąd.</span><span class="sxs-lookup"><span data-stu-id="df14c-106">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="df14c-107">Te funkcje można zaimplementować łatwe, stosując zasady Polly, np. Ponów próbę, wyłącznika grodziowego izolacji, limit czasu i powrotu.</span><span class="sxs-lookup"><span data-stu-id="df14c-107">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="df14c-108">Polly jest przeznaczony dla platformy .NET 4.x i Standard .NET w wersji 1.0 (który obsługuje .NET Core).</span><span class="sxs-lookup"><span data-stu-id="df14c-108">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="df14c-109">Zasady ponawiania w Polly jest to rozwiązanie używane w eShopOnContainers podczas implementowania HTTP ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="df14c-109">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="df14c-110">Można zaimplementować interfejsu, więc można wstrzyknąć standardowych funkcji HttpClient lub refs wersji HttpClient przy użyciu Polly, w zależności od konfiguracji zasad ponawiania, z którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="df14c-110">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="df14c-111">W poniższym przykładzie przedstawiono interfejs implementowany w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="df14c-111">The following example shows the interface implemented in eShopOnContainers.</span></span>

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

<span data-ttu-id="df14c-112">Jeśli nie chcesz używać mechanizm odporność jako podczas tworzenia i testowania prostsze podejścia, można użyć standardowego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="df14c-112">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="df14c-113">Poniższy kod przedstawia standardowych żądań możliwość wykonania w HttpClient z tokenami uwierzytelniania w przypadku opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="df14c-113">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

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

<span data-ttu-id="df14c-114">Implementacja interesujące jest kodu klasy inny, podobny, ale przy użyciu Polly wdrożyć mechanizmy elastyczne, którego chcesz użyć — w poniższym przykładzie ponownych prób z wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="df14c-114">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

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

<span data-ttu-id="df14c-115">Korzystając z Polly można określić zasady ponawiania z liczbą ponownych prób, konfiguracji wykładniczego wycofywania i działania w sytuacji, gdy występuje wyjątek HTTP, takich jak rejestrowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="df14c-115">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="df14c-116">W takim przypadku zasada jest skonfigurowana tak spróbuje liczba powtórzeń podczas rejestrowania typów w kontenerze Inwersja kontroli.</span><span class="sxs-lookup"><span data-stu-id="df14c-116">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="df14c-117">Ze względu na konfigurację wykładniczego wycofywania zawsze, gdy kod wykrywa wyjątek HttpRequest ponowną żądania Http po odczekaniu ilość czasu, który znacznie zwiększa się w zależności od konfiguracji zasad.</span><span class="sxs-lookup"><span data-stu-id="df14c-117">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="df14c-118">Metody ważne jest HttpInvoker, czyli, co sprawia, że żądania HTTP przez tę klasę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="df14c-118">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="df14c-119">Czy metoda wewnętrznie wykonuje żądanie HTTP o \_policyWrapper.ExecuteAsync, który uwzględnia zasady ponawiania.</span><span class="sxs-lookup"><span data-stu-id="df14c-119">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="df14c-120">W eShopOnContainers należy określić zasady Polly, gdy rejestrowanie typów w kontenerze Inwersja kontroli, jak w poniższym kodzie z [aplikację sieci web MVC w pliku startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) klasy.</span><span class="sxs-lookup"><span data-stu-id="df14c-120">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

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

<span data-ttu-id="df14c-121">Należy pamiętać, obiekty IHttpClient wystąpienia są tworzone jako pojedyncze zamiast jako przejściowy, dzięki czemu połączeń TCP są wydajnie używane przez usługę i [problem z gniazda](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) nie nastąpi.</span><span class="sxs-lookup"><span data-stu-id="df14c-121">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="df14c-122">Jednak istotne dotyczące odporności jest stosowanie zasad Polly WaitAndRetryAsync w ResilientHttpClientFactory w metodzie CreateResilientHttpClient, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="df14c-122">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

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
<span data-ttu-id="df14c-123">[Poprzednie] (implement-custom-http-call-retries-exponential-backoff.md) [dalej] (wdrożenie obwodu-dzielącego wyrazy pattern.md)</span><span class="sxs-lookup"><span data-stu-id="df14c-123">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>
