---
title: Zdarzenia ETW odzyskiwania pamięci
description: Wyświetl szczegółowe informacje o zdarzeniach ETW odzyskiwania pamięci. Uwzględnione zdarzenia obejmują GCStart_V1, GCEnd_V1, GCHeapStats_V1, GCCreateSegment_V1 i wiele innych.
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 58ad874ef6a12c18c404640aa66577c391573534
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309745"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="19140-104">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="19140-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="19140-105">Te zdarzenia zbierają informacje dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="19140-106">Ułatwiają one diagnostykę i debugowanie, w tym określanie, ile razy zostało wykonane wyrzucanie elementów bezużytecznych, ilości pamięci, która została zwolniona podczas odzyskiwania pamięci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="19140-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="19140-107">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="19140-108">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="19140-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="19140-109">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="19140-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="19140-110">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="19140-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="19140-111">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="19140-111">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="19140-112">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="19140-112">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="19140-113">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="19140-113">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="19140-114">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="19140-114">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="19140-115">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="19140-115">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="19140-116">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="19140-116">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="19140-117">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="19140-117">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="19140-118">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="19140-118">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="19140-119">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="19140-119">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="19140-120">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="19140-120">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="19140-121">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="19140-121">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="19140-122">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="19140-122">GCStart_V1 Event</span></span>  

<span data-ttu-id="19140-123">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="19140-123">The following table shows the keyword and level.</span></span> <span data-ttu-id="19140-124">Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="19140-124">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="19140-125">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-125">Keyword for raising the event</span></span>|<span data-ttu-id="19140-126">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-127">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-127">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-128">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-128">Informational (4)</span></span>|

<span data-ttu-id="19140-129">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-129">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-130">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-130">Event</span></span>|<span data-ttu-id="19140-131">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-131">Event ID</span></span>|<span data-ttu-id="19140-132">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="19140-133">1</span><span class="sxs-lookup"><span data-stu-id="19140-133">1</span></span>|<span data-ttu-id="19140-134">Rozpoczęto odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="19140-134">A garbage collection has started.</span></span>|

<span data-ttu-id="19140-135">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-135">The following table shows the event data:</span></span>

|<span data-ttu-id="19140-136">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="19140-136">Field name</span></span>|<span data-ttu-id="19140-137">Typ danych</span><span class="sxs-lookup"><span data-stu-id="19140-137">Data type</span></span>|<span data-ttu-id="19140-138">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-138">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="19140-139">Liczba</span><span class="sxs-lookup"><span data-stu-id="19140-139">Count</span></span>|<span data-ttu-id="19140-140">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-140">win:UInt32</span></span>|<span data-ttu-id="19140-141">*N*-ta kolekcja elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-141">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="19140-142">Ścisł</span><span class="sxs-lookup"><span data-stu-id="19140-142">Depth</span></span>|<span data-ttu-id="19140-143">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-143">win:UInt32</span></span>|<span data-ttu-id="19140-144">Generacja, która jest zbierana.</span><span class="sxs-lookup"><span data-stu-id="19140-144">The generation that is being collected.</span></span>|
|<span data-ttu-id="19140-145">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="19140-145">Reason</span></span>|<span data-ttu-id="19140-146">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-146">win:UInt32</span></span>|<span data-ttu-id="19140-147">Dlaczego wyzwolono wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="19140-147">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="19140-148">0x0 — alokacja sterty dla małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="19140-148">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="19140-149">Wywołano 0x1.</span><span class="sxs-lookup"><span data-stu-id="19140-149">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="19140-150">0x2 — mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="19140-150">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="19140-151">0x3 — puste.</span><span class="sxs-lookup"><span data-stu-id="19140-151">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="19140-152">0x4 — alokacja sterty dla dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="19140-152">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="19140-153">0x5 — brak miejsca (dla sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="19140-153">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="19140-154">0x6 — brak miejsca (dla sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="19140-154">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="19140-155">0x7 — wywołano, ale nie wymuszono blokowania.</span><span class="sxs-lookup"><span data-stu-id="19140-155">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="19140-156">Typ</span><span class="sxs-lookup"><span data-stu-id="19140-156">Type</span></span>|<span data-ttu-id="19140-157">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-157">win:UInt32</span></span>|<span data-ttu-id="19140-158">0x0 — blokowanie odzyskiwania pamięci wystąpiło poza odzyskiwaniem pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="19140-158">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="19140-159">0x1 — wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="19140-159">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="19140-160">0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpiło podczas odzyskiwania pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="19140-160">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="19140-161">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19140-161">ClrInstanceID</span></span>|<span data-ttu-id="19140-162">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-162">win:UInt16</span></span>|<span data-ttu-id="19140-163">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19140-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="19140-164">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="19140-164">GCEnd_V1 Event</span></span>

