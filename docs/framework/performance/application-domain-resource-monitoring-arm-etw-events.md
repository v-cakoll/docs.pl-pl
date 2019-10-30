---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e1c2a38be6f2c15a118b35925570119b474f096
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040564"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="ff6ed-102">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="ff6ed-103">Te zdarzenia zapewniają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="ff6ed-104">Możesz użyć tych zdarzeń lub użyć funkcji monitorowania zasobów domeny aplikacji (ARM), aby uzyskać te same informacje.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="ff6ed-105">Zdarzenie ThreadCreated —</span><span class="sxs-lookup"><span data-stu-id="ff6ed-105">ThreadCreated Event</span></span>

<span data-ttu-id="ff6ed-106">To zdarzenie jest również zgłaszane w ramach dostawcy uwalniania jako `ThreadDC` (w obszarze słowa kluczowego `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="ff6ed-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="ff6ed-107">Jest to jedyne zdarzenie zgłaszane w ramach dostawcy uwalniania w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="ff6ed-108">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="ff6ed-109">Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ff6ed-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="ff6ed-110">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-110">Keyword for raising the event</span></span>|<span data-ttu-id="ff6ed-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="ff6ed-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ff6ed-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ff6ed-113">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-113">Informational(4)</span></span>|
|<span data-ttu-id="ff6ed-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ff6ed-115">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-115">Informational(4)</span></span>|

<span data-ttu-id="ff6ed-116">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-116">The following table shows the event information:</span></span>

|<span data-ttu-id="ff6ed-117">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ff6ed-117">Event</span></span>|<span data-ttu-id="ff6ed-118">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-118">Event ID</span></span>|<span data-ttu-id="ff6ed-119">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="ff6ed-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="ff6ed-120">85</span><span class="sxs-lookup"><span data-stu-id="ff6ed-120">85</span></span>|<span data-ttu-id="ff6ed-121">Utworzono wątek dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="ff6ed-122">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-122">The following table shows the event data:</span></span>

|<span data-ttu-id="ff6ed-123">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ff6ed-123">Field name</span></span>|<span data-ttu-id="ff6ed-124">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ff6ed-124">Data type</span></span>|<span data-ttu-id="ff6ed-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ff6ed-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ff6ed-126">ThreadID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-126">ThreadID</span></span>|<span data-ttu-id="ff6ed-127">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-127">win:UInt64</span></span>|<span data-ttu-id="ff6ed-128">Identyfikator utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="ff6ed-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-129">AppDomainID</span></span>|<span data-ttu-id="ff6ed-130">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-130">win:UInt64</span></span>|<span data-ttu-id="ff6ed-131">Identyfikator domeny aplikacji, dla której jest zgłaszane działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="ff6ed-132">Flagi</span><span class="sxs-lookup"><span data-stu-id="ff6ed-132">Flags</span></span>|<span data-ttu-id="ff6ed-133">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ff6ed-133">win:UInt32</span></span>|<span data-ttu-id="ff6ed-134">Flagi tworzenia wątku.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-134">Thread creation flags.</span></span>|
|<span data-ttu-id="ff6ed-135">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="ff6ed-135">ManagedThreadIndex</span></span>|<span data-ttu-id="ff6ed-136">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ff6ed-136">win:UInt32</span></span>|<span data-ttu-id="ff6ed-137">Zarządzany indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="ff6ed-138">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-138">OSThreadID</span></span>|<span data-ttu-id="ff6ed-139">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ff6ed-139">win:UInt32</span></span>|<span data-ttu-id="ff6ed-140">Identyfikator systemu operacyjnego wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="ff6ed-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-141">ClrInstanceID</span></span>|<span data-ttu-id="ff6ed-142">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ff6ed-142">win:UInt16</span></span>|<span data-ttu-id="ff6ed-143">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="ff6ed-144">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="ff6ed-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="ff6ed-145">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ff6ed-146">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-146">Keyword for raising the event</span></span>|<span data-ttu-id="ff6ed-147">Poziom</span><span class="sxs-lookup"><span data-stu-id="ff6ed-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ff6ed-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ff6ed-149">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-149">Informational(4)</span></span>|

<span data-ttu-id="ff6ed-150">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-150">The following table shows the event information:</span></span>

|<span data-ttu-id="ff6ed-151">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ff6ed-151">Event</span></span>|<span data-ttu-id="ff6ed-152">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-152">Event ID</span></span>|<span data-ttu-id="ff6ed-153">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="ff6ed-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="ff6ed-154">83</span><span class="sxs-lookup"><span data-stu-id="ff6ed-154">83</span></span>|<span data-ttu-id="ff6ed-155">Co 4 MB pamięci (w przybliżeniu) jest przypisywany w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="ff6ed-156">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-156">The following table shows the event data:</span></span>

|<span data-ttu-id="ff6ed-157">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ff6ed-157">Field name</span></span>|<span data-ttu-id="ff6ed-158">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ff6ed-158">Data type</span></span>|<span data-ttu-id="ff6ed-159">Opis</span><span class="sxs-lookup"><span data-stu-id="ff6ed-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ff6ed-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-160">AppDomainID</span></span>|<span data-ttu-id="ff6ed-161">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-161">win:UInt64</span></span>|<span data-ttu-id="ff6ed-162">Identyfikator domeny aplikacji, dla której zgłaszane jest użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="ff6ed-163">Rozdziela</span><span class="sxs-lookup"><span data-stu-id="ff6ed-163">Allocated</span></span>|<span data-ttu-id="ff6ed-164">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-164">win:UInt64</span></span>|<span data-ttu-id="ff6ed-165">Całkowita liczba bajtów przydzielono w tej domenie aplikacji od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowana).</span><span class="sxs-lookup"><span data-stu-id="ff6ed-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="ff6ed-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-166">ClrInstanceID</span></span>|<span data-ttu-id="ff6ed-167">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ff6ed-167">win:UInt16</span></span>|<span data-ttu-id="ff6ed-168">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="ff6ed-169">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="ff6ed-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="ff6ed-170">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ff6ed-171">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-171">Keyword for raising the event</span></span>|<span data-ttu-id="ff6ed-172">Poziom</span><span class="sxs-lookup"><span data-stu-id="ff6ed-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ff6ed-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ff6ed-174">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-174">Informational(4)</span></span>|

<span data-ttu-id="ff6ed-175">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-175">The following table shows the event information:</span></span>

|<span data-ttu-id="ff6ed-176">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ff6ed-176">Event</span></span>|<span data-ttu-id="ff6ed-177">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-177">Event ID</span></span>|<span data-ttu-id="ff6ed-178">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="ff6ed-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="ff6ed-179">84</span><span class="sxs-lookup"><span data-stu-id="ff6ed-179">84</span></span>|<span data-ttu-id="ff6ed-180">Wszystkie wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="ff6ed-181">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-181">The following table shows the event data:</span></span>

|<span data-ttu-id="ff6ed-182">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ff6ed-182">Field name</span></span>|<span data-ttu-id="ff6ed-183">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ff6ed-183">Data type</span></span>|<span data-ttu-id="ff6ed-184">Opis</span><span class="sxs-lookup"><span data-stu-id="ff6ed-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ff6ed-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-185">AppDomainID</span></span>|<span data-ttu-id="ff6ed-186">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-186">win:UInt64</span></span>|<span data-ttu-id="ff6ed-187">Identyfikator domeny, dla której zgłaszane jest użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="ff6ed-188">Ocalałe</span><span class="sxs-lookup"><span data-stu-id="ff6ed-188">Survived</span></span>|<span data-ttu-id="ff6ed-189">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-189">win:UInt64</span></span>|<span data-ttu-id="ff6ed-190">Liczba bajtów przeprowadzonych po ostatniej kolekcji i, które są znane przez tę domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="ff6ed-191">Ta liczba jest dokładna i kompletna po pełnej kolekcji, ale może być niekompletna po kolekcji tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="ff6ed-192">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="ff6ed-192">ProcessSurvived</span></span>|<span data-ttu-id="ff6ed-193">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-193">win:UInt64</span></span>|<span data-ttu-id="ff6ed-194">Całkowita liczba bajtów przeczytanych z ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="ff6ed-195">Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w zarządzanych stertach.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="ff6ed-196">Po zakończeniu zbierania danych tymczasowych ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w generacjach tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="ff6ed-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-197">ClrInstanceID</span></span>|<span data-ttu-id="ff6ed-198">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ff6ed-198">win:UInt16</span></span>|<span data-ttu-id="ff6ed-199">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="ff6ed-200">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="ff6ed-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="ff6ed-201">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ff6ed-202">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-202">Keyword for raising the event</span></span>|<span data-ttu-id="ff6ed-203">Poziom</span><span class="sxs-lookup"><span data-stu-id="ff6ed-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ff6ed-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ff6ed-205">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-205">Informational(4)</span></span>|
|<span data-ttu-id="ff6ed-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ff6ed-207">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-207">Informational(4)</span></span>|

<span data-ttu-id="ff6ed-208">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-208">The following table shows the event information:</span></span>

|<span data-ttu-id="ff6ed-209">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ff6ed-209">Event</span></span>|<span data-ttu-id="ff6ed-210">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-210">Event ID</span></span>|<span data-ttu-id="ff6ed-211">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="ff6ed-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="ff6ed-212">87</span><span class="sxs-lookup"><span data-stu-id="ff6ed-212">87</span></span>|<span data-ttu-id="ff6ed-213">Wątek przechodzi do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="ff6ed-214">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-214">The following table shows the event data:</span></span>

|<span data-ttu-id="ff6ed-215">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ff6ed-215">Field name</span></span>|<span data-ttu-id="ff6ed-216">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ff6ed-216">Data type</span></span>|<span data-ttu-id="ff6ed-217">Opis</span><span class="sxs-lookup"><span data-stu-id="ff6ed-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ff6ed-218">ThreadID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-218">ThreadID</span></span>|<span data-ttu-id="ff6ed-219">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-219">win:UInt64</span></span>|<span data-ttu-id="ff6ed-220">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-220">The thread identifier.</span></span>|
|<span data-ttu-id="ff6ed-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-221">AppDomainID</span></span>|<span data-ttu-id="ff6ed-222">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-222">win:UInt64</span></span>|<span data-ttu-id="ff6ed-223">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-223">The application domain identifier.</span></span>|
|<span data-ttu-id="ff6ed-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-224">ClrInstanceID</span></span>|<span data-ttu-id="ff6ed-225">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ff6ed-225">win:UInt16</span></span>|<span data-ttu-id="ff6ed-226">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="ff6ed-227">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="ff6ed-227">ThreadTerminated Event</span></span>

<span data-ttu-id="ff6ed-228">W poniższej tabeli przedstawiono słowo kluczowe i poziom:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ff6ed-229">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-229">Keyword for raising the event</span></span>|<span data-ttu-id="ff6ed-230">Poziom</span><span class="sxs-lookup"><span data-stu-id="ff6ed-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ff6ed-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ff6ed-232">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-232">Informational(4)</span></span>|
|<span data-ttu-id="ff6ed-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ff6ed-234">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="ff6ed-234">Informational(4)</span></span>|

<span data-ttu-id="ff6ed-235">W poniższej tabeli przedstawiono informacje o zdarzeniu:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-235">The following table shows the event information:</span></span>

|<span data-ttu-id="ff6ed-236">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ff6ed-236">Event</span></span>|<span data-ttu-id="ff6ed-237">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff6ed-237">Event ID</span></span>|<span data-ttu-id="ff6ed-238">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="ff6ed-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="ff6ed-239">86</span><span class="sxs-lookup"><span data-stu-id="ff6ed-239">86</span></span>|<span data-ttu-id="ff6ed-240">Wątek kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-240">A thread terminates.</span></span>|

<span data-ttu-id="ff6ed-241">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="ff6ed-241">The following table shows the event data:</span></span>

|<span data-ttu-id="ff6ed-242">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ff6ed-242">Field name</span></span>|<span data-ttu-id="ff6ed-243">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ff6ed-243">Data type</span></span>|<span data-ttu-id="ff6ed-244">Opis</span><span class="sxs-lookup"><span data-stu-id="ff6ed-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ff6ed-245">ThreadID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-245">ThreadID</span></span>|<span data-ttu-id="ff6ed-246">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-246">win:UInt64</span></span>|<span data-ttu-id="ff6ed-247">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-247">The thread identifier.</span></span>|
|<span data-ttu-id="ff6ed-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-248">AppDomainID</span></span>|<span data-ttu-id="ff6ed-249">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ff6ed-249">win:UInt64</span></span>|<span data-ttu-id="ff6ed-250">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-250">The application domain identifier.</span></span>|
|<span data-ttu-id="ff6ed-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ff6ed-251">ClrInstanceID</span></span>|<span data-ttu-id="ff6ed-252">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ff6ed-252">win:UInt16</span></span>|<span data-ttu-id="ff6ed-253">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ff6ed-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ff6ed-254">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff6ed-254">See also</span></span>

- [<span data-ttu-id="ff6ed-255">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="ff6ed-255">CLR ETW Events</span></span>](clr-etw-events.md)
