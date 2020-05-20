---
title: Odporność rozwiązań natywnych dla chmury
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Natywna odporność w chmurze
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: f3aa89e3ae21b13a31f65013b59636b3f931553c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613775"
---
# <a name="cloud-native-resiliency"></a>Odporność rozwiązań natywnych dla chmury

Odporność to zdolność systemu do reagowania na awarie i nadal pozostaje funkcjonalna. Nie dotyczy to unikania awarii, ale akceptowania błędów i konstruowania usług natywnych w chmurze w celu reagowania na nie. Chcesz szybko przywrócić stan w pełni funkcjonalny.

W przeciwieństwie do tradycyjnych aplikacji monolitycznych, gdzie wszystko działa razem w pojedynczym procesie, systemy natywne w chmurze stosują architekturę rozproszoną, jak pokazano na rysunku 6-1:

![Rozproszone środowisko natywne w chmurze](./media/distributed-cloud-native-environment.png)

**Rysunek 6-1.** Rozproszone środowisko natywne w chmurze

Na powyższej ilustracji każda mikrousługa i oparta na chmurze [Usługa do tworzenia kopii zapasowych](https://12factor.net/backing-services) jest wykonywana w osobnym procesie, między infrastrukturą serwera, komunikujących się za pośrednictwem wywołań sieciowych.

W tym środowisku usługa musi być wrażliwa na wiele różnych wyzwań:

- Nieoczekiwane opóźnienie sieci — czas przesyłania żądania usługi do odbiornika i z powrotem.

- [Awarie przejściowe](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) — krótkie Błędy łączności sieciowej.

- Zatorem przez długotrwałą operację synchroniczną.

- Proces hosta, który uległ awarii i jest ponownie uruchamiany lub przenoszony.

- Przeciążona mikrousługa, która nie może odpowiadać przez krótki czas.

- Operacja programu Orchestrator w locie, taka jak uaktualnienie stopniowe lub przeniesienie usługi z jednego węzła do drugiego.

- Awarie sprzętu.

Platformy chmury mogą wykrywać i ograniczać wiele problemów z infrastrukturą. Może on zostać ponownie uruchomiony, przeskalowany w poziomie i nawet rozdystrybuowany do innego węzła.  Aby jednak w pełni korzystać z tej wbudowanej ochrony, należy zaprojektować usługi w celu reagowania na nie i rozwoju w tym środowisku dynamicznym.

W poniższych sekcjach opisano techniki obronne, które mogą wykorzystać usługa i zarządzane zasoby w chmurze w celu zminimalizowania przestojów i przerw w działaniu.

>[!div class="step-by-step"]
>[Poprzedni](elastic-search-in-azure.md) 
> [Dalej](application-resiliency-patterns.md)
