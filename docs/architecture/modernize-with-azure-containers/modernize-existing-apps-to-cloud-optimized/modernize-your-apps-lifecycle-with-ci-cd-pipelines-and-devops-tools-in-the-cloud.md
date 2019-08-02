---
title: Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Modernizacja cyklu życia aplikacji za pomocą potoków ciągłej integracji i ciągłego wdrażania oraz narzędzi DevOps w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676977"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze

Dzisiejsze firmy muszą szybko wprowadzać innowacje w rynku. Dostarczanie wysokiej jakości nowoczesnych aplikacji wymaga narzędzi i procesów DevOps, które mają kluczowe znaczenie dla wdrożenia tego stałego cyklu innowacji. Korzystając z odpowiednich narzędzi DevOps, deweloperzy mogą usprawnić ciągłe wdrażanie i szybciej uzyskiwać innowacyjne aplikacje.

Mimo że są dobrze zintegrowane praktyki integracji i wdrażania, wprowadzenie kontenerów wprowadza nowe zagadnienia, szczególnie w przypadku pracy z aplikacjami wielokontenerowymi.

Azure DevOps Services obsługuje ciągłą integrację i wdrażanie aplikacji z wieloma kontenerami w różnych środowiskach za pomocą oficjalnych Azure DevOps Services zadań wdrażania:

- [Wdrażanie w usłudze Azure Web App for Containers](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [Wdróż do Azure Container Service — Kubernetes](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

Możesz również wdrożyć program Docker [Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) lub DC/OS przy użyciu Azure DevOps Services zadań opartych na skryptach.

Aby nadal ułatwiać elastyczność wdrażania, narzędzia te zapewniają doskonałe środowisko wdrażania z zakresu tworzenia i testowania do produkcji w przypadku obciążeń kontenerów, z możliwością wyboru rozwiązań programistycznych i ciągłej integracji.

Rysunek 4-12 przedstawia potok ciągłego wdrażania, który jest wdrażany w klastrze Kubernetes w Azure Container Service.

![Azure DevOps Services potok ciągłego wdrażania, wdrażanie w klastrze Kubernetes](./media/image12.png)

> **Rysunek 4-12.** Azure DevOps Services potok ciągłego wdrażania, wdrażanie w klastrze Kubernetes

>[!div class="step-by-step"]
>[Poprzedni](modernize-your-apps-with-monitoring-and-telemetry.md)Następny
>[](migrate-to-hybrid-cloud-scenarios.md)
