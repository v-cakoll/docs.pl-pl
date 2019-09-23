---
title: Odporność natywną w chmurze
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Natywna odporność w chmurze
ms.date: 06/30/2019
ms.openlocfilehash: 680542abc5d8c43c577321d5ae834f0a13290da3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184842"
---
# <a name="cloud-native-resiliency"></a>Odporność natywną w chmurze

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Odporność to zdolność systemu do reagowania na awarie i nadal pozostaje funkcjonalna. Nie ma on na uniknięcie błędu. Jednak przyjmujemy, że ten błąd jest nieunikniony w systemach opartych na chmurze i kompilowanie aplikacji w celu reagowania na nią. Celem odporności jest przywrócenie aplikacji do stanu w pełni funkcjonalnym po awarii.

W przeciwieństwie do tradycyjnych aplikacji monolitycznych, gdzie wszystko działa razem w pojedynczym procesie, systemy natywne w chmurze stosują architekturę rozproszoną, jak pokazano na rysunku 6-1:

![Rozproszone środowisko natywne w chmurze](./media/distributed-cloud-native-environment.png)

**Rysunek 6-1.** Rozproszone środowisko natywne w chmurze

Na poprzedniej ilustracji należy zwrócić uwagę na to, jak każdy klient, mikrousługa i [usługa tworzenia kopii zapasowych](https://12factor.net/backing-services) oparte na chmurze wykonuje jako oddzielny proces uruchomiony na różnych serwerach, a wszystkie komunikują się za pośrednictwem wywołań sieciowych.

Co może być niewłaściwe?

- Nieoczekiwane [opóźnienie sieci](https://www.techopedia.com/definition/8553/network-latency).
- [Błędy przejściowe](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (tymczasowe błędy łączności sieciowej).
- Blokowanie przez długotrwałą operację synchroniczną.
- Proces hosta, który uległ awarii i jest ponownie uruchamiany lub przenoszony.
- Przeciążona mikrousługa, która nie może odpowiadać przez krótki czas.
- Operacja DevOps w locie, taka jak operacja aktualizacji lub skalowania.
- Operacja programu Orchestrator, taka jak przeniesienie usługi z jednego węzła do drugiego.
- Awarie sprzętowe sprzętu z asortymentu.

W przypadku wdrażania usług rozproszonych w infrastrukturze opartej na chmurze czynniki z poprzedniej listy stają się bardzo prawdziwe i należy się z nimi przydzielić i rozwijać, aby z nich pracować.

W systemie rozproszonym w niewielkim stopniu awaria nie będzie mniejsza, ale w przypadku skalowania w górę i w poziomie można oczekiwać więcej z tych problemów do punktu, w którym częściowa awaria stanie się normalną operacją.

W związku z tym aplikacja i infrastruktura muszą być odporne na błędy. W poniższych sekcjach opisano techniki obronne, które można dodać do aplikacji, oraz wbudowane funkcje w chmurze, których można użyć, aby pomóc w wykorzystaniu punktorów przez użytkownika.

>[!div class="step-by-step"]
>[Poprzedni](azure-data-storage.md)
>[Następny](application-resiliency-patterns.md)
