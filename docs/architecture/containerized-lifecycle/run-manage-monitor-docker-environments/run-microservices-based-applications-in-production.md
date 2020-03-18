---
title: Uruchamianie aplikacji złożonych i opartych na mikrousługach w środowiskach produkcyjnych
description: Poznaj kluczowe składniki do uruchamiania aplikacji opartych na kontenerach w środowisku produkcyjnym
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295464"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Uruchamianie aplikacji złożonych i opartych na mikrousługach w środowiskach produkcyjnych

Aplikacje składające się z wielu mikrousług muszą zostać wdrożone w klastrach aranżatora w celu uproszczenia złożoności wdrożenia i zwiększenia rentowności z punktu widzenia IT. Bez klastra koordynatora byłoby trudne do wdrożenia i skalowania w poziomie złożonych aplikacji mikrousług.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Wprowadzenie do koordynatorów, planistów i klastrów kontenerów

Wcześniej w tym e-book, *klastry* i *harmonogramy* zostały wprowadzone w ramach dyskusji na temat architektury oprogramowania i rozwoju. Kubernetes i sieci szkieletowej usług są przykładami klastrów platformy Docker. Oba te koordynatorów można uruchomić jako część infrastruktury świadczonej przez usługę Kubernetes platformy Microsoft Azure.

Gdy aplikacje są skalowane w sposób skalowany w sposób skalowany w czasie w wielu systemach hosta, możliwość zarządzania każdym systemem hosta i abstrakcyjne od złożoności platformy podstawowej staje się atrakcyjna. To jest dokładnie to, co zapewniają koordynatorzy i planiści. Przyjrzyjmy się im pokrótce:

- **Harmonogramy**."Planowanie" odnosi się do możliwości załadowania przez administratora pliku usługi do systemu hosta, który określa sposób uruchamiania określonego kontenera. Uruchamianie kontenerów w klastrze platformy Docker jest zwykle nazywane planowaniem. Chociaż planowanie odnosi się do określonego aktu ładowania definicji usługi, w sensie bardziej ogólnym, planiści są odpowiedzialni za podłączanie do systemu init hosta w celu zarządzania usługami w dowolnej pojemności potrzebnej.

   Harmonogram klastrów ma wiele celów: efektywne korzystanie z zasobów klastra, praca z ograniczeniami umieszczania dostarczonymi przez użytkownika, szybkie planowanie aplikacji, aby nie pozostawiać ich w stanie oczekiwania, posiadanie pewnego stopnia "uczciwości", niezawodne błędy i zawsze dostępne.

- **Orkiestratorzy**.Platformy rozszerzają możliwości zarządzania cyklem życia na złożone obciążenia wielokontenerowe wdrożone w klastrze hostów. Przez abstrakcję infrastruktury hosta, narzędzia aranżacji dać użytkownikom sposób traktowania całego klastra jako jeden cel wdrożenia.

   Proces aranżacji obejmuje narzędzia i platformę, która może zautomatyzować wszystkie aspekty zarządzania aplikacjami z początkowego rozmieszczenia lub wdrożenia na kontener; przenoszenie kontenerów do różnych hostów w zależności od kondycji lub wydajności jego hosta; przechowywanie wersji i stopniowe aktualizacje oraz funkcje monitorowania kondycji, które obsługują skalowanie i praca awaryjna; i wiele innych.

   Aranżacja to szerokie określenie, które odnosi się do planowania kontenerów, zarządzania klastrami i ewentualnie inicjowania obsługi administracyjnej dodatkowych hostów.

Możliwości dostarczane przez koordynatorów i planistów są złożone do opracowania i tworzenia od podstaw, dlatego zwykle chcesz użyć rozwiązań aranżacyjnych oferowanych przez dostawców.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](manage-production-docker-environments.md)
