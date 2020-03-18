---
title: Projektowanie aplikacji platformy Docker
description: Znajdź tutaj odwołanie do szczegółowego przewodnika po architekturze mikrousług, ponieważ jest to temat, który nie jest szczegółowo opisany w tym przewodniku.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295864"
---
# <a name="design-docker-applications"></a><span data-ttu-id="bf1cc-103">Projektowanie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="bf1cc-103">Design Docker applications</span></span>

<span data-ttu-id="bf1cc-104">Rozdział 1 wprowadził podstawowe pojęcia dotyczące kontenerów i platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="bf1cc-105">Te informacje są podstawowym poziomem informacji potrzebnych do rozpoczęcia pracy.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="bf1cc-106">Ale aplikacje dla przedsiębiorstw mogą być złożone i składają się z wielu usług zamiast pojedynczej usługi lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="bf1cc-107">W przypadku tych opcjonalnych przypadków użycia należy znać dodatkowe podejścia do projektowania, takie jak architektura zorientowana na usługi (SOA) i bardziej zaawansowane pojęcia dotyczące mikrousług i koncepcje aranżacji kontenerów.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="bf1cc-108">Zakres tego dokumentu nie jest ograniczona do mikrousług, ale do dowolnego cyklu życia aplikacji platformy Docker, w związku z tym nie eksploruje architektury mikrousług w głębi, ponieważ można również używać kontenerów i platformy Docker z regularnych SOA, zadania w tle lub zadania, a nawet nawet z monolitycznymi podejściami do wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="bf1cc-109">**Więcej informacji** Aby dowiedzieć się więcej o aplikacjach dla przedsiębiorstw i architekturze mikrousług, przeczytaj przewodnik [NET Microservices: Architecture for Containerized .NET Applications,](../../microservices/index.md) które można również pobrać z <https://aka.ms/MicroservicesEbook>programu .</span><span class="sxs-lookup"><span data-stu-id="bf1cc-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="bf1cc-110">Jednak zanim przejdziemy do cyklu życia aplikacji i DevOps, ważne jest, aby wiedzieć, jak zamierzasz projektować i konstruować aplikację i jakie są twoje wybory projektowe.</span><span class="sxs-lookup"><span data-stu-id="bf1cc-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bf1cc-111">[Poprzedni](index.md)
>[następny](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="bf1cc-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
