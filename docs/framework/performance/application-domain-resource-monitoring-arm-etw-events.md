---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
description: Przeczytaj informacje o zdarzeniach funkcji ETW monitorowania zasobów domeny aplikacji (ARM) w programie .NET, takich jak ThreadCreated —, AppDomainMemAllocated, AppDomainMemSurvived i inne.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309784"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="1b48c-103">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="1b48c-103">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="1b48c-104">Te zdarzenia zapewniają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b48c-104">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="1b48c-105">Możesz użyć tych zdarzeń lub użyć funkcji monitorowania zasobów domeny aplikacji (ARM), aby uzyskać te same informacje.</span><span class="sxs-lookup"><span data-stu-id="1b48c-105">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="1b48c-106">Zdarzenie ThreadCreated —</span><span class="sxs-lookup"><span data-stu-id="1b48c-106">ThreadCreated Event</span></span>

<span data-ttu-id="1b48c-107">To zdarzenie jest również zgłaszane w ramach dostawcy uwalniania jako `ThreadDC` (pod `AppDomainResourceManagementRundownKeyword` słowem kluczowym).</span><span class="sxs-lookup"><span data-stu-id="1b48c-107">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="1b48c-108">Jest to jedyne zdarzenie zgłaszane w ramach dostawcy uwalniania w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="1b48c-108">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="1b48c-109">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="1b48c-109">The following table shows the keyword and level.</span></span> <span data-ttu-id="1b48c-110">Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1b48c-110">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="1b48c-111">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-111">Keyword for raising the event</span></span>|<span data-ttu-id="1b48c-112">Poziom</span><span class="sxs-lookup"><span data-stu-id="1b48c-112">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1b48c-113">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="1b48c-113">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="1b48c-114">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="1b48c-114">Informational(4)</span></span>|
|<span data-ttu-id="1b48c-115">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="1b48c-115">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1b48c-116">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="1b48c-116">Informational(4)</span></span>|

<span data-ttu-id="1b48c-117">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="1b48c-117">The following table shows the event information:</span></span>

|<span data-ttu-id="1b48c-118">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="1b48c-118">Event</span></span>|<span data-ttu-id="1b48c-119">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-119">Event ID</span></span>|<span data-ttu-id="1b48c-120">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="1b48c-120">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="1b48c-121">85</span><span class="sxs-lookup"><span data-stu-id="1b48c-121">85</span></span>|<span data-ttu-id="1b48c-122">Utworzono wątek dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b48c-122">A thread was created for the application domain.</span></span>|

<span data-ttu-id="1b48c-123">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="1b48c-123">The following table shows the event data:</span></span>

|<span data-ttu-id="1b48c-124">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="1b48c-124">Field name</span></span>|<span data-ttu-id="1b48c-125">Typ danych</span><span class="sxs-lookup"><span data-stu-id="1b48c-125">Data type</span></span>|<span data-ttu-id="1b48c-126">Opis</span><span class="sxs-lookup"><span data-stu-id="1b48c-126">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="1b48c-127">ThreadID</span><span class="sxs-lookup"><span data-stu-id="1b48c-127">ThreadID</span></span>|<span data-ttu-id="1b48c-128">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-128">win:UInt64</span></span>|<span data-ttu-id="1b48c-129">Identyfikator utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="1b48c-129">ID of the thread that was created.</span></span>|
|<span data-ttu-id="1b48c-130">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="1b48c-130">AppDomainID</span></span>|<span data-ttu-id="1b48c-131">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-131">win:UInt64</span></span>|<span data-ttu-id="1b48c-132">Identyfikator domeny aplikacji, dla której jest zgłaszane działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="1b48c-132">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="1b48c-133">Flagi</span><span class="sxs-lookup"><span data-stu-id="1b48c-133">Flags</span></span>|<span data-ttu-id="1b48c-134">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="1b48c-134">win:UInt32</span></span>|<span data-ttu-id="1b48c-135">Flagi tworzenia wątku.</span><span class="sxs-lookup"><span data-stu-id="1b48c-135">Thread creation flags.</span></span>|
|<span data-ttu-id="1b48c-136">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="1b48c-136">ManagedThreadIndex</span></span>|<span data-ttu-id="1b48c-137">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="1b48c-137">win:UInt32</span></span>|<span data-ttu-id="1b48c-138">Zarządzany indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="1b48c-138">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="1b48c-139">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="1b48c-139">OSThreadID</span></span>|<span data-ttu-id="1b48c-140">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="1b48c-140">win:UInt32</span></span>|<span data-ttu-id="1b48c-141">Identyfikator systemu operacyjnego wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="1b48c-141">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="1b48c-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1b48c-142">ClrInstanceID</span></span>|<span data-ttu-id="1b48c-143">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1b48c-143">win:UInt16</span></span>|<span data-ttu-id="1b48c-144">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1b48c-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="1b48c-145">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="1b48c-145">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="1b48c-146">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="1b48c-146">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="1b48c-147">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-147">Keyword for raising the event</span></span>|<span data-ttu-id="1b48c-148">Poziom</span><span class="sxs-lookup"><span data-stu-id="1b48c-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1b48c-149">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="1b48c-149">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="1b48c-150">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="1b48c-150">Informational(4)</span></span>|

