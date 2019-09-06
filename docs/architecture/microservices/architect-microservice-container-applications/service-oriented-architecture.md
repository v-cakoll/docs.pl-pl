---
title: Architektura zorientowana na usługi
description: Poznaj podstawowe różnice między mikrousługami i architekturą zorientowaną na usługi (SOA).
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296216"
---
# <a name="service-oriented-architecture"></a>Architektura zorientowana na usługi

Architektura zorientowana na usługi (SOA) była nadstosowana i ma różne znaczenie dla różnych osób. Jednak jako typowy mianownik, SOA oznacza, że tworzysz strukturę aplikacji, tworząc ją w wielu usługach (najczęściej jako usługi HTTP), które mogą być klasyfikowane jako różne typy, takie jak podsystemy lub warstwy.

Te usługi można teraz wdrożyć jako kontenery platformy Docker, co rozwiązuje problemy z wdrażaniem, ponieważ wszystkie zależności są zawarte w obrazie kontenera. Jeśli jednak chcesz skalować w górę aplikacje SOA, możesz mieć problemy ze skalowalnością i dostępnością w przypadku wdrażania na podstawie jednego hosta platformy Docker. Jest to miejsce, w którym można znaleźć oprogramowanie do klastrowania platformy Docker lub programu Orchestrator, jak wyjaśniono w kolejnych sekcjach, w których opisano podejścia do wdrożenia dla mikrousług.

Kontenery platformy Docker są przydatne (ale nie są wymagane) dla tradycyjnych architektur zorientowanych na usługę i bardziej zaawansowanych architektur mikrousług.

Mikrousługi pochodzą z SOA, ale SOA różni się od architektury mikrousług. Funkcje takie jak duże centralne brokerzy, centralne Koordynatory na poziomie organizacji, a [Service Bus Enterprise (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) są typowe w SOA. Jednak w większości przypadków są to antywzorce w społeczności mikrousług. W rzeczywistości niektórzy użytkownicy twierdzili, że "architektura mikrousług jest w pełni gotowa."

Ten przewodnik koncentruje się na mikrousługach, ponieważ podejście SOA jest mniej opisowe niż wymagania i techniki używane w architekturze mikrousług. Jeśli wiesz, jak utworzyć aplikację opartą na mikrousługach, wiesz również, jak utworzyć prostsze aplikacje zorientowane na usługę.

>[!div class="step-by-step"]
>[Poprzedni](docker-application-state-data.md)Następny
>[](microservices-architecture.md)
