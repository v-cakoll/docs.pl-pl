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
# <a name="implement-the-circuit-breaker-pattern"></a>Implementowanie wzorca wyłącznika

Jak wspomniano wcześniej, należy obsłużyć błędy, które mogą potrwać zmienną ilość czasu na odzyskanie z programu, tak jak w przypadku próby nawiązania połączenia ze zdalną usługą lub zasobem. Obsługa tego typu błędu może poprawić stabilność i odporność aplikacji.

W środowisku rozproszonym wywołania do zdalnych zasobów i usług mogą kończyć się niepowodzeniem z powodu przejściowych błędów, takich jak wolne połączenia sieciowe i limity czasu, lub jeśli zasoby reagują powoli lub są tymczasowo niedostępne. Te błędy są zwykle poprawiane po krótkim czasie, a niezawodna aplikacja w chmurze powinna zostać przygotowana do obsługi ich przy użyciu strategii podobnej do "wzorca ponawiania prób".

Mogą jednak wystąpić sytuacje, w których błędy są spowodowane nieoczekiwanymi zdarzeniami, których naprawa może trwać znacznie dłużej. Te błędy mogą mieć różne wagi od częściowej utraty łączności z pełną awarią usługi. W takich sytuacjach może się zdarzyć, że aplikacja będzie stale ponawiać próbę wykonania operacji, która prawdopodobnie nie powiedzie się.

Zamiast tego aplikacja powinna być zakodowana w celu zaakceptowania, że operacja zakończyła się niepowodzeniem i odpowiednio obsłużyć błąd.

