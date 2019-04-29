---
title: Wnioski
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów Windows | wnioski
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 62a9a38ccbe696c34ef799b574c0f5a95bc8f726
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628330"
---
# <a name="conclusions"></a><span data-ttu-id="05dca-103">Wnioski</span><span class="sxs-lookup"><span data-stu-id="05dca-103">Conclusions</span></span>

- <span data-ttu-id="05dca-104">Rozwiązania oparte na kontenerach ostatecznie zapewniają korzyści oszczędności kosztów.</span><span class="sxs-lookup"><span data-stu-id="05dca-104">Container-based solutions ultimately provide cost savings benefits.</span></span> <span data-ttu-id="05dca-105">Kontenery są rozwiązania problemów z wdrażaniem, ponieważ usuwają zajmowania się przyczyną braku zależności w środowiskach produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="05dca-105">Containers are a solution to deployment problems because they remove the friction caused by an absence of dependencies in production environments.</span></span> <span data-ttu-id="05dca-106">Przez usunięcie tych problemów, jego znacznie poprawia operacje tworzenia i testowania, metodyki DevOps i produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="05dca-106">By removing those issues, it improves Dev/Test, DevOps, and production operations significantly.</span></span>

- <span data-ttu-id="05dca-107">Kontener platformy Docker, staje się standardową jednostką wdrożenia dla dowolnej usługi lub aplikacji opartej na serwerze.</span><span class="sxs-lookup"><span data-stu-id="05dca-107">A Docker container is becoming the standard unit of deployment for any server-based application or service.</span></span>

- <span data-ttu-id="05dca-108">W środowiskach produkcyjnych należy użyć koordynatora (np. usługi Service Fabric lub Kubernetes) do hostowania aplikacji dla komputerów z systemem Windows kontenery skalowalne.</span><span class="sxs-lookup"><span data-stu-id="05dca-108">For production environments, you should use an orchestrator (like Service Fabric or Kubernetes) to host scalable Windows Containers­­–based applications.</span></span>

- <span data-ttu-id="05dca-109">Maszyny wirtualne platformy Azure, hostingu kontenerów to szybki i prosty sposób tworzenia małych środowiska deweloperskie i testowe w chmurze.</span><span class="sxs-lookup"><span data-stu-id="05dca-109">Azure VMs hosting containers are a fast and simple way to create small Dev/Test environments in the cloud.</span></span>

- <span data-ttu-id="05dca-110">Wystąpienie usługi Azure SQL Database Managed zaleca się domyślnie, migrując relacyjnych baz danych z istniejących aplikacji na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="05dca-110">Azure SQL Database Managed Instance is recommended by default when migrating your relational databases from existing applications to Azure.</span></span>

- <span data-ttu-id="05dca-111">Visual Studio 2017 i Image2Docker są podstawowych narzędzi do uruchamiania modernizowanie istniejących aplikacji .NET za pomocą kontenerów Windows, przyspieszając pobierania wprowadzenie nauki.</span><span class="sxs-lookup"><span data-stu-id="05dca-111">Visual Studio 2017 and Image2Docker are basic tools for you to start modernizing your existing .NET applications with Windows Containers by accelerating the getting started learning curve.</span></span>

- <span data-ttu-id="05dca-112">W przypadku umieszczenia konteneryzowanych aplikacji w środowisku produkcyjnym będzie zawsze utworzyć lub przyjęcie kultury DevOps i narzędzi DevOps dla potoków ciągłej integracji/ciągłego Dostarczania, takich jak usługom DevOps platformy Azure lub usługi Jenkins.</span><span class="sxs-lookup"><span data-stu-id="05dca-112">When placing containerized applications in production you will always create or adopt a DevOps culture and DevOps tools for CI/CD pipelines, like Azure DevOps Services or Jenkins.</span></span>

- <span data-ttu-id="05dca-113">Microsoft Azure oferuje najbardziej kompleksowy i kompletne środowisko do modernizacji istniejących aplikacji .NET Framework z kontenerami Windows, infrastruktury chmury i usług PaaS.</span><span class="sxs-lookup"><span data-stu-id="05dca-113">Microsoft Azure provides the most comprehensive and complete environment to modernize your existing .NET Framework applications with Windows Containers, cloud infrastructure and PaaS services.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="05dca-114">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="05dca-114">Previous</span></span>](walkthroughs-technical-get-started-overview.md)