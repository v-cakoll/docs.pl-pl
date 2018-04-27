---
title: Aplikacje SOA
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5f60ff2fb1567d08b9e51e14ce5660a8e42f54aa
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="soa-applications"></a>Aplikacje SOA

SOA został termin nadmiernego obciążenia i przewidziany tak wiele różnych rzeczy do innej osoby. Ale co najmniej i najprostszy, SOA, lub orientacji usługi, średniej architektury aplikacji, decomposing go w wielu usługach (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typów tej możesz struktury, takie jak podsystemów lub warstwy z informacjami w innych przypadkach jako.

Obecnie można wdrożyć tych usług jako kontenery Docker, którego rozwiązuje problemy związane z wdrożenia, ponieważ wszystkie zależności są uwzględniane w obrazie kontenera. Jednak gdy musisz SOAs skalowalnego w poziomie, mogą wystąpić problemy wdrażania na podstawie pojedynczego wystąpienia. Jest to, gdzie Docker klastrowania lub oprogramowania orchestrator pomoże Ci. Przyjrzymy to bardziej szczegółowo w następnej sekcji podczas omówione podejścia mikrousług.

Na koniec dnia rozwiązań klastrowych kontenera są przydatne, dla obu tradycyjnych architektura SOA lub bardziej zaawansowanych architektura mikrousług, w której każdy mikrousługi jest właścicielem jego modelu danych. I dzięki użyciu wielu baz danych, możesz również można skalowalnego w poziomie warstwy danych, a nie Praca z wbudowanymi baz danych udostępnionych przez usługi SOA. Omówienie podział danych jest jednak wyłącznie dotyczące architektury i projektu.


>[!div class="step-by-step"]
[Poprzednie] (state-and-data-in-docker-applications.md) [dalej] (organizowania wysoki skalowalność availability.md)
