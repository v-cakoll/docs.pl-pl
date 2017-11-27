---
title: "Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: f5ba7aa2cf14e7ca9f3a1f3eb12bbe236dca7e97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="c09e9-103">Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="c09e9-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="c09e9-104">Usługa kontenera platformy Azure optymalizuje konfiguracji popularnych open source narzędzia i technologie specjalnie dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c09e9-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="c09e9-105">Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność zarówno w przypadku kontenerów, jak i konfigurację aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c09e9-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="c09e9-106">Należy wybrać rozmiar, liczby hostów i narzędzia programu orchestrator.</span><span class="sxs-lookup"><span data-stu-id="c09e9-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="c09e9-107">Usługa kontenera platformy Azure obsługuje infrastrukturę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="c09e9-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="c09e9-108">Jeśli korzystasz już z orchestrators open source, takie jak Kubernetes, DC/OS lub Docker Swarm, nie musisz zmienić swoje istniejące praktyki zarządzania przenoszenie kontenera obciążeń do chmury.</span><span class="sxs-lookup"><span data-stu-id="c09e9-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="c09e9-109">Użyj narzędzi zarządzania aplikacji jest już znanych i połączenia za pomocą standardowych punktów końcowych interfejsu API programu orchestrator wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c09e9-109">Use the application management tools that you're already familiar with, and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="c09e9-110">Wszystkie te orchestrators są dojrzałe środowisk, jeśli używasz kontenery Linux Docker, ale one również obsługę kontenery systemu Windows zgodnie z 2017 (część wcześniej, część niedawno, w zależności od orchestrator).</span><span class="sxs-lookup"><span data-stu-id="c09e9-110">All these orchestrators are mature environments if you are using Linux Docker containers, but they also support Windows Containers as of 2017 (some earlier, some more recently, depending on the orchestrator).</span></span>

<span data-ttu-id="c09e9-111">Na przykład w Kubernetes, obsługa kontenerów jest native (najwyższej jakości obywateli), za pomocą kontenery systemu Windows na Kubernetes jest również bardzo wydajny i niezawodny (w wersji zapoznawczej do wcześniej dzielą 2017).</span><span class="sxs-lookup"><span data-stu-id="c09e9-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also very effective and reliable (in preview until early fall 2017).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c09e9-112">[Poprzednie](when-to-deploy-windows-containers-to-service-fabric.md)
[dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="c09e9-112">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