<span data-ttu-id="19140-165">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-165">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-166">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-166">Keyword for raising the event</span></span>|<span data-ttu-id="19140-167">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-168">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-168">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-169">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-169">Informational (4)</span></span>|

<span data-ttu-id="19140-170">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-170">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-171">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-171">Event</span></span>|<span data-ttu-id="19140-172">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-172">Event ID</span></span>|<span data-ttu-id="19140-173">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="19140-174">2</span><span class="sxs-lookup"><span data-stu-id="19140-174">2</span></span>|<span data-ttu-id="19140-175">Wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="19140-175">The garbage collection has ended.</span></span>|

<span data-ttu-id="19140-176">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-176">The following table shows the event data:</span></span>

|<span data-ttu-id="19140-177">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="19140-177">Field name</span></span>|<span data-ttu-id="19140-178">Typ danych</span><span class="sxs-lookup"><span data-stu-id="19140-178">Data type</span></span>|<span data-ttu-id="19140-179">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-179">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="19140-180">Liczba</span><span class="sxs-lookup"><span data-stu-id="19140-180">Count</span></span>|<span data-ttu-id="19140-181">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-181">win:UInt32</span></span>|<span data-ttu-id="19140-182">*N*-ta kolekcja elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-182">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="19140-183">Ścisł</span><span class="sxs-lookup"><span data-stu-id="19140-183">Depth</span></span>|<span data-ttu-id="19140-184">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-184">win:UInt32</span></span>|<span data-ttu-id="19140-185">Generacja, która została zebrana.</span><span class="sxs-lookup"><span data-stu-id="19140-185">The generation that was collected.</span></span>|
|<span data-ttu-id="19140-186">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19140-186">ClrInstanceID</span></span>|<span data-ttu-id="19140-187">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-187">win:UInt16</span></span>|<span data-ttu-id="19140-188">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19140-188">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="19140-189">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="19140-189">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="19140-190">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-190">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-191">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-191">Keyword for raising the event</span></span>|<span data-ttu-id="19140-192">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-192">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-193">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-194">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-194">Informational (4)</span></span>|

<span data-ttu-id="19140-195">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-195">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-196">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-196">Event</span></span>|<span data-ttu-id="19140-197">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-197">Event ID</span></span>|<span data-ttu-id="19140-198">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-198">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="19140-199">4</span><span class="sxs-lookup"><span data-stu-id="19140-199">4</span></span>|<span data-ttu-id="19140-200">Pokazuje statystyki sterty na końcu każdego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-200">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="19140-201">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-201">The following table shows the event data:</span></span>

