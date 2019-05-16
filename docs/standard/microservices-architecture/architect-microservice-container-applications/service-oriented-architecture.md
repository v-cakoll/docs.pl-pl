---
title: Architektura zorientowana na usługi
description: Dowiedz się, podstawowe różnice między mikrousług i architektury zorientowanej na usługi (SOA).
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640068"
---
# <a name="service-oriented-architecture"></a>Architektura zorientowana na usługi

Dotycząca architektury zorientowanej na usługi (SOA) był nadmiernego obciążenia termin i spowodował, że różne dla różnych osób. Jednak jako uniwersalność, SOA oznacza, że struktury aplikacji przez podzielenie go na wiele usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane jako różnych typów, takich jak podsystemów lub warstwy.

Te usługi można teraz wdrażać jako kontenery platformy Docker, która rozwiązuje problemy z wdrażaniem, ponieważ wszystkie zależności są uwzględnione w obrazie kontenera. Po musisz skalować aplikacje SOA, Niewykluczone, że skalowalności i dostępności wyzwania, Jeżeli wdrażasz oparte na jednym hostów platformy Docker. Jest to gdzie oprogramowania klastra Docker lub orchestrator może pomóc, zgodnie z opisem w kolejnych sekcjach, w której opisano metody wdrażania mikrousług.

Kontenery platformy docker są przydatne (ale nie jest wymagane) dla bardziej zaawansowanych architektur mikrousług i tradycyjnych architekturach zorientowane na usługę.

Mikrousługi dziedziczyć SOA, ale SOA różni się od architektury mikrousług. Funkcje, takie jak duża brokerów centralnej, centralna koordynatorów na poziomie organizacji i [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) jest typowy w SOA. Jednak w większości przypadków są to niezalecane wzorce dotyczące społeczności mikrousług. W rzeczywistości niektórzy dokumentu uważają, że "architekturze mikrousług jest SOA wykonać".

Ten przewodnik koncentruje się na mikrousługach, ponieważ metoda SOA jest mniej normatywne niż wymagania i technik stosowanych w ramach architektury mikrousługi. Jeśli znasz sposób tworzenia aplikacji opartych na mikrousługach, możesz również wie, jak tworzyć prostsze aplikacji usługowych.

>[!div class="step-by-step"]
>[Poprzednie](docker-application-state-data.md)
>[dalej](microservices-architecture.md)
