---
title: Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Zmodernizuj cykl życia aplikacji za pomocą potoków ciągłej integracji/ciągłego dysku CD i narzędzi DevOps w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: 17a78c108bfc61471128a34191ec7a5d7cc28289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503848"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="0a27a-103">Modernizowanie cyklu życia aplikacji za pomocą potoków ciągłej integracji/ciągłego wdrażania i metodyki DevOps w chmurze</span><span class="sxs-lookup"><span data-stu-id="0a27a-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="0a27a-104">Dzisiejsze firmy muszą wprowadzać innowacje w szybkim tempie, aby być konkurencyjnym na rynku.</span><span class="sxs-lookup"><span data-stu-id="0a27a-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="0a27a-105">Dostarczanie wysokiej jakości nowoczesnych aplikacji wymaga narzędzi i procesów DevOps, które mają kluczowe znaczenie dla wdrożenia tego ciągłego cyklu innowacji.</span><span class="sxs-lookup"><span data-stu-id="0a27a-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="0a27a-106">Dzięki odpowiednim narzędziom DevOps deweloperzy mogą usprawnić ciągłe wdrażanie i szybciej urozmaicić innowacyjne aplikacje w ręce użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0a27a-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="0a27a-107">Mimo że ciągłe rozwiązania integracyjne i wdrożeniowe są dobrze ugruntowane, wprowadzenie kontenerów wprowadza nowe zagadnienia, szczególnie podczas pracy z aplikacjami wielokontenerowymi.</span><span class="sxs-lookup"><span data-stu-id="0a27a-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="0a27a-108">Usługi Azure DevOps Services obsługują ciągłą integrację i wdrażanie aplikacji wielokontenerowych w różnych środowiskach za pośrednictwem oficjalnych zadań wdrażania usług Azure DevOps Services:</span><span class="sxs-lookup"><span data-stu-id="0a27a-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="0a27a-109">Wdrażanie w aplikacji Sieci Web Azure dla kontenerów</span><span class="sxs-lookup"><span data-stu-id="0a27a-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="0a27a-110">Wdrażanie w usłudze Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="0a27a-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="0a27a-111">Ale można również wdrożyć do [docker rój](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) lub DC/OS przy użyciu zadań opartych na usługach Azure DevOps services.</span><span class="sxs-lookup"><span data-stu-id="0a27a-111">But you also can deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="0a27a-112">Aby nadal ułatwiać elastyczność wdrażania, narzędzia te zapewniają doskonałe środowisko wdrażania dev-to-test-to-production dla obciążeń kontenerów, z wyborem rozwiązań deweloperskich i ciągłej integracji/ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="0a27a-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="0a27a-113">Rysunek 4–12 przedstawia potok ciągłego wdrażania wdrażany w klastrze Kubernetes w usłudze Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="0a27a-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Zrzut ekranu przedstawiający wdrażanie usług Azure DevOps w klastrze Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="0a27a-115">**Rysunek 4-12.**</span><span class="sxs-lookup"><span data-stu-id="0a27a-115">**Figure 4-12.**</span></span> <span data-ttu-id="0a27a-116">Potoku ciągłego wdrażania usług Azure DevOps Services, wdrażającego w klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0a27a-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0a27a-117">[Poprzedni](modernize-your-apps-with-monitoring-and-telemetry.md)
>[następny](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="0a27a-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
