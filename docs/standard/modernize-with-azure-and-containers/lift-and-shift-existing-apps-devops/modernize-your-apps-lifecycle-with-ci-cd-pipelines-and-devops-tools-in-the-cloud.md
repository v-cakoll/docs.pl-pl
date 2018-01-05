---
title: "Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c0b87d01c1305695dacaf3ba112b387de2ee0cc1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
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
