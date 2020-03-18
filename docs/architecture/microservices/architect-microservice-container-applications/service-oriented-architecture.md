---
title: Architektura zorientowana na usługi
description: Poznaj podstawowe różnice między mikrousługami a architekturą zorientowaną na usługi (SOA).
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296216"
---
# <a name="service-oriented-architecture"></a>Architektura zorientowana na usługi

Architektura zorientowana na usługi (SOA) była nadużywanym terminem i oznaczała różne rzeczy dla różnych ludzi. Ale jako wspólny mianownik SOA oznacza, że struktura aplikacji przez rozkładanie go na wiele usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane jako różne typy, takie jak podsystemy lub warstwy.

Te usługi można teraz wdrożyć jako kontenery platformy Docker, co rozwiązuje problemy z wdrażaniem, ponieważ wszystkie zależności są uwzględnione w obrazie kontenera. Jednak gdy trzeba skalować w górę aplikacji SOA, może być skalowalność i dostępność wyzwania, jeśli wdrażasz na podstawie pojedynczych hostów platformy Docker. W tym miejscu oprogramowanie do klastrowania platformy Docker lub koordynator może ci pomóc, jak wyjaśniono w kolejnych sekcjach, w których opisano metody wdrażania mikrousług.

Kontenery platformy Docker są przydatne (ale nie są wymagane) zarówno dla tradycyjnych architektur zorientowanych na usługi, jak i bardziej zaawansowanych architektur mikrousług.

Mikrousługi pochodzą z SOA, ale SOA różni się od architektury mikrousług. Funkcje takie jak duzi centralni brokerzy, centralni koordynatorzy na poziomie organizacji i [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) są typowe w SOA. Ale w większości przypadków są to anty-wzorce w społeczności mikrousług. W rzeczywistości niektórzy ludzie twierdzą, że "architektura mikrousług jest SOA zrobić dobrze."

Ten przewodnik koncentruje się na mikrousług, ponieważ podejście SOA jest mniej nakazowe niż wymagania i techniki używane w architekturze mikrousług. Jeśli wiesz, jak utworzyć aplikację opartą na mikrousługach, wiesz również, jak utworzyć prostszą aplikację zorientowaną na usługi.

>[!div class="step-by-step"]
>[Poprzedni](docker-application-state-data.md)
>[następny](microservices-architecture.md)
