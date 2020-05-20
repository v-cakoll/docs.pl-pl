---
title: Wzorce odporności aplikacji
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Wzorce odporności aplikacji
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: bb72e47704c833a2ce86f103a66b0414ce3a37ff
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614330"
---
# <a name="application-resiliency-patterns"></a>Wzorce odporności aplikacji

Pierwszym wierszem obrony jest odporność aplikacji.

Chociaż można zainwestować znaczną czas pisania własnej struktury odporności, takie produkty już istnieją. [Polly](http://www.thepollyproject.org/) to kompleksowa Biblioteka programu .NET odporności i obsługi błędów przejściowych, która pozwala deweloperom na wyznaczanie zasad odporności w sposób bezpieczny dla bezpieczeństwa i bezpiecznego wątkowo. Polly są obiektami docelowymi utworzonymi za pomocą .NET Framework lub .NET Core. W poniższej tabeli opisano funkcje odporności, nazywane `policies` , dostępne w bibliotece Polly. Mogą być stosowane pojedynczo lub zgrupowane razem.

| Zasady | Środowisko użytkownika |
| :-------- | :-------- |
| Ponawianie próby | Konfiguruje operacje ponawiania dla wydzielonych operacji. |
| Wyłącznik | Bloki żądające operacji dla wstępnie zdefiniowanego okresu, gdy błędy przekraczają skonfigurowany próg |
| Limit czasu | Umieszcza limit w czasie trwania, dla którego obiekt wywołujący może czekać na odpowiedź. |
| Gródź | Ogranicza akcje do puli zasobów o stałym rozmiarze, aby zapobiec niepowodzeniu wywołań z swamping zasobów. |
| Pamięć podręczna | Automatyczne przechowywanie odpowiedzi. |
| Opcja rezerwowa | Definiuje zachowanie strukturalne w przypadku awarii. |

Zwróć uwagę na to, jak na poprzedniej ilustracji zasady odporności dotyczą komunikatów żądania, niezależnie od tego, czy pochodzą z klienta zewnętrznego, czy z usługi zaplecza. Celem jest zrekompensowanie żądania usługi, która może być chwilowo niedostępna. Te przerwy krótkoterminowe zwykle deklarują się za pomocą kodów stanu HTTP przedstawionych w poniższej tabeli.

| Kod stanu HTTP| Przyczyna |
| :-------- | :-------- |
| 404 | Nie znaleziono |
| 408 | Limit czasu żądania |
| 429 | Zbyt wiele żądań (prawdopodobnie została ograniczona) |
| 502 | Zła brama |
| 503 | Usługa jest niedostępna |
| 504 | Limit czasu bramy |

Pytanie: Czy chcesz ponowić próbę wykonania kodu stanu HTTP 403 — Dostęp zabroniony? Nie. W tym miejscu system działa prawidłowo, ale informuje obiekt wywołujący, że nie ma uprawnień do wykonywania żądanych operacji. Należy zachować ostrożność, aby ponowić próbę tylko operacji spowodowanych błędami.

Zgodnie z zaleceniami w rozdziale 1 programiści firmy Microsoft tworzący aplikacje natywne w chmurze powinni kierować platformą .NET Core. W wersji 2,1 wprowadzono bibliotekę [HTTPClientFactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) do tworzenia wystąpień klienta http na potrzeby współpracy z zasobami opartymi na adresach URL. Zastąpienie oryginalnej klasy HTTPClient, Klasa Factory obsługuje wiele ulepszonych funkcji, jednym z nich jest [ścisła integracja](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) z biblioteką odporności Polly. Dzięki niej można łatwo definiować zasady odporności w klasie uruchamiania aplikacji w celu obsługi częściowych awarii i problemów z łącznością.

Następnie Rozwińmy wzorce ponowień i wyłączników.

### <a name="retry-pattern"></a>Wzorzec ponawiania

W rozproszonym środowisku natywnym w chmurze wywołania usług i zasobów w chmurze mogą zakończyć się niepowodzeniem z powodu przejściowych (krótko-o) awarii, które zwykle są naprawione po krótkim czasie. Implementacja strategii ponawiania próbuje, aby usługa w chmurze mogła ograniczyć te scenariusze.

[Wzorzec ponawiania próby](https://docs.microsoft.com/azure/architecture/patterns/retry) umożliwia usłudze ponowienie próby nieudanej operacji żądania, która jest możliwa do skonfigurowania. Rysunek 6-2 pokazuje ponowną próbę wykonania akcji.

![Wzorzec ponawiania w akcji](./media/retry-pattern.png)

**Rysunek 6-2**. Wzorzec ponawiania w akcji

Na poprzednim rysunku został zaimplementowany wzorzec ponawiania prób dla operacji żądania. Jest skonfigurowany tak, aby zezwalał do czterech ponownych prób przed niepowodzeniem z interwałem wycofywania (czas oczekiwania), zaczynając od dwóch sekund, co wykładniczo podwaja się dla każdej kolejnej próby.

- Pierwsze wywołanie nie powiodło się i zwraca kod stanu HTTP 500. Aplikacja czeka dwie sekundy i ponawia próbę wywołania.
- Drugie wywołanie kończy się niepowodzeniem i zwraca kod stanu HTTP 500. Aplikacja teraz podwaja interwał wycofywania do czterech sekund i ponawia próbę wywołania.
- Na koniec trzecie wywołanie powiodło się.
- W tym scenariuszu próba wykonania operacji ponawiania próbuje się do czterech ponownych prób podczas podwajania czasu trwania wycofywania przed zakończeniem wywołania.
- Po czwartej ponowieniu próby nie powiodła się. można wywołać zasady powrotu, aby bezpiecznie obsłużyć problem.

Ważne jest, aby zwiększyć okres wycofywania przed ponowną próbą wywołania, aby zezwolić na samoprawidłowość usługi. Najlepszym rozwiązaniem jest wdrożenie wykładniczego wzrostu wycofywania (podwojenie okresu przy każdej ponowieniu próby), aby zapewnić odpowiedni czas korekcji.

## <a name="circuit-breaker-pattern"></a>Wzorzec wyłącznika

Chociaż wzorzec ponawiania może pomóc w odzyskaniu żądania Entangled w częściowej awarii, istnieją sytuacje, w których awarie mogą być spowodowane nieoczekiwanymi zdarzeniami, które będą wymagały dłuższych okresów czasu na rozwiązanie. Takie błędy mogą mieć różny stopień ważności — od częściowej utraty łączności do całkowitej awarii usługi. W takich sytuacjach nie jest możliwe, aby aplikacja stale ponawiać próbę wykonania operacji, która prawdopodobnie nie powiedzie się.

Aby zapewnić, że wykonywanie ciągle powtarzających się operacji w usłudze bez odpowiedzi może przeniesieć użytkownika do samodzielnego scenariusza odmowy usługi, w którym usługa jest zastosowana do ciągłego wywoływania zasobów, takich jak pamięć, wątki i połączenia bazy danych, powodując awarię niepowiązanych części systemu, które korzystają z tych samych zasobów.

W takich sytuacjach lepszym rozwiązaniem może być niepowodzenie operacji natychmiastowego i próba wywołania usługi w przypadku, gdy będzie to możliwe.

[Wzorzec wyłącznika](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) może uniemożliwić aplikacji wielokrotne ponawianie próby wykonania operacji, która może zakończyć się niepowodzeniem. Po wstępnie zdefiniowanej liczbie wywołań zakończonych niepowodzeniem blokuje cały ruch do usługi. Okresowo zezwoli na połączenie próbne w celu ustalenia, czy błąd został rozwiązany. Rysunek 6-3 pokazuje wzorzec wyłącznika w akcji.

![Wzorzec wyłącznika w akcji](./media/circuit-breaker-pattern.png)

**Rysunek 6-3**. Wzorzec wyłącznika w akcji

Na poprzedniej ilustracji wzorzec wyłącznika został dodany do oryginalnego wzorca ponawiania prób. Zwróć uwagę, jak po 100 nieudanych żądań Wyłączniki są otwierane i nie będą już zezwalać na wywołania usługi. Wartość CheckCircuit ustawiona na 30 sekund określa, jak często Biblioteka umożliwia przechodzenie do usługi za pomocą jednego żądania. Jeśli to wywołanie zakończy się pomyślnie, obwód zostanie zamknięty, a usługa zostanie ponownie udostępniona dla ruchu.

Należy pamiętać, że intencja wzorca wyłącznika *różni* się od wzorca ponawiania prób. Wzorzec ponawiania umożliwia aplikacji ponowienie próby wykonania operacji w oczekiwany sposób. Wzorzec wyłącznika uniemożliwia aplikacji wykonywanie operacji, która prawdopodobnie nie powiedzie się. Zazwyczaj aplikacja *łączy te dwa* wzorce przy użyciu wzorca ponawiania w celu wywołania operacji za pośrednictwem wyłącznika.

## <a name="testing-for-resiliency"></a>Testowanie pod kątem odporności

Testowanie pod kątem odporności nie zawsze jest możliwe w taki sam sposób, jak testowanie funkcjonalności aplikacji (przez uruchamianie testów jednostkowych, testów integracji itd.). Zamiast tego musisz przetestować, jak całościowe obciążenie się zachowuje w warunkach błędu, który występuje tylko sporadycznie. Na przykład: wstrzyknięcie błędów przez procesy powodujące awarie, wygasłe certyfikaty, udostępnianie usług zależnych itp. Struktury takie jak [chaos-małpa](https://github.com/Netflix/chaosmonkey) mogą być używane do takich testów chaos.

Odporność aplikacji jest wymagana do obsługi problematycznych operacji. Ale jest to tylko połowa wątku. Następnie omówiono funkcje odporności dostępne w chmurze platformy Azure.

>[!div class="step-by-step"]
>[Poprzedni](resiliency.md) 
> [Dalej](infrastructure-resiliency-azure.md)
