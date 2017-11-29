---
title: "Implementowanie odporność aplikacji"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie odporność aplikacji"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a6fc2f4c963d857be06e194468e2f8514437dd1d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="3a649-104">Implementowanie odporność aplikacji</span><span class="sxs-lookup"><span data-stu-id="3a649-104">Implementing Resilient Applications</span></span>

<span data-ttu-id="3a649-105">*Twoje mikrousługi i w chmurze aplikacji musi obejmować częściowe błędów, które na pewno nastąpi po pewnym czasie. Należy więc był odporny na błędy te częściowe, Utwórz projekt swojej aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="3a649-105">*Your microservice and cloud based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="3a649-106">Odporność jest możliwość skutków błędów i kontynuować działanie.</span><span class="sxs-lookup"><span data-stu-id="3a649-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="3a649-107">Nie jest o unikanie błędów, ale akceptuje fakt, że nastąpi błędów i odpowiada na je w taki sposób, który pozwala uniknąć przestoju lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="3a649-107">It is not about avoiding failures, but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="3a649-108">Celem odporności jest do zwrócenia aplikacji w pełni funkcjonalnej stan po awarii.</span><span class="sxs-lookup"><span data-stu-id="3a649-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="3a649-109">Jest trudne do projektowania i wdrażania aplikacji na podstawie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="3a649-109">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="3a649-110">Jednak należy zachować uruchomiony w środowisku jakiegoś awarii w przypadku niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a649-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="3a649-111">W związku z tym należy odporność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a649-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="3a649-112">Powinny być zaprojektowane do radzenia sobie z częściowa błędami, takich jak awarii sieci lub węzłów lub awarii w chmurze maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="3a649-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="3a649-113">Nawet mikrousług (kontenery) jest przenoszony do innego węzła w klastrze może powodować sporadyczne błędy krótkich w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a649-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="3a649-114">Wiele pojedynczych składników aplikacji powinien uwzględniać kondycji funkcji monitorowania.</span><span class="sxs-lookup"><span data-stu-id="3a649-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="3a649-115">Wykonując wskazówki zawarte w tym rozdziale można utworzyć aplikacji działającej sprawnie mimo przejściowego przestój lub hiccups normalne, które występują w przypadku wdrożeń złożona i w chmurze.</span><span class="sxs-lookup"><span data-stu-id="3a649-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="3a649-116">[Poprzednie] (.. / microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [dalej] (dojście partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="3a649-116">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span></span>