|<span data-ttu-id="19140-202">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="19140-202">Field name</span></span>|<span data-ttu-id="19140-203">Typ danych</span><span class="sxs-lookup"><span data-stu-id="19140-203">Data type</span></span>|<span data-ttu-id="19140-204">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-204">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="19140-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="19140-205">GenerationSize0</span></span>|<span data-ttu-id="19140-206">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-206">win:UInt64</span></span>|<span data-ttu-id="19140-207">Rozmiar (w bajtach) pamięci generacji 0.</span><span class="sxs-lookup"><span data-stu-id="19140-207">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="19140-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="19140-208">TotalPromotedSize0</span></span>|<span data-ttu-id="19140-209">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-209">win:UInt64</span></span>|<span data-ttu-id="19140-210">Liczba bajtów, które są podwyższane z generacji 0 do generacji 1.</span><span class="sxs-lookup"><span data-stu-id="19140-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="19140-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="19140-211">GenerationSize1</span></span>|<span data-ttu-id="19140-212">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-212">win:UInt64</span></span>|<span data-ttu-id="19140-213">Rozmiar (w bajtach) pamięci pierwszej generacji 1.</span><span class="sxs-lookup"><span data-stu-id="19140-213">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="19140-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="19140-214">TotalPromotedSize1</span></span>|<span data-ttu-id="19140-215">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-215">win:UInt64</span></span>|<span data-ttu-id="19140-216">Liczba bajtów, które są podwyższane z generacji 1 do generacji 2.</span><span class="sxs-lookup"><span data-stu-id="19140-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="19140-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="19140-217">GenerationSize2</span></span>|<span data-ttu-id="19140-218">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-218">win:UInt64</span></span>|<span data-ttu-id="19140-219">Rozmiar (w bajtach) pamięci podnoszącej 2 generacji.</span><span class="sxs-lookup"><span data-stu-id="19140-219">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="19140-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="19140-220">TotalPromotedSize2</span></span>|<span data-ttu-id="19140-221">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-221">win:UInt64</span></span>|<span data-ttu-id="19140-222">Liczba bajtów, które przeżyły w generacji 2 po ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="19140-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="19140-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="19140-223">GenerationSize3</span></span>|<span data-ttu-id="19140-224">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-224">win:UInt64</span></span>|<span data-ttu-id="19140-225">Rozmiar sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="19140-225">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="19140-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="19140-226">TotalPromotedSize3</span></span>|<span data-ttu-id="19140-227">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-227">win:UInt64</span></span>|<span data-ttu-id="19140-228">Liczba bajtów przeczytanych z sterty dużego obiektu po ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="19140-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="19140-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="19140-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="19140-230">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-230">win:UInt64</span></span>|<span data-ttu-id="19140-231">Łączny rozmiar (w bajtach) obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="19140-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="19140-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="19140-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="19140-233">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-233">win:UInt64</span></span>|<span data-ttu-id="19140-234">Liczba obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="19140-234">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="19140-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="19140-235">PinnedObjectCount</span></span>|<span data-ttu-id="19140-236">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-236">win:UInt32</span></span>|<span data-ttu-id="19140-237">Liczba przypiętych (nieruchomych) obiektów.</span><span class="sxs-lookup"><span data-stu-id="19140-237">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="19140-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="19140-238">SinkBlockCount</span></span>|<span data-ttu-id="19140-239">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-239">win:UInt32</span></span>|<span data-ttu-id="19140-240">Liczba bloków synchronizacji w użyciu.</span><span class="sxs-lookup"><span data-stu-id="19140-240">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="19140-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="19140-241">GCHandleCount</span></span>|<span data-ttu-id="19140-242">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-242">win:UInt32</span></span>|<span data-ttu-id="19140-243">Liczba dojść do wyrzucania elementów bezużytecznych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="19140-243">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="19140-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19140-244">ClrInstanceID</span></span>|<span data-ttu-id="19140-245">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-245">win:UInt16</span></span>|<span data-ttu-id="19140-246">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19140-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="19140-247">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="19140-247">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="19140-248">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-248">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-249">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-249">Keyword for raising the event</span></span>|<span data-ttu-id="19140-250">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-250">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-251">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-251">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-252">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-252">Informational (4)</span></span>|

<span data-ttu-id="19140-253">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-253">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-254">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-254">Event</span></span>|<span data-ttu-id="19140-255">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-255">Event ID</span></span>|<span data-ttu-id="19140-256">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-256">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="19140-257">5</span><span class="sxs-lookup"><span data-stu-id="19140-257">5</span></span>|<span data-ttu-id="19140-258">Utworzono nowy segment wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-258">A new garbage collection segment has been created.</span></span> <span data-ttu-id="19140-259">Ponadto po włączeniu śledzenia dla procesu, który jest już uruchomiony, to zdarzenie jest zgłaszane dla każdego istniejącego segmentu.</span><span class="sxs-lookup"><span data-stu-id="19140-259">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="19140-260">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-260">The following table shows the event data:</span></span>

