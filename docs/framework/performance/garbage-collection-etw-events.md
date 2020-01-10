---
title: Zdarzenia ETW odzyskiwania pamięci
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 5ff214314b92796f4a4a89ddd33a976d8b1f21d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716069"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="6f22c-102">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="6f22c-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="6f22c-103">Te zdarzenia zbierają informacje dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="6f22c-104">Ułatwiają one diagnostykę i debugowanie, w tym określanie, ile razy zostało wykonane wyrzucanie elementów bezużytecznych, ilości pamięci, która została zwolniona podczas odzyskiwania pamięci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6f22c-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="6f22c-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="6f22c-106">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="6f22c-107">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="6f22c-108">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="6f22c-109">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="6f22c-110">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="6f22c-111">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="6f22c-112">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="6f22c-113">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="6f22c-114">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="6f22c-115">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="6f22c-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="6f22c-116">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="6f22c-117">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="6f22c-118">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="6f22c-119">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="6f22c-120">Zdarzenie GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="6f22c-121">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="6f22c-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="6f22c-122">Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6f22c-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="6f22c-123">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-123">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-124">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-126">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-126">Informational (4)</span></span>|

<span data-ttu-id="6f22c-127">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-127">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-128">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-128">Event</span></span>|<span data-ttu-id="6f22c-129">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-129">Event ID</span></span>|<span data-ttu-id="6f22c-130">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="6f22c-131">1</span><span class="sxs-lookup"><span data-stu-id="6f22c-131">1</span></span>|<span data-ttu-id="6f22c-132">Rozpoczęto odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f22c-132">A garbage collection has started.</span></span>|

<span data-ttu-id="6f22c-133">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-133">The following table shows the event data:</span></span>

