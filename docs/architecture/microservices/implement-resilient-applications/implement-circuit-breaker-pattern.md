---
title: Implementowanie wzorca wyłącznika
description: Dowiedz się, jak zaimplementować wzorzec wyłącznika jako system uzupełniający do ponownych prób http.
ms.date: 03/03/2020
ms.openlocfilehash: a79c6fcca1e29f3c30d697cb369060d59a72c121
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847248"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Implementowanie wzorca wyłącznika

Jak wspomniano wcześniej, należy obsługiwać błędy, które mogą zająć zmienną ilość czasu, aby odzyskać od, jak może się zdarzyć podczas próby nawiązania połączenia z usługą zdalną lub zasobu. Obsługa tego typu usterki może poprawić stabilność i odporność aplikacji.

W środowisku rozproszonym wywołania zasobów i usług zdalnych mogą zakończyć się niepowodzeniem z powodu błędów przejściowych, takich jak powolne połączenia sieciowe i limity czasu, lub jeśli zasoby reagują powoli lub są tymczasowo niedostępne. Te błędy zazwyczaj korygują się po krótkim czasie, a niezawodna aplikacja w chmurze powinna być przygotowana do ich obsługi przy użyciu strategii, takiej jak "Wzorzec ponawiania próby".

Jednak mogą również wystąpić sytuacje, w których błędy są spowodowane nieprzewidzianych zdarzeń, które mogą potrwać znacznie dłużej, aby naprawić. Takie błędy mogą mieć różny stopień ważności — od częściowej utraty łączności do całkowitej awarii usługi. W takich sytuacjach może być bezcelowe dla aplikacji, aby stale ponowić próbę operacji, która jest mało prawdopodobne, aby odnieść sukces.

Zamiast tego aplikacja powinna być kodowana, aby zaakceptować, że operacja nie powiodła się i odpowiednio obsłużyć błąd.

