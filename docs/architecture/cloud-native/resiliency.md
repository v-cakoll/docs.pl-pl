---
title: Odporność rozwiązań natywnych dla chmury
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Natywna odporność w chmurze
ms.date: 06/30/2019
ms.openlocfilehash: 427405d95534c4467ab519c2188fe88e2f18e2b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781083"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="a6d0b-103">Odporność rozwiązań natywnych dla chmury</span><span class="sxs-lookup"><span data-stu-id="a6d0b-103">Cloud-native resiliency</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a6d0b-104">Odporność to zdolność systemu do reagowania na awarie i nadal pozostaje funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="a6d0b-105">Nie ma on na uniknięcie błędu.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-105">It isn't about avoiding failure.</span></span> <span data-ttu-id="a6d0b-106">Jednak przyjmujemy, że ten błąd jest nieunikniony w systemach opartych na chmurze i kompilowanie aplikacji w celu reagowania na nią.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-106">But it's about accepting that failure is inevitable in cloud-based systems and building your application to respond to it.</span></span> <span data-ttu-id="a6d0b-107">Celem odporności jest przywrócenie aplikacji do stanu w pełni funkcjonalnym po awarii.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-107">The end-goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="a6d0b-108">W przeciwieństwie do tradycyjnych aplikacji monolitycznych, gdzie wszystko działa razem w pojedynczym procesie, systemy natywne w chmurze stosują architekturę rozproszoną, jak pokazano na rysunku 6-1:</span><span class="sxs-lookup"><span data-stu-id="a6d0b-108">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace distributed architecture as shown in Figure 6-1:</span></span>

![Rozproszone środowisko natywne w chmurze](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="a6d0b-110">**Rysunek 6-1.**</span><span class="sxs-lookup"><span data-stu-id="a6d0b-110">**Figure 6-1.**</span></span> <span data-ttu-id="a6d0b-111">Rozproszone środowisko natywne w chmurze</span><span class="sxs-lookup"><span data-stu-id="a6d0b-111">Distributed cloud-native environment</span></span>

<span data-ttu-id="a6d0b-112">Na poprzedniej ilustracji należy zwrócić uwagę na to, jak każdy klient, mikrousługa i [usługa tworzenia kopii zapasowych](https://12factor.net/backing-services) oparte na chmurze wykonuje jako oddzielny proces uruchomiony na różnych serwerach, a wszystkie komunikują się za pośrednictwem wywołań sieciowych.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-112">In the previous figure, note how each client, microservice, and cloud-based [backing service](https://12factor.net/backing-services) executes as a separate process, running across different servers, all communicating via network-based calls.</span></span>

<span data-ttu-id="a6d0b-113">Co może być niewłaściwe?</span><span class="sxs-lookup"><span data-stu-id="a6d0b-113">So, what could go wrong?</span></span>

- <span data-ttu-id="a6d0b-114">Nieoczekiwane [opóźnienie sieci](https://www.techopedia.com/definition/8553/network-latency).</span><span class="sxs-lookup"><span data-stu-id="a6d0b-114">Unexpected [network latency](https://www.techopedia.com/definition/8553/network-latency).</span></span>
- <span data-ttu-id="a6d0b-115">Błędy [przejściowe](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (tymczasowe błędy łączności sieciowej).</span><span class="sxs-lookup"><span data-stu-id="a6d0b-115">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (temporary network connectivity errors).</span></span>
- <span data-ttu-id="a6d0b-116">Blokowanie przez długotrwałą operację synchroniczną.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-116">Blocking by a long-running synchronous operation.</span></span>
- <span data-ttu-id="a6d0b-117">Proces hosta, który uległ awarii i jest ponownie uruchamiany lub przenoszony.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-117">A host process that has crashed and is being restarted or moved.</span></span>
- <span data-ttu-id="a6d0b-118">Przeciążona mikrousługa, która nie może odpowiadać przez krótki czas.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-118">An overloaded microservice that can't respond for a short time.</span></span>
- <span data-ttu-id="a6d0b-119">Operacja DevOps w locie, taka jak operacja aktualizacji lub skalowania.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-119">An in-flight DevOps operation such as an update or scaling operation.</span></span>
- <span data-ttu-id="a6d0b-120">Operacja programu Orchestrator, taka jak przeniesienie usługi z jednego węzła do drugiego.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-120">An Orchestrator operation such as moving a service from one node to another.</span></span>
- <span data-ttu-id="a6d0b-121">Awarie sprzętowe sprzętu z asortymentu.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-121">Hardware failures from commodity hardware.</span></span>

<span data-ttu-id="a6d0b-122">W przypadku wdrażania usług rozproszonych w infrastrukturze opartej na chmurze czynniki z poprzedniej listy stają się bardzo prawdziwe i należy się z nimi przydzielić i rozwijać, aby z nich pracować.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-122">When deploying distributed services into cloud-based infrastructure, the factors from the previous list become very real and you must architect and develop defensively to deal with them.</span></span>

<span data-ttu-id="a6d0b-123">W systemie rozproszonym w niewielkim stopniu awaria nie będzie mniejsza, ale w przypadku skalowania w górę i w poziomie można oczekiwać więcej z tych problemów do punktu, w którym częściowa awaria stanie się normalną operacją.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-123">In a small-scale distributed system, failure will be less frequent, but as a system scales up and out, you can expect to experience more of these issues to a point where partial failure becomes normal operation.</span></span>

<span data-ttu-id="a6d0b-124">W związku z tym aplikacja i infrastruktura muszą być odporne na błędy.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-124">Therefore, your application and infrastructure must be resilient.</span></span> <span data-ttu-id="a6d0b-125">W poniższych sekcjach opisano techniki obronne, które można dodać do aplikacji, oraz wbudowane funkcje w chmurze, których można użyć, aby pomóc w wykorzystaniu punktorów przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a6d0b-125">In the following sections, we'll explore defensive techniques that you can add to your application and built-in cloud features that you can leverage to help bullet-proof your user's experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a6d0b-126">[Poprzedni](elastic-search-in-azure.md)
>[Następny](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="a6d0b-126">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>
