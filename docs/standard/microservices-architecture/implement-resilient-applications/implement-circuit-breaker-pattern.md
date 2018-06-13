---
title: Implementacja wzorca wyłącznika
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementacja wzorca wyłącznika
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.openlocfilehash: dea94d8eda3341cca5e3aaf6b3c8369c27381135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578017"
---
# <a name="implementing-the-circuit-breaker-pattern"></a>Implementacja wzorca wyłącznika

Jak wspomniano wcześniej, powinna obsługiwać błędów, które może potrwać zmiennej ilość czasu do odzyskania, może się zdarzyć, podczas próby nawiązania połączenia usługi zdalnej lub zasobu. Obsługa tego typu błędów może poprawić stabilność i odporność aplikacji.

W środowisku rozproszonym wywołania usługi i zasoby zdalne mogą zakończyć się niepowodzeniem z powodu błędów przejściowych, takie jak powolnych połączeń sieciowych i przekroczeń limitu czasu, lub jeśli zasoby są powolna lub są tymczasowo niedostępne. Takie błędy zazwyczaj skorygować po pewnym czasie i aplikacji w chmurze niezawodne powinna być przygotowana do obsługi je za pomocą strategii like wzór ponów próbę.

Jednak może również istnieć sytuacji, w którym są błędy spowodowane nieprzewidziane zdarzenia, które może trwać znacznie dłużej, aby rozwiązać. Te błędy mogą należeć do zakresu w ważności z częściowa utraty połączenia do całkowitej awarii usługi. W takich sytuacjach może być bezcelowe dla aplikacji, aby stale ponów próbę wykonania operacji, który prawdopodobnie nie powiodła się. Zamiast tego aplikacja powinny być kodowane przyjąć, że operacja zakończyła się niepowodzeniem i odpowiednio je obsłużyć awarię.

Wzorzec wyłącznika ma innym celu niż wzorzec ponów próbę. Wzorzec ponawiania umożliwia aplikacji ponowić próbę wykonania operacji w oczekiwanie, że operacja powiedzie się po pewnym czasie. Wzorzec wyłącznika uniemożliwia wykonanie operacji, który prawdopodobnie nie powiedzie się. Aplikację można połączyć tych dwóch wzorców za pomocą wzorca ponownych prób do wywołania operacji za pomocą wyłącznika. Logika ponawiania powinna być wrażliwe na wszystkie wyjątki zwrócony przez wyłącznik i należy porzucić ponownych prób, jeśli wyłącznik wskazuje, że nie jest przejściowy błąd.

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>Implementowanie wzorca wyłącznika z Polly

Podczas implementowania ponownych prób, zalecane podejście do obwodu podziałów jest wykorzystać sprawdzonych bibliotek .NET, takie jak Polly.

Aplikacja eShopOnContainers używane są zasady Polly wyłącznika podczas implementowania HTTP ponownych prób. W rzeczywistości aplikacji dotyczy klasy narzędzie ResilientHttpClient obie zasady. Zawsze, gdy używasz obiektu typu ResilientHttpClient żądań HTTP (od eShopOnContainers) będą stosować obie te zasady, ale można dodać dodatkowe zasady zbyt.

Tylko dodanie tutaj kod używany do ponownych prób połączenia HTTP jest kod, gdzie Dodaj zasady wyłącznika do listy zasad do użycia, jak pokazano na końcu następujący kod:

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

Ten kod dodaje zasady do otoki HTTP. Czy zasady określają wyłącznika, otwartym wykrycie kod określonej liczby kolejnych wyjątków (wyjątki w wierszu), jako przekazany parametr exceptionsAllowedBeforeBreaking (5 w tym przypadku). Po otwarciu obwodu żądań HTTP nie będą działać, ale zgłoszony wyjątek.

