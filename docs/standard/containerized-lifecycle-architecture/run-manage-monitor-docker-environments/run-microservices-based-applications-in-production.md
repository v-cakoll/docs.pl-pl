---
title: Uruchom złożony i mikrousług aplikacji w środowisku produkcyjnym
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b4192ff1d67a3f70bb5eeb9a36245cfd35bafb53
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105634"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Uruchom złożony i mikrousług aplikacji w środowisku produkcyjnym

Aplikacje składane przez wiele mikrousług muszą zostać wdrożone w klastrach orchestrator uproszczenie złożoności wdrażania, aby działało z punktu widzenia IT. Bez klastra orchestrator będą bardzo trudne do wdrażania i skalowania w poziomie aplikacji złożonych mikrousług.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Wprowadzenie do orchestrators, planiści i klastrów kontenera

Wcześniej w tym Książka elektroniczna wprowadzono *klastrów* i *planiści* jako część dyskusji na architekturę oprogramowania i rozwoju. Przykłady klastrów Docker są Docker Swarm i System operacyjny centrum danych Mesosphere (DC/OS). Oba te można uruchomić jako część infrastrukturę usługi kontenera platformy Microsoft Azure.

Aplikacje są skalowalne w poziomie w wielu systemach hosta, możliwość zarządzania każdym systemie hosta i abstrakcyjnej optymalizacji złożoność podstawowej platformy staje się atrakcyjne. To dokładnie czego zawiera orchestrators i transfery danych. Spójrzmy krótki ich tutaj:

-   **Planiści *** *"Planowania" odwołuje się do możliwości, aby administrator mógł załadować pliku usługi w systemie hosta, który określa sposób uruchamiania określonego kontenera. Uruchamianie kontenerów w klastrze Docker zwykle nazywane planowania. Chociaż planowanie odwołuje się do określonego zestawu act ładowania definicji usługi, w tym sensie bardziej ogólne transfery danych jest odpowiedzialny za przechwytywanie systemu init hosta do zarządzania usługami, niezależnie od pojemności potrzebne.

Harmonogram klastra ma wiele celów: efektywne korzystanie z zasobów klastra, Praca z ograniczeń umieszczania dostarczone przez użytkownika, planowania aplikacjom szybko nie pozostaw je w stanie oczekiwania, o stopniu "sprawiedliwe przydzielanie zasobów," są niezawodne błędy, i zawsze być dostępna.

-   **Orchestration *** *platform rozszerzyć funkcje zarządzania cyklem życia w przypadku złożonych, multicontainer obciążeń wdrożonych w klastrze hostów. Przez abstrakcyjność infrastruktury hosta, narzędzi orchestration nadaj sposób traktować jako cel wdrożenia pojedynczego całego klastra.

Proces aranżacji obejmuje narzędzi i platformy, który można zautomatyzować wszystkie aspekty zarządzania aplikacjami z początkowej umieszczania lub wdrażania na kontenera; Przeniesienie kontenerów na różnych hostach w zależności od jej hosta kondycji i wydajności; przechowywanie wersji i stopniowego aktualizacje i funkcje, które obsługują skalowanie i trybu failover; monitorowania kondycji i wiele innych.

Aranżacja to szerokie termin odnoszący się do kontenera planowania zarządzania klastrem i prawdopodobnie udostępniania dodatkowych hostów.

Możliwości zapewniane przez orchestrators i transfery danych są bardzo złożone do opracowywania i tworzyć od podstaw i w związku z tym zazwyczaj czy mają być stosowania rozwiązań aranżacji oferowane przez dostawców.


>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](manage-production-docker-environments.md)
