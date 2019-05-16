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
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="ad9ae-103">Tworzenie potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services dla aplikacji .NET Core 2.0 na kontenerach i wdrażanie w klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="ad9ae-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="ad9ae-104">Rysunek 5-12 widać scenariusza DevOps end-to-end, obejmujące zarządzania kodem, kompilacja kodu, tworzenie obrazów platformy Docker, obrazów platformy Docker, Wypchnij do rejestru platformy Docker, a na koniec wdrożenia w klastrze Kubernetes na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Przepływ pracy: Rozpoczyna się w komputerze deweloperskim.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="ad9ae-107">**Rysunek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-107">**Figure 5-12**.</span></span> <span data-ttu-id="ad9ae-108">Ciągła Integracja/ciągłe dostarczanie scenariusz tworzenia obrazów platformy Docker i wdrażania w klastrze Kubernetes na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="ad9ae-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="ad9ae-109">Jest ważne podkreślić, że dwa potoki kompilacji/ciągłej integracji i wersji/ciągłe dostarczanie, są połączone za pośrednictwem rejestru platformy Docker (np. usługi Docker Hub lub Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="ad9ae-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="ad9ae-110">Rejestr platformy Docker jest jednym z głównych różnic w porównaniu do tradycyjnego procesu ciągłej integracji/ciągłego wdrażania bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="ad9ae-111">Jak pokazano w rysunek 5-13, pierwsza faza jest potok kompilacji/ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="ad9ae-112">W usługom DevOps platformy Azure można utworzyć potoki kompilacji/ciągłej integracji, które będą skompilować kod, Utwórz obrazy platformy Docker i odesłać je do rejestru platformy Docker, takich jak usługi Docker Hub lub Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Widok DevOps platformy Azure, definicja zadania procesu kompilacji w przeglądarce.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="ad9ae-114">**Rysunek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-114">**Figure 5-13**.</span></span> <span data-ttu-id="ad9ae-115">Potoki kompilacji/ciągłej integracji w DevOps platformy Azure, tworzenie obrazów platformy Docker i wypychanie obrazów do rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ad9ae-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="ad9ae-116">Drugi etap polega na utworzeniu potoku wdrożenia/wydania.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="ad9ae-117">W usługach infrastruktury DevOps platformy Azure można łatwo utworzyć potok wdrożenia przeznaczone dla klastra Kubernetes za pomocą zadaniach usługi Kubernetes dla usługi DevOps platformy Azure, jak pokazano w rysunek 5-14.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Widok przeglądarki DevOps platformy Azure, Wdróż definicji zadania usługi Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="ad9ae-119">**Rysunek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="ad9ae-119">**Figure 5-14**.</span></span> <span data-ttu-id="ad9ae-120">Potok wersji/ciągłe dostarczanie we wdrażaniu usługom DevOps platformy Azure, w klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="ad9ae-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Przewodnik]<span data-ttu-id="ad9ae-121"> wdrażania eShopModernized Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="ad9ae-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="ad9ae-122">Szczegółowy przewodnik dotyczący potoków usługi Azure DevOps ciągłej integracji/ciągłego wdrażania, wdrażanie Kubernetes, zobacz ten wpis: \\</span><span class="sxs-lookup"><span data-stu-id="ad9ae-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: \\</span></span>
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="ad9ae-123">[Poprzednie](docker-application-outer-loop-devops-workflow.md)
>[dalej](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="ad9ae-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
