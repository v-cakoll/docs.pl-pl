---
title: Aplikacje SOA
description: Mieć na uwadze kontenerów można też opcji wdrożenia przydatne w przypadku aplikacji SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: ee71873ac15246f979fd2b08d92280ba797ff6ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795408"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="f8892-103">Aplikacje zorientowane na usługę</span><span class="sxs-lookup"><span data-stu-id="f8892-103">Service-oriented applications</span></span>

<span data-ttu-id="f8892-104">Architektury zorientowanej na usługi (SOA) była termin nadmiernego obciążenia, który przeznaczone wiele różnych rzeczy do różnych osób.</span><span class="sxs-lookup"><span data-stu-id="f8892-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="f8892-105">Jednak jako uniwersalność, SOA oznacza, że struktury architekturę aplikacji przez podzielenie go na kilka usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typów, takich jak podsystemów lub w innych przypadkach, w jak warstwy.</span><span class="sxs-lookup"><span data-stu-id="f8892-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="f8892-106">Obecnie te usługi można wdrożyć jako kontenery platformy Docker, które rozwiązywania problemów związanych z wdrażaniem, ponieważ wszystkie zależności są uwzględnione w obrazie kontenera.</span><span class="sxs-lookup"><span data-stu-id="f8892-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="f8892-107">Jednak jeśli potrzebne jest skalowanie w poziomie SOAs, może wystąpić wyzwania Jeśli wdrażasz na podstawie jednego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f8892-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="f8892-108">Ten problem można obsługiwać przy użyciu klastra oprogramowania lub koordynatora Docker.</span><span class="sxs-lookup"><span data-stu-id="f8892-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="f8892-109">Przyjrzymy koordynatorów bardziej szczegółowo w następnej sekcji, gdy będziemy eksplorować metody mikrousług.</span><span class="sxs-lookup"><span data-stu-id="f8892-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="f8892-110">Kontenery platformy docker są przydatne (ale nie jest wymagane) dla bardziej zaawansowanych architektur mikrousług i tradycyjnych architekturach zorientowane na usługę.</span><span class="sxs-lookup"><span data-stu-id="f8892-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="f8892-111">Na koniec dnia rozwiązań klastrowych kontenera są przydatne do obu tradycyjna architektura SOA i bardziej zaawansowanych architektury mikrousług, w której każda mikrousługa jest właścicielem swój model danych.</span><span class="sxs-lookup"><span data-stu-id="f8892-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="f8892-112">A dzięki wielu baz danych, również można skalować w poziomie warstwy danych, a nie Praca z bazami danych monolityczne, udostępniane przez usługi SOA.</span><span class="sxs-lookup"><span data-stu-id="f8892-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="f8892-113">Jednak dyskusję na temat dzielenia danych dotyczy wyłącznie architektury i projektu.</span><span class="sxs-lookup"><span data-stu-id="f8892-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f8892-114">[Poprzednie](state-and-data-in-docker-applications.md)
>[dalej](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="f8892-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
