---
title: Implementowanie wzorca wyłącznika
description: Dowiedz się, jak zaimplementować wzorzec wyłącznika jako uzupełniający system do ponownych prób Http.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 25a8b52749c3a8448a80155b233edb938e9bdd64
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464193"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Implementowanie wzorca wyłącznika

Jak wspomniano wcześniej, powinna obsługiwać błędy, które może potrwać zmienną ilość czasu, jak może się zdarzyć, gdy próbujesz połączyć się z zdalną usługą lub zasobem. Obsługa tego rodzaju błędów może zwiększyć stabilność i odporność aplikacji.

W środowisku rozproszonym wywołania do zdalnych zasobów i usług może zakończyć się niepowodzeniem z powodu przejściowych błędów, takich jak wolne połączenia sieciowe i przekroczeń limitu czasu, czy zasoby są odpowiada powoli lub są tymczasowo niedostępne. Te błędy zwykle korygują przez krótki czas i niezawodna aplikacja w chmurze powinna być przygotowana do obsługi je za pomocą strategii, takich jak "wzorca ponawiania". 

Jednak może również istnieć sytuacji, w których błędy spowodowane są nieprzewidziane zdarzenia, które może potrwać dłużej, aby rozwiązać problem. Te błędy mogą mieć różny ważności — od częściowej utraty łączności do całkowitej awarii usługi. W takich sytuacjach może być sensu aplikacji ciągłe ponawianie próby wykonania operacji, która najprawdopodobniej nie powiodła się. 

Zamiast tego aplikacja powinny być kodowane przyjąć, że operacja zakończyła się niepowodzeniem i odpowiednio obsłużyć błąd.

Za pomocą ponownych prób Http zaniedbali może spowodować utworzenie "odmowa usługi" ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) ataku w ramach własnego oprogramowania. Mikrousługi nie powiedzie się lub działa powoli, wielu klientów może wielokrotnie ponów próbę wykonania żądania zakończone niepowodzeniem. Który tworzy niebezpiecznych ryzyko wykładniczo w ten sposób ruch z celem usługi niepowodzeniem.

Dlatego należy pewnego rodzaju barierę defense tak, aby żądania nadmierne Zatrzymaj, gdy nie jest wart ponawiania prób. Tej bariery defense jest dokładnie wyłącznika.

Wzorzec wyłącznika ma innym celu niż "wzorca ponawiania". "Wzorzec ponawiania" umożliwia aplikacji ponowienie próby wykonania operacji w założeniu, że operacja powiedzie się po pewnym czasie. Wzorzec wyłącznika zapobiega aplikację wykonywania operacji, która prawdopodobnie się nie powiedzie. Aplikacja może korzystać z tych dwóch wzorców. Jednak Logika ponawiania powinna uwzględniać każdy wyjątek, zwrócone przez wyłącznik i jej przerwać ponawianie prób, jeśli wyłącznik wskazuje, że błąd nie jest przejściowy.

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a>Implementowanie wzorca wyłącznika HttpClientFactory i Polly

Podczas implementowania ponownych prób, zalecane podejście do wyłączników jest korzystanie z zalet sprawdzonej bibliotek .NET, takich jak Polly i jego natywnej integracji z HttpClientFactory.

Dodanie zasad wyłącznik do Twojej HttpClientFactory wychodzących potoku oprogramowania pośredniczącego jest tak proste, jak dodawanie przyrostowe pojedynczy fragment kodu do już posiadane przez Ciebie przy użyciu HttpClientFactory.

Tylko dodać tutaj kod umożliwiający ponownych prób wywołania HTTP jest kod, gdzie dodać zasady wyłącznik do listy zasad do użycia, jak pokazano w poniższym kodzie przyrostowe część metody ConfigureServices().

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

`AddPolicyHandler()` Metoda to, co dodaje zasady do `HttpClient` obiekty użyjesz. W tym przypadku go polega na dodaniu zasadę Polly wyłącznika.

Aby uzyskać więcej dzięki podejściu, zasada wyłącznik jest zdefiniowana w oddzielnych metodach o nazwie `GetCircuitBreakerPolicy()`, jak pokazano w poniższym kodzie:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

