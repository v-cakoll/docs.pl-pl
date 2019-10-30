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
ms.openlocfilehash: cd4a4699f115c5b134ea60e703607ff36c229a78
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040585"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="f1445-102">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="f1445-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="f1445-103">Te zdarzenia zbierają informacje dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="f1445-104">Ułatwiają one diagnostykę i debugowanie, w tym określanie, ile razy zostało wykonane wyrzucanie elementów bezużytecznych, ilości pamięci, która została zwolniona podczas odzyskiwania pamięci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f1445-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="f1445-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="f1445-106">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="f1445-107">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="f1445-108">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="f1445-109">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="f1445-110">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="f1445-111">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="f1445-112">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="f1445-113">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="f1445-114">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="f1445-115">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="f1445-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="f1445-116">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="f1445-117">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="f1445-118">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="f1445-119">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="f1445-120">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="f1445-121">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="f1445-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="f1445-122">Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f1445-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="f1445-123">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-123">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-124">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-126">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-126">Informational (4)</span></span>|

<span data-ttu-id="f1445-127">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-127">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-128">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-128">Event</span></span>|<span data-ttu-id="f1445-129">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-129">Event ID</span></span>|<span data-ttu-id="f1445-130">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="f1445-131">1</span><span class="sxs-lookup"><span data-stu-id="f1445-131">1</span></span>|<span data-ttu-id="f1445-132">Rozpoczęto odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="f1445-132">A garbage collection has started.</span></span>|

<span data-ttu-id="f1445-133">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-133">The following table shows the event data:</span></span>

