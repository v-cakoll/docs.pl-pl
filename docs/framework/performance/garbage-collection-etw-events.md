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
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149737"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="69f19-102">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="69f19-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="69f19-103">Te zdarzenia zbierać informacje dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="69f19-104">Pomagają w diagnostyce i debugowania, w tym określanie, ile razy wyrzucania elementów bezużytecznych zostało wykonane, ile pamięci została zwolniona podczas wyrzucania elementów bezużytecznych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="69f19-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="69f19-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="69f19-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="69f19-106">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="69f19-107">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="69f19-108">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="69f19-109">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="69f19-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="69f19-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="69f19-111">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="69f19-112">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="69f19-113">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="69f19-114">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="69f19-115">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="69f19-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="69f19-116">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="69f19-117">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="69f19-118">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="69f19-119">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="69f19-120">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="69f19-121">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="69f19-122">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="69f19-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="69f19-123">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-123">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-124">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-124">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-125">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-125">(0x1)</span></span>|<span data-ttu-id="69f19-126">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-127">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-128">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-128">Event</span></span>|<span data-ttu-id="69f19-129">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-129">Event ID</span></span>|<span data-ttu-id="69f19-130">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="69f19-131">1</span><span class="sxs-lookup"><span data-stu-id="69f19-131">1</span></span>|<span data-ttu-id="69f19-132">Wyrzucanie elementów bezużytecznych zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="69f19-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="69f19-133">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="69f19-134">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="69f19-134">Field name</span></span>|<span data-ttu-id="69f19-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="69f19-135">Data type</span></span>|<span data-ttu-id="69f19-136">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69f19-137">Licznik</span><span class="sxs-lookup"><span data-stu-id="69f19-137">Count</span></span>|<span data-ttu-id="69f19-138">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-138">win:UInt32</span></span>|<span data-ttu-id="69f19-139">*n*th wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="69f19-140">Głębokość</span><span class="sxs-lookup"><span data-stu-id="69f19-140">Depth</span></span>|<span data-ttu-id="69f19-141">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-141">win:UInt32</span></span>|<span data-ttu-id="69f19-142">Generowanie, które są zbierane.</span><span class="sxs-lookup"><span data-stu-id="69f19-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="69f19-143">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="69f19-143">Reason</span></span>|<span data-ttu-id="69f19-144">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-144">win:UInt32</span></span>|<span data-ttu-id="69f19-145">Dlaczego wyrzucania elementów bezużytecznych zostało wyzwolone:</span><span class="sxs-lookup"><span data-stu-id="69f19-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="69f19-146">0x0 - Alokacja sterty dla małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="69f19-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="69f19-147">0x1 — wywołane.</span><span class="sxs-lookup"><span data-stu-id="69f19-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="69f19-148">0x2 — małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="69f19-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="69f19-149">0x3 — pusta.</span><span class="sxs-lookup"><span data-stu-id="69f19-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="69f19-150">0x4 - Alokacja sterty dla dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="69f19-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="69f19-151">0x5 — Brak miejsca (dla sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="69f19-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="69f19-152">0x6 — Brak miejsca (dla sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="69f19-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="69f19-153">0x7 — wywołane, ale nie wymuszono jako blokowania.</span><span class="sxs-lookup"><span data-stu-id="69f19-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="69f19-154">Typ</span><span class="sxs-lookup"><span data-stu-id="69f19-154">Type</span></span>|<span data-ttu-id="69f19-155">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-155">win:UInt32</span></span>|<span data-ttu-id="69f19-156">0x0 — blokowanie wyrzucania elementów bezużytecznych wystąpiło poza wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="69f19-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="69f19-157">0x1 — wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="69f19-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="69f19-158">0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpił podczas wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="69f19-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="69f19-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69f19-159">ClrInstanceID</span></span>|<span data-ttu-id="69f19-160">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-160">win:UInt16</span></span>|<span data-ttu-id="69f19-161">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="69f19-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="69f19-162">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="69f19-163">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="69f19-164">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-165">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-165">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-166">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-166">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-167">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-167">(0x1)</span></span>|<span data-ttu-id="69f19-168">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-169">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-170">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-170">Event</span></span>|<span data-ttu-id="69f19-171">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-171">Event ID</span></span>|<span data-ttu-id="69f19-172">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="69f19-173">2</span><span class="sxs-lookup"><span data-stu-id="69f19-173">2</span></span>|<span data-ttu-id="69f19-174">Wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="69f19-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="69f19-175">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="69f19-176">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="69f19-176">Field name</span></span>|<span data-ttu-id="69f19-177">Typ danych</span><span class="sxs-lookup"><span data-stu-id="69f19-177">Data type</span></span>|<span data-ttu-id="69f19-178">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69f19-179">Licznik</span><span class="sxs-lookup"><span data-stu-id="69f19-179">Count</span></span>|<span data-ttu-id="69f19-180">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-180">win:UInt32</span></span>|<span data-ttu-id="69f19-181">*n*th wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="69f19-182">Głębokość</span><span class="sxs-lookup"><span data-stu-id="69f19-182">Depth</span></span>|<span data-ttu-id="69f19-183">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-183">win:UInt32</span></span>|<span data-ttu-id="69f19-184">Generowanie, które zostały zebrane.</span><span class="sxs-lookup"><span data-stu-id="69f19-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="69f19-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69f19-185">ClrInstanceID</span></span>|<span data-ttu-id="69f19-186">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-186">win:UInt16</span></span>|<span data-ttu-id="69f19-187">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="69f19-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="69f19-188">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="69f19-189">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="69f19-190">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-191">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-191">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-192">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-192">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-193">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-193">(0x1)</span></span>|<span data-ttu-id="69f19-194">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-195">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-196">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-196">Event</span></span>|<span data-ttu-id="69f19-197">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-197">Event ID</span></span>|<span data-ttu-id="69f19-198">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="69f19-199">4</span><span class="sxs-lookup"><span data-stu-id="69f19-199">4</span></span>|<span data-ttu-id="69f19-200">Pokazuje statystykę sterty na końcu każdej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="69f19-201">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="69f19-202">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="69f19-202">Field name</span></span>|<span data-ttu-id="69f19-203">Typ danych</span><span class="sxs-lookup"><span data-stu-id="69f19-203">Data type</span></span>|<span data-ttu-id="69f19-204">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69f19-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="69f19-205">GenerationSize0</span></span>|<span data-ttu-id="69f19-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-206">win:UInt64</span></span>|<span data-ttu-id="69f19-207">Rozmiar w bajtach pamięć generacji 0.</span><span class="sxs-lookup"><span data-stu-id="69f19-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="69f19-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="69f19-208">TotalPromotedSize0</span></span>|<span data-ttu-id="69f19-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-209">win:UInt64</span></span>|<span data-ttu-id="69f19-210">Liczba bajtów, które są przenoszone z generacji 0 do 1. generacji.</span><span class="sxs-lookup"><span data-stu-id="69f19-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="69f19-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="69f19-211">GenerationSize1</span></span>|<span data-ttu-id="69f19-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-212">win:UInt64</span></span>|<span data-ttu-id="69f19-213">Rozmiar w bajtach pamięci generacji 1.</span><span class="sxs-lookup"><span data-stu-id="69f19-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="69f19-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="69f19-214">TotalPromotedSize1</span></span>|<span data-ttu-id="69f19-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-215">win:UInt64</span></span>|<span data-ttu-id="69f19-216">Liczba bajtów, które są przenoszone z generacji 1 do 2. generacji.</span><span class="sxs-lookup"><span data-stu-id="69f19-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="69f19-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="69f19-217">GenerationSize2</span></span>|<span data-ttu-id="69f19-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-218">win:UInt64</span></span>|<span data-ttu-id="69f19-219">Rozmiar w bajtach pamięci generacji 2.</span><span class="sxs-lookup"><span data-stu-id="69f19-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="69f19-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="69f19-220">TotalPromotedSize2</span></span>|<span data-ttu-id="69f19-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-221">win:UInt64</span></span>|<span data-ttu-id="69f19-222">Liczba bajtów, które przetrwały w generacji 2 od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="69f19-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="69f19-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="69f19-223">GenerationSize3</span></span>|<span data-ttu-id="69f19-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-224">win:UInt64</span></span>|<span data-ttu-id="69f19-225">Rozmiar w bajtach stosu dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="69f19-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="69f19-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="69f19-226">TotalPromotedSize3</span></span>|<span data-ttu-id="69f19-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-227">win:UInt64</span></span>|<span data-ttu-id="69f19-228">Liczba bajtów, które przetrwały w stosie dużego obiektu, od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="69f19-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="69f19-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="69f19-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="69f19-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-230">win:UInt64</span></span>|<span data-ttu-id="69f19-231">Całkowity rozmiar w bajtach, obiekty, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="69f19-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="69f19-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="69f19-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="69f19-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-233">win:UInt64</span></span>|<span data-ttu-id="69f19-234">Liczba obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="69f19-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="69f19-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="69f19-235">PinnedObjectCount</span></span>|<span data-ttu-id="69f19-236">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-236">win:UInt32</span></span>|<span data-ttu-id="69f19-237">Liczba przypiętych obiektów (nieprzenośne).</span><span class="sxs-lookup"><span data-stu-id="69f19-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="69f19-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="69f19-238">SinkBlockCount</span></span>|<span data-ttu-id="69f19-239">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-239">win:UInt32</span></span>|<span data-ttu-id="69f19-240">Liczba bloków synchronizacji w użyciu.</span><span class="sxs-lookup"><span data-stu-id="69f19-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="69f19-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="69f19-241">GCHandleCount</span></span>|<span data-ttu-id="69f19-242">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-242">win:UInt32</span></span>|<span data-ttu-id="69f19-243">Obsługuje liczbę operacji wyrzucania elementów bezużytecznych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="69f19-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="69f19-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69f19-244">ClrInstanceID</span></span>|<span data-ttu-id="69f19-245">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-245">win:UInt16</span></span>|<span data-ttu-id="69f19-246">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="69f19-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="69f19-247">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="69f19-248">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="69f19-249">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-250">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-250">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-251">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-251">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-252">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-252">(0x1)</span></span>|<span data-ttu-id="69f19-253">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-254">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-255">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-255">Event</span></span>|<span data-ttu-id="69f19-256">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-256">Event ID</span></span>|<span data-ttu-id="69f19-257">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="69f19-258">5</span><span class="sxs-lookup"><span data-stu-id="69f19-258">5</span></span>|<span data-ttu-id="69f19-259">Utworzono nowy segment kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="69f19-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="69f19-260">Ponadto gdy śledzenie jest włączone na temat procesu, który jest już uruchomiony, to zdarzenie jest wywoływane dla każdego istniejącego segmentu.</span><span class="sxs-lookup"><span data-stu-id="69f19-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="69f19-261">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="69f19-262">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="69f19-262">Field name</span></span>|<span data-ttu-id="69f19-263">Typ danych</span><span class="sxs-lookup"><span data-stu-id="69f19-263">Data type</span></span>|<span data-ttu-id="69f19-264">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69f19-265">Adres</span><span class="sxs-lookup"><span data-stu-id="69f19-265">Address</span></span>|<span data-ttu-id="69f19-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-266">win:UInt64</span></span>|<span data-ttu-id="69f19-267">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="69f19-267">The address of the segment.</span></span>|  
|<span data-ttu-id="69f19-268">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="69f19-268">Size</span></span>|<span data-ttu-id="69f19-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-269">win:UInt64</span></span>|<span data-ttu-id="69f19-270">Rozmiar segmentu.</span><span class="sxs-lookup"><span data-stu-id="69f19-270">The size of the segment.</span></span>|  
|<span data-ttu-id="69f19-271">Typ</span><span class="sxs-lookup"><span data-stu-id="69f19-271">Type</span></span>|<span data-ttu-id="69f19-272">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-272">win:UInt32</span></span>|<span data-ttu-id="69f19-273">0x0 — sterty małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="69f19-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="69f19-274">0x1 — stertę dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="69f19-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="69f19-275">0x2 — tylko do odczytu sterty.</span><span class="sxs-lookup"><span data-stu-id="69f19-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="69f19-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69f19-276">ClrInstanceID</span></span>|<span data-ttu-id="69f19-277">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-277">win:UInt16</span></span>|<span data-ttu-id="69f19-278">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="69f19-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="69f19-279">Należy pamiętać, że rozmiar segmentów przydzielonej przez moduł odśmiecania pamięci jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="69f19-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="69f19-280">Twoja aplikacja nigdy nie należy wprowadzić założeń dotyczących lub zależeć od rozmiaru określonego segmentu nie ma podejmować skonfigurować ilość pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="69f19-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="69f19-281">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="69f19-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="69f19-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="69f19-283">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-284">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-284">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-285">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-285">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-286">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-286">(0x1)</span></span>|<span data-ttu-id="69f19-287">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-288">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-289">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-289">Event</span></span>|<span data-ttu-id="69f19-290">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-290">Event ID</span></span>|<span data-ttu-id="69f19-291">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="69f19-292">6</span><span class="sxs-lookup"><span data-stu-id="69f19-292">6</span></span>|<span data-ttu-id="69f19-293">Segment kolekcji wyrzucania elementów został wydany.</span><span class="sxs-lookup"><span data-stu-id="69f19-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="69f19-294">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="69f19-295">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="69f19-295">Field name</span></span>|<span data-ttu-id="69f19-296">Typ danych</span><span class="sxs-lookup"><span data-stu-id="69f19-296">Data type</span></span>|<span data-ttu-id="69f19-297">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69f19-298">Adres</span><span class="sxs-lookup"><span data-stu-id="69f19-298">Address</span></span>|<span data-ttu-id="69f19-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-299">win:UInt64</span></span>|<span data-ttu-id="69f19-300">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="69f19-300">The address of the segment.</span></span>|  
|<span data-ttu-id="69f19-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69f19-301">ClrInstanceID</span></span>|<span data-ttu-id="69f19-302">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-302">win:UInt16</span></span>|<span data-ttu-id="69f19-303">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="69f19-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="69f19-304">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="69f19-305">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="69f19-306">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-307">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-307">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-308">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-308">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-309">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-309">(0x1)</span></span>|<span data-ttu-id="69f19-310">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-311">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-312">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-312">Event</span></span>|<span data-ttu-id="69f19-313">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-313">Event ID</span></span>|<span data-ttu-id="69f19-314">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="69f19-315">7</span><span class="sxs-lookup"><span data-stu-id="69f19-315">7</span></span>|<span data-ttu-id="69f19-316">Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została rozpoczęta.</span><span class="sxs-lookup"><span data-stu-id="69f19-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="69f19-317">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-317">No event data.</span></span>  
  
 [<span data-ttu-id="69f19-318">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="69f19-319">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="69f19-320">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-321">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-321">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-322">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-322">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-323">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-323">(0x1)</span></span>|<span data-ttu-id="69f19-324">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-325">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-326">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-326">Event</span></span>|<span data-ttu-id="69f19-327">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-327">Event Id</span></span>|<span data-ttu-id="69f19-328">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="69f19-329">3</span><span class="sxs-lookup"><span data-stu-id="69f19-329">3</span></span>|<span data-ttu-id="69f19-330">Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została zakończona.</span><span class="sxs-lookup"><span data-stu-id="69f19-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="69f19-331">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-331">No event data.</span></span>  
  
 [<span data-ttu-id="69f19-332">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="69f19-333">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="69f19-334">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-335">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-335">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-336">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-336">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-337">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-337">(0x1)</span></span>|<span data-ttu-id="69f19-338">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-339">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-340">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-340">Event</span></span>|<span data-ttu-id="69f19-341">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-341">Event ID</span></span>|<span data-ttu-id="69f19-342">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="69f19-343">9</span><span class="sxs-lookup"><span data-stu-id="69f19-343">9</span></span>|<span data-ttu-id="69f19-344">Początek zawieszenia aparatu wykonywania do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="69f19-345">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="69f19-346">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="69f19-346">Field name</span></span>|<span data-ttu-id="69f19-347">Typ danych</span><span class="sxs-lookup"><span data-stu-id="69f19-347">Data type</span></span>|<span data-ttu-id="69f19-348">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69f19-349">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="69f19-349">Reason</span></span>|<span data-ttu-id="69f19-350">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-350">win:UInt16</span></span>|<span data-ttu-id="69f19-351">0x0 — inne.</span><span class="sxs-lookup"><span data-stu-id="69f19-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="69f19-352">0x1 — wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="69f19-353">0x2 — zamykania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69f19-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="69f19-354">0x3 - pitching kodu.</span><span class="sxs-lookup"><span data-stu-id="69f19-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="69f19-355">0x4 - shutdown.</span><span class="sxs-lookup"><span data-stu-id="69f19-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="69f19-356">0x5 - debugera.</span><span class="sxs-lookup"><span data-stu-id="69f19-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="69f19-357">0x6 — przygotowanie do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="69f19-358">Licznik</span><span class="sxs-lookup"><span data-stu-id="69f19-358">Count</span></span>|<span data-ttu-id="69f19-359">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-359">win:UInt32</span></span>|<span data-ttu-id="69f19-360">Liczba operacji odzyskiwania pamięci w czasie.</span><span class="sxs-lookup"><span data-stu-id="69f19-360">The GC count at the time.</span></span> <span data-ttu-id="69f19-361">Zwykle po to zobaczysz kolejnych zdarzeń początek odzyskiwania pamięci, a licznik będzie wskazywać ta liczba + 1, jak możemy zwiększyć indeksu GC podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="69f19-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69f19-362">ClrInstanceID</span></span>|<span data-ttu-id="69f19-363">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-363">win:UInt16</span></span>|<span data-ttu-id="69f19-364">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="69f19-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="69f19-365">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="69f19-366">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="69f19-367">W poniższej tabeli przedstawiono — słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="69f19-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="69f19-368">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-368">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-369">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-369">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-370">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-370">(0x1)</span></span>|<span data-ttu-id="69f19-371">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-372">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="69f19-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="69f19-373">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-373">Event</span></span>|<span data-ttu-id="69f19-374">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-374">Event ID</span></span>|<span data-ttu-id="69f19-375">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="69f19-376">8</span><span class="sxs-lookup"><span data-stu-id="69f19-376">8</span></span>|<span data-ttu-id="69f19-377">Koniec zawieszenia aparatu wykonywania do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="69f19-378">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-378">No event data.</span></span>  
  
 [<span data-ttu-id="69f19-379">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="69f19-380">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="69f19-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="69f19-381">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-382">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-382">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-383">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-383">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-384">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-384">(0x1)</span></span>|<span data-ttu-id="69f19-385">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-386">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-387">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-387">Event</span></span>|<span data-ttu-id="69f19-388">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-388">Event ID</span></span>|<span data-ttu-id="69f19-389">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="69f19-390">10</span><span class="sxs-lookup"><span data-stu-id="69f19-390">10</span></span>|<span data-ttu-id="69f19-391">Każdorazowo przydzielany około 100 KB.</span><span class="sxs-lookup"><span data-stu-id="69f19-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="69f19-392">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="69f19-393">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="69f19-393">Field name</span></span>|<span data-ttu-id="69f19-394">Typ danych</span><span class="sxs-lookup"><span data-stu-id="69f19-394">Data type</span></span>|<span data-ttu-id="69f19-395">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69f19-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="69f19-396">AllocationAmount</span></span>|<span data-ttu-id="69f19-397">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-397">win:UInt32</span></span>|<span data-ttu-id="69f19-398">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="69f19-398">The allocation size, in bytes.</span></span> <span data-ttu-id="69f19-399">Ta wartość jest prawidłowe dla alokacji, który jest mniejsza niż długość ULONG (4 294 967 295 w bajtach).</span><span class="sxs-lookup"><span data-stu-id="69f19-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="69f19-400">Jeśli alokacja jest większa, to pole zawiera obciętą wartość.</span><span class="sxs-lookup"><span data-stu-id="69f19-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="69f19-401">Użyj `AllocationAmount64` dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="69f19-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="69f19-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="69f19-402">AllocationKind</span></span>|<span data-ttu-id="69f19-403">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-403">win:UInt32</span></span>|<span data-ttu-id="69f19-404">0x0 - małych obiektów alokacji (alokacji jest sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="69f19-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="69f19-405">0x1 — alokacji dużego obiektu (alokacji znajduje się w stosie dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="69f19-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="69f19-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69f19-406">ClrInstanceID</span></span>|<span data-ttu-id="69f19-407">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-407">win:UInt16</span></span>|<span data-ttu-id="69f19-408">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="69f19-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="69f19-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="69f19-409">AllocationAmount64</span></span>|<span data-ttu-id="69f19-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="69f19-410">win:UInt64</span></span>|<span data-ttu-id="69f19-411">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="69f19-411">The allocation size, in bytes.</span></span> <span data-ttu-id="69f19-412">Ta wartość jest dokładne w przypadku bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="69f19-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="69f19-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="69f19-413">TypeId</span></span>|<span data-ttu-id="69f19-414">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="69f19-414">win:Pointer</span></span>|<span data-ttu-id="69f19-415">Adres MethodTable.</span><span class="sxs-lookup"><span data-stu-id="69f19-415">The address of the MethodTable.</span></span> <span data-ttu-id="69f19-416">W przypadku kilku typów obiektów, które zostały przydzielone podczas tego zdarzenia jest to adres MethodTable, który odpowiada ostatni obiekt przydzielony (obiekt, który spowodował zostać przekroczony próg 100 KB).</span><span class="sxs-lookup"><span data-stu-id="69f19-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="69f19-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="69f19-417">TypeName</span></span>|<span data-ttu-id="69f19-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="69f19-418">win:UnicodeString</span></span>|<span data-ttu-id="69f19-419">Nazwa typu, która została przydzielona.</span><span class="sxs-lookup"><span data-stu-id="69f19-419">The name of the type that was allocated.</span></span> <span data-ttu-id="69f19-420">W przypadku kilku typów obiektów, które zostały przydzielone podczas tego zdarzenia jest typ ostatni obiekt przydzielony (obiekt, który spowodował zostać przekroczony próg 100 KB).</span><span class="sxs-lookup"><span data-stu-id="69f19-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="69f19-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="69f19-421">HeapIndex</span></span>|<span data-ttu-id="69f19-422">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-422">win:UInt32</span></span>|<span data-ttu-id="69f19-423">Sterty, w którym został przydzielony obiekt.</span><span class="sxs-lookup"><span data-stu-id="69f19-423">The heap where the object was allocated.</span></span> <span data-ttu-id="69f19-424">Ta wartość jest 0 (zero), podczas korzystania z użyciem wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="69f19-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="69f19-425">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="69f19-426">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="69f19-427">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-428">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-428">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-429">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-429">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-430">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-430">(0x1)</span></span>|<span data-ttu-id="69f19-431">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-432">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-433">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-433">Event</span></span>|<span data-ttu-id="69f19-434">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-434">Event ID</span></span>|<span data-ttu-id="69f19-435">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="69f19-436">14</span><span class="sxs-lookup"><span data-stu-id="69f19-436">14</span></span>|<span data-ttu-id="69f19-437">Początek uruchamianie finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="69f19-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="69f19-438">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-438">No event data.</span></span>  
  
 [<span data-ttu-id="69f19-439">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="69f19-440">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="69f19-441">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-442">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-442">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-443">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-443">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-444">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-444">(0x1)</span></span>|<span data-ttu-id="69f19-445">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-446">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-447">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-447">Event</span></span>|<span data-ttu-id="69f19-448">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-448">Event ID</span></span>|<span data-ttu-id="69f19-449">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="69f19-450">13</span><span class="sxs-lookup"><span data-stu-id="69f19-450">13</span></span>|<span data-ttu-id="69f19-451">Koniec uruchamianie finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="69f19-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="69f19-452">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="69f19-453">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="69f19-453">Field name</span></span>|<span data-ttu-id="69f19-454">Typ danych</span><span class="sxs-lookup"><span data-stu-id="69f19-454">Data type</span></span>|<span data-ttu-id="69f19-455">Opis</span><span class="sxs-lookup"><span data-stu-id="69f19-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69f19-456">Licznik</span><span class="sxs-lookup"><span data-stu-id="69f19-456">Count</span></span>|<span data-ttu-id="69f19-457">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="69f19-457">win:UInt32</span></span>|<span data-ttu-id="69f19-458">Liczba finalizatorów, które zostały uruchomione.</span><span class="sxs-lookup"><span data-stu-id="69f19-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="69f19-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69f19-459">ClrInstanceID</span></span>|<span data-ttu-id="69f19-460">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="69f19-460">win:UInt16</span></span>|<span data-ttu-id="69f19-461">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="69f19-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="69f19-462">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="69f19-463">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="69f19-464">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-465">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-465">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-466">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-466">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-467">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-467">(0x1)</span></span>|<span data-ttu-id="69f19-468">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-468">Informational (4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="69f19-469">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="69f19-469">(0x10000)</span></span>|<span data-ttu-id="69f19-470">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-471">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-472">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-472">Event</span></span>|<span data-ttu-id="69f19-473">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-473">Event ID</span></span>|<span data-ttu-id="69f19-474">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="69f19-475">11</span><span class="sxs-lookup"><span data-stu-id="69f19-475">11</span></span>|<span data-ttu-id="69f19-476">Utworzono wątku kolekcji wyrzucania.</span><span class="sxs-lookup"><span data-stu-id="69f19-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="69f19-477">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-477">No event data.</span></span>  
  
 [<span data-ttu-id="69f19-478">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="69f19-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="69f19-479">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="69f19-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="69f19-480">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="69f19-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="69f19-481">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-481">Keyword for raising the event</span></span>|<span data-ttu-id="69f19-482">Poziom</span><span class="sxs-lookup"><span data-stu-id="69f19-482">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="69f19-483">(0x1)</span><span class="sxs-lookup"><span data-stu-id="69f19-483">(0x1)</span></span>|<span data-ttu-id="69f19-484">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-484">Informational (4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="69f19-485">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="69f19-485">(0x10000)</span></span>|<span data-ttu-id="69f19-486">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="69f19-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="69f19-487">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="69f19-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="69f19-488">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="69f19-488">Event</span></span>|<span data-ttu-id="69f19-489">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="69f19-489">Event ID</span></span>|<span data-ttu-id="69f19-490">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="69f19-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="69f19-491">12</span><span class="sxs-lookup"><span data-stu-id="69f19-491">12</span></span>|<span data-ttu-id="69f19-492">Wątku równoczesne wyrzucania elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="69f19-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="69f19-493">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69f19-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f19-494">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69f19-494">See also</span></span>

- [<span data-ttu-id="69f19-495">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="69f19-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
