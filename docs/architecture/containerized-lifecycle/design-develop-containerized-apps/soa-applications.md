---
title: Aplikacje SOA
description: Należy pamiętać, że kontenery mogą być również użyteczną opcją wdrażania dla aplikacji SOA.
ms.date: 02/15/2019
ms.openlocfilehash: f8619cb50a7d90b911db9ff2c8ef37c3c5fde210
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738383"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="77a74-103">Aplikacje zorientowane na usługi</span><span class="sxs-lookup"><span data-stu-id="77a74-103">Service-oriented applications</span></span>

<span data-ttu-id="77a74-104">Architektura zorientowana na usługi (SOA) była nadużywanym terminem, który oznaczał wiele różnych rzeczy dla różnych ludzi.</span><span class="sxs-lookup"><span data-stu-id="77a74-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="77a74-105">Ale jako wspólny mianownik SOA oznacza, że struktura architektury aplikacji przez rozkładanie go na kilka usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typach, takich jak podsystemy lub, w innych przypadkach, jako warstwy.</span><span class="sxs-lookup"><span data-stu-id="77a74-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="77a74-106">Obecnie można wdrożyć te usługi jako kontenery platformy Docker, które rozwiązują problemy związane z wdrażaniem, ponieważ wszystkie zależności są zawarte w obrazie kontenera.</span><span class="sxs-lookup"><span data-stu-id="77a74-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="77a74-107">Jednak gdy trzeba skalować w poziomie SOA, mogą wystąpić problemy, jeśli wdrażasz na podstawie pojedynczych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="77a74-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="77a74-108">To wyzwanie można obsługiwać za pomocą oprogramowania klastrowego platformy Docker lub koordynatora.</span><span class="sxs-lookup"><span data-stu-id="77a74-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="77a74-109">Przyjrzymy się koordynatorów bardziej szczegółowo w następnej sekcji, podczas eksplorowania mikrousług podejścia.</span><span class="sxs-lookup"><span data-stu-id="77a74-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="77a74-110">Kontenery platformy Docker są przydatne (ale nie są wymagane) zarówno dla tradycyjnych architektur zorientowanych na usługi, jak i bardziej zaawansowanych architektur mikrousług.</span><span class="sxs-lookup"><span data-stu-id="77a74-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="77a74-111">Na koniec dnia rozwiązania klastrowania kontenerów są przydatne zarówno dla tradycyjnej architektury SOA, jak i dla bardziej zaawansowanej architektury mikrousług, w której każda mikrousługa jest właścicielem swojego modelu danych.</span><span class="sxs-lookup"><span data-stu-id="77a74-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="77a74-112">Dzięki wielu bazom danych można również skalować warstwę danych w poziomie zamiast pracować z monolitycznymi bazami danych współużytku udostępnianymi przez usługi SOA.</span><span class="sxs-lookup"><span data-stu-id="77a74-112">And thanks to multiple databases, you can also scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="77a74-113">Jednak dyskusja na temat podziału danych dotyczy wyłącznie architektury i projektowania.</span><span class="sxs-lookup"><span data-stu-id="77a74-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="77a74-114">[Poprzedni](state-and-data-in-docker-applications.md)
>[następny](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="77a74-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
