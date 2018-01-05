---
title: "Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6384700c7039cb705f2db759ebd3d733bf8954ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="c3752-102">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="c3752-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a><span data-ttu-id="c3752-103">Zdarzenia te zawierają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3752-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="c3752-104">Można użyć tych zdarzeń lub użyć zasobów domen aplikacji (ARM) funkcji monitorowania w celu uzyskania tych samych informacji.</span><span class="sxs-lookup"><span data-stu-id="c3752-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="c3752-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="c3752-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="c3752-106">ThreadCreated zdarzeń</span><span class="sxs-lookup"><span data-stu-id="c3752-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="c3752-107">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="c3752-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="c3752-108">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="c3752-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="c3752-109">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="c3752-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="c3752-110">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="c3752-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="c3752-111">ThreadCreated zdarzeń</span><span class="sxs-lookup"><span data-stu-id="c3752-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="c3752-112">To zdarzenie powstaje w obszarze dostawcy stert jako `ThreadDC` (w obszarze `AppDomainResourceManagementRundownKeyword` — słowo kluczowe).</span><span class="sxs-lookup"><span data-stu-id="c3752-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="c3752-113">Jest to tylko zdarzenia, które jest wywoływane w obszarze stert dostawcy w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="c3752-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="c3752-114">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="c3752-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="c3752-115">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="c3752-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c3752-116">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-116">Keyword for raising the event</span></span>|<span data-ttu-id="c3752-117">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3752-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c3752-118">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="c3752-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c3752-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c3752-119">Informational(4)</span></span>|  
|<span data-ttu-id="c3752-120">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="c3752-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c3752-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c3752-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="c3752-122">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c3752-123">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="c3752-123">Event</span></span>|<span data-ttu-id="c3752-124">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-124">Event ID</span></span>|<span data-ttu-id="c3752-125">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="c3752-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="c3752-126">85</span><span class="sxs-lookup"><span data-stu-id="c3752-126">85</span></span>|<span data-ttu-id="c3752-127">Wątek został utworzony dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3752-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="c3752-128">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c3752-129">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="c3752-129">Field name</span></span>|<span data-ttu-id="c3752-130">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c3752-130">Data type</span></span>|<span data-ttu-id="c3752-131">Opis</span><span class="sxs-lookup"><span data-stu-id="c3752-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c3752-132">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="c3752-132">ThreadID</span></span>|<span data-ttu-id="c3752-133">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-133">win:UInt64</span></span>|<span data-ttu-id="c3752-134">Identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="c3752-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="c3752-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c3752-135">AppDomainID</span></span>|<span data-ttu-id="c3752-136">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-136">win:UInt64</span></span>|<span data-ttu-id="c3752-137">Identyfikator domeny aplikacji dla wątku, który jest raportowany działania.</span><span class="sxs-lookup"><span data-stu-id="c3752-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="c3752-138">Flagi</span><span class="sxs-lookup"><span data-stu-id="c3752-138">Flags</span></span>|<span data-ttu-id="c3752-139">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="c3752-139">win:UInt32</span></span>|<span data-ttu-id="c3752-140">Wątek flagi tworzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="c3752-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="c3752-141">ManagedThreadIndex</span></span>|<span data-ttu-id="c3752-142">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="c3752-142">win:UInt32</span></span>|<span data-ttu-id="c3752-143">Zarządzane indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="c3752-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="c3752-144">Elementu OSThreadID</span><span class="sxs-lookup"><span data-stu-id="c3752-144">OSThreadID</span></span>|<span data-ttu-id="c3752-145">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="c3752-145">win:UInt32</span></span>|<span data-ttu-id="c3752-146">System operacyjny identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="c3752-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="c3752-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c3752-147">ClrInstanceID</span></span>|<span data-ttu-id="c3752-148">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c3752-148">win:UInt16</span></span>|<span data-ttu-id="c3752-149">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3752-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c3752-150">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c3752-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="c3752-151">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="c3752-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="c3752-152">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="c3752-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c3752-153">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-153">Keyword for raising the event</span></span>|<span data-ttu-id="c3752-154">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3752-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c3752-155">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="c3752-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c3752-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c3752-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="c3752-157">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c3752-158">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="c3752-158">Event</span></span>|<span data-ttu-id="c3752-159">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-159">Event ID</span></span>|<span data-ttu-id="c3752-160">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="c3752-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="c3752-161">83</span><span class="sxs-lookup"><span data-stu-id="c3752-161">83</span></span>|<span data-ttu-id="c3752-162">Co 4 MB pamięci (około) jest przydzielane w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3752-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="c3752-163">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c3752-164">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="c3752-164">Field name</span></span>|<span data-ttu-id="c3752-165">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c3752-165">Data type</span></span>|<span data-ttu-id="c3752-166">Opis</span><span class="sxs-lookup"><span data-stu-id="c3752-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c3752-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c3752-167">AppDomainID</span></span>|<span data-ttu-id="c3752-168">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-168">win:UInt64</span></span>|<span data-ttu-id="c3752-169">Identyfikator domeny aplikacji, dla którego zasobu jest raportowany użycia.</span><span class="sxs-lookup"><span data-stu-id="c3752-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="c3752-170">Przydzielone</span><span class="sxs-lookup"><span data-stu-id="c3752-170">Allocated</span></span>|<span data-ttu-id="c3752-171">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-171">win:UInt64</span></span>|<span data-ttu-id="c3752-172">Całkowita liczba bajtów przydzielonych w tej domenie aplikacji, ponieważ domena aplikacji została utworzona (liczba zwolnionych pamięci nie jest odejmowany).</span><span class="sxs-lookup"><span data-stu-id="c3752-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="c3752-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c3752-173">ClrInstanceID</span></span>|<span data-ttu-id="c3752-174">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c3752-174">win:UInt16</span></span>|<span data-ttu-id="c3752-175">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3752-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c3752-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c3752-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="c3752-177">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="c3752-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="c3752-178">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="c3752-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c3752-179">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-179">Keyword for raising the event</span></span>|<span data-ttu-id="c3752-180">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3752-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c3752-181">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="c3752-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c3752-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c3752-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="c3752-183">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c3752-184">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="c3752-184">Event</span></span>|<span data-ttu-id="c3752-185">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-185">Event ID</span></span>|<span data-ttu-id="c3752-186">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="c3752-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="c3752-187">84</span><span class="sxs-lookup"><span data-stu-id="c3752-187">84</span></span>|<span data-ttu-id="c3752-188">Każdy wyrzucanie elementów bezużytecznych została zakończona.</span><span class="sxs-lookup"><span data-stu-id="c3752-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="c3752-189">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c3752-190">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="c3752-190">Field name</span></span>|<span data-ttu-id="c3752-191">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c3752-191">Data type</span></span>|<span data-ttu-id="c3752-192">Opis</span><span class="sxs-lookup"><span data-stu-id="c3752-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c3752-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c3752-193">AppDomainID</span></span>|<span data-ttu-id="c3752-194">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-194">win:UInt64</span></span>|<span data-ttu-id="c3752-195">Identyfikator domeny, dla którego zasobu jest raportowany użycia.</span><span class="sxs-lookup"><span data-stu-id="c3752-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="c3752-196">Udało się przetrwać</span><span class="sxs-lookup"><span data-stu-id="c3752-196">Survived</span></span>|<span data-ttu-id="c3752-197">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-197">win:UInt64</span></span>|<span data-ttu-id="c3752-198">Liczba bajtów, który udało przetrwać od ostatniego zebrania i które są znane przez tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3752-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="c3752-199">Ta liczba jest dokładne i kompletne po pełnej kolekcji, ale mogą być niekompletne po pobraniu tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="c3752-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="c3752-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="c3752-200">ProcessSurvived</span></span>|<span data-ttu-id="c3752-201">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-201">win:UInt64</span></span>|<span data-ttu-id="c3752-202">Całkowita liczba bajtów, które udało przetrwać od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="c3752-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="c3752-203">Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów zablokowany na żywo w zarządzanych stosów.</span><span class="sxs-lookup"><span data-stu-id="c3752-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="c3752-204">Po pobraniu tymczasowych ta liczba reprezentuje liczbę bajtów przechowywać na żywo w generacje tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="c3752-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="c3752-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c3752-205">ClrInstanceID</span></span>|<span data-ttu-id="c3752-206">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c3752-206">win:UInt16</span></span>|<span data-ttu-id="c3752-207">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3752-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c3752-208">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c3752-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="c3752-209">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="c3752-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="c3752-210">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="c3752-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c3752-211">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-211">Keyword for raising the event</span></span>|<span data-ttu-id="c3752-212">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3752-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c3752-213">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="c3752-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c3752-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c3752-214">Informational(4)</span></span>|  
|<span data-ttu-id="c3752-215">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="c3752-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c3752-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c3752-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="c3752-217">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c3752-218">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="c3752-218">Event</span></span>|<span data-ttu-id="c3752-219">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-219">Event ID</span></span>|<span data-ttu-id="c3752-220">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="c3752-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="c3752-221">87</span><span class="sxs-lookup"><span data-stu-id="c3752-221">87</span></span>|<span data-ttu-id="c3752-222">Wątek przechodzi domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3752-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="c3752-223">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c3752-224">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="c3752-224">Field name</span></span>|<span data-ttu-id="c3752-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c3752-225">Data type</span></span>|<span data-ttu-id="c3752-226">Opis</span><span class="sxs-lookup"><span data-stu-id="c3752-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c3752-227">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="c3752-227">ThreadID</span></span>|<span data-ttu-id="c3752-228">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-228">win:UInt64</span></span>|<span data-ttu-id="c3752-229">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="c3752-229">The thread identifier.</span></span>|  
|<span data-ttu-id="c3752-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c3752-230">AppDomainID</span></span>|<span data-ttu-id="c3752-231">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-231">win:UInt64</span></span>|<span data-ttu-id="c3752-232">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3752-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="c3752-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c3752-233">ClrInstanceID</span></span>|<span data-ttu-id="c3752-234">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c3752-234">win:UInt16</span></span>|<span data-ttu-id="c3752-235">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3752-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c3752-236">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c3752-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="c3752-237">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="c3752-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="c3752-238">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="c3752-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c3752-239">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-239">Keyword for raising the event</span></span>|<span data-ttu-id="c3752-240">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3752-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c3752-241">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="c3752-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c3752-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c3752-242">Informational(4)</span></span>|  
|<span data-ttu-id="c3752-243">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="c3752-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c3752-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c3752-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="c3752-245">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3752-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c3752-246">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="c3752-246">Event</span></span>|<span data-ttu-id="c3752-247">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3752-247">Event ID</span></span>|<span data-ttu-id="c3752-248">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="c3752-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="c3752-249">86</span><span class="sxs-lookup"><span data-stu-id="c3752-249">86</span></span>|<span data-ttu-id="c3752-250">Zakończenie wątku.</span><span class="sxs-lookup"><span data-stu-id="c3752-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="c3752-251">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="c3752-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="c3752-252">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="c3752-252">Field name</span></span>|<span data-ttu-id="c3752-253">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c3752-253">Data type</span></span>|<span data-ttu-id="c3752-254">Opis</span><span class="sxs-lookup"><span data-stu-id="c3752-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c3752-255">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="c3752-255">ThreadID</span></span>|<span data-ttu-id="c3752-256">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-256">win:UInt64</span></span>|<span data-ttu-id="c3752-257">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="c3752-257">The thread identifier.</span></span>|  
|<span data-ttu-id="c3752-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c3752-258">AppDomainID</span></span>|<span data-ttu-id="c3752-259">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="c3752-259">win:UInt64</span></span>|<span data-ttu-id="c3752-260">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3752-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="c3752-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c3752-261">ClrInstanceID</span></span>|<span data-ttu-id="c3752-262">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="c3752-262">win:UInt16</span></span>|<span data-ttu-id="c3752-263">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3752-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3752-264">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3752-264">See Also</span></span>  
 [<span data-ttu-id="c3752-265">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="c3752-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
