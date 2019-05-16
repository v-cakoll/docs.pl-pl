---
title: Aplikacje SOA
description: Mieć na uwadze kontenerów można też opcji wdrożenia przydatne w przypadku aplikacji SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644762"
---
# <a name="service-oriented-applications"></a>Aplikacje zorientowane na usługę

Architektury zorientowanej na usługi (SOA) była termin nadmiernego obciążenia, który przeznaczone wiele różnych rzeczy do różnych osób. Jednak jako uniwersalność, SOA oznacza, że struktury architekturę aplikacji przez podzielenie go na kilka usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typów, takich jak podsystemów lub w innych przypadkach, w jak warstwy.

Obecnie te usługi można wdrożyć jako kontenery platformy Docker, które rozwiązywania problemów związanych z wdrażaniem, ponieważ wszystkie zależności są uwzględnione w obrazie kontenera. Jednak jeśli potrzebne jest skalowanie w poziomie SOAs, może wystąpić wyzwania Jeśli wdrażasz na podstawie jednego wystąpienia. Ten problem można obsługiwać przy użyciu klastra oprogramowania lub koordynatora Docker. Przyjrzymy koordynatorów bardziej szczegółowo w następnej sekcji, gdy będziemy eksplorować metody mikrousług.

Kontenery platformy docker są przydatne (ale nie jest wymagane) dla bardziej zaawansowanych architektur mikrousług i tradycyjnych architekturach zorientowane na usługę.

Na koniec dnia rozwiązań klastrowych kontenera są przydatne do obu tradycyjna architektura SOA i bardziej zaawansowanych architektury mikrousług, w której każda mikrousługa jest właścicielem swój model danych. A dzięki wielu baz danych, również można skalować w poziomie warstwy danych, a nie Praca z bazami danych monolityczne, udostępniane przez usługi SOA. Jednak dyskusję na temat dzielenia danych dotyczy wyłącznie architektury i projektu.

>[!div class="step-by-step"]
>[Poprzednie](state-and-data-in-docker-applications.md)
>[dalej](orchestrate-high-scalability-availability.md)
