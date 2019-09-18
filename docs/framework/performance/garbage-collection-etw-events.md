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
ms.openlocfilehash: ec90d022a0c72782f413a84b6fbd2c1b8d663a73
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046496"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="795fd-102">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="795fd-102">Garbage Collection ETW Events</span></span>
<a name="top"></a><span data-ttu-id="795fd-103">Te zdarzenia zbierają informacje dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="795fd-104">Ułatwiają one diagnostykę i debugowanie, w tym określanie, ile razy zostało wykonane wyrzucanie elementów bezużytecznych, ilości pamięci, która została zwolniona podczas odzyskiwania pamięci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="795fd-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="795fd-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="795fd-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="795fd-106">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
- [<span data-ttu-id="795fd-107">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
- [<span data-ttu-id="795fd-108">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
- [<span data-ttu-id="795fd-109">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
- [<span data-ttu-id="795fd-110">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
- [<span data-ttu-id="795fd-111">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
- [<span data-ttu-id="795fd-112">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
- [<span data-ttu-id="795fd-113">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
- [<span data-ttu-id="795fd-114">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
- [<span data-ttu-id="795fd-115">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="795fd-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
- [<span data-ttu-id="795fd-116">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
- [<span data-ttu-id="795fd-117">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
- [<span data-ttu-id="795fd-118">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
- [<span data-ttu-id="795fd-119">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstart_v1-event"></a><span data-ttu-id="795fd-120">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="795fd-121">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="795fd-122">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="795fd-122">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="795fd-123">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-123">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-124">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-125">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-126">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-127">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-128">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-128">Event</span></span>|<span data-ttu-id="795fd-129">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-129">Event ID</span></span>|<span data-ttu-id="795fd-130">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="795fd-131">1</span><span class="sxs-lookup"><span data-stu-id="795fd-131">1</span></span>|<span data-ttu-id="795fd-132">Rozpoczęto odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="795fd-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="795fd-133">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="795fd-134">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="795fd-134">Field name</span></span>|<span data-ttu-id="795fd-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="795fd-135">Data type</span></span>|<span data-ttu-id="795fd-136">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="795fd-137">Count</span><span class="sxs-lookup"><span data-stu-id="795fd-137">Count</span></span>|<span data-ttu-id="795fd-138">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-138">win:UInt32</span></span>|<span data-ttu-id="795fd-139">*N*-ta kolekcja elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="795fd-140">Ścisł</span><span class="sxs-lookup"><span data-stu-id="795fd-140">Depth</span></span>|<span data-ttu-id="795fd-141">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-141">win:UInt32</span></span>|<span data-ttu-id="795fd-142">Generacja, która jest zbierana.</span><span class="sxs-lookup"><span data-stu-id="795fd-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="795fd-143">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="795fd-143">Reason</span></span>|<span data-ttu-id="795fd-144">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-144">win:UInt32</span></span>|<span data-ttu-id="795fd-145">Dlaczego wyzwolono wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="795fd-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="795fd-146">0x0 — alokacja sterty dla małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="795fd-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="795fd-147">Wywołano 0x1.</span><span class="sxs-lookup"><span data-stu-id="795fd-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="795fd-148">0x2 — mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="795fd-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="795fd-149">0x3 — puste.</span><span class="sxs-lookup"><span data-stu-id="795fd-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="795fd-150">0x4 — alokacja sterty dla dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="795fd-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="795fd-151">0x5 — brak miejsca (dla sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="795fd-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="795fd-152">0x6 — brak miejsca (dla sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="795fd-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="795fd-153">0x7 — wywołano, ale nie wymuszono blokowania.</span><span class="sxs-lookup"><span data-stu-id="795fd-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="795fd-154">Typ</span><span class="sxs-lookup"><span data-stu-id="795fd-154">Type</span></span>|<span data-ttu-id="795fd-155">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-155">win:UInt32</span></span>|<span data-ttu-id="795fd-156">0x0 — blokowanie odzyskiwania pamięci wystąpiło poza odzyskiwaniem pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="795fd-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="795fd-157">0x1 — wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="795fd-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="795fd-158">0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpiło podczas odzyskiwania pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="795fd-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="795fd-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="795fd-159">ClrInstanceID</span></span>|<span data-ttu-id="795fd-160">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-160">win:UInt16</span></span>|<span data-ttu-id="795fd-161">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="795fd-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="795fd-162">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcend_v1-event"></a><span data-ttu-id="795fd-163">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="795fd-164">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-165">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-165">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-166">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-167">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-168">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-169">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-170">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-170">Event</span></span>|<span data-ttu-id="795fd-171">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-171">Event ID</span></span>|<span data-ttu-id="795fd-172">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="795fd-173">2</span><span class="sxs-lookup"><span data-stu-id="795fd-173">2</span></span>|<span data-ttu-id="795fd-174">Wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="795fd-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="795fd-175">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="795fd-176">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="795fd-176">Field name</span></span>|<span data-ttu-id="795fd-177">Typ danych</span><span class="sxs-lookup"><span data-stu-id="795fd-177">Data type</span></span>|<span data-ttu-id="795fd-178">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="795fd-179">Count</span><span class="sxs-lookup"><span data-stu-id="795fd-179">Count</span></span>|<span data-ttu-id="795fd-180">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-180">win:UInt32</span></span>|<span data-ttu-id="795fd-181">*N*-ta kolekcja elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="795fd-182">Ścisł</span><span class="sxs-lookup"><span data-stu-id="795fd-182">Depth</span></span>|<span data-ttu-id="795fd-183">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-183">win:UInt32</span></span>|<span data-ttu-id="795fd-184">Generacja, która została zebrana.</span><span class="sxs-lookup"><span data-stu-id="795fd-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="795fd-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="795fd-185">ClrInstanceID</span></span>|<span data-ttu-id="795fd-186">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-186">win:UInt16</span></span>|<span data-ttu-id="795fd-187">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="795fd-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="795fd-188">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstats_v1-event"></a><span data-ttu-id="795fd-189">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="795fd-190">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-191">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-191">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-192">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-193">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-194">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-195">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-196">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-196">Event</span></span>|<span data-ttu-id="795fd-197">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-197">Event ID</span></span>|<span data-ttu-id="795fd-198">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="795fd-199">4</span><span class="sxs-lookup"><span data-stu-id="795fd-199">4</span></span>|<span data-ttu-id="795fd-200">Pokazuje statystyki sterty na końcu każdego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="795fd-201">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="795fd-202">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="795fd-202">Field name</span></span>|<span data-ttu-id="795fd-203">Typ danych</span><span class="sxs-lookup"><span data-stu-id="795fd-203">Data type</span></span>|<span data-ttu-id="795fd-204">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="795fd-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="795fd-205">GenerationSize0</span></span>|<span data-ttu-id="795fd-206">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-206">win:UInt64</span></span>|<span data-ttu-id="795fd-207">Rozmiar (w bajtach) pamięci generacji 0.</span><span class="sxs-lookup"><span data-stu-id="795fd-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="795fd-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="795fd-208">TotalPromotedSize0</span></span>|<span data-ttu-id="795fd-209">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-209">win:UInt64</span></span>|<span data-ttu-id="795fd-210">Liczba bajtów, które są podwyższane z generacji 0 do generacji 1.</span><span class="sxs-lookup"><span data-stu-id="795fd-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="795fd-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="795fd-211">GenerationSize1</span></span>|<span data-ttu-id="795fd-212">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-212">win:UInt64</span></span>|<span data-ttu-id="795fd-213">Rozmiar (w bajtach) pamięci pierwszej generacji 1.</span><span class="sxs-lookup"><span data-stu-id="795fd-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="795fd-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="795fd-214">TotalPromotedSize1</span></span>|<span data-ttu-id="795fd-215">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-215">win:UInt64</span></span>|<span data-ttu-id="795fd-216">Liczba bajtów, które są podwyższane z generacji 1 do generacji 2.</span><span class="sxs-lookup"><span data-stu-id="795fd-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="795fd-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="795fd-217">GenerationSize2</span></span>|<span data-ttu-id="795fd-218">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-218">win:UInt64</span></span>|<span data-ttu-id="795fd-219">Rozmiar (w bajtach) pamięci podnoszącej 2 generacji.</span><span class="sxs-lookup"><span data-stu-id="795fd-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="795fd-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="795fd-220">TotalPromotedSize2</span></span>|<span data-ttu-id="795fd-221">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-221">win:UInt64</span></span>|<span data-ttu-id="795fd-222">Liczba bajtów, które przeżyły w generacji 2 po ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="795fd-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="795fd-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="795fd-223">GenerationSize3</span></span>|<span data-ttu-id="795fd-224">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-224">win:UInt64</span></span>|<span data-ttu-id="795fd-225">Rozmiar sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="795fd-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="795fd-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="795fd-226">TotalPromotedSize3</span></span>|<span data-ttu-id="795fd-227">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-227">win:UInt64</span></span>|<span data-ttu-id="795fd-228">Liczba bajtów przeczytanych z sterty dużego obiektu po ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="795fd-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="795fd-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="795fd-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="795fd-230">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-230">win:UInt64</span></span>|<span data-ttu-id="795fd-231">Łączny rozmiar (w bajtach) obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="795fd-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="795fd-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="795fd-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="795fd-233">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-233">win:UInt64</span></span>|<span data-ttu-id="795fd-234">Liczba obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="795fd-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="795fd-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="795fd-235">PinnedObjectCount</span></span>|<span data-ttu-id="795fd-236">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-236">win:UInt32</span></span>|<span data-ttu-id="795fd-237">Liczba przypiętych (nieruchomych) obiektów.</span><span class="sxs-lookup"><span data-stu-id="795fd-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="795fd-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="795fd-238">SinkBlockCount</span></span>|<span data-ttu-id="795fd-239">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-239">win:UInt32</span></span>|<span data-ttu-id="795fd-240">Liczba bloków synchronizacji w użyciu.</span><span class="sxs-lookup"><span data-stu-id="795fd-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="795fd-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="795fd-241">GCHandleCount</span></span>|<span data-ttu-id="795fd-242">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-242">win:UInt32</span></span>|<span data-ttu-id="795fd-243">Liczba dojść do wyrzucania elementów bezużytecznych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="795fd-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="795fd-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="795fd-244">ClrInstanceID</span></span>|<span data-ttu-id="795fd-245">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-245">win:UInt16</span></span>|<span data-ttu-id="795fd-246">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="795fd-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="795fd-247">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="795fd-248">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="795fd-249">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-250">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-250">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-251">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-252">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-253">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-254">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-255">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-255">Event</span></span>|<span data-ttu-id="795fd-256">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-256">Event ID</span></span>|<span data-ttu-id="795fd-257">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="795fd-258">5</span><span class="sxs-lookup"><span data-stu-id="795fd-258">5</span></span>|<span data-ttu-id="795fd-259">Utworzono nowy segment wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="795fd-260">Ponadto po włączeniu śledzenia dla procesu, który jest już uruchomiony, to zdarzenie jest zgłaszane dla każdego istniejącego segmentu.</span><span class="sxs-lookup"><span data-stu-id="795fd-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="795fd-261">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="795fd-262">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="795fd-262">Field name</span></span>|<span data-ttu-id="795fd-263">Typ danych</span><span class="sxs-lookup"><span data-stu-id="795fd-263">Data type</span></span>|<span data-ttu-id="795fd-264">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="795fd-265">Adres</span><span class="sxs-lookup"><span data-stu-id="795fd-265">Address</span></span>|<span data-ttu-id="795fd-266">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-266">win:UInt64</span></span>|<span data-ttu-id="795fd-267">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="795fd-267">The address of the segment.</span></span>|  
|<span data-ttu-id="795fd-268">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="795fd-268">Size</span></span>|<span data-ttu-id="795fd-269">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-269">win:UInt64</span></span>|<span data-ttu-id="795fd-270">Rozmiar segmentu.</span><span class="sxs-lookup"><span data-stu-id="795fd-270">The size of the segment.</span></span>|  
|<span data-ttu-id="795fd-271">Typ</span><span class="sxs-lookup"><span data-stu-id="795fd-271">Type</span></span>|<span data-ttu-id="795fd-272">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-272">win:UInt32</span></span>|<span data-ttu-id="795fd-273">0x0 — sterta małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="795fd-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="795fd-274">0x1 — sterta dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="795fd-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="795fd-275">0x2 — sterta tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="795fd-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="795fd-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="795fd-276">ClrInstanceID</span></span>|<span data-ttu-id="795fd-277">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-277">win:UInt16</span></span>|<span data-ttu-id="795fd-278">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="795fd-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="795fd-279">Należy zauważyć, że rozmiar segmentów przydzielone przez moduł wyrzucania elementów bezużytecznych jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami.</span><span class="sxs-lookup"><span data-stu-id="795fd-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="795fd-280">Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="795fd-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="795fd-281">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="795fd-282">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="795fd-283">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-284">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-284">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-285">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-286">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-287">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-288">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-289">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-289">Event</span></span>|<span data-ttu-id="795fd-290">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-290">Event ID</span></span>|<span data-ttu-id="795fd-291">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="795fd-292">6</span><span class="sxs-lookup"><span data-stu-id="795fd-292">6</span></span>|<span data-ttu-id="795fd-293">Wydano segment wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="795fd-294">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="795fd-295">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="795fd-295">Field name</span></span>|<span data-ttu-id="795fd-296">Typ danych</span><span class="sxs-lookup"><span data-stu-id="795fd-296">Data type</span></span>|<span data-ttu-id="795fd-297">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="795fd-298">Adres</span><span class="sxs-lookup"><span data-stu-id="795fd-298">Address</span></span>|<span data-ttu-id="795fd-299">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-299">win:UInt64</span></span>|<span data-ttu-id="795fd-300">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="795fd-300">The address of the segment.</span></span>|  
|<span data-ttu-id="795fd-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="795fd-301">ClrInstanceID</span></span>|<span data-ttu-id="795fd-302">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-302">win:UInt16</span></span>|<span data-ttu-id="795fd-303">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="795fd-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="795fd-304">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="795fd-305">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="795fd-306">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-307">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-307">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-308">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-309">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-310">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-311">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-312">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-312">Event</span></span>|<span data-ttu-id="795fd-313">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-313">Event ID</span></span>|<span data-ttu-id="795fd-314">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="795fd-315">7</span><span class="sxs-lookup"><span data-stu-id="795fd-315">7</span></span>|<span data-ttu-id="795fd-316">Rozpoczęto wznawianie od zawieszenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="795fd-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="795fd-317">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-317">No event data.</span></span>  
  
 [<span data-ttu-id="795fd-318">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="795fd-319">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="795fd-320">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-321">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-321">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-322">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-323">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-324">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-325">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-326">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-326">Event</span></span>|<span data-ttu-id="795fd-327">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-327">Event Id</span></span>|<span data-ttu-id="795fd-328">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="795fd-329">3</span><span class="sxs-lookup"><span data-stu-id="795fd-329">3</span></span>|<span data-ttu-id="795fd-330">Zakończono wznawianie z zawieszenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="795fd-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="795fd-331">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-331">No event data.</span></span>  
  
 [<span data-ttu-id="795fd-332">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="795fd-333">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="795fd-334">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-335">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-335">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-336">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-337">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-338">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-339">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-340">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-340">Event</span></span>|<span data-ttu-id="795fd-341">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-341">Event ID</span></span>|<span data-ttu-id="795fd-342">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="795fd-343">9</span><span class="sxs-lookup"><span data-stu-id="795fd-343">9</span></span>|<span data-ttu-id="795fd-344">Początek zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="795fd-345">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="795fd-346">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="795fd-346">Field name</span></span>|<span data-ttu-id="795fd-347">Typ danych</span><span class="sxs-lookup"><span data-stu-id="795fd-347">Data type</span></span>|<span data-ttu-id="795fd-348">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="795fd-349">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="795fd-349">Reason</span></span>|<span data-ttu-id="795fd-350">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-350">win:UInt16</span></span>|<span data-ttu-id="795fd-351">0x0 — inne.</span><span class="sxs-lookup"><span data-stu-id="795fd-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="795fd-352">0x1 — odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="795fd-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="795fd-353">0x2 — zamknięcie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="795fd-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="795fd-354">0x3 — nachylenie kodu.</span><span class="sxs-lookup"><span data-stu-id="795fd-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="795fd-355">0x4 — zamykanie.</span><span class="sxs-lookup"><span data-stu-id="795fd-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="795fd-356">0x5 — debuger.</span><span class="sxs-lookup"><span data-stu-id="795fd-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="795fd-357">0x6 — przygotowanie do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="795fd-358">Count</span><span class="sxs-lookup"><span data-stu-id="795fd-358">Count</span></span>|<span data-ttu-id="795fd-359">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-359">win:UInt32</span></span>|<span data-ttu-id="795fd-360">Liczba GC w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="795fd-360">The GC count at the time.</span></span> <span data-ttu-id="795fd-361">Zwykle po wykonaniu tej operacji zobaczysz kolejne zdarzenie uruchomienia GC, a jego liczba jest taka sama jak liczba + 1, ponieważ zwiększy indeks GC podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="795fd-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="795fd-362">ClrInstanceID</span></span>|<span data-ttu-id="795fd-363">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-363">win:UInt16</span></span>|<span data-ttu-id="795fd-364">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="795fd-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="795fd-365">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="795fd-366">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="795fd-367">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="795fd-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="795fd-368">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-368">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-369">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-370">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-371">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-372">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="795fd-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="795fd-373">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-373">Event</span></span>|<span data-ttu-id="795fd-374">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-374">Event ID</span></span>|<span data-ttu-id="795fd-375">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="795fd-376">8</span><span class="sxs-lookup"><span data-stu-id="795fd-376">8</span></span>|<span data-ttu-id="795fd-377">Koniec zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="795fd-378">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-378">No event data.</span></span>  
  
 [<span data-ttu-id="795fd-379">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="795fd-380">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="795fd-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="795fd-381">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-382">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-382">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-383">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-384">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-385">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-386">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-387">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-387">Event</span></span>|<span data-ttu-id="795fd-388">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-388">Event ID</span></span>|<span data-ttu-id="795fd-389">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="795fd-390">10</span><span class="sxs-lookup"><span data-stu-id="795fd-390">10</span></span>|<span data-ttu-id="795fd-391">Za każdym razem przydzielono około 100 KB.</span><span class="sxs-lookup"><span data-stu-id="795fd-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="795fd-392">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="795fd-393">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="795fd-393">Field name</span></span>|<span data-ttu-id="795fd-394">Typ danych</span><span class="sxs-lookup"><span data-stu-id="795fd-394">Data type</span></span>|<span data-ttu-id="795fd-395">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="795fd-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="795fd-396">AllocationAmount</span></span>|<span data-ttu-id="795fd-397">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-397">win:UInt32</span></span>|<span data-ttu-id="795fd-398">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="795fd-398">The allocation size, in bytes.</span></span> <span data-ttu-id="795fd-399">Ta wartość jest dokładna dla przydziałów, które są mniejsze niż długość ULONG (4 294 967 295 bajtów).</span><span class="sxs-lookup"><span data-stu-id="795fd-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="795fd-400">Jeśli alokacja jest większa, to pole zawiera obciętą wartość.</span><span class="sxs-lookup"><span data-stu-id="795fd-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="795fd-401">Używane `AllocationAmount64` dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="795fd-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="795fd-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="795fd-402">AllocationKind</span></span>|<span data-ttu-id="795fd-403">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-403">win:UInt32</span></span>|<span data-ttu-id="795fd-404">0x0 — alokacja małego obiektu (alokacja jest w ramach sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="795fd-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="795fd-405">0x1 — alokacja dużego obiektu (alokacja jest w sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="795fd-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="795fd-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="795fd-406">ClrInstanceID</span></span>|<span data-ttu-id="795fd-407">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-407">win:UInt16</span></span>|<span data-ttu-id="795fd-408">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="795fd-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="795fd-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="795fd-409">AllocationAmount64</span></span>|<span data-ttu-id="795fd-410">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="795fd-410">win:UInt64</span></span>|<span data-ttu-id="795fd-411">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="795fd-411">The allocation size, in bytes.</span></span> <span data-ttu-id="795fd-412">Ta wartość jest dokładna dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="795fd-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="795fd-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="795fd-413">TypeId</span></span>|<span data-ttu-id="795fd-414">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="795fd-414">win:Pointer</span></span>|<span data-ttu-id="795fd-415">Adres metody.</span><span class="sxs-lookup"><span data-stu-id="795fd-415">The address of the MethodTable.</span></span> <span data-ttu-id="795fd-416">Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to adres metody, która odnosi się do ostatniego przydzielony obiekt (obiekt, który spowodował przekroczenie 100 KB progu).</span><span class="sxs-lookup"><span data-stu-id="795fd-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="795fd-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="795fd-417">TypeName</span></span>|<span data-ttu-id="795fd-418">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="795fd-418">win:UnicodeString</span></span>|<span data-ttu-id="795fd-419">Nazwa przydzieloną typ.</span><span class="sxs-lookup"><span data-stu-id="795fd-419">The name of the type that was allocated.</span></span> <span data-ttu-id="795fd-420">Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to typ ostatniego przydzielono obiektu (obiektu, który spowodował przekroczenie 100 KB).</span><span class="sxs-lookup"><span data-stu-id="795fd-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="795fd-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="795fd-421">HeapIndex</span></span>|<span data-ttu-id="795fd-422">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-422">win:UInt32</span></span>|<span data-ttu-id="795fd-423">Sterta, do której został przydzielony obiekt.</span><span class="sxs-lookup"><span data-stu-id="795fd-423">The heap where the object was allocated.</span></span> <span data-ttu-id="795fd-424">Ta wartość jest równa 0 (zero) podczas uruchamiania z odzyskiwaniem pamięci stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="795fd-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="795fd-425">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="795fd-426">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="795fd-427">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-428">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-428">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-429">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-430">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-431">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-432">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-433">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-433">Event</span></span>|<span data-ttu-id="795fd-434">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-434">Event ID</span></span>|<span data-ttu-id="795fd-435">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="795fd-436">14</span><span class="sxs-lookup"><span data-stu-id="795fd-436">14</span></span>|<span data-ttu-id="795fd-437">Początek uruchamiania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="795fd-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="795fd-438">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-438">No event data.</span></span>  
  
 [<span data-ttu-id="795fd-439">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="795fd-440">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="795fd-441">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-442">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-442">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-443">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-444">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-445">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-446">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-447">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-447">Event</span></span>|<span data-ttu-id="795fd-448">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-448">Event ID</span></span>|<span data-ttu-id="795fd-449">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="795fd-450">13</span><span class="sxs-lookup"><span data-stu-id="795fd-450">13</span></span>|<span data-ttu-id="795fd-451">Koniec uruchomionych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="795fd-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="795fd-452">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="795fd-453">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="795fd-453">Field name</span></span>|<span data-ttu-id="795fd-454">Typ danych</span><span class="sxs-lookup"><span data-stu-id="795fd-454">Data type</span></span>|<span data-ttu-id="795fd-455">Opis</span><span class="sxs-lookup"><span data-stu-id="795fd-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="795fd-456">Count</span><span class="sxs-lookup"><span data-stu-id="795fd-456">Count</span></span>|<span data-ttu-id="795fd-457">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="795fd-457">win:UInt32</span></span>|<span data-ttu-id="795fd-458">Liczba uruchomionych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="795fd-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="795fd-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="795fd-459">ClrInstanceID</span></span>|<span data-ttu-id="795fd-460">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="795fd-460">win:UInt16</span></span>|<span data-ttu-id="795fd-461">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="795fd-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="795fd-462">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="795fd-463">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="795fd-464">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-465">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-465">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-466">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-467">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-468">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-468">Informational (4)</span></span>|  
|<span data-ttu-id="795fd-469">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="795fd-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="795fd-470">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-471">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-472">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-472">Event</span></span>|<span data-ttu-id="795fd-473">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-473">Event ID</span></span>|<span data-ttu-id="795fd-474">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="795fd-475">11</span><span class="sxs-lookup"><span data-stu-id="795fd-475">11</span></span>|<span data-ttu-id="795fd-476">Utworzono wątek współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="795fd-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="795fd-477">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-477">No event data.</span></span>  
  
 [<span data-ttu-id="795fd-478">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="795fd-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="795fd-479">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="795fd-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="795fd-480">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="795fd-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="795fd-481">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-481">Keyword for raising the event</span></span>|<span data-ttu-id="795fd-482">Poziom</span><span class="sxs-lookup"><span data-stu-id="795fd-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="795fd-483">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="795fd-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="795fd-484">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-484">Informational (4)</span></span>|  
|<span data-ttu-id="795fd-485">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="795fd-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="795fd-486">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="795fd-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="795fd-487">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="795fd-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="795fd-488">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="795fd-488">Event</span></span>|<span data-ttu-id="795fd-489">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="795fd-489">Event ID</span></span>|<span data-ttu-id="795fd-490">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="795fd-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="795fd-491">12</span><span class="sxs-lookup"><span data-stu-id="795fd-491">12</span></span>|<span data-ttu-id="795fd-492">Wątek współbieżnego wyrzucania elementów bezużytecznych został zakończony.</span><span class="sxs-lookup"><span data-stu-id="795fd-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="795fd-493">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="795fd-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795fd-494">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="795fd-494">See also</span></span>

- [<span data-ttu-id="795fd-495">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="795fd-495">CLR ETW Events</span></span>](clr-etw-events.md)