Obwód podziałów powinny również przekierować żądania do rezerwowego infrastruktury, jeśli masz problemy z określonego zasobu, które zostało wdrożone w środowisku innej niż aplikacja klienta lub usługę, która wykonuje wywołanie HTTP. W ten sposób w przypadku wystąpienia awarii w centrum danych, które ma wpływ tylko mikrousług wewnętrznej bazy danych, ale nie w aplikacji klienta, rezerwowego usług można przekierować aplikacje klienckie. Polly jest planowanie nowych zasad w celu zautomatyzowania tego [zasad trybu failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenariusza.

Oczywiście te funkcje są w przypadkach, w których zarządzasz trybu failover z kodem .NET, zamiast go zarządzane automatycznie dla Ciebie przez platformę Azure, z lokalizacji przezroczystość.

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>Używanie klasy narzędzie ResilientHttpClient z eShopOnContainers

Klasa narzędzia ResilientHttpClient służy w sposób podobny do sposób użycia klasy .NET HttpClient. W poniższym przykładzie z aplikacji sieci web MVC eShopOnContainers (klasa agenta OrderingService używane przez OrderController) obiektu ResilientHttpClient jest wprowadzone za pomocą parametru httpClient konstruktora. Następnie obiekt jest używany do wykonywania żądań HTTP.

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

Zawsze, gdy \_apiClient elementu członkowskiego obiekt jest używany, wewnętrznie używa klasy otoki z Polly policiesؙ — zasady ponawiania, zasad wyłącznika i innych zasad, który można zastosować z kolekcji zasad Polly.

## <a name="testing-retries-in-eshoponcontainers"></a>Testowanie ponownych prób w eShopOnContainers

Przy każdym uruchomieniu rozwiązania eShopOnContainers w hostach Docker musi uruchomić wiele kontenerów. Niektóre z kontenerów są wolniejszej do uruchamiania i zainicjować, takich jak kontenera programu SQL Server. To jest szczególnie ważne podczas pierwszego wdrażania aplikacji eShopOnContainers Docker, ponieważ należy ją skonfigurować obrazów i bazy danych. Fakt, że niektóre kontenery start wolniej niż inne może spowodować pozostała część usługi do początkowo zgłaszają wyjątki HTTP, nawet w przypadku ustawienia zależności między kontenery w rozwiązania docker compose poziom, zgodnie z objaśnieniem w poprzednich sekcjach. Te rozwiązania docker-compose zależności między kontenery są tylko na poziomie procesu. Proces punktu wejścia kontenera może zostać uruchomiony, ale serwer SQL może nie być gotowy do zapytania. Może to spowodować powstanie kolejne błędy, a aplikacja może uzyskać Wystąpił wyjątek podczas próby korzystać z tym kontenerem.

Ten typ błędu może być również wyświetlany podczas uruchamiania, gdy aplikacja jest wdrażana w chmurze. W takim przypadku orchestrators może być przeniesienie kontenery z jednego węzła lub maszyny Wirtualnej do innego (tj. uruchamia nowe wystąpienia) do równoważenia liczba kontenerów w węzłach klastra.

Sposób eShopOnContainers rozwiązuje ten problem jest za pomocą wzorca ponownych prób, które firma Microsoft przedstawionymi wcześniej. Należy również określić powód błędu, podczas uruchamiania rozwiązania, można uzyskać ślady dziennika lub ostrzeżenia podobne do poniższych:

> "**1 Ponów zaimplementowany przy użyciu jego Polly RetryPolicy**, z powodu: System.Net.Http.HttpRequestException: Wystąpił błąd podczas wysyłania żądania. ---&gt; System.Net.Http.CurlException: Nie można nawiązać połączenia z serwerem\\n na System.Net.Http.CurlHandler.ThrowIfCURLEError (błąd CURLcode)\\n na \[... \].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>Testowanie wyłącznik w eShopOnContainers

Istnieje kilka sposobów można otworzyć obwodu i przetestować go z eShopOnContainers.

Ma jedną opcję obniżyć dozwoloną liczbę ponownych prób 1 w zasadach wyłącznika i ponownie wdrożyć całe rozwiązanie do Docker. Z jednej ponownych prób istnieje szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, wyłącznik zostanie otwarty i wystąpi błąd.

Inną opcją jest użycie niestandardowego oprogramowania pośredniczącego, która jest zaimplementowana w `Basket` mikrousługi. Po włączeniu tego oprogramowania pośredniczącego przechwytuje żądania HTTP i zwraca kod stanu 500. Oprogramowanie pośredniczące można włączyć dokonując żądanie GET, do którego nie można wykonać identyfikatora URI, takich jak następujące:

-   Pobierz/niepowodzenie

To żądanie zwraca bieżący stan oprogramowania pośredniczącego. Jeśli oprogramowanie pośredniczące jest włączone, żądanie zwraca kod stanu 500. Jeśli oprogramowanie pośredniczące jest wyłączony, nie będzie odpowiedzi.

-   Pobierz/niepowodzeniem? Włącz

To żądanie umożliwia oprogramowania pośredniczącego.

-   Pobierz/niepowodzeniem? wyłączone

To żądanie wyłącza oprogramowania pośredniczącego.

Na przykład gdy aplikacja jest uruchomiona, można włączyć oprogramowanie pośredniczące dokonując żądania za pomocą następującego identyfikatora URI w dowolnej przeglądarce. Należy pamiętać, że porządkowania mikrousługi korzysta z portu 5103.

http://localhost:5103/failing?enable

Następnie można sprawdzić stan, za pomocą identyfikatora URI [ http://localhost:5103/failing ](http://localhost:5103/failing), jak pokazano na rysunku nr 10-4.

![](./media/image4.png)

**Rysunek 10-4**. Sprawdzanie stanu "Niepowodzenie" ASP.NET oprogramowanie pośredniczące — w takim przypadku wyłączone. 

W tym momencie odpowiada mikrousługi koszyka z kodem stanu 500, przy każdym wywołaniu wywołania go.

Gdy oprogramowanie pośredniczące jest uruchomiony, możesz spróbować wprowadzania zamówienia z aplikacji sieci web MVC. Ponieważ żądania nie powiedzie się, zostanie otwarty obwodu.

W poniższym przykładzie widać, że aplikacja sieci web MVC ma catch bloku w logikę złożeniem zamówienia. Jeśli kod przechwytuje wyjątek Otwórz obwód, przedstawia on użytkownika przyjazną komunikat z informacją oczekiwania.

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            //… Other code
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

Poniżej przedstawiono podsumowanie. Zasady ponawiania próbuje wielokrotnie w celu żądania HTTP i pobiera komunikaty o błędach HTTP. Gdy liczbę prób osiągnie maksymalny ustawiony numer wyłącznika zasad (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException. Wynik jest przyjazny komunikat, jak pokazano na rysunku nr 10-5.

![](./media/image5.png)

**Rysunek 10-5**. Wyłącznika zwróciła błąd do interfejsu użytkownika

Można zaimplementować logiki inny program otworzyć obwodu. Lub spróbować żądanie HTTP względem różnych mikrousługi zaplecza przypadku rezerwowy centrum danych lub nadmiarowe systemu zaplecza.

Na koniec CircuitBreakerPolicy inną możliwością jest użycie Isolate (który wymusza otwarte i utrzymujących otwarte obwodu) i resetowania (który zamyka ponownie). Te mogą służyć do tworzenia punktu końcowego HTTP narzędzie wywołująca Isolate i resetowanie bezpośrednio w zasadach. Punkt końcowy HTTP można również użyć odpowiednio zabezpieczony w środowisku produkcyjnym tymczasowo izolowania podrzędne systemu, np. Jeśli chcesz ją uaktualnić. Lub jego można rzeczy przed wyjazdem obwodu ręcznie, aby chronić podrzędne system, który podejrzewasz można powodujący błąd.

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Dodawanie strategii zakłócenia zasadami ponów próbę

Regularne zasady ponawiania może wpłynąć na systemu w przypadku wysokiej współbieżności i skalowalności i w obszarze wysokiej rywalizacji. Aby wyeliminować pików podobne ponownych prób pochodzących z wielu klientów w przypadku awarii częściowe, dobre rozwiązanie jest dodanie strategii zakłócenia do algorytmu/zasady ponawiania. Może to zwiększyć ogólną wydajność systemu na trasie przez dodanie losowości do wykładniczego wycofywania. To rozprzestrzenia się nagłego o problemach. Gdy używasz Polly kod w celu zaimplementowania zakłócenia może wyglądać jak w następującym przykładzie:

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Spróbuj ponownie wzorca**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Elastyczność połączenia** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** (.NET odporności i przejściowy błąd obsługi biblioteki) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Wzorzec wyłącznika**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Brooker wytłoków. Zakłócenia: Tworzenie elementów lepiej z losowości** https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[Poprzednie] (implement-http-call-retries-exponential-backoff-polly.md) [dalej] (monitor-app-health.md)
