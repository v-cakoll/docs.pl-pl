---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e4002ae248022a9e4380c79174109494b5e4ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046767"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="aefd9-102">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="aefd9-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a><span data-ttu-id="aefd9-103">Te zdarzenia zapewniają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aefd9-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="aefd9-104">Możesz użyć tych zdarzeń lub użyć funkcji monitorowania zasobów domeny aplikacji (ARM), aby uzyskać te same informacje.</span><span class="sxs-lookup"><span data-stu-id="aefd9-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="aefd9-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="aefd9-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="aefd9-106">Zdarzenie ThreadCreated —</span><span class="sxs-lookup"><span data-stu-id="aefd9-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="aefd9-107">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="aefd9-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="aefd9-108">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="aefd9-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="aefd9-109">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="aefd9-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="aefd9-110">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="aefd9-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="aefd9-111">Zdarzenie ThreadCreated —</span><span class="sxs-lookup"><span data-stu-id="aefd9-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="aefd9-112">To zdarzenie jest również zgłaszane w ramach dostawcy uwalniania `ThreadDC` jako ( `AppDomainResourceManagementRundownKeyword` pod słowem kluczowym).</span><span class="sxs-lookup"><span data-stu-id="aefd9-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="aefd9-113">Jest to jedyne zdarzenie zgłaszane w ramach dostawcy uwalniania w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="aefd9-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="aefd9-114">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="aefd9-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="aefd9-115">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="aefd9-115">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="aefd9-116">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-116">Keyword for raising the event</span></span>|<span data-ttu-id="aefd9-117">Poziom</span><span class="sxs-lookup"><span data-stu-id="aefd9-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="aefd9-118">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aefd9-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aefd9-119">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="aefd9-119">Informational(4)</span></span>|  
|<span data-ttu-id="aefd9-120">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="aefd9-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="aefd9-121">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="aefd9-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="aefd9-122">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="aefd9-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="aefd9-123">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aefd9-123">Event</span></span>|<span data-ttu-id="aefd9-124">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-124">Event ID</span></span>|<span data-ttu-id="aefd9-125">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="aefd9-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="aefd9-126">85</span><span class="sxs-lookup"><span data-stu-id="aefd9-126">85</span></span>|<span data-ttu-id="aefd9-127">Utworzono wątek dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aefd9-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="aefd9-128">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aefd9-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="aefd9-129">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="aefd9-129">Field name</span></span>|<span data-ttu-id="aefd9-130">Typ danych</span><span class="sxs-lookup"><span data-stu-id="aefd9-130">Data type</span></span>|<span data-ttu-id="aefd9-131">Opis</span><span class="sxs-lookup"><span data-stu-id="aefd9-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="aefd9-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="aefd9-132">ThreadID</span></span>|<span data-ttu-id="aefd9-133">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-133">win:UInt64</span></span>|<span data-ttu-id="aefd9-134">Identyfikator utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="aefd9-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="aefd9-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aefd9-135">AppDomainID</span></span>|<span data-ttu-id="aefd9-136">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-136">win:UInt64</span></span>|<span data-ttu-id="aefd9-137">Identyfikator domeny aplikacji, dla której jest zgłaszane działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="aefd9-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="aefd9-138">Flagi</span><span class="sxs-lookup"><span data-stu-id="aefd9-138">Flags</span></span>|<span data-ttu-id="aefd9-139">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="aefd9-139">win:UInt32</span></span>|<span data-ttu-id="aefd9-140">Flagi tworzenia wątku.</span><span class="sxs-lookup"><span data-stu-id="aefd9-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="aefd9-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="aefd9-141">ManagedThreadIndex</span></span>|<span data-ttu-id="aefd9-142">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="aefd9-142">win:UInt32</span></span>|<span data-ttu-id="aefd9-143">Zarządzany indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="aefd9-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="aefd9-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="aefd9-144">OSThreadID</span></span>|<span data-ttu-id="aefd9-145">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="aefd9-145">win:UInt32</span></span>|<span data-ttu-id="aefd9-146">Identyfikator systemu operacyjnego wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="aefd9-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="aefd9-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aefd9-147">ClrInstanceID</span></span>|<span data-ttu-id="aefd9-148">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aefd9-148">win:UInt16</span></span>|<span data-ttu-id="aefd9-149">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aefd9-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="aefd9-150">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="aefd9-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="aefd9-151">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="aefd9-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="aefd9-152">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="aefd9-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="aefd9-153">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-153">Keyword for raising the event</span></span>|<span data-ttu-id="aefd9-154">Poziom</span><span class="sxs-lookup"><span data-stu-id="aefd9-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="aefd9-155">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aefd9-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aefd9-156">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="aefd9-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="aefd9-157">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="aefd9-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="aefd9-158">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aefd9-158">Event</span></span>|<span data-ttu-id="aefd9-159">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-159">Event ID</span></span>|<span data-ttu-id="aefd9-160">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="aefd9-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="aefd9-161">83</span><span class="sxs-lookup"><span data-stu-id="aefd9-161">83</span></span>|<span data-ttu-id="aefd9-162">Co 4 MB pamięci (w przybliżeniu) jest przypisywany w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aefd9-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="aefd9-163">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aefd9-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="aefd9-164">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="aefd9-164">Field name</span></span>|<span data-ttu-id="aefd9-165">Typ danych</span><span class="sxs-lookup"><span data-stu-id="aefd9-165">Data type</span></span>|<span data-ttu-id="aefd9-166">Opis</span><span class="sxs-lookup"><span data-stu-id="aefd9-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="aefd9-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aefd9-167">AppDomainID</span></span>|<span data-ttu-id="aefd9-168">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-168">win:UInt64</span></span>|<span data-ttu-id="aefd9-169">Identyfikator domeny aplikacji, dla której zgłaszane jest użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="aefd9-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="aefd9-170">Rozdziela</span><span class="sxs-lookup"><span data-stu-id="aefd9-170">Allocated</span></span>|<span data-ttu-id="aefd9-171">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-171">win:UInt64</span></span>|<span data-ttu-id="aefd9-172">Całkowita liczba bajtów przydzielono w tej domenie aplikacji od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowana).</span><span class="sxs-lookup"><span data-stu-id="aefd9-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="aefd9-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aefd9-173">ClrInstanceID</span></span>|<span data-ttu-id="aefd9-174">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aefd9-174">win:UInt16</span></span>|<span data-ttu-id="aefd9-175">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aefd9-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="aefd9-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="aefd9-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="aefd9-177">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="aefd9-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="aefd9-178">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="aefd9-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="aefd9-179">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-179">Keyword for raising the event</span></span>|<span data-ttu-id="aefd9-180">Poziom</span><span class="sxs-lookup"><span data-stu-id="aefd9-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="aefd9-181">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aefd9-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aefd9-182">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="aefd9-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="aefd9-183">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="aefd9-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="aefd9-184">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aefd9-184">Event</span></span>|<span data-ttu-id="aefd9-185">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-185">Event ID</span></span>|<span data-ttu-id="aefd9-186">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="aefd9-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="aefd9-187">84</span><span class="sxs-lookup"><span data-stu-id="aefd9-187">84</span></span>|<span data-ttu-id="aefd9-188">Wszystkie wyrzucanie elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="aefd9-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="aefd9-189">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aefd9-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="aefd9-190">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="aefd9-190">Field name</span></span>|<span data-ttu-id="aefd9-191">Typ danych</span><span class="sxs-lookup"><span data-stu-id="aefd9-191">Data type</span></span>|<span data-ttu-id="aefd9-192">Opis</span><span class="sxs-lookup"><span data-stu-id="aefd9-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="aefd9-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aefd9-193">AppDomainID</span></span>|<span data-ttu-id="aefd9-194">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-194">win:UInt64</span></span>|<span data-ttu-id="aefd9-195">Identyfikator domeny, dla której zgłaszane jest użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="aefd9-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="aefd9-196">Ocalałe</span><span class="sxs-lookup"><span data-stu-id="aefd9-196">Survived</span></span>|<span data-ttu-id="aefd9-197">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-197">win:UInt64</span></span>|<span data-ttu-id="aefd9-198">Liczba bajtów przeprowadzonych po ostatniej kolekcji i, które są znane przez tę domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aefd9-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="aefd9-199">Ta liczba jest dokładna i kompletna po pełnej kolekcji, ale może być niekompletna po kolekcji tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="aefd9-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="aefd9-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="aefd9-200">ProcessSurvived</span></span>|<span data-ttu-id="aefd9-201">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-201">win:UInt64</span></span>|<span data-ttu-id="aefd9-202">Całkowita liczba bajtów przeczytanych z ostatniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="aefd9-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="aefd9-203">Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w zarządzanych stertach.</span><span class="sxs-lookup"><span data-stu-id="aefd9-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="aefd9-204">Po zakończeniu zbierania danych tymczasowych ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w generacjach tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="aefd9-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="aefd9-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aefd9-205">ClrInstanceID</span></span>|<span data-ttu-id="aefd9-206">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aefd9-206">win:UInt16</span></span>|<span data-ttu-id="aefd9-207">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aefd9-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="aefd9-208">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="aefd9-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="aefd9-209">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="aefd9-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="aefd9-210">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="aefd9-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="aefd9-211">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-211">Keyword for raising the event</span></span>|<span data-ttu-id="aefd9-212">Poziom</span><span class="sxs-lookup"><span data-stu-id="aefd9-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="aefd9-213">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aefd9-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aefd9-214">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="aefd9-214">Informational(4)</span></span>|  
|<span data-ttu-id="aefd9-215">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="aefd9-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="aefd9-216">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="aefd9-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="aefd9-217">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="aefd9-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="aefd9-218">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aefd9-218">Event</span></span>|<span data-ttu-id="aefd9-219">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-219">Event ID</span></span>|<span data-ttu-id="aefd9-220">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="aefd9-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="aefd9-221">87</span><span class="sxs-lookup"><span data-stu-id="aefd9-221">87</span></span>|<span data-ttu-id="aefd9-222">Wątek przechodzi do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aefd9-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="aefd9-223">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aefd9-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="aefd9-224">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="aefd9-224">Field name</span></span>|<span data-ttu-id="aefd9-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="aefd9-225">Data type</span></span>|<span data-ttu-id="aefd9-226">Opis</span><span class="sxs-lookup"><span data-stu-id="aefd9-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="aefd9-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="aefd9-227">ThreadID</span></span>|<span data-ttu-id="aefd9-228">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-228">win:UInt64</span></span>|<span data-ttu-id="aefd9-229">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="aefd9-229">The thread identifier.</span></span>|  
|<span data-ttu-id="aefd9-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aefd9-230">AppDomainID</span></span>|<span data-ttu-id="aefd9-231">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-231">win:UInt64</span></span>|<span data-ttu-id="aefd9-232">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aefd9-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="aefd9-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aefd9-233">ClrInstanceID</span></span>|<span data-ttu-id="aefd9-234">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aefd9-234">win:UInt16</span></span>|<span data-ttu-id="aefd9-235">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aefd9-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="aefd9-236">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="aefd9-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="aefd9-237">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="aefd9-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="aefd9-238">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="aefd9-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="aefd9-239">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-239">Keyword for raising the event</span></span>|<span data-ttu-id="aefd9-240">Poziom</span><span class="sxs-lookup"><span data-stu-id="aefd9-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="aefd9-241">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aefd9-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aefd9-242">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="aefd9-242">Informational(4)</span></span>|  
|<span data-ttu-id="aefd9-243">`ThreadingKeyword`0x10000</span><span class="sxs-lookup"><span data-stu-id="aefd9-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="aefd9-244">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="aefd9-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="aefd9-245">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="aefd9-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="aefd9-246">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aefd9-246">Event</span></span>|<span data-ttu-id="aefd9-247">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="aefd9-247">Event ID</span></span>|<span data-ttu-id="aefd9-248">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="aefd9-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="aefd9-249">86</span><span class="sxs-lookup"><span data-stu-id="aefd9-249">86</span></span>|<span data-ttu-id="aefd9-250">Wątek kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="aefd9-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="aefd9-251">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="aefd9-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="aefd9-252">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="aefd9-252">Field name</span></span>|<span data-ttu-id="aefd9-253">Typ danych</span><span class="sxs-lookup"><span data-stu-id="aefd9-253">Data type</span></span>|<span data-ttu-id="aefd9-254">Opis</span><span class="sxs-lookup"><span data-stu-id="aefd9-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="aefd9-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="aefd9-255">ThreadID</span></span>|<span data-ttu-id="aefd9-256">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-256">win:UInt64</span></span>|<span data-ttu-id="aefd9-257">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="aefd9-257">The thread identifier.</span></span>|  
|<span data-ttu-id="aefd9-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aefd9-258">AppDomainID</span></span>|<span data-ttu-id="aefd9-259">win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aefd9-259">win:UInt64</span></span>|<span data-ttu-id="aefd9-260">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aefd9-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="aefd9-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aefd9-261">ClrInstanceID</span></span>|<span data-ttu-id="aefd9-262">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aefd9-262">win:UInt16</span></span>|<span data-ttu-id="aefd9-263">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aefd9-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aefd9-264">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aefd9-264">See also</span></span>

- [<span data-ttu-id="aefd9-265">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="aefd9-265">CLR ETW Events</span></span>](clr-etw-events.md)
