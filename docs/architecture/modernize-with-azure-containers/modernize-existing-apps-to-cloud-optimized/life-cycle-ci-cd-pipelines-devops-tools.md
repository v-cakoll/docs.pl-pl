---
title: Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Zmodernizuj cykl życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i narzędzi DevOps w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: ac2d9a1e9ab432cf69cb3da670fc91c681f802c2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987858"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze

Dzisiejsze przedsiębiorstwa muszą w szybkim tempie wprowadzać innowacje, aby być konkurencyjnym na rynku. Dostarczanie wysokiej jakości, nowoczesnych aplikacji wymaga narzędzi i procesów DevOps, które mają kluczowe znaczenie dla wdrożenia tego stałego cyklu innowacji. Dzięki odpowiednim narzędziom DevOps deweloperzy mogą usprawnić ciągłe wdrażanie i szybciej udostępniać innowacyjne aplikacje użytkownikom.

Chociaż praktyki ciągłej integracji i wdrażania są dobrze ugruntowane, wprowadzenie kontenerów wprowadza nowe zagadnienia, szczególnie podczas pracy z aplikacjami z wieloma kontenerami.

Usługi Azure DevOps obsługuje ciągłą integrację i wdrażanie aplikacji z wieloma kontenerami w różnych środowiskach za pośrednictwem oficjalnych zadań wdrażania usług Azure DevOps Services:

- [Wdrażanie w aplikacji sieci Web platformy Azure dla kontenerów](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Wdrażanie w usłudze Azure Kubernetes Service](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Ale można również wdrożyć do [docker swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) lub DC/OS przy użyciu zadań opartych na skryptach usługi Azure DevOps services.

Aby nadal ułatwiać elastyczność wdrażania, narzędzia te zapewniają doskonałe środowisko wdrażania dev-to-test-to-production dla obciążeń kontenerów, z możliwością wyboru rozwiązań deweloperskich i ciągłych integracji/ciągłego wdrażania.

Rysunek 4-12 przedstawia potok ciągłego wdrażania, który wdraża w klastrze Kubernetes w usłudze Azure Container Service.

![Zrzut ekranu przedstawiający usługi Azure DevOps wdrażające w klastrze usługi Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Rysunek 4-12.** Potok ciągłego wdrażania usług Azure DevOps, wdrażanie w klastrze usługi Kubernetes

>[!div class="step-by-step"]
>[Poprzedni](modernize-your-apps-with-monitoring-and-telemetry.md)
>[następny](migrate-to-hybrid-cloud-scenarios.md)
