---
title: Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker
description: Cykl życia konteneryzowanych aplikacji platformy Docker korzystających z platformy i narzędzi firmy Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644985"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Tworzenie potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services dla aplikacji .NET Core 2.0 na kontenerach i wdrażanie w klastrze Kubernetes

Rysunek 5-12 widać scenariusza DevOps end-to-end, obejmujące zarządzania kodem, kompilacja kodu, tworzenie obrazów platformy Docker, obrazów platformy Docker, Wypchnij do rejestru platformy Docker, a na koniec wdrożenia w klastrze Kubernetes na platformie Azure.

![Przepływ pracy: Rozpoczyna się w komputerze deweloperskim. Wypychanie do repozytorium rozpoczyna się zadanie kompilacji/ciągłej integracji przy użyciu niestandardowego obrazu, który pobiera wypchnięte do rejestru platformy Docker, a następnie jest używany przez ciągłe dostarczanie/wdrażanie zadania, na koniec Wypychanie do usługi AKS.](media/docker-workflow-ci-cd-aks.png)

**Rysunek 5 – 12**. Ciągła Integracja/ciągłe dostarczanie scenariusz tworzenia obrazów platformy Docker i wdrażania w klastrze Kubernetes na platformie Azure

Jest ważne podkreślić, że dwa potoki kompilacji/ciągłej integracji i wersji/ciągłe dostarczanie, są połączone za pośrednictwem rejestru platformy Docker (np. usługi Docker Hub lub Azure Container Registry). Rejestr platformy Docker jest jednym z głównych różnic w porównaniu do tradycyjnego procesu ciągłej integracji/ciągłego wdrażania bez platformy Docker.

Jak pokazano w rysunek 5-13, pierwsza faza jest potok kompilacji/ciągłej integracji. W usługom DevOps platformy Azure można utworzyć potoki kompilacji/ciągłej integracji, które będą skompilować kod, Utwórz obrazy platformy Docker i odesłać je do rejestru platformy Docker, takich jak usługi Docker Hub lub Azure Container Registry.

![Widok DevOps platformy Azure, definicja zadania procesu kompilacji w przeglądarce.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Rysunek 5-13**. Potoki kompilacji/ciągłej integracji w DevOps platformy Azure, tworzenie obrazów platformy Docker i wypychanie obrazów do rejestru platformy Docker

Drugi etap polega na utworzeniu potoku wdrożenia/wydania. W usługach infrastruktury DevOps platformy Azure można łatwo utworzyć potok wdrożenia przeznaczone dla klastra Kubernetes za pomocą zadaniach usługi Kubernetes dla usługi DevOps platformy Azure, jak pokazano w rysunek 5-14.

![Widok przeglądarki DevOps platformy Azure, Wdróż definicji zadania usługi Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Rysunek 5-14**. Potok wersji/ciągłe dostarczanie we wdrażaniu usługom DevOps platformy Azure, w klastrze Kubernetes

> [! Przewodnik] wdrażania eShopModernized Kubernetes:
>
> Szczegółowy przewodnik dotyczący potoków usługi Azure DevOps ciągłej integracji/ciągłego wdrażania, wdrażanie Kubernetes, zobacz ten wpis: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Poprzednie](docker-application-outer-loop-devops-workflow.md)
>[dalej](../run-manage-monitor-docker-environments/index.md)
