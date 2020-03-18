---
title: Aplikacje SOA
description: Należy pamiętać, że kontenery mogą być również użyteczną opcją wdrażania dla aplikacji SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295274"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="4ce65-103">Aplikacje zorientowane na usługi</span><span class="sxs-lookup"><span data-stu-id="4ce65-103">Service-oriented applications</span></span>

<span data-ttu-id="4ce65-104">Service-Oriented Architecture (SOA) był nadużywany termin, który oznaczał wiele różnych rzeczy dla różnych ludzi.</span><span class="sxs-lookup"><span data-stu-id="4ce65-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="4ce65-105">Ale jako wspólny mianownik SOA oznacza, że struktura architektury aplikacji przez rozkładanie go na kilka usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typach, takich jak podsystemy lub, w innych przypadkach, jako warstwy.</span><span class="sxs-lookup"><span data-stu-id="4ce65-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="4ce65-106">Obecnie można wdrożyć te usługi jako kontenery platformy Docker, które rozwiązują problemy związane z wdrażaniem, ponieważ wszystkie zależności są uwzględnione w obrazie kontenera.</span><span class="sxs-lookup"><span data-stu-id="4ce65-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="4ce65-107">Jednak gdy trzeba skalować w sposób skalowania w sposób skalowania w czasie, mogą wystąpić problemy, jeśli wdrażasz na podstawie pojedynczych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="4ce65-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="4ce65-108">To wyzwanie można obsługiwać za pomocą oprogramowania klastrowania platformy Docker lub koordynatora.</span><span class="sxs-lookup"><span data-stu-id="4ce65-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="4ce65-109">Przyjrzymy się koordynatorów bardziej szczegółowo w następnej sekcji, gdy eksplorujemy podejścia mikrousług.</span><span class="sxs-lookup"><span data-stu-id="4ce65-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="4ce65-110">Kontenery platformy Docker są przydatne (ale nie są wymagane) zarówno dla tradycyjnych architektur zorientowanych na usługi, jak i bardziej zaawansowanych architektur mikrousług.</span><span class="sxs-lookup"><span data-stu-id="4ce65-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="4ce65-111">Na koniec dnia rozwiązania klastrowania kontenerów są przydatne zarówno dla tradycyjnej architektury SOA, jak i dla bardziej zaawansowanej architektury mikrousług, w której każda mikrousługa jest właścicielem modelu danych.</span><span class="sxs-lookup"><span data-stu-id="4ce65-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="4ce65-112">Dzięki wielu bazom danych można również skalować w poziomie warstwy danych zamiast pracować z monolitycznymi bazami danych współużytkowane przez usługi SOA.</span><span class="sxs-lookup"><span data-stu-id="4ce65-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="4ce65-113">Jednak dyskusja na temat dzielenia danych dotyczy wyłącznie architektury i projektowania.</span><span class="sxs-lookup"><span data-stu-id="4ce65-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4ce65-114">[Poprzedni](state-and-data-in-docker-applications.md)
>[następny](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="4ce65-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
