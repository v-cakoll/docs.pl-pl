---
title: Strategie dotyczące obsługi częściowych niepowodzeń
description: Poznaj kilka strategii w celu bezpiecznego obsługi błędów częściowych.
ms.date: 10/16/2018
ms.openlocfilehash: e96fe99ab44b924460e01abaad30aa3e2432117a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296048"
---
# <a name="strategies-to-handle-partial-failure"></a>Strategie obsługi awarii częściowej

Poniżej przedstawiono strategie postępowania w przypadku awarii częściowych.

**Używaj komunikacji asynchronicznej (na przykład komunikacja oparta na komunikatach) między mikrousługami wewnętrznymi**. Zdecydowanie zaleca się, aby nie tworzyć długich łańcuchów synchronicznych wywołań HTTP w ramach wewnętrznych mikrousług, ponieważ niewłaściwy projekt będzie ostatecznie stanowić główną przyczynę nieprawidłowej awarii. W przeciwieństwie do komunikacji frontonu między aplikacjami klienckimi a pierwszym poziomem mikrousług lub z szczegółowymi bramami interfejsu API zaleca się używanie tylko komunikacji asynchronicznej (opartej na komunikatach) po wcześniejszym żądaniu początkowym/ cykl odpowiedzi dla mikrousług wewnętrznych. Spójność ostateczna i architektury sterowane zdarzeniami pomogą zminimalizować skutki działania programu Ripple. Te podejścia powodują wymuszenie wyższego poziomu autonomii mikrousługi i w związku z tym uniemożliwiają zanotowanie tego problemu.

**Użyj ponownych prób przy użyciu wykładniczej wycofywania**. Ta technika pozwala uniknąć krótkich i sporadycznych błędów przez wykonanie wywołania ponawianie próby określoną liczbę razy, na wypadek gdy usługa była niedostępna tylko przez krótki czas. Może to być spowodowane sporadycznymi problemami z siecią lub przeniesieniem mikrousługi/kontenera do innego węzła w klastrze. Jeśli jednak te ponowne próby nie są prawidłowo zaprojektowane z wyłącznikami, można pogłębić efekty programu Ripple, ostatecznie nawet powodując [odmowę usługi (DOS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

Obejść **limity czasu sieci**. Ogólnie rzecz biorąc klienci powinni być zaprojektowani tak, aby nie blokowały się w nieskończoność, a zawsze używać limitów czasu podczas oczekiwania na odpowiedź. Użycie limitów czasu gwarantuje, że zasoby nigdy nie są powiązane w nieskończoność.

**Użyj wzorca wyłącznika**. W tym podejściu proces klienta śledzi liczbę żądań zakończonych niepowodzeniem. W przypadku przekroczenia skonfigurowanego limitu wartość "wyłącznik" spowoduje, że dalsze próby zakończą się niepowodzeniem. (Jeśli duża liczba żądań kończy się niepowodzeniem, sugeruje to, że usługa jest niedostępna i że żądania wysyłania nie są bezpunktowe). Po upływie limitu czasu klient powinien ponowić próbę, a jeśli nowe żądania zakończą się pomyślnie, Zamknij wyłącznika.

**Podaj rezerwy**. W tym podejściu proces klienta wykonuje logikę rezerwową, gdy żądanie nie powiedzie się, takie jak zwrócenie danych w pamięci podręcznej lub wartości domyślnej. Jest to podejście odpowiednie dla zapytań i jest bardziej skomplikowane dla aktualizacji lub poleceń.

**Ogranicz liczbę żądań umieszczonych w kolejce**. Klienci powinni również wprowadzić górną granicę liczby oczekujących żądań wysyłanych przez mikrousługę klienta do określonej usługi. Jeśli limit został osiągnięty, najprawdopodobniej nie wskazuje to dodatkowych żądań, a te próby powinny natychmiast zakończyć się niepowodzeniem. W warunkach implementacji zasady [izolacji Polly grodzi](https://github.com/App-vNext/Polly/wiki/Bulkhead) mogą służyć do spełnienia tego wymagania. To podejście jest zasadniczo przetwarzanie równoległe ograniczeniem <xref:System.Threading.SemaphoreSlim> do wdrożenia. Umożliwia także "queue" poza grodzią. Można aktywnie powiększać nadmierne obciążenie nawet przed wykonaniem (na przykład, ponieważ pojemność jest uznawana za zapełnienie). Powoduje to, że odpowiedź na niektóre scenariusze awarii jest szybsza niż wyłącznika, ponieważ wyłącznik czeka na błędy. Obiekt BulkheadPolicy w [Polly](http://www.thepollyproject.org/) uwidacznia, jak pełen grodzię i kolejkę są, i oferuje zdarzenia w przepełnieniu, tak aby można go było również używać do tworzenia zautomatyzowanego skalowania w poziomie.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wzorce odporności**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Dodawanie odporności i Optymalizowanie wydajności**\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Bulkhead.** Repozytorium GitHub. Implementacja z zasadami Polly. \
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Projektowanie odpornych aplikacji na platformę Azure**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **Obsługa błędów przejściowych**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Poprzedni](handle-partial-failure.md)Następny
>[](implement-retries-exponential-backoff.md)
