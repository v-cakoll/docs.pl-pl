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
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="6d4ee-103">Tworzenie potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services dla aplikacji .NET Core 2.0 na kontenerach i wdrażanie w klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="6d4ee-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="6d4ee-104">Na rysunku 5-12 można zobaczyć scenariusz devops end-to-end obejmujący zarządzanie kodem, kompilację kodu, kompilację obrazów platformy Docker, obrazy platformy Docker wypychają do rejestru platformy Docker i na koniec wdrożenie klastra Kubernetes na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Przepływ pracy: Uruchamia się w maszynie deweloperskiej.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="6d4ee-107">**Rysunek 5-12**.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-107">**Figure 5-12**.</span></span> <span data-ttu-id="6d4ee-108">Scenariusz ciągłej integracji/dysku CD tworzenia obrazów platformy Docker i wdrażania w klastrze Kubernetes na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="6d4ee-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="6d4ee-109">Należy podkreślić, że dwa potoki, kompilacji/ciągłej integracji i wydania/dysku CD, są połączone za pośrednictwem rejestru platformy Docker (na przykład Docker Hub lub Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="6d4ee-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="6d4ee-110">Rejestr platformy Docker jest jedną z głównych różnic w porównaniu do tradycyjnego procesu ciągłej integracji/ciągłego przetwarzania bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="6d4ee-111">Jak pokazano na rysunku 5-13, pierwsza faza to potok kompilacji/CI.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="6d4ee-112">W usłudze Azure DevOps Services można tworzyć potoki kompilacji/księgi kupna, które skompilują kod, tworzyć obrazy platformy Docker i wypychać je do rejestru platformy Docker, takiego jak Docker Hub lub Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Widok przeglądarki azure devops, tworzenie definicji zadań procesu.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="6d4ee-114">**Rysunek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-114">**Figure 5-13**.</span></span> <span data-ttu-id="6d4ee-115">Tworzenie/potok pzwu w usłudze Azure DevOps tworzenia obrazów platformy Docker i wypychania obrazów do rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6d4ee-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="6d4ee-116">Druga faza polega na utworzeniu potoku wdrażania/wydania.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="6d4ee-117">W usłudze Azure DevOps Services można łatwo utworzyć potok wdrażania przeznaczony dla klastra Kubernetes przy użyciu zadań Kubernetes dla usług Azure DevOps, jak pokazano na rysunku 5-14.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Widok przeglądarki usługi Azure DevOps, wdrożenie w definicji zadań kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="6d4ee-119">**Rysunek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="6d4ee-119">**Figure 5-14**.</span></span> <span data-ttu-id="6d4ee-120">Potok wydania/dysku CD w usłudze Azure DevOps Services wdrażającej w klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="6d4ee-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Instruktaż]<span data-ttu-id="6d4ee-121"> Wdrażanie eShopModernized do Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="6d4ee-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="6d4ee-122">Aby uzyskać szczegółowy opis potoków ciągłej wdrażania usługi Azure DevOps ci/CD w kubernetes, zobacz ten wpis: </span><span class="sxs-lookup"><span data-stu-id="6d4ee-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="6d4ee-123">[Poprzedni](docker-application-outer-loop-devops-workflow.md)
>[następny](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="6d4ee-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
