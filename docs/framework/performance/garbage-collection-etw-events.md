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
ms.openlocfilehash: 13f7e935ab999ccc3cd3ea1e308e8d686bed4171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="80924-102">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="80924-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="80924-103">Te zdarzenia zbierać informacje dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="80924-104">Pomagają w diagnostyce i debugowanie, określając, ile razy wyrzucanie elementów bezużytecznych została wykonana, ile pamięci został zwolniony podczas wyrzucanie elementów bezużytecznych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="80924-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="80924-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="80924-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="80924-106">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="80924-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="80924-107">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="80924-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="80924-108">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="80924-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="80924-109">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="80924-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="80924-110">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="80924-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="80924-111">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="80924-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="80924-112">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="80924-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="80924-113">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="80924-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="80924-114">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="80924-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="80924-115">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="80924-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="80924-116">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="80924-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="80924-117">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="80924-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="80924-118">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="80924-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="80924-119">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="80924-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="80924-120">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="80924-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="80924-121">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="80924-122">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="80924-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="80924-123">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-123">Keyword for raising the event</span></span>|<span data-ttu-id="80924-124">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-126">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-127">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-128">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-128">Event</span></span>|<span data-ttu-id="80924-129">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-129">Event ID</span></span>|<span data-ttu-id="80924-130">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="80924-131">1</span><span class="sxs-lookup"><span data-stu-id="80924-131">1</span></span>|<span data-ttu-id="80924-132">Wyrzucanie elementów bezużytecznych została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="80924-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="80924-133">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="80924-134">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="80924-134">Field name</span></span>|<span data-ttu-id="80924-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="80924-135">Data type</span></span>|<span data-ttu-id="80924-136">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="80924-137">Liczba</span><span class="sxs-lookup"><span data-stu-id="80924-137">Count</span></span>|<span data-ttu-id="80924-138">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-138">win:UInt32</span></span>|<span data-ttu-id="80924-139">*n*th wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="80924-140">Głębokość</span><span class="sxs-lookup"><span data-stu-id="80924-140">Depth</span></span>|<span data-ttu-id="80924-141">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-141">win:UInt32</span></span>|<span data-ttu-id="80924-142">Generowanie zbieranych.</span><span class="sxs-lookup"><span data-stu-id="80924-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="80924-143">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="80924-143">Reason</span></span>|<span data-ttu-id="80924-144">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-144">win:UInt32</span></span>|<span data-ttu-id="80924-145">Dlaczego zostało wyzwolone odzyskiwanie pamięci:</span><span class="sxs-lookup"><span data-stu-id="80924-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="80924-146">0x0 - Alokacja sterty dla małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="80924-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="80924-147">0x1 — powstaniu.</span><span class="sxs-lookup"><span data-stu-id="80924-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="80924-148">0x2 — Brak pamięci.</span><span class="sxs-lookup"><span data-stu-id="80924-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="80924-149">0x3 — pusty.</span><span class="sxs-lookup"><span data-stu-id="80924-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="80924-150">0x4 - Alokacja sterty dla dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="80924-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="80924-151">0x5 — Brak miejsca (dla sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="80924-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="80924-152">0x6 — Brak miejsca (dla sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="80924-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="80924-153">0x7 - powstaniu, ale nie wymuszono jako blokowania.</span><span class="sxs-lookup"><span data-stu-id="80924-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="80924-154">Typ</span><span class="sxs-lookup"><span data-stu-id="80924-154">Type</span></span>|<span data-ttu-id="80924-155">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-155">win:UInt32</span></span>|<span data-ttu-id="80924-156">0x0 — blokowanie pamięci wystąpiło poza odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="80924-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="80924-157">0x1 — odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="80924-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="80924-158">0x2 — blokowanie wyrzucanie elementów bezużytecznych podczas odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="80924-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="80924-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="80924-159">ClrInstanceID</span></span>|<span data-ttu-id="80924-160">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-160">win:UInt16</span></span>|<span data-ttu-id="80924-161">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="80924-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="80924-162">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="80924-163">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="80924-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="80924-164">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-165">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-165">Keyword for raising the event</span></span>|<span data-ttu-id="80924-166">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-168">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-169">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-170">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-170">Event</span></span>|<span data-ttu-id="80924-171">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-171">Event ID</span></span>|<span data-ttu-id="80924-172">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="80924-173">2</span><span class="sxs-lookup"><span data-stu-id="80924-173">2</span></span>|<span data-ttu-id="80924-174">Wyrzucanie elementów bezużytecznych została zakończona.</span><span class="sxs-lookup"><span data-stu-id="80924-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="80924-175">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="80924-176">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="80924-176">Field name</span></span>|<span data-ttu-id="80924-177">Typ danych</span><span class="sxs-lookup"><span data-stu-id="80924-177">Data type</span></span>|<span data-ttu-id="80924-178">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="80924-179">Liczba</span><span class="sxs-lookup"><span data-stu-id="80924-179">Count</span></span>|<span data-ttu-id="80924-180">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-180">win:UInt32</span></span>|<span data-ttu-id="80924-181">*n*th wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="80924-182">Głębokość</span><span class="sxs-lookup"><span data-stu-id="80924-182">Depth</span></span>|<span data-ttu-id="80924-183">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-183">win:UInt32</span></span>|<span data-ttu-id="80924-184">Generowanie, który został zebrany.</span><span class="sxs-lookup"><span data-stu-id="80924-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="80924-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="80924-185">ClrInstanceID</span></span>|<span data-ttu-id="80924-186">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-186">win:UInt16</span></span>|<span data-ttu-id="80924-187">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="80924-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="80924-188">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="80924-189">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="80924-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="80924-190">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-191">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-191">Keyword for raising the event</span></span>|<span data-ttu-id="80924-192">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-194">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-195">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-196">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-196">Event</span></span>|<span data-ttu-id="80924-197">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-197">Event ID</span></span>|<span data-ttu-id="80924-198">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="80924-199">4</span><span class="sxs-lookup"><span data-stu-id="80924-199">4</span></span>|<span data-ttu-id="80924-200">Wyświetla statystyki sterty na końcu każdej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="80924-201">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="80924-202">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="80924-202">Field name</span></span>|<span data-ttu-id="80924-203">Typ danych</span><span class="sxs-lookup"><span data-stu-id="80924-203">Data type</span></span>|<span data-ttu-id="80924-204">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="80924-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="80924-205">GenerationSize0</span></span>|<span data-ttu-id="80924-206">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-206">win:UInt64</span></span>|<span data-ttu-id="80924-207">Rozmiar w bajtach pamięć generacji 0.</span><span class="sxs-lookup"><span data-stu-id="80924-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="80924-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="80924-208">TotalPromotedSize0</span></span>|<span data-ttu-id="80924-209">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-209">win:UInt64</span></span>|<span data-ttu-id="80924-210">Liczba bajtów, które zostały awansowane z pokolenia 0 na pokolenie 1.</span><span class="sxs-lookup"><span data-stu-id="80924-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="80924-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="80924-211">GenerationSize1</span></span>|<span data-ttu-id="80924-212">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-212">win:UInt64</span></span>|<span data-ttu-id="80924-213">Rozmiar w bajtach pamięci generacji 1.</span><span class="sxs-lookup"><span data-stu-id="80924-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="80924-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="80924-214">TotalPromotedSize1</span></span>|<span data-ttu-id="80924-215">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-215">win:UInt64</span></span>|<span data-ttu-id="80924-216">Liczba bajtów, które zostały awansowane z pokolenia 1 na pokolenie 2.</span><span class="sxs-lookup"><span data-stu-id="80924-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="80924-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="80924-217">GenerationSize2</span></span>|<span data-ttu-id="80924-218">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-218">win:UInt64</span></span>|<span data-ttu-id="80924-219">Rozmiar w bajtach pamięci generacji 2.</span><span class="sxs-lookup"><span data-stu-id="80924-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="80924-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="80924-220">TotalPromotedSize2</span></span>|<span data-ttu-id="80924-221">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-221">win:UInt64</span></span>|<span data-ttu-id="80924-222">Liczba bajtów, które udało przetrwać podczas generowania 2 od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="80924-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="80924-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="80924-223">GenerationSize3</span></span>|<span data-ttu-id="80924-224">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-224">win:UInt64</span></span>|<span data-ttu-id="80924-225">Rozmiar w bajtach sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="80924-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="80924-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="80924-226">TotalPromotedSize3</span></span>|<span data-ttu-id="80924-227">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-227">win:UInt64</span></span>|<span data-ttu-id="80924-228">Liczba bajtów, które udało przetrwać w sterty dużego obiektu, od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="80924-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="80924-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="80924-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="80924-230">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-230">win:UInt64</span></span>|<span data-ttu-id="80924-231">Całkowity rozmiar w bajtach obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="80924-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="80924-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="80924-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="80924-233">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-233">win:UInt64</span></span>|<span data-ttu-id="80924-234">Liczba obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="80924-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="80924-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="80924-235">PinnedObjectCount</span></span>|<span data-ttu-id="80924-236">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-236">win:UInt32</span></span>|<span data-ttu-id="80924-237">Liczbę unieruchomionych obiektów (nieprzenośne).</span><span class="sxs-lookup"><span data-stu-id="80924-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="80924-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="80924-238">SinkBlockCount</span></span>|<span data-ttu-id="80924-239">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-239">win:UInt32</span></span>|<span data-ttu-id="80924-240">Liczba bloków synchronizacji w użyciu.</span><span class="sxs-lookup"><span data-stu-id="80924-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="80924-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="80924-241">GCHandleCount</span></span>|<span data-ttu-id="80924-242">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-242">win:UInt32</span></span>|<span data-ttu-id="80924-243">Obsługuje liczbę operacji wyrzucania elementów bezużytecznych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="80924-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="80924-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="80924-244">ClrInstanceID</span></span>|<span data-ttu-id="80924-245">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-245">win:UInt16</span></span>|<span data-ttu-id="80924-246">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="80924-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="80924-247">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="80924-248">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="80924-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="80924-249">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-250">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-250">Keyword for raising the event</span></span>|<span data-ttu-id="80924-251">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-253">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-254">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-255">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-255">Event</span></span>|<span data-ttu-id="80924-256">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-256">Event ID</span></span>|<span data-ttu-id="80924-257">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="80924-258">5</span><span class="sxs-lookup"><span data-stu-id="80924-258">5</span></span>|<span data-ttu-id="80924-259">Utworzono nowy segment kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="80924-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="80924-260">Ponadto gdy śledzenie jest włączone dla procesu, który jest już uruchomiona, to zdarzenie jest wywoływane dla każdego istniejącego segmentu.</span><span class="sxs-lookup"><span data-stu-id="80924-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="80924-261">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="80924-262">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="80924-262">Field name</span></span>|<span data-ttu-id="80924-263">Typ danych</span><span class="sxs-lookup"><span data-stu-id="80924-263">Data type</span></span>|<span data-ttu-id="80924-264">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="80924-265">Adres</span><span class="sxs-lookup"><span data-stu-id="80924-265">Address</span></span>|<span data-ttu-id="80924-266">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-266">win:UInt64</span></span>|<span data-ttu-id="80924-267">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="80924-267">The address of the segment.</span></span>|  
|<span data-ttu-id="80924-268">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="80924-268">Size</span></span>|<span data-ttu-id="80924-269">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-269">win:UInt64</span></span>|<span data-ttu-id="80924-270">Rozmiar segmentu.</span><span class="sxs-lookup"><span data-stu-id="80924-270">The size of the segment.</span></span>|  
|<span data-ttu-id="80924-271">Typ</span><span class="sxs-lookup"><span data-stu-id="80924-271">Type</span></span>|<span data-ttu-id="80924-272">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-272">win:UInt32</span></span>|<span data-ttu-id="80924-273">0x0 - sterty małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="80924-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="80924-274">0x1 — sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="80924-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="80924-275">0x2 — sterty tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="80924-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="80924-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="80924-276">ClrInstanceID</span></span>|<span data-ttu-id="80924-277">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-277">win:UInt16</span></span>|<span data-ttu-id="80924-278">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="80924-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="80924-279">Należy zauważyć, że rozmiar segmentów przydzielone przez moduł garbage collector konkretnej implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="80924-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="80924-280">Aplikacji nigdy nie może dokonać założeń dotyczących lub zależą od rozmiaru określonego segmentu nie powinny podejmować próby skonfiguruj ilość pamięci dostępnej dla segmentu alokacji.</span><span class="sxs-lookup"><span data-stu-id="80924-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="80924-281">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="80924-282">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="80924-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="80924-283">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-284">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-284">Keyword for raising the event</span></span>|<span data-ttu-id="80924-285">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-287">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-288">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-289">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-289">Event</span></span>|<span data-ttu-id="80924-290">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-290">Event ID</span></span>|<span data-ttu-id="80924-291">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="80924-292">6</span><span class="sxs-lookup"><span data-stu-id="80924-292">6</span></span>|<span data-ttu-id="80924-293">Segment kolekcji odzyskiwanie zostało zwolnione.</span><span class="sxs-lookup"><span data-stu-id="80924-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="80924-294">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="80924-295">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="80924-295">Field name</span></span>|<span data-ttu-id="80924-296">Typ danych</span><span class="sxs-lookup"><span data-stu-id="80924-296">Data type</span></span>|<span data-ttu-id="80924-297">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="80924-298">Adres</span><span class="sxs-lookup"><span data-stu-id="80924-298">Address</span></span>|<span data-ttu-id="80924-299">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-299">win:UInt64</span></span>|<span data-ttu-id="80924-300">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="80924-300">The address of the segment.</span></span>|  
|<span data-ttu-id="80924-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="80924-301">ClrInstanceID</span></span>|<span data-ttu-id="80924-302">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-302">win:UInt16</span></span>|<span data-ttu-id="80924-303">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="80924-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="80924-304">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="80924-305">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="80924-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="80924-306">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-307">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-307">Keyword for raising the event</span></span>|<span data-ttu-id="80924-308">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-310">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-311">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-312">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-312">Event</span></span>|<span data-ttu-id="80924-313">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-313">Event ID</span></span>|<span data-ttu-id="80924-314">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="80924-315">7</span><span class="sxs-lookup"><span data-stu-id="80924-315">7</span></span>|<span data-ttu-id="80924-316">Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="80924-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="80924-317">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-317">No event data.</span></span>  
  
 [<span data-ttu-id="80924-318">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="80924-319">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="80924-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="80924-320">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-321">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-321">Keyword for raising the event</span></span>|<span data-ttu-id="80924-322">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-324">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-325">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-326">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-326">Event</span></span>|<span data-ttu-id="80924-327">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-327">Event Id</span></span>|<span data-ttu-id="80924-328">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="80924-329">3</span><span class="sxs-lookup"><span data-stu-id="80924-329">3</span></span>|<span data-ttu-id="80924-330">Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została zakończona.</span><span class="sxs-lookup"><span data-stu-id="80924-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="80924-331">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-331">No event data.</span></span>  
  
 [<span data-ttu-id="80924-332">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="80924-333">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="80924-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="80924-334">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-335">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-335">Keyword for raising the event</span></span>|<span data-ttu-id="80924-336">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-338">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-339">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-340">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-340">Event</span></span>|<span data-ttu-id="80924-341">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-341">Event ID</span></span>|<span data-ttu-id="80924-342">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="80924-343">9</span><span class="sxs-lookup"><span data-stu-id="80924-343">9</span></span>|<span data-ttu-id="80924-344">Początek zawieszenia aparat wykonywania dla wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="80924-345">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="80924-346">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="80924-346">Field name</span></span>|<span data-ttu-id="80924-347">Typ danych</span><span class="sxs-lookup"><span data-stu-id="80924-347">Data type</span></span>|<span data-ttu-id="80924-348">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="80924-349">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="80924-349">Reason</span></span>|<span data-ttu-id="80924-350">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-350">win:UInt16</span></span>|<span data-ttu-id="80924-351">0x0 - innych.</span><span class="sxs-lookup"><span data-stu-id="80924-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="80924-352">0x1 — wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="80924-353">0x2 — zamknięcia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80924-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="80924-354">0x3 - pitching kodu.</span><span class="sxs-lookup"><span data-stu-id="80924-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="80924-355">0x4 - shutdown.</span><span class="sxs-lookup"><span data-stu-id="80924-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="80924-356">0x5 - debugera.</span><span class="sxs-lookup"><span data-stu-id="80924-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="80924-357">0x6 — przygotowanie do wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="80924-358">Liczba</span><span class="sxs-lookup"><span data-stu-id="80924-358">Count</span></span>|<span data-ttu-id="80924-359">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-359">win:UInt32</span></span>|<span data-ttu-id="80924-360">Liczba GC, w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="80924-360">The GC count at the time.</span></span> <span data-ttu-id="80924-361">Zwykle zobaczysz kolejnych zdarzeń GC Start po to, a licznika wyjątkowo licznik ten uwzględnia + 1, ponieważ indeks GC możemy zwiększyć podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="80924-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="80924-362">ClrInstanceID</span></span>|<span data-ttu-id="80924-363">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-363">win:UInt16</span></span>|<span data-ttu-id="80924-364">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="80924-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="80924-365">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="80924-366">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="80924-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="80924-367">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu:</span><span class="sxs-lookup"><span data-stu-id="80924-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="80924-368">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-368">Keyword for raising the event</span></span>|<span data-ttu-id="80924-369">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-371">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-372">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="80924-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="80924-373">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-373">Event</span></span>|<span data-ttu-id="80924-374">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-374">Event ID</span></span>|<span data-ttu-id="80924-375">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="80924-376">8</span><span class="sxs-lookup"><span data-stu-id="80924-376">8</span></span>|<span data-ttu-id="80924-377">Koniec zawieszenia aparat wykonywania dla wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="80924-378">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-378">No event data.</span></span>  
  
 [<span data-ttu-id="80924-379">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="80924-380">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="80924-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="80924-381">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-382">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-382">Keyword for raising the event</span></span>|<span data-ttu-id="80924-383">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-385">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-386">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-387">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-387">Event</span></span>|<span data-ttu-id="80924-388">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-388">Event ID</span></span>|<span data-ttu-id="80924-389">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="80924-390">10</span><span class="sxs-lookup"><span data-stu-id="80924-390">10</span></span>|<span data-ttu-id="80924-391">Zawsze przydzielone około 100 KB.</span><span class="sxs-lookup"><span data-stu-id="80924-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="80924-392">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="80924-393">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="80924-393">Field name</span></span>|<span data-ttu-id="80924-394">Typ danych</span><span class="sxs-lookup"><span data-stu-id="80924-394">Data type</span></span>|<span data-ttu-id="80924-395">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="80924-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="80924-396">AllocationAmount</span></span>|<span data-ttu-id="80924-397">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-397">win:UInt32</span></span>|<span data-ttu-id="80924-398">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="80924-398">The allocation size, in bytes.</span></span> <span data-ttu-id="80924-399">Ta wartość jest dokładna dla alokacji, który jest mniejsza niż długość ULONG (4 294 967 295 w bajtach).</span><span class="sxs-lookup"><span data-stu-id="80924-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="80924-400">Jeśli przydział jest większa, to pole zawiera obciętą wartość.</span><span class="sxs-lookup"><span data-stu-id="80924-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="80924-401">Użyj `AllocationAmount64` dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="80924-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="80924-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="80924-402">AllocationKind</span></span>|<span data-ttu-id="80924-403">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-403">win:UInt32</span></span>|<span data-ttu-id="80924-404">0x0 - małego obiektu alokacji (alokacji jest sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="80924-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="80924-405">0x1 — alokacji dużego obiektu (alokacji jest sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="80924-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="80924-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="80924-406">ClrInstanceID</span></span>|<span data-ttu-id="80924-407">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-407">win:UInt16</span></span>|<span data-ttu-id="80924-408">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="80924-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="80924-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="80924-409">AllocationAmount64</span></span>|<span data-ttu-id="80924-410">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="80924-410">win:UInt64</span></span>|<span data-ttu-id="80924-411">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="80924-411">The allocation size, in bytes.</span></span> <span data-ttu-id="80924-412">Ta wartość jest dokładne w przypadku bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="80924-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="80924-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="80924-413">TypeId</span></span>|<span data-ttu-id="80924-414">Windows: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="80924-414">win:Pointer</span></span>|<span data-ttu-id="80924-415">Adres MethodTable.</span><span class="sxs-lookup"><span data-stu-id="80924-415">The address of the MethodTable.</span></span> <span data-ttu-id="80924-416">Jeśli istnieje kilka typów obiektów, które zostały przydzielone podczas tego zdarzenia, jest to adres MethodTable, odpowiadający ostatni obiekt przydzielony (obiekt, który spowodował może przekroczyć próg 100 KB).</span><span class="sxs-lookup"><span data-stu-id="80924-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="80924-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="80924-417">TypeName</span></span>|<span data-ttu-id="80924-418">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="80924-418">win:UnicodeString</span></span>|<span data-ttu-id="80924-419">Nazwa typu, który został przydzielony.</span><span class="sxs-lookup"><span data-stu-id="80924-419">The name of the type that was allocated.</span></span> <span data-ttu-id="80924-420">Jeśli istnieje kilka typów obiektów, które zostały przydzielone podczas tego zdarzenia, jest to typ ostatni obiekt przydzielony (obiekt, który spowodował może przekroczyć próg 100 KB).</span><span class="sxs-lookup"><span data-stu-id="80924-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="80924-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="80924-421">HeapIndex</span></span>|<span data-ttu-id="80924-422">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-422">win:UInt32</span></span>|<span data-ttu-id="80924-423">Stosu, w którym obiekt został przydzielony.</span><span class="sxs-lookup"><span data-stu-id="80924-423">The heap where the object was allocated.</span></span> <span data-ttu-id="80924-424">Ta wartość jest 0 (zero), gdy uruchomiona stacji roboczej wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="80924-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="80924-425">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="80924-426">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="80924-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="80924-427">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-428">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-428">Keyword for raising the event</span></span>|<span data-ttu-id="80924-429">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-431">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-432">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-433">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-433">Event</span></span>|<span data-ttu-id="80924-434">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-434">Event ID</span></span>|<span data-ttu-id="80924-435">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="80924-436">14</span><span class="sxs-lookup"><span data-stu-id="80924-436">14</span></span>|<span data-ttu-id="80924-437">Początek systemem finalizatory.</span><span class="sxs-lookup"><span data-stu-id="80924-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="80924-438">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-438">No event data.</span></span>  
  
 [<span data-ttu-id="80924-439">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="80924-440">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="80924-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="80924-441">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-442">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-442">Keyword for raising the event</span></span>|<span data-ttu-id="80924-443">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-445">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-446">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-447">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-447">Event</span></span>|<span data-ttu-id="80924-448">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-448">Event ID</span></span>|<span data-ttu-id="80924-449">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="80924-450">13</span><span class="sxs-lookup"><span data-stu-id="80924-450">13</span></span>|<span data-ttu-id="80924-451">Koniec systemem finalizatory.</span><span class="sxs-lookup"><span data-stu-id="80924-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="80924-452">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="80924-453">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="80924-453">Field name</span></span>|<span data-ttu-id="80924-454">Typ danych</span><span class="sxs-lookup"><span data-stu-id="80924-454">Data type</span></span>|<span data-ttu-id="80924-455">Opis</span><span class="sxs-lookup"><span data-stu-id="80924-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="80924-456">Liczba</span><span class="sxs-lookup"><span data-stu-id="80924-456">Count</span></span>|<span data-ttu-id="80924-457">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="80924-457">win:UInt32</span></span>|<span data-ttu-id="80924-458">Liczba finalizatory, które zostały uruchomione.</span><span class="sxs-lookup"><span data-stu-id="80924-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="80924-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="80924-459">ClrInstanceID</span></span>|<span data-ttu-id="80924-460">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="80924-460">win:UInt16</span></span>|<span data-ttu-id="80924-461">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="80924-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="80924-462">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="80924-463">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="80924-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="80924-464">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-465">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-465">Keyword for raising the event</span></span>|<span data-ttu-id="80924-466">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-468">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-468">Informational (4)</span></span>|  
|<span data-ttu-id="80924-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="80924-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="80924-470">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-471">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-472">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-472">Event</span></span>|<span data-ttu-id="80924-473">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-473">Event ID</span></span>|<span data-ttu-id="80924-474">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="80924-475">11</span><span class="sxs-lookup"><span data-stu-id="80924-475">11</span></span>|<span data-ttu-id="80924-476">Współbieżne odzyskiwanie kolekcji wątek został utworzony.</span><span class="sxs-lookup"><span data-stu-id="80924-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="80924-477">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-477">No event data.</span></span>  
  
 [<span data-ttu-id="80924-478">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="80924-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="80924-479">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="80924-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="80924-480">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="80924-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="80924-481">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-481">Keyword for raising the event</span></span>|<span data-ttu-id="80924-482">Poziom</span><span class="sxs-lookup"><span data-stu-id="80924-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="80924-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="80924-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="80924-484">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-484">Informational (4)</span></span>|  
|<span data-ttu-id="80924-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="80924-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="80924-486">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="80924-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="80924-487">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="80924-488">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="80924-488">Event</span></span>|<span data-ttu-id="80924-489">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80924-489">Event ID</span></span>|<span data-ttu-id="80924-490">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="80924-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="80924-491">12</span><span class="sxs-lookup"><span data-stu-id="80924-491">12</span></span>|<span data-ttu-id="80924-492">Współbieżne odzyskiwanie kolekcji wątek został przerwany.</span><span class="sxs-lookup"><span data-stu-id="80924-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="80924-493">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80924-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80924-494">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80924-494">See Also</span></span>  
 [<span data-ttu-id="80924-495">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="80924-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
