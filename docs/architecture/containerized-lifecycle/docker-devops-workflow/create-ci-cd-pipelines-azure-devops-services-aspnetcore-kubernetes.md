---
title: Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker
description: Cykl życia konteneryzowanych aplikacji platformy Docker korzystających z platformy i narzędzi firmy Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295779"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Tworzenie potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services dla aplikacji .NET Core 2.0 na kontenerach i wdrażanie w klastrze Kubernetes

Na rysunku 5-12 można zobaczyć scenariusz devops end-to-end obejmujący zarządzanie kodem, kompilację kodu, kompilację obrazów platformy Docker, obrazy platformy Docker wypychają do rejestru platformy Docker i na koniec wdrożenie klastra Kubernetes na platformie Azure.

![Przepływ pracy: Uruchamia się w maszynie deweloperskiej. Wypychanie do repów rozpoczyna zadanie kompilacji/ciągłej integracji przy użyciu niestandardowego obrazu, który zostanie wypchnięty do rejestru platformy Docker, a następnie jest używany przez zadanie CD/wdrażania, aby w reszcie wypychać do usługi AKS.](media/docker-workflow-ci-cd-aks.png)

**Rysunek 5-12**. Scenariusz ciągłej integracji/dysku CD tworzenia obrazów platformy Docker i wdrażania w klastrze Kubernetes na platformie Azure

Należy podkreślić, że dwa potoki, kompilacji/ciągłej integracji i wydania/dysku CD, są połączone za pośrednictwem rejestru platformy Docker (na przykład Docker Hub lub Azure Container Registry). Rejestr platformy Docker jest jedną z głównych różnic w porównaniu do tradycyjnego procesu ciągłej integracji/ciągłego przetwarzania bez platformy Docker.

Jak pokazano na rysunku 5-13, pierwsza faza to potok kompilacji/CI. W usłudze Azure DevOps Services można tworzyć potoki kompilacji/księgi kupna, które skompilują kod, tworzyć obrazy platformy Docker i wypychać je do rejestru platformy Docker, takiego jak Docker Hub lub Azure Container Registry.

![Widok przeglądarki azure devops, tworzenie definicji zadań procesu.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Rysunek 5-13**. Tworzenie/potok pzwu w usłudze Azure DevOps tworzenia obrazów platformy Docker i wypychania obrazów do rejestru platformy Docker

Druga faza polega na utworzeniu potoku wdrażania/wydania. W usłudze Azure DevOps Services można łatwo utworzyć potok wdrażania przeznaczony dla klastra Kubernetes przy użyciu zadań Kubernetes dla usług Azure DevOps, jak pokazano na rysunku 5-14.

![Widok przeglądarki usługi Azure DevOps, wdrożenie w definicji zadań kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Rysunek 5-14**. Potok wydania/dysku CD w usłudze Azure DevOps Services wdrażającej w klastrze Kubernetes

> [! Instruktaż] Wdrażanie eShopModernized do Kubernetes:
>
> Aby uzyskać szczegółowy opis potoków ciągłej wdrażania usługi Azure DevOps ci/CD w kubernetes, zobacz ten wpis: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Poprzedni](docker-application-outer-loop-devops-workflow.md)
>[następny](../run-manage-monitor-docker-environments/index.md)
