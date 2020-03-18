---
title: Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Zmodernizuj cykl życia aplikacji za pomocą potoków ciągłej integracji/ciągłego dysku CD i narzędzi DevOps w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: 17a78c108bfc61471128a34191ec7a5d7cc28289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503848"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze

Dzisiejsze firmy muszą wprowadzać innowacje w szybkim tempie, aby być konkurencyjnym na rynku. Dostarczanie wysokiej jakości nowoczesnych aplikacji wymaga narzędzi i procesów DevOps, które mają kluczowe znaczenie dla wdrożenia tego ciągłego cyklu innowacji. Dzięki odpowiednim narzędziom DevOps deweloperzy mogą usprawnić ciągłe wdrażanie i szybciej urozmaicić innowacyjne aplikacje w ręce użytkowników.

Mimo że ciągłe rozwiązania integracyjne i wdrożeniowe są dobrze ugruntowane, wprowadzenie kontenerów wprowadza nowe zagadnienia, szczególnie podczas pracy z aplikacjami wielokontenerowymi.

Usługi Azure DevOps Services obsługują ciągłą integrację i wdrażanie aplikacji wielokontenerowych w różnych środowiskach za pośrednictwem oficjalnych zadań wdrażania usług Azure DevOps Services:

- [Wdrażanie w aplikacji Sieci Web Azure dla kontenerów](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Wdrażanie w usłudze Azure Kubernetes Service](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Ale można również wdrożyć do [docker rój](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) lub DC/OS przy użyciu zadań opartych na usługach Azure DevOps services.

Aby nadal ułatwiać elastyczność wdrażania, narzędzia te zapewniają doskonałe środowisko wdrażania dev-to-test-to-production dla obciążeń kontenerów, z wyborem rozwiązań deweloperskich i ciągłej integracji/ciągłej integracji.

Rysunek 4–12 przedstawia potok ciągłego wdrażania wdrażany w klastrze Kubernetes w usłudze Azure Container Service.

![Zrzut ekranu przedstawiający wdrażanie usług Azure DevOps w klastrze Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Rysunek 4-12.** Potoku ciągłego wdrażania usług Azure DevOps Services, wdrażającego w klastrze Kubernetes

>[!div class="step-by-step"]
>[Poprzedni](modernize-your-apps-with-monitoring-and-telemetry.md)
>[następny](migrate-to-hybrid-cloud-scenarios.md)
