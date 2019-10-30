---
title: Implementowanie wzorca wyłącznika
description: Dowiedz się, jak zaimplementować wzorzec wyłącznika jako uzupełniający system do ponawiania prób http.
ms.date: 10/16/2018
ms.openlocfilehash: a1a24094ae98d8c767ccf692fe8ded6e28d47854
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094115"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="aa033-103">Implementowanie wzorca wyłącznika</span><span class="sxs-lookup"><span data-stu-id="aa033-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="aa033-104">Jak wspomniano wcześniej, należy obsłużyć błędy, które mogą potrwać zmienną ilość czasu na odzyskanie z programu, tak jak w przypadku próby nawiązania połączenia ze zdalną usługą lub zasobem.</span><span class="sxs-lookup"><span data-stu-id="aa033-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="aa033-105">Obsługa tego typu błędu może poprawić stabilność i odporność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa033-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="aa033-106">W środowisku rozproszonym wywołania do zdalnych zasobów i usług mogą kończyć się niepowodzeniem z powodu przejściowych błędów, takich jak wolne połączenia sieciowe i limity czasu, lub jeśli zasoby reagują powoli lub są tymczasowo niedostępne.</span><span class="sxs-lookup"><span data-stu-id="aa033-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="aa033-107">Te błędy są zwykle poprawiane po krótkim czasie, a niezawodna aplikacja w chmurze powinna zostać przygotowana do obsługi ich przy użyciu strategii podobnej do "wzorca ponawiania prób".</span><span class="sxs-lookup"><span data-stu-id="aa033-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span>

<span data-ttu-id="aa033-108">Mogą jednak wystąpić sytuacje, w których błędy są spowodowane nieoczekiwanymi zdarzeniami, których naprawa może trwać znacznie dłużej.</span><span class="sxs-lookup"><span data-stu-id="aa033-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="aa033-109">Te błędy mogą mieć różne wagi od częściowej utraty łączności z pełną awarią usługi.</span><span class="sxs-lookup"><span data-stu-id="aa033-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="aa033-110">W takich sytuacjach może się zdarzyć, że aplikacja będzie stale ponawiać próbę wykonania operacji, która prawdopodobnie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="aa033-110">In these situations, it might be pointless for an application to continually retry an operation that's unlikely to succeed.</span></span>

