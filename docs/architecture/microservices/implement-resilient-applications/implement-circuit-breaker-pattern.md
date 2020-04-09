---
title: Implementowanie wzorca wyłącznika
description: Dowiedz się, jak zaimplementować wzorzec wyłącznika jako system uzupełniający do ponawiania ponawiania protokołu Http.
ms.date: 03/03/2020
ms.openlocfilehash: bebe0b4a622db928175f78f8d3e303d3d7adf170
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988888"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="a17fd-103">Implementowanie wzorca wyłącznika</span><span class="sxs-lookup"><span data-stu-id="a17fd-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="a17fd-104">Jak wspomniano wcześniej, należy obsługiwać błędy, które mogą zająć zmienną ilość czasu, aby odzyskać od, jak może się zdarzyć podczas próby połączenia z usługą zdalną lub zasobem.</span><span class="sxs-lookup"><span data-stu-id="a17fd-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="a17fd-105">Obsługa tego typu usterek może poprawić stabilność i odporność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a17fd-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="a17fd-106">W środowisku rozproszonym wywołania zasobów zdalnych i usług mogą zakończyć się niepowodzeniem z powodu błędów przejściowych, takich jak wolne połączenia sieciowe i limity czasu, lub jeśli zasoby reagują powoli lub są tymczasowo niedostępne.</span><span class="sxs-lookup"><span data-stu-id="a17fd-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="a17fd-107">Te błędy zazwyczaj poprawić się po krótkim czasie i niezawodnej aplikacji w chmurze powinny być przygotowane do obsługi ich przy użyciu strategii, takich jak "Wzorzec ponawiania próby".</span><span class="sxs-lookup"><span data-stu-id="a17fd-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span>

<span data-ttu-id="a17fd-108">Jednak mogą również wystąpić sytuacje, w których błędy są spowodowane nieoczekiwanymi zdarzeniami, które mogą potrwać znacznie dłużej, aby naprawić.</span><span class="sxs-lookup"><span data-stu-id="a17fd-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="a17fd-109">Takie błędy mogą mieć różny stopień ważności — od częściowej utraty łączności do całkowitej awarii usługi.</span><span class="sxs-lookup"><span data-stu-id="a17fd-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="a17fd-110">W takich sytuacjach może być bezcelowe dla aplikacji do ciągłego ponawiania próby operacji, która jest mało prawdopodobne, aby zakończyć się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a17fd-110">In these situations, it might be pointless for an application to continually retry an operation that's unlikely to succeed.</span></span>

<span data-ttu-id="a17fd-111">Zamiast tego aplikacja powinna być zakodowana, aby zaakceptować, że operacja nie powiodła się i odpowiednio obsłużyć błąd.</span><span class="sxs-lookup"><span data-stu-id="a17fd-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="a17fd-112">Korzystanie z protokołu Http ponownych prób niedbale może spowodować utworzenie typu "odmowa usługi"[(DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)ataku w ramach własnego oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="a17fd-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="a17fd-113">Ponieważ mikrousługa kończy się niepowodzeniem lub wykonuje się powoli, wielu klientów może wielokrotnie ponowić próbę nieudanych żądań.</span><span class="sxs-lookup"><span data-stu-id="a17fd-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="a17fd-114">Stwarza to niebezpieczne ryzyko wykładniczo zwiększenie ruchu kierowanego na usługę uchybienia.</span><span class="sxs-lookup"><span data-stu-id="a17fd-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="a17fd-115">W związku z tym, trzeba pewnego rodzaju bariery obronnej, tak aby nadmierne żądania zatrzymać, gdy nie warto próbować.</span><span class="sxs-lookup"><span data-stu-id="a17fd-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it isn't worth to keep trying.</span></span> <span data-ttu-id="a17fd-116">Ta bariera obronna jest właśnie wyłącznikiem.</span><span class="sxs-lookup"><span data-stu-id="a17fd-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="a17fd-117">Wzorzec wyłącznika ma inny cel niż "Wzorzec ponawiania próby".</span><span class="sxs-lookup"><span data-stu-id="a17fd-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="a17fd-118">"Wzorzec ponawiania" umożliwia aplikacji ponowić próbę operacji w oczekiwaniu, że operacja ostatecznie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a17fd-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="a17fd-119">Wzorzec wyłącznika uniemożliwia aplikacji wykonywanie operacji, która może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a17fd-119">The Circuit Breaker pattern prevents an application from performing an operation that's likely to fail.</span></span> <span data-ttu-id="a17fd-120">Aplikacja może połączyć te dwa wzorce.</span><span class="sxs-lookup"><span data-stu-id="a17fd-120">An application can combine these two patterns.</span></span> <span data-ttu-id="a17fd-121">Jednak logika ponawiania powinna być wrażliwa na wyjątek zwracany przez wyłącznik i należy zrezygnować z ponownych prób, jeśli wyłącznik wskazuje, że błąd nie jest przejściowy.</span><span class="sxs-lookup"><span data-stu-id="a17fd-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-ihttpclientfactory-and-polly"></a><span data-ttu-id="a17fd-122">Implementowanie wzorca `IHttpClientFactory` wyłącznika z i Polly</span><span class="sxs-lookup"><span data-stu-id="a17fd-122">Implement Circuit Breaker pattern with `IHttpClientFactory` and Polly</span></span>