|<span data-ttu-id="6f22c-134">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="6f22c-134">Field name</span></span>|<span data-ttu-id="6f22c-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6f22c-135">Data type</span></span>|<span data-ttu-id="6f22c-136">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="6f22c-137">Count</span><span class="sxs-lookup"><span data-stu-id="6f22c-137">Count</span></span>|<span data-ttu-id="6f22c-138">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-138">win:UInt32</span></span>|<span data-ttu-id="6f22c-139">*N*-ta kolekcja elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="6f22c-140">Ścisł</span><span class="sxs-lookup"><span data-stu-id="6f22c-140">Depth</span></span>|<span data-ttu-id="6f22c-141">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-141">win:UInt32</span></span>|<span data-ttu-id="6f22c-142">Generacja, która jest zbierana.</span><span class="sxs-lookup"><span data-stu-id="6f22c-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="6f22c-143">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="6f22c-143">Reason</span></span>|<span data-ttu-id="6f22c-144">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-144">win:UInt32</span></span>|<span data-ttu-id="6f22c-145">Dlaczego wyzwolono wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="6f22c-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="6f22c-146">0x0 — alokacja sterty dla małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="6f22c-147">Wywołano 0x1.</span><span class="sxs-lookup"><span data-stu-id="6f22c-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="6f22c-148">0x2 — mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f22c-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="6f22c-149">0x3 — puste.</span><span class="sxs-lookup"><span data-stu-id="6f22c-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="6f22c-150">0x4 — alokacja sterty dla dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="6f22c-151">0x5 — brak miejsca (dla sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="6f22c-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="6f22c-152">0x6 — brak miejsca (dla sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="6f22c-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="6f22c-153">0x7 — wywołano, ale nie wymuszono blokowania.</span><span class="sxs-lookup"><span data-stu-id="6f22c-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="6f22c-154">Typ</span><span class="sxs-lookup"><span data-stu-id="6f22c-154">Type</span></span>|<span data-ttu-id="6f22c-155">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-155">win:UInt32</span></span>|<span data-ttu-id="6f22c-156">0x0 — blokowanie odzyskiwania pamięci wystąpiło poza odzyskiwaniem pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="6f22c-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="6f22c-157">0x1 — wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="6f22c-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="6f22c-158">0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpiło podczas odzyskiwania pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="6f22c-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="6f22c-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f22c-159">ClrInstanceID</span></span>|<span data-ttu-id="6f22c-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-160">win:UInt16</span></span>|<span data-ttu-id="6f22c-161">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6f22c-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="6f22c-162">Zdarzenie GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="6f22c-163">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-164">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-164">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-165">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-167">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-167">Informational (4)</span></span>|

<span data-ttu-id="6f22c-168">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-168">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-169">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-169">Event</span></span>|<span data-ttu-id="6f22c-170">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-170">Event ID</span></span>|<span data-ttu-id="6f22c-171">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="6f22c-172">2</span><span class="sxs-lookup"><span data-stu-id="6f22c-172">2</span></span>|<span data-ttu-id="6f22c-173">Wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="6f22c-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="6f22c-174">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-174">The following table shows the event data:</span></span>

|<span data-ttu-id="6f22c-175">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="6f22c-175">Field name</span></span>|<span data-ttu-id="6f22c-176">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6f22c-176">Data type</span></span>|<span data-ttu-id="6f22c-177">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="6f22c-178">Count</span><span class="sxs-lookup"><span data-stu-id="6f22c-178">Count</span></span>|<span data-ttu-id="6f22c-179">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-179">win:UInt32</span></span>|<span data-ttu-id="6f22c-180">*N*-ta kolekcja elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="6f22c-181">Ścisł</span><span class="sxs-lookup"><span data-stu-id="6f22c-181">Depth</span></span>|<span data-ttu-id="6f22c-182">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-182">win:UInt32</span></span>|<span data-ttu-id="6f22c-183">Generacja, która została zebrana.</span><span class="sxs-lookup"><span data-stu-id="6f22c-183">The generation that was collected.</span></span>|
|<span data-ttu-id="6f22c-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f22c-184">ClrInstanceID</span></span>|<span data-ttu-id="6f22c-185">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-185">win:UInt16</span></span>|<span data-ttu-id="6f22c-186">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6f22c-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="6f22c-187">Zdarzenie GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="6f22c-188">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-189">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-189">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-190">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-192">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-192">Informational (4)</span></span>|

<span data-ttu-id="6f22c-193">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-193">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-194">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-194">Event</span></span>|<span data-ttu-id="6f22c-195">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-195">Event ID</span></span>|<span data-ttu-id="6f22c-196">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="6f22c-197">4</span><span class="sxs-lookup"><span data-stu-id="6f22c-197">4</span></span>|<span data-ttu-id="6f22c-198">Pokazuje statystyki sterty na końcu każdego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="6f22c-199">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-199">The following table shows the event data:</span></span>

|<span data-ttu-id="6f22c-200">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="6f22c-200">Field name</span></span>|<span data-ttu-id="6f22c-201">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6f22c-201">Data type</span></span>|<span data-ttu-id="6f22c-202">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="6f22c-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="6f22c-203">GenerationSize0</span></span>|<span data-ttu-id="6f22c-204">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-204">win:UInt64</span></span>|<span data-ttu-id="6f22c-205">Rozmiar (w bajtach) pamięci generacji 0.</span><span class="sxs-lookup"><span data-stu-id="6f22c-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="6f22c-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="6f22c-206">TotalPromotedSize0</span></span>|<span data-ttu-id="6f22c-207">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-207">win:UInt64</span></span>|<span data-ttu-id="6f22c-208">Liczba bajtów, które są podwyższane z generacji 0 do generacji 1.</span><span class="sxs-lookup"><span data-stu-id="6f22c-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="6f22c-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="6f22c-209">GenerationSize1</span></span>|<span data-ttu-id="6f22c-210">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-210">win:UInt64</span></span>|<span data-ttu-id="6f22c-211">Rozmiar (w bajtach) pamięci pierwszej generacji 1.</span><span class="sxs-lookup"><span data-stu-id="6f22c-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="6f22c-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="6f22c-212">TotalPromotedSize1</span></span>|<span data-ttu-id="6f22c-213">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-213">win:UInt64</span></span>|<span data-ttu-id="6f22c-214">Liczba bajtów, które są podwyższane z generacji 1 do generacji 2.</span><span class="sxs-lookup"><span data-stu-id="6f22c-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="6f22c-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="6f22c-215">GenerationSize2</span></span>|<span data-ttu-id="6f22c-216">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-216">win:UInt64</span></span>|<span data-ttu-id="6f22c-217">Rozmiar (w bajtach) pamięci podnoszącej 2 generacji.</span><span class="sxs-lookup"><span data-stu-id="6f22c-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="6f22c-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="6f22c-218">TotalPromotedSize2</span></span>|<span data-ttu-id="6f22c-219">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-219">win:UInt64</span></span>|<span data-ttu-id="6f22c-220">Liczba bajtów, które przeżyły w generacji 2 po ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6f22c-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="6f22c-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="6f22c-221">GenerationSize3</span></span>|<span data-ttu-id="6f22c-222">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-222">win:UInt64</span></span>|<span data-ttu-id="6f22c-223">Rozmiar sterty dużego obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="6f22c-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="6f22c-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="6f22c-224">TotalPromotedSize3</span></span>|<span data-ttu-id="6f22c-225">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-225">win:UInt64</span></span>|<span data-ttu-id="6f22c-226">Liczba bajtów przeczytanych z sterty dużego obiektu po ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6f22c-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="6f22c-227">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="6f22c-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="6f22c-228">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-228">win:UInt64</span></span>|<span data-ttu-id="6f22c-229">Łączny rozmiar (w bajtach) obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="6f22c-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="6f22c-230">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="6f22c-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="6f22c-231">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-231">win:UInt64</span></span>|<span data-ttu-id="6f22c-232">Liczba obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="6f22c-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="6f22c-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="6f22c-233">PinnedObjectCount</span></span>|<span data-ttu-id="6f22c-234">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-234">win:UInt32</span></span>|<span data-ttu-id="6f22c-235">Liczba przypiętych (nieruchomych) obiektów.</span><span class="sxs-lookup"><span data-stu-id="6f22c-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="6f22c-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="6f22c-236">SinkBlockCount</span></span>|<span data-ttu-id="6f22c-237">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-237">win:UInt32</span></span>|<span data-ttu-id="6f22c-238">Liczba bloków synchronizacji w użyciu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="6f22c-239">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="6f22c-239">GCHandleCount</span></span>|<span data-ttu-id="6f22c-240">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-240">win:UInt32</span></span>|<span data-ttu-id="6f22c-241">Liczba dojść do wyrzucania elementów bezużytecznych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="6f22c-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f22c-242">ClrInstanceID</span></span>|<span data-ttu-id="6f22c-243">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-243">win:UInt16</span></span>|<span data-ttu-id="6f22c-244">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6f22c-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="6f22c-245">Zdarzenie GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="6f22c-246">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-247">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-247">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-248">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-250">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-250">Informational (4)</span></span>|

<span data-ttu-id="6f22c-251">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-251">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-252">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-252">Event</span></span>|<span data-ttu-id="6f22c-253">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-253">Event ID</span></span>|<span data-ttu-id="6f22c-254">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="6f22c-255">5</span><span class="sxs-lookup"><span data-stu-id="6f22c-255">5</span></span>|<span data-ttu-id="6f22c-256">Utworzono nowy segment wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="6f22c-257">Ponadto po włączeniu śledzenia dla procesu, który jest już uruchomiony, to zdarzenie jest zgłaszane dla każdego istniejącego segmentu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="6f22c-258">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-258">The following table shows the event data:</span></span>

|<span data-ttu-id="6f22c-259">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="6f22c-259">Field name</span></span>|<span data-ttu-id="6f22c-260">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6f22c-260">Data type</span></span>|<span data-ttu-id="6f22c-261">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="6f22c-262">Adres</span><span class="sxs-lookup"><span data-stu-id="6f22c-262">Address</span></span>|<span data-ttu-id="6f22c-263">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-263">win:UInt64</span></span>|<span data-ttu-id="6f22c-264">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-264">The address of the segment.</span></span>|
|<span data-ttu-id="6f22c-265">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="6f22c-265">Size</span></span>|<span data-ttu-id="6f22c-266">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-266">win:UInt64</span></span>|<span data-ttu-id="6f22c-267">Rozmiar segmentu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-267">The size of the segment.</span></span>|
|<span data-ttu-id="6f22c-268">Typ</span><span class="sxs-lookup"><span data-stu-id="6f22c-268">Type</span></span>|<span data-ttu-id="6f22c-269">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-269">win:UInt32</span></span>|<span data-ttu-id="6f22c-270">0x0 — sterta małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="6f22c-271">0x1 — sterta dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="6f22c-272">0x2 — sterta tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="6f22c-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f22c-273">ClrInstanceID</span></span>|<span data-ttu-id="6f22c-274">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-274">win:UInt16</span></span>|<span data-ttu-id="6f22c-275">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6f22c-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="6f22c-276">Należy zauważyć, że rozmiar segmentów przydzielone przez moduł wyrzucania elementów bezużytecznych jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami.</span><span class="sxs-lookup"><span data-stu-id="6f22c-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="6f22c-277">Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="6f22c-278">Zdarzenie GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="6f22c-279">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-280">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-280">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-281">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-283">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-283">Informational (4)</span></span>|

<span data-ttu-id="6f22c-284">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-284">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-285">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-285">Event</span></span>|<span data-ttu-id="6f22c-286">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-286">Event ID</span></span>|<span data-ttu-id="6f22c-287">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="6f22c-288">6</span><span class="sxs-lookup"><span data-stu-id="6f22c-288">6</span></span>|<span data-ttu-id="6f22c-289">Wydano segment wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="6f22c-290">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-290">The following table shows the event data:</span></span>

|<span data-ttu-id="6f22c-291">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="6f22c-291">Field name</span></span>|<span data-ttu-id="6f22c-292">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6f22c-292">Data type</span></span>|<span data-ttu-id="6f22c-293">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="6f22c-294">Adres</span><span class="sxs-lookup"><span data-stu-id="6f22c-294">Address</span></span>|<span data-ttu-id="6f22c-295">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-295">win:UInt64</span></span>|<span data-ttu-id="6f22c-296">Adres segmentu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-296">The address of the segment.</span></span>|
|<span data-ttu-id="6f22c-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f22c-297">ClrInstanceID</span></span>|<span data-ttu-id="6f22c-298">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-298">win:UInt16</span></span>|<span data-ttu-id="6f22c-299">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6f22c-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="6f22c-300">Zdarzenie GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="6f22c-301">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-302">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-302">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-303">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-305">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-305">Informational (4)</span></span>|

<span data-ttu-id="6f22c-306">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-306">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-307">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-307">Event</span></span>|<span data-ttu-id="6f22c-308">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-308">Event ID</span></span>|<span data-ttu-id="6f22c-309">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="6f22c-310">7</span><span class="sxs-lookup"><span data-stu-id="6f22c-310">7</span></span>|<span data-ttu-id="6f22c-311">Rozpoczęto wznawianie od zawieszenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="6f22c-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="6f22c-312">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6f22c-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="6f22c-313">Zdarzenie GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="6f22c-314">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-315">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-315">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-316">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-318">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-318">Informational (4)</span></span>|

<span data-ttu-id="6f22c-319">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-319">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-320">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-320">Event</span></span>|<span data-ttu-id="6f22c-321">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-321">Event Id</span></span>|<span data-ttu-id="6f22c-322">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="6f22c-323">3</span><span class="sxs-lookup"><span data-stu-id="6f22c-323">3</span></span>|<span data-ttu-id="6f22c-324">Zakończono wznawianie z zawieszenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="6f22c-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="6f22c-325">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6f22c-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="6f22c-326">Zdarzenie GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="6f22c-327">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-328">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-328">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-329">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-331">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-331">Informational (4)</span></span>|

<span data-ttu-id="6f22c-332">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-332">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-333">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-333">Event</span></span>|<span data-ttu-id="6f22c-334">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-334">Event ID</span></span>|<span data-ttu-id="6f22c-335">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="6f22c-336">9</span><span class="sxs-lookup"><span data-stu-id="6f22c-336">9</span></span>|<span data-ttu-id="6f22c-337">Początek zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="6f22c-338">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-338">The following table shows the event data:</span></span>

|<span data-ttu-id="6f22c-339">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="6f22c-339">Field name</span></span>|<span data-ttu-id="6f22c-340">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6f22c-340">Data type</span></span>|<span data-ttu-id="6f22c-341">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="6f22c-342">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="6f22c-342">Reason</span></span>|<span data-ttu-id="6f22c-343">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-343">win:UInt16</span></span>|<span data-ttu-id="6f22c-344">0x0 — inne.</span><span class="sxs-lookup"><span data-stu-id="6f22c-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="6f22c-345">0x1 — odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f22c-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="6f22c-346">0x2 — zamknięcie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f22c-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="6f22c-347">0x3 — nachylenie kodu.</span><span class="sxs-lookup"><span data-stu-id="6f22c-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="6f22c-348">0x4 — zamykanie.</span><span class="sxs-lookup"><span data-stu-id="6f22c-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="6f22c-349">0x5 — debuger.</span><span class="sxs-lookup"><span data-stu-id="6f22c-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="6f22c-350">0x6 — przygotowanie do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="6f22c-351">Count</span><span class="sxs-lookup"><span data-stu-id="6f22c-351">Count</span></span>|<span data-ttu-id="6f22c-352">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-352">win:UInt32</span></span>|<span data-ttu-id="6f22c-353">Liczba GC w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="6f22c-353">The GC count at the time.</span></span> <span data-ttu-id="6f22c-354">Zwykle po wykonaniu tej operacji zobaczysz kolejne zdarzenie uruchomienia GC, a jego liczba jest taka sama jak liczba + 1, ponieważ zwiększy indeks GC podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="6f22c-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f22c-355">ClrInstanceID</span></span>|<span data-ttu-id="6f22c-356">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-356">win:UInt16</span></span>|<span data-ttu-id="6f22c-357">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6f22c-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="6f22c-358">Zdarzenie GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="6f22c-359">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-360">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-360">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-361">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-363">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-363">Informational (4)</span></span>|

<span data-ttu-id="6f22c-364">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-364">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-365">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-365">Event</span></span>|<span data-ttu-id="6f22c-366">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-366">Event ID</span></span>|<span data-ttu-id="6f22c-367">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="6f22c-368">8</span><span class="sxs-lookup"><span data-stu-id="6f22c-368">8</span></span>|<span data-ttu-id="6f22c-369">Koniec zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="6f22c-370">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6f22c-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="6f22c-371">Zdarzenie GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="6f22c-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="6f22c-372">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-373">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-373">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-374">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-376">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-376">Informational (4)</span></span>|

<span data-ttu-id="6f22c-377">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-377">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-378">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-378">Event</span></span>|<span data-ttu-id="6f22c-379">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-379">Event ID</span></span>|<span data-ttu-id="6f22c-380">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="6f22c-381">10</span><span class="sxs-lookup"><span data-stu-id="6f22c-381">10</span></span>|<span data-ttu-id="6f22c-382">Za każdym razem przydzielono około 100 KB.</span><span class="sxs-lookup"><span data-stu-id="6f22c-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="6f22c-383">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-383">The following table shows the event data:</span></span>

|<span data-ttu-id="6f22c-384">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="6f22c-384">Field name</span></span>|<span data-ttu-id="6f22c-385">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6f22c-385">Data type</span></span>|<span data-ttu-id="6f22c-386">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="6f22c-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="6f22c-387">AllocationAmount</span></span>|<span data-ttu-id="6f22c-388">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-388">win:UInt32</span></span>|<span data-ttu-id="6f22c-389">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="6f22c-389">The allocation size, in bytes.</span></span> <span data-ttu-id="6f22c-390">Ta wartość jest dokładna dla przydziałów, które są mniejsze niż długość ULONG (4 294 967 295 bajtów).</span><span class="sxs-lookup"><span data-stu-id="6f22c-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="6f22c-391">Jeśli alokacja jest większa, to pole zawiera obciętą wartość.</span><span class="sxs-lookup"><span data-stu-id="6f22c-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="6f22c-392">Użyj `AllocationAmount64` dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="6f22c-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="6f22c-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="6f22c-393">AllocationKind</span></span>|<span data-ttu-id="6f22c-394">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-394">win:UInt32</span></span>|<span data-ttu-id="6f22c-395">0x0 — alokacja małego obiektu (alokacja jest w ramach sterty małego obiektu).</span><span class="sxs-lookup"><span data-stu-id="6f22c-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="6f22c-396">0x1 — alokacja dużego obiektu (alokacja jest w sterty dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="6f22c-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="6f22c-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f22c-397">ClrInstanceID</span></span>|<span data-ttu-id="6f22c-398">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-398">win:UInt16</span></span>|<span data-ttu-id="6f22c-399">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6f22c-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="6f22c-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="6f22c-400">AllocationAmount64</span></span>|<span data-ttu-id="6f22c-401">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f22c-401">win:UInt64</span></span>|<span data-ttu-id="6f22c-402">Rozmiar alokacji w bajtach.</span><span class="sxs-lookup"><span data-stu-id="6f22c-402">The allocation size, in bytes.</span></span> <span data-ttu-id="6f22c-403">Ta wartość jest dokładna dla bardzo dużych alokacji.</span><span class="sxs-lookup"><span data-stu-id="6f22c-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="6f22c-404">IdentyfikatorTypu</span><span class="sxs-lookup"><span data-stu-id="6f22c-404">TypeId</span></span>|<span data-ttu-id="6f22c-405">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="6f22c-405">win:Pointer</span></span>|<span data-ttu-id="6f22c-406">Adres metody.</span><span class="sxs-lookup"><span data-stu-id="6f22c-406">The address of the MethodTable.</span></span> <span data-ttu-id="6f22c-407">Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to adres metody, która odnosi się do ostatniego przydzielony obiekt (obiekt, który spowodował przekroczenie 100 KB progu).</span><span class="sxs-lookup"><span data-stu-id="6f22c-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="6f22c-408">TypeName</span><span class="sxs-lookup"><span data-stu-id="6f22c-408">TypeName</span></span>|<span data-ttu-id="6f22c-409">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6f22c-409">win:UnicodeString</span></span>|<span data-ttu-id="6f22c-410">Nazwa przydzieloną typ.</span><span class="sxs-lookup"><span data-stu-id="6f22c-410">The name of the type that was allocated.</span></span> <span data-ttu-id="6f22c-411">Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to typ ostatniego przydzielono obiektu (obiektu, który spowodował przekroczenie 100 KB).</span><span class="sxs-lookup"><span data-stu-id="6f22c-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="6f22c-412">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="6f22c-412">HeapIndex</span></span>|<span data-ttu-id="6f22c-413">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-413">win:UInt32</span></span>|<span data-ttu-id="6f22c-414">Sterta, do której został przydzielony obiekt.</span><span class="sxs-lookup"><span data-stu-id="6f22c-414">The heap where the object was allocated.</span></span> <span data-ttu-id="6f22c-415">Ta wartość jest równa 0 (zero) podczas uruchamiania z odzyskiwaniem pamięci stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="6f22c-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="6f22c-416">Zdarzenie GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="6f22c-417">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-418">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-418">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-419">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-421">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-421">Informational (4)</span></span>|

<span data-ttu-id="6f22c-422">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-422">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-423">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-423">Event</span></span>|<span data-ttu-id="6f22c-424">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-424">Event ID</span></span>|<span data-ttu-id="6f22c-425">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="6f22c-426">14</span><span class="sxs-lookup"><span data-stu-id="6f22c-426">14</span></span>|<span data-ttu-id="6f22c-427">Początek uruchamiania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="6f22c-427">The start of running finalizers.</span></span>|

<span data-ttu-id="6f22c-428">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6f22c-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="6f22c-429">Zdarzenie GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="6f22c-430">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-431">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-431">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-432">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-434">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-434">Informational (4)</span></span>|

<span data-ttu-id="6f22c-435">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-435">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-436">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-436">Event</span></span>|<span data-ttu-id="6f22c-437">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-437">Event ID</span></span>|<span data-ttu-id="6f22c-438">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="6f22c-439">13</span><span class="sxs-lookup"><span data-stu-id="6f22c-439">13</span></span>|<span data-ttu-id="6f22c-440">Koniec uruchomionych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="6f22c-440">The end of running finalizers.</span></span>|

<span data-ttu-id="6f22c-441">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="6f22c-441">The following table shows the event data:</span></span>

|<span data-ttu-id="6f22c-442">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="6f22c-442">Field name</span></span>|<span data-ttu-id="6f22c-443">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6f22c-443">Data type</span></span>|<span data-ttu-id="6f22c-444">Opis</span><span class="sxs-lookup"><span data-stu-id="6f22c-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="6f22c-445">Count</span><span class="sxs-lookup"><span data-stu-id="6f22c-445">Count</span></span>|<span data-ttu-id="6f22c-446">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f22c-446">win:UInt32</span></span>|<span data-ttu-id="6f22c-447">Liczba uruchomionych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="6f22c-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="6f22c-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f22c-448">ClrInstanceID</span></span>|<span data-ttu-id="6f22c-449">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f22c-449">win:UInt16</span></span>|<span data-ttu-id="6f22c-450">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6f22c-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="6f22c-451">Zdarzenie GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="6f22c-452">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-453">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-453">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-454">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-456">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-456">Informational (4)</span></span>|
|<span data-ttu-id="6f22c-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="6f22c-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="6f22c-458">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-458">Informational (4)</span></span>|

<span data-ttu-id="6f22c-459">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-459">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-460">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-460">Event</span></span>|<span data-ttu-id="6f22c-461">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-461">Event ID</span></span>|<span data-ttu-id="6f22c-462">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="6f22c-463">11</span><span class="sxs-lookup"><span data-stu-id="6f22c-463">11</span></span>|<span data-ttu-id="6f22c-464">Utworzono wątek współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f22c-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="6f22c-465">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6f22c-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="6f22c-466">Zdarzenie GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="6f22c-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="6f22c-467">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="6f22c-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="6f22c-468">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-468">Keyword for raising the event</span></span>|<span data-ttu-id="6f22c-469">Poziom</span><span class="sxs-lookup"><span data-stu-id="6f22c-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6f22c-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="6f22c-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6f22c-471">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-471">Informational (4)</span></span>|
|<span data-ttu-id="6f22c-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="6f22c-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="6f22c-473">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="6f22c-473">Informational (4)</span></span>|

<span data-ttu-id="6f22c-474">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="6f22c-474">The following table shows the event information:</span></span>

|<span data-ttu-id="6f22c-475">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6f22c-475">Event</span></span>|<span data-ttu-id="6f22c-476">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6f22c-476">Event ID</span></span>|<span data-ttu-id="6f22c-477">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="6f22c-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="6f22c-478">12</span><span class="sxs-lookup"><span data-stu-id="6f22c-478">12</span></span>|<span data-ttu-id="6f22c-479">Wątek współbieżnego wyrzucania elementów bezużytecznych został zakończony.</span><span class="sxs-lookup"><span data-stu-id="6f22c-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="6f22c-480">Brak danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6f22c-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f22c-481">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f22c-481">See also</span></span>

- [<span data-ttu-id="6f22c-482">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="6f22c-482">CLR ETW Events</span></span>](clr-etw-events.md)
