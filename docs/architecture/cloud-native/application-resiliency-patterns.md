---
title: Wzorce odporności aplikacji
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Wzorce odporności aplikacji
ms.date: 06/30/2019
ms.openlocfilehash: 67ae20f14a67f3a96d6c74cad727afe680ff3178
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315946"
---
# <a name="application-resiliency-patterns"></a>Wzorce odporności aplikacji

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Pierwszym wierszem obrony jest odporność aplikacji z włączoną obsługą oprogramowania. 

Chociaż można zainwestować znaczną czas pisania własnej struktury odporności, takie produkty już istnieją. Na przykład [Polly](http://www.thepollyproject.org/) jest kompleksową biblioteką odporności platformy .NET i obsługi błędów przejściowych, która pozwala deweloperom na wyznaczanie zasad odporności w sposób bezpieczny dla bezpieczeństwa i bezpiecznego wątkowo. Polly są obiektami docelowymi utworzonymi za pomocą pełnej .NET Framework lub platformy .NET Core. Rysunek 6-2 przedstawia zasady odporności (czyli funkcje) dostępne w bibliotece Polly. Te zasady można stosować pojedynczo lub wspólnie ze sobą.

![Polly Framework](./media/polly-resiliency-framework.png)

**Rysunek 6-2**. Funkcje platformy odporności Polly

Zwróć uwagę na to, jak na poprzednim rysunku zasady odporności dotyczą komunikatów żądania, niezależnie od tego, czy pochodzą z klienta zewnętrznego czy innej usługi zaplecza. Celem jest zrekompensowanie żądania usługi, która może być chwilowo niedostępna. Te krótkie przerwy zwykle deklarują się za pomocą kodów stanu HTTP przedstawionych na rysunku 6-3.

![Kody stanu HTTP do ponowienia próby](./media/http-status-codes.png)

**Rysunek 6-3**. Kody stanu HTTP do ponowienia próby

Pytanie: Czy chcesz ponowić próbę wykonania kodu stanu HTTP 403 — Dostęp zabroniony? Nie. W tym miejscu system działa prawidłowo, ale informuje obiekt wywołujący, że nie ma uprawnień do wykonywania żądanych operacji. Należy zachować ostrożność, aby ponowić próbę tylko operacji spowodowanych błędami.

Zgodnie z zaleceniami w rozdziale 1 programiści firmy Microsoft tworzący aplikacje natywne w chmurze powinni kierować platformą .NET Core. W wersji 2,1 wprowadzono bibliotekę [HTTPClientFactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) do tworzenia wystąpień klienta http na potrzeby współpracy z zasobami opartymi na adresach URL. Zastąpienie oryginalnej klasy HTTPClient, Klasa Factory obsługuje wiele ulepszonych funkcji, jednym z nich jest [ścisła integracja](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) z biblioteką odporności Polly. Dzięki niej można łatwo definiować zasady odporności w klasie uruchamiania aplikacji w celu obsługi częściowych awarii i problemów z łącznością.

Następnie Rozwińmy wzorce ponowień i wyłączników.

### <a name="retry-pattern"></a>Wzorzec ponawiania

W rozproszonym środowisku natywnym w chmurze wywołania usług i zasobów w chmurze mogą zakończyć się niepowodzeniem z powodu przejściowych (krótko-o) awarii, które zwykle są naprawione po krótkim czasie. Wdrożenie strategii ponawiania próbuje obsłużyć usługę natywną w chmurze.

[Wzorzec ponawiania próby](https://docs.microsoft.com/azure/architecture/patterns/retry) umożliwia usłudze ponowienie próby nieudanej operacji żądania, która jest możliwa do skonfigurowania. Rysunek 6-4 pokazuje ponowną próbę wykonania akcji.

![Wzorzec ponawiania w akcji](./media/retry-pattern.png)

**Rysunek 6-4**. Wzorzec ponawiania w akcji

Na poprzednim rysunku został zaimplementowany wzorzec ponawiania prób dla operacji żądania. Jest skonfigurowany tak, aby zezwalał do czterech ponownych prób przed niepowodzeniem z interwałem wycofywania (czas oczekiwania), zaczynając od dwóch sekund, co wykładniczo podwaja się dla każdej kolejnej próby.

- Pierwsze wywołanie nie powiodło się i zwraca kod stanu HTTP 500. Aplikacja czeka dwie sekundy i ponawia próbę wywołania.
- Drugie wywołanie kończy się niepowodzeniem i zwraca kod stanu HTTP 500. Aplikacja teraz podwaja interwał wycofywania do czterech sekund i ponawia próbę wywołania.
- Na koniec trzecie wywołanie powiodło się.
- W tym scenariuszu próba wykonania operacji ponawiania próbuje się do czterech ponownych prób podczas podwajania czasu trwania wycofywania przed zakończeniem wywołania.

Ważne jest, aby zwiększyć okres wycofywania przed ponowną próbą wywołania, aby zezwolić na samoprawidłowość usługi. Najlepszym rozwiązaniem jest wdrożenie wykładniczego wzrostu wycofywania (podwojenie okresu przy każdej ponowieniu próby), aby zapewnić odpowiedni czas korekcji.

## <a name="circuit-breaker-pattern"></a>Wzorzec wyłącznika

Chociaż wzorzec ponawiania może pomóc w odzyskaniu żądania Entangled w częściowej awarii, istnieją sytuacje, w których awarie mogą być spowodowane nieoczekiwanymi zdarzeniami, które będą wymagały dłuższych okresów czasu na rozwiązanie. Te błędy mogą mieć różne wagi od częściowej utraty łączności z pełną awarią usługi. W takich sytuacjach nie jest możliwe, aby aplikacja stale ponawiać próbę wykonania operacji, która prawdopodobnie nie powiedzie się.

Aby zapewnić, że wykonywanie operacji ciągłego ponawiania w usłudze, która nie odpowiada, może przejść do samodzielnego scenariusza odmowy usługi, w którym usługa jest zalewana przez ciągłe wywoływanie zasobów, takich jak pamięć, wątki i baza danych. połączenia, powodując niepowodzenie niepowiązanych części systemu wykorzystujących te same zasoby.

W takich sytuacjach lepszym rozwiązaniem może być niepowodzenie operacji natychmiastowego i próba wywołania usługi w przypadku, gdy będzie to możliwe.

[Wzorzec wyłącznika](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) może uniemożliwić aplikacji wielokrotne ponawianie próby wykonania operacji, która może zakończyć się niepowodzeniem. Monitoruje również aplikację z okresowym wywołaniem próbnym w celu ustalenia, czy błąd został rozwiązany. Rysunek 6-5 pokazuje wzorzec wyłącznika w akcji.

![Wzorzec wyłącznika w akcji](./media/circuit-breaker-pattern.png)

**Rysunek 6-5**. Wzorzec wyłącznika w akcji

Na poprzedniej ilustracji wzorzec wyłącznika został dodany do oryginalnego wzorca ponawiania prób. Zwróć uwagę, jak po 10 żądaniach zakończonych niepowodzeniem Wyłączniki są otwierane i nie będą już zezwalać na wywołania usługi. Wartość CheckCircuit ustawiona na 30 sekund określa, jak często Biblioteka umożliwia przechodzenie do usługi za pomocą jednego żądania. Jeśli to wywołanie zakończy się pomyślnie, obwód zostanie zamknięty, a usługa zostanie ponownie udostępniona dla ruchu.

Należy pamiętać, że intencja wzorca wyłącznika *różni* się od wzorca ponawiania prób. Wzorzec ponawiania umożliwia aplikacji ponowienie próby wykonania operacji w oczekiwany sposób. Wzorzec wyłącznika uniemożliwia aplikacji wykonywanie operacji, która prawdopodobnie nie powiedzie się. Często aplikacja *łączy te dwa* wzorce przy użyciu wzorca ponawiania w celu wywołania operacji za pośrednictwem wyłącznika. Jednak logika ponawiania powinna być wrażliwa na wszystkie wyjątki zwrócone przez wyłącznik i porzucanie ponowień próby, jeśli wyłącznik wskazuje, że błąd nie jest przejściowy.

Odporność aplikacji jest wymagana do obsługi problematycznych operacji. Ale jest to tylko połowa wątku. Następnie omówiono funkcje odporności dostępne w chmurze platformy Azure.

>[!div class="step-by-step"]
>[Poprzedni](resiliency.md)
>[Następny](infrastructure-resiliency-azure.md)
