---
title: Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego Dostarczania i metodyki DevOps w chmurze
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c4eeb5606d3ea93b76efee58ddfecae0abbbd743
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012177"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze

Dzisiejsze firmy muszą wprowadzać innowacje w szybkim tempie konkurencyjności w portalu marketplace. Dostarczanie wysokiej jakości, nowoczesnych aplikacji wymaga narzędzi DevOps i procesy, które są niezbędne do zaimplementowania tej stałej cyklu innowacji. Odpowiednie narzędzia DevOps deweloperzy mogą uprościć ciągłego wdrażania i szybciej uzyskać innowacyjne aplikacje w ręce użytkowników.

Chociaż utrwalonego ciągłej integracji i ciągłego wdrażania rozwiązania wprowadzenie kontenerów wprowadza nowe zagadnienia, szczególnie w przypadku, gdy pracujesz z wieloma kontenerami aplikacji.

Usługom DevOps platformy Azure obsługuje ciągłej integracji i wdrażania aplikacji z wieloma kontenerami do różnych środowisk za pomocą oficjalnego zadania wdrażania usługom DevOps platformy Azure:

- [Wdrażanie autonomicznej maszyny Wirtualnej hosta platformy Docker](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux lub Windows Server 2016 lub nowszy)

- [Wdrażanie w usłudze Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

- [Wdrażanie w usłudze Azure Container Service — Kubernetes](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

Ale również można wdrożyć na [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) lub DC/OS za pomocą zadań opartych na skryptach usługom DevOps platformy Azure.

Aby kontynuować, ułatwiając elastyczność wdrażania, narzędzia te zawierają doskonałe wdrożenie dev do test — do produkcji środowisk dla obciążeń kontenerów, z możliwością wyboru rozwoju i ciągłej integracji/ciągłego wdrażania rozwiązania.

Rysunek 4-12 przedstawiono potok ciągłego wdrażania, który wdraża klaster Kubernetes w usłudze Azure Container Service.

![Potok ciągłego wdrażania usługom DevOps platformy Azure, wdrażanie klastra Kubernetes](./media/image12.png)

> **Rysunek 4-12.** Potok ciągłego wdrażania usługom DevOps platformy Azure, wdrażanie klastra Kubernetes

>[!div class="step-by-step"]
>[Poprzednie](modernize-your-apps-with-monitoring-and-telemetry.md)
>[dalej](migrate-to-hybrid-cloud-scenarios.md)