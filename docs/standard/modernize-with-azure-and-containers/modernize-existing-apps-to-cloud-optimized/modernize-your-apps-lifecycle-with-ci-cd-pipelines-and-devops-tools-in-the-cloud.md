---
title: Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego Dostarczania i metodyki DevOps w chmurze
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 7f2637db3ed43f98d5b3b0cac43f7221388770fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611668"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="d190f-103">Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze</span><span class="sxs-lookup"><span data-stu-id="d190f-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="d190f-104">Dzisiejsze firmy muszą wprowadzać innowacje w szybkim tempie konkurencyjności w portalu marketplace.</span><span class="sxs-lookup"><span data-stu-id="d190f-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="d190f-105">Dostarczanie wysokiej jakości, nowoczesnych aplikacji wymaga narzędzi DevOps i procesy, które są niezbędne do zaimplementowania tej stałej cyklu innowacji.</span><span class="sxs-lookup"><span data-stu-id="d190f-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="d190f-106">Odpowiednie narzędzia DevOps deweloperzy mogą uprościć ciągłego wdrażania i szybciej uzyskać innowacyjne aplikacje w ręce użytkowników.</span><span class="sxs-lookup"><span data-stu-id="d190f-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="d190f-107">Chociaż utrwalonego ciągłej integracji i ciągłego wdrażania rozwiązania wprowadzenie kontenerów wprowadza nowe zagadnienia, szczególnie w przypadku, gdy pracujesz z wieloma kontenerami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d190f-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="d190f-108">Usługom DevOps platformy Azure obsługuje ciągłej integracji i wdrażania aplikacji z wieloma kontenerami do różnych środowisk za pomocą oficjalnego zadania wdrażania usługom DevOps platformy Azure:</span><span class="sxs-lookup"><span data-stu-id="d190f-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- <span data-ttu-id="d190f-109">[Wdrażanie autonomicznej maszyny Wirtualnej hosta platformy Docker](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux lub Windows Server 2016 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="d190f-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

- [<span data-ttu-id="d190f-110">Wdrażanie w usłudze Service Fabric</span><span class="sxs-lookup"><span data-stu-id="d190f-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

- [<span data-ttu-id="d190f-111">Wdrażanie w usłudze Azure Container Service — Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d190f-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="d190f-112">Ale również można wdrożyć na [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) lub DC/OS za pomocą zadań opartych na skryptach usługom DevOps platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="d190f-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="d190f-113">Aby kontynuować, ułatwiając elastyczność wdrażania, narzędzia te zawierają doskonałe wdrożenie dev do test — do produkcji środowisk dla obciążeń kontenerów, z możliwością wyboru rozwoju i ciągłej integracji/ciągłego wdrażania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d190f-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="d190f-114">Rysunek 4-12 przedstawiono potok ciągłego wdrażania, który wdraża klaster Kubernetes w usłudze Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="d190f-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Potok ciągłego wdrażania usługom DevOps platformy Azure, wdrażanie klastra Kubernetes](./media/image12.png)

> <span data-ttu-id="d190f-116">**Rysunek 4-12.**</span><span class="sxs-lookup"><span data-stu-id="d190f-116">**Figure 4-12.**</span></span> <span data-ttu-id="d190f-117">Potok ciągłego wdrażania usługom DevOps platformy Azure, wdrażanie klastra Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d190f-117">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d190f-118">[Poprzednie](modernize-your-apps-with-monitoring-and-telemetry.md)
>[dalej](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="d190f-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>