|<span data-ttu-id="19140-261">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="19140-261">Field name</span></span>|<span data-ttu-id="19140-262">Typ danych</span><span class="sxs-lookup"><span data-stu-id="19140-262">Data type</span></span>|<span data-ttu-id="19140-263">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-263">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="19140-264">Adres</span><span class="sxs-lookup"><span data-stu-id="19140-264">Address</span></span>|<span data-ttu-id="19140-265">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-265">win:UInt64</span></span>|<span data-ttu-id="19140-266">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="19140-266">The address of the segment.</span></span>|
|<span data-ttu-id="19140-267">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="19140-267">Size</span></span>|<span data-ttu-id="19140-268">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-268">win:UInt64</span></span>|<span data-ttu-id="19140-269">Rozmiar segmentu.</span><span class="sxs-lookup"><span data-stu-id="19140-269">The size of the segment.</span></span>|
|<span data-ttu-id="19140-270">Typ</span><span class="sxs-lookup"><span data-stu-id="19140-270">Type</span></span>|<span data-ttu-id="19140-271">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-271">win:UInt32</span></span>|<span data-ttu-id="19140-272">0x0 — sterta małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="19140-272">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="19140-273">0x1 — sterta dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="19140-273">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="19140-274">0x2 — sterta tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="19140-274">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="19140-275">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19140-275">ClrInstanceID</span></span>|<span data-ttu-id="19140-276">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-276">win:UInt16</span></span>|<span data-ttu-id="19140-277">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19140-277">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="19140-278">Należy zauważyć, że rozmiar segmentów przydzielone przez moduł wyrzucania elementów bezużytecznych jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami.</span><span class="sxs-lookup"><span data-stu-id="19140-278">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="19140-279">Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="19140-279">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="19140-280">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="19140-280">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="19140-281">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-281">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-282">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-282">Keyword for raising the event</span></span>|<span data-ttu-id="19140-283">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-283">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-284">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-284">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-285">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-285">Informational (4)</span></span>|

<span data-ttu-id="19140-286">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-286">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-287">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-287">Event</span></span>|<span data-ttu-id="19140-288">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-288">Event ID</span></span>|<span data-ttu-id="19140-289">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-289">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="19140-290">6</span><span class="sxs-lookup"><span data-stu-id="19140-290">6</span></span>|<span data-ttu-id="19140-291">Wydano segment wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-291">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="19140-292">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-292">The following table shows the event data:</span></span>

|<span data-ttu-id="19140-293">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="19140-293">Field name</span></span>|<span data-ttu-id="19140-294">Typ danych</span><span class="sxs-lookup"><span data-stu-id="19140-294">Data type</span></span>|<span data-ttu-id="19140-295">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-295">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="19140-296">Adres</span><span class="sxs-lookup"><span data-stu-id="19140-296">Address</span></span>|<span data-ttu-id="19140-297">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-297">win:UInt64</span></span>|<span data-ttu-id="19140-298">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="19140-298">The address of the segment.</span></span>|
|<span data-ttu-id="19140-299">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19140-299">ClrInstanceID</span></span>|<span data-ttu-id="19140-300">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-300">win:UInt16</span></span>|<span data-ttu-id="19140-301">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19140-301">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="19140-302">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="19140-302">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="19140-303">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-303">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-304">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-304">Keyword for raising the event</span></span>|<span data-ttu-id="19140-305">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-305">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-306">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-306">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-307">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-307">Informational (4)</span></span>|

<span data-ttu-id="19140-308">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-308">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-309">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-309">Event</span></span>|<span data-ttu-id="19140-310">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-310">Event ID</span></span>|<span data-ttu-id="19140-311">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-311">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="19140-312">7</span><span class="sxs-lookup"><span data-stu-id="19140-312">7</span></span>|<span data-ttu-id="19140-313">Rozpoczęto wznawianie od zawieszenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="19140-313">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="19140-314">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19140-314">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="19140-315">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="19140-315">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="19140-316">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-316">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-317">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-317">Keyword for raising the event</span></span>|<span data-ttu-id="19140-318">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-318">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-319">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-319">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-320">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-320">Informational (4)</span></span>|

