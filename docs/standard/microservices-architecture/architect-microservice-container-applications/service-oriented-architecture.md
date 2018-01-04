---
title: "Architektura zorientowane na usługę"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Architektura zorientowane na usługę"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6a5f0f53f4208c9944adea33fe1aa3f35fed81ab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="e8d8d-104">Architektura zorientowane na usługę</span><span class="sxs-lookup"><span data-stu-id="e8d8d-104">Service-oriented architecture</span></span> 

<span data-ttu-id="e8d8d-105">Zorientowane na usługę architektura (SOA) został termin nadmiernego obciążenia i oznacza różnych rzeczy do innej osoby.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-105">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="e8d8d-106">Jednak uzyskać punkt odniesienia, SOA oznacza struktury aplikacji przez decomposing go do wielu usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane jako różnych typów, takie jak podsystemów lub warstwy.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-106">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="e8d8d-107">Te usługi staje się możliwe wdrożenie jako kontenery Docker, która rozwiązuje problemy z wdrażaniem, ponieważ wszystkie zależności są uwzględnione w obrazie kontenera.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-107">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="e8d8d-108">Po trzeba skalowanie w górę SOA aplikacji, może być skalowalności i dostępności wyzwania w przypadku wdrażania w oparciu pojedynczego hostów Docker.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-108">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="e8d8d-109">Jest to gdzie Docker klastrowania lub oprogramowania orchestrator pomoże Ci, zgodnie z objaśnieniem w kolejnych sekcjach, w których opisano wdrożenie podejścia mikrousług.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-109">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="e8d8d-110">Kontenery docker są przydatne (ale nie są wymagane) dla tradycyjnych architektury zorientowane na usługę i bardziej zaawansowanych architektury mikrousług.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="e8d8d-111">Mikrousług pochodzi od SOA, ale SOA różni się od architektury mikrousług.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-111">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="e8d8d-112">Funkcje, takie jak duży brokerzy centralnej, centralnej orchestrators na poziomie organizacji i [magistrali usługi przedsiębiorstwa (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) opisano typowe w SOA.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-112">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="e8d8d-113">Jednak w większości przypadków przed wzorce w społeczności mikrousługi są to.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-113">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="e8d8d-114">W rzeczywistości niektóre osoby argumentowało, że "architektury mikrousługi jest SOA wykonywane po prawej".</span><span class="sxs-lookup"><span data-stu-id="e8d8d-114">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="e8d8d-115">Ten przewodnik koncentruje się na mikrousług, ponieważ metoda SOA jest przetestowanego mniej niż wymagania i techniki stosowane w przypadku architektury mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-115">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="e8d8d-116">Jeśli wiesz, jak utworzyć aplikację na podstawie mikrousługi, również należy znać sposób tworzenia aplikacji opartych na usługach prostsze.</span><span class="sxs-lookup"><span data-stu-id="e8d8d-116">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="e8d8d-117">[Poprzednie] (docker aplikacji — stan data.md) [dalej] (mikrousług architecture.md)</span><span class="sxs-lookup"><span data-stu-id="e8d8d-117">[Previous] (docker-application-state-data.md) [Next] (microservices-architecture.md)</span></span>
