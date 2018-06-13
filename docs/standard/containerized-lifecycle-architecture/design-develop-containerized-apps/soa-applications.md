---
title: Aplikacje SOA
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 37313c4eb437b6b7a362456a7d1ee3b3aecb6020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569428"
---
# <a name="soa-applications"></a><span data-ttu-id="67b0b-103">Aplikacje SOA</span><span class="sxs-lookup"><span data-stu-id="67b0b-103">SOA applications</span></span>

<span data-ttu-id="67b0b-104">SOA został termin nadmiernego obciążenia i przewidziany tak wiele różnych rzeczy do innej osoby.</span><span class="sxs-lookup"><span data-stu-id="67b0b-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="67b0b-105">Ale co najmniej i najprostszy, SOA, lub orientacji usługi, średniej architektury aplikacji, decomposing go w wielu usługach (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typów tej możesz struktury, takie jak podsystemów lub warstwy z informacjami w innych przypadkach jako.</span><span class="sxs-lookup"><span data-stu-id="67b0b-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="67b0b-106">Obecnie można wdrożyć tych usług jako kontenery Docker, którego rozwiązuje problemy związane z wdrożenia, ponieważ wszystkie zależności są uwzględniane w obrazie kontenera.</span><span class="sxs-lookup"><span data-stu-id="67b0b-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="67b0b-107">Jednak gdy musisz SOAs skalowalnego w poziomie, mogą wystąpić problemy wdrażania na podstawie pojedynczego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="67b0b-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="67b0b-108">Jest to, gdzie Docker klastrowania lub oprogramowania orchestrator pomoże Ci.</span><span class="sxs-lookup"><span data-stu-id="67b0b-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="67b0b-109">Przyjrzymy to bardziej szczegółowo w następnej sekcji podczas omówione podejścia mikrousług.</span><span class="sxs-lookup"><span data-stu-id="67b0b-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="67b0b-110">Na koniec dnia rozwiązań klastrowych kontenera są przydatne, dla obu tradycyjnych architektura SOA lub bardziej zaawansowanych architektura mikrousług, w której każdy mikrousługi jest właścicielem jego modelu danych.</span><span class="sxs-lookup"><span data-stu-id="67b0b-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="67b0b-111">I dzięki użyciu wielu baz danych, możesz również można skalowalnego w poziomie warstwy danych, a nie Praca z wbudowanymi baz danych udostępnionych przez usługi SOA.</span><span class="sxs-lookup"><span data-stu-id="67b0b-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="67b0b-112">Omówienie podział danych jest jednak wyłącznie dotyczące architektury i projektu.</span><span class="sxs-lookup"><span data-stu-id="67b0b-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="67b0b-113">[Poprzednie] (state-and-data-in-docker-applications.md) [dalej] (organizowania wysoki skalowalność availability.md)</span><span class="sxs-lookup"><span data-stu-id="67b0b-113">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>
