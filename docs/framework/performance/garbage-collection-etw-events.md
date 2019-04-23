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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149737"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="cdc38-102">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="cdc38-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="cdc38-103">Te zdarzenia zbierać informacje dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="cdc38-104">Pomagają w diagnostyce i debugowania, w tym określanie, ile razy wyrzucania elementów bezużytecznych zostało wykonane, ile pamięci została zwolniona podczas wyrzucania elementów bezużytecznych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="cdc38-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="cdc38-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="cdc38-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="cdc38-106">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="cdc38-107">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="cdc38-108">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="cdc38-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="cdc38-109">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="cdc38-110">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="cdc38-111">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="cdc38-112">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="cdc38-113">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="cdc38-114">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="cdc38-115">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="cdc38-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="cdc38-116">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="cdc38-117">GCFinalizersEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="cdc38-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="cdc38-118">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="cdc38-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="cdc38-119">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="cdc38-120">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="cdc38-121">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="cdc38-122">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="cdc38-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="cdc38-123">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-123">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-124">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-126">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-127">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-128">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-128">Event</span></span>|<span data-ttu-id="cdc38-129">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-129">Event ID</span></span>|<span data-ttu-id="cdc38-130">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="cdc38-131">1</span><span class="sxs-lookup"><span data-stu-id="cdc38-131">1</span></span>|<span data-ttu-id="cdc38-132">Wyrzucanie elementów bezużytecznych zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="cdc38-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="cdc38-133">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdc38-134">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cdc38-134">Field name</span></span>|<span data-ttu-id="cdc38-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cdc38-135">Data type</span></span>|<span data-ttu-id="cdc38-136">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdc38-137">Licznik</span><span class="sxs-lookup"><span data-stu-id="cdc38-137">Count</span></span>|<span data-ttu-id="cdc38-138">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-138">win:UInt32</span></span>|<span data-ttu-id="cdc38-139">*n*th wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="cdc38-140">Głębokość</span><span class="sxs-lookup"><span data-stu-id="cdc38-140">Depth</span></span>|<span data-ttu-id="cdc38-141">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-141">win:UInt32</span></span>|<span data-ttu-id="cdc38-142">Generowanie, które są zbierane.</span><span class="sxs-lookup"><span data-stu-id="cdc38-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="cdc38-143">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="cdc38-143">Reason</span></span>|<span data-ttu-id="cdc38-144">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-144">win:UInt32</span></span>|<span data-ttu-id="cdc38-145">Dlaczego wyrzucania elementów bezużytecznych zostało wyzwolone:</span><span class="sxs-lookup"><span data-stu-id="cdc38-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="cdc38-146">0x0 - Alokacja sterty dla małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="cdc38-147">0x1 — wywołane.</span><span class="sxs-lookup"><span data-stu-id="cdc38-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="cdc38-148">0x2 — małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="cdc38-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="cdc38-149">0x3 — pusta.</span><span class="sxs-lookup"><span data-stu-id="cdc38-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="cdc38-150">0x4 - Alokacja sterty dla dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="cdc38-151">0x5 — Brak miejsca (dla sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="cdc38-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="cdc38-152">0x6 — Brak miejsca (dla sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="cdc38-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="cdc38-153">0x7 — wywołane, ale nie wymuszono jako blokowania.</span><span class="sxs-lookup"><span data-stu-id="cdc38-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="cdc38-154">Typ</span><span class="sxs-lookup"><span data-stu-id="cdc38-154">Type</span></span>|<span data-ttu-id="cdc38-155">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-155">win:UInt32</span></span>|<span data-ttu-id="cdc38-156">0x0 — blokowanie wyrzucania elementów bezużytecznych wystąpiło poza wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="cdc38-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="cdc38-157">0x1 — wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="cdc38-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="cdc38-158">0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpił podczas wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="cdc38-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="cdc38-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdc38-159">ClrInstanceID</span></span>|<span data-ttu-id="cdc38-160">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-160">win:UInt16</span></span>|<span data-ttu-id="cdc38-161">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cdc38-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cdc38-162">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="cdc38-163">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="cdc38-164">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-165">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-165">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-166">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-168">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-169">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-170">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-170">Event</span></span>|<span data-ttu-id="cdc38-171">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-171">Event ID</span></span>|<span data-ttu-id="cdc38-172">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="cdc38-173">2</span><span class="sxs-lookup"><span data-stu-id="cdc38-173">2</span></span>|<span data-ttu-id="cdc38-174">Wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="cdc38-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="cdc38-175">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdc38-176">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cdc38-176">Field name</span></span>|<span data-ttu-id="cdc38-177">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cdc38-177">Data type</span></span>|<span data-ttu-id="cdc38-178">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdc38-179">Licznik</span><span class="sxs-lookup"><span data-stu-id="cdc38-179">Count</span></span>|<span data-ttu-id="cdc38-180">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-180">win:UInt32</span></span>|<span data-ttu-id="cdc38-181">*n*th wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="cdc38-182">Głębokość</span><span class="sxs-lookup"><span data-stu-id="cdc38-182">Depth</span></span>|<span data-ttu-id="cdc38-183">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-183">win:UInt32</span></span>|<span data-ttu-id="cdc38-184">Generowanie, które zostały zebrane.</span><span class="sxs-lookup"><span data-stu-id="cdc38-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="cdc38-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdc38-185">ClrInstanceID</span></span>|<span data-ttu-id="cdc38-186">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-186">win:UInt16</span></span>|<span data-ttu-id="cdc38-187">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cdc38-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cdc38-188">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="cdc38-189">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="cdc38-190">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-191">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-191">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-192">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-194">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-195">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-196">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-196">Event</span></span>|<span data-ttu-id="cdc38-197">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-197">Event ID</span></span>|<span data-ttu-id="cdc38-198">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="cdc38-199">4</span><span class="sxs-lookup"><span data-stu-id="cdc38-199">4</span></span>|<span data-ttu-id="cdc38-200">Pokazuje statystykę sterty na końcu każdej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="cdc38-201">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdc38-202">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cdc38-202">Field name</span></span>|<span data-ttu-id="cdc38-203">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cdc38-203">Data type</span></span>|<span data-ttu-id="cdc38-204">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdc38-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="cdc38-205">GenerationSize0</span></span>|<span data-ttu-id="cdc38-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-206">win:UInt64</span></span>|<span data-ttu-id="cdc38-207">Rozmiar w bajtach pamięć generacji 0.</span><span class="sxs-lookup"><span data-stu-id="cdc38-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="cdc38-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="cdc38-208">TotalPromotedSize0</span></span>|<span data-ttu-id="cdc38-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-209">win:UInt64</span></span>|<span data-ttu-id="cdc38-210">Liczba bajtów, które są przenoszone z generacji 0 do 1. generacji.</span><span class="sxs-lookup"><span data-stu-id="cdc38-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="cdc38-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="cdc38-211">GenerationSize1</span></span>|<span data-ttu-id="cdc38-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-212">win:UInt64</span></span>|<span data-ttu-id="cdc38-213">Rozmiar w bajtach pamięci generacji 1.</span><span class="sxs-lookup"><span data-stu-id="cdc38-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="cdc38-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="cdc38-214">TotalPromotedSize1</span></span>|<span data-ttu-id="cdc38-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-215">win:UInt64</span></span>|<span data-ttu-id="cdc38-216">Liczba bajtów, które są przenoszone z generacji 1 do 2. generacji.</span><span class="sxs-lookup"><span data-stu-id="cdc38-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="cdc38-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="cdc38-217">GenerationSize2</span></span>|<span data-ttu-id="cdc38-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-218">win:UInt64</span></span>|<span data-ttu-id="cdc38-219">Rozmiar w bajtach pamięci generacji 2.</span><span class="sxs-lookup"><span data-stu-id="cdc38-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="cdc38-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="cdc38-220">TotalPromotedSize2</span></span>|<span data-ttu-id="cdc38-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-221">win:UInt64</span></span>|<span data-ttu-id="cdc38-222">Liczba bajtów, które przetrwały w generacji 2 od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="cdc38-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="cdc38-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="cdc38-223">GenerationSize3</span></span>|<span data-ttu-id="cdc38-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-224">win:UInt64</span></span>|<span data-ttu-id="cdc38-225">Rozmiar w bajtach stosu dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="cdc38-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="cdc38-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="cdc38-226">TotalPromotedSize3</span></span>|<span data-ttu-id="cdc38-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-227">win:UInt64</span></span>|<span data-ttu-id="cdc38-228">Liczba bajtów, które przetrwały w stosie dużego obiektu, od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="cdc38-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="cdc38-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="cdc38-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="cdc38-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-230">win:UInt64</span></span>|<span data-ttu-id="cdc38-231">Całkowity rozmiar w bajtach, obiekty, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="cdc38-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="cdc38-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="cdc38-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="cdc38-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-233">win:UInt64</span></span>|<span data-ttu-id="cdc38-234">Liczba obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="cdc38-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="cdc38-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="cdc38-235">PinnedObjectCount</span></span>|<span data-ttu-id="cdc38-236">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-236">win:UInt32</span></span>|<span data-ttu-id="cdc38-237">Liczba przypiętych obiektów (nieprzenośne).</span><span class="sxs-lookup"><span data-stu-id="cdc38-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="cdc38-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="cdc38-238">SinkBlockCount</span></span>|<span data-ttu-id="cdc38-239">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-239">win:UInt32</span></span>|<span data-ttu-id="cdc38-240">Liczba bloków synchronizacji w użyciu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="cdc38-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="cdc38-241">GCHandleCount</span></span>|<span data-ttu-id="cdc38-242">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-242">win:UInt32</span></span>|<span data-ttu-id="cdc38-243">Obsługuje liczbę operacji wyrzucania elementów bezużytecznych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="cdc38-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdc38-244">ClrInstanceID</span></span>|<span data-ttu-id="cdc38-245">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-245">win:UInt16</span></span>|<span data-ttu-id="cdc38-246">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cdc38-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cdc38-247">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="cdc38-248">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="cdc38-249">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-250">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-250">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-251">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-253">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-254">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-255">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-255">Event</span></span>|<span data-ttu-id="cdc38-256">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-256">Event ID</span></span>|<span data-ttu-id="cdc38-257">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="cdc38-258">5</span><span class="sxs-lookup"><span data-stu-id="cdc38-258">5</span></span>|<span data-ttu-id="cdc38-259">Utworzono nowy segment kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="cdc38-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="cdc38-260">Ponadto gdy śledzenie jest włączone na temat procesu, który jest już uruchomiony, to zdarzenie jest wywoływane dla każdego istniejącego segmentu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="cdc38-261">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdc38-262">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cdc38-262">Field name</span></span>|<span data-ttu-id="cdc38-263">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cdc38-263">Data type</span></span>|<span data-ttu-id="cdc38-264">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdc38-265">Adres</span><span class="sxs-lookup"><span data-stu-id="cdc38-265">Address</span></span>|<span data-ttu-id="cdc38-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-266">win:UInt64</span></span>|<span data-ttu-id="cdc38-267">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-267">The address of the segment.</span></span>|  
|<span data-ttu-id="cdc38-268">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="cdc38-268">Size</span></span>|<span data-ttu-id="cdc38-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-269">win:UInt64</span></span>|<span data-ttu-id="cdc38-270">Rozmiar segmentu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-270">The size of the segment.</span></span>|  
|<span data-ttu-id="cdc38-271">Typ</span><span class="sxs-lookup"><span data-stu-id="cdc38-271">Type</span></span>|<span data-ttu-id="cdc38-272">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-272">win:UInt32</span></span>|<span data-ttu-id="cdc38-273">0x0 — sterty małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="cdc38-274">0x1 — stertę dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="cdc38-275">0x2 — tylko do odczytu sterty.</span><span class="sxs-lookup"><span data-stu-id="cdc38-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="cdc38-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdc38-276">ClrInstanceID</span></span>|<span data-ttu-id="cdc38-277">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-277">win:UInt16</span></span>|<span data-ttu-id="cdc38-278">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cdc38-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="cdc38-279">Należy pamiętać, że rozmiar segmentów przydzielonej przez moduł odśmiecania pamięci jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="cdc38-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="cdc38-280">Twoja aplikacja nigdy nie należy wprowadzić założeń dotyczących lub zależeć od rozmiaru określonego segmentu nie ma podejmować skonfigurować ilość pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="cdc38-281">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="cdc38-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="cdc38-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="cdc38-283">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-284">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-284">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-285">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-287">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-288">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-289">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-289">Event</span></span>|<span data-ttu-id="cdc38-290">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-290">Event ID</span></span>|<span data-ttu-id="cdc38-291">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="cdc38-292">6</span><span class="sxs-lookup"><span data-stu-id="cdc38-292">6</span></span>|<span data-ttu-id="cdc38-293">Segment kolekcji wyrzucania elementów został wydany.</span><span class="sxs-lookup"><span data-stu-id="cdc38-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="cdc38-294">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdc38-295">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cdc38-295">Field name</span></span>|<span data-ttu-id="cdc38-296">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cdc38-296">Data type</span></span>|<span data-ttu-id="cdc38-297">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdc38-298">Adres</span><span class="sxs-lookup"><span data-stu-id="cdc38-298">Address</span></span>|<span data-ttu-id="cdc38-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-299">win:UInt64</span></span>|<span data-ttu-id="cdc38-300">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-300">The address of the segment.</span></span>|  
|<span data-ttu-id="cdc38-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdc38-301">ClrInstanceID</span></span>|<span data-ttu-id="cdc38-302">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-302">win:UInt16</span></span>|<span data-ttu-id="cdc38-303">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cdc38-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cdc38-304">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="cdc38-305">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="cdc38-306">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-307">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-307">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-308">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-310">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-311">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-312">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-312">Event</span></span>|<span data-ttu-id="cdc38-313">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-313">Event ID</span></span>|<span data-ttu-id="cdc38-314">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="cdc38-315">7</span><span class="sxs-lookup"><span data-stu-id="cdc38-315">7</span></span>|<span data-ttu-id="cdc38-316">Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została rozpoczęta.</span><span class="sxs-lookup"><span data-stu-id="cdc38-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="cdc38-317">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-317">No event data.</span></span>  
  
 [<span data-ttu-id="cdc38-318">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="cdc38-319">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="cdc38-320">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-321">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-321">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-322">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-324">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-325">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-326">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-326">Event</span></span>|<span data-ttu-id="cdc38-327">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-327">Event Id</span></span>|<span data-ttu-id="cdc38-328">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="cdc38-329">3</span><span class="sxs-lookup"><span data-stu-id="cdc38-329">3</span></span>|<span data-ttu-id="cdc38-330">Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została zakończona.</span><span class="sxs-lookup"><span data-stu-id="cdc38-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="cdc38-331">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-331">No event data.</span></span>  
  
 [<span data-ttu-id="cdc38-332">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="cdc38-333">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="cdc38-334">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-335">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-335">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-336">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-338">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-339">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-340">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-340">Event</span></span>|<span data-ttu-id="cdc38-341">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-341">Event ID</span></span>|<span data-ttu-id="cdc38-342">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="cdc38-343">9</span><span class="sxs-lookup"><span data-stu-id="cdc38-343">9</span></span>|<span data-ttu-id="cdc38-344">Początek zawieszenia aparatu wykonywania do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="cdc38-345">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdc38-346">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cdc38-346">Field name</span></span>|<span data-ttu-id="cdc38-347">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cdc38-347">Data type</span></span>|<span data-ttu-id="cdc38-348">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdc38-349">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="cdc38-349">Reason</span></span>|<span data-ttu-id="cdc38-350">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-350">win:UInt16</span></span>|<span data-ttu-id="cdc38-351">0x0 — inne.</span><span class="sxs-lookup"><span data-stu-id="cdc38-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="cdc38-352">0x1 — wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="cdc38-353">0x2 — zamykania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cdc38-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="cdc38-354">0x3 - pitching kodu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="cdc38-355">0x4 - shutdown.</span><span class="sxs-lookup"><span data-stu-id="cdc38-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="cdc38-356">0x5 - debugera.</span><span class="sxs-lookup"><span data-stu-id="cdc38-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="cdc38-357">0x6 — przygotowanie do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="cdc38-358">Licznik</span><span class="sxs-lookup"><span data-stu-id="cdc38-358">Count</span></span>|<span data-ttu-id="cdc38-359">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-359">win:UInt32</span></span>|<span data-ttu-id="cdc38-360">Liczba operacji odzyskiwania pamięci w czasie.</span><span class="sxs-lookup"><span data-stu-id="cdc38-360">The GC count at the time.</span></span> <span data-ttu-id="cdc38-361">Zwykle po to zobaczysz kolejnych zdarzeń początek odzyskiwania pamięci, a licznik będzie wskazywać ta liczba + 1, jak możemy zwiększyć indeksu GC podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="cdc38-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdc38-362">ClrInstanceID</span></span>|<span data-ttu-id="cdc38-363">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-363">win:UInt16</span></span>|<span data-ttu-id="cdc38-364">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cdc38-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cdc38-365">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="cdc38-366">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="cdc38-367">W poniższej tabeli przedstawiono — słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="cdc38-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="cdc38-368">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-368">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-369">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-371">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-372">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="cdc38-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="cdc38-373">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-373">Event</span></span>|<span data-ttu-id="cdc38-374">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-374">Event ID</span></span>|<span data-ttu-id="cdc38-375">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="cdc38-376">8</span><span class="sxs-lookup"><span data-stu-id="cdc38-376">8</span></span>|<span data-ttu-id="cdc38-377">Koniec zawieszenia aparatu wykonywania do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="cdc38-378">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-378">No event data.</span></span>  
  
 [<span data-ttu-id="cdc38-379">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="cdc38-380">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="cdc38-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="cdc38-381">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-382">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-382">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-383">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-385">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-386">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-387">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-387">Event</span></span>|<span data-ttu-id="cdc38-388">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-388">Event ID</span></span>|<span data-ttu-id="cdc38-389">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="cdc38-390">10</span><span class="sxs-lookup"><span data-stu-id="cdc38-390">10</span></span>|<span data-ttu-id="cdc38-391">Każdorazowo przydzielany około 100 KB.</span><span class="sxs-lookup"><span data-stu-id="cdc38-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="cdc38-392">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdc38-393">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cdc38-393">Field name</span></span>|<span data-ttu-id="cdc38-394">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cdc38-394">Data type</span></span>|<span data-ttu-id="cdc38-395">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdc38-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="cdc38-396">AllocationAmount</span></span>|<span data-ttu-id="cdc38-397">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-397">win:UInt32</span></span>|<span data-ttu-id="cdc38-398">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="cdc38-398">The allocation size, in bytes.</span></span> <span data-ttu-id="cdc38-399">Ta wartość jest prawidłowe dla alokacji, który jest mniejsza niż długość ULONG (4 294 967 295 w bajtach).</span><span class="sxs-lookup"><span data-stu-id="cdc38-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="cdc38-400">Jeśli alokacja jest większa, to pole zawiera obciętą wartość.</span><span class="sxs-lookup"><span data-stu-id="cdc38-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="cdc38-401">Użyj `AllocationAmount64` dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="cdc38-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="cdc38-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="cdc38-402">AllocationKind</span></span>|<span data-ttu-id="cdc38-403">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-403">win:UInt32</span></span>|<span data-ttu-id="cdc38-404">0x0 - małych obiektów alokacji (alokacji jest sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="cdc38-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="cdc38-405">0x1 — alokacji dużego obiektu (alokacji znajduje się w stosie dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="cdc38-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="cdc38-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdc38-406">ClrInstanceID</span></span>|<span data-ttu-id="cdc38-407">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-407">win:UInt16</span></span>|<span data-ttu-id="cdc38-408">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cdc38-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="cdc38-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="cdc38-409">AllocationAmount64</span></span>|<span data-ttu-id="cdc38-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="cdc38-410">win:UInt64</span></span>|<span data-ttu-id="cdc38-411">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="cdc38-411">The allocation size, in bytes.</span></span> <span data-ttu-id="cdc38-412">Ta wartość jest dokładne w przypadku bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="cdc38-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="cdc38-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="cdc38-413">TypeId</span></span>|<span data-ttu-id="cdc38-414">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="cdc38-414">win:Pointer</span></span>|<span data-ttu-id="cdc38-415">Adres MethodTable.</span><span class="sxs-lookup"><span data-stu-id="cdc38-415">The address of the MethodTable.</span></span> <span data-ttu-id="cdc38-416">W przypadku kilku typów obiektów, które zostały przydzielone podczas tego zdarzenia jest to adres MethodTable, który odpowiada ostatni obiekt przydzielony (obiekt, który spowodował zostać przekroczony próg 100 KB).</span><span class="sxs-lookup"><span data-stu-id="cdc38-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="cdc38-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="cdc38-417">TypeName</span></span>|<span data-ttu-id="cdc38-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="cdc38-418">win:UnicodeString</span></span>|<span data-ttu-id="cdc38-419">Nazwa typu, która została przydzielona.</span><span class="sxs-lookup"><span data-stu-id="cdc38-419">The name of the type that was allocated.</span></span> <span data-ttu-id="cdc38-420">W przypadku kilku typów obiektów, które zostały przydzielone podczas tego zdarzenia jest typ ostatni obiekt przydzielony (obiekt, który spowodował zostać przekroczony próg 100 KB).</span><span class="sxs-lookup"><span data-stu-id="cdc38-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="cdc38-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="cdc38-421">HeapIndex</span></span>|<span data-ttu-id="cdc38-422">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-422">win:UInt32</span></span>|<span data-ttu-id="cdc38-423">Sterty, w którym został przydzielony obiekt.</span><span class="sxs-lookup"><span data-stu-id="cdc38-423">The heap where the object was allocated.</span></span> <span data-ttu-id="cdc38-424">Ta wartość jest 0 (zero), podczas korzystania z użyciem wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cdc38-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="cdc38-425">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="cdc38-426">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="cdc38-427">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-428">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-428">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-429">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-431">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-432">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-433">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-433">Event</span></span>|<span data-ttu-id="cdc38-434">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-434">Event ID</span></span>|<span data-ttu-id="cdc38-435">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="cdc38-436">14</span><span class="sxs-lookup"><span data-stu-id="cdc38-436">14</span></span>|<span data-ttu-id="cdc38-437">Początek uruchamianie finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="cdc38-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="cdc38-438">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-438">No event data.</span></span>  
  
 [<span data-ttu-id="cdc38-439">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="cdc38-440">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="cdc38-441">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-442">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-442">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-443">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-445">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-446">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-447">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-447">Event</span></span>|<span data-ttu-id="cdc38-448">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-448">Event ID</span></span>|<span data-ttu-id="cdc38-449">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="cdc38-450">13</span><span class="sxs-lookup"><span data-stu-id="cdc38-450">13</span></span>|<span data-ttu-id="cdc38-451">Koniec uruchamianie finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="cdc38-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="cdc38-452">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdc38-453">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cdc38-453">Field name</span></span>|<span data-ttu-id="cdc38-454">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cdc38-454">Data type</span></span>|<span data-ttu-id="cdc38-455">Opis</span><span class="sxs-lookup"><span data-stu-id="cdc38-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdc38-456">Licznik</span><span class="sxs-lookup"><span data-stu-id="cdc38-456">Count</span></span>|<span data-ttu-id="cdc38-457">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cdc38-457">win:UInt32</span></span>|<span data-ttu-id="cdc38-458">Liczba finalizatorów, które zostały uruchomione.</span><span class="sxs-lookup"><span data-stu-id="cdc38-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="cdc38-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdc38-459">ClrInstanceID</span></span>|<span data-ttu-id="cdc38-460">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="cdc38-460">win:UInt16</span></span>|<span data-ttu-id="cdc38-461">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="cdc38-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cdc38-462">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="cdc38-463">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="cdc38-464">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-465">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-465">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-466">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-468">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-468">Informational (4)</span></span>|  
|<span data-ttu-id="cdc38-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="cdc38-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="cdc38-470">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-471">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-472">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-472">Event</span></span>|<span data-ttu-id="cdc38-473">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-473">Event ID</span></span>|<span data-ttu-id="cdc38-474">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="cdc38-475">11</span><span class="sxs-lookup"><span data-stu-id="cdc38-475">11</span></span>|<span data-ttu-id="cdc38-476">Utworzono wątku kolekcji wyrzucania.</span><span class="sxs-lookup"><span data-stu-id="cdc38-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="cdc38-477">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-477">No event data.</span></span>  
  
 [<span data-ttu-id="cdc38-478">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="cdc38-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="cdc38-479">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="cdc38-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="cdc38-480">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdc38-481">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-481">Keyword for raising the event</span></span>|<span data-ttu-id="cdc38-482">Poziom</span><span class="sxs-lookup"><span data-stu-id="cdc38-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdc38-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="cdc38-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="cdc38-484">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-484">Informational (4)</span></span>|  
|<span data-ttu-id="cdc38-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="cdc38-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="cdc38-486">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="cdc38-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="cdc38-487">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdc38-488">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cdc38-488">Event</span></span>|<span data-ttu-id="cdc38-489">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdc38-489">Event ID</span></span>|<span data-ttu-id="cdc38-490">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cdc38-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="cdc38-491">12</span><span class="sxs-lookup"><span data-stu-id="cdc38-491">12</span></span>|<span data-ttu-id="cdc38-492">Wątku równoczesne wyrzucania elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="cdc38-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="cdc38-493">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cdc38-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc38-494">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdc38-494">See also</span></span>

- [<span data-ttu-id="cdc38-495">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="cdc38-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