<span data-ttu-id="1b48c-151">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="1b48c-151">The following table shows the event information:</span></span>

|<span data-ttu-id="1b48c-152">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="1b48c-152">Event</span></span>|<span data-ttu-id="1b48c-153">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-153">Event ID</span></span>|<span data-ttu-id="1b48c-154">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="1b48c-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="1b48c-155">83</span><span class="sxs-lookup"><span data-stu-id="1b48c-155">83</span></span>|<span data-ttu-id="1b48c-156">Co 4 MB pamięci (w przybliżeniu) jest przypisywany w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b48c-156">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="1b48c-157">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="1b48c-157">The following table shows the event data:</span></span>

|<span data-ttu-id="1b48c-158">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="1b48c-158">Field name</span></span>|<span data-ttu-id="1b48c-159">Typ danych</span><span class="sxs-lookup"><span data-stu-id="1b48c-159">Data type</span></span>|<span data-ttu-id="1b48c-160">Opis</span><span class="sxs-lookup"><span data-stu-id="1b48c-160">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="1b48c-161">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="1b48c-161">AppDomainID</span></span>|<span data-ttu-id="1b48c-162">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-162">win:UInt64</span></span>|<span data-ttu-id="1b48c-163">Identyfikator domeny aplikacji, dla której zgłaszane jest użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="1b48c-163">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="1b48c-164">Rozdziela</span><span class="sxs-lookup"><span data-stu-id="1b48c-164">Allocated</span></span>|<span data-ttu-id="1b48c-165">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-165">win:UInt64</span></span>|<span data-ttu-id="1b48c-166">Całkowita liczba bajtów przydzielono w tej domenie aplikacji od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowana).</span><span class="sxs-lookup"><span data-stu-id="1b48c-166">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="1b48c-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1b48c-167">ClrInstanceID</span></span>|<span data-ttu-id="1b48c-168">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1b48c-168">win:UInt16</span></span>|<span data-ttu-id="1b48c-169">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1b48c-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="1b48c-170">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="1b48c-170">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="1b48c-171">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="1b48c-171">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="1b48c-172">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-172">Keyword for raising the event</span></span>|<span data-ttu-id="1b48c-173">Poziom</span><span class="sxs-lookup"><span data-stu-id="1b48c-173">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1b48c-174">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="1b48c-174">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="1b48c-175">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="1b48c-175">Informational(4)</span></span>|

<span data-ttu-id="1b48c-176">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="1b48c-176">The following table shows the event information:</span></span>

|<span data-ttu-id="1b48c-177">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="1b48c-177">Event</span></span>|<span data-ttu-id="1b48c-178">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-178">Event ID</span></span>|<span data-ttu-id="1b48c-179">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="1b48c-179">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="1b48c-180">84</span><span class="sxs-lookup"><span data-stu-id="1b48c-180">84</span></span>|<span data-ttu-id="1b48c-181">Wszystkie wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="1b48c-181">Each garbage collection has ended.</span></span>|

<span data-ttu-id="1b48c-182">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="1b48c-182">The following table shows the event data:</span></span>

|<span data-ttu-id="1b48c-183">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="1b48c-183">Field name</span></span>|<span data-ttu-id="1b48c-184">Typ danych</span><span class="sxs-lookup"><span data-stu-id="1b48c-184">Data type</span></span>|<span data-ttu-id="1b48c-185">Opis</span><span class="sxs-lookup"><span data-stu-id="1b48c-185">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="1b48c-186">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="1b48c-186">AppDomainID</span></span>|<span data-ttu-id="1b48c-187">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-187">win:UInt64</span></span>|<span data-ttu-id="1b48c-188">Identyfikator domeny, dla której zgłaszane jest użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="1b48c-188">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="1b48c-189">Ocalałe</span><span class="sxs-lookup"><span data-stu-id="1b48c-189">Survived</span></span>|<span data-ttu-id="1b48c-190">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-190">win:UInt64</span></span>|<span data-ttu-id="1b48c-191">Liczba bajtów przeprowadzonych po ostatniej kolekcji i, które są znane przez tę domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b48c-191">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="1b48c-192">Ta liczba jest dokładna i kompletna po pełnej kolekcji, ale może być niekompletna po kolekcji tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="1b48c-192">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="1b48c-193">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="1b48c-193">ProcessSurvived</span></span>|<span data-ttu-id="1b48c-194">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-194">win:UInt64</span></span>|<span data-ttu-id="1b48c-195">Całkowita liczba bajtów przeczytanych z ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1b48c-195">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="1b48c-196">Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w zarządzanych stertach.</span><span class="sxs-lookup"><span data-stu-id="1b48c-196">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="1b48c-197">Po zakończeniu zbierania danych tymczasowych ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w generacjach tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="1b48c-197">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="1b48c-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1b48c-198">ClrInstanceID</span></span>|<span data-ttu-id="1b48c-199">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1b48c-199">win:UInt16</span></span>|<span data-ttu-id="1b48c-200">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1b48c-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="1b48c-201">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="1b48c-201">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="1b48c-202">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="1b48c-202">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="1b48c-203">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-203">Keyword for raising the event</span></span>|<span data-ttu-id="1b48c-204">Poziom</span><span class="sxs-lookup"><span data-stu-id="1b48c-204">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1b48c-205">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="1b48c-205">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="1b48c-206">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="1b48c-206">Informational(4)</span></span>|
|<span data-ttu-id="1b48c-207">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="1b48c-207">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1b48c-208">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="1b48c-208">Informational(4)</span></span>|

