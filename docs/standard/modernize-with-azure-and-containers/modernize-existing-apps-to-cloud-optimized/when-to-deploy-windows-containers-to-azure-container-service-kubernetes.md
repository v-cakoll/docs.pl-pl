---
title: Kiedy należy wdrażać kontenery Windows w usłudze Azure Container Service (czyli Kubernetes)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kiedy należy wdrażać kontenery Windows w usłudze Azure Container Service (czyli Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758566"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="006f8-103">Kiedy należy wdrażać kontenery Windows w usłudze Azure Container Service (czyli Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="006f8-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="006f8-104">Usługa Azure Container Service optymalizuje konfigurację popularnych narzędzi typu open source i technologii pod kątem platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="006f8-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="006f8-105">Uzyskujesz otwarte rozwiązanie, przenośność kontenerów i konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="006f8-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="006f8-106">Wybierasz rozmiar, liczbę hostów i narzędzia koordynatora.</span><span class="sxs-lookup"><span data-stu-id="006f8-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="006f8-107">Usługa Azure Container Service obsługuje infrastrukturę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="006f8-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="006f8-108">Jeśli pracujesz już z orkiestratorów typu open source, takich jak Kubernetes, Docker Swarm lub DC/OS, nie trzeba zmieniać swoje istniejących praktyk dotyczących zarządzania, aby przenieść obciążenia kontenerów do chmury.</span><span class="sxs-lookup"><span data-stu-id="006f8-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="006f8-109">Użyj narzędzi do zarządzania aplikacjami, które już znasz z i połączyć za pośrednictwem standardowych punktów końcowych interfejsu API dla wybranego koordynatora.</span><span class="sxs-lookup"><span data-stu-id="006f8-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="006f8-110">Wszystkie te koordynatorów są dojrzałe środowiska, jeśli korzystają z kontenerów platformy Docker w systemie Linux, ale może składać się wyłącznie w wersji zapoznawczej dla kontenerów Windows.</span><span class="sxs-lookup"><span data-stu-id="006f8-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="006f8-111">Na przykład w usłudze Kubernetes, obsługa kontenerów jest natywne ("pełnoprawnym najwyższej jakości"), za pomocą kontenerów Windows na platformie Kubernetes jest również skutecznie (wersja zapoznawcza usługi ACS, począwszy od początku 2018 roku).</span><span class="sxs-lookup"><span data-stu-id="006f8-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="006f8-112">Ważna Uwaga: Wydzielonego i "więcej PaaS" (usługi Azure Kubernetes Service) w usłudze AKS jest wersja usługi ACS (Azure Container Service) dla rozwiązania Kubernetes, jednak Windows kontenery nie są nadal obsługiwane począwszy od 2 kwartale 2018 roku, ale obsługa zostanie dodana wkrótce.</span><span class="sxs-lookup"><span data-stu-id="006f8-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="006f8-113">[Poprzednie](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[dalej](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="006f8-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
