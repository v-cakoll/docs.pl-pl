---
title: Implementowanie wzorca wyłącznika
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie wzorca wyłącznika jako uzupełniający system do ponownych prób Http
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 8cd3564e5240ec5a8783edb336957549be27ea6a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880782"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="8f535-103">Implementowanie wzorca wyłącznika</span><span class="sxs-lookup"><span data-stu-id="8f535-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="8f535-104">Jak wspomniano wcześniej, powinna obsługiwać błędy, które może potrwać zmienną ilość czasu, jak może się zdarzyć, gdy próbujesz połączyć się z zdalną usługą lub zasobem.</span><span class="sxs-lookup"><span data-stu-id="8f535-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="8f535-105">Obsługa tego rodzaju błędów może zwiększyć stabilność i odporność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f535-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="8f535-106">W środowisku rozproszonym wywołania do zdalnych zasobów i usług może zakończyć się niepowodzeniem z powodu przejściowych błędów, takich jak wolne połączenia sieciowe i przekroczeń limitu czasu, czy zasoby są odpowiada powoli lub są tymczasowo niedostępne.</span><span class="sxs-lookup"><span data-stu-id="8f535-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="8f535-107">Te błędy zwykle korygują przez krótki czas i niezawodna aplikacja w chmurze powinna być przygotowana do obsługi je za pomocą strategii, takich jak "wzorca ponawiania".</span><span class="sxs-lookup"><span data-stu-id="8f535-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span> 

<span data-ttu-id="8f535-108">Jednak może również istnieć sytuacji, w których błędy spowodowane są nieprzewidziane zdarzenia, które może potrwać dłużej, aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="8f535-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="8f535-109">Te błędy mogą mieć różny ważności — od częściowej utraty łączności do całkowitej awarii usługi.</span><span class="sxs-lookup"><span data-stu-id="8f535-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="8f535-110">W takich sytuacjach może być sensu aplikacji ciągłe ponawianie próby wykonania operacji, która najprawdopodobniej nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="8f535-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> 

