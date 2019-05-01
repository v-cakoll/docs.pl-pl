---
title: Projektowanie aplikacji platformy Docker
description: Tu znaleźć odwołania do szczegółowy przewodnik dotyczący architektury mikrousług, ponieważ jest to tematu, który nie jest szczegółowo w tym przewodniku.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1d49f7509c0a12edfe375486429147e8fd240b2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799349"
---
# <a name="design-docker-applications"></a><span data-ttu-id="6ddb5-103">Projektowanie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6ddb5-103">Design Docker applications</span></span>

<span data-ttu-id="6ddb5-104">Rozdział 1 wprowadzono podstawowe pojęcia dotyczące kontenerów i platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="6ddb5-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="6ddb5-105">Te informacje są podstawowy poziom informacje wymagane do rozpoczęcia pracy.</span><span class="sxs-lookup"><span data-stu-id="6ddb5-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="6ddb5-106">Jednak aplikacje dla przedsiębiorstw mogą być złożone i składa się z wielu usług, zamiast jednej usługi lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="6ddb5-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="6ddb5-107">Dla tych przypadków Opcjonalnie użyj musisz wiedzieć dodatkowe podejścia do projektowania, takich jak architektura Service-Oriented (SOA) i bardziej zaawansowane pojęcia mikrousług i kontenerów koncepcjami dotyczącymi organizowania.</span><span class="sxs-lookup"><span data-stu-id="6ddb5-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="6ddb5-108">Zakres tego dokumentu nie jest ograniczona do mikrousług, ale aby wszelkie cyklu życia aplikacji platformy Docker, w związku z tym, go nie zapoznaj się z architektury mikrousług, bardziej ponieważ możesz również używać kontenerów i platformy Docker za pomocą regularnego SOA, zadania w tle lub zadania lub nawet za pomocą metod wdrażania aplikacji monolitycznej.</span><span class="sxs-lookup"><span data-stu-id="6ddb5-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="6ddb5-109">**Więcej informacji o** Aby dowiedzieć się więcej na temat aplikacji dla przedsiębiorstw i architektury mikrousług szczegółowo, zapoznaj się z przewodnikiem [Mikrousług .NET: Architektura aplikacji kontenerowych nimi .NET](../../microservices-architecture/index.md) , którą można również pobrać z <https://aka.ms/MicroservicesEbook>.</span><span class="sxs-lookup"><span data-stu-id="6ddb5-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices-architecture/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="6ddb5-110">Jednak przed przejściem do cyklu życia aplikacji i metodyki DevOps, jest ważne, aby dowiedzieć się, jak możesz zacząć projektowanie i tworzenie aplikacji i jakie są uzasadnienie wyboru tych elementów.</span><span class="sxs-lookup"><span data-stu-id="6ddb5-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6ddb5-111">[Poprzednie](index.md)
>[dalej](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="6ddb5-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>