W powyższym przykładzie kodu skonfigurowano zasad wyłącznika, dlatego przerywa ani otwiera obwodu, gdy było pięć kolejnych błędów podczas ponownego wykonywania żądania Http. Jeśli tak się stanie, obwodu spowoduje przerwanie przez 30 sekund: w tym okresie wywołania nie powiedzie się natychmiast przez wyłącznik — zamiast faktycznie umieszczone.  Zasady automatycznie interpretuje [istotne wyjątki i kodów stanu HTTP](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) jako błędy.  

Wyłączniki powinien również przekierować żądania do rezerwowego infrastruktury, jeśli masz problemy w określonego zasobu, który jest wdrożony w innym środowisku niż aplikacja kliencka lub usługa, która wykonuje wywołania HTTP. W ten sposób w przypadku wystąpienia awarii w centrum danych, która ma wpływ na tylko mikrousługi wewnętrznej bazy danych, ale nie w aplikacji klienta, aplikacje klienckie mogą przekierowywać do rezerwowego usługi. Polly jest planowanie nowe zasady w celu zautomatyzowania tego [zasad trybu failover](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenariusza. 

Wszystkie te funkcje są w przypadkach, w których zarządzasz trybu failover z kodem .NET, zamiast go zarządzane automatycznie dla Ciebie przez platformę Azure, z przezroczystością lokalizacji. 

Z użycia punktu widzenia, gdy za pomocą elementu HttpClient nie ma potrzeby, aby dodać coś nowego w tym miejscu, ponieważ kod jest taki sam, niż gdy za pomocą elementu HttpClient z HttpClientFactory, jak pokazano w poprzednich sekcjach. 

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Testowanie ponownych prób Http i wyłączników w ramach aplikacji eShopOnContainers

Przy każdym uruchomieniu rozwiązania w ramach aplikacji eShopOnContainers hosta platformy Docker musi uruchomić wiele kontenerów. Niektóre z nich są wolniejsze uruchamianie i zainicjować, takich jak kontener programu SQL Server. Jest to szczególnie istotne, możesz wdrożyć ją w ramach aplikacji eShopOnContainers platformy docker, ponieważ należy ją skonfigurować obrazów i bazę danych po raz pierwszy. Fakt, że niektóre kontenery start wolniej niż inne mogą powodować pozostałych usług początkowo zgłaszają wyjątki protokołu HTTP, nawet wtedy, gdy ustawisz zależności między kontenerami w docker-compose poziom, zgodnie z opisem w poprzedniej sekcji. Te narzędzia docker-compose zależności między kontenery są tylko na poziomie procesu. Proces punktu wejścia kontener może być uruchomiona, ale program SQL Server może nie być gotowe dla zapytań. Może to spowodować kaskadę błędów, a aplikacja może uzyskać Wystąpił wyjątek podczas próby korzystania z tego określonego kontenera.

Mogą również zawiera tego typu błędu podczas uruchamiania, wdrażając aplikację w chmurze. W takim przypadku koordynatorów może być przenoszenie kontenerów z jednego węzła lub maszyny Wirtualnej do innego (który rozpocznie się nowych wystąpień) do równoważenia liczba kontenerów w węzłach klastra.

Sposób "w ramach aplikacji eShopOnContainers" rozwiązuje te problemy podczas uruchamiania wszystkich kontenerów jest przy użyciu wzorca ponawiania przedstawionymi wcześniej. 

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>Testowanie wyłącznika w ramach aplikacji eShopOnContainers

Istnieje kilka sposobów podziału/Otwórz obwodu i przetestujemy ramach aplikacji eShopOnContainers.

Jedną z opcji jest, aby zmniejszyć dozwoloną liczbę ponownych prób na 1 w zasadach wyłącznika i ponownego wdrożenia całej rozwiązania platformy docker. Za pomocą pojedynczego ponawiania próby istnieje szansa, że żądanie HTTP zakończy się niepowodzeniem podczas wdrażania, spowoduje to otwarcie wyłącznika i zostanie wyświetlony komunikat o błędzie.

Innym rozwiązaniem jest użycie niestandardowego oprogramowania pośredniczącego, które jest zaimplementowana w **koszyka** mikrousług. Po włączeniu tego oprogramowania pośredniczącego przechwytuje wszystkie żądania HTTP i zwraca kod stanu 500. Aby umożliwić oprogramowanie pośredniczące, żądania GET niepowodzenia identyfikatora URI, takich jak następujące:

- `GET http://localhost:5103/failing`\
  To żądanie zwraca bieżący stan oprogramowania pośredniczącego. Jeśli oprogramowanie pośredniczące jest włączona, żądanie zwrócić kod stanu 500. Jeśli oprogramowanie pośredniczące jest wyłączona, nie będzie odpowiedzi.

- `GET http://localhost:5103/failing?enable`\
  To żądanie temu oprogramowanie pośredniczące.

- `GET http://localhost:5103/failing?disable`\
  To żądanie wyłącza oprogramowania pośredniczącego.

Na przykład gdy aplikacja jest uruchomiona, można włączyć oprogramowanie pośredniczące, wprowadzając żądanie przy użyciu następujący identyfikator URI w dowolnej przeglądarce. Należy pamiętać, że szeregowania mikrousług korzysta z portu 5103.

`http://localhost:5103/failing?enable` 

Następnie można sprawdzić stan, używając identyfikatora URI `http://localhost:5103/failing`, jak pokazano na rysunku 8-5.

![Widok przeglądarki wynik sprawdzania stanu niepowodzenia symulacji oprogramowania pośredniczącego](./media/image4.png)

**Rysunek 8-5**. Sprawdzanie stanu "Niepowodzenie" ASP.NET oprogramowanie pośredniczące — w tym przypadku wyłączone.

W tym momencie współpracuje mikrousług koszyka, kod stanu 500 w każdym przypadku, gdy wywołujesz wywołać go.

Gdy oprogramowanie pośredniczące jest uruchomiona, możesz wypróbować, co składa zamówienie z aplikacji sieci web MVC. Ponieważ żądania nie powiedzie się, zostanie otwarty obwodu. 

W poniższym przykładzie widać, że aplikacja sieci web MVC ma bloku catch block złożeniu zamówienia przez logikę.  Jeśli kod przechwytuje wyjątek open obwodu, przedstawia użytkownika przyjazna wiadomość o odrzuceniu oczekiwania.

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

Poniżej przedstawiono podsumowanie. Zasady ponawiania spróbuje kilka razy, aby żądania HTTP i pobiera błędy HTTP. Gdy liczba ponownych prób osiągnie maksymalny ustawiony numer wyłącznik zasad (w tym przypadku 5), aplikacja zgłasza BrokenCircuitException. Wynik jest przyjazny komunikat, jak pokazano w rysunek 8-6.

![Widok aplikacji sieci web MVC, przedstawiający komunikat "Usługa koszyka niedziałających" wyzwalanych przez zasady wyłącznika w przeglądarce](./media/image5.png)

**Rysunek 8 – 6**. Wyłącznik zwróci błąd w interfejsie użytkownika

Można zaimplementować logikę różnych kiedy open/break obwodu. Lub możesz spróbować żądanie HTTP względem różne mikrousługi serwer zaplecza w przypadku rezerwowego centrum danych lub nadmiarowe systemu zaplecza. 

Na koniec inną możliwością `CircuitBreakerPolicy` jest użycie `Isolate` (który wymusza otwarte i przechowuje Otwórz obwodu) i `Reset` (który zamyka go ponownie). Mogą one służyć do tworzenia punktu końcowego HTTP narzędzie wywołującego odizolować i resetowanie bezpośrednio w zasadach.  Punkt końcowy HTTP można również użyć odpowiednio zabezpieczony w środowisku produkcyjnym tymczasowo izolowania podrzędnego systemu, takie jak kiedy chcesz ją uaktualnić. Lub można go przełączył obwodu ręcznie, aby chronić system podrzędnego, gdy istnieje podejrzenie, aby być powodujący błąd.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wzorzec wyłącznika**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Poprzednie](implement-http-call-retries-exponential-backoff-polly.md)
>[dalej](monitor-app-health.md)