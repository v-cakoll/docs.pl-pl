---
title: Aplikacje SOA
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 7f88daaf0787cf780e7ab9602f35ae4e6ab8308c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155317"
---
# <a name="soa-applications"></a>Aplikacje SOA

SOA nadmiernego obciążenia termin został i jest przeznaczone tak wiele różnych rzeczy do różnych osób. Ale co najmniej i uniwersalność, SOA, lub orientacji usługi, mean architekturę aplikacji przez podzielenie go w wielu usługach (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typach tej można struktury, takie jak podsystemów lub w innych przypadkach jako warstwy.

Obecnie można wdrożyć te usługi jako kontenery platformy Docker, która rozwiązuje problemów związanych z wdrażaniem, ponieważ wszystkie zależności są zawarte w obrębie obrazu kontenera. Jednak gdy trzeba skalowalnego w poziomie SOAs mogą wystąpić problemy wdrażania na podstawie jednego wystąpienia. Jest to, gdzie klastra oprogramowania lub koordynatora Docker pomoże Ci. Omówimy to bardziej szczegółowo w następnej sekcji podczas omówiony podejścia mikrousług.

Na koniec dnia rozwiązań klastrowych kontenera są przydatne, dla obu tradycyjna architektura SOA lub bardziej zaawansowanych architektury mikrousług, w której każda mikrousługa jest właścicielem swój model danych. A dzięki wielu baz danych, możesz też może skalowalnego w poziomie warstwy danych, a nie Praca z bazami danych monolityczne, udostępniane przez usługi SOA. Jednak dyskusję na temat dzielenia danych dotyczy wyłącznie architektury i projektu.

>[!div class="step-by-step"]
>[Poprzednie](state-and-data-in-docker-applications.md)
>[dalej](orchestrate-high-scalability-availability.md)