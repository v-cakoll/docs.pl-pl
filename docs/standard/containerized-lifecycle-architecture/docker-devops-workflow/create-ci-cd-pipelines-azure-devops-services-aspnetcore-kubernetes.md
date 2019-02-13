---
title: Kroki w przepływie pracy DevOps zewnętrznej pętli dla aplikacji platformy Docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 7a98c34bfdbbdc9b34a04c891ca031f454ac4396
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221397"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Tworzenie potoków ciągłej integracji/ciągłego Dostarczania w usłudze Azure Services DevOps dla aplikacji .NET Core 2.0 na kontenerach i wdrażania w klastrze Kubernetes

Rysunek 5-12 widać scenariusza DevOps end-to-end, obejmujące zarządzania kodem, kompilacja kodu, tworzenie obrazów platformy Docker, obrazów platformy Docker, Wypchnij do rejestru platformy Docker, a na koniec wdrożenia w klastrze Kubernetes na platformie Azure.

![Przepływ pracy: Rozpoczyna się w komputerze deweloperskim. Wypychanie do repozytorium rozpoczyna się zadanie kompilacji/ciągłej integracji przy użyciu niestandardowego obrazu, który pobiera wypchnięte do rejestru platformy Docker, a następnie jest używany przez ciągłe dostarczanie/wdrażanie zadania, na koniec Wypychanie do usługi AKS.](media/docker-workflow-ci-cd-aks.png)

**Rysunek 5 – 12**. Ciągła Integracja/ciągłe dostarczanie scenariusz tworzenia obrazów platformy Docker i wdrażania w klastrze Kubernetes na platformie Azure

Jest ważne podkreślić, że dwa potoki kompilacji/ciągłej integracji i wersji/ciągłe dostarczanie, są połączone za pośrednictwem rejestru platformy Docker (np. usługi Docker Hub lub Azure Container Registry). Rejestr platformy Docker jest jednym z głównych różnic w porównaniu do tradycyjnego procesu ciągłej integracji/ciągłego wdrażania bez platformy Docker.

Jak pokazano w rysunek 5-13, pierwsza faza jest potok kompilacji/ciągłej integracji. W usługom DevOps platformy Azure można utworzyć potoki kompilacji i ciągłego wdrażania, które będą skompilować kod, Utwórz obrazy platformy Docker i odesłać je do rejestru platformy Docker, takich jak usługi Docker Hub lub Azure Container Registry.

![](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Rysunek 5-13**. Potoki kompilacji/ciągłej integracji w DevOps platformy Azure, tworzenie obrazów platformy Docker i wypychanie obrazów do rejestru platformy Docker

Drugi etap polega na utworzeniu potoku wdrożenia/wydania. W usługach infrastruktury DevOps platformy Azure można łatwo utworzyć potok wdrożenia przeznaczone dla klastra Kubernetes za pomocą zadaniach usługi Kubernetes dla usługi DevOps platformy Azure, jak pokazano w rysunek 5-14.

![Deploy MVC](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Rysunek 5-14**. Potok wersji/ciągłe dostarczanie we wdrażaniu usługom DevOps platformy Azure, w klastrze Kubernetes

> [! Przewodnik] wdrażania eShopModernized Kubernetes:
>
> Szczegółowy przewodnik dotyczący potoków usługi Azure DevOps ciągłej integracji/ciągłego wdrażania, wdrażanie Kubernetes, zobacz ten wpis: \
>[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

>[!div class="step-by-step"]
>[Poprzednie](docker-application-outer-loop-devops-workflow.md)
>[dalej](../run-manage-monitor-docker-environments/index.md)
