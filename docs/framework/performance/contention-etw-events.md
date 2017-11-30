---
title: Zdarzenia rywalizacji ETW
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d739eaf73ff8336e74130d7176697229fdffd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="contention-etw-events"></a><span data-ttu-id="299e1-102">Zdarzenia rywalizacji ETW</span><span class="sxs-lookup"><span data-stu-id="299e1-102">Contention ETW Events</span></span>
<span data-ttu-id="299e1-103">Zdarzenia rywalizacji są wywoływane zawsze, gdy w przypadku konfliktu między <xref:System.Threading.Monitor?displayProperty=nameWithType> blokady lub blokad natywnego używane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="299e1-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="299e1-104">Gdy wątek oczekuje na blokadę, podczas gdy inny wątek posiada blokady wystąpienia rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="299e1-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="299e1-105">W poniższej tabeli przedstawiono — słowo kluczowe, w którym są wywoływane zdarzenia rywalizacji i poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="299e1-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="299e1-106">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="299e1-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="299e1-107">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="299e1-107">Keyword for raising the event</span></span>|<span data-ttu-id="299e1-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="299e1-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="299e1-109">`ContentionKeyword`(0x4000)</span><span class="sxs-lookup"><span data-stu-id="299e1-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="299e1-110">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="299e1-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="299e1-111">W poniższej tabeli przedstawiono informacje o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="299e1-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="299e1-112">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="299e1-112">Event</span></span>|<span data-ttu-id="299e1-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="299e1-113">Event ID</span></span>|<span data-ttu-id="299e1-114">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="299e1-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="299e1-115">81</span><span class="sxs-lookup"><span data-stu-id="299e1-115">81</span></span>|<span data-ttu-id="299e1-116">Uruchamia rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="299e1-116">Contention starts.</span></span> <span data-ttu-id="299e1-117">To zdarzenie nie zawiera ilość wirowania przed wątek oczekuje na uzyskanie blokady; jest on wywoływane tylko wtedy, gdy wątek oczekuje na uzyskanie blokady.</span><span class="sxs-lookup"><span data-stu-id="299e1-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="299e1-118">81</span><span class="sxs-lookup"><span data-stu-id="299e1-118">81</span></span>|<span data-ttu-id="299e1-119">Kończy się rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="299e1-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="299e1-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="299e1-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="299e1-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="299e1-121">Field name</span></span>|<span data-ttu-id="299e1-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="299e1-122">Data type</span></span>|<span data-ttu-id="299e1-123">Opis</span><span class="sxs-lookup"><span data-stu-id="299e1-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="299e1-124">Flagi</span><span class="sxs-lookup"><span data-stu-id="299e1-124">Flags</span></span>|<span data-ttu-id="299e1-125">Windows: UInt8</span><span class="sxs-lookup"><span data-stu-id="299e1-125">win:UInt8</span></span>|<span data-ttu-id="299e1-126">zarządzane 0; 1 w przypadku natywnego.</span><span class="sxs-lookup"><span data-stu-id="299e1-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="299e1-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="299e1-127">ClrInstanceID</span></span>|<span data-ttu-id="299e1-128">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="299e1-128">win:UInt16</span></span>|<span data-ttu-id="299e1-129">Unikatowy identyfikator wystąpienia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="299e1-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="299e1-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="299e1-130">See Also</span></span>  
 [<span data-ttu-id="299e1-131">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="299e1-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