<span data-ttu-id="19140-321">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-321">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-322">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-322">Event</span></span>|<span data-ttu-id="19140-323">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-323">Event Id</span></span>|<span data-ttu-id="19140-324">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-324">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="19140-325">3</span><span class="sxs-lookup"><span data-stu-id="19140-325">3</span></span>|<span data-ttu-id="19140-326">Zakończono wznawianie z zawieszenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="19140-326">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="19140-327">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19140-327">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="19140-328">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="19140-328">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="19140-329">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-329">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-330">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-330">Keyword for raising the event</span></span>|<span data-ttu-id="19140-331">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-331">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-332">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-332">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-333">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-333">Informational (4)</span></span>|

<span data-ttu-id="19140-334">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-334">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-335">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-335">Event</span></span>|<span data-ttu-id="19140-336">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-336">Event ID</span></span>|<span data-ttu-id="19140-337">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-337">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="19140-338">9</span><span class="sxs-lookup"><span data-stu-id="19140-338">9</span></span>|<span data-ttu-id="19140-339">Początek zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-339">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="19140-340">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-340">The following table shows the event data:</span></span>

|<span data-ttu-id="19140-341">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="19140-341">Field name</span></span>|<span data-ttu-id="19140-342">Typ danych</span><span class="sxs-lookup"><span data-stu-id="19140-342">Data type</span></span>|<span data-ttu-id="19140-343">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-343">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="19140-344">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="19140-344">Reason</span></span>|<span data-ttu-id="19140-345">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-345">win:UInt16</span></span>|<span data-ttu-id="19140-346">0x0 — inne.</span><span class="sxs-lookup"><span data-stu-id="19140-346">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="19140-347">0x1 — odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="19140-347">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="19140-348">0x2 — zamknięcie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19140-348">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="19140-349">0x3 — nachylenie kodu.</span><span class="sxs-lookup"><span data-stu-id="19140-349">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="19140-350">0x4 — zamykanie.</span><span class="sxs-lookup"><span data-stu-id="19140-350">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="19140-351">0x5 — debuger.</span><span class="sxs-lookup"><span data-stu-id="19140-351">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="19140-352">0x6 — przygotowanie do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-352">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="19140-353">Liczba</span><span class="sxs-lookup"><span data-stu-id="19140-353">Count</span></span>|<span data-ttu-id="19140-354">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-354">win:UInt32</span></span>|<span data-ttu-id="19140-355">Liczba GC w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="19140-355">The GC count at the time.</span></span> <span data-ttu-id="19140-356">Zwykle po wykonaniu tej operacji zobaczysz kolejne zdarzenie uruchomienia GC, a jego liczba jest taka sama jak liczba + 1, ponieważ zwiększy indeks GC podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-356">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="19140-357">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19140-357">ClrInstanceID</span></span>|<span data-ttu-id="19140-358">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-358">win:UInt16</span></span>|<span data-ttu-id="19140-359">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19140-359">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="19140-360">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="19140-360">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="19140-361">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-361">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-362">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-362">Keyword for raising the event</span></span>|<span data-ttu-id="19140-363">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-363">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-364">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-364">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-365">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-365">Informational (4)</span></span>|

<span data-ttu-id="19140-366">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-366">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-367">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-367">Event</span></span>|<span data-ttu-id="19140-368">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-368">Event ID</span></span>|<span data-ttu-id="19140-369">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-369">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="19140-370">8</span><span class="sxs-lookup"><span data-stu-id="19140-370">8</span></span>|<span data-ttu-id="19140-371">Koniec zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-371">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="19140-372">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19140-372">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="19140-373">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="19140-373">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="19140-374">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-374">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-375">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-375">Keyword for raising the event</span></span>|<span data-ttu-id="19140-376">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-376">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-377">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-377">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-378">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-378">Informational (4)</span></span>|

<span data-ttu-id="19140-379">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-379">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-380">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-380">Event</span></span>|<span data-ttu-id="19140-381">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-381">Event ID</span></span>|<span data-ttu-id="19140-382">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-382">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="19140-383">10</span><span class="sxs-lookup"><span data-stu-id="19140-383">10</span></span>|<span data-ttu-id="19140-384">Za każdym razem przydzielono około 100 KB.</span><span class="sxs-lookup"><span data-stu-id="19140-384">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="19140-385">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-385">The following table shows the event data:</span></span>