<span data-ttu-id="aa033-111">Zamiast tego aplikacja powinna być zakodowana w celu zaakceptowania, że operacja zakończyła się niepowodzeniem i odpowiednio obsłużyć błąd.</span><span class="sxs-lookup"><span data-stu-id="aa033-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="aa033-112">Korzystanie z ponawiania prób http carelessly może skutkować powstaniem ataku typu "odmowa usługi" ([DOS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) w ramach własnego oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="aa033-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="aa033-113">Gdy mikrousługa kończy się niepowodzeniem lub działa wolno, wielu klientów może wielokrotnie ponawiać próby niepomyślnych żądań.</span><span class="sxs-lookup"><span data-stu-id="aa033-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="aa033-114">Powoduje to powstanie niebezpiecznego ryzyka wykładniczego wzrostu ruchu przeznaczonego dla usługi z niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="aa033-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="aa033-115">W związku z tym potrzebujesz pewnego rodzaju bariery obrony, aby nadmierne żądania były przerywane, gdy nie będzie to konieczne.</span><span class="sxs-lookup"><span data-stu-id="aa033-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it isn't worth to keep trying.</span></span> <span data-ttu-id="aa033-116">Bariera obrony jest precyzyjnie wyłącznikiem.</span><span class="sxs-lookup"><span data-stu-id="aa033-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="aa033-117">Wzorzec wyłącznika ma inny cel niż "wzorzec ponawiania prób".</span><span class="sxs-lookup"><span data-stu-id="aa033-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="aa033-118">"Wzorzec ponowienia próby" umożliwia aplikacji ponowienie próby wykonania operacji w czasie oczekiwania, że operacja zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa033-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="aa033-119">Wzorzec wyłącznika uniemożliwia aplikacji wykonywanie operacji, która może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="aa033-119">The Circuit Breaker pattern prevents an application from performing an operation that's likely to fail.</span></span> <span data-ttu-id="aa033-120">Aplikacja może łączyć te dwa wzorce.</span><span class="sxs-lookup"><span data-stu-id="aa033-120">An application can combine these two patterns.</span></span> <span data-ttu-id="aa033-121">Jednak logika ponowień powinna być wrażliwa na każdy wyjątek zwracany przez wyłącznik i powinien porzucić ponowienie próby, jeśli wyłącznik wskazuje, że błąd nie jest przejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa033-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="aa033-122">Implementuj wzorzec wyłącznika z HttpClientFactory i Polly</span><span class="sxs-lookup"><span data-stu-id="aa033-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="aa033-123">Podobnie jak w przypadku wdrażania ponownych prób, zalecane podejście dla wyłączników ma na celu skorzystanie z sprawdzonych bibliotek .NET, takich jak Polly i natywnej integracji z HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="aa033-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="aa033-124">Dodanie zasad wyłącznika do HttpClientFactory wychodzącego oprogramowania pośredniczącego jest tak proste jak dodanie pojedynczego przyrostowego fragmentu kodu do tego, co już istnieje podczas korzystania z HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="aa033-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="aa033-125">Jedynym dodatkiem do kodu używanego do ponawiania wywołań HTTP jest kod, w którym dodajesz zasady wyłącznika do listy zasad, które mają być używane, jak pokazano w poniższym przyrostowym kodzie w metodzie ConfigureServices ().</span><span class="sxs-lookup"><span data-stu-id="aa033-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="aa033-126">`AddPolicyHandler()` Metoda dodaje zasady do obiektów `HttpClient`, które będą używane.</span><span class="sxs-lookup"><span data-stu-id="aa033-126">The `AddPolicyHandler()` method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="aa033-127">W takim przypadku dodawana jest zasada Polly dla wyłącznika.</span><span class="sxs-lookup"><span data-stu-id="aa033-127">In this case, it's adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="aa033-128">Aby uzyskać bardziej modularne podejście, zasady wyłącznika są zdefiniowane w oddzielnej metodzie o nazwie `GetCircuitBreakerPolicy()`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="aa033-128">To have a more modular approach, the Circuit Breaker Policy is defined in a separate method called `GetCircuitBreakerPolicy()`, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="aa033-129">W powyższym przykładzie kodu zasady wyłącznika są skonfigurowane w taki sposób, że przerywają lub otwierają obwód, gdy wystąpią pięć kolejnych błędów podczas ponawiania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="aa033-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="aa033-130">Gdy tak się stanie, obwód zostanie przerwany przez 30 sekund: w tym czasie wywołania będą kończyły się niepowodzeniem natychmiast po wyłączniku, a nie w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="aa033-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="aa033-131">Zasady automatycznie interpretują [odpowiednie wyjątki i kody stanu HTTP](/aspnet/core/fundamentals/http-requests#handle-transient-faults) jako błędy.</span><span class="sxs-lookup"><span data-stu-id="aa033-131">The policy automatically interprets [relevant exceptions and HTTP status codes](/aspnet/core/fundamentals/http-requests#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="aa033-132">Wyłączniki powinny być również używane do przekierowywania żądań do infrastruktury rezerwowej, jeśli występują problemy w konkretnym zasobie, który jest wdrażany w innym środowisku niż aplikacja kliencka lub usługa wykonująca wywołanie HTTP.</span><span class="sxs-lookup"><span data-stu-id="aa033-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that's deployed in a different environment than the client application or service that's performing the HTTP call.</span></span> <span data-ttu-id="aa033-133">Dzięki temu w przypadku awarii w centrum danych, która ma wpływ tylko na mikrousługi zaplecza, ale nie aplikacji klienckich, aplikacje klienckie mogą przekierować do usługi rezerwowej.</span><span class="sxs-lookup"><span data-stu-id="aa033-133">That way, if there's an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="aa033-134">Polly planowania nowych zasad w celu zautomatyzowania tego scenariusza [zasad trybu failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) .</span><span class="sxs-lookup"><span data-stu-id="aa033-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="aa033-135">Wszystkie te funkcje są przeznaczone dla przypadków, w których zarządzanie trybem failover odbywa się z poziomu kodu .NET, w przeciwieństwie do tego, że jest ono zarządzane automatycznie przez platformę Azure, z przezroczystością lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="aa033-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

