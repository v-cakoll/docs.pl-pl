---
title: Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 63907a1911b4c95f0dbecb2af33964225cf3e7b1
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="90f88-103">Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD</span><span class="sxs-lookup"><span data-stu-id="90f88-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="90f88-104">Obecnie firma potrzebuje do innowacji w tempie szybkie dla utrzymania konkurencyjności w witrynie marketplace.</span><span class="sxs-lookup"><span data-stu-id="90f88-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="90f88-105">Dostarczanie wysokiej jakości, nowoczesnych aplikacji wymaga narzędzia DevOps i procesy, które są niezbędne do zaimplementowania stałej cyklu innowacji.</span><span class="sxs-lookup"><span data-stu-id="90f88-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="90f88-106">Odpowiednie narzędzia DevOps deweloperów może usprawnić ciągłego wdrażania i szybciej Pobierz innowacyjnych aplikacje w ręce użytkowników.</span><span class="sxs-lookup"><span data-stu-id="90f88-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="90f88-107">Choć utrwalonego ciągłej integracji i wdrażania rozwiązań, wprowadzenie kontenery wprowadza nowe zagadnienia, szczególnie w przypadku, gdy użytkownik pracuje z wieloma kontenera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="90f88-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="90f88-108">Visual Studio Team Services obsługuje ciągłej integracji i wdrażanie aplikacji kontenera wielu różnych środowiskach przez oficjalnego zadania wdrożenia usługi Team Services:</span><span class="sxs-lookup"><span data-stu-id="90f88-108">Visual Studio Team Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Team Services deployment tasks:</span></span>

-   <span data-ttu-id="90f88-109">[Wdrażanie do autonomicznej maszyny Wirtualnej hosta Docker](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux lub Windows Server 2016 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="90f88-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="90f88-110">Wdrażanie sieci szkieletowej usług</span><span class="sxs-lookup"><span data-stu-id="90f88-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="90f88-111">Wdrażanie usługi kontenera platformy Azure — Kubernetes</span><span class="sxs-lookup"><span data-stu-id="90f88-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="90f88-112">Ale też można wdrożyć [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) lub DC/OS, przy użyciu zadań opartych na skryptach Team Services.</span><span class="sxs-lookup"><span data-stu-id="90f88-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Team Services script-based tasks.</span></span>

<span data-ttu-id="90f88-113">Aby kontynuować, ułatwiające elastyczności wdrożenia, te narzędzia umożliwiają napotka znakomity deweloperów do testu do produkcyjne wdrożenie kontenera w przypadku obciążeń z wyborem programowanie i rozwiązań CI/CD.</span><span class="sxs-lookup"><span data-stu-id="90f88-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="90f88-114">Rysunek 4-12 przedstawiono potoku ciągłego wdrażania, która wdraża do Kubernetes klastra usługi kontenera platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="90f88-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Visual Studio Team Services potoku ciągłego wdrażania, wdrożenie klastra Kubernetes](./media/image12.png)

> <span data-ttu-id="90f88-116">**Rysunek 4-12.**</span><span class="sxs-lookup"><span data-stu-id="90f88-116">**Figure 4-12.**</span></span> <span data-ttu-id="90f88-117">Visual Studio Team Services potoku ciągłego wdrażania, wdrożenie klastra Kubernetes</span><span class="sxs-lookup"><span data-stu-id="90f88-117">Visual Studio Team Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="90f88-118">[Poprzednie](modernize-your-apps-with-monitoring-and-telemetry.md)
[dalej](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="90f88-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
