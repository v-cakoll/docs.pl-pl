---
title: "Implementacja wzorca wyłącznika"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementacja wzorca wyłącznika"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2a629e25a7565aaba156f68cf06d9a24b6c2b8b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="3b9ab-104">Implementacja wzorca wyłącznika</span><span class="sxs-lookup"><span data-stu-id="3b9ab-104">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="3b9ab-105">Jak wspomniano wcześniej, powinna obsługiwać błędów, które może potrwać zmiennej ilość czasu do odzyskania, może się zdarzyć, podczas próby nawiązania połączenia usługi zdalnej lub zasobu.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-105">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="3b9ab-106">Obsługa tego typu błędów może poprawić stabilność i odporność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-106">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="3b9ab-107">W środowisku rozproszonym wywołania usługi i zasoby zdalne mogą zakończyć się niepowodzeniem z powodu błędów przejściowych, takie jak powolnych połączeń sieciowych i przekroczeń limitu czasu, lub jeśli zasoby są powolna lub są tymczasowo niedostępne.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-107">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="3b9ab-108">Takie błędy zazwyczaj skorygować po pewnym czasie i aplikacji w chmurze niezawodne powinna być przygotowana do obsługi je za pomocą strategii like wzór ponów próbę.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-108">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="3b9ab-109">Jednak może również istnieć sytuacji, w którym są błędy spowodowane nieprzewidziane zdarzenia, które może trwać znacznie dłużej, aby rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-109">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="3b9ab-110">Te błędy mogą należeć do zakresu w ważności z częściowa utraty połączenia do całkowitej awarii usługi.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-110">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="3b9ab-111">W takich sytuacjach może być bezcelowe dla aplikacji, aby stale ponów próbę wykonania operacji, który prawdopodobnie nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-111">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="3b9ab-112">Zamiast tego aplikacja powinny być kodowane przyjąć, że operacja zakończyła się niepowodzeniem i odpowiednio je obsłużyć awarię.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-112">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="3b9ab-113">Wzorzec wyłącznika ma innym celu niż wzorzec ponów próbę.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-113">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="3b9ab-114">Wzorzec ponawiania umożliwia aplikacji ponowić próbę wykonania operacji w oczekiwanie, że operacja powiedzie się po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-114">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="3b9ab-115">Wzorzec wyłącznika uniemożliwia wykonanie operacji, który prawdopodobnie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-115">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="3b9ab-116">Aplikację można połączyć tych dwóch wzorców za pomocą wzorca ponownych prób do wywołania operacji za pomocą wyłącznika.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-116">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="3b9ab-117">Logika ponawiania powinna być wrażliwe na wszystkie wyjątki zwrócony przez wyłącznik i należy porzucić ponownych prób, jeśli wyłącznik wskazuje, że nie jest przejściowy błąd.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-117">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="3b9ab-118">Implementowanie wzorca wyłącznika z Polly</span><span class="sxs-lookup"><span data-stu-id="3b9ab-118">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="3b9ab-119">Podczas implementowania ponownych prób, zalecane podejście do obwodu podziałów jest wykorzystać sprawdzonych bibliotek .NET, takie jak Polly.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-119">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="3b9ab-120">Aplikacja eShopOnContainers używane są zasady Polly wyłącznika podczas implementowania HTTP ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-120">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="3b9ab-121">W rzeczywistości aplikacji dotyczy klasy narzędzie ResilientHttpClient obie zasady.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-121">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="3b9ab-122">Zawsze, gdy używasz obiektu typu ResilientHttpClient żądań HTTP (od eShopOnContainers) będą stosować obie te zasady, ale można dodać dodatkowe zasady zbyt.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-122">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="3b9ab-123">Tylko dodanie tutaj kod używany do ponownych prób połączenia HTTP jest kod, gdzie Dodaj zasady wyłącznika do listy zasad do użycia, jak pokazano na końcu następujący kod:</span><span class="sxs-lookup"><span data-stu-id="3b9ab-123">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
            // number of retries
            6,
            // exponential backofff
            retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
            // on retry
            (exception, timeSpan, retryCount, context) =>
            {
                var msg = $"Retry {retryCount} implemented with Polly RetryPolicy " +
                    $"of {context.PolicyKey} " +
                    $"at {context.ExecutionKey}, " +
                    $"due to: {exception}.";
                _logger.LogWarning(msg);
                _logger.LogDebug(msg);
            }),
            Policy.Handle<HttpRequestException>()
                .CircuitBreakerAsync(
                    // number of exceptions before breaking circuit
                    5,
                    // time circuit opened before retry
                    TimeSpan.FromMinutes(1),
                    (exception, duration) =>
                    {
                        // on circuit opened
                        _logger.LogTrace("Circuit breaker opened");
                    },
                    () =>
                    {
                        // on circuit closed
                        _logger.LogTrace("Circuit breaker reset");
                    })
    };
}
```

<span data-ttu-id="3b9ab-124">Ten kod dodaje zasady do otoki HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-124">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="3b9ab-125">Czy zasady określają wyłącznika, otwartym wykrycie kod określonej liczby kolejnych wyjątków (wyjątki w wierszu), jako przekazany parametr exceptionsAllowedBeforeBreaking (5 w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="3b9ab-125">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="3b9ab-126">Po otwarciu obwodu żądań HTTP nie będą działać, ale zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-126">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="3b9ab-127">Obwód podziałów powinny również przekierować żądania do rezerwowego infrastruktury, jeśli masz problemy z określonego zasobu, które zostało wdrożone w środowisku innej niż aplikacja klienta lub usługę, która wykonuje wywołanie HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-127">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="3b9ab-128">W ten sposób w przypadku wystąpienia awarii w centrum danych, które ma wpływ tylko mikrousług wewnętrznej bazy danych, ale nie w aplikacji klienta, rezerwowego usług można przekierować aplikacje klienckie.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-128">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="3b9ab-129">Polly jest planowanie nowych zasad w celu zautomatyzowania tego [zasad trybu failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenariusza.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-129">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="3b9ab-130">Oczywiście te funkcje są w przypadkach, w których zarządzasz trybu failover z kodem .NET, zamiast go zarządzane automatycznie dla Ciebie przez platformę Azure, z lokalizacji przezroczystość.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-130">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="3b9ab-131">Używanie klasy narzędzie ResilientHttpClient z eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="3b9ab-131">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="3b9ab-132">Klasa narzędzia ResilientHttpClient służy w sposób podobny do sposób użycia klasy .NET HttpClient.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-132">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="3b9ab-133">W poniższym przykładzie z aplikacji sieci web MVC eShopOnContainers (klasa agenta OrderingService używane przez OrderController) obiektu ResilientHttpClient jest wprowadzone za pomocą parametru httpClient konstruktora.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-133">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="3b9ab-134">Następnie obiekt jest używany do wykonywania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-134">Then the object is used to perform HTTP requests.</span></span>

```csharp
public class OrderingService : IOrderingService
{
    private IHttpClient _apiClient;
    private readonly string _remoteServiceBaseUrl;
    private readonly IOptionsSnapshot<AppSettings> _settings;
    private readonly IHttpContextAccessor _httpContextAccesor;

