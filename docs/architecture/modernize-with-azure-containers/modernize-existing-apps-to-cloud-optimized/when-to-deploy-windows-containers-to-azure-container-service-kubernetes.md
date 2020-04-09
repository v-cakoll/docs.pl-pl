---
title: Kiedy wdrożyć kontenery systemu Windows w usłudze kontenerów platformy Azure (czyli w usłudze Kubernetes)
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrożyć kontenery systemu Windows w usłudze kontenerów platformy Azure (czyli w usłudze Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 3ff51a70d4e158b831155ab4992ec32f5d98cedb
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987767"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="19fb7-103">Kiedy wdrożyć kontenery systemu Windows w usłudze kontenerów platformy Azure (czyli w usłudze Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="19fb7-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="19fb7-104">Usługa Azure Container Service optymalizuje konfigurację popularnych narzędzi i technologii typu open source specjalnie dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="19fb7-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="19fb7-105">Otrzymujesz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i dla konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19fb7-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="19fb7-106">Można wybrać rozmiar, liczbę hostów i narzędzia aranżatora.</span><span class="sxs-lookup"><span data-stu-id="19fb7-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="19fb7-107">Usługa Azure Container Service obsługuje infrastrukturę za Ciebie.</span><span class="sxs-lookup"><span data-stu-id="19fb7-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="19fb7-108">Jeśli już pracujesz z koordynatorami open source, takimi jak Kubernetes, Docker Swarm lub DC/OS, nie musisz zmieniać istniejących praktyk zarządzania, aby przenieść obciążenia kontenerów do chmury.</span><span class="sxs-lookup"><span data-stu-id="19fb7-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="19fb7-109">Użyj narzędzi do zarządzania aplikacjami, które są już znane i połączyć za pośrednictwem standardowych punktów końcowych interfejsu API dla koordynatora do wyboru.</span><span class="sxs-lookup"><span data-stu-id="19fb7-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="19fb7-110">Wszystkie te orchestrators są środowiskami dojrzałymi, jeśli używasz kontenerów platformy Docker systemu Linux, ale może być tylko w stanie podglądu dla kontenerów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="19fb7-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="19fb7-111">Na przykład w usłudze Kubernetes obsługa kontenerów jest natywna (obywatel pierwszej klasy), więc używanie kontenerów systemu Windows w usłudze Kubernetes jest również skuteczne (w wersji zapoznawczej w programie ACS na początku 2018 r.).</span><span class="sxs-lookup"><span data-stu-id="19fb7-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="19fb7-112">Ważna uwaga: Ewoluowała i "więcej PaaS" wersja usługi ACS (Usługa azure kontenera) dla usługi Kubernetes jest AKS (Usługa Azure Kubernetes), jednak kontenery systemu Windows nadal nie są obsługiwane od Q2 2018, ale wkrótce będą obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="19fb7-112">Important note: The evolved and "more PaaS" version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="19fb7-113">[Poprzedni](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[następny](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="19fb7-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
