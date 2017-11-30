---
title: Aplikacje SOA
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 92a69ccd18759be3b319395d8609d65bb6d3e1b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="soa-applications"></a>Aplikacje SOA

SOA został termin nadmiernego obciążenia i przewidziany tak wiele różnych rzeczy do innej osoby. Ale co najmniej i najprostszy, SOA, lub orientacji usługi, średniej architektury aplikacji, decomposing go w wielu usługach (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typów tej możesz struktury, takie jak podsystemów lub warstwy z informacjami w innych przypadkach jako.

Obecnie można wdrożyć tych usług jako kontenery Docker, którego rozwiązuje problemy związane z wdrożenia, ponieważ wszystkie zależności są uwzględniane w obrazie kontenera. Jednak gdy musisz SOAs skalowalnego w poziomie, mogą wystąpić problemy wdrażania na podstawie pojedynczego wystąpienia. Jest to, gdzie Docker klastrowania lub oprogramowania orchestrator pomoże Ci. Przyjrzymy to bardziej szczegółowo w następnej sekcji podczas omówione podejścia mikrousług.

Na koniec dnia rozwiązań klastrowych kontenera są przydatne, dla obu tradycyjnych architektura SOA lub bardziej zaawansowanych architektura mikrousług, w której każdy mikrousługi jest właścicielem jego modelu danych. I dzięki użyciu wielu baz danych, możesz również można skalowalnego w poziomie warstwy danych, a nie Praca z wbudowanymi baz danych udostępnionych przez usługi SOA. Omówienie podział danych jest jednak wyłącznie dotyczące architektury i projektu.


>[!div class="step-by-step"]
[Poprzednie] (state-and-data-in-docker-applications.md) [dalej] (organizowania wysoki skalowalność availability.md)
