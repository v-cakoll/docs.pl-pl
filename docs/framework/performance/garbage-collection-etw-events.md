---
title: Zdarzenia ETW odzyskiwania pamięci
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95762cbda4a1a251dd64fd33b2815d474f1fe2b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685220"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="ae2b1-102">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="ae2b1-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="ae2b1-103">Te zdarzenia zbierać informacje dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="ae2b1-104">Pomagają w diagnostyce i debugowania, w tym określanie, ile razy wyrzucania elementów bezużytecznych zostało wykonane, ile pamięci została zwolniona podczas wyrzucania elementów bezużytecznych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="ae2b1-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="ae2b1-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="ae2b1-106">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="ae2b1-107">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="ae2b1-108">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="ae2b1-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="ae2b1-109">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="ae2b1-110">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="ae2b1-111">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="ae2b1-112">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="ae2b1-113">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="ae2b1-114">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="ae2b1-115">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="ae2b1-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="ae2b1-116">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="ae2b1-117">GCFinalizersEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="ae2b1-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="ae2b1-118">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="ae2b1-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="ae2b1-119">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="ae2b1-120">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-121">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="ae2b1-122">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="ae2b1-123">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-123">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-124">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-126">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-127">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-128">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-128">Event</span></span>|<span data-ttu-id="ae2b1-129">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-129">Event ID</span></span>|<span data-ttu-id="ae2b1-130">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="ae2b1-131">1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-131">1</span></span>|<span data-ttu-id="ae2b1-132">Wyrzucanie elementów bezużytecznych zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="ae2b1-133">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae2b1-134">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae2b1-134">Field name</span></span>|<span data-ttu-id="ae2b1-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae2b1-135">Data type</span></span>|<span data-ttu-id="ae2b1-136">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae2b1-137">Licznik</span><span class="sxs-lookup"><span data-stu-id="ae2b1-137">Count</span></span>|<span data-ttu-id="ae2b1-138">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-138">win:UInt32</span></span>|<span data-ttu-id="ae2b1-139">*n*th wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="ae2b1-140">Głębokość</span><span class="sxs-lookup"><span data-stu-id="ae2b1-140">Depth</span></span>|<span data-ttu-id="ae2b1-141">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-141">win:UInt32</span></span>|<span data-ttu-id="ae2b1-142">Generowanie, które są zbierane.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="ae2b1-143">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ae2b1-143">Reason</span></span>|<span data-ttu-id="ae2b1-144">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-144">win:UInt32</span></span>|<span data-ttu-id="ae2b1-145">Dlaczego wyrzucania elementów bezużytecznych zostało wyzwolone:</span><span class="sxs-lookup"><span data-stu-id="ae2b1-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="ae2b1-146">0x0 - Alokacja sterty dla małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="ae2b1-147">0x1 — wywołane.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="ae2b1-148">0x2 — małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="ae2b1-149">0x3 — pusta.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="ae2b1-150">0x4 - Alokacja sterty dla dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="ae2b1-151">0x5 — Brak miejsca (dla sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="ae2b1-152">0x6 — Brak miejsca (dla sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="ae2b1-153">0x7 — wywołane, ale nie wymuszono jako blokowania.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="ae2b1-154">Typ</span><span class="sxs-lookup"><span data-stu-id="ae2b1-154">Type</span></span>|<span data-ttu-id="ae2b1-155">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-155">win:UInt32</span></span>|<span data-ttu-id="ae2b1-156">0x0 — blokowanie wyrzucania elementów bezużytecznych wystąpiło poza wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="ae2b1-157">0x1 — wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="ae2b1-158">0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpił podczas wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="ae2b1-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae2b1-159">ClrInstanceID</span></span>|<span data-ttu-id="ae2b1-160">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-160">win:UInt16</span></span>|<span data-ttu-id="ae2b1-161">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae2b1-162">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="ae2b1-163">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-164">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-165">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-165">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-166">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-168">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-169">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-170">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-170">Event</span></span>|<span data-ttu-id="ae2b1-171">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-171">Event ID</span></span>|<span data-ttu-id="ae2b1-172">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="ae2b1-173">2</span><span class="sxs-lookup"><span data-stu-id="ae2b1-173">2</span></span>|<span data-ttu-id="ae2b1-174">Wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="ae2b1-175">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae2b1-176">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae2b1-176">Field name</span></span>|<span data-ttu-id="ae2b1-177">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae2b1-177">Data type</span></span>|<span data-ttu-id="ae2b1-178">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae2b1-179">Licznik</span><span class="sxs-lookup"><span data-stu-id="ae2b1-179">Count</span></span>|<span data-ttu-id="ae2b1-180">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-180">win:UInt32</span></span>|<span data-ttu-id="ae2b1-181">*n*th wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="ae2b1-182">Głębokość</span><span class="sxs-lookup"><span data-stu-id="ae2b1-182">Depth</span></span>|<span data-ttu-id="ae2b1-183">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-183">win:UInt32</span></span>|<span data-ttu-id="ae2b1-184">Generowanie, które zostały zebrane.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="ae2b1-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae2b1-185">ClrInstanceID</span></span>|<span data-ttu-id="ae2b1-186">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-186">win:UInt16</span></span>|<span data-ttu-id="ae2b1-187">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae2b1-188">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="ae2b1-189">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-190">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-191">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-191">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-192">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-194">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-195">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-196">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-196">Event</span></span>|<span data-ttu-id="ae2b1-197">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-197">Event ID</span></span>|<span data-ttu-id="ae2b1-198">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="ae2b1-199">4</span><span class="sxs-lookup"><span data-stu-id="ae2b1-199">4</span></span>|<span data-ttu-id="ae2b1-200">Pokazuje statystykę sterty na końcu każdej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="ae2b1-201">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae2b1-202">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae2b1-202">Field name</span></span>|<span data-ttu-id="ae2b1-203">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae2b1-203">Data type</span></span>|<span data-ttu-id="ae2b1-204">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae2b1-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="ae2b1-205">GenerationSize0</span></span>|<span data-ttu-id="ae2b1-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-206">win:UInt64</span></span>|<span data-ttu-id="ae2b1-207">Rozmiar w bajtach pamięć generacji 0.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="ae2b1-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="ae2b1-208">TotalPromotedSize0</span></span>|<span data-ttu-id="ae2b1-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-209">win:UInt64</span></span>|<span data-ttu-id="ae2b1-210">Liczba bajtów, które są przenoszone z generacji 0 do 1. generacji.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="ae2b1-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-211">GenerationSize1</span></span>|<span data-ttu-id="ae2b1-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-212">win:UInt64</span></span>|<span data-ttu-id="ae2b1-213">Rozmiar w bajtach pamięci generacji 1.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="ae2b1-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-214">TotalPromotedSize1</span></span>|<span data-ttu-id="ae2b1-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-215">win:UInt64</span></span>|<span data-ttu-id="ae2b1-216">Liczba bajtów, które są przenoszone z generacji 1 do 2. generacji.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="ae2b1-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="ae2b1-217">GenerationSize2</span></span>|<span data-ttu-id="ae2b1-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-218">win:UInt64</span></span>|<span data-ttu-id="ae2b1-219">Rozmiar w bajtach pamięci generacji 2.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="ae2b1-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="ae2b1-220">TotalPromotedSize2</span></span>|<span data-ttu-id="ae2b1-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-221">win:UInt64</span></span>|<span data-ttu-id="ae2b1-222">Liczba bajtów, które przetrwały w generacji 2 od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="ae2b1-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="ae2b1-223">GenerationSize3</span></span>|<span data-ttu-id="ae2b1-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-224">win:UInt64</span></span>|<span data-ttu-id="ae2b1-225">Rozmiar w bajtach stosu dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="ae2b1-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="ae2b1-226">TotalPromotedSize3</span></span>|<span data-ttu-id="ae2b1-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-227">win:UInt64</span></span>|<span data-ttu-id="ae2b1-228">Liczba bajtów, które przetrwały w stosie dużego obiektu, od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="ae2b1-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="ae2b1-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="ae2b1-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-230">win:UInt64</span></span>|<span data-ttu-id="ae2b1-231">Całkowity rozmiar w bajtach, obiekty, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="ae2b1-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="ae2b1-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="ae2b1-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-233">win:UInt64</span></span>|<span data-ttu-id="ae2b1-234">Liczba obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="ae2b1-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="ae2b1-235">PinnedObjectCount</span></span>|<span data-ttu-id="ae2b1-236">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-236">win:UInt32</span></span>|<span data-ttu-id="ae2b1-237">Liczba przypiętych obiektów (nieprzenośne).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="ae2b1-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="ae2b1-238">SinkBlockCount</span></span>|<span data-ttu-id="ae2b1-239">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-239">win:UInt32</span></span>|<span data-ttu-id="ae2b1-240">Liczba bloków synchronizacji w użyciu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="ae2b1-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="ae2b1-241">GCHandleCount</span></span>|<span data-ttu-id="ae2b1-242">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-242">win:UInt32</span></span>|<span data-ttu-id="ae2b1-243">Obsługuje liczbę operacji wyrzucania elementów bezużytecznych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="ae2b1-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae2b1-244">ClrInstanceID</span></span>|<span data-ttu-id="ae2b1-245">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-245">win:UInt16</span></span>|<span data-ttu-id="ae2b1-246">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae2b1-247">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="ae2b1-248">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-249">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-250">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-250">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-251">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-253">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-254">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-255">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-255">Event</span></span>|<span data-ttu-id="ae2b1-256">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-256">Event ID</span></span>|<span data-ttu-id="ae2b1-257">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="ae2b1-258">5</span><span class="sxs-lookup"><span data-stu-id="ae2b1-258">5</span></span>|<span data-ttu-id="ae2b1-259">Utworzono nowy segment kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="ae2b1-260">Ponadto gdy śledzenie jest włączone na temat procesu, który jest już uruchomiony, to zdarzenie jest wywoływane dla każdego istniejącego segmentu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="ae2b1-261">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae2b1-262">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae2b1-262">Field name</span></span>|<span data-ttu-id="ae2b1-263">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae2b1-263">Data type</span></span>|<span data-ttu-id="ae2b1-264">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae2b1-265">Adres</span><span class="sxs-lookup"><span data-stu-id="ae2b1-265">Address</span></span>|<span data-ttu-id="ae2b1-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-266">win:UInt64</span></span>|<span data-ttu-id="ae2b1-267">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-267">The address of the segment.</span></span>|  
|<span data-ttu-id="ae2b1-268">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="ae2b1-268">Size</span></span>|<span data-ttu-id="ae2b1-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-269">win:UInt64</span></span>|<span data-ttu-id="ae2b1-270">Rozmiar segmentu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-270">The size of the segment.</span></span>|  
|<span data-ttu-id="ae2b1-271">Typ</span><span class="sxs-lookup"><span data-stu-id="ae2b1-271">Type</span></span>|<span data-ttu-id="ae2b1-272">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-272">win:UInt32</span></span>|<span data-ttu-id="ae2b1-273">0x0 — sterty małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="ae2b1-274">0x1 — stertę dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="ae2b1-275">0x2 — tylko do odczytu sterty.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="ae2b1-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae2b1-276">ClrInstanceID</span></span>|<span data-ttu-id="ae2b1-277">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-277">win:UInt16</span></span>|<span data-ttu-id="ae2b1-278">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="ae2b1-279">Należy pamiętać, że rozmiar segmentów przydzielonej przez moduł odśmiecania pamięci jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="ae2b1-280">Twoja aplikacja nigdy nie należy wprowadzić założeń dotyczących lub zależeć od rozmiaru określonego segmentu nie ma podejmować skonfigurować ilość pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="ae2b1-281">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="ae2b1-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="ae2b1-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-283">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-284">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-284">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-285">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-287">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-288">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-289">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-289">Event</span></span>|<span data-ttu-id="ae2b1-290">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-290">Event ID</span></span>|<span data-ttu-id="ae2b1-291">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="ae2b1-292">6</span><span class="sxs-lookup"><span data-stu-id="ae2b1-292">6</span></span>|<span data-ttu-id="ae2b1-293">Segment kolekcji wyrzucania elementów został wydany.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="ae2b1-294">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae2b1-295">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae2b1-295">Field name</span></span>|<span data-ttu-id="ae2b1-296">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae2b1-296">Data type</span></span>|<span data-ttu-id="ae2b1-297">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae2b1-298">Adres</span><span class="sxs-lookup"><span data-stu-id="ae2b1-298">Address</span></span>|<span data-ttu-id="ae2b1-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-299">win:UInt64</span></span>|<span data-ttu-id="ae2b1-300">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-300">The address of the segment.</span></span>|  
|<span data-ttu-id="ae2b1-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae2b1-301">ClrInstanceID</span></span>|<span data-ttu-id="ae2b1-302">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-302">win:UInt16</span></span>|<span data-ttu-id="ae2b1-303">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae2b1-304">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="ae2b1-305">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-306">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-307">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-307">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-308">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-310">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-311">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-312">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-312">Event</span></span>|<span data-ttu-id="ae2b1-313">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-313">Event ID</span></span>|<span data-ttu-id="ae2b1-314">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="ae2b1-315">7</span><span class="sxs-lookup"><span data-stu-id="ae2b1-315">7</span></span>|<span data-ttu-id="ae2b1-316">Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została rozpoczęta.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="ae2b1-317">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-317">No event data.</span></span>  
  
 [<span data-ttu-id="ae2b1-318">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="ae2b1-319">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-320">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-321">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-321">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-322">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-324">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-325">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-326">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-326">Event</span></span>|<span data-ttu-id="ae2b1-327">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-327">Event Id</span></span>|<span data-ttu-id="ae2b1-328">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="ae2b1-329">3</span><span class="sxs-lookup"><span data-stu-id="ae2b1-329">3</span></span>|<span data-ttu-id="ae2b1-330">Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została zakończona.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="ae2b1-331">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-331">No event data.</span></span>  
  
 [<span data-ttu-id="ae2b1-332">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="ae2b1-333">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-334">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-335">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-335">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-336">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-338">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-339">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-340">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-340">Event</span></span>|<span data-ttu-id="ae2b1-341">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-341">Event ID</span></span>|<span data-ttu-id="ae2b1-342">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="ae2b1-343">9</span><span class="sxs-lookup"><span data-stu-id="ae2b1-343">9</span></span>|<span data-ttu-id="ae2b1-344">Początek zawieszenia aparatu wykonywania do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="ae2b1-345">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae2b1-346">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae2b1-346">Field name</span></span>|<span data-ttu-id="ae2b1-347">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae2b1-347">Data type</span></span>|<span data-ttu-id="ae2b1-348">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae2b1-349">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ae2b1-349">Reason</span></span>|<span data-ttu-id="ae2b1-350">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-350">win:UInt16</span></span>|<span data-ttu-id="ae2b1-351">0x0 — inne.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="ae2b1-352">0x1 — wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="ae2b1-353">0x2 — zamykania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="ae2b1-354">0x3 - pitching kodu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="ae2b1-355">0x4 - shutdown.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="ae2b1-356">0x5 - debugera.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="ae2b1-357">0x6 — przygotowanie do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="ae2b1-358">Licznik</span><span class="sxs-lookup"><span data-stu-id="ae2b1-358">Count</span></span>|<span data-ttu-id="ae2b1-359">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-359">win:UInt32</span></span>|<span data-ttu-id="ae2b1-360">Liczba operacji odzyskiwania pamięci w czasie.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-360">The GC count at the time.</span></span> <span data-ttu-id="ae2b1-361">Zwykle po to zobaczysz kolejnych zdarzeń początek odzyskiwania pamięci, a licznik będzie wskazywać ta liczba + 1, jak możemy zwiększyć indeksu GC podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="ae2b1-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae2b1-362">ClrInstanceID</span></span>|<span data-ttu-id="ae2b1-363">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-363">win:UInt16</span></span>|<span data-ttu-id="ae2b1-364">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae2b1-365">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="ae2b1-366">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-367">W poniższej tabeli przedstawiono — słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="ae2b1-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="ae2b1-368">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-368">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-369">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-371">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-372">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="ae2b1-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="ae2b1-373">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-373">Event</span></span>|<span data-ttu-id="ae2b1-374">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-374">Event ID</span></span>|<span data-ttu-id="ae2b1-375">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="ae2b1-376">8</span><span class="sxs-lookup"><span data-stu-id="ae2b1-376">8</span></span>|<span data-ttu-id="ae2b1-377">Koniec zawieszenia aparatu wykonywania do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="ae2b1-378">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-378">No event data.</span></span>  
  
 [<span data-ttu-id="ae2b1-379">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="ae2b1-380">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="ae2b1-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="ae2b1-381">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-382">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-382">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-383">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-385">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-386">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-387">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-387">Event</span></span>|<span data-ttu-id="ae2b1-388">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-388">Event ID</span></span>|<span data-ttu-id="ae2b1-389">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="ae2b1-390">10</span><span class="sxs-lookup"><span data-stu-id="ae2b1-390">10</span></span>|<span data-ttu-id="ae2b1-391">Każdorazowo przydzielany około 100 KB.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="ae2b1-392">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae2b1-393">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae2b1-393">Field name</span></span>|<span data-ttu-id="ae2b1-394">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae2b1-394">Data type</span></span>|<span data-ttu-id="ae2b1-395">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae2b1-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="ae2b1-396">AllocationAmount</span></span>|<span data-ttu-id="ae2b1-397">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-397">win:UInt32</span></span>|<span data-ttu-id="ae2b1-398">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-398">The allocation size, in bytes.</span></span> <span data-ttu-id="ae2b1-399">Ta wartość jest prawidłowe dla alokacji, który jest mniejsza niż długość ULONG (4 294 967 295 w bajtach).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="ae2b1-400">Jeśli alokacja jest większa, to pole zawiera obciętą wartość.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="ae2b1-401">Użyj `AllocationAmount64` dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="ae2b1-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="ae2b1-402">AllocationKind</span></span>|<span data-ttu-id="ae2b1-403">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-403">win:UInt32</span></span>|<span data-ttu-id="ae2b1-404">0x0 - małych obiektów alokacji (alokacji jest sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="ae2b1-405">0x1 — alokacji dużego obiektu (alokacji znajduje się w stosie dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="ae2b1-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae2b1-406">ClrInstanceID</span></span>|<span data-ttu-id="ae2b1-407">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-407">win:UInt16</span></span>|<span data-ttu-id="ae2b1-408">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="ae2b1-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-409">AllocationAmount64</span></span>|<span data-ttu-id="ae2b1-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae2b1-410">win:UInt64</span></span>|<span data-ttu-id="ae2b1-411">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-411">The allocation size, in bytes.</span></span> <span data-ttu-id="ae2b1-412">Ta wartość jest dokładne w przypadku bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="ae2b1-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="ae2b1-413">TypeId</span></span>|<span data-ttu-id="ae2b1-414">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="ae2b1-414">win:Pointer</span></span>|<span data-ttu-id="ae2b1-415">Adres MethodTable.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-415">The address of the MethodTable.</span></span> <span data-ttu-id="ae2b1-416">W przypadku kilku typów obiektów, które zostały przydzielone podczas tego zdarzenia jest to adres MethodTable, który odpowiada ostatni obiekt przydzielony (obiekt, który spowodował zostać przekroczony próg 100 KB).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="ae2b1-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="ae2b1-417">TypeName</span></span>|<span data-ttu-id="ae2b1-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ae2b1-418">win:UnicodeString</span></span>|<span data-ttu-id="ae2b1-419">Nazwa typu, która została przydzielona.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-419">The name of the type that was allocated.</span></span> <span data-ttu-id="ae2b1-420">W przypadku kilku typów obiektów, które zostały przydzielone podczas tego zdarzenia jest typ ostatni obiekt przydzielony (obiekt, który spowodował zostać przekroczony próg 100 KB).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="ae2b1-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="ae2b1-421">HeapIndex</span></span>|<span data-ttu-id="ae2b1-422">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-422">win:UInt32</span></span>|<span data-ttu-id="ae2b1-423">Sterty, w którym został przydzielony obiekt.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-423">The heap where the object was allocated.</span></span> <span data-ttu-id="ae2b1-424">Ta wartość jest 0 (zero), podczas korzystania z użyciem wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="ae2b1-425">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="ae2b1-426">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-427">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-428">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-428">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-429">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-431">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-432">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-433">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-433">Event</span></span>|<span data-ttu-id="ae2b1-434">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-434">Event ID</span></span>|<span data-ttu-id="ae2b1-435">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="ae2b1-436">14</span><span class="sxs-lookup"><span data-stu-id="ae2b1-436">14</span></span>|<span data-ttu-id="ae2b1-437">Początek uruchamianie finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="ae2b1-438">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-438">No event data.</span></span>  
  
 [<span data-ttu-id="ae2b1-439">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="ae2b1-440">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-441">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-442">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-442">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-443">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-445">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-446">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-447">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-447">Event</span></span>|<span data-ttu-id="ae2b1-448">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-448">Event ID</span></span>|<span data-ttu-id="ae2b1-449">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="ae2b1-450">13</span><span class="sxs-lookup"><span data-stu-id="ae2b1-450">13</span></span>|<span data-ttu-id="ae2b1-451">Koniec uruchamianie finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="ae2b1-452">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae2b1-453">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae2b1-453">Field name</span></span>|<span data-ttu-id="ae2b1-454">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae2b1-454">Data type</span></span>|<span data-ttu-id="ae2b1-455">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2b1-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae2b1-456">Licznik</span><span class="sxs-lookup"><span data-stu-id="ae2b1-456">Count</span></span>|<span data-ttu-id="ae2b1-457">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-457">win:UInt32</span></span>|<span data-ttu-id="ae2b1-458">Liczba finalizatorów, które zostały uruchomione.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="ae2b1-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae2b1-459">ClrInstanceID</span></span>|<span data-ttu-id="ae2b1-460">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-460">win:UInt16</span></span>|<span data-ttu-id="ae2b1-461">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae2b1-462">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="ae2b1-463">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-464">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-465">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-465">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-466">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-468">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-468">Informational (4)</span></span>|  
|<span data-ttu-id="ae2b1-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ae2b1-470">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-471">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-472">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-472">Event</span></span>|<span data-ttu-id="ae2b1-473">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-473">Event ID</span></span>|<span data-ttu-id="ae2b1-474">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="ae2b1-475">11</span><span class="sxs-lookup"><span data-stu-id="ae2b1-475">11</span></span>|<span data-ttu-id="ae2b1-476">Utworzono wątku kolekcji wyrzucania.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="ae2b1-477">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-477">No event data.</span></span>  
  
 [<span data-ttu-id="ae2b1-478">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ae2b1-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="ae2b1-479">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="ae2b1-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="ae2b1-480">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae2b1-481">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-481">Keyword for raising the event</span></span>|<span data-ttu-id="ae2b1-482">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae2b1-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae2b1-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ae2b1-484">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-484">Informational (4)</span></span>|  
|<span data-ttu-id="ae2b1-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ae2b1-486">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ae2b1-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="ae2b1-487">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae2b1-488">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae2b1-488">Event</span></span>|<span data-ttu-id="ae2b1-489">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae2b1-489">Event ID</span></span>|<span data-ttu-id="ae2b1-490">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae2b1-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="ae2b1-491">12</span><span class="sxs-lookup"><span data-stu-id="ae2b1-491">12</span></span>|<span data-ttu-id="ae2b1-492">Wątku równoczesne wyrzucania elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="ae2b1-493">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2b1-494">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae2b1-494">See also</span></span>
- [<span data-ttu-id="ae2b1-495">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="ae2b1-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