<span data-ttu-id="a17fd-123">Podobnie jak podczas wdrażania ponownych prób, zalecanym podejściem do wyłączników jest skorzystanie ze sprawdzonych bibliotek .NET, takich jak Polly i jej natywnej integracji z `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="a17fd-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with `IHttpClientFactory`.</span></span>

<span data-ttu-id="a17fd-124">Dodawanie zasad wyłącznika do `IHttpClientFactory` wychodzącego potoku oprogramowania pośredniczącego jest tak proste, jak dodanie `IHttpClientFactory`pojedynczego przyrostowego fragmentu kodu do tego, co już masz podczas korzystania z programu .</span><span class="sxs-lookup"><span data-stu-id="a17fd-124">Adding a circuit breaker policy into your `IHttpClientFactory` outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using `IHttpClientFactory`.</span></span>

<span data-ttu-id="a17fd-125">Jedynym dodatkiem do kodu używanego do ponownych prób wywołań HTTP jest kod, w którym dodajesz zasady wyłącznika do listy zasad, które mają być używane, jak pokazano w poniższym kodzie przyrostowym, część metody ConfigureServices().</span><span class="sxs-lookup"><span data-stu-id="a17fd-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="a17fd-126">Metoda `AddPolicyHandler()` jest to, co `HttpClient` dodaje zasady do obiektów, które będą używane.</span><span class="sxs-lookup"><span data-stu-id="a17fd-126">The `AddPolicyHandler()` method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="a17fd-127">W takim przypadku jest dodanie zasad Polly dla wyłącznika.</span><span class="sxs-lookup"><span data-stu-id="a17fd-127">In this case, it's adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="a17fd-128">Aby uzyskać bardziej modułowe podejście, zasady wyłącznika jest `GetCircuitBreakerPolicy()`zdefiniowany w oddzielnej metody o nazwie , jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="a17fd-128">To have a more modular approach, the Circuit Breaker Policy is defined in a separate method called `GetCircuitBreakerPolicy()`, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="a17fd-129">W powyższym przykładzie kodu zasady wyłącznika jest skonfigurowany tak, aby przerywa lub otwiera obwód, gdy było pięć kolejnych błędów podczas ponawiania żądań Http.</span><span class="sxs-lookup"><span data-stu-id="a17fd-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="a17fd-130">Gdy tak się stanie, obwód zostanie przerwany na 30 sekund: w tym okresie połączenia zostaną natychmiast przerwane przez wyłącznik, a nie zostaną faktycznie umieszczone.</span><span class="sxs-lookup"><span data-stu-id="a17fd-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="a17fd-131">Zasady automatycznie interpretują [odpowiednie wyjątki i kody stanu HTTP](/aspnet/core/fundamentals/http-requests#handle-transient-faults) jako błędy.</span><span class="sxs-lookup"><span data-stu-id="a17fd-131">The policy automatically interprets [relevant exceptions and HTTP status codes](/aspnet/core/fundamentals/http-requests#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="a17fd-132">Wyłączniki powinny być również używane do przekierowywania żądań do infrastruktury rezerwowej, jeśli wystąpiły problemy w określonym zasobie, który jest wdrażany w innym środowisku niż aplikacja kliencka lub usługa, która wykonuje wywołanie HTTP.</span><span class="sxs-lookup"><span data-stu-id="a17fd-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that's deployed in a different environment than the client application or service that's performing the HTTP call.</span></span> <span data-ttu-id="a17fd-133">W ten sposób, jeśli istnieje awaria w centrum danych, który wpływa tylko na mikrousług wewnętrznej bazy danych, ale nie aplikacji klienckich, aplikacje klienckie można przekierować do usług rezerwowych.</span><span class="sxs-lookup"><span data-stu-id="a17fd-133">That way, if there's an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="a17fd-134">Polly planuje nowe zasady do automatyzacji tego scenariusza [zasad trybu failover.](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)</span><span class="sxs-lookup"><span data-stu-id="a17fd-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="a17fd-135">Wszystkie te funkcje są dla przypadków, w których zarządzasz pracy awaryjnej z poziomu kodu .NET, w przeciwieństwie do konieczności to zarządzane automatycznie dla Ciebie przez platformę Azure, z przezroczystości lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a17fd-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

<span data-ttu-id="a17fd-136">Z punktu widzenia użycia, podczas korzystania z HttpClient, nie ma potrzeby, aby dodać coś `HttpClient` `IHttpClientFactory`nowego tutaj, ponieważ kod jest taki sam niż podczas korzystania z , jak pokazano w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="a17fd-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using `HttpClient` with `IHttpClientFactory`, as shown in previous sections.</span></span>

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="a17fd-137">Testowanie ponownych prób i wyłączników w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="a17fd-137">Test Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="a17fd-138">Za każdym razem, gdy uruchamiasz rozwiązanie eShopOnContainers na hoście platformy Docker, musi uruchomić wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a17fd-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="a17fd-139">Niektóre kontenery są wolniejsze do uruchamiania i inicjowania, takie jak kontener programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a17fd-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="a17fd-140">Jest to szczególnie prawdziwe przy pierwszym wdrożeniu aplikacji eShopOnContainers w docker, ponieważ musi skonfigurować obrazy i bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a17fd-140">This is especially true the first time you deploy the eShopOnContainers application into Docker because it needs to set up the images and the database.</span></span> <span data-ttu-id="a17fd-141">Fakt, że niektóre kontenery uruchomić wolniej niż inne mogą spowodować, że pozostałe usługi początkowo zgłaszać wyjątki HTTP, nawet jeśli ustawiono zależności między kontenerami na poziomie docker-compose, jak wyjaśniono w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="a17fd-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="a17fd-142">Te zależności docker-compose między kontenerami są tylko na poziomie procesu.</span><span class="sxs-lookup"><span data-stu-id="a17fd-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="a17fd-143">Proces punktu wejścia kontenera może zostać uruchomiony, ale program SQL Server może nie być gotowy do kwerend.</span><span class="sxs-lookup"><span data-stu-id="a17fd-143">The container's entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="a17fd-144">Wynik może być kaskada błędów, a aplikacja może uzyskać wyjątek podczas próby korzystania z tego określonego kontenera.</span><span class="sxs-lookup"><span data-stu-id="a17fd-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="a17fd-145">Ten typ błędu może również zostać wyświetlony podczas uruchamiania podczas wdrażania aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="a17fd-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="a17fd-146">W takim przypadku orchestrators może być przenoszenie kontenerów z jednego węzła lub maszyny Wirtualnej do innego (czyli uruchamianie nowych wystąpień) podczas równoważenia liczby kontenerów w węzłach klastra.</span><span class="sxs-lookup"><span data-stu-id="a17fd-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster's nodes.</span></span>

<span data-ttu-id="a17fd-147">Sposób "eShopOnContainers" rozwiązuje te problemy podczas uruchamiania wszystkich kontenerów jest przy użyciu wzorzec Ponów próbę zilustrowane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a17fd-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span>

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="a17fd-148">Przetestuj wyłącznik w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="a17fd-148">Test the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="a17fd-149">Istnieje kilka sposobów, można złamać / otworzyć obwód i przetestować go z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a17fd-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="a17fd-150">Jedną z opcji jest obniżenie dozwolonej liczby ponownych prób do 1 w zasadach wyłącznika i ponowne wdrożenie całego rozwiązania do platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="a17fd-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="a17fd-151">Przy jednej próbie ponawiania istnieje duża szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, wyłącznik zostanie otwarty i pojawi się błąd.</span><span class="sxs-lookup"><span data-stu-id="a17fd-151">With a single retry, there's a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="a17fd-152">Inną opcją jest użycie niestandardowego oprogramowania pośredniczącego, które jest zaimplementowane w mikrousługi **koszyka.**</span><span class="sxs-lookup"><span data-stu-id="a17fd-152">Another option is to use custom middleware that's implemented in the **Basket** microservice.</span></span> <span data-ttu-id="a17fd-153">Gdy to oprogramowanie pośredniczące jest włączone, przechwytuje wszystkie żądania HTTP i zwraca kod stanu 500.</span><span class="sxs-lookup"><span data-stu-id="a17fd-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="a17fd-154">Oprogramowanie pośredniczące można włączyć, wysyłając żądanie GET do identyfikatora URI, który nie działa, podobnie jak następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a17fd-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`\
  <span data-ttu-id="a17fd-155">To żądanie zwraca bieżący stan oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="a17fd-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="a17fd-156">Jeśli oprogramowanie pośredniczące jest włączone, kod stanu zwrotu żądania 500.</span><span class="sxs-lookup"><span data-stu-id="a17fd-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="a17fd-157">Jeśli oprogramowanie pośredniczące jest wyłączone, nie ma odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a17fd-157">If the middleware is disabled, there's no response.</span></span>