    public OrderingService(IOptionsSnapshot<AppSettings> settings,
        IHttpContextAccessor httpContextAccesor,
        IHttpClient httpClient)
    {
        _remoteServiceBaseUrl = $"{settings.Value.OrderingUrl}/api/v1/orders";
        _settings = settings;
        _httpContextAccesor = httpContextAccesor;
        _apiClient = httpClient;
    }

    async public Task<List<Order>> GetMyOrders(ApplicationUser user)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        var ordersUrl = _remoteServiceBaseUrl;
        var dataString = await _apiClient.GetStringAsync(ordersUrl);
        var response = JsonConvert.DeserializeObject<List<Order>>(dataString);
        return response;
    }

    // Other methods ...
    async public Task CreateOrder(Order order)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        _apiClient.Inst.DefaultRequestHeaders.Add("x-requestid",
            order.RequestId.ToString());
        var ordersUrl = $"{_remoteServiceBaseUrl}/new";
        order.CardTypeId = 1;
        order.CardExpirationApiFormat();
        SetFakeIdToProducts(order);
        var response = await _apiClient.PostAsync(ordersUrl, order);
        response.EnsureSuccessStatusCode();
    }
}
```

<span data-ttu-id="3b9ab-135">Zawsze, gdy \_apiClient elementu członkowskiego obiekt jest używany, wewnętrznie używa klasy otoki z Polly policiesؙ — zasady ponawiania, zasad wyłącznika i innych zasad, który można zastosować z kolekcji zasad Polly.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-135">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="3b9ab-136">Testowanie ponownych prób w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="3b9ab-136">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="3b9ab-137">Przy każdym uruchomieniu rozwiązania eShopOnContainers w hostach Docker musi uruchomić wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="3b9ab-138">Niektóre z kontenerów są wolniejszej do uruchamiania i zainicjować, takich jak kontenera programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="3b9ab-139">To jest szczególnie ważne podczas pierwszego wdrażania aplikacji eShopOnContainers Docker, ponieważ należy ją skonfigurować obrazów i bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="3b9ab-140">Fakt, że niektóre kontenery start wolniej niż inne może spowodować pozostała część usługi do początkowo zgłaszają wyjątki HTTP, nawet w przypadku ustawienia zależności między kontenery w rozwiązania docker compose poziom, zgodnie z objaśnieniem w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="3b9ab-141">Te rozwiązania docker-compose zależności między kontenery są tylko na poziomie procesu.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="3b9ab-142">Proces punktu wejścia kontenera może zostać uruchomiony, ale serwer SQL może nie być gotowy do zapytania.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="3b9ab-143">Może to spowodować powstanie kolejne błędy, a aplikacja może uzyskać Wystąpił wyjątek podczas próby korzystać z tym kontenerem.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="3b9ab-144">Ten typ błędu może być również wyświetlany podczas uruchamiania, gdy aplikacja jest wdrażana w chmurze.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="3b9ab-145">W takim przypadku orchestrators może być przeniesienie kontenery z jednego węzła lub maszyny Wirtualnej do innego (tj. uruchamia nowe wystąpienia) do równoważenia liczba kontenerów w węzłach klastra.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="3b9ab-146">Sposób eShopOnContainers rozwiązuje ten problem jest za pomocą wzorca ponownych prób, które firma Microsoft przedstawionymi wcześniej.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-146">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="3b9ab-147">Należy również określić powód błędu, podczas uruchamiania rozwiązania, można uzyskać ślady dziennika lub ostrzeżenia podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="3b9ab-147">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="3b9ab-148">"**1 Ponów zaimplementowany przy użyciu jego Polly RetryPolicy**, z powodu: System.Net.Http.HttpRequestException: Wystąpił błąd podczas wysyłania żądania.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-148">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="3b9ab-149"> ---&gt;System.Net.Http.CurlException: Nie można nawiązać połączenia z serwerem\\n na System.Net.Http.CurlHandler.ThrowIfCURLEError (błąd CURLcode)\\n na \[... \].</span><span class="sxs-lookup"><span data-stu-id="3b9ab-149"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="3b9ab-150">Testowanie wyłącznik w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="3b9ab-150">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="3b9ab-151">Istnieje kilka sposobów można otworzyć obwodu i przetestować go z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-151">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="3b9ab-152">Ma jedną opcję obniżyć dozwoloną liczbę ponownych prób 1 w zasadach wyłącznika i ponownie wdrożyć całe rozwiązanie do Docker.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-152">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="3b9ab-153">Z jednej ponownych prób istnieje szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, wyłącznik zostanie otwarty i wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-153">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="3b9ab-154">Innym rozwiązaniem jest do użycia niestandardowego oprogramowania pośredniczącego wdrożonej porządkowania mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-154">Another option is to use custom middleware that is implemented in the ordering microservice.</span></span> <span data-ttu-id="3b9ab-155">Po włączeniu tego oprogramowania pośredniczącego przechwytuje żądania HTTP i zwraca kod stanu 500.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-155">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="3b9ab-156">Oprogramowanie pośredniczące można włączyć dokonując żądanie GET, do którego nie można wykonać identyfikatora URI, takich jak następujące:</span><span class="sxs-lookup"><span data-stu-id="3b9ab-156">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="3b9ab-157">Pobierz/niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="3b9ab-157">GET /failing</span></span>

<span data-ttu-id="3b9ab-158">To żądanie zwraca bieżący stan oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-158">This request returns the current state of the middleware.</span></span> <span data-ttu-id="3b9ab-159">Jeśli oprogramowanie pośredniczące jest włączone, żądanie zwraca kod stanu 500.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-159">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="3b9ab-160">Jeśli oprogramowanie pośredniczące jest wyłączony, nie będzie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-160">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="3b9ab-161">Pobierz/niepowodzeniem? Włącz</span><span class="sxs-lookup"><span data-stu-id="3b9ab-161">GET /failing?enable</span></span>

<span data-ttu-id="3b9ab-162">To żądanie umożliwia oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-162">This request enables the middleware.</span></span>

-   <span data-ttu-id="3b9ab-163">Pobierz/niepowodzeniem? wyłączone</span><span class="sxs-lookup"><span data-stu-id="3b9ab-163">GET /failing?disable</span></span>

<span data-ttu-id="3b9ab-164">To żądanie wyłącza oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-164">This request disables the middleware.</span></span>

<span data-ttu-id="3b9ab-165">Na przykład gdy aplikacja jest uruchomiona, można włączyć oprogramowanie pośredniczące dokonując żądania za pomocą następującego identyfikatora URI w dowolnej przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-165">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="3b9ab-166">Należy pamiętać, że porządkowania mikrousługi korzysta z portu 5102.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-166">Note that the ordering microservice uses port 5102.</span></span>

<span data-ttu-id="3b9ab-167">http://localhost:5102 / niepowodzeniem? Włącz</span><span class="sxs-lookup"><span data-stu-id="3b9ab-167">http://localhost:5102/failing?enable</span></span>

<span data-ttu-id="3b9ab-168">Następnie można sprawdzić stan, za pomocą identyfikatora URI [http://localhost:5102 / niepowodzeniem](http://localhost:5100/failing), jak pokazano na rysunku nr 10-4.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-168">You can then check the status using the URI [http://localhost:5102/failing](http://localhost:5100/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="3b9ab-169">**Rysunek 10-4**.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-169">**Figure 10-4**.</span></span> <span data-ttu-id="3b9ab-170">Symulację awarii z platformy ASP.NET oprogramowania pośredniczącego</span><span class="sxs-lookup"><span data-stu-id="3b9ab-170">Simulating a failure with ASP.NET middleware</span></span>

<span data-ttu-id="3b9ab-171">W tym momencie porządkowania odpowiada mikrousługi z kodem stanu 500, przy każdym wywołaniu wywołania go.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-171">At this point, the ordering microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="3b9ab-172">Gdy oprogramowanie pośredniczące jest uruchomiony, możesz spróbować wprowadzania zamówienia z aplikacji sieci web MVC.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-172">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="3b9ab-173">Ponieważ żądania nie powiedzie się, zostanie otwarty obwodu.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-173">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="3b9ab-174">W poniższym przykładzie widać, że aplikacja sieci web MVC ma catch bloku w logikę złożeniem zamówienia.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-174">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="3b9ab-175">Jeśli kod przechwytuje wyjątek Otwórz obwód, przedstawia on użytkownika przyjazną komunikat z informacją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-175">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
[HttpPost]
public async Task<IActionResult> Create(Order model, string action)
{
    try
    {
        if (ModelState.IsValid)
        {
            var user = _appUserParser.Parse(HttpContext.User);
            await _orderSvc.CreateOrder(model);
            //Redirect to historic list.
            return RedirectToAction("Index");
        }
    }
    catch(BrokenCircuitException ex)
    {
        ModelState.AddModelError("Error",
            "It was not possible to create a new order, please try later on");
    }
    return View(model);
}
```