Korzystanie z ponawiania prób http carelessly może skutkować powstaniem ataku typu "odmowa usługi" ([DOS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) w ramach własnego oprogramowania. Gdy mikrousługa kończy się niepowodzeniem lub działa wolno, wielu klientów może wielokrotnie ponawiać próby niepomyślnych żądań. Powoduje to powstanie niebezpiecznego ryzyka wykładniczego wzrostu ruchu przeznaczonego dla usługi z niepowodzeniem.

W związku z tym potrzebujesz pewnego rodzaju bariery obrony, aby nadmierne żądania były przerywane, gdy nie będzie to konieczne. Bariera obrony jest precyzyjnie wyłącznikiem.

Wzorzec wyłącznika ma inny cel niż "wzorzec ponawiania prób". "Wzorzec ponowienia próby" umożliwia aplikacji ponowienie próby wykonania operacji w czasie oczekiwania, że operacja zakończy się pomyślnie. Wzorzec wyłącznika uniemożliwia aplikacji wykonywanie operacji, która może zakończyć się niepowodzeniem. Aplikacja może łączyć te dwa wzorce. Jednak logika ponowień powinna być wrażliwa na każdy wyjątek zwracany przez wyłącznik i powinien porzucić ponowienie próby, jeśli wyłącznik wskazuje, że błąd nie jest przejściowy.

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a>Implementuj wzorzec wyłącznika z HttpClientFactory i Polly

Podobnie jak w przypadku wdrażania ponownych prób, zalecane podejście dla wyłączników ma na celu skorzystanie z sprawdzonych bibliotek .NET, takich jak Polly i natywnej integracji z HttpClientFactory.

Dodanie zasad wyłącznika do HttpClientFactory wychodzącego oprogramowania pośredniczącego jest tak proste jak dodanie pojedynczego przyrostowego fragmentu kodu do tego, co już istnieje podczas korzystania z HttpClientFactory.

Jedynym dodatkiem do kodu używanego do ponawiania wywołań HTTP jest kod, w którym dodajesz zasady wyłącznika do listy zasad, które mają być używane, jak pokazano w poniższym przyrostowym kodzie w metodzie ConfigureServices ().

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

`AddPolicyHandler()` Metoda dodaje zasady do obiektów `HttpClient`, które będą używane. W takim przypadku dodawana jest zasada Polly dla wyłącznika.

Aby uzyskać bardziej modularne podejście, zasady wyłącznika są zdefiniowane w oddzielnej metodzie o nazwie `GetCircuitBreakerPolicy()`, jak pokazano w poniższym kodzie:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

W powyższym przykładzie kodu zasady wyłącznika są skonfigurowane w taki sposób, że przerywają lub otwierają obwód, gdy wystąpią pięć kolejnych błędów podczas ponawiania żądań HTTP. Gdy tak się stanie, obwód zostanie przerwany przez 30 sekund: w tym czasie wywołania będą kończyły się niepowodzeniem natychmiast po wyłączniku, a nie w rzeczywistości.  Zasady automatycznie interpretują [odpowiednie wyjątki i kody stanu HTTP](/aspnet/core/fundamentals/http-requests#handle-transient-faults) jako błędy.  

Wyłączniki powinny być również używane do przekierowywania żądań do infrastruktury rezerwowej, jeśli występują problemy w konkretnym zasobie, który jest wdrażany w innym środowisku niż aplikacja kliencka lub usługa wykonująca wywołanie HTTP. Dzięki temu w przypadku awarii w centrum danych, która ma wpływ tylko na mikrousługi zaplecza, ale nie aplikacji klienckich, aplikacje klienckie mogą przekierować do usługi rezerwowej. Polly planowania nowych zasad w celu zautomatyzowania tego scenariusza [zasad trybu failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) .

Wszystkie te funkcje są przeznaczone dla przypadków, w których zarządzanie trybem failover odbywa się z poziomu kodu .NET, w przeciwieństwie do tego, że jest ono zarządzane automatycznie przez platformę Azure, z przezroczystością lokalizacji.

Z punktu widzenia użycia w przypadku korzystania z HttpClient nie trzeba dodawać żadnych nowych informacji w tym miejscu, ponieważ kod jest taki sam, jak w przypadku używania HttpClient z HttpClientFactory, jak pokazano w poprzednich sekcjach.

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Testowanie ponownych prób http i wyłączników w eShopOnContainers

Za każdym razem, gdy zostanie uruchomione rozwiązanie eShopOnContainers na hoście platformy Docker, należy uruchomić wiele kontenerów. Niektóre kontenery są wolniejsze do uruchomienia i zainicjowania, podobnie jak kontener SQL Server. Jest to szczególnie ważne przy pierwszym wdrożeniu aplikacji eShopOnContainers do platformy Docker, ponieważ wymaga ona skonfigurowania obrazów i bazy danych. Fakt, że niektóre kontenery zaczynają się wolniej niż inne mogą spowodować, że pozostała część usług będzie początkowo generować wyjątki HTTP, nawet jeśli ustawisz zależności między kontenerami na poziomie tworzenia platformy Docker, jak wyjaśniono w poprzednich sekcjach. Te zależności platformy Docker — tworzenie między kontenerami są tylko na poziomie procesu. Proces punktu wejścia kontenera może zostać uruchomiony, ale SQL Server mogą nie być gotowe do wykonywania zapytań. Wynik może być kaskadą błędów, a aplikacja może uzyskać wyjątek podczas próby użycia określonego kontenera.

Ten typ błędu może być również wyświetlany podczas uruchamiania aplikacji w chmurze. W takim przypadku koordynatorzy mogą przenosić kontenery z jednego węzła lub maszyny wirtualnej do innego (czyli do uruchamiania nowych wystąpień) w przypadku zrównoważenia liczby kontenerów w węzłach klastra.

Sposób "eShopOnContainers" rozwiązuje te problemy podczas uruchamiania wszystkich kontenerów jest za pomocą wzorca ponawiania prób przedstawiony wcześniej.

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>Testowanie wyłącznika w eShopOnContainers

Istnieje kilka sposobów na przerwanie/otwarcie obwodu i przetestowanie go za pomocą eShopOnContainers.

Jedną z opcji jest obniżenie dozwolonej liczby ponownych prób na 1 w zasadach wyłącznika i ponowne wdrożenie całego rozwiązania na platformie Docker. Przy pojedynczej ponowieniu próby istnieje dobry szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, zostanie otwarty wyłącznik i zostanie wyświetlony komunikat o błędzie.

Innym rozwiązaniem jest użycie niestandardowego oprogramowania pośredniczącego, które zostało zaimplementowane w mikrousłudze **koszyka** . Gdy to oprogramowanie pośredniczące jest włączone, przechwytuje wszystkie żądania HTTP i zwraca kod stanu 500. Oprogramowanie pośredniczące można włączyć, wysyłając żądanie GET do niekończącego identyfikatora URI, na przykład następujące:

- `GET http://localhost:5103/failing`\
  To żądanie zwraca bieżący stan oprogramowania pośredniczącego. Jeśli oprogramowanie pośredniczące jest włączone, żądanie zwróci kod stanu 500. Jeśli oprogramowanie pośredniczące jest wyłączone, nie ma odpowiedzi.

- `GET http://localhost:5103/failing?enable`\
  To żądanie umożliwia oprogramowanie pośredniczące.

- `GET http://localhost:5103/failing?disable`\
  To żądanie wyłącza oprogramowanie pośredniczące.

Na przykład, gdy aplikacja jest uruchomiona, można włączyć oprogramowanie pośredniczące, wykonując żądanie przy użyciu poniższego identyfikatora URI w dowolnej przeglądarce. Należy zauważyć, że mikrousługa porządkowania używa portu 5103.

`http://localhost:5103/failing?enable`

Następnie można sprawdzić stan przy użyciu identyfikatora URI `http://localhost:5103/failing`, jak pokazano na rysunku 8-5.

![Widok przeglądarki wyniku sprawdzania stanu niepowodzenia symulacji oprogramowania pośredniczącego](./media/image4.png)

**Rysunek 8-5**. Sprawdzanie stanu ASP.NET oprogramowania pośredniczącego "Niepowodzenie" — w tym przypadku wyłączone.

W tym momencie mikrousługa koszyka reaguje na kod stanu 500 przy każdym wywołaniu metody Invoke.

Po uruchomieniu oprogramowania pośredniczącego możesz spróbować wykonać zamówienie z poziomu aplikacji sieci Web MVC. Ponieważ żądania kończą się niepowodzeniem, obwód zostanie otwarty.

W poniższym przykładzie widać, że aplikacja sieci Web MVC ma blok catch w logice do umieszczania zamówienia.  Jeśli kod przechwytuje wyjątek typu "Open Circuit", pokazuje użytkownikowi przyjazny komunikat informujący o tym, że czeka.

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

Oto podsumowanie. Zasady ponawiania próbją kilka razy wykonać żądanie HTTP i pobierają błędy HTTP. Gdy liczba ponownych prób osiągnie maksymalną liczbę ustawioną dla zasad wyłącznika (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException. Wynik jest przyjaznym komunikatem, jak pokazano na rysunku 8-6.

![Widok przeglądarki aplikacji sieci Web MVC pokazujący komunikat "usługa koszyka" wyzwolony przez zasady wyłącznika](./media/image5.png)

**Rysunek 8-6**. Wyłącznik zwraca błąd do interfejsu użytkownika

Można zaimplementować różne logiki, gdy należy otworzyć/przerwać obwód. Możesz też wypróbować żądanie HTTP względem innej mikrousługi zaplecza, jeśli istnieje rezerwowy centrum danych lub nadmiarowy system zaplecza.

Kolejną możliwością `CircuitBreakerPolicy` jest użycie `Isolate` (które wymuszają otwieranie obwodu przez otwarte i przechowywane) oraz `Reset` (co spowoduje jego zamknięcie). Mogą one służyć do tworzenia punktów końcowych HTTP narzędzi, które wywołuje izolowanie i resetuje bezpośrednio na zasadzie.  Taki punkt końcowy HTTP może być również używany, odpowiednio zabezpieczony, w środowisku produkcyjnym w celu tymczasowego wyizolowania systemu podrzędnego, na przykład wtedy, gdy chcesz go uaktualnić. Można też ręcznie wypróbować obwód w celu ochrony systemu podrzędnego, który podejrzewa, że wystąpi błąd.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wzorzec Wyłącznika**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Poprzedni](implement-http-call-retries-exponential-backoff-polly.md)
>[Następny](monitor-app-health.md)
