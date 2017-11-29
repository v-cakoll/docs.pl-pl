---
title: Projektowanie aplikacji Docker
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: db8376abf95aab51fad23f4b351cb772351117ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="design-docker-applications"></a><span data-ttu-id="51fa0-104">Projektowanie aplikacji Docker</span><span class="sxs-lookup"><span data-stu-id="51fa0-104">Design Docker applications</span></span>

<span data-ttu-id="51fa0-105">Rozdział 1 wprowadzono podstawowe pojęcia dotyczące kontenerów i Docker.</span><span class="sxs-lookup"><span data-stu-id="51fa0-105">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="51fa0-106">Te informacje jest podstawowy poziom informacje wymagane do rozpoczęcia pracy.</span><span class="sxs-lookup"><span data-stu-id="51fa0-106">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="51fa0-107">Jednak aplikacje przedsiębiorstwa mogą być złożone i składać się z wielu usług zamiast jednej usługi lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="51fa0-107">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="51fa0-108">W tych przypadkach opcjonalnym użyciem musisz wiedzieć dodatkowe podejścia do projektu, takie jak architektura Service-Oriented (SOA) oraz bardziej zaawansowanych mikrousług pojęcia i kontener pojęcia aranżacji.</span><span class="sxs-lookup"><span data-stu-id="51fa0-108">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="51fa0-109">Zakres tego dokumentu nie jest ograniczone do mikrousług, ale do dowolnego Docker cyklu życia aplikacji, w związku z tym go nie Eksploruj architektura mikrousług szczegółowo ponieważ możesz również użyć kontenery i Docker z zadań, zadania w tle i regularnie Wyspy, lub nawet z metod wdrażania wbudowanymi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51fa0-109">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="51fa0-110">Przed uzyskujemy w cyklu życia aplikacji i opracowywania oprogramowania, należy wiedzieć, jak zamierzasz projektowania i tworzenia aplikacji i jakie są opcje projektu.</span><span class="sxs-lookup"><span data-stu-id="51fa0-110">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="51fa0-111">[Poprzednie] (index.md) [dalej] (typowe kontenera projekt principles.md)</span><span class="sxs-lookup"><span data-stu-id="51fa0-111">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
