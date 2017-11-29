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
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>Implementowanie ponawia próbę połączenia HTTP z wykładniczego wycofywania z Polly

Zalecane podejście do ponownych prób z wykładniczego wycofywania jest mógł korzystać z bardziej zaawansowanych bibliotek .NET, jak typu open source [Polly](https://github.com/App-vNext/Polly) biblioteki.

Polly jest biblioteki .NET, która zapewnia odporność i możliwości obsługi przejściowy błąd. Te funkcje można zaimplementować łatwe, stosując zasady Polly, np. Ponów próbę, wyłącznika grodziowego izolacji, limit czasu i powrotu. Polly jest przeznaczony dla platformy .NET 4.x i Standard .NET w wersji 1.0 (który obsługuje .NET Core).

Zasady ponawiania w Polly jest to rozwiązanie używane w eShopOnContainers podczas implementowania HTTP ponownych prób. Można zaimplementować interfejsu, więc można wstrzyknąć standardowych funkcji HttpClient lub refs wersji HttpClient przy użyciu Polly, w zależności od konfiguracji zasad ponawiania, z którego chcesz użyć.

W poniższym przykładzie przedstawiono interfejs implementowany w eShopOnContainers.

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

Jeśli nie chcesz używać mechanizm odporność jako podczas tworzenia i testowania prostsze podejścia, można użyć standardowego wdrożenia. Poniższy kod przedstawia standardowych żądań możliwość wykonania w HttpClient z tokenami uwierzytelniania w przypadku opcjonalne.

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

Implementacja interesujące jest kodu klasy inny, podobny, ale przy użyciu Polly wdrożyć mechanizmy elastyczne, którego chcesz użyć — w poniższym przykładzie ponownych prób z wykładniczego wycofywania.

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

Korzystając z Polly można określić zasady ponawiania z liczbą ponownych prób, konfiguracji wykładniczego wycofywania i działania w sytuacji, gdy występuje wyjątek HTTP, takich jak rejestrowanie błędu. W takim przypadku zasada jest skonfigurowana tak spróbuje liczba powtórzeń podczas rejestrowania typów w kontenerze Inwersja kontroli. Ze względu na konfigurację wykładniczego wycofywania zawsze, gdy kod wykrywa wyjątek HttpRequest ponowną żądania Http po odczekaniu ilość czasu, który znacznie zwiększa się w zależności od konfiguracji zasad.

Metody ważne jest HttpInvoker, czyli, co sprawia, że żądania HTTP przez tę klasę narzędzia. Czy metoda wewnętrznie wykonuje żądanie HTTP o \_policyWrapper.ExecuteAsync, który uwzględnia zasady ponawiania.

W eShopOnContainers należy określić zasady Polly, gdy rejestrowanie typów w kontenerze Inwersja kontroli, jak w poniższym kodzie z [aplikację sieci web MVC w pliku startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) klasy.

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

Należy pamiętać, obiekty IHttpClient wystąpienia są tworzone jako pojedyncze zamiast jako przejściowy, dzięki czemu połączeń TCP są wydajnie używane przez usługę i [problem z gniazda](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) nie nastąpi.

Jednak istotne dotyczące odporności jest stosowanie zasad Polly WaitAndRetryAsync w ResilientHttpClientFactory w metodzie CreateResilientHttpClient, jak pokazano w poniższym kodzie:

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
[Poprzednie] (implement-custom-http-call-retries-exponential-backoff.md) [dalej] (wdrożenie obwodu-dzielącego wyrazy pattern.md)