|<span data-ttu-id="19140-386">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="19140-386">Field name</span></span>|<span data-ttu-id="19140-387">Typ danych</span><span class="sxs-lookup"><span data-stu-id="19140-387">Data type</span></span>|<span data-ttu-id="19140-388">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-388">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="19140-389">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="19140-389">AllocationAmount</span></span>|<span data-ttu-id="19140-390">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-390">win:UInt32</span></span>|<span data-ttu-id="19140-391">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="19140-391">The allocation size, in bytes.</span></span> <span data-ttu-id="19140-392">Ta wartość jest dokładna dla przydziałów, które są mniejsze niż długość ULONG (4 294 967 295 bajtów).</span><span class="sxs-lookup"><span data-stu-id="19140-392">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="19140-393">Jeśli alokacja jest większa, to pole zawiera obciętą wartość.</span><span class="sxs-lookup"><span data-stu-id="19140-393">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="19140-394">Używane `AllocationAmount64` dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="19140-394">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="19140-395">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="19140-395">AllocationKind</span></span>|<span data-ttu-id="19140-396">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-396">win:UInt32</span></span>|<span data-ttu-id="19140-397">0x0 — alokacja małego obiektu (alokacja jest w ramach sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="19140-397">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="19140-398">0x1 — alokacja dużego obiektu (alokacja jest w sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="19140-398">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="19140-399">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19140-399">ClrInstanceID</span></span>|<span data-ttu-id="19140-400">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-400">win:UInt16</span></span>|<span data-ttu-id="19140-401">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19140-401">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="19140-402">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="19140-402">AllocationAmount64</span></span>|<span data-ttu-id="19140-403">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="19140-403">win:UInt64</span></span>|<span data-ttu-id="19140-404">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="19140-404">The allocation size, in bytes.</span></span> <span data-ttu-id="19140-405">Ta wartość jest dokładna dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="19140-405">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="19140-406">Parametru</span><span class="sxs-lookup"><span data-stu-id="19140-406">TypeId</span></span>|<span data-ttu-id="19140-407">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="19140-407">win:Pointer</span></span>|<span data-ttu-id="19140-408">Adres metody.</span><span class="sxs-lookup"><span data-stu-id="19140-408">The address of the MethodTable.</span></span> <span data-ttu-id="19140-409">Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to adres metody, która odnosi się do ostatniego przydzielony obiekt (obiekt, który spowodował przekroczenie 100 KB progu).</span><span class="sxs-lookup"><span data-stu-id="19140-409">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="19140-410">TypeName</span><span class="sxs-lookup"><span data-stu-id="19140-410">TypeName</span></span>|<span data-ttu-id="19140-411">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="19140-411">win:UnicodeString</span></span>|<span data-ttu-id="19140-412">Nazwa przydzieloną typ.</span><span class="sxs-lookup"><span data-stu-id="19140-412">The name of the type that was allocated.</span></span> <span data-ttu-id="19140-413">Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to typ ostatniego przydzielono obiektu (obiektu, który spowodował przekroczenie 100 KB).</span><span class="sxs-lookup"><span data-stu-id="19140-413">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="19140-414">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="19140-414">HeapIndex</span></span>|<span data-ttu-id="19140-415">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-415">win:UInt32</span></span>|<span data-ttu-id="19140-416">Sterta, do której został przydzielony obiekt.</span><span class="sxs-lookup"><span data-stu-id="19140-416">The heap where the object was allocated.</span></span> <span data-ttu-id="19140-417">Ta wartość jest równa 0 (zero) podczas uruchamiania z odzyskiwaniem pamięci stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="19140-417">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="19140-418">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="19140-418">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="19140-419">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-419">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-420">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-420">Keyword for raising the event</span></span>|<span data-ttu-id="19140-421">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-421">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-422">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-422">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-423">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-423">Informational (4)</span></span>|