<span data-ttu-id="1b48c-209">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="1b48c-209">The following table shows the event information:</span></span>

|<span data-ttu-id="1b48c-210">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="1b48c-210">Event</span></span>|<span data-ttu-id="1b48c-211">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-211">Event ID</span></span>|<span data-ttu-id="1b48c-212">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="1b48c-212">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="1b48c-213">87</span><span class="sxs-lookup"><span data-stu-id="1b48c-213">87</span></span>|<span data-ttu-id="1b48c-214">Wątek przechodzi do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b48c-214">A thread enters an application domain.</span></span>|

<span data-ttu-id="1b48c-215">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="1b48c-215">The following table shows the event data:</span></span>

|<span data-ttu-id="1b48c-216">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="1b48c-216">Field name</span></span>|<span data-ttu-id="1b48c-217">Typ danych</span><span class="sxs-lookup"><span data-stu-id="1b48c-217">Data type</span></span>|<span data-ttu-id="1b48c-218">Opis</span><span class="sxs-lookup"><span data-stu-id="1b48c-218">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="1b48c-219">ThreadID</span><span class="sxs-lookup"><span data-stu-id="1b48c-219">ThreadID</span></span>|<span data-ttu-id="1b48c-220">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-220">win:UInt64</span></span>|<span data-ttu-id="1b48c-221">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="1b48c-221">The thread identifier.</span></span>|
|<span data-ttu-id="1b48c-222">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="1b48c-222">AppDomainID</span></span>|<span data-ttu-id="1b48c-223">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-223">win:UInt64</span></span>|<span data-ttu-id="1b48c-224">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b48c-224">The application domain identifier.</span></span>|
|<span data-ttu-id="1b48c-225">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1b48c-225">ClrInstanceID</span></span>|<span data-ttu-id="1b48c-226">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1b48c-226">win:UInt16</span></span>|<span data-ttu-id="1b48c-227">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1b48c-227">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="1b48c-228">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="1b48c-228">ThreadTerminated Event</span></span>

<span data-ttu-id="1b48c-229">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="1b48c-229">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="1b48c-230">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-230">Keyword for raising the event</span></span>|<span data-ttu-id="1b48c-231">Poziom</span><span class="sxs-lookup"><span data-stu-id="1b48c-231">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1b48c-232">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="1b48c-232">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="1b48c-233">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="1b48c-233">Informational(4)</span></span>|
|<span data-ttu-id="1b48c-234">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="1b48c-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1b48c-235">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="1b48c-235">Informational(4)</span></span>|

<span data-ttu-id="1b48c-236">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="1b48c-236">The following table shows the event information:</span></span>

|<span data-ttu-id="1b48c-237">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="1b48c-237">Event</span></span>|<span data-ttu-id="1b48c-238">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b48c-238">Event ID</span></span>|<span data-ttu-id="1b48c-239">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="1b48c-239">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="1b48c-240">86</span><span class="sxs-lookup"><span data-stu-id="1b48c-240">86</span></span>|<span data-ttu-id="1b48c-241">Wątek kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="1b48c-241">A thread terminates.</span></span>|

<span data-ttu-id="1b48c-242">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="1b48c-242">The following table shows the event data:</span></span>

|<span data-ttu-id="1b48c-243">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="1b48c-243">Field name</span></span>|<span data-ttu-id="1b48c-244">Typ danych</span><span class="sxs-lookup"><span data-stu-id="1b48c-244">Data type</span></span>|<span data-ttu-id="1b48c-245">Opis</span><span class="sxs-lookup"><span data-stu-id="1b48c-245">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="1b48c-246">ThreadID</span><span class="sxs-lookup"><span data-stu-id="1b48c-246">ThreadID</span></span>|<span data-ttu-id="1b48c-247">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-247">win:UInt64</span></span>|<span data-ttu-id="1b48c-248">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="1b48c-248">The thread identifier.</span></span>|
|<span data-ttu-id="1b48c-249">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="1b48c-249">AppDomainID</span></span>|<span data-ttu-id="1b48c-250">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1b48c-250">win:UInt64</span></span>|<span data-ttu-id="1b48c-251">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b48c-251">The application domain identifier.</span></span>|
|<span data-ttu-id="1b48c-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1b48c-252">ClrInstanceID</span></span>|<span data-ttu-id="1b48c-253">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1b48c-253">win:UInt16</span></span>|<span data-ttu-id="1b48c-254">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1b48c-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1b48c-255">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b48c-255">See also</span></span>

- [<span data-ttu-id="1b48c-256">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="1b48c-256">CLR ETW Events</span></span>](clr-etw-events.md)
