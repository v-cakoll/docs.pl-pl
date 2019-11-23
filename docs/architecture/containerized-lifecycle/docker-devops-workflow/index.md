---
title: Przepływ pracy DevOps dla aplikacji platformy Docker z wykorzystaniem narzędzi firmy Microsoft
description: Cykl życia aplikacji platformy Docker z platformą Microsoft i narzędziami DevOps przepływ pracy przy użyciu narzędzi firmy Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 6b138301a7e6794ce0a7b15957684b3b73e9f89f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295743"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Przepływ pracy DevOps dla aplikacji platformy Docker z wykorzystaniem narzędzi firmy Microsoft

*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server i Azure Monitor zapewnia kompleksowy ekosystem do programowania i operacji IT, który umożliwia zespołowi zarządzanie projektami i szybkie kompilowanie, testowanie i wdrażanie kontenerów zastosowania.*

Dzięki programowi Visual Studio i Azure DevOps Services w chmurze, wraz z Team Foundation Server lokalnym, zespoły programistyczne mogą wydajnie kompilować, testować i wystawić aplikacje z kontenerami przeznaczonymi dla systemu Windows lub Linux.

Narzędzia firmy Microsoft mogą zautomatyzować potok dla konkretnych implementacji aplikacji kontenerowych — Docker, .NET Core lub dowolnej kombinacji z innymi platformami — od kompilacji globalnych i ciągłej integracji (CI) oraz testów z Azure DevOps Services lub zespołem Program Foundation Server, do ciągłego wdrażania (CD) w środowiskach platformy Docker (projektowanie, przemieszczanie, produkcja) i przekazywanie informacji analitycznych dotyczących usług do zespołu programistycznego za pomocą Azure Monitor. Każde zatwierdzenie kodu może inicjować kompilację (CI) i automatycznie wdrażać usługi w określonych środowiskach kontenerowych (CD).

Deweloperzy i testerzy mogą łatwo i szybko dostarczać środowiska deweloperskie i testowe podobne do produkcji w oparciu o platformę Docker, korzystając z szablonów w Microsoft Azure.

Złożoność tworzenia kontenerów aplikacji jest stale rośnie w zależności od potrzeb związanych z złożonością i skalowalnością biznesową. Dobrym przykładem tej złożoności są aplikacje oparte na architekturze mikrousług. Aby pomyślnie w tym środowisku, projekt musi zautomatyzować cały cykl życia — nie tylko kompilację i wdrożenie, ale również musi zarządzać wersjami wraz z kolekcją telemetrii. Azure DevOps Services i platforma Azure oferują następujące możliwości:

- Azure DevOps Services/Team Foundation Server zarządzania kodem źródłowym (w oparciu o narzędzia Git lub Kontrola wersji serwera Team Foundation), planowanie Agile (Agile, Scrum i CMMI są obsługiwane), CI, Zarządzanie zleceniami i inne narzędzia dla zespołów Agile.

- Azure DevOps Services i Team Foundation Server obejmują zaawansowany i rosnący ekosystem rozszerzeń pierwszej i innej firmy, z których można łatwo skonstruować potok CI, kompilację, testowanie, dostarczanie i Zarządzanie zleceniami dla mikrousług.

- Uruchamiaj testy automatyczne w ramach potoku kompilacji w Azure DevOps Services.

- Azure DevOps Services może zwiększyć cykl życia DevOps z dostarczaniem do wielu środowisk, nie tylko dla środowisk produkcyjnych, ale również do testowania, w tym eksperymentów A/B, [wydań Kanaryjskich](https://martinfowler.com/bliki/CanaryRelease.html)i tak dalej.

- Organizacje mogą łatwo udostępniać kontenery platformy Docker na podstawie obrazów prywatnych przechowywanych w Azure Container Registry wraz z każdą zależnością dotyczącą składników platformy Azure (danymi, PaaS itp.) przy użyciu szablonów Azure Resource Manager z narzędziami, które są już wygodne.

>[!div class="step-by-step"]
>[Poprzedni](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[Następny](docker-application-outer-loop-devops-workflow.md)
