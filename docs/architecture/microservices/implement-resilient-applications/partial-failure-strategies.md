---
title: Strategie dotyczące obsługi częściowych niepowodzeń
description: Zapoznaj się z kilkoma strategiami obsługi częściowych awarii z gracją.
ms.date: 10/16/2018
ms.openlocfilehash: abf87df5afed02b4d794a1307a0ed943cafb4db3
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988807"
---
# <a name="strategies-to-handle-partial-failure"></a>Strategie obsługi częściowej awarii

Strategie radzenia sobie z częściowymi awariami są następujące.

**Użyj komunikacji asynchroniiowej (na przykład komunikacji opartej na wiadomościach) w mikrousługach wewnętrznych.** Jest wysoce wskazane, aby nie tworzyć długie łańcuchy synchronicznych wywołań HTTP w ramach mikrousług wewnętrznych, ponieważ ten niepoprawny projekt ostatecznie stanie się główną przyczyną awarii. Wręcz przeciwnie, z wyjątkiem komunikacji frontonu między aplikacjami klienckimi i pierwszego poziomu mikrousług lub szczegółowe bramy interfejsu API, zaleca się używać tylko komunikacji asynchroniiowej (opartej na wiadomości) po przekroczeniu początkowego cyklu żądania/odpowiedzi w ramach wewnętrznych mikrousług. Spójność ostateczna i architektury oparte na zdarzeniach pomogą zminimalizować efekty tętnienia. Te podejścia wymuszają wyższy poziom autonomii mikrousług i w związku z tym zapobiegają problemowi odnotowanemu w tym miejscu.

**Użyj ponownych prób z wykładniczym wycofywania**. Ta technika pomaga uniknąć błędów krótkich i przerywanych przez wykonywanie prób ponawiania połączeń określoną liczbę razy, w przypadku, gdy usługa nie była dostępna tylko przez krótki czas. Może to wystąpić z powodu sporadyczne problemy z siecią lub gdy mikrousługi/kontenera jest przenoszony do innego węzła w klastrze. Jeśli jednak te ponownych prób nie są prawidłowo zaprojektowane z wyłącznikami, może to pogorszyć efekty tętnienia, ostatecznie nawet powodując [odmowę usługi (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Obejście limitów czasu sieci .** Ogólnie rzecz biorąc klienci powinni być zaprojektowane, aby nie blokować przez czas nieokreślony i zawsze używać limitów czasu podczas oczekiwania na odpowiedź. Za pomocą limitów czasu zapewnia, że zasoby nigdy nie są powiązane przez czas nieokreślony.

**Użyj wzorca wyłącznika**. W tym podejściu proces klienta śledzi liczbę żądań nie powiodło się. Jeśli poziom błędu przekracza skonfigurowany limit, "wyłącznik" pokonuje, aby natychmiast zakończyć się niepowodzeniem. (Jeśli duża liczba żądań nie powiódł się, sugeruje to, że usługa jest niedostępna i że wysyłanie żądań jest bezcelowe). Po upływie limitu czasu klient powinien spróbować ponownie i, jeśli nowe żądania zakończą się pomyślnie, zamknij wyłącznik.

**Zapewnij rezerwowe**. W tym podejściu proces klienta wykonuje logikę rezerwową, gdy żądanie kończy się niepowodzeniem, takie jak zwracanie danych w pamięci podręcznej lub wartość domyślna. Jest to podejście odpowiednie dla zapytań i jest bardziej złożone dla aktualizacji lub poleceń.

**Ogranicz liczbę żądań w kolejce**. Klienci powinni również nałożyć górną granicę na liczbę zaległych żądań, które mikrousługa klienta może wysyłać do określonej usługi. Jeśli limit został osiągnięty, prawdopodobnie nie ma sensu wysuwać dodatkowych żądań, a te próby powinny zakończyć się niepowodzeniem natychmiast. Pod względem implementacji zasady [izolacji grodzi](https://github.com/App-vNext/Polly/wiki/Bulkhead) polly mogą być używane do spełnienia tego wymogu. Takie podejście jest zasadniczo przepustnicy równoległości z <xref:System.Threading.SemaphoreSlim> jako implementacji. Pozwala również na "kolejkę" poza grodzią. Można proaktywnie zrzucić nadmiar obciążenia jeszcze przed wykonaniem (na przykład, ponieważ pojemność jest uważana za pełną). To sprawia, że jego odpowiedzi na niektóre scenariusze awarii szybciej niż wyłącznik będzie, ponieważ wyłącznik czeka na awarie. Obiekt BulkheadPolicy w [Polly](http://www.thepollyproject.org/) ujawnia, jak pełne są grodzi i kolejki i oferuje zdarzenia na przepełnienie, dzięki czemu może być również używany do kierowania automatycznego skalowania poziomego.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wzorce odporności**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Dodawanie odporności i optymalizacja wydajności**\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Grodzi.** Repozytorium GitHub. Implementacja z zasadą Polly.\
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Projektowanie odpornych aplikacji na platformę Azure**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **Obsługa błędów przejściowych**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Poprzedni](handle-partial-failure.md)
>[następny](implement-retries-exponential-backoff.md)
