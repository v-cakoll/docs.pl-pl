---
title: Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego Dostarczania i metodyki DevOps w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833954"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze

Dzisiejsze firmy muszą wprowadzać innowacje w szybkim tempie konkurencyjności w portalu marketplace. Dostarczanie wysokiej jakości, nowoczesnych aplikacji wymaga narzędzi DevOps i procesy, które są niezbędne do zaimplementowania tej stałej cyklu innowacji. Odpowiednie narzędzia DevOps deweloperzy mogą uprościć ciągłego wdrażania i szybciej uzyskać innowacyjne aplikacje w ręce użytkowników.

Chociaż utrwalonego ciągłej integracji i ciągłego wdrażania rozwiązania wprowadzenie kontenerów wprowadza nowe zagadnienia, szczególnie w przypadku, gdy pracujesz z wieloma kontenerami aplikacji.

Usługom DevOps platformy Azure obsługuje ciągłej integracji i wdrażania aplikacji z wieloma kontenerami do różnych środowisk za pomocą oficjalnego zadania wdrażania usługom DevOps platformy Azure:

- [Wdrażanie aplikacji sieci Web platformy Azure for Containers](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [Wdrażanie w usłudze Azure Container Service — Kubernetes](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

Ale również można wdrożyć na [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) lub DC/OS za pomocą zadań opartych na skryptach usługom DevOps platformy Azure.

Aby kontynuować, ułatwiając elastyczność wdrażania, narzędzia te zawierają doskonałe wdrożenie dev do test — do produkcji środowisk dla obciążeń kontenerów, z możliwością wyboru rozwoju i ciągłej integracji/ciągłego wdrażania rozwiązania.

Rysunek 4-12 przedstawiono potok ciągłego wdrażania, który wdraża klaster Kubernetes w usłudze Azure Container Service.

![Potok ciągłego wdrażania usługom DevOps platformy Azure, wdrażanie klastra Kubernetes](./media/image12.png)

> **Rysunek 4-12.** Potok ciągłego wdrażania usługom DevOps platformy Azure, wdrażanie klastra Kubernetes

>[!div class="step-by-step"]
>[Poprzednie](modernize-your-apps-with-monitoring-and-telemetry.md)
>[dalej](migrate-to-hybrid-cloud-scenarios.md)
