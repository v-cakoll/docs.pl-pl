---
title: Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 63907a1911b4c95f0dbecb2af33964225cf3e7b1
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958210"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD

Obecnie firma potrzebuje do innowacji w tempie szybkie dla utrzymania konkurencyjności w witrynie marketplace. Dostarczanie wysokiej jakości, nowoczesnych aplikacji wymaga narzędzia DevOps i procesy, które są niezbędne do zaimplementowania stałej cyklu innowacji. Odpowiednie narzędzia DevOps deweloperów może usprawnić ciągłego wdrażania i szybciej Pobierz innowacyjnych aplikacje w ręce użytkowników.

Choć utrwalonego ciągłej integracji i wdrażania rozwiązań, wprowadzenie kontenery wprowadza nowe zagadnienia, szczególnie w przypadku, gdy użytkownik pracuje z wieloma kontenera aplikacji.

Visual Studio Team Services obsługuje ciągłej integracji i wdrażanie aplikacji kontenera wielu różnych środowiskach przez oficjalnego zadania wdrożenia usługi Team Services:

-   [Wdrażanie do autonomicznej maszyny Wirtualnej hosta Docker](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux lub Windows Server 2016 lub nowszy)

-   [Wdrażanie sieci szkieletowej usług](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [Wdrażanie usługi kontenera platformy Azure — Kubernetes](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

Ale też można wdrożyć [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) lub DC/OS, przy użyciu zadań opartych na skryptach Team Services.

Aby kontynuować, ułatwiające elastyczności wdrożenia, te narzędzia umożliwiają napotka znakomity deweloperów do testu do produkcyjne wdrożenie kontenera w przypadku obciążeń z wyborem programowanie i rozwiązań CI/CD.

Rysunek 4-12 przedstawiono potoku ciągłego wdrażania, która wdraża do Kubernetes klastra usługi kontenera platformy Azure.

![Visual Studio Team Services potoku ciągłego wdrażania, wdrożenie klastra Kubernetes](./media/image12.png)

> **Rysunek 4-12.** Visual Studio Team Services potoku ciągłego wdrażania, wdrożenie klastra Kubernetes

>[!div class="step-by-step"]
[Poprzednie](modernize-your-apps-with-monitoring-and-telemetry.md)
[dalej](migrate-to-hybrid-cloud-scenarios.md)
