---
title: "Wspólne zasady projektowania kontenera"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a9cd569a931824c4fab060b99265ea9e3ca75129
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="common-container-design-principles"></a><span data-ttu-id="90778-104">Wspólne zasady projektowania kontenera</span><span class="sxs-lookup"><span data-stu-id="90778-104">Common container design principles</span></span>

<span data-ttu-id="90778-105">Wyprzedzeniem wprowadzenie do procesu tworzenia dostępnych jest kilka podstawowych pojęć, warto zauważyć w odniesieniu do sposobu korzystania kontenerów.</span><span class="sxs-lookup"><span data-stu-id="90778-105">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="90778-106">Kontener jest równe procesu</span><span class="sxs-lookup"><span data-stu-id="90778-106">Container equals a process</span></span>

<span data-ttu-id="90778-107">W modelu kontenera kontener reprezentuje jednego procesu.</span><span class="sxs-lookup"><span data-stu-id="90778-107">In the container model, a container represents a single process.</span></span> <span data-ttu-id="90778-108">Definiując kontener jako granica procesu, rozpoczęciem tworzenia podstawowych używane do skalowania, lub wyłącz partii, procesów.</span><span class="sxs-lookup"><span data-stu-id="90778-108">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="90778-109">Po uruchomieniu kontenera Docker zobaczysz [punktu wejścia](https://docs.docker.com/engine/reference/builder/#/entrypoint) definicji.</span><span class="sxs-lookup"><span data-stu-id="90778-109">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="90778-110">Definiuje proces i okresem istnienia kontenera.</span><span class="sxs-lookup"><span data-stu-id="90778-110">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="90778-111">Po zakończeniu tego procesu, kończy się cyklu życia kontenera.</span><span class="sxs-lookup"><span data-stu-id="90778-111">When the process completes, the container life cycle ends.</span></span> <span data-ttu-id="90778-112">Brak procesy długotrwałe, takie jak serwery sieci web i krótkim okresie procesy, takie jak zadania wsadowego, które może być zaimplementowany jako Microsoft Azure [Webjob](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/).</span><span class="sxs-lookup"><span data-stu-id="90778-112">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="90778-113">Jeśli proces zakończy się niepowodzeniem, kończy się kontenera i orchestrator ma.</span><span class="sxs-lookup"><span data-stu-id="90778-113">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="90778-114">Jeśli poinstruowano orchestrator w celu zachowania pięć uruchomionych wystąpień i zawiedzie, orchestrator utworzy innego kontenera, aby zastąpić procesu nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="90778-114">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="90778-115">Proces jest uruchomiony w ramach zadania wsadowego parametrów.</span><span class="sxs-lookup"><span data-stu-id="90778-115">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="90778-116">Po zakończeniu tego procesu, praca jest ukończona.</span><span class="sxs-lookup"><span data-stu-id="90778-116">When the process completes, the work is complete.</span></span>

<span data-ttu-id="90778-117">Może się okazać scenariusz, w którym ma wiele procesów uruchomionych w jeden kontener.</span><span class="sxs-lookup"><span data-stu-id="90778-117">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="90778-118">Architektura dokumentów, nigdy nie jest nigdy "," nie ma zawsze jako "zawsze".</span><span class="sxs-lookup"><span data-stu-id="90778-118">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="90778-119">W scenariuszach wymagających wielu procesów, jest użycie wspólnego wzorca [przełożonego](http://supervisord.org/).</span><span class="sxs-lookup"><span data-stu-id="90778-119">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="90778-120">[Poprzednie] (projekt docker-applications.md) [dalej] (wbudowanymi applications.md)</span><span class="sxs-lookup"><span data-stu-id="90778-120">[Previous] (design-docker-applications.md) [Next] (monolithic-applications.md)</span></span>
