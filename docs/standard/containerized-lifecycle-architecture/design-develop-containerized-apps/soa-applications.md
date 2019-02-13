---
title: Aplikacje SOA
description: Mieć na uwadze kontenerów można też opcji wdrożenia przydatne w przypadku aplikacji SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 4fd39e075c5730cf7fddb0138cdb5267a914c91f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221267"
---
# <a name="soa-applications"></a>Aplikacje SOA

SOA nadmiernego obciążenia termin został i jest przeznaczone tak wiele różnych rzeczy do różnych osób. Ale co najmniej i uniwersalność, SOA, lub orientacji usługi, mean architekturę aplikacji przez podzielenie go w wielu usługach (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typach tej można struktury, takie jak podsystemów lub w innych przypadkach jako warstwy.

Obecnie można wdrożyć te usługi jako kontenery platformy Docker, która rozwiązuje problemów związanych z wdrażaniem, ponieważ wszystkie zależności są zawarte w obrębie obrazu kontenera. Jednak gdy trzeba skalowalnego w poziomie SOAs mogą wystąpić problemy wdrażania na podstawie jednego wystąpienia. Jest to, gdzie klastra oprogramowania lub koordynatora Docker pomoże Ci. Omówimy to bardziej szczegółowo w następnej sekcji podczas omówiony podejścia mikrousług.

Na koniec dnia rozwiązań klastrowych kontenera są przydatne, dla obu tradycyjna architektura SOA lub bardziej zaawansowanych architektury mikrousług, w której każda mikrousługa jest właścicielem swój model danych. A dzięki wielu baz danych, możesz też może skalowalnego w poziomie warstwy danych, a nie Praca z bazami danych monolityczne, udostępniane przez usługi SOA. Jednak dyskusję na temat dzielenia danych dotyczy wyłącznie architektury i projektu.

>[!div class="step-by-step"]
>[Poprzednie](state-and-data-in-docker-applications.md)
>[dalej](orchestrate-high-scalability-availability.md)