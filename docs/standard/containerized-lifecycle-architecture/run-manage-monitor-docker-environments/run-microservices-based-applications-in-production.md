---
title: Uruchamianie aplikacji złożonych i opartych na mikrousługach w środowiskach produkcyjnych
description: Poznaj najważniejsze składniki do uruchamiania aplikacji opartych na kontenerach w środowisku produkcyjnym
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644967"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Uruchamianie aplikacji złożonych i opartych na mikrousługach w środowiskach produkcyjnych

Aplikacje składające się przez wiele mikrousług muszą zostać wdrożone w klastrach programu orchestrator, aby uprościć złożoność wdrożenia i przypisz ją jako możliwego do użycia z punktu widzenia IT. Bez klastra usługi orchestrator będzie trudne wdrażanie i skalowanie aplikacji złożonych mikrousług.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Wprowadzenie do koordynatorów, harmonogramów i klastrów kontenerów

Wcześniej w tej książce elektronicznej, *klastrów* i *lotów* zostały wprowadzone w ramach dyskusji o architekturze oprogramowania i rozwoju. Kubernetes i usługi Service Fabric to przykłady klastrów platformy Docker. Oba te koordynatorów można uruchomić jako część infrastruktury zapewnianej przez usługi Microsoft Azure Kubernetes Service.

Aplikacje są skalowanych w poziomie w wielu systemach hosta, możliwość zarządzania każdym systemie hosta i streszczenie natychmiast złożoność podstawowej platformy staje się atrakcyjne. To dokładnie co zapewniają koordynatorów i transfery danych. Przyjrzyjmy się krótki opis ich tutaj:

- **Planiści**. "Planowanie" odnosi się do możliwości, aby administrator mógł załadować pliku service w systemie hosta, który określa sposób uruchamiania kontenera dla. Uruchamianie kontenerów w klastrze Docker zwykle nazywane planowania. Chociaż planowanie odwołuje się do określonych act ładowania definicji usługi, w tym sensie bardziej ogólnych transfery danych są odpowiedzialne za przechwytywanie systemu init hosta do zarządzania usługami w każdej pojemności potrzebne.

   Harmonogram klastra ma wiele cele: efektywne korzystanie z zasobów klastra, Praca z ograniczeniami dotyczącymi umieszczania dostarczone przez użytkownika, w planowanie aplikacjom szybko nie pozostawić je w stanie oczekiwania, o stopniu "sprawiedliwe", są niezawodne, błędy, a zawsze być dostępna.

- **Koordynatorów**. Platform rozszerzyć możliwości zarządzania cyklem życia złożonych, wielokontenerowych obciążenia wdrożone w klastrze hostów. Zapewniając abstrakcyjność infrastruktury hostowania, narzędziami koordynowania zapewniają sposób traktować cały klaster jako obiekt docelowy pojedynczego wdrożenia.

   Proces aranżacji obejmuje narzędzia i platformy, które można zautomatyzować wszystkie aspekty zarządzania aplikacjami z początkowe położenie lub wdrażania na kontener; Przenoszenie kontenerów na różnych hostach w zależności od kondycji jej hosta lub wykonania; przechowywanie wersji stopniowe aktualizacje i funkcje, które obsługują skalowanie i trybu failover; monitorowania kondycji i wiele więcej.

   Aranżacja to szeroka termin, który odwołuje się do kontenera planowania, zarządzania klastrem i prawdopodobnie udostępniania dodatkowych hostów.

Możliwości zapewniane przez orkiestratory i transfery danych są złożone i dlatego tworzenie i utworzyć od podstaw, dlatego zazwyczaj chcesz użyć rozwiązań aranżacji oferowanych przez dostawców.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](manage-production-docker-environments.md)