<span data-ttu-id="aa033-136">Z punktu widzenia użycia w przypadku korzystania z HttpClient nie trzeba dodawać żadnych nowych informacji w tym miejscu, ponieważ kod jest taki sam, jak w przypadku używania HttpClient z HttpClientFactory, jak pokazano w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="aa033-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span>

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="aa033-137">Testowanie ponownych prób http i wyłączników w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="aa033-137">Test Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="aa033-138">Za każdym razem, gdy zostanie uruchomione rozwiązanie eShopOnContainers na hoście platformy Docker, należy uruchomić wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="aa033-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="aa033-139">Niektóre kontenery są wolniejsze do uruchomienia i zainicjowania, podobnie jak kontener SQL Server.</span><span class="sxs-lookup"><span data-stu-id="aa033-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="aa033-140">Jest to szczególnie ważne przy pierwszym wdrożeniu aplikacji eShopOnContainers do platformy Docker, ponieważ wymaga ona skonfigurowania obrazów i bazy danych.</span><span class="sxs-lookup"><span data-stu-id="aa033-140">This is especially true the first time you deploy the eShopOnContainers application into Docker because it needs to set up the images and the database.</span></span> <span data-ttu-id="aa033-141">Fakt, że niektóre kontenery zaczynają się wolniej niż inne mogą spowodować, że pozostała część usług będzie początkowo generować wyjątki HTTP, nawet jeśli ustawisz zależności między kontenerami na poziomie tworzenia platformy Docker, jak wyjaśniono w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="aa033-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="aa033-142">Te zależności platformy Docker — tworzenie między kontenerami są tylko na poziomie procesu.</span><span class="sxs-lookup"><span data-stu-id="aa033-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="aa033-143">Proces punktu wejścia kontenera może zostać uruchomiony, ale SQL Server mogą nie być gotowe do wykonywania zapytań.</span><span class="sxs-lookup"><span data-stu-id="aa033-143">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="aa033-144">Wynik może być kaskadą błędów, a aplikacja może uzyskać wyjątek podczas próby użycia określonego kontenera.</span><span class="sxs-lookup"><span data-stu-id="aa033-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="aa033-145">Ten typ błędu może być również wyświetlany podczas uruchamiania aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="aa033-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="aa033-146">W takim przypadku koordynatorzy mogą przenosić kontenery z jednego węzła lub maszyny wirtualnej do innego (czyli do uruchamiania nowych wystąpień) w przypadku zrównoważenia liczby kontenerów w węzłach klastra.</span><span class="sxs-lookup"><span data-stu-id="aa033-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="aa033-147">Sposób "eShopOnContainers" rozwiązuje te problemy podczas uruchamiania wszystkich kontenerów jest za pomocą wzorca ponawiania prób przedstawiony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="aa033-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span>

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="aa033-148">Testowanie wyłącznika w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="aa033-148">Test the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="aa033-149">Istnieje kilka sposobów na przerwanie/otwarcie obwodu i przetestowanie go za pomocą eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="aa033-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="aa033-150">Jedną z opcji jest obniżenie dozwolonej liczby ponownych prób na 1 w zasadach wyłącznika i ponowne wdrożenie całego rozwiązania na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="aa033-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="aa033-151">Przy pojedynczej ponowieniu próby istnieje dobry szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, zostanie otwarty wyłącznik i zostanie wyświetlony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="aa033-151">With a single retry, there's a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="aa033-152">Innym rozwiązaniem jest użycie niestandardowego oprogramowania pośredniczącego, które zostało zaimplementowane w mikrousłudze **koszyka** .</span><span class="sxs-lookup"><span data-stu-id="aa033-152">Another option is to use custom middleware that's implemented in the **Basket** microservice.</span></span> <span data-ttu-id="aa033-153">Gdy to oprogramowanie pośredniczące jest włączone, przechwytuje wszystkie żądania HTTP i zwraca kod stanu 500.</span><span class="sxs-lookup"><span data-stu-id="aa033-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="aa033-154">Oprogramowanie pośredniczące można włączyć, wysyłając żądanie GET do niekończącego identyfikatora URI, na przykład następujące:</span><span class="sxs-lookup"><span data-stu-id="aa033-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`\
  <span data-ttu-id="aa033-155">To żądanie zwraca bieżący stan oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="aa033-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="aa033-156">Jeśli oprogramowanie pośredniczące jest włączone, żądanie zwróci kod stanu 500.</span><span class="sxs-lookup"><span data-stu-id="aa033-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="aa033-157">Jeśli oprogramowanie pośredniczące jest wyłączone, nie ma odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="aa033-157">If the middleware is disabled, there's no response.</span></span>

- `GET http://localhost:5103/failing?enable`\
  <span data-ttu-id="aa033-158">To żądanie umożliwia oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="aa033-158">This request enables the middleware.</span></span>

- `GET http://localhost:5103/failing?disable`\
  <span data-ttu-id="aa033-159">To żądanie wyłącza oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="aa033-159">This request disables the middleware.</span></span>

<span data-ttu-id="aa033-160">Na przykład, gdy aplikacja jest uruchomiona, można włączyć oprogramowanie pośredniczące, wykonując żądanie przy użyciu poniższego identyfikatora URI w dowolnej przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="aa033-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="aa033-161">Należy zauważyć, że mikrousługa porządkowania używa portu 5103.</span><span class="sxs-lookup"><span data-stu-id="aa033-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable`

<span data-ttu-id="aa033-162">Następnie można sprawdzić stan przy użyciu identyfikatora URI `http://localhost:5103/failing`, jak pokazano na rysunku 8-5.</span><span class="sxs-lookup"><span data-stu-id="aa033-162">You can then check the status using the URI `http://localhost:5103/failing`, as shown in Figure 8-5.</span></span>

![Widok przeglądarki wyniku sprawdzania stanu niepowodzenia symulacji oprogramowania pośredniczącego](./media/image4.png)

