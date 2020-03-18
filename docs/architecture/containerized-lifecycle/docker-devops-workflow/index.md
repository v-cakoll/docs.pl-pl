---
title: Przepływ pracy DevOps dla aplikacji platformy Docker z wykorzystaniem narzędzi firmy Microsoft
description: Cykl życia aplikacji doplatformy kontenerowej z przepływem pracy DevOps platformy Microsoft platformy i narzędzi za pomocą narzędzi firmy Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 6b138301a7e6794ce0a7b15957684b3b73e9f89f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70295743"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Przepływ pracy DevOps dla aplikacji platformy Docker z wykorzystaniem narzędzi firmy Microsoft

*Microsoft Visual Studio, Usługi Azure DevOps, Team Foundation Server i Azure Monitor zapewniają kompleksowy ekosystem dla operacji deweloperskich i IT, które zapewniają zespołowi narzędzia do zarządzania projektami i szybkiego tworzenia, testowania i wdrażania konteneryzowanych Aplikacji.*

Dzięki programom Visual Studio i usłudze Azure DevOps Services w chmurze wraz z lokalnym programem Team Foundation Server zespoły programistyczne mogą wydajnie tworzyć, testować i udostępniać aplikacje konteneryzowane przeznaczone dla systemu Windows lub Linux.

Narzędzia firmy Microsoft mogą zautomatyzować potok dla określonych implementacji aplikacji konteneryzowanych — platformy Docker, .NET Core lub dowolnej kombinacji z innymi platformami — od kompilacji globalnych i ciągłej integracji (CI) i testów z usługami Azure DevOps lub zespołem Serwer Fundacji, do ciągłego wdrażania (CD) do środowisk platformy Docker (programowanie, przemieszczania, produkcji) i do przesyłania informacji analitycznych o usługach do zespołu programistycznego za pośrednictwem usługi Azure Monitor. Każde zatwierdzenie kodu może zainicjować kompilację (CI) i automatycznie wdrożyć usługi w określonych środowiskach konteneryzowanych (CD).

Deweloperzy i testerzy mogą łatwo i szybko aprowizować środowiska programistyczne i testowe podobne do produkcji na podstawie platformy Docker przy użyciu szablonów na platformie Microsoft Azure.

Złożoność konteneryzowanych aplikacji zwiększa się stale w zależności od złożoności biznesowej i potrzeb skalowalności. Dobrym przykładem tej złożoności są aplikacje oparte na architekturach mikrousług. Aby odnieść sukces w takim środowisku, projekt musi zautomatyzować cały cykl życia — nie tylko kompilacji i wdrażania, ale także zarządzać wersjami wraz z kolekcją danych telemetrycznych. Usługi Azure DevOps i platforma Azure oferują następujące możliwości:

- Zarządzanie kodem źródłowym usługi Azure DevOps Services/Team Foundation Server (oparte na git lub Team Foundation Version Control), planowanie agile (obsługiwane są agile, scrum i CMMI), ci, zarządzanie wersjami i inne narzędzia dla zespołów Agile.

- Usługi Azure DevOps i Team Foundation Server obejmują zaawansowany i rozwijający się ekosystem rozszerzeń pierwszej i innej firmy, za pomocą których można łatwo skonstruować potok zarządzania zasobami, kompilacji, testowania, dostarczania i wydania dla mikrousług.

- Uruchamianie testów automatycznych w ramach potoku kompilacji w usłudze Azure DevOps Services.

- Usługi Azure DevOps mogą zaostrzyć cykl życia DevOps dzięki dostarczaniu do wielu środowisk, nie tylko w środowiskach produkcyjnych, ale także w celu testowania, w tym eksperymentów A/B, [wydań kanaryjskich](https://martinfowler.com/bliki/CanaryRelease.html)i tak dalej.

- Organizacje z łatwością mogą aprowizować kontenery platformy Docker z prywatnych obrazów przechowywanych w rejestrze kontenerów platformy Azure wraz z zależnością od składników platformy Azure (Dane, PaaS itp.) przy użyciu szablonów usługi Azure Resource Manager za pomocą narzędzi, które już są wygodne.

>[!div class="step-by-step"]
>[Poprzedni](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[następny](docker-application-outer-loop-devops-workflow.md)
