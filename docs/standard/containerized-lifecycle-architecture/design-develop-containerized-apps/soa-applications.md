---
title: Aplikacje SOA
description: Mieć na uwadze kontenerów można też opcji wdrożenia przydatne w przypadku aplikacji SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 4fd39e075c5730cf7fddb0138cdb5267a914c91f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221267"
---
# <a name="soa-applications"></a><span data-ttu-id="99f0e-103">Aplikacje SOA</span><span class="sxs-lookup"><span data-stu-id="99f0e-103">SOA applications</span></span>

<span data-ttu-id="99f0e-104">SOA nadmiernego obciążenia termin został i jest przeznaczone tak wiele różnych rzeczy do różnych osób.</span><span class="sxs-lookup"><span data-stu-id="99f0e-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="99f0e-105">Ale co najmniej i uniwersalność, SOA, lub orientacji usługi, mean architekturę aplikacji przez podzielenie go w wielu usługach (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typach tej można struktury, takie jak podsystemów lub w innych przypadkach jako warstwy.</span><span class="sxs-lookup"><span data-stu-id="99f0e-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="99f0e-106">Obecnie można wdrożyć te usługi jako kontenery platformy Docker, która rozwiązuje problemów związanych z wdrażaniem, ponieważ wszystkie zależności są zawarte w obrębie obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="99f0e-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="99f0e-107">Jednak gdy trzeba skalowalnego w poziomie SOAs mogą wystąpić problemy wdrażania na podstawie jednego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="99f0e-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="99f0e-108">Jest to, gdzie klastra oprogramowania lub koordynatora Docker pomoże Ci.</span><span class="sxs-lookup"><span data-stu-id="99f0e-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="99f0e-109">Omówimy to bardziej szczegółowo w następnej sekcji podczas omówiony podejścia mikrousług.</span><span class="sxs-lookup"><span data-stu-id="99f0e-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="99f0e-110">Na koniec dnia rozwiązań klastrowych kontenera są przydatne, dla obu tradycyjna architektura SOA lub bardziej zaawansowanych architektury mikrousług, w której każda mikrousługa jest właścicielem swój model danych.</span><span class="sxs-lookup"><span data-stu-id="99f0e-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="99f0e-111">A dzięki wielu baz danych, możesz też może skalowalnego w poziomie warstwy danych, a nie Praca z bazami danych monolityczne, udostępniane przez usługi SOA.</span><span class="sxs-lookup"><span data-stu-id="99f0e-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="99f0e-112">Jednak dyskusję na temat dzielenia danych dotyczy wyłącznie architektury i projektu.</span><span class="sxs-lookup"><span data-stu-id="99f0e-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="99f0e-113">[Poprzednie](state-and-data-in-docker-applications.md)
>[dalej](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="99f0e-113">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>