<span data-ttu-id="19140-424">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-424">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-425">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-425">Event</span></span>|<span data-ttu-id="19140-426">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-426">Event ID</span></span>|<span data-ttu-id="19140-427">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-427">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="19140-428">14</span><span class="sxs-lookup"><span data-stu-id="19140-428">14</span></span>|<span data-ttu-id="19140-429">Początek uruchamiania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="19140-429">The start of running finalizers.</span></span>|

<span data-ttu-id="19140-430">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19140-430">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="19140-431">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="19140-431">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="19140-432">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-432">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-433">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-433">Keyword for raising the event</span></span>|<span data-ttu-id="19140-434">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-435">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-435">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-436">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-436">Informational (4)</span></span>|

<span data-ttu-id="19140-437">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-437">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-438">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-438">Event</span></span>|<span data-ttu-id="19140-439">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-439">Event ID</span></span>|<span data-ttu-id="19140-440">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-440">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="19140-441">13</span><span class="sxs-lookup"><span data-stu-id="19140-441">13</span></span>|<span data-ttu-id="19140-442">Koniec uruchomionych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="19140-442">The end of running finalizers.</span></span>|

<span data-ttu-id="19140-443">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="19140-443">The following table shows the event data:</span></span>

|<span data-ttu-id="19140-444">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="19140-444">Field name</span></span>|<span data-ttu-id="19140-445">Typ danych</span><span class="sxs-lookup"><span data-stu-id="19140-445">Data type</span></span>|<span data-ttu-id="19140-446">Opis</span><span class="sxs-lookup"><span data-stu-id="19140-446">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="19140-447">Liczba</span><span class="sxs-lookup"><span data-stu-id="19140-447">Count</span></span>|<span data-ttu-id="19140-448">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="19140-448">win:UInt32</span></span>|<span data-ttu-id="19140-449">Liczba uruchomionych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="19140-449">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="19140-450">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19140-450">ClrInstanceID</span></span>|<span data-ttu-id="19140-451">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="19140-451">win:UInt16</span></span>|<span data-ttu-id="19140-452">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19140-452">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="19140-453">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="19140-453">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="19140-454">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-454">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-455">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-455">Keyword for raising the event</span></span>|<span data-ttu-id="19140-456">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-456">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-457">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-457">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-458">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-458">Informational (4)</span></span>|
|<span data-ttu-id="19140-459">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="19140-459">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="19140-460">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-460">Informational (4)</span></span>|

<span data-ttu-id="19140-461">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-461">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-462">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-462">Event</span></span>|<span data-ttu-id="19140-463">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-463">Event ID</span></span>|<span data-ttu-id="19140-464">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-464">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="19140-465">11</span><span class="sxs-lookup"><span data-stu-id="19140-465">11</span></span>|<span data-ttu-id="19140-466">Utworzono wątek współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="19140-466">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="19140-467">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19140-467">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="19140-468">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="19140-468">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="19140-469">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="19140-469">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="19140-470">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-470">Keyword for raising the event</span></span>|<span data-ttu-id="19140-471">Poziom</span><span class="sxs-lookup"><span data-stu-id="19140-471">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="19140-472">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="19140-472">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="19140-473">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-473">Informational (4)</span></span>|
|<span data-ttu-id="19140-474">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="19140-474">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="19140-475">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="19140-475">Informational (4)</span></span>|

<span data-ttu-id="19140-476">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="19140-476">The following table shows the event information:</span></span>

|<span data-ttu-id="19140-477">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="19140-477">Event</span></span>|<span data-ttu-id="19140-478">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19140-478">Event ID</span></span>|<span data-ttu-id="19140-479">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="19140-479">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="19140-480">12</span><span class="sxs-lookup"><span data-stu-id="19140-480">12</span></span>|<span data-ttu-id="19140-481">Wątek współbieżnego wyrzucania elementów bezużytecznych został zakończony.</span><span class="sxs-lookup"><span data-stu-id="19140-481">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="19140-482">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19140-482">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="19140-483">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19140-483">See also</span></span>

- [<span data-ttu-id="19140-484">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="19140-484">CLR ETW Events</span></span>](clr-etw-events.md)
