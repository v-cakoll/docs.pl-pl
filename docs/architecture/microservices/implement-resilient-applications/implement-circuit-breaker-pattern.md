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
# <a name="implement-the-circuit-breaker-pattern"></a>Implementowanie wzorca wyłącznika

Jak wspomniano wcześniej, należy obsługiwać błędy, które mogą zająć zmienną ilość czasu, aby odzyskać od, jak może się zdarzyć podczas próby połączenia z usługą zdalną lub zasobem. Obsługa tego typu usterek może poprawić stabilność i odporność aplikacji.

W środowisku rozproszonym wywołania zasobów zdalnych i usług mogą zakończyć się niepowodzeniem z powodu błędów przejściowych, takich jak wolne połączenia sieciowe i limity czasu, lub jeśli zasoby reagują powoli lub są tymczasowo niedostępne. Te błędy zazwyczaj poprawić się po krótkim czasie i niezawodnej aplikacji w chmurze powinny być przygotowane do obsługi ich przy użyciu strategii, takich jak "Wzorzec ponawiania próby".

Jednak mogą również wystąpić sytuacje, w których błędy są spowodowane nieoczekiwanymi zdarzeniami, które mogą potrwać znacznie dłużej, aby naprawić. Takie błędy mogą mieć różny stopień ważności — od częściowej utraty łączności do całkowitej awarii usługi. W takich sytuacjach może być bezcelowe dla aplikacji do ciągłego ponawiania próby operacji, która jest mało prawdopodobne, aby zakończyć się pomyślnie.

Zamiast tego aplikacja powinna być zakodowana, aby zaakceptować, że operacja nie powiodła się i odpowiednio obsłużyć błąd.

