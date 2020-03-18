---
title: Kiedy wdrażać kontenery systemu Windows w usłudze Azure Container Service (czyli Kubernetes)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrażać kontenery systemu Windows w usłudze Azure Container Service (czyli Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676911"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="83854-103">Kiedy wdrażać kontenery systemu Windows w usłudze Azure Container Service (czyli Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="83854-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="83854-104">Usługa Azure Container Service optymalizuje konfigurację popularnych narzędzi i technologii typu open source specjalnie dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="83854-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="83854-105">Otrzymujesz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83854-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="83854-106">Wybierz rozmiar, liczbę hostów i narzędzia koordynatora.</span><span class="sxs-lookup"><span data-stu-id="83854-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="83854-107">Usługa Azure Container Service obsługuje infrastrukturę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="83854-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="83854-108">Jeśli pracujesz już z koordynatorami open source, takimi jak Kubernetes, Docker Swarm lub DC/OS, nie musisz zmieniać istniejących praktyk zarządzania, aby przenieść obciążenia kontenerów do chmury.</span><span class="sxs-lookup"><span data-stu-id="83854-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="83854-109">Użyj narzędzi do zarządzania aplikacjami, które już znasz i połączyć się za pomocą standardowych punktów końcowych interfejsu API dla wybranego koordynatora.</span><span class="sxs-lookup"><span data-stu-id="83854-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="83854-110">Wszystkie te koordynatory są środowisk dojrzałych, jeśli używasz kontenerów platformy Docker systemu Linux, ale może być tylko w stanie podglądu dla kontenerów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="83854-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="83854-111">Na przykład w programie Kubernetes obsługa kontenerów jest natywna (obywatel pierwszej klasy), więc korzystanie z kontenerów systemu Windows w programie Kubernetes jest również skuteczne (w wersji zapoznawczej w programie ACS od początku 2018 r.).</span><span class="sxs-lookup"><span data-stu-id="83854-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="83854-112">Ważna uwaga: Ewoluowała i "więcej PaaS" wersja ACS (Usługa Azure Container Service) dla Kubernetes jest AKS (Usługa Azure Kubernetes), jednak kontenery systemu Windows nadal nie są obsługiwane od Q2 2018, ale będzie obsługiwana wkrótce.</span><span class="sxs-lookup"><span data-stu-id="83854-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="83854-113">[Poprzedni](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[następny](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="83854-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
