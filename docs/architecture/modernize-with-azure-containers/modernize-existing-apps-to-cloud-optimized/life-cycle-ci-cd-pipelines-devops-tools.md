---
title: Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Modernizacja cyklu życia aplikacji za pomocą potoków ciągłej integracji i ciągłego wdrażania oraz narzędzi DevOps w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: d1aa2e156e87cafe99fb994233786f67bf7a81a1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396216"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="99198-103">Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze</span><span class="sxs-lookup"><span data-stu-id="99198-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="99198-104">Dzisiejsze firmy muszą szybko wprowadzać innowacje w rynku.</span><span class="sxs-lookup"><span data-stu-id="99198-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="99198-105">Dostarczanie wysokiej jakości nowoczesnych aplikacji wymaga narzędzi i procesów DevOps, które mają kluczowe znaczenie dla wdrożenia tego stałego cyklu innowacji.</span><span class="sxs-lookup"><span data-stu-id="99198-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="99198-106">Korzystając z odpowiednich narzędzi DevOps, deweloperzy mogą usprawnić ciągłe wdrażanie i szybciej uzyskiwać innowacyjne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="99198-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="99198-107">Mimo że są dobrze zintegrowane praktyki integracji i wdrażania, wprowadzenie kontenerów wprowadza nowe zagadnienia, szczególnie w przypadku pracy z aplikacjami wielokontenerowymi.</span><span class="sxs-lookup"><span data-stu-id="99198-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="99198-108">Azure DevOps Services obsługuje ciągłą integrację i wdrażanie aplikacji z wieloma kontenerami w różnych środowiskach za pomocą oficjalnych Azure DevOps Services zadań wdrażania:</span><span class="sxs-lookup"><span data-stu-id="99198-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="99198-109">Wdrażanie w usłudze Azure Web App for Containers</span><span class="sxs-lookup"><span data-stu-id="99198-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="99198-110">Wdróż w usłudze Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="99198-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="99198-111">Możesz również wdrożyć program [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) lub DC/OS przy użyciu Azure DevOps Services zadań opartych na skryptach.</span><span class="sxs-lookup"><span data-stu-id="99198-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="99198-112">Aby nadal ułatwiać elastyczność wdrażania, narzędzia te zapewniają doskonałe środowisko wdrażania z zakresu tworzenia i testowania do produkcji w przypadku obciążeń kontenerów, z możliwością wyboru rozwiązań programistycznych i ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="99198-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="99198-113">Rysunek 4-12 przedstawia potok ciągłego wdrażania, który jest wdrażany w klastrze Kubernetes w Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="99198-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Zrzut ekranu przedstawiający Azure DevOps Services wdrożenie w klastrze Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="99198-115">**Rysunek 4-12.**</span><span class="sxs-lookup"><span data-stu-id="99198-115">**Figure 4-12.**</span></span> <span data-ttu-id="99198-116">Azure DevOps Services potok ciągłego wdrażania, wdrażanie w klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="99198-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="99198-117">[Poprzedni](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Następny](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="99198-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
