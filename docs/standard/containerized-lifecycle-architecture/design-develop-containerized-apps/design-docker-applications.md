---
title: Projektowanie aplikacji platformy Docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: d02cec0595024eb7bd7c0ac46df093359680da74
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155382"
---
# <a name="design-docker-applications"></a><span data-ttu-id="35b2e-103">Projektowanie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="35b2e-103">Design Docker applications</span></span>

<span data-ttu-id="35b2e-104">Rozdział 1 wprowadzono podstawowe pojęcia dotyczące kontenerów i platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="35b2e-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="35b2e-105">Te informacje są podstawowy poziom informacje wymagane do rozpoczęcia pracy.</span><span class="sxs-lookup"><span data-stu-id="35b2e-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="35b2e-106">Jednak aplikacje dla przedsiębiorstw mogą być złożone i składa się z wielu usług, zamiast jednej usługi lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="35b2e-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="35b2e-107">Dla tych przypadków Opcjonalnie użyj musisz wiedzieć dodatkowe podejścia do projektowania, takich jak architektura Service-Oriented (SOA) i bardziej zaawansowane pojęcia mikrousług i kontenerów koncepcjami dotyczącymi organizowania.</span><span class="sxs-lookup"><span data-stu-id="35b2e-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="35b2e-108">Zakres tego dokumentu nie jest ograniczona do mikrousług, ale aby wszelkie cyklu życia aplikacji platformy Docker, w związku z tym, go nie zapoznaj się z architektury mikrousług szczegółowo ponieważ również można użyć kontenerów i platformy Docker za pomocą regularnego SAO, zadania w tle lub zadania, lub nawet za pomocą metod wdrażania aplikacji monolitycznej.</span><span class="sxs-lookup"><span data-stu-id="35b2e-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="35b2e-109">Jednak przed przejściem do cyklu życia aplikacji i metodyki DevOps, jest ważne, aby dowiedzieć się, jak zamierzasz projektowania i tworzenia aplikacji i jakie uzasadnienie wyboru tych elementów.</span><span class="sxs-lookup"><span data-stu-id="35b2e-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="35b2e-110">[Poprzednie](index.md)
>[dalej](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="35b2e-110">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>