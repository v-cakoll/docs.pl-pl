---
title: Projektowanie aplikacji platformy Docker
description: Znajdź tutaj odwołanie do szczegółowego przewodnika po architekturze mikrousług, ponieważ jest to temat, który nie jest szczegółowo opisany w tym przewodniku.
ms.date: 02/15/2019
ms.openlocfilehash: b8a08658ec6c3df3e1aed596a0240223768dd647
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738463"
---
# <a name="design-docker-applications"></a><span data-ttu-id="03597-103">Projektowanie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="03597-103">Design Docker applications</span></span>

<span data-ttu-id="03597-104">W rozdziale 1 wprowadzono podstawowe pojęcia dotyczące kontenerów i platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="03597-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="03597-105">Te informacje są podstawowym poziomem informacji potrzebnych do rozpoczęcia pracy.</span><span class="sxs-lookup"><span data-stu-id="03597-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="03597-106">Jednak aplikacje dla przedsiębiorstw mogą być złożone i składają się z wielu usług zamiast jednej usługi lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="03597-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="03597-107">W przypadku tych przypadków opcjonalnych użycia należy znać dodatkowe podejścia do projektowania, takie jak architektura zorientowana na usługę (SOA) i bardziej zaawansowane koncepcje mikrousług i koncepcje aranżacji kontenera.</span><span class="sxs-lookup"><span data-stu-id="03597-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="03597-108">Zakres tego dokumentu nie ogranicza się do mikrousług, ale do dowolnego cyklu życia aplikacji platformy Docker, w związku z tym nie eksploruje architektury mikrousług w głębi, ponieważ można również używać kontenerów i platformy Docker z regularnych SOA, zadania w tle lub zadania, a nawet z monolitycznych metod wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03597-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="03597-109">**Więcej informacji** Aby dowiedzieć się więcej na temat aplikacji dla przedsiębiorstw i architektury mikrousług w głębi, przeczytaj przewodnik <https://aka.ms/MicroservicesEbook> [NET Microservices: Architektura dla konteneryzowanych aplikacji .NET,](../../microservices/index.md) które można również pobrać z .</span><span class="sxs-lookup"><span data-stu-id="03597-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="03597-110">Jednak zanim przejdziemy do cyklu życia aplikacji i DevOps, ważne jest, aby wiedzieć, jak masz zamiar zaprojektować i skonstruować aplikację i jakie są twoje wybory projektowe.</span><span class="sxs-lookup"><span data-stu-id="03597-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="03597-111">[Poprzedni](index.md)
>[następny](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="03597-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
