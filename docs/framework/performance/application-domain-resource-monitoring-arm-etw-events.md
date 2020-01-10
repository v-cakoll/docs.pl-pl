---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: 0e453b2bafffd9e07a1bdddd97282c5b97f5483d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716215"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="fe698-102">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="fe698-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="fe698-103">Te zdarzenia zapewniają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe698-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="fe698-104">Możesz użyć tych zdarzeń lub użyć funkcji monitorowania zasobów domeny aplikacji (ARM), aby uzyskać te same informacje.</span><span class="sxs-lookup"><span data-stu-id="fe698-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="fe698-105">Zdarzenie ThreadCreated —</span><span class="sxs-lookup"><span data-stu-id="fe698-105">ThreadCreated Event</span></span>

<span data-ttu-id="fe698-106">To zdarzenie jest również zgłaszane w ramach dostawcy uwalniania jako `ThreadDC` (w obszarze słowa kluczowego `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="fe698-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="fe698-107">Jest to jedyne zdarzenie zgłaszane w ramach dostawcy uwalniania w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="fe698-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="fe698-108">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="fe698-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="fe698-109">Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="fe698-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="fe698-110">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-110">Keyword for raising the event</span></span>|<span data-ttu-id="fe698-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="fe698-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="fe698-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe698-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe698-113">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fe698-113">Informational(4)</span></span>|
|<span data-ttu-id="fe698-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="fe698-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fe698-115">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fe698-115">Informational(4)</span></span>|

<span data-ttu-id="fe698-116">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="fe698-116">The following table shows the event information:</span></span>

|<span data-ttu-id="fe698-117">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="fe698-117">Event</span></span>|<span data-ttu-id="fe698-118">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-118">Event ID</span></span>|<span data-ttu-id="fe698-119">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="fe698-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="fe698-120">85</span><span class="sxs-lookup"><span data-stu-id="fe698-120">85</span></span>|<span data-ttu-id="fe698-121">Utworzono wątek dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe698-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="fe698-122">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="fe698-122">The following table shows the event data:</span></span>

|<span data-ttu-id="fe698-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="fe698-123">Field name</span></span>|<span data-ttu-id="fe698-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fe698-124">Data type</span></span>|<span data-ttu-id="fe698-125">Opis</span><span class="sxs-lookup"><span data-stu-id="fe698-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="fe698-126">ThreadID</span><span class="sxs-lookup"><span data-stu-id="fe698-126">ThreadID</span></span>|<span data-ttu-id="fe698-127">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-127">win:UInt64</span></span>|<span data-ttu-id="fe698-128">Identyfikator utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="fe698-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="fe698-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe698-129">AppDomainID</span></span>|<span data-ttu-id="fe698-130">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-130">win:UInt64</span></span>|<span data-ttu-id="fe698-131">Identyfikator domeny aplikacji, dla której jest zgłaszane działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="fe698-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="fe698-132">Flagi</span><span class="sxs-lookup"><span data-stu-id="fe698-132">Flags</span></span>|<span data-ttu-id="fe698-133">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fe698-133">win:UInt32</span></span>|<span data-ttu-id="fe698-134">Flagi tworzenia wątku.</span><span class="sxs-lookup"><span data-stu-id="fe698-134">Thread creation flags.</span></span>|
|<span data-ttu-id="fe698-135">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="fe698-135">ManagedThreadIndex</span></span>|<span data-ttu-id="fe698-136">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fe698-136">win:UInt32</span></span>|<span data-ttu-id="fe698-137">Zarządzany indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="fe698-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="fe698-138">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="fe698-138">OSThreadID</span></span>|<span data-ttu-id="fe698-139">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fe698-139">win:UInt32</span></span>|<span data-ttu-id="fe698-140">Identyfikator systemu operacyjnego wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="fe698-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="fe698-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe698-141">ClrInstanceID</span></span>|<span data-ttu-id="fe698-142">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fe698-142">win:UInt16</span></span>|<span data-ttu-id="fe698-143">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe698-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="fe698-144">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="fe698-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="fe698-145">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="fe698-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="fe698-146">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-146">Keyword for raising the event</span></span>|<span data-ttu-id="fe698-147">Poziom</span><span class="sxs-lookup"><span data-stu-id="fe698-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="fe698-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe698-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe698-149">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fe698-149">Informational(4)</span></span>|

<span data-ttu-id="fe698-150">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="fe698-150">The following table shows the event information:</span></span>

|<span data-ttu-id="fe698-151">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="fe698-151">Event</span></span>|<span data-ttu-id="fe698-152">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-152">Event ID</span></span>|<span data-ttu-id="fe698-153">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="fe698-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="fe698-154">83</span><span class="sxs-lookup"><span data-stu-id="fe698-154">83</span></span>|<span data-ttu-id="fe698-155">Co 4 MB pamięci (w przybliżeniu) jest przypisywany w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe698-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="fe698-156">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="fe698-156">The following table shows the event data:</span></span>

|<span data-ttu-id="fe698-157">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="fe698-157">Field name</span></span>|<span data-ttu-id="fe698-158">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fe698-158">Data type</span></span>|<span data-ttu-id="fe698-159">Opis</span><span class="sxs-lookup"><span data-stu-id="fe698-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="fe698-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe698-160">AppDomainID</span></span>|<span data-ttu-id="fe698-161">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-161">win:UInt64</span></span>|<span data-ttu-id="fe698-162">Identyfikator domeny aplikacji, dla której zgłaszane jest użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="fe698-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="fe698-163">Rozdziela</span><span class="sxs-lookup"><span data-stu-id="fe698-163">Allocated</span></span>|<span data-ttu-id="fe698-164">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-164">win:UInt64</span></span>|<span data-ttu-id="fe698-165">Całkowita liczba bajtów przydzielono w tej domenie aplikacji od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowana).</span><span class="sxs-lookup"><span data-stu-id="fe698-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="fe698-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe698-166">ClrInstanceID</span></span>|<span data-ttu-id="fe698-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fe698-167">win:UInt16</span></span>|<span data-ttu-id="fe698-168">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe698-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="fe698-169">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="fe698-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="fe698-170">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="fe698-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="fe698-171">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-171">Keyword for raising the event</span></span>|<span data-ttu-id="fe698-172">Poziom</span><span class="sxs-lookup"><span data-stu-id="fe698-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="fe698-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe698-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe698-174">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fe698-174">Informational(4)</span></span>|

<span data-ttu-id="fe698-175">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="fe698-175">The following table shows the event information:</span></span>

|<span data-ttu-id="fe698-176">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="fe698-176">Event</span></span>|<span data-ttu-id="fe698-177">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-177">Event ID</span></span>|<span data-ttu-id="fe698-178">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="fe698-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="fe698-179">84</span><span class="sxs-lookup"><span data-stu-id="fe698-179">84</span></span>|<span data-ttu-id="fe698-180">Wszystkie wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="fe698-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="fe698-181">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="fe698-181">The following table shows the event data:</span></span>

|<span data-ttu-id="fe698-182">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="fe698-182">Field name</span></span>|<span data-ttu-id="fe698-183">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fe698-183">Data type</span></span>|<span data-ttu-id="fe698-184">Opis</span><span class="sxs-lookup"><span data-stu-id="fe698-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="fe698-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe698-185">AppDomainID</span></span>|<span data-ttu-id="fe698-186">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-186">win:UInt64</span></span>|<span data-ttu-id="fe698-187">Identyfikator domeny, dla której zgłaszane jest użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="fe698-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="fe698-188">Ocalałe</span><span class="sxs-lookup"><span data-stu-id="fe698-188">Survived</span></span>|<span data-ttu-id="fe698-189">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-189">win:UInt64</span></span>|<span data-ttu-id="fe698-190">Liczba bajtów przeprowadzonych po ostatniej kolekcji i, które są znane przez tę domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe698-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="fe698-191">Ta liczba jest dokładna i kompletna po pełnej kolekcji, ale może być niekompletna po kolekcji tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="fe698-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="fe698-192">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="fe698-192">ProcessSurvived</span></span>|<span data-ttu-id="fe698-193">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-193">win:UInt64</span></span>|<span data-ttu-id="fe698-194">Całkowita liczba bajtów przeczytanych z ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fe698-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="fe698-195">Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w zarządzanych stertach.</span><span class="sxs-lookup"><span data-stu-id="fe698-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="fe698-196">Po zakończeniu zbierania danych tymczasowych ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w generacjach tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="fe698-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="fe698-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe698-197">ClrInstanceID</span></span>|<span data-ttu-id="fe698-198">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fe698-198">win:UInt16</span></span>|<span data-ttu-id="fe698-199">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe698-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="fe698-200">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="fe698-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="fe698-201">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="fe698-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="fe698-202">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-202">Keyword for raising the event</span></span>|<span data-ttu-id="fe698-203">Poziom</span><span class="sxs-lookup"><span data-stu-id="fe698-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="fe698-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe698-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe698-205">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fe698-205">Informational(4)</span></span>|
|<span data-ttu-id="fe698-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="fe698-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fe698-207">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fe698-207">Informational(4)</span></span>|

<span data-ttu-id="fe698-208">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="fe698-208">The following table shows the event information:</span></span>

|<span data-ttu-id="fe698-209">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="fe698-209">Event</span></span>|<span data-ttu-id="fe698-210">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-210">Event ID</span></span>|<span data-ttu-id="fe698-211">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="fe698-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="fe698-212">87</span><span class="sxs-lookup"><span data-stu-id="fe698-212">87</span></span>|<span data-ttu-id="fe698-213">Wątek przechodzi do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe698-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="fe698-214">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="fe698-214">The following table shows the event data:</span></span>

|<span data-ttu-id="fe698-215">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="fe698-215">Field name</span></span>|<span data-ttu-id="fe698-216">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fe698-216">Data type</span></span>|<span data-ttu-id="fe698-217">Opis</span><span class="sxs-lookup"><span data-stu-id="fe698-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="fe698-218">ThreadID</span><span class="sxs-lookup"><span data-stu-id="fe698-218">ThreadID</span></span>|<span data-ttu-id="fe698-219">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-219">win:UInt64</span></span>|<span data-ttu-id="fe698-220">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="fe698-220">The thread identifier.</span></span>|
|<span data-ttu-id="fe698-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe698-221">AppDomainID</span></span>|<span data-ttu-id="fe698-222">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-222">win:UInt64</span></span>|<span data-ttu-id="fe698-223">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe698-223">The application domain identifier.</span></span>|
|<span data-ttu-id="fe698-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe698-224">ClrInstanceID</span></span>|<span data-ttu-id="fe698-225">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fe698-225">win:UInt16</span></span>|<span data-ttu-id="fe698-226">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe698-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="fe698-227">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="fe698-227">ThreadTerminated Event</span></span>

<span data-ttu-id="fe698-228">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="fe698-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="fe698-229">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-229">Keyword for raising the event</span></span>|<span data-ttu-id="fe698-230">Poziom</span><span class="sxs-lookup"><span data-stu-id="fe698-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="fe698-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="fe698-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fe698-232">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fe698-232">Informational(4)</span></span>|
|<span data-ttu-id="fe698-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="fe698-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fe698-234">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="fe698-234">Informational(4)</span></span>|

<span data-ttu-id="fe698-235">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="fe698-235">The following table shows the event information:</span></span>

|<span data-ttu-id="fe698-236">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="fe698-236">Event</span></span>|<span data-ttu-id="fe698-237">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fe698-237">Event ID</span></span>|<span data-ttu-id="fe698-238">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="fe698-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="fe698-239">86</span><span class="sxs-lookup"><span data-stu-id="fe698-239">86</span></span>|<span data-ttu-id="fe698-240">Wątek kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="fe698-240">A thread terminates.</span></span>|

<span data-ttu-id="fe698-241">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="fe698-241">The following table shows the event data:</span></span>

|<span data-ttu-id="fe698-242">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="fe698-242">Field name</span></span>|<span data-ttu-id="fe698-243">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fe698-243">Data type</span></span>|<span data-ttu-id="fe698-244">Opis</span><span class="sxs-lookup"><span data-stu-id="fe698-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="fe698-245">ThreadID</span><span class="sxs-lookup"><span data-stu-id="fe698-245">ThreadID</span></span>|<span data-ttu-id="fe698-246">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-246">win:UInt64</span></span>|<span data-ttu-id="fe698-247">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="fe698-247">The thread identifier.</span></span>|
|<span data-ttu-id="fe698-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fe698-248">AppDomainID</span></span>|<span data-ttu-id="fe698-249">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fe698-249">win:UInt64</span></span>|<span data-ttu-id="fe698-250">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe698-250">The application domain identifier.</span></span>|
|<span data-ttu-id="fe698-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fe698-251">ClrInstanceID</span></span>|<span data-ttu-id="fe698-252">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fe698-252">win:UInt16</span></span>|<span data-ttu-id="fe698-253">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fe698-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fe698-254">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe698-254">See also</span></span>

- [<span data-ttu-id="fe698-255">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="fe698-255">CLR ETW Events</span></span>](clr-etw-events.md)