|<span data-ttu-id="f1445-134">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f1445-134">Field name</span></span>|<span data-ttu-id="f1445-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f1445-135">Data type</span></span>|<span data-ttu-id="f1445-136">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="f1445-137">Liczbą</span><span class="sxs-lookup"><span data-stu-id="f1445-137">Count</span></span>|<span data-ttu-id="f1445-138">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-138">win:UInt32</span></span>|<span data-ttu-id="f1445-139">*N*-ta kolekcja elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="f1445-140">Ścisł</span><span class="sxs-lookup"><span data-stu-id="f1445-140">Depth</span></span>|<span data-ttu-id="f1445-141">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-141">win:UInt32</span></span>|<span data-ttu-id="f1445-142">Generacja, która jest zbierana.</span><span class="sxs-lookup"><span data-stu-id="f1445-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="f1445-143">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f1445-143">Reason</span></span>|<span data-ttu-id="f1445-144">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-144">win:UInt32</span></span>|<span data-ttu-id="f1445-145">Dlaczego wyzwolono wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="f1445-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="f1445-146">0x0 — alokacja sterty dla małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1445-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="f1445-147">Wywołano 0x1.</span><span class="sxs-lookup"><span data-stu-id="f1445-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="f1445-148">0x2 — mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="f1445-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="f1445-149">0x3 — puste.</span><span class="sxs-lookup"><span data-stu-id="f1445-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="f1445-150">0x4 — alokacja sterty dla dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1445-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="f1445-151">0x5 — brak miejsca (dla sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="f1445-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="f1445-152">0x6 — brak miejsca (dla sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="f1445-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="f1445-153">0x7 — wywołano, ale nie wymuszono blokowania.</span><span class="sxs-lookup"><span data-stu-id="f1445-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="f1445-154">Typ</span><span class="sxs-lookup"><span data-stu-id="f1445-154">Type</span></span>|<span data-ttu-id="f1445-155">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-155">win:UInt32</span></span>|<span data-ttu-id="f1445-156">0x0 — blokowanie odzyskiwania pamięci wystąpiło poza odzyskiwaniem pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="f1445-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="f1445-157">0x1 — wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="f1445-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="f1445-158">0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpiło podczas odzyskiwania pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="f1445-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="f1445-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f1445-159">ClrInstanceID</span></span>|<span data-ttu-id="f1445-160">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-160">win:UInt16</span></span>|<span data-ttu-id="f1445-161">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f1445-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="f1445-162">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="f1445-163">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-164">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-164">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-165">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-167">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-167">Informational (4)</span></span>|

<span data-ttu-id="f1445-168">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-168">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-169">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-169">Event</span></span>|<span data-ttu-id="f1445-170">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-170">Event ID</span></span>|<span data-ttu-id="f1445-171">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="f1445-172">2</span><span class="sxs-lookup"><span data-stu-id="f1445-172">2</span></span>|<span data-ttu-id="f1445-173">Wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="f1445-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="f1445-174">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-174">The following table shows the event data:</span></span>

|<span data-ttu-id="f1445-175">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f1445-175">Field name</span></span>|<span data-ttu-id="f1445-176">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f1445-176">Data type</span></span>|<span data-ttu-id="f1445-177">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="f1445-178">Liczbą</span><span class="sxs-lookup"><span data-stu-id="f1445-178">Count</span></span>|<span data-ttu-id="f1445-179">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-179">win:UInt32</span></span>|<span data-ttu-id="f1445-180">*N*-ta kolekcja elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="f1445-181">Ścisł</span><span class="sxs-lookup"><span data-stu-id="f1445-181">Depth</span></span>|<span data-ttu-id="f1445-182">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-182">win:UInt32</span></span>|<span data-ttu-id="f1445-183">Generacja, która została zebrana.</span><span class="sxs-lookup"><span data-stu-id="f1445-183">The generation that was collected.</span></span>|
|<span data-ttu-id="f1445-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f1445-184">ClrInstanceID</span></span>|<span data-ttu-id="f1445-185">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-185">win:UInt16</span></span>|<span data-ttu-id="f1445-186">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f1445-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="f1445-187">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="f1445-188">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-189">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-189">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-190">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-192">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-192">Informational (4)</span></span>|

<span data-ttu-id="f1445-193">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-193">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-194">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-194">Event</span></span>|<span data-ttu-id="f1445-195">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-195">Event ID</span></span>|<span data-ttu-id="f1445-196">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="f1445-197">4</span><span class="sxs-lookup"><span data-stu-id="f1445-197">4</span></span>|<span data-ttu-id="f1445-198">Pokazuje statystyki sterty na końcu każdego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="f1445-199">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-199">The following table shows the event data:</span></span>

|<span data-ttu-id="f1445-200">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f1445-200">Field name</span></span>|<span data-ttu-id="f1445-201">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f1445-201">Data type</span></span>|<span data-ttu-id="f1445-202">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="f1445-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="f1445-203">GenerationSize0</span></span>|<span data-ttu-id="f1445-204">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-204">win:UInt64</span></span>|<span data-ttu-id="f1445-205">Rozmiar (w bajtach) pamięci generacji 0.</span><span class="sxs-lookup"><span data-stu-id="f1445-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="f1445-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="f1445-206">TotalPromotedSize0</span></span>|<span data-ttu-id="f1445-207">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-207">win:UInt64</span></span>|<span data-ttu-id="f1445-208">Liczba bajtów, które są podwyższane z generacji 0 do generacji 1.</span><span class="sxs-lookup"><span data-stu-id="f1445-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="f1445-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="f1445-209">GenerationSize1</span></span>|<span data-ttu-id="f1445-210">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-210">win:UInt64</span></span>|<span data-ttu-id="f1445-211">Rozmiar (w bajtach) pamięci pierwszej generacji 1.</span><span class="sxs-lookup"><span data-stu-id="f1445-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="f1445-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="f1445-212">TotalPromotedSize1</span></span>|<span data-ttu-id="f1445-213">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-213">win:UInt64</span></span>|<span data-ttu-id="f1445-214">Liczba bajtów, które są podwyższane z generacji 1 do generacji 2.</span><span class="sxs-lookup"><span data-stu-id="f1445-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="f1445-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="f1445-215">GenerationSize2</span></span>|<span data-ttu-id="f1445-216">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-216">win:UInt64</span></span>|<span data-ttu-id="f1445-217">Rozmiar (w bajtach) pamięci podnoszącej 2 generacji.</span><span class="sxs-lookup"><span data-stu-id="f1445-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="f1445-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="f1445-218">TotalPromotedSize2</span></span>|<span data-ttu-id="f1445-219">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-219">win:UInt64</span></span>|<span data-ttu-id="f1445-220">Liczba bajtów, które przeżyły w generacji 2 po ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f1445-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="f1445-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="f1445-221">GenerationSize3</span></span>|<span data-ttu-id="f1445-222">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-222">win:UInt64</span></span>|<span data-ttu-id="f1445-223">Rozmiar sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f1445-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="f1445-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="f1445-224">TotalPromotedSize3</span></span>|<span data-ttu-id="f1445-225">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-225">win:UInt64</span></span>|<span data-ttu-id="f1445-226">Liczba bajtów przeczytanych z sterty dużego obiektu po ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f1445-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="f1445-227">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="f1445-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="f1445-228">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-228">win:UInt64</span></span>|<span data-ttu-id="f1445-229">Łączny rozmiar (w bajtach) obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="f1445-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="f1445-230">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="f1445-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="f1445-231">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-231">win:UInt64</span></span>|<span data-ttu-id="f1445-232">Liczba obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="f1445-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="f1445-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="f1445-233">PinnedObjectCount</span></span>|<span data-ttu-id="f1445-234">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-234">win:UInt32</span></span>|<span data-ttu-id="f1445-235">Liczba przypiętych (nieruchomych) obiektów.</span><span class="sxs-lookup"><span data-stu-id="f1445-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="f1445-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="f1445-236">SinkBlockCount</span></span>|<span data-ttu-id="f1445-237">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-237">win:UInt32</span></span>|<span data-ttu-id="f1445-238">Liczba bloków synchronizacji w użyciu.</span><span class="sxs-lookup"><span data-stu-id="f1445-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="f1445-239">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="f1445-239">GCHandleCount</span></span>|<span data-ttu-id="f1445-240">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-240">win:UInt32</span></span>|<span data-ttu-id="f1445-241">Liczba dojść do wyrzucania elementów bezużytecznych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="f1445-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="f1445-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f1445-242">ClrInstanceID</span></span>|<span data-ttu-id="f1445-243">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-243">win:UInt16</span></span>|<span data-ttu-id="f1445-244">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f1445-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="f1445-245">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="f1445-246">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-247">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-247">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-248">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-250">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-250">Informational (4)</span></span>|

<span data-ttu-id="f1445-251">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-251">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-252">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-252">Event</span></span>|<span data-ttu-id="f1445-253">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-253">Event ID</span></span>|<span data-ttu-id="f1445-254">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="f1445-255">5</span><span class="sxs-lookup"><span data-stu-id="f1445-255">5</span></span>|<span data-ttu-id="f1445-256">Utworzono nowy segment wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="f1445-257">Ponadto po włączeniu śledzenia dla procesu, który jest już uruchomiony, to zdarzenie jest zgłaszane dla każdego istniejącego segmentu.</span><span class="sxs-lookup"><span data-stu-id="f1445-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="f1445-258">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-258">The following table shows the event data:</span></span>

|<span data-ttu-id="f1445-259">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f1445-259">Field name</span></span>|<span data-ttu-id="f1445-260">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f1445-260">Data type</span></span>|<span data-ttu-id="f1445-261">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="f1445-262">Ulica</span><span class="sxs-lookup"><span data-stu-id="f1445-262">Address</span></span>|<span data-ttu-id="f1445-263">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-263">win:UInt64</span></span>|<span data-ttu-id="f1445-264">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="f1445-264">The address of the segment.</span></span>|
|<span data-ttu-id="f1445-265">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="f1445-265">Size</span></span>|<span data-ttu-id="f1445-266">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-266">win:UInt64</span></span>|<span data-ttu-id="f1445-267">Rozmiar segmentu.</span><span class="sxs-lookup"><span data-stu-id="f1445-267">The size of the segment.</span></span>|
|<span data-ttu-id="f1445-268">Typ</span><span class="sxs-lookup"><span data-stu-id="f1445-268">Type</span></span>|<span data-ttu-id="f1445-269">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-269">win:UInt32</span></span>|<span data-ttu-id="f1445-270">0x0 — sterta małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1445-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="f1445-271">0x1 — sterta dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1445-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="f1445-272">0x2 — sterta tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="f1445-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="f1445-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f1445-273">ClrInstanceID</span></span>|<span data-ttu-id="f1445-274">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-274">win:UInt16</span></span>|<span data-ttu-id="f1445-275">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f1445-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="f1445-276">Należy zauważyć, że rozmiar segmentów przydzielone przez moduł wyrzucania elementów bezużytecznych jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami.</span><span class="sxs-lookup"><span data-stu-id="f1445-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="f1445-277">Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="f1445-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="f1445-278">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="f1445-279">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-280">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-280">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-281">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-283">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-283">Informational (4)</span></span>|

<span data-ttu-id="f1445-284">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-284">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-285">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-285">Event</span></span>|<span data-ttu-id="f1445-286">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-286">Event ID</span></span>|<span data-ttu-id="f1445-287">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="f1445-288">6</span><span class="sxs-lookup"><span data-stu-id="f1445-288">6</span></span>|<span data-ttu-id="f1445-289">Wydano segment wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="f1445-290">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-290">The following table shows the event data:</span></span>

|<span data-ttu-id="f1445-291">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f1445-291">Field name</span></span>|<span data-ttu-id="f1445-292">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f1445-292">Data type</span></span>|<span data-ttu-id="f1445-293">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="f1445-294">Ulica</span><span class="sxs-lookup"><span data-stu-id="f1445-294">Address</span></span>|<span data-ttu-id="f1445-295">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-295">win:UInt64</span></span>|<span data-ttu-id="f1445-296">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="f1445-296">The address of the segment.</span></span>|
|<span data-ttu-id="f1445-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f1445-297">ClrInstanceID</span></span>|<span data-ttu-id="f1445-298">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-298">win:UInt16</span></span>|<span data-ttu-id="f1445-299">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f1445-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="f1445-300">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="f1445-301">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-302">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-302">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-303">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-305">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-305">Informational (4)</span></span>|

<span data-ttu-id="f1445-306">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-306">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-307">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-307">Event</span></span>|<span data-ttu-id="f1445-308">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-308">Event ID</span></span>|<span data-ttu-id="f1445-309">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="f1445-310">7</span><span class="sxs-lookup"><span data-stu-id="f1445-310">7</span></span>|<span data-ttu-id="f1445-311">Rozpoczęto wznawianie od zawieszenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f1445-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="f1445-312">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f1445-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="f1445-313">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="f1445-314">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-315">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-315">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-316">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-318">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-318">Informational (4)</span></span>|

<span data-ttu-id="f1445-319">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-319">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-320">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-320">Event</span></span>|<span data-ttu-id="f1445-321">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-321">Event Id</span></span>|<span data-ttu-id="f1445-322">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="f1445-323">3</span><span class="sxs-lookup"><span data-stu-id="f1445-323">3</span></span>|<span data-ttu-id="f1445-324">Zakończono wznawianie z zawieszenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f1445-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="f1445-325">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f1445-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="f1445-326">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="f1445-327">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-328">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-328">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-329">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-331">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-331">Informational (4)</span></span>|

<span data-ttu-id="f1445-332">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-332">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-333">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-333">Event</span></span>|<span data-ttu-id="f1445-334">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-334">Event ID</span></span>|<span data-ttu-id="f1445-335">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="f1445-336">9</span><span class="sxs-lookup"><span data-stu-id="f1445-336">9</span></span>|<span data-ttu-id="f1445-337">Początek zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="f1445-338">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-338">The following table shows the event data:</span></span>

|<span data-ttu-id="f1445-339">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f1445-339">Field name</span></span>|<span data-ttu-id="f1445-340">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f1445-340">Data type</span></span>|<span data-ttu-id="f1445-341">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="f1445-342">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f1445-342">Reason</span></span>|<span data-ttu-id="f1445-343">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-343">win:UInt16</span></span>|<span data-ttu-id="f1445-344">0x0 — inne.</span><span class="sxs-lookup"><span data-stu-id="f1445-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="f1445-345">0x1 — odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="f1445-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="f1445-346">0x2 — zamknięcie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1445-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="f1445-347">0x3 — nachylenie kodu.</span><span class="sxs-lookup"><span data-stu-id="f1445-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="f1445-348">0x4 — zamykanie.</span><span class="sxs-lookup"><span data-stu-id="f1445-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="f1445-349">0x5 — debuger.</span><span class="sxs-lookup"><span data-stu-id="f1445-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="f1445-350">0x6 — przygotowanie do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="f1445-351">Liczbą</span><span class="sxs-lookup"><span data-stu-id="f1445-351">Count</span></span>|<span data-ttu-id="f1445-352">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-352">win:UInt32</span></span>|<span data-ttu-id="f1445-353">Liczba GC w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="f1445-353">The GC count at the time.</span></span> <span data-ttu-id="f1445-354">Zwykle po wykonaniu tej operacji zobaczysz kolejne zdarzenie uruchomienia GC, a jego liczba jest taka sama jak liczba + 1, ponieważ zwiększy indeks GC podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="f1445-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f1445-355">ClrInstanceID</span></span>|<span data-ttu-id="f1445-356">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-356">win:UInt16</span></span>|<span data-ttu-id="f1445-357">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f1445-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="f1445-358">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="f1445-359">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-360">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-360">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-361">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-363">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-363">Informational (4)</span></span>|

<span data-ttu-id="f1445-364">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-364">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-365">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-365">Event</span></span>|<span data-ttu-id="f1445-366">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-366">Event ID</span></span>|<span data-ttu-id="f1445-367">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="f1445-368">8</span><span class="sxs-lookup"><span data-stu-id="f1445-368">8</span></span>|<span data-ttu-id="f1445-369">Koniec zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="f1445-370">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f1445-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="f1445-371">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="f1445-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="f1445-372">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-373">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-373">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-374">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-376">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-376">Informational (4)</span></span>|

<span data-ttu-id="f1445-377">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-377">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-378">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-378">Event</span></span>|<span data-ttu-id="f1445-379">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-379">Event ID</span></span>|<span data-ttu-id="f1445-380">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="f1445-381">10</span><span class="sxs-lookup"><span data-stu-id="f1445-381">10</span></span>|<span data-ttu-id="f1445-382">Za każdym razem przydzielono około 100 KB.</span><span class="sxs-lookup"><span data-stu-id="f1445-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="f1445-383">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-383">The following table shows the event data:</span></span>

|<span data-ttu-id="f1445-384">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f1445-384">Field name</span></span>|<span data-ttu-id="f1445-385">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f1445-385">Data type</span></span>|<span data-ttu-id="f1445-386">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="f1445-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="f1445-387">AllocationAmount</span></span>|<span data-ttu-id="f1445-388">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-388">win:UInt32</span></span>|<span data-ttu-id="f1445-389">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f1445-389">The allocation size, in bytes.</span></span> <span data-ttu-id="f1445-390">Ta wartość jest dokładna dla przydziałów, które są mniejsze niż długość ULONG (4 294 967 295 bajtów).</span><span class="sxs-lookup"><span data-stu-id="f1445-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="f1445-391">Jeśli alokacja jest większa, to pole zawiera obciętą wartość.</span><span class="sxs-lookup"><span data-stu-id="f1445-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="f1445-392">Użyj `AllocationAmount64` dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="f1445-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="f1445-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="f1445-393">AllocationKind</span></span>|<span data-ttu-id="f1445-394">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-394">win:UInt32</span></span>|<span data-ttu-id="f1445-395">0x0 — alokacja małego obiektu (alokacja jest w ramach sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="f1445-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="f1445-396">0x1 — alokacja dużego obiektu (alokacja jest w sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="f1445-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="f1445-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f1445-397">ClrInstanceID</span></span>|<span data-ttu-id="f1445-398">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-398">win:UInt16</span></span>|<span data-ttu-id="f1445-399">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f1445-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="f1445-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="f1445-400">AllocationAmount64</span></span>|<span data-ttu-id="f1445-401">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="f1445-401">win:UInt64</span></span>|<span data-ttu-id="f1445-402">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f1445-402">The allocation size, in bytes.</span></span> <span data-ttu-id="f1445-403">Ta wartość jest dokładna dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="f1445-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="f1445-404">Parametru</span><span class="sxs-lookup"><span data-stu-id="f1445-404">TypeId</span></span>|<span data-ttu-id="f1445-405">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="f1445-405">win:Pointer</span></span>|<span data-ttu-id="f1445-406">Adres metody.</span><span class="sxs-lookup"><span data-stu-id="f1445-406">The address of the MethodTable.</span></span> <span data-ttu-id="f1445-407">Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to adres metody, która odnosi się do ostatniego przydzielony obiekt (obiekt, który spowodował przekroczenie 100 KB progu).</span><span class="sxs-lookup"><span data-stu-id="f1445-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="f1445-408">TypeName</span><span class="sxs-lookup"><span data-stu-id="f1445-408">TypeName</span></span>|<span data-ttu-id="f1445-409">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f1445-409">win:UnicodeString</span></span>|<span data-ttu-id="f1445-410">Nazwa przydzieloną typ.</span><span class="sxs-lookup"><span data-stu-id="f1445-410">The name of the type that was allocated.</span></span> <span data-ttu-id="f1445-411">Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to typ ostatniego przydzielono obiektu (obiektu, który spowodował przekroczenie 100 KB).</span><span class="sxs-lookup"><span data-stu-id="f1445-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="f1445-412">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="f1445-412">HeapIndex</span></span>|<span data-ttu-id="f1445-413">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-413">win:UInt32</span></span>|<span data-ttu-id="f1445-414">Sterta, do której został przydzielony obiekt.</span><span class="sxs-lookup"><span data-stu-id="f1445-414">The heap where the object was allocated.</span></span> <span data-ttu-id="f1445-415">Ta wartość jest równa 0 (zero) podczas uruchamiania z odzyskiwaniem pamięci stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="f1445-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="f1445-416">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="f1445-417">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-418">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-418">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-419">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-421">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-421">Informational (4)</span></span>|

<span data-ttu-id="f1445-422">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-422">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-423">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-423">Event</span></span>|<span data-ttu-id="f1445-424">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-424">Event ID</span></span>|<span data-ttu-id="f1445-425">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="f1445-426">14,5</span><span class="sxs-lookup"><span data-stu-id="f1445-426">14</span></span>|<span data-ttu-id="f1445-427">Początek uruchamiania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="f1445-427">The start of running finalizers.</span></span>|

<span data-ttu-id="f1445-428">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f1445-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="f1445-429">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="f1445-430">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-431">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-431">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-432">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-434">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-434">Informational (4)</span></span>|

<span data-ttu-id="f1445-435">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-435">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-436">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-436">Event</span></span>|<span data-ttu-id="f1445-437">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-437">Event ID</span></span>|<span data-ttu-id="f1445-438">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="f1445-439">13</span><span class="sxs-lookup"><span data-stu-id="f1445-439">13</span></span>|<span data-ttu-id="f1445-440">Koniec uruchomionych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="f1445-440">The end of running finalizers.</span></span>|

<span data-ttu-id="f1445-441">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f1445-441">The following table shows the event data:</span></span>

|<span data-ttu-id="f1445-442">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f1445-442">Field name</span></span>|<span data-ttu-id="f1445-443">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f1445-443">Data type</span></span>|<span data-ttu-id="f1445-444">Opis</span><span class="sxs-lookup"><span data-stu-id="f1445-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="f1445-445">Liczbą</span><span class="sxs-lookup"><span data-stu-id="f1445-445">Count</span></span>|<span data-ttu-id="f1445-446">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f1445-446">win:UInt32</span></span>|<span data-ttu-id="f1445-447">Liczba uruchomionych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="f1445-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="f1445-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f1445-448">ClrInstanceID</span></span>|<span data-ttu-id="f1445-449">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f1445-449">win:UInt16</span></span>|<span data-ttu-id="f1445-450">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f1445-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="f1445-451">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="f1445-452">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-453">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-453">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-454">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-456">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-456">Informational (4)</span></span>|
|<span data-ttu-id="f1445-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f1445-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f1445-458">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-458">Informational (4)</span></span>|

<span data-ttu-id="f1445-459">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-459">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-460">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-460">Event</span></span>|<span data-ttu-id="f1445-461">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-461">Event ID</span></span>|<span data-ttu-id="f1445-462">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="f1445-463">11</span><span class="sxs-lookup"><span data-stu-id="f1445-463">11</span></span>|<span data-ttu-id="f1445-464">Utworzono wątek współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f1445-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="f1445-465">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f1445-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="f1445-466">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="f1445-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="f1445-467">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="f1445-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="f1445-468">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-468">Keyword for raising the event</span></span>|<span data-ttu-id="f1445-469">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1445-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="f1445-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f1445-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f1445-471">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-471">Informational (4)</span></span>|
|<span data-ttu-id="f1445-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f1445-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f1445-473">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="f1445-473">Informational (4)</span></span>|

<span data-ttu-id="f1445-474">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="f1445-474">The following table shows the event information:</span></span>

|<span data-ttu-id="f1445-475">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f1445-475">Event</span></span>|<span data-ttu-id="f1445-476">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f1445-476">Event ID</span></span>|<span data-ttu-id="f1445-477">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f1445-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="f1445-478">12</span><span class="sxs-lookup"><span data-stu-id="f1445-478">12</span></span>|<span data-ttu-id="f1445-479">Wątek współbieżnego wyrzucania elementów bezużytecznych został zakończony.</span><span class="sxs-lookup"><span data-stu-id="f1445-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="f1445-480">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f1445-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1445-481">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1445-481">See also</span></span>

- [<span data-ttu-id="f1445-482">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="f1445-482">CLR ETW Events</span></span>](clr-etw-events.md)
