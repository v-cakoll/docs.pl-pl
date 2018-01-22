---
title: "Strategie dotyczące postępowania z częściowa awarii"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Strategie dotyczące postępowania z częściowa awarii"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: baeeb47dde77ceaa461214f55482d2312d67ccec
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="strategies-for-handling-partial-failure"></a>Strategie dotyczące postępowania z częściowa awarii

Strategie dotyczące postępowania z błędami częściowe są następujące.

**Użyj asynchroniczne komunikacji (na przykład oparta na komunikatach) na wewnętrznej mikrousług**. Stanowczo zaleca nie, aby utworzyć długie łańcuchy synchroniczne wywołania HTTP w wewnętrznych mikrousług, ponieważ tego projektu niepoprawne będzie przestać główną przyczynę awarii zła. Przeciwnie, z wyjątkiem frontonu komunikacji między aplikacjami klienta i pierwszy poziom mikrousług lub szczegółowych bramy interfejsu API, zaleca się do użycia tylko (oparta na komunikatach) komunikacji asynchronicznej raz osiągnęła początkowej żądania / Cykl odpowiedzi przez wewnętrzny mikrousług. Spójność ostateczna i architektur sterowane zdarzeniami pomogą zminimalizować wpływ ripple. Tych metod wymuszania wyższego poziomu Autonomia mikrousługi i w związku z tym zapobiegać problem oznaczane w tym miejscu.

**Ponowne próby za pomocą wykładniczego wycofywania**. Ta technika pozwala uniknąć krótki i błędami okresowymi, wykonując wywołanie ponowi próbę kilka razy, w przypadku, gdy usługa nie jest dostępna tylko w przypadku przez krótki czas. Może to być spowodowane problemami z siecią tymczasowymi lub mikrousługi/kontenera jest przenoszona do innego węzła w klastrze. Jednak jeśli te ponownych prób nie są prawidłowo zaprojektowane z obwodem podziałów, jego pogłębić efekty ripple ostatecznie nawet powodując [przeprowadzenie ataku typu "odmowa usługi" (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Obejść limity czasu sieci**. Ogólnie rzecz biorąc klientów należy tak zaprojektować nie blokuj nieograniczony czas i zawsze używaj przekroczeń limitu czasu podczas oczekiwania na odpowiedź. Korzystanie z limitów czasu zapewnia, że zasoby są nigdy nie blokowana przez nieograniczony czas.

**Użyj wzorca wyłącznika**. W tym podejście procesu klienta śledzi liczbę niepomyślnych żądań. Jeśli częstotliwość błędów przekracza skonfigurowany limit, rund "wyłącznika", aby dalszych prób natychmiast się nie powieść. (Jeśli duża liczba żądań, które kończą się niepowodzeniem, które sugeruje usługa jest niedostępna i że wysyłania żądań jest bezcelowe.) Po upływie limitu czasu klienta należy ponownie i, jeśli nowych żądań nie powiodło się, zamknij wyłącznik.

**Podaj przejścia**. W takie podejście proces klienta sprawdza logiki rezerwowej, gdy żądanie zakończy się niepowodzeniem, takich jak przekazywania danych z pamięci podręcznej lub wartość domyślną. Jest to podejście, które są odpowiednie dla zapytań i jest bardziej złożony dla aktualizacji lub poleceń.

**Ogranicz liczbę żądań w kolejce**. Klienci także powinna nałożyć górnej granicy liczby oczekujących żądań, które mikrousługi klienta mogą wysyłać do określonej usługi. Jeśli został osiągnięty limit, jest prawdopodobnie bezcelowe dokonanie dodatkowych żądań i tymi próbami powinna zakończyć się niepowodzeniem natychmiast. W implementacji, Polly [izolacji grodziowego](https://github.com/App-vNext/Polly/wiki/Bulkhead) zasad może służyć do spełnienia tego wymagania. Ta metoda jest zasadniczo ograniczania paralelizacja z [SemaphoreSlim](https://docs.microsoft.com/dotnet/api/system.threading.semaphoreslim?view=netcore-1.1) jako implementacja. Umożliwia on również "kolejki" poza grodzi. Nadmiarowe obciążenia nawet przed wykonaniem można pozostawia aktywnego, (na przykład, ponieważ za pojemność jest pełna). Dzięki temu można szybciej niż wyłącznika, ponieważ oczekuje wyłącznik niepowodzeń swojej odpowiedzi do pewnych scenariuszy awarii. Obiekt BulkheadPolicy w Polly udostępnia jak Pełna grodziowego są kolejki i zdarzenia oferty na przepełnienie tak mogą służyć do kierowania automatyczne skalowanie w poziomie.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wzorce odporności**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Dodawanie odporności i optymalizacji wydajności**
    [*https://msdn.microsoft.com/library/jj591574.aspx*](https://msdn.microsoft.com/library/jj591574.aspx)

-   **Bulkhead.** Repozytorium GitHub. Wdrożenia z zasadami Polly. \
    [*https://github.com/App-vNext/Polly/wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   **Projektowanie aplikacji odporne na platformie Azure**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)

-   **Obsługa błędów przejściowych**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults>


>[!div class="step-by-step"]
[Poprzednie] (uchwyt partial-failure.md) [dalej] (wdrożenie-ponownych prób wykładniczej backoff.md)
