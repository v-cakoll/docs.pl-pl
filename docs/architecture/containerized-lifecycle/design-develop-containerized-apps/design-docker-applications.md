---
title: Projektowanie aplikacji platformy Docker
description: Zapoznaj się z tym artykułem, aby uzyskać szczegółowy przewodnik dotyczący architektury mikrousług, ponieważ jest to temat, którego nie opisano w tym przewodniku.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295864"
---
# <a name="design-docker-applications"></a><span data-ttu-id="b2867-103">Projektowanie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b2867-103">Design Docker applications</span></span>

<span data-ttu-id="b2867-104">Rozdział 1 wprowadził podstawowe koncepcje dotyczące kontenerów i platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b2867-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="b2867-105">Te informacje to podstawowy poziom informacji, które należy wykonać, aby rozpocząć pracę.</span><span class="sxs-lookup"><span data-stu-id="b2867-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="b2867-106">Jednak aplikacje dla przedsiębiorstw mogą być złożone i składać się z wielu usług zamiast jednej usługi lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="b2867-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="b2867-107">W przypadku tych opcjonalnych przypadków użycia należy poznać dodatkowe podejścia do projektowania, takie jak architektura zorientowana na usługę (SOA) i bardziej zaawansowane koncepcje mikrousług i koncepcje aranżacji kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b2867-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="b2867-108">Zakres tego dokumentu nie jest ograniczony do mikrousług, ale do dowolnego cyklu życia aplikacji platformy Docker, dlatego nie sprawdza architektury mikrousług, ponieważ można również używać kontenerów i platformy Docker z regularnym elementem SOA, zadaniami w tle lub zadaniami, a nawet ze podejściami do wdrożenia aplikacji monolitycznych.</span><span class="sxs-lookup"><span data-stu-id="b2867-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="b2867-109">**Więcej informacji** Aby dowiedzieć się więcej na temat architektury aplikacji i mikrousług dla przedsiębiorstw, zapoznaj się z przewodnikiem [dotyczącym mikrousług w sieci: architekturą dla kontenerów aplikacji .NET](../../microservices/index.md) , które można również pobrać z <https://aka.ms/MicroservicesEbook>.</span><span class="sxs-lookup"><span data-stu-id="b2867-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="b2867-110">Jednak zanim przejdziemy do cyklu życia aplikacji i DevOps, ważne jest, aby wiedzieć, w jaki sposób planujesz projektowanie i konstruowanie aplikacji oraz jakie są opcje projektowania.</span><span class="sxs-lookup"><span data-stu-id="b2867-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b2867-111">[Poprzedni](index.md)
>[Następny](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="b2867-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
