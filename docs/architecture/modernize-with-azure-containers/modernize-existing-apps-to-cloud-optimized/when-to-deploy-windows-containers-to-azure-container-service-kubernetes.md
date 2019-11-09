---
title: Kiedy należy wdrażać kontenery systemu Windows w celu Azure Container Service (to jest Kubernetes)
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Kiedy należy wdrażać kontenery systemu Windows w celu Azure Container Service (to jest Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676911"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="c72df-103">Kiedy należy wdrażać kontenery systemu Windows w celu Azure Container Service (to jest Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="c72df-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="c72df-104">Azure Container Service optymalizuje konfigurację popularnych narzędzi i technologii typu "open source" przeznaczonych dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c72df-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="c72df-105">Uzyskasz otwarte rozwiązanie, które oferuje przenośność dla kontenerów i konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c72df-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="c72df-106">Wybierasz rozmiar, liczbę hostów i narzędzia programu Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="c72df-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="c72df-107">Azure Container Service obsługuje infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="c72df-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="c72df-108">Jeśli już pracujesz z koordynatorami typu "open source", takimi jak Kubernetes, Docker Swarm lub DC/OS, nie musisz zmieniać istniejących praktyk zarządzania w celu przenoszenia obciążeń kontenera do chmury.</span><span class="sxs-lookup"><span data-stu-id="c72df-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="c72df-109">Skorzystaj z narzędzi do zarządzania aplikacjami, które są już znane, i Połącz się za pośrednictwem standardowych punktów końcowych interfejsu API dla wybranego koordynatora.</span><span class="sxs-lookup"><span data-stu-id="c72df-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="c72df-110">Wszystkie te koordynatorzy są dojrzałymi środowiskami, jeśli używasz kontenerów platformy Docker systemu Linux, ale może to być tylko w wersji zapoznawczej dla kontenerów Windows.</span><span class="sxs-lookup"><span data-stu-id="c72df-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="c72df-111">Na przykład w Kubernetes, obsługa kontenerów jest natywna (obywatel pierwszej klasy), więc korzystanie z kontenerów systemu Windows na Kubernetes jest również skuteczne (w wersji zapoznawczej w usłudze ACS od początku 2018).</span><span class="sxs-lookup"><span data-stu-id="c72df-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="c72df-112">Ważna Uwaga: rozwijająca się i "więcej PaaS" wersja usług ACS (Azure Container Service) dla Kubernetes to AKS (usługa Azure Kubernetes Service), jednak kontenery systemu Windows nadal nie są obsługiwane w przypadku wersji Q2 2018, ale będzie ona dostępna wkrótce.</span><span class="sxs-lookup"><span data-stu-id="c72df-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c72df-113">[Poprzedni](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[dalej](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="c72df-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
