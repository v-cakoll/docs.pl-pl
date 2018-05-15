---
title: Implementowanie odporność aplikacji
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie odporność aplikacji
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 211814eff0f2aaf0cf71a19cfcaaeb44924fb6f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="1328c-103">Implementowanie odporność aplikacji</span><span class="sxs-lookup"><span data-stu-id="1328c-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="1328c-104">*Twoje mikrousługi i w chmurze aplikacji musi obejmować częściowe błędów, które na pewno nastąpi po pewnym czasie. Należy więc był odporny na błędy te częściowe, Utwórz projekt swojej aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="1328c-104">*Your microservice and cloud based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="1328c-105">Odporność jest możliwość skutków błędów i kontynuować działanie.</span><span class="sxs-lookup"><span data-stu-id="1328c-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="1328c-106">Nie jest o unikanie błędów, ale akceptuje fakt, że nastąpi błędów i odpowiada na je w taki sposób, który pozwala uniknąć przestoju lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="1328c-106">It is not about avoiding failures, but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="1328c-107">Celem odporności jest do zwrócenia aplikacji w pełni funkcjonalnej stan po awarii.</span><span class="sxs-lookup"><span data-stu-id="1328c-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="1328c-108">Jest trudne do projektowania i wdrażania aplikacji na podstawie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="1328c-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="1328c-109">Jednak należy zachować uruchomiony w środowisku jakiegoś awarii w przypadku niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1328c-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="1328c-110">W związku z tym należy odporność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1328c-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="1328c-111">Powinny być zaprojektowane do radzenia sobie z częściowa błędami, takich jak awarii sieci lub węzłów lub awarii w chmurze maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="1328c-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="1328c-112">Nawet mikrousług (kontenery) jest przenoszony do innego węzła w klastrze może powodować sporadyczne błędy krótkich w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1328c-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="1328c-113">Wiele pojedynczych składników aplikacji powinien uwzględniać kondycji funkcji monitorowania.</span><span class="sxs-lookup"><span data-stu-id="1328c-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="1328c-114">Wykonując wskazówki zawarte w tym rozdziale można utworzyć aplikacji działającej sprawnie mimo przejściowego przestój lub hiccups normalne, które występują w przypadku wdrożeń złożona i w chmurze.</span><span class="sxs-lookup"><span data-stu-id="1328c-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1328c-115">[Poprzednie] (.. / microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [dalej] (dojście partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="1328c-115">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span></span>
