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
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="4986f-102">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="4986f-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<span data-ttu-id="4986f-103"><a name="top"></a>Zdarzenia te zawierają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4986f-103"><a name="top"></a> These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="4986f-104">Można użyć tych zdarzeń lub użyć zasobów domen aplikacji (ARM) funkcji monitorowania w celu uzyskania tych samych informacji.</span><span class="sxs-lookup"><span data-stu-id="4986f-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="4986f-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="4986f-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="4986f-106">ThreadCreated zdarzeń</span><span class="sxs-lookup"><span data-stu-id="4986f-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="4986f-107">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="4986f-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="4986f-108">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="4986f-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="4986f-109">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="4986f-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="4986f-110">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="4986f-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="4986f-111">ThreadCreated zdarzeń</span><span class="sxs-lookup"><span data-stu-id="4986f-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="4986f-112">To zdarzenie powstaje w obszarze dostawcy stert jako `ThreadDC` (w obszarze `AppDomainResourceManagementRundownKeyword` — słowo kluczowe).</span><span class="sxs-lookup"><span data-stu-id="4986f-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="4986f-113">Jest to tylko zdarzenia, które jest wywoływane w obszarze stert dostawcy w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="4986f-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="4986f-114">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="4986f-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="4986f-115">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="4986f-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="4986f-116">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-116">Keyword for raising the event</span></span>|<span data-ttu-id="4986f-117">Poziom</span><span class="sxs-lookup"><span data-stu-id="4986f-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4986f-118">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="4986f-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4986f-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4986f-119">Informational(4)</span></span>|  
|<span data-ttu-id="4986f-120">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="4986f-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4986f-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4986f-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="4986f-122">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4986f-123">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="4986f-123">Event</span></span>|<span data-ttu-id="4986f-124">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-124">Event ID</span></span>|<span data-ttu-id="4986f-125">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="4986f-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="4986f-126">85</span><span class="sxs-lookup"><span data-stu-id="4986f-126">85</span></span>|<span data-ttu-id="4986f-127">Wątek został utworzony dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4986f-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="4986f-128">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4986f-129">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="4986f-129">Field name</span></span>|<span data-ttu-id="4986f-130">Typ danych</span><span class="sxs-lookup"><span data-stu-id="4986f-130">Data type</span></span>|<span data-ttu-id="4986f-131">Opis</span><span class="sxs-lookup"><span data-stu-id="4986f-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4986f-132">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="4986f-132">ThreadID</span></span>|<span data-ttu-id="4986f-133">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-133">win:UInt64</span></span>|<span data-ttu-id="4986f-134">Identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="4986f-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="4986f-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4986f-135">AppDomainID</span></span>|<span data-ttu-id="4986f-136">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-136">win:UInt64</span></span>|<span data-ttu-id="4986f-137">Identyfikator domeny aplikacji dla wątku, który jest raportowany działania.</span><span class="sxs-lookup"><span data-stu-id="4986f-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="4986f-138">Flagi</span><span class="sxs-lookup"><span data-stu-id="4986f-138">Flags</span></span>|<span data-ttu-id="4986f-139">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="4986f-139">win:UInt32</span></span>|<span data-ttu-id="4986f-140">Wątek flagi tworzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="4986f-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="4986f-141">ManagedThreadIndex</span></span>|<span data-ttu-id="4986f-142">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="4986f-142">win:UInt32</span></span>|<span data-ttu-id="4986f-143">Zarządzane indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="4986f-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="4986f-144">Elementu OSThreadID</span><span class="sxs-lookup"><span data-stu-id="4986f-144">OSThreadID</span></span>|<span data-ttu-id="4986f-145">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="4986f-145">win:UInt32</span></span>|<span data-ttu-id="4986f-146">System operacyjny identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="4986f-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="4986f-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4986f-147">ClrInstanceID</span></span>|<span data-ttu-id="4986f-148">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="4986f-148">win:UInt16</span></span>|<span data-ttu-id="4986f-149">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4986f-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4986f-150">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="4986f-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="4986f-151">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="4986f-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="4986f-152">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="4986f-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4986f-153">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-153">Keyword for raising the event</span></span>|<span data-ttu-id="4986f-154">Poziom</span><span class="sxs-lookup"><span data-stu-id="4986f-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4986f-155">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="4986f-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4986f-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4986f-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="4986f-157">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4986f-158">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="4986f-158">Event</span></span>|<span data-ttu-id="4986f-159">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-159">Event ID</span></span>|<span data-ttu-id="4986f-160">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="4986f-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="4986f-161">83</span><span class="sxs-lookup"><span data-stu-id="4986f-161">83</span></span>|<span data-ttu-id="4986f-162">Co 4 MB pamięci (około) jest przydzielane w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4986f-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="4986f-163">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4986f-164">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="4986f-164">Field name</span></span>|<span data-ttu-id="4986f-165">Typ danych</span><span class="sxs-lookup"><span data-stu-id="4986f-165">Data type</span></span>|<span data-ttu-id="4986f-166">Opis</span><span class="sxs-lookup"><span data-stu-id="4986f-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4986f-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4986f-167">AppDomainID</span></span>|<span data-ttu-id="4986f-168">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-168">win:UInt64</span></span>|<span data-ttu-id="4986f-169">Identyfikator domeny aplikacji, dla którego zasobu jest raportowany użycia.</span><span class="sxs-lookup"><span data-stu-id="4986f-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="4986f-170">Przydzielone</span><span class="sxs-lookup"><span data-stu-id="4986f-170">Allocated</span></span>|<span data-ttu-id="4986f-171">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-171">win:UInt64</span></span>|<span data-ttu-id="4986f-172">Całkowita liczba bajtów przydzielonych w tej domenie aplikacji, ponieważ domena aplikacji została utworzona (liczba zwolnionych pamięci nie jest odejmowany).</span><span class="sxs-lookup"><span data-stu-id="4986f-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="4986f-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4986f-173">ClrInstanceID</span></span>|<span data-ttu-id="4986f-174">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="4986f-174">win:UInt16</span></span>|<span data-ttu-id="4986f-175">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4986f-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4986f-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="4986f-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="4986f-177">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="4986f-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="4986f-178">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="4986f-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4986f-179">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-179">Keyword for raising the event</span></span>|<span data-ttu-id="4986f-180">Poziom</span><span class="sxs-lookup"><span data-stu-id="4986f-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4986f-181">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="4986f-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4986f-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4986f-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="4986f-183">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4986f-184">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="4986f-184">Event</span></span>|<span data-ttu-id="4986f-185">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-185">Event ID</span></span>|<span data-ttu-id="4986f-186">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="4986f-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="4986f-187">84</span><span class="sxs-lookup"><span data-stu-id="4986f-187">84</span></span>|<span data-ttu-id="4986f-188">Każdy wyrzucanie elementów bezużytecznych została zakończona.</span><span class="sxs-lookup"><span data-stu-id="4986f-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="4986f-189">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4986f-190">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="4986f-190">Field name</span></span>|<span data-ttu-id="4986f-191">Typ danych</span><span class="sxs-lookup"><span data-stu-id="4986f-191">Data type</span></span>|<span data-ttu-id="4986f-192">Opis</span><span class="sxs-lookup"><span data-stu-id="4986f-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4986f-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4986f-193">AppDomainID</span></span>|<span data-ttu-id="4986f-194">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-194">win:UInt64</span></span>|<span data-ttu-id="4986f-195">Identyfikator domeny, dla którego zasobu jest raportowany użycia.</span><span class="sxs-lookup"><span data-stu-id="4986f-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="4986f-196">Udało się przetrwać</span><span class="sxs-lookup"><span data-stu-id="4986f-196">Survived</span></span>|<span data-ttu-id="4986f-197">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-197">win:UInt64</span></span>|<span data-ttu-id="4986f-198">Liczba bajtów, który udało przetrwać od ostatniego zebrania i które są znane przez tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4986f-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="4986f-199">Ta liczba jest dokładne i kompletne po pełnej kolekcji, ale mogą być niekompletne po pobraniu tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="4986f-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="4986f-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="4986f-200">ProcessSurvived</span></span>|<span data-ttu-id="4986f-201">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-201">win:UInt64</span></span>|<span data-ttu-id="4986f-202">Całkowita liczba bajtów, które udało przetrwać od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="4986f-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="4986f-203">Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów zablokowany na żywo w zarządzanych stosów.</span><span class="sxs-lookup"><span data-stu-id="4986f-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="4986f-204">Po pobraniu tymczasowych ta liczba reprezentuje liczbę bajtów przechowywać na żywo w generacje tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="4986f-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="4986f-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4986f-205">ClrInstanceID</span></span>|<span data-ttu-id="4986f-206">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="4986f-206">win:UInt16</span></span>|<span data-ttu-id="4986f-207">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4986f-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4986f-208">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="4986f-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="4986f-209">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="4986f-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="4986f-210">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="4986f-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4986f-211">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-211">Keyword for raising the event</span></span>|<span data-ttu-id="4986f-212">Poziom</span><span class="sxs-lookup"><span data-stu-id="4986f-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4986f-213">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="4986f-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4986f-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4986f-214">Informational(4)</span></span>|  
|<span data-ttu-id="4986f-215">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="4986f-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4986f-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4986f-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="4986f-217">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4986f-218">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="4986f-218">Event</span></span>|<span data-ttu-id="4986f-219">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-219">Event ID</span></span>|<span data-ttu-id="4986f-220">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="4986f-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="4986f-221">87</span><span class="sxs-lookup"><span data-stu-id="4986f-221">87</span></span>|<span data-ttu-id="4986f-222">Wątek przechodzi domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4986f-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="4986f-223">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4986f-224">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="4986f-224">Field name</span></span>|<span data-ttu-id="4986f-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="4986f-225">Data type</span></span>|<span data-ttu-id="4986f-226">Opis</span><span class="sxs-lookup"><span data-stu-id="4986f-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4986f-227">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="4986f-227">ThreadID</span></span>|<span data-ttu-id="4986f-228">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-228">win:UInt64</span></span>|<span data-ttu-id="4986f-229">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="4986f-229">The thread identifier.</span></span>|  
|<span data-ttu-id="4986f-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4986f-230">AppDomainID</span></span>|<span data-ttu-id="4986f-231">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-231">win:UInt64</span></span>|<span data-ttu-id="4986f-232">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4986f-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="4986f-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4986f-233">ClrInstanceID</span></span>|<span data-ttu-id="4986f-234">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="4986f-234">win:UInt16</span></span>|<span data-ttu-id="4986f-235">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4986f-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4986f-236">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="4986f-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="4986f-237">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="4986f-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="4986f-238">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="4986f-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4986f-239">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-239">Keyword for raising the event</span></span>|<span data-ttu-id="4986f-240">Poziom</span><span class="sxs-lookup"><span data-stu-id="4986f-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4986f-241">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="4986f-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="4986f-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4986f-242">Informational(4)</span></span>|  
|<span data-ttu-id="4986f-243">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="4986f-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4986f-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4986f-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="4986f-245">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4986f-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4986f-246">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="4986f-246">Event</span></span>|<span data-ttu-id="4986f-247">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4986f-247">Event ID</span></span>|<span data-ttu-id="4986f-248">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="4986f-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="4986f-249">86</span><span class="sxs-lookup"><span data-stu-id="4986f-249">86</span></span>|<span data-ttu-id="4986f-250">Zakończenie wątku.</span><span class="sxs-lookup"><span data-stu-id="4986f-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="4986f-251">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="4986f-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="4986f-252">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="4986f-252">Field name</span></span>|<span data-ttu-id="4986f-253">Typ danych</span><span class="sxs-lookup"><span data-stu-id="4986f-253">Data type</span></span>|<span data-ttu-id="4986f-254">Opis</span><span class="sxs-lookup"><span data-stu-id="4986f-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4986f-255">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="4986f-255">ThreadID</span></span>|<span data-ttu-id="4986f-256">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-256">win:UInt64</span></span>|<span data-ttu-id="4986f-257">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="4986f-257">The thread identifier.</span></span>|  
|<span data-ttu-id="4986f-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="4986f-258">AppDomainID</span></span>|<span data-ttu-id="4986f-259">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="4986f-259">win:UInt64</span></span>|<span data-ttu-id="4986f-260">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4986f-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="4986f-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4986f-261">ClrInstanceID</span></span>|<span data-ttu-id="4986f-262">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="4986f-262">win:UInt16</span></span>|<span data-ttu-id="4986f-263">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4986f-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4986f-264">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4986f-264">See Also</span></span>  
 [<span data-ttu-id="4986f-265">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="4986f-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
