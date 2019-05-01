---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bb2b0dd95877fc6492f6d23a19c14688cd78f7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788066"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="06e9a-102">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="06e9a-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="06e9a-103">Zdarzenia te zawierają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06e9a-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="06e9a-104">Można użyć tych zdarzeń, lub użyć zasobów domen aplikacji (ARM) funkcji monitorowania można uzyskać te same informacje.</span><span class="sxs-lookup"><span data-stu-id="06e9a-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="06e9a-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="06e9a-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="06e9a-106">Threadcreated — zdarzenie</span><span class="sxs-lookup"><span data-stu-id="06e9a-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="06e9a-107">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="06e9a-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="06e9a-108">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="06e9a-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="06e9a-109">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="06e9a-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="06e9a-110">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="06e9a-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="06e9a-111">Threadcreated — zdarzenie</span><span class="sxs-lookup"><span data-stu-id="06e9a-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="06e9a-112">To zdarzenie jest także inicjowane w obszarze dostawcy podsumowań jako `ThreadDC` (w obszarze `AppDomainResourceManagementRundownKeyword` — słowo kluczowe).</span><span class="sxs-lookup"><span data-stu-id="06e9a-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="06e9a-113">Jest to jedyne zdarzenie, które jest wywoływane w obszarze dostawcy podsumowań w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="06e9a-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="06e9a-114">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="06e9a-115">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="06e9a-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="06e9a-116">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-116">Keyword for raising the event</span></span>|<span data-ttu-id="06e9a-117">Poziom</span><span class="sxs-lookup"><span data-stu-id="06e9a-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="06e9a-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="06e9a-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="06e9a-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="06e9a-119">Informational(4)</span></span>|  
|<span data-ttu-id="06e9a-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="06e9a-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="06e9a-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="06e9a-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="06e9a-122">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="06e9a-123">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="06e9a-123">Event</span></span>|<span data-ttu-id="06e9a-124">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-124">Event ID</span></span>|<span data-ttu-id="06e9a-125">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="06e9a-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="06e9a-126">85</span><span class="sxs-lookup"><span data-stu-id="06e9a-126">85</span></span>|<span data-ttu-id="06e9a-127">Wątek został utworzony dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06e9a-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="06e9a-128">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="06e9a-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="06e9a-129">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="06e9a-129">Field name</span></span>|<span data-ttu-id="06e9a-130">Typ danych</span><span class="sxs-lookup"><span data-stu-id="06e9a-130">Data type</span></span>|<span data-ttu-id="06e9a-131">Opis</span><span class="sxs-lookup"><span data-stu-id="06e9a-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="06e9a-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="06e9a-132">ThreadID</span></span>|<span data-ttu-id="06e9a-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-133">win:UInt64</span></span>|<span data-ttu-id="06e9a-134">Identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="06e9a-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="06e9a-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="06e9a-135">AppDomainID</span></span>|<span data-ttu-id="06e9a-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-136">win:UInt64</span></span>|<span data-ttu-id="06e9a-137">Identyfikator wątku, który jest zgłaszany działania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06e9a-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="06e9a-138">Flagi</span><span class="sxs-lookup"><span data-stu-id="06e9a-138">Flags</span></span>|<span data-ttu-id="06e9a-139">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="06e9a-139">win:UInt32</span></span>|<span data-ttu-id="06e9a-140">Wątek flagi tworzenia.</span><span class="sxs-lookup"><span data-stu-id="06e9a-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="06e9a-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="06e9a-141">ManagedThreadIndex</span></span>|<span data-ttu-id="06e9a-142">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="06e9a-142">win:UInt32</span></span>|<span data-ttu-id="06e9a-143">Zarządzane indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="06e9a-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="06e9a-144">Elementu OSThreadID</span><span class="sxs-lookup"><span data-stu-id="06e9a-144">OSThreadID</span></span>|<span data-ttu-id="06e9a-145">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="06e9a-145">win:UInt32</span></span>|<span data-ttu-id="06e9a-146">Identyfikator wątku, który został utworzony w system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="06e9a-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="06e9a-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="06e9a-147">ClrInstanceID</span></span>|<span data-ttu-id="06e9a-148">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="06e9a-148">win:UInt16</span></span>|<span data-ttu-id="06e9a-149">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="06e9a-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="06e9a-150">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="06e9a-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="06e9a-151">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="06e9a-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="06e9a-152">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="06e9a-153">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-153">Keyword for raising the event</span></span>|<span data-ttu-id="06e9a-154">Poziom</span><span class="sxs-lookup"><span data-stu-id="06e9a-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="06e9a-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="06e9a-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="06e9a-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="06e9a-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="06e9a-157">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="06e9a-158">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="06e9a-158">Event</span></span>|<span data-ttu-id="06e9a-159">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-159">Event ID</span></span>|<span data-ttu-id="06e9a-160">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="06e9a-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="06e9a-161">83</span><span class="sxs-lookup"><span data-stu-id="06e9a-161">83</span></span>|<span data-ttu-id="06e9a-162">Co 4 MB pamięci (w przybliżeniu) jest przydzielany w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06e9a-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="06e9a-163">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="06e9a-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="06e9a-164">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="06e9a-164">Field name</span></span>|<span data-ttu-id="06e9a-165">Typ danych</span><span class="sxs-lookup"><span data-stu-id="06e9a-165">Data type</span></span>|<span data-ttu-id="06e9a-166">Opis</span><span class="sxs-lookup"><span data-stu-id="06e9a-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="06e9a-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="06e9a-167">AppDomainID</span></span>|<span data-ttu-id="06e9a-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-168">win:UInt64</span></span>|<span data-ttu-id="06e9a-169">Identyfikator domeny aplikacji do zasobu, który jest zgłaszany użycia.</span><span class="sxs-lookup"><span data-stu-id="06e9a-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="06e9a-170">przydzielona</span><span class="sxs-lookup"><span data-stu-id="06e9a-170">Allocated</span></span>|<span data-ttu-id="06e9a-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-171">win:UInt64</span></span>|<span data-ttu-id="06e9a-172">Całkowita liczba bajtów przydzielonych w tej domenie aplikacji, od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowany).</span><span class="sxs-lookup"><span data-stu-id="06e9a-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="06e9a-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="06e9a-173">ClrInstanceID</span></span>|<span data-ttu-id="06e9a-174">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="06e9a-174">win:UInt16</span></span>|<span data-ttu-id="06e9a-175">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="06e9a-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="06e9a-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="06e9a-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="06e9a-177">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="06e9a-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="06e9a-178">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="06e9a-179">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-179">Keyword for raising the event</span></span>|<span data-ttu-id="06e9a-180">Poziom</span><span class="sxs-lookup"><span data-stu-id="06e9a-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="06e9a-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="06e9a-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="06e9a-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="06e9a-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="06e9a-183">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="06e9a-184">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="06e9a-184">Event</span></span>|<span data-ttu-id="06e9a-185">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-185">Event ID</span></span>|<span data-ttu-id="06e9a-186">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="06e9a-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="06e9a-187">84</span><span class="sxs-lookup"><span data-stu-id="06e9a-187">84</span></span>|<span data-ttu-id="06e9a-188">Każdy wyrzucania elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="06e9a-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="06e9a-189">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="06e9a-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="06e9a-190">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="06e9a-190">Field name</span></span>|<span data-ttu-id="06e9a-191">Typ danych</span><span class="sxs-lookup"><span data-stu-id="06e9a-191">Data type</span></span>|<span data-ttu-id="06e9a-192">Opis</span><span class="sxs-lookup"><span data-stu-id="06e9a-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="06e9a-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="06e9a-193">AppDomainID</span></span>|<span data-ttu-id="06e9a-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-194">win:UInt64</span></span>|<span data-ttu-id="06e9a-195">Identyfikator domeny dla zasobu, który jest zgłaszany użycia.</span><span class="sxs-lookup"><span data-stu-id="06e9a-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="06e9a-196">Przetrwały</span><span class="sxs-lookup"><span data-stu-id="06e9a-196">Survived</span></span>|<span data-ttu-id="06e9a-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-197">win:UInt64</span></span>|<span data-ttu-id="06e9a-198">Liczba bajtów, które przetrwały od ostatniego zebrania i które są znane przez tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06e9a-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="06e9a-199">Ta liczba jest dokładne i kompletne po pełnej kolekcji, ale mogą być niekompletne po pobraniu tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="06e9a-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="06e9a-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="06e9a-200">ProcessSurvived</span></span>|<span data-ttu-id="06e9a-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-201">win:UInt64</span></span>|<span data-ttu-id="06e9a-202">Całkowita liczba bajtów, które przetrwały od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="06e9a-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="06e9a-203">Po pełnego ta liczba przedstawia liczbę bajtów przechowywanych na żywo w zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="06e9a-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="06e9a-204">Po pobraniu tymczasowych ten numer reprezentuje liczbę bajtów przechowywanych na żywo w generacje efemeryczne.</span><span class="sxs-lookup"><span data-stu-id="06e9a-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="06e9a-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="06e9a-205">ClrInstanceID</span></span>|<span data-ttu-id="06e9a-206">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="06e9a-206">win:UInt16</span></span>|<span data-ttu-id="06e9a-207">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="06e9a-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="06e9a-208">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="06e9a-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="06e9a-209">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="06e9a-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="06e9a-210">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="06e9a-211">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-211">Keyword for raising the event</span></span>|<span data-ttu-id="06e9a-212">Poziom</span><span class="sxs-lookup"><span data-stu-id="06e9a-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="06e9a-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="06e9a-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="06e9a-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="06e9a-214">Informational(4)</span></span>|  
|<span data-ttu-id="06e9a-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="06e9a-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="06e9a-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="06e9a-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="06e9a-217">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="06e9a-218">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="06e9a-218">Event</span></span>|<span data-ttu-id="06e9a-219">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-219">Event ID</span></span>|<span data-ttu-id="06e9a-220">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="06e9a-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="06e9a-221">87</span><span class="sxs-lookup"><span data-stu-id="06e9a-221">87</span></span>|<span data-ttu-id="06e9a-222">Wątek wchodzi domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06e9a-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="06e9a-223">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="06e9a-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="06e9a-224">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="06e9a-224">Field name</span></span>|<span data-ttu-id="06e9a-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="06e9a-225">Data type</span></span>|<span data-ttu-id="06e9a-226">Opis</span><span class="sxs-lookup"><span data-stu-id="06e9a-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="06e9a-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="06e9a-227">ThreadID</span></span>|<span data-ttu-id="06e9a-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-228">win:UInt64</span></span>|<span data-ttu-id="06e9a-229">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="06e9a-229">The thread identifier.</span></span>|  
|<span data-ttu-id="06e9a-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="06e9a-230">AppDomainID</span></span>|<span data-ttu-id="06e9a-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-231">win:UInt64</span></span>|<span data-ttu-id="06e9a-232">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06e9a-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="06e9a-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="06e9a-233">ClrInstanceID</span></span>|<span data-ttu-id="06e9a-234">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="06e9a-234">win:UInt16</span></span>|<span data-ttu-id="06e9a-235">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="06e9a-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="06e9a-236">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="06e9a-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="06e9a-237">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="06e9a-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="06e9a-238">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="06e9a-239">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-239">Keyword for raising the event</span></span>|<span data-ttu-id="06e9a-240">Poziom</span><span class="sxs-lookup"><span data-stu-id="06e9a-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="06e9a-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="06e9a-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="06e9a-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="06e9a-242">Informational(4)</span></span>|  
|<span data-ttu-id="06e9a-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="06e9a-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="06e9a-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="06e9a-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="06e9a-245">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="06e9a-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="06e9a-246">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="06e9a-246">Event</span></span>|<span data-ttu-id="06e9a-247">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="06e9a-247">Event ID</span></span>|<span data-ttu-id="06e9a-248">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="06e9a-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="06e9a-249">86</span><span class="sxs-lookup"><span data-stu-id="06e9a-249">86</span></span>|<span data-ttu-id="06e9a-250">Wątek kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="06e9a-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="06e9a-251">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="06e9a-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="06e9a-252">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="06e9a-252">Field name</span></span>|<span data-ttu-id="06e9a-253">Typ danych</span><span class="sxs-lookup"><span data-stu-id="06e9a-253">Data type</span></span>|<span data-ttu-id="06e9a-254">Opis</span><span class="sxs-lookup"><span data-stu-id="06e9a-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="06e9a-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="06e9a-255">ThreadID</span></span>|<span data-ttu-id="06e9a-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-256">win:UInt64</span></span>|<span data-ttu-id="06e9a-257">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="06e9a-257">The thread identifier.</span></span>|  
|<span data-ttu-id="06e9a-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="06e9a-258">AppDomainID</span></span>|<span data-ttu-id="06e9a-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="06e9a-259">win:UInt64</span></span>|<span data-ttu-id="06e9a-260">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06e9a-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="06e9a-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="06e9a-261">ClrInstanceID</span></span>|<span data-ttu-id="06e9a-262">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="06e9a-262">win:UInt16</span></span>|<span data-ttu-id="06e9a-263">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="06e9a-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06e9a-264">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06e9a-264">See also</span></span>

- [<span data-ttu-id="06e9a-265">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="06e9a-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
