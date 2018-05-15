---
title: Zdarzenia rywalizacji ETW
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3487b67ea49cecfd0da2b5b3f993ea54d562145d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="contention-etw-events"></a><span data-ttu-id="33d9d-102">Zdarzenia rywalizacji ETW</span><span class="sxs-lookup"><span data-stu-id="33d9d-102">Contention ETW Events</span></span>
<span data-ttu-id="33d9d-103">Zdarzenia rywalizacji są wywoływane zawsze, gdy w przypadku konfliktu między <xref:System.Threading.Monitor?displayProperty=nameWithType> blokady lub blokad natywnego używane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="33d9d-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="33d9d-104">Gdy wątek oczekuje na blokadę, podczas gdy inny wątek posiada blokady wystąpienia rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="33d9d-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="33d9d-105">W poniższej tabeli przedstawiono — słowo kluczowe, w którym są wywoływane zdarzenia rywalizacji i poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="33d9d-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="33d9d-106">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="33d9d-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="33d9d-107">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="33d9d-107">Keyword for raising the event</span></span>|<span data-ttu-id="33d9d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="33d9d-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="33d9d-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="33d9d-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="33d9d-110">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="33d9d-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="33d9d-111">W poniższej tabeli przedstawiono informacje o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="33d9d-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="33d9d-112">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="33d9d-112">Event</span></span>|<span data-ttu-id="33d9d-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="33d9d-113">Event ID</span></span>|<span data-ttu-id="33d9d-114">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="33d9d-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="33d9d-115">81</span><span class="sxs-lookup"><span data-stu-id="33d9d-115">81</span></span>|<span data-ttu-id="33d9d-116">Uruchamia rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="33d9d-116">Contention starts.</span></span> <span data-ttu-id="33d9d-117">To zdarzenie nie zawiera ilość wirowania przed wątek oczekuje na uzyskanie blokady; jest on wywoływane tylko wtedy, gdy wątek oczekuje na uzyskanie blokady.</span><span class="sxs-lookup"><span data-stu-id="33d9d-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="33d9d-118">81</span><span class="sxs-lookup"><span data-stu-id="33d9d-118">81</span></span>|<span data-ttu-id="33d9d-119">Kończy się rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="33d9d-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="33d9d-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="33d9d-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="33d9d-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="33d9d-121">Field name</span></span>|<span data-ttu-id="33d9d-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="33d9d-122">Data type</span></span>|<span data-ttu-id="33d9d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="33d9d-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="33d9d-124">Flagi</span><span class="sxs-lookup"><span data-stu-id="33d9d-124">Flags</span></span>|<span data-ttu-id="33d9d-125">Windows: UInt8</span><span class="sxs-lookup"><span data-stu-id="33d9d-125">win:UInt8</span></span>|<span data-ttu-id="33d9d-126">zarządzane 0; 1 w przypadku natywnego.</span><span class="sxs-lookup"><span data-stu-id="33d9d-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="33d9d-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="33d9d-127">ClrInstanceID</span></span>|<span data-ttu-id="33d9d-128">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="33d9d-128">win:UInt16</span></span>|<span data-ttu-id="33d9d-129">Unikatowy identyfikator wystąpienia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="33d9d-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33d9d-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33d9d-130">See Also</span></span>  
 [<span data-ttu-id="33d9d-131">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="33d9d-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
