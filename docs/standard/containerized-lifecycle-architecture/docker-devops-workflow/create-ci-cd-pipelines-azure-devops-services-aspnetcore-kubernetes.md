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
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="73836-103">Tworzenie potoków ciągłej integracji/ciągłego Dostarczania w usłudze Azure Services DevOps dla aplikacji .NET Core 2.0 na kontenerach i wdrażania w klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="73836-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="73836-104">Rysunek 5-12 widać scenariusza DevOps end-to-end, obejmujące zarządzania kodem, kompilacja kodu, tworzenie obrazów platformy Docker, obrazów platformy Docker, Wypchnij do rejestru platformy Docker, a na koniec wdrożenia w klastrze Kubernetes na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="73836-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Przepływ pracy: Rozpoczyna się w komputerze deweloperskim.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="73836-107">**Rysunek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="73836-107">**Figure 5-12**.</span></span> <span data-ttu-id="73836-108">Ciągła Integracja/ciągłe dostarczanie scenariusz tworzenia obrazów platformy Docker i wdrażania w klastrze Kubernetes na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="73836-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="73836-109">Jest ważne podkreślić, że dwa potoki kompilacji/ciągłej integracji i wersji/ciągłe dostarczanie, są połączone za pośrednictwem rejestru platformy Docker (np. usługi Docker Hub lub Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="73836-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="73836-110">Rejestr platformy Docker jest jednym z głównych różnic w porównaniu do tradycyjnego procesu ciągłej integracji/ciągłego wdrażania bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="73836-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="73836-111">Jak pokazano w rysunek 5-13, pierwsza faza jest potok kompilacji/ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="73836-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="73836-112">W usługom DevOps platformy Azure można utworzyć potoki kompilacji i ciągłego wdrażania, które będą skompilować kod, Utwórz obrazy platformy Docker i odesłać je do rejestru platformy Docker, takich jak usługi Docker Hub lub Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="73836-112">In Azure DevOps Services you can create build/CD pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="73836-113">**Rysunek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="73836-113">**Figure 5-13**.</span></span> <span data-ttu-id="73836-114">Potoki kompilacji/ciągłej integracji w DevOps platformy Azure, tworzenie obrazów platformy Docker i wypychanie obrazów do rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="73836-114">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="73836-115">Drugi etap polega na utworzeniu potoku wdrożenia/wydania.</span><span class="sxs-lookup"><span data-stu-id="73836-115">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="73836-116">W usługach infrastruktury DevOps platformy Azure można łatwo utworzyć potok wdrożenia przeznaczone dla klastra Kubernetes za pomocą zadaniach usługi Kubernetes dla usługi DevOps platformy Azure, jak pokazano w rysunek 5-14.</span><span class="sxs-lookup"><span data-stu-id="73836-116">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Deploy MVC](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="73836-118">**Rysunek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="73836-118">**Figure 5-14**.</span></span> <span data-ttu-id="73836-119">Potok wersji/ciągłe dostarczanie we wdrażaniu usługom DevOps platformy Azure, w klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="73836-119">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Przewodnik]<span data-ttu-id="73836-120"> wdrażania eShopModernized Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="73836-120"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="73836-121">Szczegółowy przewodnik dotyczący potoków usługi Azure DevOps ciągłej integracji/ciągłego wdrażania, wdrażanie Kubernetes, zobacz ten wpis: \\</span><span class="sxs-lookup"><span data-stu-id="73836-121">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: \\</span></span>
>[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

>[!div class="step-by-step"]
><span data-ttu-id="73836-122">[Poprzednie](docker-application-outer-loop-devops-workflow.md)
>[dalej](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="73836-122">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
