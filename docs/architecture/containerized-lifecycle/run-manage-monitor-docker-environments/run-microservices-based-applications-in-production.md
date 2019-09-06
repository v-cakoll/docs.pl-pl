---
title: Uruchamianie aplikacji złożonych i opartych na mikrousługach w środowiskach produkcyjnych
description: Poznaj najważniejsze składniki do uruchamiania aplikacji opartych na kontenerach w środowisku produkcyjnym
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295464"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Uruchamianie aplikacji złożonych i opartych na mikrousługach w środowiskach produkcyjnych

Aplikacje składające się z wielu mikrousług muszą zostać wdrożone w klastrach programu Orchestrator w celu uproszczenia złożoności wdrożenia i zapewnienia jej działania z punktu widzenia IT. Bez klastra programu Orchestrator nie można wdrożyć i skalować złożonej aplikacji mikrousług.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Wprowadzenie do koordynatorów, harmonogramów i klastrów kontenerów

Wcześniej w tej książce elektronicznej, *klastry* i *harmonogramy* zostały wprowadzone w ramach dyskusji na temat architektury oprogramowania i programowania. Kubernetes i Service Fabric są przykładami klastrów platformy Docker. Oba te koordynatorzy mogą działać jako część infrastruktury udostępnianej przez usługę Microsoft Azure Kubernetes.

Gdy aplikacje są skalowane w wielu systemach hosta, możliwość zarządzania każdym systemem hosta i nieabstrakcyjna złożoność podstawowej platformy staną się atrakcyjne. To dokładnie, co zapewnia koordynatorów i harmonogramów. Na koniec Przyjrzyjmy się tutaj:

- **Harmonogramy**. "Planowanie" oznacza możliwość, aby administrator ładował plik usługi do systemu hosta, który ustanawia sposób uruchamiania określonego kontenera. Uruchamianie kontenerów w klastrze platformy Docker jest nazywane planowaniem. Chociaż planowanie odnosi się do konkretnego aktu załadowania definicji usługi, w bardziej ogólnym sensie, harmonogramy są odpowiedzialne za Podłączanie do systemu inicjowania hosta w celu zarządzania usługami w dowolnej wymaganej pojemności.

   Harmonogram klastra ma wiele celów: wydajnie korzysta z zasobów klastra, pracując z ograniczeniami umieszczania podaną przez użytkownika, co pozwala na szybkie zaplanowanie aplikacji w stanie oczekiwania, co sprawia, że jest to niezawodne, a zawsze dostępne.

- **Koordynatorzy**. Platformy zwiększają możliwości zarządzania cyklem życia w przypadku złożonych obciążeń wielokontenerowych wdrożonych w klastrze hostów. Dzięki abstrakcji infrastruktury hosta narzędzia aranżacji zapewniają użytkownikom sposób traktowania całego klastra jako jednego celu wdrożenia.

   Proces aranżacji obejmuje narzędzia i platformę, która umożliwia automatyzację wszystkich aspektów zarządzania aplikacjami od początkowej rozmieszczenia lub wdrożenia na kontener; przeniesienie kontenerów na różne hosty w zależności od jego kondycji lub wydajności hosta; wersje i aktualizacje stopniowe oraz funkcje monitorowania kondycji obsługujące skalowanie i przełączanie w tryb failover; i wiele innych.

   Aranżacja to obszerny termin, który odnosi się do planowania kontenerów, zarządzania klastrami i ewentualnej aprowizacji dodatkowych hostów.

Możliwości zapewniane przez koordynatorów i harmonogramów są skomplikowane do tworzenia i opracowywania od podstaw, dlatego zazwyczaj warto używać rozwiązań aranżacji oferowanych przez dostawców.

>[!div class="step-by-step"]
>[Poprzedni](index.md)Następny
>[](manage-production-docker-environments.md)