Korzystanie z protokołu Http ponownych prób niedbale może spowodować utworzenie typu "odmowa usługi"[(DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)ataku w ramach własnego oprogramowania. Ponieważ mikrousługa kończy się niepowodzeniem lub wykonuje się powoli, wielu klientów może wielokrotnie ponowić próbę nieudanych żądań. Stwarza to niebezpieczne ryzyko wykładniczo zwiększenie ruchu kierowanego na usługę uchybienia.

W związku z tym, trzeba pewnego rodzaju bariery obronnej, tak aby nadmierne żądania zatrzymać, gdy nie warto próbować. Ta bariera obronna jest właśnie wyłącznikiem.

Wzorzec wyłącznika ma inny cel niż "Wzorzec ponawiania próby". "Wzorzec ponawiania" umożliwia aplikacji ponowić próbę operacji w oczekiwaniu, że operacja ostatecznie zakończy się pomyślnie. Wzorzec wyłącznika uniemożliwia aplikacji wykonywanie operacji, która może zakończyć się niepowodzeniem. Aplikacja może połączyć te dwa wzorce. Jednak logika ponawiania powinna być wrażliwa na wyjątek zwracany przez wyłącznik i należy zrezygnować z ponownych prób, jeśli wyłącznik wskazuje, że błąd nie jest przejściowy.

## <a name="implement-circuit-breaker-pattern-with-ihttpclientfactory-and-polly"></a>Implementowanie wzorca `IHttpClientFactory` wyłącznika z i Polly

Podobnie jak podczas wdrażania ponownych prób, zalecanym podejściem do wyłączników jest skorzystanie ze sprawdzonych bibliotek .NET, takich jak Polly i jej natywnej integracji z `IHttpClientFactory`.

Dodawanie zasad wyłącznika do `IHttpClientFactory` wychodzącego potoku oprogramowania pośredniczącego jest tak proste, jak dodanie `IHttpClientFactory`pojedynczego przyrostowego fragmentu kodu do tego, co już masz podczas korzystania z programu .

Jedynym dodatkiem do kodu używanego do ponownych prób wywołań HTTP jest kod, w którym dodajesz zasady wyłącznika do listy zasad, które mają być używane, jak pokazano w poniższym kodzie przyrostowym, część metody ConfigureServices().

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Metoda `AddPolicyHandler()` jest to, co `HttpClient` dodaje zasady do obiektów, które będą używane. W takim przypadku jest dodanie zasad Polly dla wyłącznika.

Aby uzyskać bardziej modułowe podejście, zasady wyłącznika jest `GetCircuitBreakerPolicy()`zdefiniowany w oddzielnej metody o nazwie , jak pokazano w poniższym kodzie:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

W powyższym przykładzie kodu zasady wyłącznika jest skonfigurowany tak, aby przerywa lub otwiera obwód, gdy było pięć kolejnych błędów podczas ponawiania żądań Http. Gdy tak się stanie, obwód zostanie przerwany na 30 sekund: w tym okresie połączenia zostaną natychmiast przerwane przez wyłącznik, a nie zostaną faktycznie umieszczone.  Zasady automatycznie interpretują [odpowiednie wyjątki i kody stanu HTTP](/aspnet/core/fundamentals/http-requests#handle-transient-faults) jako błędy.  

Wyłączniki powinny być również używane do przekierowywania żądań do infrastruktury rezerwowej, jeśli wystąpiły problemy w określonym zasobie, który jest wdrażany w innym środowisku niż aplikacja kliencka lub usługa, która wykonuje wywołanie HTTP. W ten sposób, jeśli istnieje awaria w centrum danych, który wpływa tylko na mikrousług wewnętrznej bazy danych, ale nie aplikacji klienckich, aplikacje klienckie można przekierować do usług rezerwowych. Polly planuje nowe zasady do automatyzacji tego scenariusza [zasad trybu failover.](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)

Wszystkie te funkcje są dla przypadków, w których zarządzasz pracy awaryjnej z poziomu kodu .NET, w przeciwieństwie do konieczności to zarządzane automatycznie dla Ciebie przez platformę Azure, z przezroczystości lokalizacji.

Z punktu widzenia użycia, podczas korzystania z HttpClient, nie ma potrzeby, aby dodać coś `HttpClient` `IHttpClientFactory`nowego tutaj, ponieważ kod jest taki sam niż podczas korzystania z , jak pokazano w poprzednich sekcjach.

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Testowanie ponownych prób i wyłączników w eShopOnContainers

Za każdym razem, gdy uruchamiasz rozwiązanie eShopOnContainers na hoście platformy Docker, musi uruchomić wiele kontenerów. Niektóre kontenery są wolniejsze do uruchamiania i inicjowania, takie jak kontener programu SQL Server. Jest to szczególnie prawdziwe przy pierwszym wdrożeniu aplikacji eShopOnContainers w docker, ponieważ musi skonfigurować obrazy i bazy danych. Fakt, że niektóre kontenery uruchomić wolniej niż inne mogą spowodować, że pozostałe usługi początkowo zgłaszać wyjątki HTTP, nawet jeśli ustawiono zależności między kontenerami na poziomie docker-compose, jak wyjaśniono w poprzednich sekcjach. Te zależności docker-compose między kontenerami są tylko na poziomie procesu. Proces punktu wejścia kontenera może zostać uruchomiony, ale program SQL Server może nie być gotowy do kwerend. Wynik może być kaskada błędów, a aplikacja może uzyskać wyjątek podczas próby korzystania z tego określonego kontenera.

Ten typ błędu może również zostać wyświetlony podczas uruchamiania podczas wdrażania aplikacji w chmurze. W takim przypadku orchestrators może być przenoszenie kontenerów z jednego węzła lub maszyny Wirtualnej do innego (czyli uruchamianie nowych wystąpień) podczas równoważenia liczby kontenerów w węzłach klastra.

Sposób "eShopOnContainers" rozwiązuje te problemy podczas uruchamiania wszystkich kontenerów jest przy użyciu wzorzec Ponów próbę zilustrowane wcześniej.

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>Przetestuj wyłącznik w eShopOnContainers

Istnieje kilka sposobów, można złamać / otworzyć obwód i przetestować go z eShopOnContainers.

Jedną z opcji jest obniżenie dozwolonej liczby ponownych prób do 1 w zasadach wyłącznika i ponowne wdrożenie całego rozwiązania do platformy Docker. Przy jednej próbie ponawiania istnieje duża szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, wyłącznik zostanie otwarty i pojawi się błąd.

Inną opcją jest użycie niestandardowego oprogramowania pośredniczącego, które jest zaimplementowane w mikrousługi **koszyka.** Gdy to oprogramowanie pośredniczące jest włączone, przechwytuje wszystkie żądania HTTP i zwraca kod stanu 500. Oprogramowanie pośredniczące można włączyć, wysyłając żądanie GET do identyfikatora URI, który nie działa, podobnie jak następujące czynności:

- `GET http://localhost:5103/failing`\
  To żądanie zwraca bieżący stan oprogramowania pośredniczącego. Jeśli oprogramowanie pośredniczące jest włączone, kod stanu zwrotu żądania 500. Jeśli oprogramowanie pośredniczące jest wyłączone, nie ma odpowiedzi.

- `GET http://localhost:5103/failing?enable`\
  To żądanie umożliwia oprogramowanie pośredniczące.

- `GET http://localhost:5103/failing?disable`\
  To żądanie wyłącza oprogramowanie pośredniczące.

Na przykład po uruchomieniu aplikacji można włączyć oprogramowanie pośredniczące, składając żądanie przy użyciu następującego identyfikatora URI w dowolnej przeglądarce. Należy zauważyć, że mikrousługa zamawiania używa portu 5103.

`http://localhost:5103/failing?enable`

Następnie można sprawdzić stan przy `http://localhost:5103/failing`użyciu identyfikatora URI , jak pokazano na rysunku 8-5.

![Zrzut ekranu przedstawiający sprawdzanie stanu nieudanej symulacji oprogramowania pośredniczącego.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

**Rysunek 8-5**. Sprawdzanie stanu oprogramowania pośredniczącego "Niepowodzenie" ASP.NET — w tym przypadku wyłączone.

W tym momencie mikrousługi Koszyk odpowiada kod stanu 500 za każdym razem, gdy wywołasz wywołać go.

Po uruchomieniu oprogramowania pośredniczącego można spróbować złożyć zamówienie z aplikacji sieci web MVC. Ponieważ żądania nie powiodą się, zostanie otwarty obwód.

W poniższym przykładzie widać, że aplikacja sieci web MVC ma blok catch w logice składania zamówienia.  Jeśli kod przechwytuje wyjątek otwartego obwodu, pokazuje użytkownikowi przyjazny komunikat z informacją, aby poczekać.

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

Oto podsumowanie tych zmiennych. Zasady ponawiania próby kilka razy, aby zrobić żądanie HTTP i pobiera błędy HTTP. Gdy liczba ponownych prób osiągnie maksymalną liczbę ustawioną dla zasad wyłącznika (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException. Wynik jest przyjazny komunikat, jak pokazano na rysunku 8-6.

![Zrzut ekranu przedstawiający aplikację sieci web MVC z niedziałaowym błędem usługi koszyka.](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

**Rysunek 8-6**. Wyłącznik zwracający błąd do interfejsu użytkownika

Można zaimplementować inną logikę, kiedy otworzyć/przerwać obwód. Lub można spróbować żądania HTTP względem różnych mikrousług zaplecza, jeśli istnieje rezerwowy centr danych lub nadmiarowy system zaplecza.

Wreszcie, inną możliwością `CircuitBreakerPolicy` jest `Isolate` użycie (które wymusza otwarcie `Reset` i utrzymuje otwarty obwód) i (który zamyka go ponownie). Te mogą służyć do tworzenia punktu końcowego http narzędzia, który wywołuje Izolowanie i resetowanie bezpośrednio na zasadach.  Taki punkt końcowy HTTP może być również używany, odpowiednio zabezpieczone, w produkcji do tymczasowego izolowania systemu niższego rzędu, na przykład, gdy chcesz go uaktualnić. Lub może potknąć się o obwodzie ręcznie, aby chronić system niższego rzędu, który podejrzewasz o błąd.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wzór wyłącznika**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Poprzedni](implement-http-call-retries-exponential-backoff-polly.md)
>[następny](monitor-app-health.md)
