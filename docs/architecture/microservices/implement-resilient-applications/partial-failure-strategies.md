---
title: Strategie dotyczące obsługi częściowych niepowodzeń
description: Poznaj kilka strategii obsługi częściowych awarii z wdziękiem.
ms.date: 10/16/2018
ms.openlocfilehash: e96fe99ab44b924460e01abaad30aa3e2432117a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296048"
---
# <a name="strategies-to-handle-partial-failure"></a>Strategie obsługi częściowej awarii

Strategie radzenia sobie z częściowymi awariami są następujące.

**Użyj komunikacji asynchronicznej (na przykład komunikacji opartej na wiadomościach) w mikrousługach wewnętrznych**. Zaleca się, aby nie tworzyć długich łańcuchów synchronicznych wywołań HTTP w mikrousługach wewnętrznych, ponieważ ten niepoprawny projekt ostatecznie stanie się główną przyczyną nieprawidłowych awarii. Wręcz przeciwnie, z wyjątkiem komunikacji frontonu między aplikacjami klienckimi i pierwszego poziomu mikrousług lub szczegółowych bram interfejsu API, zaleca się używać tylko komunikacji asynchronicznej (opartej na wiadomościach) po zakończeniu początkowego cyklu żądania/odpowiedzi w mikrousługach wewnętrznych. Spójność ostateczna i architektury oparte na zdarzeniach pomogą zminimalizować efekty tętnienia. Te podejścia wymuszają wyższy poziom autonomii mikrousług i w związku z tym zapobiegają problemowi, który został wymieniony w tym miejscu.

**Użyj ponownych prób z wykładniczym wycofywaniem**. Ta technika pomaga uniknąć krótkich i przerywanych błędów, wykonując próby wywołania określoną liczbę razy, w przypadku, gdy usługa nie była dostępna tylko przez krótki czas. Może to nastąpić z powodu sporadycznych problemów z siecią lub gdy mikrousługi/kontener a zostanie przeniesiony do innego węzła w klastrze. Jednakże, jeśli te ponownych prób nie są poprawnie zaprojektowane z wyłączników, może to pogorszyć efekty tętnienia, ostatecznie nawet powodując [Denial of Service (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Obejść timeouts sieci**. Ogólnie rzecz biorąc klienci powinni być zaprojektowane, aby nie blokować przez czas nieokreślony i zawsze używać timeouts podczas oczekiwania na odpowiedź. Korzystanie z timeouts zapewnia, że zasoby nigdy nie są wiązane w nieskończoność.

**Użyj wzorca wyłącznika**. W tym podejściu proces klienta śledzi liczbę żądań nie powiodło się. Jeśli poziom błędu przekracza skonfigurowany limit, "wyłącznik" posunie się tak, że dalsze próby nie powiedzie się natychmiast. (Jeśli duża liczba żądań nie działa, oznacza to, że usługa jest niedostępna, a wysyłanie żądań jest bezcelowe). Po upływie określonego czasu klient powinien spróbować ponownie i, jeśli nowe żądania są pomyślne, zamknij wyłącznik.

**Zapewnij rezerwowe**. W tym podejściu proces klienta wykonuje logikę rezerwową, gdy żądanie nie powiedzie się, takie jak zwracanie buforowanych danych lub wartość domyślna. Jest to podejście odpowiednie dla zapytań i jest bardziej złożone dla aktualizacji lub poleceń.

**Ogranicz liczbę żądań w kolejce**. Klienci powinni również nałożyć górną granicę na liczbę zaległych żądań, które mikrousługa klienta może wysyłać do określonej usługi. Jeśli limit został osiągnięty, prawdopodobnie nie ma sensu wysyłać dodatkowych żądań, a te próby powinny zakończyć się natychmiastowym niepowodzeniem. Pod względem implementacji polly [zasady izolacji grodziowej](https://github.com/App-vNext/Polly/wiki/Bulkhead) może służyć do spełnienia tego wymagania. Takie podejście jest zasadniczo parallelization przepustnicy z <xref:System.Threading.SemaphoreSlim> jako implementacji. Pozwala również na "kolejkę" poza grodzią. Można proaktywnie zrzucić nadmiar obciążenia jeszcze przed wykonaniem (na przykład dlatego, że pojemność jest uważana za pełną). To sprawia, że jego odpowiedź na niektóre scenariusze awarii szybciej niż wyłącznik będzie, ponieważ wyłącznik czeka na awarie. BulkheadPolicy obiektu w [Polly](http://www.thepollyproject.org/) ujawnia, jak pełne są grodzi i kolejki i oferuje zdarzenia na przepełnienie, dzięki czemu może również służyć do napędu automatyczne skalowanie w poziomie.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wzorce odporności**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Zwiększanie odporności i optymalizacji wydajności**\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Grodzi.** Repozytorium GitHub. Implementacja z zasadami Polly.\
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Projektowanie odpornych aplikacji dla platformy Azure**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **Przemijająca obsługa usterek**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Poprzedni](handle-partial-failure.md)
>[następny](implement-retries-exponential-backoff.md)
