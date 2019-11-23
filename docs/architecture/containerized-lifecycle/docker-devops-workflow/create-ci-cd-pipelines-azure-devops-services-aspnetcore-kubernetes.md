---
title: Kroki przepływu pracy DevOps w zewnętrznej pętli dla aplikacji platformy Docker
description: Cykl życia konteneryzowanych aplikacji platformy Docker korzystających z platformy i narzędzi firmy Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295779"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Tworzenie potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services dla aplikacji .NET Core 2.0 na kontenerach i wdrażanie w klastrze Kubernetes

Na rysunku 5-12 można zobaczyć kompleksowy scenariusz DevOps obejmujący Zarządzanie kodem, kompilację kodu, kompilację obrazów platformy Docker, wypychanie obrazów Docker do rejestru platformy Docker, a wreszcie Wdrożenie klastra Kubernetes na platformie Azure.

![Przepływ pracy: uruchamiany na komputerze deweloperskim. Wypychanie do repozytorium rozpoczyna zadanie kompilacji/CI przy użyciu niestandardowego obrazu, który jest wypychany do rejestru platformy Docker, a następnie jest używany przez zadanie CD/Deploy w programie, a wreszcie wypychanie do AKS.](media/docker-workflow-ci-cd-aks.png)

**Rysunek 5-12**. Scenariusz ciągłej integracji/ciągłego tworzenia obrazów platformy Docker i wdrażania ich w klastrze Kubernetes na platformie Azure

Należy zaznaczyć, że dwa potoki, kompilacja/CI i wersja/dysk CD są połączone za pomocą rejestru platformy Docker (takiego jak usługa Docker Hub lub Azure Container Registry). Rejestr platformy Docker jest jedną z głównych różnic w porównaniu do tradycyjnego procesu ciągłej integracji/ciągłego wdrażania bez platformy Docker.

Jak pokazano na rysunku 5-13, Pierwsza faza to potok kompilacji/elementu konfiguracji. W Azure DevOps Services można tworzyć potoki kompilacji/CI, które będą kompilować kod, tworzyć obrazy platformy Docker i wypchnąć je do rejestru Docker, takiego jak Docker Hub lub Azure Container Registry.

![Widok przeglądarki Azure DevOps, definicja zadania procesu kompilacji.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Rysunek 5-13**. Potok kompilacji/elementu konfiguracji w usłudze Azure DevOps tworzenie obrazów platformy Docker i wypychanie obrazów do rejestru platformy Docker

Drugim etapem jest utworzenie potoku wdrożenia/wydania. W Azure DevOps Services można łatwo utworzyć potok wdrożenia przeznaczony dla klastra Kubernetes za pomocą Kubernetes zadań dla Azure DevOps Services, jak pokazano na rysunku 5-14.

![Widok przeglądarki Azure DevOps, wdrażanie do Kubernetes definicji zadań.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Rysunek 5-14**. Potok wydania/CD w Azure DevOps Services wdrożenia w klastrze Kubernetes

> [! Przewodnik] wdrażanie eShopModernized do Kubernetes:
>
> Aby zapoznać się ze szczegółowymi wskazówkami dotyczącymi potoków ciągłej integracji/ciągłego wdrażania w usłudze Azure DevOps, zobacz ten wpis: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Poprzedni](docker-application-outer-loop-devops-workflow.md)
>[Następny](../run-manage-monitor-docker-environments/index.md)