<span data-ttu-id="3b9ab-176">Poniżej przedstawiono podsumowanie.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-176">Here’s a summary.</span></span> <span data-ttu-id="3b9ab-177">Zasady ponawiania próbuje wielokrotnie w celu żądania HTTP i pobiera komunikaty o błędach HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-177">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="3b9ab-178">Gdy liczbę prób osiągnie maksymalny ustawiony numer wyłącznika zasad (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-178">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="3b9ab-179">Wynik jest przyjazny komunikat, jak pokazano na rysunku nr 10-5.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-179">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="3b9ab-180">**Rysunek 10-5**.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-180">**Figure 10-5**.</span></span> <span data-ttu-id="3b9ab-181">Wyłącznika zwróciła błąd do interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3b9ab-181">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="3b9ab-182">Można zaimplementować logiki inny program otworzyć obwodu.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-182">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="3b9ab-183">Lub spróbować żądanie HTTP względem różnych mikrousługi zaplecza przypadku rezerwowy centrum danych lub nadmiarowe systemu zaplecza.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-183">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="3b9ab-184">Na koniec CircuitBreakerPolicy inną możliwością jest użycie Isolate (który wymusza otwarte i utrzymujących otwarte obwodu) i resetowania (który zamyka ponownie).</span><span class="sxs-lookup"><span data-stu-id="3b9ab-184">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="3b9ab-185">Te mogą służyć do tworzenia punktu końcowego HTTP narzędzie wywołująca Isolate i resetowanie bezpośrednio w zasadach.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-185">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="3b9ab-186">Punkt końcowy HTTP można również użyć odpowiednio zabezpieczony w środowisku produkcyjnym tymczasowo izolowania podrzędne systemu, np. Jeśli chcesz ją uaktualnić.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-186">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="3b9ab-187">Lub jego można rzeczy przed wyjazdem obwodu ręcznie, aby chronić podrzędne system, który podejrzewasz można powodujący błąd.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-187">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="3b9ab-188">Dodawanie strategii zakłócenia zasadami ponów próbę</span><span class="sxs-lookup"><span data-stu-id="3b9ab-188">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="3b9ab-189">Regularne zasady ponawiania może wpłynąć na systemu w przypadku wysokiej współbieżności i skalowalności i w obszarze wysokiej rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-189">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="3b9ab-190">Aby wyeliminować pików podobne ponownych prób pochodzących z wielu klientów w przypadku awarii częściowe, dobre rozwiązanie jest dodanie strategii zakłócenia do algorytmu/zasady ponawiania.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-190">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="3b9ab-191">Może to zwiększyć ogólną wydajność systemu na trasie przez dodanie losowości do wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-191">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="3b9ab-192">To rozprzestrzenia się nagłego o problemach.</span><span class="sxs-lookup"><span data-stu-id="3b9ab-192">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="3b9ab-193">Gdy używasz Polly kod w celu zaimplementowania zakłócenia może wyglądać jak w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3b9ab-193">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="3b9ab-194">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="3b9ab-194">Additional resources</span></span>

-   <span data-ttu-id="3b9ab-195">**Spróbuj ponownie wzorzec**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="3b9ab-195">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="3b9ab-196">**Elastyczność połączenia** (Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="3b9ab-196">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="3b9ab-197">**Polly** (.NET odporności i biblioteki przejściowy błąd obsługi) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="3b9ab-197">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="3b9ab-198">**Wzorzec wyłącznika**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="3b9ab-198">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="3b9ab-199">**Brooker wytłoków. Zakłócenia: Tworzenie elementów lepiej z losowości** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="3b9ab-199">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="3b9ab-200">[Poprzednie] (implement-http-call-retries-exponential-backoff-polly.md) [dalej] (monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="3b9ab-200">[Previous] (implement-http-call-retries-exponential-backoff-polly.md) [Next] (monitor-app-health.md)</span></span>