- `GET http://localhost:5103/failing?enable`\
  <span data-ttu-id="a17fd-158">To żądanie umożliwia oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="a17fd-158">This request enables the middleware.</span></span>

- `GET http://localhost:5103/failing?disable`\
  <span data-ttu-id="a17fd-159">To żądanie wyłącza oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="a17fd-159">This request disables the middleware.</span></span>

<span data-ttu-id="a17fd-160">Na przykład po uruchomieniu aplikacji można włączyć oprogramowanie pośredniczące, składając żądanie przy użyciu następującego identyfikatora URI w dowolnej przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="a17fd-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="a17fd-161">Należy zauważyć, że mikrousługa zamawiania używa portu 5103.</span><span class="sxs-lookup"><span data-stu-id="a17fd-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable`

<span data-ttu-id="a17fd-162">Następnie można sprawdzić stan przy `http://localhost:5103/failing`użyciu identyfikatora URI , jak pokazano na rysunku 8-5.</span><span class="sxs-lookup"><span data-stu-id="a17fd-162">You can then check the status using the URI `http://localhost:5103/failing`, as shown in Figure 8-5.</span></span>

![Zrzut ekranu przedstawiający sprawdzanie stanu nieudanej symulacji oprogramowania pośredniczącego.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

<span data-ttu-id="a17fd-164">**Rysunek 8-5**.</span><span class="sxs-lookup"><span data-stu-id="a17fd-164">**Figure 8-5**.</span></span> <span data-ttu-id="a17fd-165">Sprawdzanie stanu oprogramowania pośredniczącego "Niepowodzenie" ASP.NET — w tym przypadku wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a17fd-165">Checking the state of the "Failing" ASP.NET middleware – In this case, disabled.</span></span>

<span data-ttu-id="a17fd-166">W tym momencie mikrousługi Koszyk odpowiada kod stanu 500 za każdym razem, gdy wywołasz wywołać go.</span><span class="sxs-lookup"><span data-stu-id="a17fd-166">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="a17fd-167">Po uruchomieniu oprogramowania pośredniczącego można spróbować złożyć zamówienie z aplikacji sieci web MVC.</span><span class="sxs-lookup"><span data-stu-id="a17fd-167">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="a17fd-168">Ponieważ żądania nie powiodą się, zostanie otwarty obwód.</span><span class="sxs-lookup"><span data-stu-id="a17fd-168">Because the requests fail, the circuit will open.</span></span>

<span data-ttu-id="a17fd-169">W poniższym przykładzie widać, że aplikacja sieci web MVC ma blok catch w logice składania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a17fd-169">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="a17fd-170">Jeśli kod przechwytuje wyjątek otwartego obwodu, pokazuje użytkownikowi przyjazny komunikat z informacją, aby poczekać.</span><span class="sxs-lookup"><span data-stu-id="a17fd-170">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            var user = _appUserParser.Parse(HttpContext.User);
            //Http requests using the Typed Client (Service Agent)
            var vm = await _basketSvc.GetBasket(user);
            return View(vm);
        }
        catch (BrokenCircuitException)
        {
            // Catches error when Basket.api is in circuit-opened mode
            HandleBrokenCircuitException();
        }
        return View();
    }

    private void HandleBrokenCircuitException()
    {
        TempData["BasketInoperativeMsg"] = "Basket Service is inoperative, please try later on. (Business message due to Circuit-Breaker)";
    }
}
```

<span data-ttu-id="a17fd-171">Oto podsumowanie tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="a17fd-171">Here's a summary.</span></span> <span data-ttu-id="a17fd-172">Zasady ponawiania próby kilka razy, aby zrobić żądanie HTTP i pobiera błędy HTTP.</span><span class="sxs-lookup"><span data-stu-id="a17fd-172">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="a17fd-173">Gdy liczba ponownych prób osiągnie maksymalną liczbę ustawioną dla zasad wyłącznika (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="a17fd-173">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="a17fd-174">Wynik jest przyjazny komunikat, jak pokazano na rysunku 8-6.</span><span class="sxs-lookup"><span data-stu-id="a17fd-174">The result is a friendly message, as shown in Figure 8-6.</span></span>

![Zrzut ekranu przedstawiający aplikację sieci web MVC z niedziałaowym błędem usługi koszyka.](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

<span data-ttu-id="a17fd-176">**Rysunek 8-6**.</span><span class="sxs-lookup"><span data-stu-id="a17fd-176">**Figure 8-6**.</span></span> <span data-ttu-id="a17fd-177">Wyłącznik zwracający błąd do interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a17fd-177">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="a17fd-178">Można zaimplementować inną logikę, kiedy otworzyć/przerwać obwód.</span><span class="sxs-lookup"><span data-stu-id="a17fd-178">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="a17fd-179">Lub można spróbować żądania HTTP względem różnych mikrousług zaplecza, jeśli istnieje rezerwowy centr danych lub nadmiarowy system zaplecza.</span><span class="sxs-lookup"><span data-stu-id="a17fd-179">Or you can try an HTTP request against a different back-end microservice if there's a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="a17fd-180">Wreszcie, inną możliwością `CircuitBreakerPolicy` jest `Isolate` użycie (które wymusza otwarcie `Reset` i utrzymuje otwarty obwód) i (który zamyka go ponownie).</span><span class="sxs-lookup"><span data-stu-id="a17fd-180">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="a17fd-181">Te mogą służyć do tworzenia punktu końcowego http narzędzia, który wywołuje Izolowanie i resetowanie bezpośrednio na zasadach.</span><span class="sxs-lookup"><span data-stu-id="a17fd-181">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="a17fd-182">Taki punkt końcowy HTTP może być również używany, odpowiednio zabezpieczone, w produkcji do tymczasowego izolowania systemu niższego rzędu, na przykład, gdy chcesz go uaktualnić.</span><span class="sxs-lookup"><span data-stu-id="a17fd-182">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="a17fd-183">Lub może potknąć się o obwodzie ręcznie, aby chronić system niższego rzędu, który podejrzewasz o błąd.</span><span class="sxs-lookup"><span data-stu-id="a17fd-183">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a17fd-184">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="a17fd-184">Additional resources</span></span>

- <span data-ttu-id="a17fd-185">**Wzór wyłącznika**</span><span class="sxs-lookup"><span data-stu-id="a17fd-185">**Circuit Breaker pattern**</span></span>\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
><span data-ttu-id="a17fd-186">[Poprzedni](implement-http-call-retries-exponential-backoff-polly.md)
>[następny](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="a17fd-186">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