Użycie ponawiania prób http niedbale może spowodować utworzenie ataku typu "odmowa usługi"[(DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)w ramach własnego oprogramowania. Ponieważ mikrousługa kończy się niepowodzeniem lub działa powoli, wielu klientów może wielokrotnie ponowić próbę żądania nie powiodło się. Stwarza to niebezpieczne ryzyko wykładniczo rosnącego ruchu ukierunkowanego na usługę, która upada.

Dlatego potrzebujesz jakiejś bariery obronnej, aby nadmierne żądania zatrzymywają się, gdy nie warto próbować. Ta bariera obronna jest właśnie wyłącznikiem.

Wzorzec wyłącznika ma inny cel niż "Wzorzec ponawiania próby". "Wzorzec ponawiania próby" umożliwia aplikacji ponowienie próby wykonania operacji w oczekiwaniu, że operacja zakończy się pomyślnie. Wzorzec wyłącznika uniemożliwia aplikacji wykonywanie operacji, która może zakończyć się niepowodzeniem. Aplikacja może połączyć te dwa wzorce. Jednak logika ponawiania powinna być wrażliwa na każdy wyjątek zwracany przez wyłącznik i należy porzucić próby ponawiania, jeśli wyłącznik wskazuje, że błąd nie jest przejściowy.

## <a name="implement-circuit-breaker-pattern-with-ihttpclientfactory-and-polly"></a>Implementowanie wzorca `IHttpClientFactory` wyłącznika z i Polly

Podobnie jak podczas implementowania ponownych prób, zalecane podejście dla wyłączników jest skorzystać ze sprawdzonych bibliotek .NET, takich jak Polly i jego integracji macierzystej z . `IHttpClientFactory`

Dodanie zasad wyłącznika `IHttpClientFactory` do wychodzącego potoku urządzenia pośrednicznego jest tak proste, jak dodanie `IHttpClientFactory`pojedynczego przyrostowego fragmentu kodu do tego, co już masz podczas korzystania .

Jedynym dodatkiem w tym miejscu do kodu używanego do ponownych prób wywołań HTTP jest kod, w którym można dodać zasady wyłącznika do listy zasad do użycia, jak pokazano w następującym kodzie przyrostowym, część ConfigureServices() metody.

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Metoda `AddPolicyHandler()` jest, co dodaje `HttpClient` zasady do obiektów, których będziesz używać. W takim przypadku jest dodanie zasad Polly dla wyłącznika.

Aby mieć bardziej modułowe podejście, zasady wyłącznika jest `GetCircuitBreakerPolicy()`zdefiniowany w oddzielnej metody o nazwie , jak pokazano w następującym kodzie:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

W powyższym przykładzie kodu zasady wyłącznika jest skonfigurowany tak, aby przerwać lub otwiera obwód, gdy było pięć kolejnych błędów podczas ponawiania żądań Http. Gdy tak się stanie, obwód zostanie przerwana na 30 sekund: w tym okresie wywołania będą natychmiast nie powiodło się przez wyłącznik, a nie faktycznie być umieszczone.  Zasady automatycznie interpretują [odpowiednie wyjątki i kody stanu HTTP](/aspnet/core/fundamentals/http-requests#handle-transient-faults) jako błędy.  

Wyłączniki powinny być również używane do przekierowywania żądań do infrastruktury rezerwowej, jeśli wystąpiły problemy w określonym zasobie, który jest wdrożony w innym środowisku niż aplikacja kliencka lub usługa wykonująca wywołanie HTTP. W ten sposób, jeśli w centrum danych występuje awaria, która ma wpływ tylko na mikrousługi zaplecza, ale nie na aplikacje klienckie, aplikacje klienckie mogą przekierowywać do usług rezerwowych. Polly planuje nową politykę, aby zautomatyzować ten scenariusz [zasad pracy awaryjnej.](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)

Wszystkie te funkcje są w przypadkach, gdy zarządzasz trybu failover z poziomu kodu .NET, w przeciwieństwie do konieczności zarządzania automatycznie dla Ciebie przez platformę Azure, z przezroczystością lokalizacji.

Z punktu widzenia użycia, podczas korzystania z HttpClient, nie ma potrzeby, aby dodać coś `HttpClient` `IHttpClientFactory`nowego w tym miejscu, ponieważ kod jest taki sam niż w przypadku korzystania z , jak pokazano w poprzednich sekcjach.

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Testowanie ponownych prób http i wyłączników w eShopOnContainers

Za każdym razem, gdy uruchamiasz rozwiązanie eShopOnContainers w hoście platformy Docker, musi uruchomić wiele kontenerów. Niektóre kontenery są wolniejsze do uruchamiania i inicjowania, takich jak kontener programu SQL Server. Jest to szczególnie ważne po raz pierwszy wdrożyć aplikację eShopOnContainers do platformy Docker, ponieważ musi skonfigurować obrazy i bazy danych. Fakt, że niektóre kontenery rozpoczynają się wolniej niż inne może spowodować, że pozostałe usługi początkowo zgłaszać wyjątki HTTP, nawet jeśli ustawisz zależności między kontenerami na poziomie docker-compose, jak wyjaśniono w poprzednich sekcjach. Te docker-compose zależności między kontenerami są tylko na poziomie procesu. Proces punktu wejścia kontenera może zostać uruchomiony, ale program SQL Server może nie być gotowy do kwerend. Wynik może być kaskadą błędów, a aplikacja może uzyskać wyjątek podczas próby użycia tego określonego kontenera.

Ten typ błędu może również zostać wyświetlony podczas uruchamiania podczas wdrażania aplikacji w chmurze. W takim przypadku koordynatorzy mogą przenosić kontenery z jednego węzła lub maszyny Wirtualnej do innego (czyli uruchamiania nowych wystąpień) podczas równoważenia liczby kontenerów w węzłach klastra.

Sposób "eShopOnContainers" rozwiązuje te problemy podczas uruchamiania wszystkich kontenerów jest przy użyciu wzorca ponawiania ilustrowane wcześniej.

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>Przetestuj wyłącznik w eShopOnContainers

Istnieje kilka sposobów, aby złamać / otworzyć obwód i przetestować go z eShopOnContainers.

Jedną z opcji jest zmniejszenie dozwolonej liczby ponownych prób do 1 w zasadach wyłącznika i ponowne wdrożenie całego rozwiązania do platformy Docker. W przypadku pojedynczej ponawiania próby istnieje duża szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, wyłącznik otworzy się i pojawi się błąd.

Inną opcją jest użycie niestandardowego narzędzia pośredniczego, które jest implementowane w mikrousługach **koszyka.** Po włączeniu tego środka pośredniczego przechwytuje wszystkie żądania HTTP i zwraca kod stanu 500. Zagęszanie można włączyć, wykonując żądanie GET do upadającego identyfikatora URI, na przykład:

- `GET http://localhost:5103/failing`\
  To żądanie zwraca bieżący stan zagęszartki. Jeśli zagęszstanie jest włączone, kod stanu zwracania żądania 500. Jeśli pośrednice są wyłączone, nie ma odpowiedzi.

- `GET http://localhost:5103/failing?enable`\
  To żądanie umożliwia zagęszanie.

- `GET http://localhost:5103/failing?disable`\
  To żądanie wyłącza program pośredniczy.

Na przykład po uruchomieniu aplikacji można włączyć pośrednice, wykonując żądanie przy użyciu następującego identyfikatora URI w dowolnej przeglądarce. Należy zauważyć, że mikrousługi porządkowania używa portu 5103.

`http://localhost:5103/failing?enable`

Następnie można sprawdzić stan przy `http://localhost:5103/failing`użyciu identyfikatora URI , jak pokazano na rysunku 8-5.

![Zrzut ekranu przedstawiający sprawdzanie stanu nieudanej symulacji urządzenia pośredniczego.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

**Rysunek 8-5**. Sprawdzanie stanu "Niepowodzenie" ASP.NET pośredniczenie — w tym przypadku wyłączone.

W tym momencie mikrousługi koszyka odpowiada z kodem stanu 500 za każdym razem, gdy wywołasz wywołać go.

Po uruchomieniu pośrednieniu można spróbować złożyć zamówienie z aplikacji sieci Web MVC. Ponieważ żądania nie powiodą się, obwód zostanie otwarty.

W poniższym przykładzie widać, że aplikacja sieci Web MVC ma catch bloku w logice do składania zamówienia.  Jeśli kod przechwytuje wyjątek otwartego obwodu, pokazuje użytkownikowi przyjazny komunikat z informacją, aby poczekać.

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

Oto podsumowanie. Zasady ponawiania próbuje kilka razy, aby żądanie HTTP i pobiera błędy HTTP. Gdy liczba ponownych prób osiągnie maksymalną liczbę ustawioną dla zasad wyłącznika (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException. Wynik jest przyjazny komunikat, jak pokazano na rysunku 8-6.

![Zrzut ekranu przedstawiający niedziała komunikat o błędzie usługi koszyka z nieoperacyjnym błędem usługi koszyka.](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

**Rysunek 8-6**. Wyłącznik zwracabłąd do interfejsu interfejsu

Można zaimplementować inną logikę, kiedy otworzyć/złamać obwód. Lub można spróbować żądania HTTP przeciwko innej mikrousługi zaplecza, jeśli istnieje rezerwowe centrum danych lub nadmiarowy system zaplecza.

Wreszcie, inną `CircuitBreakerPolicy` możliwością `Isolate` jest użycie (co wymusza otwarcie `Reset` i utrzymuje otwarty obwód) i (który zamyka go ponownie). Te mogą służyć do tworzenia narzędzia http punktu końcowego, który wywołuje izolować i resetować bezpośrednio na zasadach.  Taki punkt końcowy HTTP może być również używany, odpowiednio zabezpieczony, w środowisku produkcyjnym do tymczasowego izolowania systemu niższego rzędu, na przykład gdy chcesz go uaktualnić. Lub może potknąć się o obwód ręcznie, aby chronić system niższego rzędu, który podejrzewasz, że jest uszkodzony.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wzór wyłącznika**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Poprzedni](implement-http-call-retries-exponential-backoff-polly.md)
>[następny](monitor-app-health.md)
