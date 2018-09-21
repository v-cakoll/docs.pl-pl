---
title: Uruchamianie aplikacji złożonych i opartych na mikrousługach w środowiskach produkcyjnych
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 18e6cb1fb5f496b66c89cb8e009a67894b8a76ad
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540596"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Uruchamianie aplikacji złożonych i opartych na mikrousługach w środowiskach produkcyjnych

Aplikacje składające się przez wiele mikrousług muszą zostać wdrożone w klastrach programu orchestrator, aby uprościć złożoność wdrożenia i przypisz ją jako możliwego do użycia z punktu widzenia IT. Bez klastra usługi orchestrator byłoby bardzo trudne do wdrażania i skalowania w poziomie aplikacji złożonych mikrousług.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Wprowadzenie do koordynatorów, harmonogramów i klastrów kontenerów

Wcześniej w tej książce elektronicznej, wprowadziliśmy *klastrów* i *lotów* jako część dyskusji o architekturze oprogramowania i rozwoju. Przykłady klastrów platformy Docker Swarm i System operacyjny centrum danych Mesosphere (DC/OS). Oba te można uruchomić jako część infrastruktury zapewnianej przez Microsoft usługi Azure Container Service.

Aplikacje są skalowanych w poziomie w wielu systemach hosta, możliwość zarządzania każdym systemie hosta i streszczenie natychmiast złożoność podstawowej platformy staje się atrakcyjne. To dokładnie co zapewniają koordynatorów i transfery danych. Przyjrzyjmy się krótki opis ich tutaj:

- **Planiści**. "Planowanie" odnosi się do możliwości, aby administrator mógł załadować pliku service w systemie hosta, który określa sposób uruchamiania kontenera dla. Uruchamianie kontenerów w klastrze Docker zwykle nazywane planowania. Chociaż planowanie odwołuje się do określonych act ładowania definicji usługi, w tym sensie bardziej ogólnych transfery danych są odpowiedzialne za przechwytywanie systemu init hosta do zarządzania usługami w każdej pojemności potrzebne.

   Harmonogram klastra ma wiele cele: efektywne korzystanie z zasobów klastra, Praca z ograniczeniami dotyczącymi umieszczania dostarczone przez użytkownika, w planowanie aplikacjom szybko nie pozostawić je w stanie oczekiwania, o stopniu "sprawiedliwe", są niezawodne, błędy, a zawsze być dostępna.

- **Organizowanie**. Platform rozszerzyć możliwości zarządzania cyklem życia złożone, z wieloma kontenerami w celu obciążenia wdrożone w klastrze hostów. Zapewniając abstrakcyjność infrastruktury hostowania, narzędziami koordynowania zapewniają sposób traktować cały klaster jako obiekt docelowy pojedynczego wdrożenia.

   Proces aranżacji obejmuje narzędzia i platformy, które można zautomatyzować wszystkie aspekty zarządzania aplikacjami z początkowe położenie lub wdrażania na kontener; Przenoszenie kontenerów na różnych hostach w zależności od kondycji jej hosta lub wykonania; przechowywanie wersji stopniowe aktualizacje i funkcje, które obsługują skalowanie i trybu failover; monitorowania kondycji i wiele więcej.

   Aranżacja to szeroka termin, który odwołuje się do kontenera planowania, zarządzania klastrem i prawdopodobnie udostępniania dodatkowych hostów.

Możliwości zapewniane przez orkiestratory i transfery danych są bardzo skomplikowane, do tworzenia i utworzyć od podstaw, a w związku z tym zazwyczaj chcesz wprowadzić użytkowania aranżacji rozwiązań oferowanych przez dostawców.


>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](manage-production-docker-environments.md)