<span data-ttu-id="8f535-111">Zamiast tego aplikacja powinny być kodowane przyjąć, że operacja zakończyła się niepowodzeniem i odpowiednio obsłużyć błąd.</span><span class="sxs-lookup"><span data-stu-id="8f535-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="8f535-112">Za pomocą ponownych prób Http zaniedbali może spowodować utworzenie "odmowa usługi" ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) ataku w ramach własnego oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="8f535-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="8f535-113">Mikrousługi nie powiedzie się lub działa powoli, wielu klientów może wielokrotnie ponów próbę wykonania żądania zakończone niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8f535-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="8f535-114">Który tworzy niebezpiecznych ryzyko wykładniczo w ten sposób ruch z celem usługi niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8f535-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="8f535-115">Dlatego należy pewnego rodzaju barierę defense tak, aby żądania nadmierne Zatrzymaj, gdy nie zaleca się utrzymywanie podjęcie próby.</span><span class="sxs-lookup"><span data-stu-id="8f535-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it is not worth keeping trying.</span></span> <span data-ttu-id="8f535-116">Tej bariery defense jest dokładnie wyłącznika.</span><span class="sxs-lookup"><span data-stu-id="8f535-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="8f535-117">Wzorzec wyłącznika ma innym celu niż "wzorca ponawiania".</span><span class="sxs-lookup"><span data-stu-id="8f535-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="8f535-118">"Wzorzec ponawiania" umożliwia aplikacji ponowienie próby wykonania operacji w założeniu, że operacja powiedzie się po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="8f535-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="8f535-119">Wzorzec wyłącznika zapobiega aplikację wykonywania operacji, która prawdopodobnie się nie powiedzie.</span><span class="sxs-lookup"><span data-stu-id="8f535-119">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="8f535-120">Aplikacja może korzystać z tych dwóch wzorców.</span><span class="sxs-lookup"><span data-stu-id="8f535-120">An application can combine these two patterns.</span></span> <span data-ttu-id="8f535-121">Jednak Logika ponawiania powinna uwzględniać każdy wyjątek, zwrócone przez wyłącznik i jej przerwać ponawianie prób, jeśli wyłącznik wskazuje, że błąd nie jest przejściowy.</span><span class="sxs-lookup"><span data-stu-id="8f535-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="8f535-122">Implementowanie wzorca wyłącznika HttpClientFactory i Polly</span><span class="sxs-lookup"><span data-stu-id="8f535-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="8f535-123">Podczas implementowania ponownych prób, zalecane podejście do wyłączników jest korzystanie z zalet sprawdzonej bibliotek .NET, takich jak Polly i jego natywnej integracji z HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="8f535-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="8f535-124">Dodanie zasad wyłącznik do Twojej HttpClientFactory wychodzących potoku oprogramowania pośredniczącego jest tak proste, jak dodawanie przyrostowe pojedynczy fragment kodu do już posiadane przez Ciebie przy użyciu HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="8f535-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="8f535-125">Tylko dodać tutaj kod umożliwiający ponownych prób wywołania HTTP jest kod, gdzie dodać zasady wyłącznik do listy zasad do użycia, jak pokazano w poniższym kodzie przyrostowe część metody ConfigureServices().</span><span class="sxs-lookup"><span data-stu-id="8f535-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="8f535-126">`AddPolicyHandler()`Metoda to, co dodaje zasady do obiektów klasy HttpClient będą używane.</span><span class="sxs-lookup"><span data-stu-id="8f535-126">The `AddPolicyHandler()`method is what adds policies to the HttpClient objects you will use.</span></span> <span data-ttu-id="8f535-127">W tym przypadku go polega na dodaniu zasadę Polly wyłącznika.</span><span class="sxs-lookup"><span data-stu-id="8f535-127">In this case, it is adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="8f535-128">Aby uzyskać więcej dzięki podejściu, zasada wyłącznik jest zdefiniowana w oddzielnych metodach o nazwie GetCircuitBreakerPolicy() jako następujący kod.</span><span class="sxs-lookup"><span data-stu-id="8f535-128">In order to have a more modular approach, the Circuit Breaker Policy is defined in a separate method named GetCircuitBreakerPolicy(), as the following code.</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="8f535-129">W powyższym przykładzie kodu skonfigurowano zasad wyłącznika, dlatego przerywa ani otwiera obwodu, gdy było pięć kolejnych błędów podczas ponownego wykonywania żądania Http.</span><span class="sxs-lookup"><span data-stu-id="8f535-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="8f535-130">Jeśli tak się stanie, obwodu spowoduje przerwanie przez 30 sekund: w tym okresie wywołania nie powiedzie się natychmiast przez wyłącznik — zamiast faktycznie umieszczone.</span><span class="sxs-lookup"><span data-stu-id="8f535-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="8f535-131">Zasady automatycznie interpretuje [istotne wyjątki i kodów stanu HTTP](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) jako błędy.</span><span class="sxs-lookup"><span data-stu-id="8f535-131">The policy automatically interprets [relevant exceptions and HTTP status codes](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="8f535-132">Wyłączniki powinien również przekierować żądania do rezerwowego infrastruktury, jeśli masz problemy dotyczące określonego zasobu, który jest wdrożony w innym środowisku niż aplikacja kliencka lub usługa, która wykonuje wywołania HTTP.</span><span class="sxs-lookup"><span data-stu-id="8f535-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="8f535-133">W ten sposób w przypadku wystąpienia awarii w centrum danych, która ma wpływ na tylko mikrousługi wewnętrznej bazy danych, ale nie w aplikacji klienta, aplikacje klienckie mogą przekierowywać do rezerwowego usługi.</span><span class="sxs-lookup"><span data-stu-id="8f535-133">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="8f535-134">Polly jest planowanie nowe zasady w celu zautomatyzowania tego [zasad trybu failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenariusza.</span><span class="sxs-lookup"><span data-stu-id="8f535-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span> 

<span data-ttu-id="8f535-135">Wszystkie te funkcje są w przypadkach, w których zarządzasz trybu failover z kodem .NET, zamiast go zarządzane automatycznie dla Ciebie przez platformę Azure, z przezroczystością lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="8f535-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span> 

<span data-ttu-id="8f535-136">Z użycia punktu widzenia, gdy za pomocą elementu HttpClient nie ma potrzeby, aby dodać coś nowego w tym miejscu, ponieważ kod jest taki sam, niż gdy za pomocą elementu HttpClient z HttpClientFactory, jak pokazano w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="8f535-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span> 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="8f535-137">Testowanie ponownych prób Http i wyłączników w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8f535-137">Testing Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="8f535-138">Przy każdym uruchomieniu rozwiązania w ramach aplikacji eShopOnContainers hosta platformy Docker musi uruchomić wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="8f535-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="8f535-139">Niektóre z nich są wolniejsze uruchamianie i zainicjować, takich jak kontener programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8f535-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="8f535-140">Jest to szczególnie istotne po raz pierwszy można wdrażać w ramach aplikacji eShopOnContainers platformy docker, ponieważ należy ją skonfigurować obrazów i bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8f535-140">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="8f535-141">Fakt, że niektóre kontenery start wolniej niż inne mogą powodować pozostałych usług początkowo zgłaszają wyjątki protokołu HTTP, nawet wtedy, gdy ustawisz zależności między kontenerami w docker-compose poziom, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="8f535-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="8f535-142">Te narzędzia docker-compose zależności między kontenery są tylko na poziomie procesu.</span><span class="sxs-lookup"><span data-stu-id="8f535-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="8f535-143">Proces punktu wejścia kontener może być uruchomiona, ale program SQL Server może nie być gotowe dla zapytań.</span><span class="sxs-lookup"><span data-stu-id="8f535-143">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="8f535-144">Może to spowodować kaskadę błędów, a aplikacja może uzyskać Wystąpił wyjątek podczas próby korzystania z tego określonego kontenera.</span><span class="sxs-lookup"><span data-stu-id="8f535-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span> 

<span data-ttu-id="8f535-145">Mogą również zawiera tego typu błędu podczas uruchamiania, wdrażając aplikację w chmurze.</span><span class="sxs-lookup"><span data-stu-id="8f535-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="8f535-146">W takim przypadku koordynatorów może być przenoszenie kontenerów z jednego węzła lub maszyny Wirtualnej do innego (który rozpocznie się nowych wystąpień) do równoważenia liczba kontenerów w węzłach klastra.</span><span class="sxs-lookup"><span data-stu-id="8f535-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="8f535-147">Sposób "w ramach aplikacji eShopOnContainers" rozwiązuje te problemy podczas uruchamiania wszystkich kontenerów jest przy użyciu wzorca ponawiania przedstawionymi wcześniej.</span><span class="sxs-lookup"><span data-stu-id="8f535-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span> 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="8f535-148">Testowanie wyłącznika w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8f535-148">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="8f535-149">Istnieje kilka sposobów podziału/Otwórz obwodu i przetestujemy ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8f535-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="8f535-150">Jedną z opcji jest, aby zmniejszyć dozwoloną liczbę ponownych prób na 1 w zasadach wyłącznika i ponownego wdrożenia całej rozwiązania platformy docker.</span><span class="sxs-lookup"><span data-stu-id="8f535-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="8f535-151">Za pomocą pojedynczego ponawiania próby istnieje szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, spowoduje to otwarcie wyłącznika i zostanie wyświetlony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="8f535-151">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="8f535-152">Innym rozwiązaniem jest, aby użyć niestandardowego oprogramowania pośredniczącego, które jest zaimplementowana w mikrousługach koszyka.</span><span class="sxs-lookup"><span data-stu-id="8f535-152">Another option is to use custom middleware that is implemented in the Basket microservice.</span></span> <span data-ttu-id="8f535-153">Po włączeniu tego oprogramowania pośredniczącego przechwytuje wszystkie żądania HTTP i zwraca kod stanu 500.</span><span class="sxs-lookup"><span data-stu-id="8f535-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="8f535-154">Aby umożliwić oprogramowanie pośredniczące, żądania GET niepowodzenia identyfikatora URI, takich jak następujące:</span><span class="sxs-lookup"><span data-stu-id="8f535-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`

<span data-ttu-id="8f535-155">To żądanie zwraca bieżący stan oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="8f535-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="8f535-156">Jeśli oprogramowanie pośredniczące jest włączona, żądanie zwrócić kod stanu 500.</span><span class="sxs-lookup"><span data-stu-id="8f535-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="8f535-157">Jeśli oprogramowanie pośredniczące jest wyłączona, nie będzie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8f535-157">If the middleware is disabled, there is no response.</span></span> 

- `GET http://localhost:5103/failing?enable`

<span data-ttu-id="8f535-158">To żądanie temu oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="8f535-158">This request enables the middleware.</span></span> 

- `GET http://localhost:5103/failing?disable`

<span data-ttu-id="8f535-159">To żądanie wyłącza oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="8f535-159">This request disables the middleware.</span></span> 

<span data-ttu-id="8f535-160">Na przykład gdy aplikacja jest uruchomiona, można włączyć oprogramowanie pośredniczące, wprowadzając żądanie przy użyciu następujący identyfikator URI w dowolnej przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="8f535-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="8f535-161">Należy pamiętać, że szeregowania mikrousług korzysta z portu 5103.</span><span class="sxs-lookup"><span data-stu-id="8f535-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable` 

<span data-ttu-id="8f535-162">Następnie można sprawdzić stan, używając identyfikatora URI http://localhost:5103/failing, jak pokazano na rysunku 10-4.</span><span class="sxs-lookup"><span data-stu-id="8f535-162">You can then check the status using the URI http://localhost:5103/failing, as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="8f535-163">**Rysunek 10-4**.</span><span class="sxs-lookup"><span data-stu-id="8f535-163">**Figure 10-4**.</span></span> <span data-ttu-id="8f535-164">Sprawdzanie stanu "Niepowodzenie" ASP.NET oprogramowanie pośredniczące — w tym przypadku wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8f535-164">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="8f535-165">W tym momencie współpracuje mikrousług koszyka, kod stanu 500 w każdym przypadku, gdy wywołujesz wywołać go.</span><span class="sxs-lookup"><span data-stu-id="8f535-165">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="8f535-166">Gdy oprogramowanie pośredniczące jest uruchomiona, możesz wypróbować, co składa zamówienie z aplikacji sieci web MVC.</span><span class="sxs-lookup"><span data-stu-id="8f535-166">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="8f535-167">Ponieważ żądania nie powiedzie się, zostanie otwarty obwodu.</span><span class="sxs-lookup"><span data-stu-id="8f535-167">Because the requests fail, the circuit will open.</span></span> 

<span data-ttu-id="8f535-168">W poniższym przykładzie widać, że aplikacja sieci web MVC ma bloku catch block złożeniu zamówienia przez logikę.</span><span class="sxs-lookup"><span data-stu-id="8f535-168">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="8f535-169">Jeśli kod przechwytuje wyjątek open obwodu, przedstawia użytkownika przyjazna wiadomość o odrzuceniu oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8f535-169">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="8f535-170">Poniżej przedstawiono podsumowanie.</span><span class="sxs-lookup"><span data-stu-id="8f535-170">Here’s a summary.</span></span> <span data-ttu-id="8f535-171">Zasady ponawiania spróbuje kilka razy, aby żądania HTTP i pobiera błędy HTTP.</span><span class="sxs-lookup"><span data-stu-id="8f535-171">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="8f535-172">Gdy liczba ponownych prób osiągnie maksymalny ustawiony numer wyłącznik zasad (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="8f535-172">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="8f535-173">Wynik jest przyjazny komunikat, jak pokazano na rysunku 10-5.</span><span class="sxs-lookup"><span data-stu-id="8f535-173">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="8f535-174">**Rysunek 10-5**.</span><span class="sxs-lookup"><span data-stu-id="8f535-174">**Figure 10-5**.</span></span> <span data-ttu-id="8f535-175">Wyłącznik zwróci błąd w interfejsie użytkownika</span><span class="sxs-lookup"><span data-stu-id="8f535-175">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="8f535-176">Można zaimplementować logikę różnych kiedy open/break obwodu.</span><span class="sxs-lookup"><span data-stu-id="8f535-176">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="8f535-177">Lub możesz spróbować żądanie HTTP względem różne mikrousługi serwer zaplecza w przypadku rezerwowego centrum danych lub nadmiarowe systemu zaplecza.</span><span class="sxs-lookup"><span data-stu-id="8f535-177">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span> 

<span data-ttu-id="8f535-178">Na koniec inną możliwością `CircuitBreakerPolicy` jest użycie `Isolate` (który wymusza otwarte i przechowuje Otwórz obwodu) i `Reset` (który zamyka go ponownie).</span><span class="sxs-lookup"><span data-stu-id="8f535-178">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="8f535-179">Mogą one służyć do tworzenia punktu końcowego HTTP narzędzie wywołującego odizolować i resetowanie bezpośrednio w zasadach.</span><span class="sxs-lookup"><span data-stu-id="8f535-179">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="8f535-180">Punkt końcowy HTTP można również użyć odpowiednio zabezpieczony w środowisku produkcyjnym tymczasowo izolowania podrzędnego systemu, takie jak kiedy chcesz ją uaktualnić.</span><span class="sxs-lookup"><span data-stu-id="8f535-180">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="8f535-181">Lub można go przełączył obwodu ręcznie, aby chronić system podrzędnego, gdy istnieje podejrzenie, aby być powodujący błąd.</span><span class="sxs-lookup"><span data-stu-id="8f535-181">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>


## <a name="additional-resources"></a><span data-ttu-id="8f535-182">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="8f535-182">Additional resources</span></span>


-   <span data-ttu-id="8f535-183">**Wzorzec wyłącznika**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="8f535-183">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8f535-184">[Poprzednie](implement-http-call-retries-exponential-backoff-polly.md)
[dalej](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="8f535-184">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
