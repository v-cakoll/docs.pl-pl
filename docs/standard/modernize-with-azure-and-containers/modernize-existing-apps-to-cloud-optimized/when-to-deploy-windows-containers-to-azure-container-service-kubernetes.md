---
title: Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958291"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="01856-103">Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="01856-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="01856-104">Usługa kontenera platformy Azure optymalizuje konfiguracji popularnych open source narzędzia i technologie specjalnie dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="01856-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="01856-105">Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność zarówno w przypadku kontenerów, jak i konfigurację aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01856-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="01856-106">Należy wybrać rozmiar, liczby hostów i narzędzia programu orchestrator.</span><span class="sxs-lookup"><span data-stu-id="01856-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="01856-107">Usługa kontenera platformy Azure obsługuje infrastrukturę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="01856-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="01856-108">Jeśli korzystasz już z orchestrators open source, takie jak Kubernetes, DC/OS lub Docker Swarm, nie musisz zmienić swoje istniejące praktyki zarządzania przenoszenie kontenera obciążeń do chmury.</span><span class="sxs-lookup"><span data-stu-id="01856-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="01856-109">Użyj narzędzia do zarządzania aplikacjami, które znasz już i połączenia za pomocą standardowych punktów końcowych interfejsu API programu orchestrator wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="01856-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="01856-110">Wszystkie te orchestrators są dojrzałe środowisk, jeśli używasz kontenery Linux Docker, ale tylko może być w stanie Podgląd kontenery systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="01856-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="01856-111">Na przykład w Kubernetes, obsługa kontenerów jest native (najwyższej jakości obywateli), za pomocą kontenery systemu Windows na Kubernetes obowiązuje również (w wersji zapoznawczej usługi ACS od początku 2018).</span><span class="sxs-lookup"><span data-stu-id="01856-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="01856-112">Ważna Uwaga: wydzielonego i "więcej PaaS" wersja ACS (usługi kontenera platformy Azure) dla Kubernetes jest AKS (usługa Azure Kubernetes), jednak kontenery systemu Windows nie są nadal obsługiwane począwszy od 2018 K2, ale będzie możliwe wkrótce.</span><span class="sxs-lookup"><span data-stu-id="01856-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="01856-113">[Poprzednie](when-to-deploy-windows-containers-to-service-fabric.md)
[dalej](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="01856-113">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
