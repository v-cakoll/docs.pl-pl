---
title: "Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 2799f203cec2b01d2c9ff1a60ece801dc5939104
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="b57fb-103">Modernizacji cyklem życia aplikacji narzędzia DevOps w chmurze i potoki CI/CD</span><span class="sxs-lookup"><span data-stu-id="b57fb-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="b57fb-104">Obecnie firma potrzebuje do innowacji w tempie szybkie dla utrzymania konkurencyjności w witrynie marketplace.</span><span class="sxs-lookup"><span data-stu-id="b57fb-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="b57fb-105">Dostarczanie wysokiej jakości, nowoczesnych aplikacji wymaga narzędzia DevOps i procesy, które są niezbędne do zaimplementowania stałej cyklu innowacji.</span><span class="sxs-lookup"><span data-stu-id="b57fb-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="b57fb-106">Odpowiednie narzędzia DevOps deweloperów może usprawnić ciągłego wdrażania i szybciej Pobierz innowacyjnych aplikacje w ręce użytkowników.</span><span class="sxs-lookup"><span data-stu-id="b57fb-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="b57fb-107">Choć utrwalonego ciągłej integracji i wdrażania rozwiązań, wprowadzenie kontenery wprowadza nowe zagadnienia, szczególnie w przypadku, gdy użytkownik pracuje z wieloma kontenera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b57fb-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="b57fb-108">Visual Studio Team Services obsługuje ciągłej integracji i wdrażanie aplikacji kontenera wielu różnych środowiskach przez oficjalnego zadania wdrożenia usługi Team Services:</span><span class="sxs-lookup"><span data-stu-id="b57fb-108">Visual Studio Team Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Team Services deployment tasks:</span></span>

-   <span data-ttu-id="b57fb-109">[Wdrażanie do autonomicznej maszyny Wirtualnej hosta Docker](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux lub Windows Server 2016 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b57fb-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="b57fb-110">Wdrażanie sieci szkieletowej usług</span><span class="sxs-lookup"><span data-stu-id="b57fb-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="b57fb-111">Wdrażanie usługi kontenera platformy Azure — Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b57fb-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="b57fb-112">Ale też można wdrożyć [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) lub DC/OS, przy użyciu zadań opartych na skryptach Team Services.</span><span class="sxs-lookup"><span data-stu-id="b57fb-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Team Services script-based tasks.</span></span>

<span data-ttu-id="b57fb-113">Aby kontynuować, ułatwiające elastyczności wdrożenia, te narzędzia umożliwiają napotka znakomity deweloperów do testu do produkcyjne wdrożenie kontenera w przypadku obciążeń z wyborem programowanie i rozwiązań CI/CD.</span><span class="sxs-lookup"><span data-stu-id="b57fb-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="b57fb-114">Rysunek 4-12 przedstawiono potoku ciągłego wdrażania, która wdraża do Kubernetes klastra usługi kontenera platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b57fb-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Visual Studio Team Services potoku ciągłego wdrażania, wdrożenie klastra Kubernetes](./media/image12.png)

> <span data-ttu-id="b57fb-116">**Rysunek 4-12.**</span><span class="sxs-lookup"><span data-stu-id="b57fb-116">**Figure 4-12.**</span></span> <span data-ttu-id="b57fb-117">Visual Studio Team Services potoku ciągłego wdrażania, wdrożenie klastra Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b57fb-117">Visual Studio Team Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b57fb-118">[Poprzednie](modernize-your-apps-with-monitoring-and-telemetry.md)
[dalej](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="b57fb-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
