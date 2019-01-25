---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8442b8723476984b90f740beac912688719f1791
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689838"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="0a071-102">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="0a071-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="0a071-103">Zdarzenia te zawierają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a071-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="0a071-104">Można użyć tych zdarzeń, lub użyć zasobów domen aplikacji (ARM) funkcji monitorowania można uzyskać te same informacje.</span><span class="sxs-lookup"><span data-stu-id="0a071-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="0a071-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="0a071-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="0a071-106">Threadcreated — zdarzenie</span><span class="sxs-lookup"><span data-stu-id="0a071-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="0a071-107">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="0a071-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="0a071-108">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="0a071-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="0a071-109">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="0a071-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="0a071-110">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="0a071-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="0a071-111">Threadcreated — zdarzenie</span><span class="sxs-lookup"><span data-stu-id="0a071-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="0a071-112">To zdarzenie jest także inicjowane w obszarze dostawcy podsumowań jako `ThreadDC` (w obszarze `AppDomainResourceManagementRundownKeyword` — słowo kluczowe).</span><span class="sxs-lookup"><span data-stu-id="0a071-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="0a071-113">Jest to jedyne zdarzenie, które jest wywoływane w obszarze dostawcy podsumowań w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="0a071-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="0a071-114">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="0a071-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="0a071-115">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="0a071-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0a071-116">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-116">Keyword for raising the event</span></span>|<span data-ttu-id="0a071-117">Poziom</span><span class="sxs-lookup"><span data-stu-id="0a071-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0a071-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0a071-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0a071-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0a071-119">Informational(4)</span></span>|  
|<span data-ttu-id="0a071-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0a071-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0a071-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0a071-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="0a071-122">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="0a071-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0a071-123">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="0a071-123">Event</span></span>|<span data-ttu-id="0a071-124">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-124">Event ID</span></span>|<span data-ttu-id="0a071-125">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="0a071-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="0a071-126">85</span><span class="sxs-lookup"><span data-stu-id="0a071-126">85</span></span>|<span data-ttu-id="0a071-127">Wątek został utworzony dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a071-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="0a071-128">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0a071-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0a071-129">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="0a071-129">Field name</span></span>|<span data-ttu-id="0a071-130">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0a071-130">Data type</span></span>|<span data-ttu-id="0a071-131">Opis</span><span class="sxs-lookup"><span data-stu-id="0a071-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0a071-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="0a071-132">ThreadID</span></span>|<span data-ttu-id="0a071-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-133">win:UInt64</span></span>|<span data-ttu-id="0a071-134">Identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="0a071-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="0a071-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0a071-135">AppDomainID</span></span>|<span data-ttu-id="0a071-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-136">win:UInt64</span></span>|<span data-ttu-id="0a071-137">Identyfikator wątku, który jest zgłaszany działania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a071-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="0a071-138">Flagi</span><span class="sxs-lookup"><span data-stu-id="0a071-138">Flags</span></span>|<span data-ttu-id="0a071-139">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="0a071-139">win:UInt32</span></span>|<span data-ttu-id="0a071-140">Wątek flagi tworzenia.</span><span class="sxs-lookup"><span data-stu-id="0a071-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="0a071-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="0a071-141">ManagedThreadIndex</span></span>|<span data-ttu-id="0a071-142">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="0a071-142">win:UInt32</span></span>|<span data-ttu-id="0a071-143">Zarządzane indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="0a071-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="0a071-144">Elementu OSThreadID</span><span class="sxs-lookup"><span data-stu-id="0a071-144">OSThreadID</span></span>|<span data-ttu-id="0a071-145">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="0a071-145">win:UInt32</span></span>|<span data-ttu-id="0a071-146">Identyfikator wątku, który został utworzony w system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="0a071-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="0a071-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0a071-147">ClrInstanceID</span></span>|<span data-ttu-id="0a071-148">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="0a071-148">win:UInt16</span></span>|<span data-ttu-id="0a071-149">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0a071-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0a071-150">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="0a071-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="0a071-151">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="0a071-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="0a071-152">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="0a071-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0a071-153">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-153">Keyword for raising the event</span></span>|<span data-ttu-id="0a071-154">Poziom</span><span class="sxs-lookup"><span data-stu-id="0a071-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0a071-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0a071-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0a071-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0a071-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="0a071-157">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="0a071-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0a071-158">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="0a071-158">Event</span></span>|<span data-ttu-id="0a071-159">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-159">Event ID</span></span>|<span data-ttu-id="0a071-160">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="0a071-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="0a071-161">83</span><span class="sxs-lookup"><span data-stu-id="0a071-161">83</span></span>|<span data-ttu-id="0a071-162">Co 4 MB pamięci (w przybliżeniu) jest przydzielany w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a071-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="0a071-163">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0a071-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0a071-164">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="0a071-164">Field name</span></span>|<span data-ttu-id="0a071-165">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0a071-165">Data type</span></span>|<span data-ttu-id="0a071-166">Opis</span><span class="sxs-lookup"><span data-stu-id="0a071-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0a071-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0a071-167">AppDomainID</span></span>|<span data-ttu-id="0a071-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-168">win:UInt64</span></span>|<span data-ttu-id="0a071-169">Identyfikator domeny aplikacji do zasobu, który jest zgłaszany użycia.</span><span class="sxs-lookup"><span data-stu-id="0a071-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="0a071-170">przydzielona</span><span class="sxs-lookup"><span data-stu-id="0a071-170">Allocated</span></span>|<span data-ttu-id="0a071-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-171">win:UInt64</span></span>|<span data-ttu-id="0a071-172">Całkowita liczba bajtów przydzielonych w tej domenie aplikacji, od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowany).</span><span class="sxs-lookup"><span data-stu-id="0a071-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="0a071-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0a071-173">ClrInstanceID</span></span>|<span data-ttu-id="0a071-174">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="0a071-174">win:UInt16</span></span>|<span data-ttu-id="0a071-175">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0a071-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0a071-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="0a071-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="0a071-177">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="0a071-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="0a071-178">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="0a071-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0a071-179">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-179">Keyword for raising the event</span></span>|<span data-ttu-id="0a071-180">Poziom</span><span class="sxs-lookup"><span data-stu-id="0a071-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0a071-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0a071-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0a071-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0a071-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="0a071-183">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="0a071-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0a071-184">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="0a071-184">Event</span></span>|<span data-ttu-id="0a071-185">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-185">Event ID</span></span>|<span data-ttu-id="0a071-186">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="0a071-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="0a071-187">84</span><span class="sxs-lookup"><span data-stu-id="0a071-187">84</span></span>|<span data-ttu-id="0a071-188">Każdy wyrzucania elementów bezużytecznych zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="0a071-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="0a071-189">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0a071-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0a071-190">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="0a071-190">Field name</span></span>|<span data-ttu-id="0a071-191">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0a071-191">Data type</span></span>|<span data-ttu-id="0a071-192">Opis</span><span class="sxs-lookup"><span data-stu-id="0a071-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0a071-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0a071-193">AppDomainID</span></span>|<span data-ttu-id="0a071-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-194">win:UInt64</span></span>|<span data-ttu-id="0a071-195">Identyfikator domeny dla zasobu, który jest zgłaszany użycia.</span><span class="sxs-lookup"><span data-stu-id="0a071-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="0a071-196">Przetrwały</span><span class="sxs-lookup"><span data-stu-id="0a071-196">Survived</span></span>|<span data-ttu-id="0a071-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-197">win:UInt64</span></span>|<span data-ttu-id="0a071-198">Liczba bajtów, które przetrwały od ostatniego zebrania i które są znane przez tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a071-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="0a071-199">Ta liczba jest dokładne i kompletne po pełnej kolekcji, ale mogą być niekompletne po pobraniu tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="0a071-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="0a071-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="0a071-200">ProcessSurvived</span></span>|<span data-ttu-id="0a071-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-201">win:UInt64</span></span>|<span data-ttu-id="0a071-202">Całkowita liczba bajtów, które przetrwały od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="0a071-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="0a071-203">Po pełnego ta liczba przedstawia liczbę bajtów przechowywanych na żywo w zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="0a071-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="0a071-204">Po pobraniu tymczasowych ten numer reprezentuje liczbę bajtów przechowywanych na żywo w generacje efemeryczne.</span><span class="sxs-lookup"><span data-stu-id="0a071-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="0a071-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0a071-205">ClrInstanceID</span></span>|<span data-ttu-id="0a071-206">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="0a071-206">win:UInt16</span></span>|<span data-ttu-id="0a071-207">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0a071-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0a071-208">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="0a071-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="0a071-209">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="0a071-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="0a071-210">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="0a071-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0a071-211">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-211">Keyword for raising the event</span></span>|<span data-ttu-id="0a071-212">Poziom</span><span class="sxs-lookup"><span data-stu-id="0a071-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0a071-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0a071-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0a071-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0a071-214">Informational(4)</span></span>|  
|<span data-ttu-id="0a071-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0a071-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0a071-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0a071-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="0a071-217">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="0a071-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0a071-218">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="0a071-218">Event</span></span>|<span data-ttu-id="0a071-219">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-219">Event ID</span></span>|<span data-ttu-id="0a071-220">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="0a071-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="0a071-221">87</span><span class="sxs-lookup"><span data-stu-id="0a071-221">87</span></span>|<span data-ttu-id="0a071-222">Wątek wchodzi domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a071-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="0a071-223">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0a071-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0a071-224">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="0a071-224">Field name</span></span>|<span data-ttu-id="0a071-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0a071-225">Data type</span></span>|<span data-ttu-id="0a071-226">Opis</span><span class="sxs-lookup"><span data-stu-id="0a071-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0a071-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="0a071-227">ThreadID</span></span>|<span data-ttu-id="0a071-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-228">win:UInt64</span></span>|<span data-ttu-id="0a071-229">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="0a071-229">The thread identifier.</span></span>|  
|<span data-ttu-id="0a071-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0a071-230">AppDomainID</span></span>|<span data-ttu-id="0a071-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-231">win:UInt64</span></span>|<span data-ttu-id="0a071-232">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a071-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="0a071-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0a071-233">ClrInstanceID</span></span>|<span data-ttu-id="0a071-234">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="0a071-234">win:UInt16</span></span>|<span data-ttu-id="0a071-235">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0a071-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0a071-236">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="0a071-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="0a071-237">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="0a071-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="0a071-238">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="0a071-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0a071-239">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-239">Keyword for raising the event</span></span>|<span data-ttu-id="0a071-240">Poziom</span><span class="sxs-lookup"><span data-stu-id="0a071-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0a071-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="0a071-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="0a071-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0a071-242">Informational(4)</span></span>|  
|<span data-ttu-id="0a071-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0a071-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0a071-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="0a071-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="0a071-245">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="0a071-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0a071-246">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="0a071-246">Event</span></span>|<span data-ttu-id="0a071-247">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0a071-247">Event ID</span></span>|<span data-ttu-id="0a071-248">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="0a071-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="0a071-249">86</span><span class="sxs-lookup"><span data-stu-id="0a071-249">86</span></span>|<span data-ttu-id="0a071-250">Wątek kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="0a071-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="0a071-251">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="0a071-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="0a071-252">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="0a071-252">Field name</span></span>|<span data-ttu-id="0a071-253">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0a071-253">Data type</span></span>|<span data-ttu-id="0a071-254">Opis</span><span class="sxs-lookup"><span data-stu-id="0a071-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0a071-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="0a071-255">ThreadID</span></span>|<span data-ttu-id="0a071-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-256">win:UInt64</span></span>|<span data-ttu-id="0a071-257">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="0a071-257">The thread identifier.</span></span>|  
|<span data-ttu-id="0a071-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="0a071-258">AppDomainID</span></span>|<span data-ttu-id="0a071-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0a071-259">win:UInt64</span></span>|<span data-ttu-id="0a071-260">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a071-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="0a071-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0a071-261">ClrInstanceID</span></span>|<span data-ttu-id="0a071-262">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="0a071-262">win:UInt16</span></span>|<span data-ttu-id="0a071-263">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0a071-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a071-264">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a071-264">See also</span></span>
- [<span data-ttu-id="0a071-265">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="0a071-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