<span data-ttu-id="aa033-164">**Rysunek 8-5**.</span><span class="sxs-lookup"><span data-stu-id="aa033-164">**Figure 8-5**.</span></span> <span data-ttu-id="aa033-165">Sprawdzanie stanu ASP.NET oprogramowania pośredniczącego "Niepowodzenie" — w tym przypadku wyłączone.</span><span class="sxs-lookup"><span data-stu-id="aa033-165">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span>

<span data-ttu-id="aa033-166">W tym momencie mikrousługa koszyka reaguje na kod stanu 500 przy każdym wywołaniu metody Invoke.</span><span class="sxs-lookup"><span data-stu-id="aa033-166">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="aa033-167">Po uruchomieniu oprogramowania pośredniczącego możesz spróbować wykonać zamówienie z poziomu aplikacji sieci Web MVC.</span><span class="sxs-lookup"><span data-stu-id="aa033-167">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="aa033-168">Ponieważ żądania kończą się niepowodzeniem, obwód zostanie otwarty.</span><span class="sxs-lookup"><span data-stu-id="aa033-168">Because the requests fail, the circuit will open.</span></span>

<span data-ttu-id="aa033-169">W poniższym przykładzie widać, że aplikacja sieci Web MVC ma blok catch w logice do umieszczania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="aa033-169">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="aa033-170">Jeśli kod przechwytuje wyjątek typu "Open Circuit", pokazuje użytkownikowi przyjazny komunikat informujący o tym, że czeka.</span><span class="sxs-lookup"><span data-stu-id="aa033-170">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="aa033-171">Oto podsumowanie.</span><span class="sxs-lookup"><span data-stu-id="aa033-171">Here’s a summary.</span></span> <span data-ttu-id="aa033-172">Zasady ponawiania próbją kilka razy wykonać żądanie HTTP i pobierają błędy HTTP.</span><span class="sxs-lookup"><span data-stu-id="aa033-172">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="aa033-173">Gdy liczba ponownych prób osiągnie maksymalną liczbę ustawioną dla zasad wyłącznika (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="aa033-173">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="aa033-174">Wynik jest przyjaznym komunikatem, jak pokazano na rysunku 8-6.</span><span class="sxs-lookup"><span data-stu-id="aa033-174">The result is a friendly message, as shown in Figure 8-6.</span></span>

![Widok przeglądarki aplikacji sieci Web MVC pokazujący komunikat "usługa koszyka" wyzwolony przez zasady wyłącznika](./media/image5.png)

<span data-ttu-id="aa033-176">**Rysunek 8-6**.</span><span class="sxs-lookup"><span data-stu-id="aa033-176">**Figure 8-6**.</span></span> <span data-ttu-id="aa033-177">Wyłącznik zwraca błąd do interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="aa033-177">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="aa033-178">Można zaimplementować różne logiki, gdy należy otworzyć/przerwać obwód.</span><span class="sxs-lookup"><span data-stu-id="aa033-178">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="aa033-179">Możesz też wypróbować żądanie HTTP względem innej mikrousługi zaplecza, jeśli istnieje rezerwowy centrum danych lub nadmiarowy system zaplecza.</span><span class="sxs-lookup"><span data-stu-id="aa033-179">Or you can try an HTTP request against a different back-end microservice if there's a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="aa033-180">Kolejną możliwością `CircuitBreakerPolicy` jest użycie `Isolate` (które wymuszają otwieranie obwodu przez otwarte i przechowywane) oraz `Reset` (co spowoduje jego zamknięcie).</span><span class="sxs-lookup"><span data-stu-id="aa033-180">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="aa033-181">Mogą one służyć do tworzenia punktów końcowych HTTP narzędzi, które wywołuje izolowanie i resetuje bezpośrednio na zasadzie.</span><span class="sxs-lookup"><span data-stu-id="aa033-181">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="aa033-182">Taki punkt końcowy HTTP może być również używany, odpowiednio zabezpieczony, w środowisku produkcyjnym w celu tymczasowego wyizolowania systemu podrzędnego, na przykład wtedy, gdy chcesz go uaktualnić.</span><span class="sxs-lookup"><span data-stu-id="aa033-182">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="aa033-183">Można też ręcznie wypróbować obwód w celu ochrony systemu podrzędnego, który podejrzewa, że wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="aa033-183">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="aa033-184">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="aa033-184">Additional resources</span></span>

- <span data-ttu-id="aa033-185">**Wzorzec Wyłącznika**</span><span class="sxs-lookup"><span data-stu-id="aa033-185">**Circuit Breaker pattern**</span></span>\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
><span data-ttu-id="aa033-186">[Poprzedni](implement-http-call-retries-exponential-backoff-polly.md)
>[Następny](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="aa033-186">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
