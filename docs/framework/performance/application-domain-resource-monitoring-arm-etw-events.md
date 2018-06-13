---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47ab6e52278c77156e828869dd23575561879bff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398186"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="a00d7-102">Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)</span><span class="sxs-lookup"><span data-stu-id="a00d7-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="a00d7-103">Zdarzenia te zawierają szczegółowe informacje diagnostyczne o stanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a00d7-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="a00d7-104">Można użyć tych zdarzeń lub użyć zasobów domen aplikacji (ARM) funkcji monitorowania w celu uzyskania tych samych informacji.</span><span class="sxs-lookup"><span data-stu-id="a00d7-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="a00d7-105">Ta kategoria obejmuje następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a00d7-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="a00d7-106">ThreadCreated zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a00d7-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="a00d7-107">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="a00d7-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="a00d7-108">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="a00d7-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="a00d7-109">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="a00d7-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="a00d7-110">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="a00d7-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="a00d7-111">ThreadCreated zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a00d7-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="a00d7-112">To zdarzenie powstaje w obszarze dostawcy stert jako `ThreadDC` (w obszarze `AppDomainResourceManagementRundownKeyword` — słowo kluczowe).</span><span class="sxs-lookup"><span data-stu-id="a00d7-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="a00d7-113">Jest to tylko zdarzenia, które jest wywoływane w obszarze stert dostawcy w tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="a00d7-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="a00d7-114">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="a00d7-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="a00d7-115">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="a00d7-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="a00d7-116">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-116">Keyword for raising the event</span></span>|<span data-ttu-id="a00d7-117">Poziom</span><span class="sxs-lookup"><span data-stu-id="a00d7-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a00d7-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a00d7-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a00d7-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a00d7-119">Informational(4)</span></span>|  
|<span data-ttu-id="a00d7-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a00d7-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a00d7-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a00d7-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="a00d7-122">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a00d7-123">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a00d7-123">Event</span></span>|<span data-ttu-id="a00d7-124">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-124">Event ID</span></span>|<span data-ttu-id="a00d7-125">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="a00d7-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="a00d7-126">85</span><span class="sxs-lookup"><span data-stu-id="a00d7-126">85</span></span>|<span data-ttu-id="a00d7-127">Wątek został utworzony dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a00d7-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="a00d7-128">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a00d7-129">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a00d7-129">Field name</span></span>|<span data-ttu-id="a00d7-130">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a00d7-130">Data type</span></span>|<span data-ttu-id="a00d7-131">Opis</span><span class="sxs-lookup"><span data-stu-id="a00d7-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a00d7-132">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="a00d7-132">ThreadID</span></span>|<span data-ttu-id="a00d7-133">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-133">win:UInt64</span></span>|<span data-ttu-id="a00d7-134">Identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="a00d7-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="a00d7-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a00d7-135">AppDomainID</span></span>|<span data-ttu-id="a00d7-136">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-136">win:UInt64</span></span>|<span data-ttu-id="a00d7-137">Identyfikator domeny aplikacji dla wątku, który jest raportowany działania.</span><span class="sxs-lookup"><span data-stu-id="a00d7-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="a00d7-138">Flagi</span><span class="sxs-lookup"><span data-stu-id="a00d7-138">Flags</span></span>|<span data-ttu-id="a00d7-139">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a00d7-139">win:UInt32</span></span>|<span data-ttu-id="a00d7-140">Wątek flagi tworzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="a00d7-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="a00d7-141">ManagedThreadIndex</span></span>|<span data-ttu-id="a00d7-142">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a00d7-142">win:UInt32</span></span>|<span data-ttu-id="a00d7-143">Zarządzane indeks wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="a00d7-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="a00d7-144">Elementu OSThreadID</span><span class="sxs-lookup"><span data-stu-id="a00d7-144">OSThreadID</span></span>|<span data-ttu-id="a00d7-145">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="a00d7-145">win:UInt32</span></span>|<span data-ttu-id="a00d7-146">System operacyjny identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="a00d7-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="a00d7-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a00d7-147">ClrInstanceID</span></span>|<span data-ttu-id="a00d7-148">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="a00d7-148">win:UInt16</span></span>|<span data-ttu-id="a00d7-149">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a00d7-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a00d7-150">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="a00d7-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="a00d7-151">Zdarzenie AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="a00d7-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="a00d7-152">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="a00d7-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a00d7-153">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-153">Keyword for raising the event</span></span>|<span data-ttu-id="a00d7-154">Poziom</span><span class="sxs-lookup"><span data-stu-id="a00d7-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a00d7-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a00d7-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a00d7-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a00d7-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="a00d7-157">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a00d7-158">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a00d7-158">Event</span></span>|<span data-ttu-id="a00d7-159">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-159">Event ID</span></span>|<span data-ttu-id="a00d7-160">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="a00d7-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="a00d7-161">83</span><span class="sxs-lookup"><span data-stu-id="a00d7-161">83</span></span>|<span data-ttu-id="a00d7-162">Co 4 MB pamięci (około) jest przydzielane w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a00d7-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="a00d7-163">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a00d7-164">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a00d7-164">Field name</span></span>|<span data-ttu-id="a00d7-165">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a00d7-165">Data type</span></span>|<span data-ttu-id="a00d7-166">Opis</span><span class="sxs-lookup"><span data-stu-id="a00d7-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a00d7-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a00d7-167">AppDomainID</span></span>|<span data-ttu-id="a00d7-168">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-168">win:UInt64</span></span>|<span data-ttu-id="a00d7-169">Identyfikator domeny aplikacji, dla którego zasobu jest raportowany użycia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="a00d7-170">Przydzielone</span><span class="sxs-lookup"><span data-stu-id="a00d7-170">Allocated</span></span>|<span data-ttu-id="a00d7-171">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-171">win:UInt64</span></span>|<span data-ttu-id="a00d7-172">Całkowita liczba bajtów przydzielonych w tej domenie aplikacji, ponieważ domena aplikacji została utworzona (liczba zwolnionych pamięci nie jest odejmowany).</span><span class="sxs-lookup"><span data-stu-id="a00d7-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="a00d7-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a00d7-173">ClrInstanceID</span></span>|<span data-ttu-id="a00d7-174">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="a00d7-174">win:UInt16</span></span>|<span data-ttu-id="a00d7-175">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a00d7-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a00d7-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="a00d7-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="a00d7-177">Zdarzenie AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="a00d7-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="a00d7-178">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="a00d7-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a00d7-179">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-179">Keyword for raising the event</span></span>|<span data-ttu-id="a00d7-180">Poziom</span><span class="sxs-lookup"><span data-stu-id="a00d7-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a00d7-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a00d7-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a00d7-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a00d7-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="a00d7-183">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a00d7-184">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a00d7-184">Event</span></span>|<span data-ttu-id="a00d7-185">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-185">Event ID</span></span>|<span data-ttu-id="a00d7-186">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="a00d7-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="a00d7-187">84</span><span class="sxs-lookup"><span data-stu-id="a00d7-187">84</span></span>|<span data-ttu-id="a00d7-188">Każdy wyrzucanie elementów bezużytecznych została zakończona.</span><span class="sxs-lookup"><span data-stu-id="a00d7-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="a00d7-189">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a00d7-190">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a00d7-190">Field name</span></span>|<span data-ttu-id="a00d7-191">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a00d7-191">Data type</span></span>|<span data-ttu-id="a00d7-192">Opis</span><span class="sxs-lookup"><span data-stu-id="a00d7-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a00d7-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a00d7-193">AppDomainID</span></span>|<span data-ttu-id="a00d7-194">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-194">win:UInt64</span></span>|<span data-ttu-id="a00d7-195">Identyfikator domeny, dla którego zasobu jest raportowany użycia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="a00d7-196">Udało się przetrwać</span><span class="sxs-lookup"><span data-stu-id="a00d7-196">Survived</span></span>|<span data-ttu-id="a00d7-197">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-197">win:UInt64</span></span>|<span data-ttu-id="a00d7-198">Liczba bajtów, który udało przetrwać od ostatniego zebrania i które są znane przez tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a00d7-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="a00d7-199">Ta liczba jest dokładne i kompletne po pełnej kolekcji, ale mogą być niekompletne po pobraniu tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="a00d7-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="a00d7-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="a00d7-200">ProcessSurvived</span></span>|<span data-ttu-id="a00d7-201">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-201">win:UInt64</span></span>|<span data-ttu-id="a00d7-202">Całkowita liczba bajtów, które udało przetrwać od ostatniego zebrania.</span><span class="sxs-lookup"><span data-stu-id="a00d7-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="a00d7-203">Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów zablokowany na żywo w zarządzanych stosów.</span><span class="sxs-lookup"><span data-stu-id="a00d7-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="a00d7-204">Po pobraniu tymczasowych ta liczba reprezentuje liczbę bajtów przechowywać na żywo w generacje tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="a00d7-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="a00d7-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a00d7-205">ClrInstanceID</span></span>|<span data-ttu-id="a00d7-206">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="a00d7-206">win:UInt16</span></span>|<span data-ttu-id="a00d7-207">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a00d7-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a00d7-208">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="a00d7-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="a00d7-209">Zdarzenie ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="a00d7-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="a00d7-210">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="a00d7-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a00d7-211">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-211">Keyword for raising the event</span></span>|<span data-ttu-id="a00d7-212">Poziom</span><span class="sxs-lookup"><span data-stu-id="a00d7-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a00d7-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a00d7-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a00d7-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a00d7-214">Informational(4)</span></span>|  
|<span data-ttu-id="a00d7-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a00d7-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a00d7-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a00d7-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="a00d7-217">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a00d7-218">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a00d7-218">Event</span></span>|<span data-ttu-id="a00d7-219">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-219">Event ID</span></span>|<span data-ttu-id="a00d7-220">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="a00d7-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="a00d7-221">87</span><span class="sxs-lookup"><span data-stu-id="a00d7-221">87</span></span>|<span data-ttu-id="a00d7-222">Wątek przechodzi domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a00d7-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="a00d7-223">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a00d7-224">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a00d7-224">Field name</span></span>|<span data-ttu-id="a00d7-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a00d7-225">Data type</span></span>|<span data-ttu-id="a00d7-226">Opis</span><span class="sxs-lookup"><span data-stu-id="a00d7-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a00d7-227">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="a00d7-227">ThreadID</span></span>|<span data-ttu-id="a00d7-228">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-228">win:UInt64</span></span>|<span data-ttu-id="a00d7-229">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="a00d7-229">The thread identifier.</span></span>|  
|<span data-ttu-id="a00d7-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a00d7-230">AppDomainID</span></span>|<span data-ttu-id="a00d7-231">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-231">win:UInt64</span></span>|<span data-ttu-id="a00d7-232">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a00d7-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="a00d7-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a00d7-233">ClrInstanceID</span></span>|<span data-ttu-id="a00d7-234">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="a00d7-234">win:UInt16</span></span>|<span data-ttu-id="a00d7-235">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a00d7-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a00d7-236">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="a00d7-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="a00d7-237">Zdarzenie ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="a00d7-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="a00d7-238">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="a00d7-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a00d7-239">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-239">Keyword for raising the event</span></span>|<span data-ttu-id="a00d7-240">Poziom</span><span class="sxs-lookup"><span data-stu-id="a00d7-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a00d7-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="a00d7-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a00d7-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a00d7-242">Informational(4)</span></span>|  
|<span data-ttu-id="a00d7-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a00d7-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a00d7-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a00d7-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="a00d7-245">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a00d7-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a00d7-246">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a00d7-246">Event</span></span>|<span data-ttu-id="a00d7-247">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a00d7-247">Event ID</span></span>|<span data-ttu-id="a00d7-248">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="a00d7-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="a00d7-249">86</span><span class="sxs-lookup"><span data-stu-id="a00d7-249">86</span></span>|<span data-ttu-id="a00d7-250">Zakończenie wątku.</span><span class="sxs-lookup"><span data-stu-id="a00d7-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="a00d7-251">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a00d7-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="a00d7-252">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a00d7-252">Field name</span></span>|<span data-ttu-id="a00d7-253">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a00d7-253">Data type</span></span>|<span data-ttu-id="a00d7-254">Opis</span><span class="sxs-lookup"><span data-stu-id="a00d7-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a00d7-255">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="a00d7-255">ThreadID</span></span>|<span data-ttu-id="a00d7-256">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-256">win:UInt64</span></span>|<span data-ttu-id="a00d7-257">Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="a00d7-257">The thread identifier.</span></span>|  
|<span data-ttu-id="a00d7-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a00d7-258">AppDomainID</span></span>|<span data-ttu-id="a00d7-259">Windows: UInt64</span><span class="sxs-lookup"><span data-stu-id="a00d7-259">win:UInt64</span></span>|<span data-ttu-id="a00d7-260">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a00d7-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="a00d7-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a00d7-261">ClrInstanceID</span></span>|<span data-ttu-id="a00d7-262">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="a00d7-262">win:UInt16</span></span>|<span data-ttu-id="a00d7-263">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a00d7-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a00d7-264">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a00d7-264">See Also</span></span>  
 [<span data-ttu-id="a00d7-265">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="a00d7-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
