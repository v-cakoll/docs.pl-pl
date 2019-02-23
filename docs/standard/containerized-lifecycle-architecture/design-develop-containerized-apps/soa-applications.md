---
title: Aplikacje SOA
description: Mieć na uwadze kontenerów można też opcji wdrożenia przydatne w przypadku aplikacji SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 353ba738143b7dcd92c7c75ac27ea6a7370f9da6
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745836"
---
# <a name="service-oriented-applications"></a>Aplikacje zorientowane na usługę

Architektury zorientowanej na usługi (SOA) była termin nadmiernego obciążenia, który przeznaczone wiele różnych rzeczy do różnych osób. Jednak jako uniwersalność, SOA oznacza, że struktury architekturę aplikacji przez podzielenie go na kilka usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typów, takich jak podsystemów lub w innych przypadkach, w jak warstwy.

Obecnie te usługi można wdrożyć jako kontenery platformy Docker, które rozwiązywania problemów związanych z wdrażaniem, ponieważ wszystkie zależności są uwzględnione w obrazie kontenera. Jednak gdy zachodzi potrzeba skalowanie w poziomie SOAs, może wystąpić wyzwaniom wdrażania na podstawie jednego wystąpienia. Ten problem można obsługiwać przy użyciu klastra oprogramowania lub koordynatora Docker. Przyjrzymy koordynatorów bardziej szczegółowo w następnej sekcji, gdy będziemy eksplorować metody mikrousług.

Kontenery platformy docker są przydatne (ale nie jest wymagane) dla bardziej zaawansowanych architektur mikrousług i tradycyjnych architekturach zorientowane na usługę.

Na koniec dnia rozwiązań klastrowych kontenera są przydatne do obu tradycyjna architektura SOA i bardziej zaawansowanych architektury mikrousług, w której każda mikrousługa jest właścicielem swój model danych. A dzięki wielu baz danych, również można skalować w poziomie warstwy danych, a nie Praca z bazami danych monolityczne, udostępniane przez usługi SOA. Jednak dyskusję na temat dzielenia danych dotyczy wyłącznie architektury i projektu.

>[!div class="step-by-step"]
>[Poprzednie](state-and-data-in-docker-applications.md)
>[dalej](orchestrate-high-scalability-availability.md)
