---
title: Odzyskiwanie pamięci i wydajność
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aa04051a8aad56c653eaee1a79fb48a849cf377
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310567"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="c97c6-102">Odzyskiwanie pamięci i wydajność</span><span class="sxs-lookup"><span data-stu-id="c97c6-102">Garbage Collection and Performance</span></span>
<a name="top"></a> <span data-ttu-id="c97c6-103">W tym temacie opisano problemy związane z wyrzucania elementów kolekcji oraz użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="c97c6-104">Ona rozwiązuje problemy, które odnoszą się do zarządzanej sterty i wyjaśnia, jak można zminimalizować wpływ wyrzucania elementów bezużytecznych na swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="c97c6-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="c97c6-105">Każde wydanie zawiera łącza do procedur służących do badania problemów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-105">Each issue has links to procedures that you can use to investigate problems.</span></span>  
  
 <span data-ttu-id="c97c6-106">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="c97c6-106">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="c97c6-107">Narzędzia do analizy wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-107">Performance Analysis Tools</span></span>](#performance_analysis_tools)  
  
-   [<span data-ttu-id="c97c6-108">Rozwiązywanie problemów z wydajnością</span><span class="sxs-lookup"><span data-stu-id="c97c6-108">Troubleshooting Performance Issues</span></span>](#troubleshooting_performance_issues)  
  
-   [<span data-ttu-id="c97c6-109">Wskazówki dotyczące rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="c97c6-109">Troubleshooting Guidelines</span></span>](#troubleshooting_guidelines)  
  
-   [<span data-ttu-id="c97c6-110">Procedury wyboru wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-110">Performance Check Procedures</span></span>](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a><span data-ttu-id="c97c6-111">Narzędzia do analizy wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-111">Performance Analysis Tools</span></span>  
 <span data-ttu-id="c97c6-112">W poniższych sekcjach opisano narzędzia, które są dostępne do badania problemów kolekcji użycia i odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-112">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="c97c6-113">[Procedury](#performance_check_procedures) podane w dalszej części tego tematu odnoszą się do tych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c97c6-113">The [procedures](#performance_check_procedures) provided later in this topic refer to these tools.</span></span>  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a><span data-ttu-id="c97c6-114">Liczniki wydajności pamięci</span><span class="sxs-lookup"><span data-stu-id="c97c6-114">Memory Performance Counters</span></span>  
 <span data-ttu-id="c97c6-115">Można użyć liczników wydajności do zbierania danych wydajności.</span><span class="sxs-lookup"><span data-stu-id="c97c6-115">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="c97c6-116">Aby uzyskać instrukcje, zobacz [profilowanie środowiska uruchomieniowego](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="c97c6-116">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="c97c6-117">Pamięć .NET CLR kategorii liczników wydajności, zgodnie z opisem w [liczników wydajności w .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), zawiera informacje dotyczące modułu odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-117">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a><span data-ttu-id="c97c6-118">Debugowanie za pomocą SOS</span><span class="sxs-lookup"><span data-stu-id="c97c6-118">Debugging with SOS</span></span>  
 <span data-ttu-id="c97c6-119">Możesz użyć [debuger Windows (WinDbg)](/windows-hardware/drivers/debugger/index) do inspekcji obiektów w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-119">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>
 
 <span data-ttu-id="c97c6-120">Aby zainstalować WinDbg, należy zainstalować debugowania Tools for Windows z [Pobierz debugowania narzędzi dla Windows](/windows-hardware/drivers/debugger/debugger-download-tools) strony.</span><span class="sxs-lookup"><span data-stu-id="c97c6-120">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a><span data-ttu-id="c97c6-121">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="c97c6-121">Garbage Collection ETW Events</span></span>  
 <span data-ttu-id="c97c6-122">Śledzenie zdarzeń dla Windows (ETW) to system śledzenia, który uzupełnia profilowania i pomoc techniczna jest świadczona przez program .NET Framework — profilowanie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-122">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="c97c6-123">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [zdarzenia ETW odzyskiwania pamięci](../../../docs/framework/performance/garbage-collection-etw-events.md) przechwytywać informacje przydatne do analizowania sterty zarządzanej z punktu widzenia statystycznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-123">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="c97c6-124">Na przykład `GCStart_V1` zdarzenie, które jest wywoływane, gdy ma wystąpić wyrzucanie elementów bezużytecznych, zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="c97c6-124">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>  
  
-   <span data-ttu-id="c97c6-125">Które generacji obiektów są zbierane.</span><span class="sxs-lookup"><span data-stu-id="c97c6-125">Which generation of objects is being collected.</span></span>  
  
-   <span data-ttu-id="c97c6-126">Przyczyny ich wyzwolenia wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-126">What triggered the garbage collection.</span></span>  
  
-   <span data-ttu-id="c97c6-127">Typ wyrzucania elementów bezużytecznych (współbieżnych lub nie współbieżnych).</span><span class="sxs-lookup"><span data-stu-id="c97c6-127">Type of garbage collection (concurrent or not concurrent).</span></span>  
  
 <span data-ttu-id="c97c6-128">Rejestrowanie zdarzeń ETW jest wydajny i nie będzie maskował wszelkich problemów z wydajnością związanych z wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-128">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="c97c6-129">Proces może zapewnić swoje własne zdarzenia w połączeniu z zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="c97c6-129">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="c97c6-130">Po zalogowaniu, zarówno w przypadku zdarzeń aplikacji, jak i zdarzenia odzyskiwania pamięci możliwe było skorelowanie ich ustalenie, jak i kiedy sterty problemów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-130">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="c97c6-131">Na przykład aplikacja serwera może dostarczyć zdarzenia na początku i końcu żądanie klienta.</span><span class="sxs-lookup"><span data-stu-id="c97c6-131">For example, a server application could provide events at the start and end of a client request.</span></span>  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a><span data-ttu-id="c97c6-132">API profilowania</span><span class="sxs-lookup"><span data-stu-id="c97c6-132">The Profiling API</span></span>  
 <span data-ttu-id="c97c6-133">Wspólnych interfejsów profilowania środowiska uruchomieniowego (języka wspólnego CLR) języka zawierają szczegółowe informacje o obiektach, które miały wpływ podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-133">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="c97c6-134">Program profilujący może zostać poinformowany podczas wyrzucania elementów bezużytecznych rozpoczyna i kończy.</span><span class="sxs-lookup"><span data-stu-id="c97c6-134">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="c97c6-135">Umożliwia ona raportów dotyczących obiektów w zarządzanym stosie, w tym identyfikator obiektów w każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-135">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="c97c6-136">Aby uzyskać więcej informacji, zobacz [Przegląd profilowania](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c97c6-136">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>  
  
 <span data-ttu-id="c97c6-137">Profilery może zapewnić kompleksowe informacje.</span><span class="sxs-lookup"><span data-stu-id="c97c6-137">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="c97c6-138">Jednak złożone profilery potencjalnie można zmodyfikować zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-138">However, complex profilers can potentially modify an application's behavior.</span></span>  
  
### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="c97c6-139">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="c97c6-139">Application Domain Resource Monitoring</span></span>  
 <span data-ttu-id="c97c6-140">Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], (ARM) do monitorowania zasobów domen aplikacji włącza hosty do monitorowania wykorzystania procesora CPU i pamięci przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-140">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="c97c6-141">Aby uzyskać więcej informacji, zobacz [monitorowanie zasobów domeny aplikacji](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="c97c6-141">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>  
  
 [<span data-ttu-id="c97c6-142">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c97c6-142">Back to top</span></span>](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="c97c6-143">Rozwiązywanie problemów z wydajnością</span><span class="sxs-lookup"><span data-stu-id="c97c6-143">Troubleshooting Performance Issues</span></span>  
 <span data-ttu-id="c97c6-144">Pierwszym krokiem jest [ustalić, czy problem jest faktycznie wyrzucania elementów bezużytecznych](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="c97c6-144">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="c97c6-145">Jeśli okaże się, że jest, wybierz z poniższej listy, aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="c97c6-145">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>  
  
-   [<span data-ttu-id="c97c6-146">Wyjątek braku pamięci</span><span class="sxs-lookup"><span data-stu-id="c97c6-146">An out-of-memory exception is thrown</span></span>](#Issue_OOM)  
  
-   [<span data-ttu-id="c97c6-147">Proces używa zbyt dużo pamięci</span><span class="sxs-lookup"><span data-stu-id="c97c6-147">The process uses too much memory</span></span>](#Issue_TooMuchMemory)  
  
-   [<span data-ttu-id="c97c6-148">Moduł odśmiecania pamięci nie spowoduje odzyskania obiektów wystarczająco szybko</span><span class="sxs-lookup"><span data-stu-id="c97c6-148">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)  
  
-   [<span data-ttu-id="c97c6-149">Zarządzanego stosu za jest pofragmentowana.</span><span class="sxs-lookup"><span data-stu-id="c97c6-149">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)  
  
-   [<span data-ttu-id="c97c6-150">Wstrzymuje kolekcji wyrzucania elementów są za długie</span><span class="sxs-lookup"><span data-stu-id="c97c6-150">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)  
  
-   [<span data-ttu-id="c97c6-151">Generacja 0 jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="c97c6-151">Generation 0 is too big</span></span>](#Issue_Gen0)  
  
-   [<span data-ttu-id="c97c6-152">Użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt wysoka</span><span class="sxs-lookup"><span data-stu-id="c97c6-152">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="c97c6-153">Problem: Wyjątek braku pamięci</span><span class="sxs-lookup"><span data-stu-id="c97c6-153">Issue: An Out-of-Memory Exception Is Thrown</span></span>  
 <span data-ttu-id="c97c6-154">Istnieją dwa przypadki uzasadnione dla zarządzanej <xref:System.OutOfMemoryException> zgłoszenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-154">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>  
  
-   <span data-ttu-id="c97c6-155">Mało pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c97c6-155">Running out of virtual memory.</span></span>  
  
     <span data-ttu-id="c97c6-156">Moduł odśmiecania pamięci przydziela pamięć z systemu w segmentach ustalonej rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="c97c6-156">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="c97c6-157">Jeśli przydział wymaga dodatkowych segmentu, ale nie ciągłych wolny blok, w obszarze pamięci wirtualnej procesu, alokacji sterty zarządzanej nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="c97c6-157">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>  
  
-   <span data-ttu-id="c97c6-158">Nie ma wystarczającej ilości pamięci fizycznej do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="c97c6-158">Not having enough physical memory to allocate.</span></span>  
  
|<span data-ttu-id="c97c6-159">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-159">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="c97c6-160">Określa, czy wyjątek braku pamięci jest zarządzana.</span><span class="sxs-lookup"><span data-stu-id="c97c6-160">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="c97c6-161">Określ ilość pamięci wirtualnej może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="c97c6-161">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="c97c6-162">Ustal, czy jest wystarczająca ilość fizycznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-162">Determine whether there is enough physical memory.</span></span>](#Physical)|  
  
 <span data-ttu-id="c97c6-163">Jeśli okaże się, że wyjątek nie jest uzasadnione, skontaktuj się z działem obsługi klienta firmy Microsoft i pomocy technicznej z następującymi informacjami:</span><span class="sxs-lookup"><span data-stu-id="c97c6-163">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>  
  
-   <span data-ttu-id="c97c6-164">Stos o zarządzanym wyjątku braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-164">The stack with the managed out-of-memory exception.</span></span>  
  
-   <span data-ttu-id="c97c6-165">Pełny zrzut pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-165">Full memory dump.</span></span>  
  
-   <span data-ttu-id="c97c6-166">Dane, gdy okaże się, że nie jest uzasadnione wyjątku braku pamięci, w tym dane, które pokazuje, że pamięć wirtualny lub fizyczny nie jest problemem.</span><span class="sxs-lookup"><span data-stu-id="c97c6-166">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="c97c6-167">Problem: Proces używa zbyt dużo pamięci</span><span class="sxs-lookup"><span data-stu-id="c97c6-167">Issue: The Process Uses Too Much Memory</span></span>  
 <span data-ttu-id="c97c6-168">Typowe zakłada się, że użycie pamięci jest wyświetlane na **wydajności** kartę w Menedżerze zadań Windows można wskazać, kiedy jest on używany zbyt dużej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-168">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="c97c6-169">Jednakże obok którego wyświetlona odnoszą się do zestawu roboczego; zapewnia ona informacje na temat użycia pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c97c6-169">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>  
  
 <span data-ttu-id="c97c6-170">Jeśli okaże się, że problem jest spowodowany przez sterty zarządzanej, muszą mierzyć sterty zarządzanej, wraz z upływem czasu, aby określić wszystkie wzorce.</span><span class="sxs-lookup"><span data-stu-id="c97c6-170">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>  
  
 <span data-ttu-id="c97c6-171">Jeśli okaże się, że problem nie leży po zarządzanym stosie, należy użyć debugowanie natywne.</span><span class="sxs-lookup"><span data-stu-id="c97c6-171">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>  
  
|<span data-ttu-id="c97c6-172">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-172">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="c97c6-173">Określ ilość pamięci wirtualnej może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="c97c6-173">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="c97c6-174">Określ, ile pamięci sterty zarządzanej jest zatwierdzanie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-174">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="c97c6-175">Określ, ile pamięci sterty zarządzanej zastrzega sobie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-175">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="c97c6-176">Określ dużych obiektów w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="c97c6-176">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="c97c6-177">Określ odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-177">Determine references to objects.</span></span>](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="c97c6-178">Problem: Moduł odśmiecania pamięci nie spowoduje odzyskania obiektów wystarczająco szybko</span><span class="sxs-lookup"><span data-stu-id="c97c6-178">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>  
 <span data-ttu-id="c97c6-179">Gdy się pojawi, tak jakby obiekty nie są są odzyskane, zgodnie z oczekiwaniami do wyrzucania elementów bezużytecznych, należy określić, czy wszystkie silne odwołania do tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-179">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>  
  
 <span data-ttu-id="c97c6-180">Ten problem może również wystąpić, jeśli nie było żadnych elementów bezużytecznych generacji, która zawiera obiekt martwy, co oznacza, że finalizator martwy obiektu nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="c97c6-180">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="c97c6-181">Na przykład jest to możliwe po uruchomieniu aplikacji apartamentem jednowątkowym (przedziale STA) i wątku tej usługi, których nie można wywołać; kolejka finalizatorów tę sytuację.</span><span class="sxs-lookup"><span data-stu-id="c97c6-181">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>  
  
|<span data-ttu-id="c97c6-182">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-182">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="c97c6-183">Sprawdź odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-183">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="c97c6-184">Ustal, czy finalizator został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="c97c6-184">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="c97c6-185">Ustal, czy istnieją obiekty oczekujące na można sfinalizować.</span><span class="sxs-lookup"><span data-stu-id="c97c6-185">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="c97c6-186">Problem: Zarządzanego stosu jest zbyt dużej fragmentacji</span><span class="sxs-lookup"><span data-stu-id="c97c6-186">Issue: The Managed Heap Is Too fragmented</span></span>  
 <span data-ttu-id="c97c6-187">Poziom fragmentacji jest obliczana jako stosunek wolnego miejsca na dysku łączna ilość przydzielonej pamięci do generowania.</span><span class="sxs-lookup"><span data-stu-id="c97c6-187">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="c97c6-188">Generacji 2 akceptowalny poziom fragmentacji jest nie więcej niż 20%.</span><span class="sxs-lookup"><span data-stu-id="c97c6-188">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="c97c6-189">Ponieważ generacji 2 można uzyskać bardzo duże, stosunek fragmentacji jest ważniejsza niż wartość bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="c97c6-189">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>  
  
 <span data-ttu-id="c97c6-190">O dużej ilości wolnego miejsca w generacji 0 nie jest problemem, ponieważ jest generowanie gdzie są przydzielane nowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-190">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>  
  
 <span data-ttu-id="c97c6-191">Fragmentacja zawsze występuje stertę dużego obiektu, ponieważ nie jest kompaktowana.</span><span class="sxs-lookup"><span data-stu-id="c97c6-191">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="c97c6-192">Bezpłatne obiekty, które sąsiadują naturalnie są zwinięte do pojedynczego obszaru do spełnienia żądania alokacji dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-192">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>  
  
 <span data-ttu-id="c97c6-193">Fragmentacja może stać się problemem w generacji 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="c97c6-193">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="c97c6-194">Jeśli generacje te dużą ilością wolnego miejsca na dysku po wyrzucania elementów bezużytecznych, użycie obiektu aplikacji mogą wymagać modyfikacji i należy rozważyć ponownej oceny okresu istnienia obiektów długoterminowego.</span><span class="sxs-lookup"><span data-stu-id="c97c6-194">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>  
  
 <span data-ttu-id="c97c6-195">Przypinanie nadmierne obiektów może zwiększyć fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-195">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="c97c6-196">Jeśli fragmentacji jest wysoka, można przypiąć za dużo obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-196">If fragmentation is high, too many objects could be pinned.</span></span>  
  
 <span data-ttu-id="c97c6-197">Jeżeli fragmentacji pamięci wirtualnej uniemożliwia Dodawanie segmentów moduł zbierający elementy bezużyteczne, powoduje, że może to być jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c97c6-197">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>  
  
-   <span data-ttu-id="c97c6-198">Częste ładowanie i zwalnianie wiele małych zestawów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-198">Frequent loading and unloading of many small assemblies.</span></span>  
  
-   <span data-ttu-id="c97c6-199">Przytrzymanie zbyt wiele odwołań do obiektów COM, gdy współdziałanie z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="c97c6-199">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>  
  
-   <span data-ttu-id="c97c6-200">Tworzenie dużych obiektów przejściowy, co powoduje, że stertę dużego obiektu przydzielać i zwalniać często segmenty sterty.</span><span class="sxs-lookup"><span data-stu-id="c97c6-200">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>  
  
     <span data-ttu-id="c97c6-201">W przypadku hostowania środowiska CLR, aplikacja może zażądać zachowanie jego segmentów moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-201">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="c97c6-202">Pozwala to zmniejszyć częstotliwość alokacje segmentu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-202">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="c97c6-203">Jest to realizowane za pomocą flagi STARTUP_HOARD_GC_VM w [startup_flags — wyliczenie](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c97c6-203">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
|<span data-ttu-id="c97c6-204">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-204">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="c97c6-205">Określ ilość wolnego miejsca w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-205">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="c97c6-206">Określ liczbę przypiętych obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-206">Determine the number of pinned objects.</span></span>](#Pinned)|  
  
 <span data-ttu-id="c97c6-207">Jeśli uważasz, że nie stanowi uzasadnione fragmentacji, skontaktuj się z działem obsługi klienta firmy Microsoft i pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="c97c6-207">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="c97c6-208">Problem: Wstrzymuje kolekcji wyrzucania elementów są za długie</span><span class="sxs-lookup"><span data-stu-id="c97c6-208">Issue: Garbage Collection Pauses Are Too Long</span></span>  
 <span data-ttu-id="c97c6-209">Wyrzucanie elementów bezużytecznych działa w czasie rzeczywistym nietrwałego, więc aplikacja musi być w stanie tolerować kilka wstrzymuje.</span><span class="sxs-lookup"><span data-stu-id="c97c6-209">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="c97c6-210">Kryterium czasu rzeczywistego nietrwałego jest, że 95% operacji musi zostać zakończone na czas.</span><span class="sxs-lookup"><span data-stu-id="c97c6-210">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>  
  
 <span data-ttu-id="c97c6-211">W współbieżne wyrzucanie elementów bezużytecznych zarządzane wątki mogą być uruchamiane podczas zbierania, co oznacza, że wstrzymuje są minimalne.</span><span class="sxs-lookup"><span data-stu-id="c97c6-211">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>  
  
 <span data-ttu-id="c97c6-212">Tymczasowe wyrzucanie elementów bezużytecznych (generacje 0 i 1) trwać tylko kilka milisekund, więc zmniejsza wstrzymuje zwykle nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="c97c6-212">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="c97c6-213">Można jednak zmniejszyć przerw w kolekcji generacji 2, zmieniając wzorzec żądań alokacji przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c97c6-213">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>  
  
 <span data-ttu-id="c97c6-214">Inny, bardziej precyzyjne metoda polega na użyciu [zdarzenia ETW odzyskiwania pamięci](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="c97c6-214">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="c97c6-215">Możesz znaleźć chronometrażu dla kolekcji, dodając różnice sygnatury czasu sekwencji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c97c6-215">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="c97c6-216">Sekwencja całej kolekcji zawiera zawieszenie aparatu wykonywania, wyrzucanie elementów bezużytecznych, sama i wznowienie aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c97c6-216">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>  
  
 <span data-ttu-id="c97c6-217">Możesz użyć [powiadomienia dotyczące odzyskiwania pamięci](../../../docs/standard/garbage-collection/notifications.md) można określić, czy serwer ma mieć kolekcji generacji 2 i czy Przekierowywanie żądań do innego serwera, można zmniejszyć, problemów z pauzy.</span><span class="sxs-lookup"><span data-stu-id="c97c6-217">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>  
  
|<span data-ttu-id="c97c6-218">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-218">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="c97c6-219">Określ czas, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-219">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="c97c6-220">Określ, co spowodowało wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-220">Determine what caused a garbage collection.</span></span>](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="c97c6-221">Problem: Generacja 0 jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="c97c6-221">Issue: Generation 0 Is Too Big</span></span>  
 <span data-ttu-id="c97c6-222">Może mieć większą liczbę obiektów w systemie 64-bitowych, szczególnie w przypadku, gdy używasz wyrzucanie elementów bezużytecznych serwera zamiast wyrzucanie elementów bezużytecznych jest generacji 0.</span><span class="sxs-lookup"><span data-stu-id="c97c6-222">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="c97c6-223">Jest to spowodowane próg wyzwolenia generację 0 wyrzucania elementów bezużytecznych jest wyższa w tych środowiskach i uzyskać znacznie większe generacji 0.</span><span class="sxs-lookup"><span data-stu-id="c97c6-223">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="c97c6-224">Lepsza wydajność aplikacji przydziela większej ilości pamięci, zanim zostanie wywołany wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-224">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="c97c6-225">Problem: Użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt wysoka</span><span class="sxs-lookup"><span data-stu-id="c97c6-225">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>  
 <span data-ttu-id="c97c6-226">Użycie procesora CPU będzie wysoka podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-226">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="c97c6-227">Znaczną ilość czasu proces odbywa się w wyrzucania elementów bezużytecznych, liczby kolekcji jest zbyt często czy kolekcja jest zbyt długo trwające.</span><span class="sxs-lookup"><span data-stu-id="c97c6-227">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="c97c6-228">Współczynnik zwiększenia alokacji obiektów na stosie zarządzanym powoduje, że wyrzucanie elementów bezużytecznych częściej.</span><span class="sxs-lookup"><span data-stu-id="c97c6-228">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="c97c6-229">Zmniejsza szybkość alokacji zmniejsza częstotliwość wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-229">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>  
  
 <span data-ttu-id="c97c6-230">Stawki alokacji można monitorować za pomocą `Allocated Bytes/second` licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="c97c6-230">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="c97c6-231">Aby uzyskać więcej informacji, zobacz [liczników wydajności w .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="c97c6-231">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>  
  
 <span data-ttu-id="c97c6-232">Czas trwania kolekcji jest głównie współczynnik liczby obiektów, które przeżyły po alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-232">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="c97c6-233">Moduł zbierający elementy bezużyteczne musi przejść przez dużą ilość pamięci, jeśli wiele obiektów nadal mają być zbierane.</span><span class="sxs-lookup"><span data-stu-id="c97c6-233">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="c97c6-234">Praca kompaktowanie pozostałości jest czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="c97c6-234">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="c97c6-235">Aby ustalić, ile obiekty zostały obsłużone w kolekcji, należy ustawić punkt przerwania w debugerze na końcu wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-235">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>  
  
|<span data-ttu-id="c97c6-236">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-236">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="c97c6-237">Określ, jeśli wysokie użycie procesora CPU jest spowodowany przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-237">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="c97c6-238">Ustaw punkt przerwania na końcu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-238">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|  
  
 [<span data-ttu-id="c97c6-239">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c97c6-239">Back to top</span></span>](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a><span data-ttu-id="c97c6-240">Wskazówki dotyczące rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="c97c6-240">Troubleshooting Guidelines</span></span>  
 <span data-ttu-id="c97c6-241">W tej sekcji opisano wskazówki, które należy wziąć pod uwagę po rozpoczęciu swoje badania.</span><span class="sxs-lookup"><span data-stu-id="c97c6-241">This section describes guidelines that you should consider as you begin your investigations.</span></span>  
  
### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="c97c6-242">Stacja robocza lub serwer wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="c97c6-242">Workstation or Server Garbage Collection</span></span>  
 <span data-ttu-id="c97c6-243">Określ, jeśli używasz poprawnego typu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-243">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="c97c6-244">Jeśli aplikacja korzysta z wielu wątków i wystąpienia obiektów, wyrzucanie elementów bezużytecznych serwera należy użyć zamiast wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-244">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="c97c6-245">Wyrzucanie elementów bezużytecznych serwera działa w wielu wątkach, wyrzucanie elementów bezużytecznych wymaga wielu wystąpień aplikacji do uruchamiania ich własnych wątków wyrzucania elementów bezużytecznych i konkurować o czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="c97c6-245">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>  
  
 <span data-ttu-id="c97c6-246">Aplikacja ma niskie obciążenie i rzadko w tle, takie jak usługa, która wykonuje zadania można za pomocą wyrzucanie elementów bezużytecznych współbieżne wyrzucanie elementów bezużytecznych wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c97c6-246">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>  
  
### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="c97c6-247">Gdy do mierzenia rozmiaru sterty zarządzanej</span><span class="sxs-lookup"><span data-stu-id="c97c6-247">When to Measure the Managed Heap Size</span></span>  
 <span data-ttu-id="c97c6-248">O ile nie jest używany program profilujący, trzeba będzie utworzyć spójne wzorzec pomiaru skutecznie zdiagnozować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="c97c6-248">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="c97c6-249">Należy wziąć pod uwagę następujące kwestie, aby ustanowić harmonogram:</span><span class="sxs-lookup"><span data-stu-id="c97c6-249">Consider the following points to establish a schedule:</span></span>  
  
-   <span data-ttu-id="c97c6-250">Jeśli mierzonych po wyrzucania elementów bezużytecznych generacji 2 całą zarządzaną stertę będą wolne od pamięci (obiekty martwe).</span><span class="sxs-lookup"><span data-stu-id="c97c6-250">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>  
  
-   <span data-ttu-id="c97c6-251">Jeśli mierzonych natychmiast po wyrzucania elementów bezużytecznych generacji 0 obiekty w generacji 1 i 2 nie będą zbierane jeszcze.</span><span class="sxs-lookup"><span data-stu-id="c97c6-251">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>  
  
-   <span data-ttu-id="c97c6-252">W przypadku mierzonych bezpośrednio przed wyrzucania elementów bezużytecznych będzie zmierzyć tak dużej ilości alokacji, jak to możliwe, zanim rozpocznie się wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-252">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>  
  
-   <span data-ttu-id="c97c6-253">Pomiaru podczas wyrzucania elementów bezużytecznych jest problemem, ponieważ struktur danych modułu odśmiecania pamięci nie znajdują się w nieprawidłowym stanie dla przechodzenia i nie można dostarczać pełnych wyników.</span><span class="sxs-lookup"><span data-stu-id="c97c6-253">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="c97c6-254">To jest celowe.</span><span class="sxs-lookup"><span data-stu-id="c97c6-254">This is by design.</span></span>  
  
-   <span data-ttu-id="c97c6-255">Używając wyrzucania elementów bezużytecznych dla stacji roboczych z współbieżne wyrzucanie elementów bezużytecznych, odzyskiwanego obiekty nie są skompaktowany, dzięki czemu rozmiar sterty może być taki sam lub większy (fragmentacji może wydawać się większe).</span><span class="sxs-lookup"><span data-stu-id="c97c6-255">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>  
  
-   <span data-ttu-id="c97c6-256">Współbieżne wyrzucanie elementów bezużytecznych w generacji 2 jest opóźnione, gdy obciążenie pamięci fizycznej jest zbyt duży.</span><span class="sxs-lookup"><span data-stu-id="c97c6-256">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>  
  
 <span data-ttu-id="c97c6-257">Poniższa procedura opisuje sposób Ustaw punkt przerwania, dzięki czemu można mierzyć zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-257">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="c97c6-258">Aby ustawić punkt przerwania na końcu wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="c97c6-258">To set a breakpoint at the end of garbage collection</span></span>  
  
-   <span data-ttu-id="c97c6-259">W WinDbg za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-259">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="c97c6-260">**najlepszych praktyk w zakresie mscorwks! WKS::GCHeap::RestartEE "j (dwo (mscorwks! WKS::GCHeap::GcCondemnedGeneration) == 2) "kb"; " g ""**</span><span class="sxs-lookup"><span data-stu-id="c97c6-260">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>  
  
     <span data-ttu-id="c97c6-261">gdzie **GcCondemnedGeneration** jest ustawiona na żądaną generacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-261">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="c97c6-262">To polecenie wymaga symboli prywatnych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-262">This command requires private symbols.</span></span>  
  
     <span data-ttu-id="c97c6-263">To polecenie wymusza podziału **RestartEE** jest uruchamiane po obiekty generacji 2 odzyskano do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-263">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>  
  
     <span data-ttu-id="c97c6-264">W serwerze wyrzucanie elementów bezużytecznych, tylko jeden wątek wywołuje **RestartEE**, więc punkt przerwania zostanie wystąpić tylko raz podczas wyrzucania elementów bezużytecznych generacji 2.</span><span class="sxs-lookup"><span data-stu-id="c97c6-264">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>  
  
 [<span data-ttu-id="c97c6-265">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="c97c6-265">Back to top</span></span>](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a><span data-ttu-id="c97c6-266">Procedury wyboru wydajności</span><span class="sxs-lookup"><span data-stu-id="c97c6-266">Performance Check Procedures</span></span>  
 <span data-ttu-id="c97c6-267">W tej sekcji opisano następujące procedury, aby ustalić przyczynę problemu z wydajnością:</span><span class="sxs-lookup"><span data-stu-id="c97c6-267">This section describes the following procedures to isolate the cause of your performance issue:</span></span>  
  
-   [<span data-ttu-id="c97c6-268">Ustal, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-268">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)  
  
-   [<span data-ttu-id="c97c6-269">Określa, czy wyjątek braku pamięci jest zarządzana.</span><span class="sxs-lookup"><span data-stu-id="c97c6-269">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)  
  
-   [<span data-ttu-id="c97c6-270">Określ ilość pamięci wirtualnej może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="c97c6-270">Determine how much virtual memory can be reserved.</span></span>](#GetVM)  
  
-   [<span data-ttu-id="c97c6-271">Ustal, czy jest wystarczająca ilość fizycznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-271">Determine whether there is enough physical memory.</span></span>](#Physical)  
  
-   [<span data-ttu-id="c97c6-272">Określ, ile pamięci sterty zarządzanej jest zatwierdzanie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-272">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)  
  
-   [<span data-ttu-id="c97c6-273">Określ, ile pamięci sterty zarządzanej zastrzega sobie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-273">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)  
  
-   [<span data-ttu-id="c97c6-274">Określ dużych obiektów w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="c97c6-274">Determine large objects in generation 2.</span></span>](#ExamineGen2)  
  
-   [<span data-ttu-id="c97c6-275">Określ odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-275">Determine references to objects.</span></span>](#ObjRef)  
  
-   [<span data-ttu-id="c97c6-276">Ustal, czy finalizator został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="c97c6-276">Determine whether a finalizer has been run.</span></span>](#Induce)  
  
-   [<span data-ttu-id="c97c6-277">Ustal, czy istnieją obiekty oczekujące na można sfinalizować.</span><span class="sxs-lookup"><span data-stu-id="c97c6-277">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)  
  
-   [<span data-ttu-id="c97c6-278">Określ ilość wolnego miejsca w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-278">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)  
  
-   [<span data-ttu-id="c97c6-279">Określ liczbę przypiętych obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-279">Determine the number of pinned objects.</span></span>](#Pinned)  
  
-   [<span data-ttu-id="c97c6-280">Określ czas, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-280">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)  
  
-   [<span data-ttu-id="c97c6-281">Określ, co wyzwoliło wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-281">Determine what triggered a garbage collection.</span></span>](#Triggered)  
  
-   [<span data-ttu-id="c97c6-282">Ustal, czy wysokie użycie procesora CPU jest spowodowany przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-282">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="c97c6-283">Aby określić, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="c97c6-283">To determine whether the problem is caused by garbage collection</span></span>  
  
-   <span data-ttu-id="c97c6-284">Sprawdź następujące liczniki wydajności dwóch pamięci:</span><span class="sxs-lookup"><span data-stu-id="c97c6-284">Examine the following two memory performance counters:</span></span>  
  
    -   <span data-ttu-id="c97c6-285">**% Czas działania modułu GC**.</span><span class="sxs-lookup"><span data-stu-id="c97c6-285">**% Time in GC**.</span></span> <span data-ttu-id="c97c6-286">Wyświetla procent minionego czasu, jaki był poświęcony na wykonywanie wyrzucania elementów bezużytecznych od ostatniego cyklu wyrzucania elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-286">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="c97c6-287">Ten licznik umożliwia określenie, czy moduł zbierający elementy bezużyteczne zużywa zbyt dużo czasu, aby zwiększyć ilość miejsca na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="c97c6-287">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="c97c6-288">Jeśli czas potrzebny do wyrzucania elementów bezużytecznych jest stosunkowo niska, który może wskazywać na problem zasobów, poza zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-288">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="c97c6-289">Ten licznik mogą być niedokładne, gdy współbieżnych lub uczestniczy wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="c97c6-289">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>  
  
    -   <span data-ttu-id="c97c6-290">**# Łączna liczba przydzielonych bajtów**.</span><span class="sxs-lookup"><span data-stu-id="c97c6-290">**# Total committed Bytes**.</span></span> <span data-ttu-id="c97c6-291">Przedstawia ilość pamięci wirtualnej, które aktualnie przydzielonej przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-291">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="c97c6-292">Ten licznik umożliwia określenie, czy pamięci używane przez moduł odśmiecania pamięci jest nadmierne część pamięci, która korzysta z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-292">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>  
  
     <span data-ttu-id="c97c6-293">Większość liczników wydajności pamięci są aktualizowane na końcu każdej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-293">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="c97c6-294">Może nie odzwierciedlają one bieżące warunki, które chcesz uzyskać informacje.</span><span class="sxs-lookup"><span data-stu-id="c97c6-294">Therefore, they may not reflect the current conditions that you want information about.</span></span>  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="c97c6-295">Aby ustalić, czy wyjątek braku pamięci jest zarządzany</span><span class="sxs-lookup"><span data-stu-id="c97c6-295">To determine whether the out-of-memory exception is managed</span></span>  
  
1. <span data-ttu-id="c97c6-296">W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane typ wyjątku drukowania (**pe**) polecenia:</span><span class="sxs-lookup"><span data-stu-id="c97c6-296">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>  
  
     <span data-ttu-id="c97c6-297">**! pe**</span><span class="sxs-lookup"><span data-stu-id="c97c6-297">**!pe**</span></span>  
  
     <span data-ttu-id="c97c6-298">Jeśli wyjątek jest zarządzany, <xref:System.OutOfMemoryException> jest wyświetlany jako typ wyjątku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-298">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2. <span data-ttu-id="c97c6-299">Dane wyjściowe nie określony wyjątek, należy określić, który wątek wyjątku braku pamięci pochodzi z.</span><span class="sxs-lookup"><span data-stu-id="c97c6-299">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="c97c6-300">Wpisz następujące polecenie w debugerze, aby wyświetlić wszystkie wątki z ich stosów wywołań:</span><span class="sxs-lookup"><span data-stu-id="c97c6-300">Type the following command in the debugger to show all the threads with their call stacks:</span></span>  
  
     <span data-ttu-id="c97c6-301">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="c97c6-301">**~\*kb**</span></span>  
  
     <span data-ttu-id="c97c6-302">Wątek przy użyciu stosu, który ma wywołań wyjątków jest wskazywany przez `RaiseTheException` argumentu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-302">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="c97c6-303">Jest to obiektu zarządzanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c97c6-303">This is the managed exception object.</span></span>  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3. <span data-ttu-id="c97c6-304">Następujące polecenie służy do porzucenia wyjątków zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-304">You can use the following command to dump nested exceptions.</span></span>  
  
     <span data-ttu-id="c97c6-305">**! pe-zagnieżdżonych**</span><span class="sxs-lookup"><span data-stu-id="c97c6-305">**!pe -nested**</span></span>  
  
     <span data-ttu-id="c97c6-306">Jeśli nie możesz znaleźć wszystkie wyjątki, wyjątek braku pamięci pochodzi z niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-306">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="c97c6-307">Aby określić ilość pamięci wirtualnej może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="c97c6-307">To determine how much virtual memory can be reserved</span></span>  
  
-   <span data-ttu-id="c97c6-308">W WinDbg za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie, aby pobrać największego wolnego regionu:</span><span class="sxs-lookup"><span data-stu-id="c97c6-308">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>  
  
     <span data-ttu-id="c97c6-309">**! adresów — podsumowanie**</span><span class="sxs-lookup"><span data-stu-id="c97c6-309">**!address -summary**</span></span>  
  
     <span data-ttu-id="c97c6-310">Największego wolnego region jest wyświetlany, jak pokazano w następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-310">The largest free region is displayed as shown in the following output.</span></span>  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     <span data-ttu-id="c97c6-311">W tym przykładzie rozmiar największego wolnego region jest około 24000 KB (3A980 w formacie szesnastkowym).</span><span class="sxs-lookup"><span data-stu-id="c97c6-311">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="c97c6-312">Ten region jest znacznie mniejszy niż moduł zbierający elementy bezużyteczne musi dla segmentu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-312">This region is much smaller than what the garbage collector needs for a segment.</span></span>  
  
     <span data-ttu-id="c97c6-313">—lub—</span><span class="sxs-lookup"><span data-stu-id="c97c6-313">-or-</span></span>  
  
-   <span data-ttu-id="c97c6-314">Użyj **vmstat** polecenia:</span><span class="sxs-lookup"><span data-stu-id="c97c6-314">Use the **vmstat** command:</span></span>  
  
     <span data-ttu-id="c97c6-315">**! vmstat**</span><span class="sxs-lookup"><span data-stu-id="c97c6-315">**!vmstat**</span></span>  
  
     <span data-ttu-id="c97c6-316">Największego wolnego region jest największą wartość w kolumnie maksymalna, jak pokazano w następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-316">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>  
  
    ```  
    TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL  
    ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~  
    Free:  
    Small       8K        64K         46K       36          1,671K  
    Medium      80K       864K        349K      3           1,047K  
    Large       1,384K    1,278,848K  151,834K  12          1,822,015K  
    Summary     8K        1,278,848K  35,779K   51          1,824,735K  
    ```  
  
<a name="Physical"></a>   
##### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="c97c6-317">Aby ustalić, czy jest wystarczająca ilość fizycznej pamięci</span><span class="sxs-lookup"><span data-stu-id="c97c6-317">To determine whether there is enough physical memory</span></span>  
  
1. <span data-ttu-id="c97c6-318">Uruchamianie Menedżera zadań Windows.</span><span class="sxs-lookup"><span data-stu-id="c97c6-318">Start Windows Task Manager.</span></span>  
  
2. <span data-ttu-id="c97c6-319">Na **wydajności** kartę, sprawdź wartość zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="c97c6-319">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="c97c6-320">(W Windows 7, Przyjrzyj się **zatwierdzenia (KB)** w **grupy systemowej**.)</span><span class="sxs-lookup"><span data-stu-id="c97c6-320">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>  
  
     <span data-ttu-id="c97c6-321">Jeśli **całkowita** jest bliska **Limit**, kończy się w pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="c97c6-321">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="c97c6-322">Aby określić, ile pamięci zatwierdza sterty zarządzanej</span><span class="sxs-lookup"><span data-stu-id="c97c6-322">To determine how much memory the managed heap is committing</span></span>  
  
-   <span data-ttu-id="c97c6-323">Użyj `# Total committed bytes` licznika wydajności pamięci, aby uzyskać liczbę bajtów, które zatwierdza sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="c97c6-323">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="c97c6-324">Moduł zbierający elementy bezużyteczne zatwierdzeń fragmentów w segmencie, zgodnie z potrzebami, nie wszystkie w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-324">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c97c6-325">Nie używaj `# Bytes in all Heaps` liczników wydajności, ponieważ nie reprezentuje aktualnego stanu użycia pamięci w stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="c97c6-325">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="c97c6-326">Rozmiar generacji znajduje się w tej wartości i jest faktycznie jego rozmiar progu, oznacza to, rozmiar, który wywołuje wyrzucanie elementów bezużytecznych, jeśli generacja jest wypełniony przy użyciu obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-326">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="c97c6-327">W związku z tym ta wartość zazwyczaj wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="c97c6-327">Therefore, this value is usually zero.</span></span>  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="c97c6-328">Aby określić ilość pamięci sterty zarządzanej rezerwy</span><span class="sxs-lookup"><span data-stu-id="c97c6-328">To determine how much memory the managed heap reserves</span></span>  
  
-   <span data-ttu-id="c97c6-329">Użyj `# Total reserved bytes` licznika wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-329">Use the `# Total reserved bytes` memory performance counter.</span></span>  
  
     <span data-ttu-id="c97c6-330">Moduł zbierający elementy bezużyteczne zastrzega pamięć w segmentach i określić, gdzie segment uruchamia się za pomocą **eeheap** polecenia.</span><span class="sxs-lookup"><span data-stu-id="c97c6-330">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c97c6-331">Mimo że można określić ilość pamięci, które moduł odśmiecania pamięci przydziela dla każdego segmentu, rozmiar segmentu jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="c97c6-331">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="c97c6-332">Twoja aplikacja nigdy nie należy wprowadzić założeń dotyczących lub zależeć od rozmiaru określonego segmentu nie ma podejmować skonfigurować ilość pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-332">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
-   <span data-ttu-id="c97c6-333">W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-333">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="c97c6-334">**! eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="c97c6-334">**!eeheap -gc**</span></span>  
  
     <span data-ttu-id="c97c6-335">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="c97c6-335">The result is as follows.</span></span>  
  
    ```  
    Number of GC Heaps: 2  
    ------------------------------  
    Heap 0 (002db550)  
    generation 0 starts at 0x02abe29c  
    generation 1 starts at 0x02abdd08  
    generation 2 starts at 0x02ab0038  
    ephemeral segment allocation context: none  
     segment    begin allocated     size  
    02ab0000 02ab0038  02aceff4 0x0001efbc(126908)  
    Large object heap starts at 0x0aab0038  
     segment    begin allocated     size  
    0aab0000 0aab0038  0aab2278 0x00002240(8768)  
    Heap Size   0x211fc(135676)  
    ------------------------------  
    Heap 1 (002dc958)  
    generation 0 starts at 0x06ab1bd8  
    generation 1 starts at 0x06ab1bcc  
    generation 2 starts at 0x06ab0038  
    ephemeral segment allocation context: none  
     segment    begin allocated     size  
    06ab0000 06ab0038  06ab3be4 0x00003bac(15276)  
    Large object heap starts at 0x0cab0038  
     segment    begin allocated     size  
    0cab0000 0cab0038  0cab0048 0x00000010(16)  
    Heap Size    0x3bbc(15292)  
    ------------------------------  
    GC Heap Size   0x24db8(150968)  
    ```  
  
     <span data-ttu-id="c97c6-336">Adresy, wskazywanym przez "segmentu" adresów początkowy segmentów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-336">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="c97c6-337">Aby określić dużych obiektów w generacji 2</span><span class="sxs-lookup"><span data-stu-id="c97c6-337">To determine large objects in generation 2</span></span>  
  
-   <span data-ttu-id="c97c6-338">W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-338">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="c97c6-339">**! dumpheap-stat**</span><span class="sxs-lookup"><span data-stu-id="c97c6-339">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="c97c6-340">Jeśli zarządzanego stosu jest duży, **dumpheap** może potrwać kilka minut na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-340">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>  
  
     <span data-ttu-id="c97c6-341">Możesz zacząć analizować w ciągu ostatnich kilku wierszy danych wyjściowych, ponieważ ich listę obiektów, które najwięcej miejsca.</span><span class="sxs-lookup"><span data-stu-id="c97c6-341">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="c97c6-342">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c97c6-342">For example:</span></span>  
  
    ```  
    2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo  
    00155f80      533     15216804      Free  
    7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary  
    2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo  
    79124228   121143     29064120 System.Object[]  
    035f0ee4    81626     35588936 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    791242ec    40182     90664128 System.Collections.Hashtable+bucket[]  
    790fa3e0  3154024    137881448 System.String  
    Total 8454945 objects  
    ```  
  
     <span data-ttu-id="c97c6-343">Ostatni obiekt na liście jest ciągiem i zajmuje najwięcej miejsca na.</span><span class="sxs-lookup"><span data-stu-id="c97c6-343">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="c97c6-344">Można sprawdzić w aplikacji, aby zobaczyć, jak można optymalizować obiektów w postaci ciągów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-344">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="c97c6-345">Aby wyświetlić ciągów, które należą do zakresu od 150 do 200 bajtów, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-345">To see strings that are between 150 and 200 bytes, type the following:</span></span>  
  
     <span data-ttu-id="c97c6-346">**! dumpheap-typ System.String -minutowy 150 - max 200**</span><span class="sxs-lookup"><span data-stu-id="c97c6-346">**!dumpheap -type System.String -min 150 -max 200**</span></span>  
  
     <span data-ttu-id="c97c6-347">Przykładem wyniki jest następujący.</span><span class="sxs-lookup"><span data-stu-id="c97c6-347">An example of the results is as follows.</span></span>  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     <span data-ttu-id="c97c6-348">Za pomocą całkowitą zamiast ciągu dla Identyfikatora może być bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="c97c6-348">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="c97c6-349">Jeśli ten sam ciąg jest powtarza się tysiące razy, należy wziąć pod uwagę wewnętrzne przygotowanie ciągu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-349">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="c97c6-350">Aby uzyskać więcej informacji na temat wewnętrzne przygotowanie ciągu, zobacz temat referencyjny dotyczący <xref:System.String.Intern%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c97c6-350">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a><span data-ttu-id="c97c6-351">Aby określić odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="c97c6-351">To determine references to objects</span></span>  
  
-   <span data-ttu-id="c97c6-352">W WinDbg za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie, aby listy odwołania do obiektów:</span><span class="sxs-lookup"><span data-stu-id="c97c6-352">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>  
  
     <span data-ttu-id="c97c6-353">**! gcroot**</span><span class="sxs-lookup"><span data-stu-id="c97c6-353">**!gcroot**</span></span>  
  
     `-or-`  
  
-   <span data-ttu-id="c97c6-354">Aby ustalić, odwołania do określonego obiektu, należy uwzględnić adres:</span><span class="sxs-lookup"><span data-stu-id="c97c6-354">To determine the references for a specific object, include the address:</span></span>  
  
     <span data-ttu-id="c97c6-355">**! gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="c97c6-355">**!gcroot 1c37b2ac**</span></span>  
  
     <span data-ttu-id="c97c6-356">Znalezione na stosach obiekty główne może być wyników fałszywie dodatnich.</span><span class="sxs-lookup"><span data-stu-id="c97c6-356">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="c97c6-357">Aby uzyskać więcej informacji, użyj polecenia `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="c97c6-357">For more information, use the command `!help gcroot`.</span></span>  
  
    ```  
    ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->  
    19010b78(DemoApp.FormDemoApp)->  
    19011158(System.Windows.Forms.PropertyStore)->  
    … [omitted]  
    1c3745ec(System.Data.DataTable)->  
    1c3747a8(System.Data.DataColumnCollection)->  
    1c3747f8(System.Collections.Hashtable)->  
    1c376590(System.Collections.Hashtable+bucket[])->  
    1c376c98(System.Data.DataColumn)->  
    1c37b270(System.Data.Common.DoubleStorage)->  
    1c37b2ac(System.Double[])  
    Scan Thread 0 OSTHread 99c  
    Scan Thread 6 OSTHread 484  
    ```  
  
     <span data-ttu-id="c97c6-358">**Gcroot** polecenia może zająć dużo czasu na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-358">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="c97c6-359">Każdy obiekt, który nie jest odzyskiwane przez wyrzucanie elementów bezużytecznych jest obiektem na żywo.</span><span class="sxs-lookup"><span data-stu-id="c97c6-359">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="c97c6-360">Oznacza to, że niektóre główny jest bezpośrednio lub pośrednio trzymając na obiekt, więc **gcroot** powinna zwrócić informacje o ścieżce do obiektu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-360">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="c97c6-361">Należy sprawdzić wykresy zwracane i zobacz, dlaczego te obiekty są nadal istnieją odwołania.</span><span class="sxs-lookup"><span data-stu-id="c97c6-361">You should examine the graphs returned and see why these objects are still referenced.</span></span>  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="c97c6-362">Aby określić, czy finalizator została uruchomiona</span><span class="sxs-lookup"><span data-stu-id="c97c6-362">To determine whether a finalizer has been run</span></span>  
  
-   <span data-ttu-id="c97c6-363">Uruchom program test, który zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="c97c6-363">Run a test program that contains the following code:</span></span>  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     <span data-ttu-id="c97c6-364">Jeśli test nie zostanie rozwiązany, oznacza to, że moduł odśmiecania pamięci nie został odzyskiwaniu obiektów, ponieważ została wstrzymana finalizatory dla tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-364">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="c97c6-365"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metoda umożliwia finalizatory do wykonywania swoich zadań i rozwiąże problem.</span><span class="sxs-lookup"><span data-stu-id="c97c6-365">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="c97c6-366">Aby ustalić, czy istnieją obiekty oczekujące na sfinalizowana</span><span class="sxs-lookup"><span data-stu-id="c97c6-366">To determine whether there are objects waiting to be finalized</span></span>  
  
1. <span data-ttu-id="c97c6-367">W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-367">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="c97c6-368">**! finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="c97c6-368">**!finalizequeue**</span></span>  
  
     <span data-ttu-id="c97c6-369">Spójrz na liczbę obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-369">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="c97c6-370">Jeśli liczba jest wysokie, należy zbadać, dlaczego te finalizatory nie postępu na wszystkich lub nie postęp szybkiego wystarczająco.</span><span class="sxs-lookup"><span data-stu-id="c97c6-370">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>  
  
2. <span data-ttu-id="c97c6-371">Aby uzyskać dane wyjściowe wątków, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-371">To get an output of threads, type the following command:</span></span>  
  
     <span data-ttu-id="c97c6-372">**wątki — specjalne**</span><span class="sxs-lookup"><span data-stu-id="c97c6-372">**threads -special**</span></span>  
  
     <span data-ttu-id="c97c6-373">To polecenie dostarcza dane wyjściowe, takie jak poniżej.</span><span class="sxs-lookup"><span data-stu-id="c97c6-373">This command provides output such as the following.</span></span>  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     <span data-ttu-id="c97c6-374">Wątek finalizatora wskazuje, które finalizatora, jeśli jest aktualnie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="c97c6-374">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="c97c6-375">Wątek finalizatora nie jest uruchomiona żadnych finalizatorów, trwa oczekiwanie na zdarzenie nakazać mu wykonać swoją pracę.</span><span class="sxs-lookup"><span data-stu-id="c97c6-375">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="c97c6-376">W większości przypadków zostanie wyświetlony wątek finalizatora w tym stanie ponieważ działa na THREAD_HIGHEST_PRIORITY i powinna zakończyć działanie finalizatorów, jeśli istnieje bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="c97c6-376">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="c97c6-377">Aby określić ilość wolnego miejsca w zarządzanym stosie</span><span class="sxs-lookup"><span data-stu-id="c97c6-377">To determine the amount of free space in the managed heap</span></span>  
  
-   <span data-ttu-id="c97c6-378">W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-378">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="c97c6-379">**! dumpheap-wpisz bezpłatne - stat**</span><span class="sxs-lookup"><span data-stu-id="c97c6-379">**!dumpheap -type Free -stat**</span></span>  
  
     <span data-ttu-id="c97c6-380">To polecenie wyświetla całkowity rozmiar wszystkich obiektów bezpłatne na zarządzanym stosie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-380">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   <span data-ttu-id="c97c6-381">Aby określić ilość wolnego miejsca w generacji 0, wpisz następujące polecenie, aby uzyskać informacje dotyczące użycia pamięci przez generacji:</span><span class="sxs-lookup"><span data-stu-id="c97c6-381">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>  
  
     <span data-ttu-id="c97c6-382">**! eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="c97c6-382">**!eeheap -gc**</span></span>  
  
     <span data-ttu-id="c97c6-383">To polecenie wyświetla dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="c97c6-383">This command displays output similar to the following.</span></span> <span data-ttu-id="c97c6-384">Ostatni wiersz zawiera segment efemeryczny.</span><span class="sxs-lookup"><span data-stu-id="c97c6-384">The last line shows the ephemeral segment.</span></span>  
  
    ```  
    Heap 0 (0015ad08)  
    generation 0 starts at 0x49521f8c  
    generation 1 starts at 0x494d7f64  
    generation 2 starts at 0x007f0038  
    ephemeral segment allocation context: none  
    segment  begin     allocated  size  
    00178250 7a80d84c  7a82f1cc   0x00021980(137600)  
    00161918 78c50e40  78c7056c   0x0001f72c(128812)  
    007f0000 007f0038  047eed28   0x03ffecf0(67103984)  
    3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)  
    46120000 46120038  49e05d04   0x03ce5ccc(63855820)  
    ```  
  
-   <span data-ttu-id="c97c6-385">Oblicz przestrzeni używanej przez generacji 0:</span><span class="sxs-lookup"><span data-stu-id="c97c6-385">Calculate the space used by generation 0:</span></span>  
  
     <span data-ttu-id="c97c6-386">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="c97c6-386">**? 49e05d04-0x49521f8c**</span></span>  
  
     <span data-ttu-id="c97c6-387">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="c97c6-387">The result is as follows.</span></span> <span data-ttu-id="c97c6-388">Generacji 0 to około 9 MB.</span><span class="sxs-lookup"><span data-stu-id="c97c6-388">Generation 0 is approximately 9 MB.</span></span>  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   <span data-ttu-id="c97c6-389">Poniższe polecenie wykonuje ilość wolnego miejsca w zakresie generacji 0:</span><span class="sxs-lookup"><span data-stu-id="c97c6-389">The following command dumps the free space within the generation 0 range:</span></span>  
  
     <span data-ttu-id="c97c6-390">**! dumpheap-wpisz bezpłatne - stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="c97c6-390">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>  
  
     <span data-ttu-id="c97c6-391">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="c97c6-391">The result is as follows.</span></span>  
  
    ```  
    ------------------------------  
    Heap 0  
    total 409 objects  
    ------------------------------  
    Heap 1  
    total 0 objects  
    ------------------------------  
    Heap 2  
    total 0 objects  
    ------------------------------  
    Heap 3  
    total 0 objects  
    ------------------------------  
    total 409 objects  
    Statistics:  
          MT    Count TotalSize Class Name  
    0015a498      409   7296540      Free  
    Total 409 objects  
    ```  
  
     <span data-ttu-id="c97c6-392">Te dane wyjściowe pokazuje, że generacji 0 części stosu obiektów przy użyciu 9 MB miejsca i znajduje się 7 MB wolnego.</span><span class="sxs-lookup"><span data-stu-id="c97c6-392">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="c97c6-393">Ta analiza przedstawia zakres generacji 0 przyczynia się do fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-393">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="c97c6-394">Tę kwotę użycie sterty powinien obniżone z łącznej kwoty jako przyczynę fragmentacji przez obiekty długoterminowego.</span><span class="sxs-lookup"><span data-stu-id="c97c6-394">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="c97c6-395">Aby określić liczbę obiektów przypięte</span><span class="sxs-lookup"><span data-stu-id="c97c6-395">To determine the number of pinned objects</span></span>  
  
-   <span data-ttu-id="c97c6-396">W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-396">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="c97c6-397">**! gchandles**</span><span class="sxs-lookup"><span data-stu-id="c97c6-397">**!gchandles**</span></span>  
  
     <span data-ttu-id="c97c6-398">Statystyki, wyświetlane zawiera liczbę przypiętych uchwytów, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="c97c6-398">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="c97c6-399">Aby określić czas w wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="c97c6-399">To determine the length of time in a garbage collection</span></span>  
  
-   <span data-ttu-id="c97c6-400">Sprawdź `% Time in GC` licznika wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="c97c6-400">Examine the `% Time in GC` memory performance counter.</span></span>  
  
     <span data-ttu-id="c97c6-401">Wartość jest obliczana przy użyciu interwałów próbkowania.</span><span class="sxs-lookup"><span data-stu-id="c97c6-401">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="c97c6-402">Ponieważ liczniki zostały zaktualizowane na końcu każdej operacji wyrzucania elementów bezużytecznych, bieżąca przykładowa będzie mieć taką samą wartość jak w poprzednim przykładzie, jeśli żadne kolekcje, które wystąpiły interwału.</span><span class="sxs-lookup"><span data-stu-id="c97c6-402">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>  
  
     <span data-ttu-id="c97c6-403">Czas zbierania mnożąc interwałów próbkowania przy użyciu wartości procentowej.</span><span class="sxs-lookup"><span data-stu-id="c97c6-403">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>  
  
     <span data-ttu-id="c97c6-404">Następujące dane zawiera cztery próbkowania dwóch sekund do badania 8 sekund.</span><span class="sxs-lookup"><span data-stu-id="c97c6-404">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="c97c6-405">`Gen0`, `Gen1`, I `Gen2` kolumny zawierają liczbę wyrzucania elementów bezużytecznych, które wystąpiły podczas tego interwału dla danej generacji.</span><span class="sxs-lookup"><span data-stu-id="c97c6-405">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     <span data-ttu-id="c97c6-406">Te informacje nie są wyświetlane podczas wyrzucania elementów bezużytecznych wystąpił, ale można określić liczbę wyrzucania elementów bezużytecznych, które wystąpiły w odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-406">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="c97c6-407">Zakładając, że najgorszym przypadku, oraz generacji 0 wyrzucania elementów bezużytecznych zostało zakończone na początku drugiej interwał i jedenasty generację 0 wyrzucania elementów bezużytecznych zostało zakończone na końcu interwału piąty.</span><span class="sxs-lookup"><span data-stu-id="c97c6-407">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="c97c6-408">Czas między końcem dziesiątego i na końcu jedenasty wyrzucania elementów bezużytecznych jest około 2 sekundy, a licznik wydajności przedstawia 3%, aby był czas trwania jedenasty wyrzucania elementów bezużytecznych generacji 0 (% w ciągu kilku sekund 2 \* 3 = 60ms).</span><span class="sxs-lookup"><span data-stu-id="c97c6-408">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>  
  
     <span data-ttu-id="c97c6-409">W tym przykładzie istnieją 5 okresów.</span><span class="sxs-lookup"><span data-stu-id="c97c6-409">In this example, there are 5 periods.</span></span>  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     <span data-ttu-id="c97c6-410">Drugiej generacji 2 wyrzucania elementów bezużytecznych pracę trzeci przedział czasu i zostało zakończone w piątym odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="c97c6-410">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="c97c6-411">Zakładając, że najgorszym przypadku, ostatni wyrzucania elementów bezużytecznych był dla kolekcji generacji 0, które kończy się na początku drugiej interwał i 2 wyrzucania elementów bezużytecznych generacji zakończone na końcu piąty interwał.</span><span class="sxs-lookup"><span data-stu-id="c97c6-411">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="c97c6-412">W związku z tym czas od zakończenia operacji wyrzucania elementów bezużytecznych generacji 0 i na końcu wyrzucania elementów bezużytecznych generacji 2 jest 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="c97c6-412">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="c97c6-413">Ponieważ `% Time in GC` licznika wynosi 20%, maksymalną ilość czasu, w generacji 2 wyrzucania elementów bezużytecznych może miały jest (w sekundach 4 \* 20% = 800ms).</span><span class="sxs-lookup"><span data-stu-id="c97c6-413">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>  
  
-   <span data-ttu-id="c97c6-414">Alternatywnie, można określić długość wyrzucania elementów bezużytecznych za pomocą [zdarzenia ETW odzyskiwania pamięci](../../../docs/framework/performance/garbage-collection-etw-events.md)i Analizuj informacje, aby określić czas trwania operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-414">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>  
  
     <span data-ttu-id="c97c6-415">Na przykład następujące dane przedstawiono sekwencję zdarzeń, który wystąpił podczas niejednoczesne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-415">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>  
  
    ```  
    Timestamp    Event name  
    513052        GCSuspendEEBegin_V1  
    513078        GCSuspendEEEnd  
    513090        GCStart_V1  
    517890        GCEnd_V1  
    517894        GCHeapStats  
    517897        GCRestartEEBegin  
    517918        GCRestartEEEnd  
    ```  
  
     <span data-ttu-id="c97c6-416">Zawieszanie wątków zarządzanych trwało 26us (`GCSuspendEEEnd` — `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="c97c6-416">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>  
  
     <span data-ttu-id="c97c6-417">Rzeczywiste wyrzucania elementów bezużytecznych zajęło 4.8ms (`GCEnd_V1` — `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="c97c6-417">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>  
  
     <span data-ttu-id="c97c6-418">Wznawianie wątków zarządzanych trwało 21us (`GCRestartEEEnd` — `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="c97c6-418">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>  
  
     <span data-ttu-id="c97c6-419">Następujące dane wyjściowe zawiera przykład wyrzucanie elementów bezużytecznych w tle i obejmuje procesu, wątku i pola, zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c97c6-419">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="c97c6-420">(Nie wszystkie dane są wyświetlane).</span><span class="sxs-lookup"><span data-stu-id="c97c6-420">(Not all data is shown.)</span></span>  
  
    ```  
    timestamp(us)    event name            process    thread    event field  
    42504385        GCSuspendEEBegin_V1    Test.exe    4372             1  
    42504648        GCSuspendEEEnd         Test.exe    4372          
    42504816        GCStart_V1             Test.exe    4372        102019  
    42504907        GCStart_V1             Test.exe    4372        102020  
    42514170        GCEnd_V1               Test.exe    4372          
    42514204        GCHeapStats            Test.exe    4372        102020  
    42832052        GCRestartEEBegin       Test.exe    4372          
    42832136        GCRestartEEEnd         Test.exe    4372          
    63685394        GCSuspendEEBegin_V1    Test.exe    4744             6  
    63686347        GCSuspendEEEnd         Test.exe    4744          
    63784294        GCRestartEEBegin       Test.exe    4744          
    63784407        GCRestartEEEnd         Test.exe    4744          
    89931423        GCEnd_V1               Test.exe    4372        102019  
    89931464        GCHeapStats            Test.exe    4372          
    ```  
  
     <span data-ttu-id="c97c6-421">`GCStart_V1` Zdarzenie w 42504816 oznacza, że jest tle wyrzucania elementów bezużytecznych, ponieważ jest ostatnim polu `1`.</span><span class="sxs-lookup"><span data-stu-id="c97c6-421">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="c97c6-422">Staje się on wyrzucania elementów bezużytecznych nie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-422">This becomes garbage collection No.</span></span> <span data-ttu-id="c97c6-423">102019.</span><span class="sxs-lookup"><span data-stu-id="c97c6-423">102019.</span></span>  
  
     <span data-ttu-id="c97c6-424">`GCStart` Wystąpi zdarzenie, ponieważ nie istnieje potrzeba efemerycznego wyrzucania elementów bezużytecznych, przed rozpoczęciem bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="c97c6-424">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="c97c6-425">Staje się on wyrzucania elementów bezużytecznych nie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-425">This becomes garbage collection No.</span></span> <span data-ttu-id="c97c6-426">102020.</span><span class="sxs-lookup"><span data-stu-id="c97c6-426">102020.</span></span>  
  
     <span data-ttu-id="c97c6-427">W 42514170, wyrzucanie elementów bezużytecznych nie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-427">At 42514170, garbage collection No.</span></span> <span data-ttu-id="c97c6-428">102020 zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="c97c6-428">102020 finishes.</span></span> <span data-ttu-id="c97c6-429">Zarządzane wątki są ponownie uruchamiane na tym etapie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-429">The managed threads are restarted at this point.</span></span> <span data-ttu-id="c97c6-430">To pole jest wypełniane w wątku 4372, która wywołała to bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="c97c6-430">This is completed on thread 4372, which triggered this background garbage collection.</span></span>  
  
     <span data-ttu-id="c97c6-431">W wątku 4744 występuje zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="c97c6-431">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="c97c6-432">Jest to jedyny raz, w tle wyrzucanie elementów bezużytecznych ma wstrzymania zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="c97c6-432">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="c97c6-433">Ten czas trwania wynosi około 99ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="c97c6-433">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>  
  
     <span data-ttu-id="c97c6-434">`GCEnd` Zdarzeń do wyrzucania elementów bezużytecznych tła wynosi 89931423.</span><span class="sxs-lookup"><span data-stu-id="c97c6-434">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="c97c6-435">Oznacza to, że odzyskiwanie pamięci w tle trwał o 47seconds ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="c97c6-435">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>  
  
     <span data-ttu-id="c97c6-436">Gdy zarządzane wątki są uruchomione, widać dowolną liczbę tymczasowe wyrzucanie elementów bezużytecznych występuje.</span><span class="sxs-lookup"><span data-stu-id="c97c6-436">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="c97c6-437">Aby ustalić przyczyny ich wyzwolenia wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="c97c6-437">To determine what triggered a garbage collection</span></span>  
  
-   <span data-ttu-id="c97c6-438">W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie, aby wyświetlić wszystkie wątki z ich stosów wywołań:</span><span class="sxs-lookup"><span data-stu-id="c97c6-438">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>  
  
     <span data-ttu-id="c97c6-439">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="c97c6-439">**~\*kb**</span></span>  
  
     <span data-ttu-id="c97c6-440">To polecenie wyświetla dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="c97c6-440">This command displays output similar to the following.</span></span>  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     <span data-ttu-id="c97c6-441">Wyrzucanie elementów bezużytecznych zostało spowodowane przez powiadomienie małej ilości pamięci systemu operacyjnego, stos wywołań jest podobna, z tą różnicą, że wątek znajduje się wątek finalizatora.</span><span class="sxs-lookup"><span data-stu-id="c97c6-441">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="c97c6-442">Wątek finalizatora pobiera wiadomość z powiadomieniem asynchronicznego małej ilości pamięci i wywołuje wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c97c6-442">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>  
  
     <span data-ttu-id="c97c6-443">Jeśli wyrzucanie elementów bezużytecznych zostało spowodowane przez alokacji pamięci, stos wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="c97c6-443">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>  
  
    ```  
    0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration  
    0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1  
    0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18  
    0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b  
    0012f310 7a02ae4c mscorwks!Alloc+0x60  
    0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd  
    0012f424 300027f4 mscorwks!JIT_NewArr1+0x148  
    000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c  
    0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153  
    ```  
  
     <span data-ttu-id="c97c6-444">Pomocnik just-in-time (`JIT_New*`) po pewnym czasie wywołania `GCHeap::GarbageCollectGeneration`.</span><span class="sxs-lookup"><span data-stu-id="c97c6-444">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="c97c6-445">Jeśli okaże się, że wyrzucania generacji 2 są spowodowane przez alokacje, musisz określić obiekty, które są zbierane przez 2 wyrzucania elementów bezużytecznych generacji, a także jak ich unikać.</span><span class="sxs-lookup"><span data-stu-id="c97c6-445">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="c97c6-446">Oznacza to, że chcesz określić różnicę między początek i koniec 2 wyrzucania elementów bezużytecznych generacji i obiekty przez nie spowodował kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="c97c6-446">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>  
  
     <span data-ttu-id="c97c6-447">Na przykład wpisz następujące polecenie w debugerze, aby pokazać początku kolekcji generacji 2:</span><span class="sxs-lookup"><span data-stu-id="c97c6-447">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>  
  
     <span data-ttu-id="c97c6-448">**! dumpheap-stat**</span><span class="sxs-lookup"><span data-stu-id="c97c6-448">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="c97c6-449">Przykładowe dane wyjściowe (skróconej informacji wyświetlenie obiektów, które używają najwięcej miejsca na):</span><span class="sxs-lookup"><span data-stu-id="c97c6-449">Example output (abridged to show the objects that use the most space):</span></span>  
  
    ```  
    79124228    31857      9862328 System.Object[]  
    035f0384    25668     11601936 Toolkit.TlkPosition  
    00155f80    21248     12256296      Free  
    79103b6c   297003     13068132 System.Threading.ReaderWriterLock  
    7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary  
    7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary  
    035f0ee4    89192     38887712 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    7912c444    91616     71887080 System.Double[]  
    791242ec    32451     82462728 System.Collections.Hashtable+bucket[]  
    790fa3e0  2459154    112128436 System.String  
    Total 6471774 objects  
    ```  
  
     <span data-ttu-id="c97c6-450">Na koniec generacji 2, powtórz polecenie:</span><span class="sxs-lookup"><span data-stu-id="c97c6-450">Repeat the command at the end of generation 2:</span></span>  
  
     <span data-ttu-id="c97c6-451">**! dumpheap-stat**</span><span class="sxs-lookup"><span data-stu-id="c97c6-451">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="c97c6-452">Przykładowe dane wyjściowe (skróconej informacji wyświetlenie obiektów, które używają najwięcej miejsca na):</span><span class="sxs-lookup"><span data-stu-id="c97c6-452">Example output (abridged to show the objects that use the most space):</span></span>  
  
    ```  
    79124228    26648      9314256 System.Object[]  
    035f0384    25668     11601936 Toolkit.TlkPosition  
    79103b6c   296770     13057880 System.Threading.ReaderWriterLock  
    7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary  
    7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary  
    00155f80    13806     34007212      Free  
    035f0ee4    89187     38885532 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    791242ec    32370     82359768 System.Collections.Hashtable+bucket[]  
    790fa3e0  2440020    111341808 System.String  
    Total 6417525 objects  
    ```  
  
     <span data-ttu-id="c97c6-453">`double[]` Obiektów zniknął od końca danych wyjściowych, co oznacza, że zostały zebrane.</span><span class="sxs-lookup"><span data-stu-id="c97c6-453">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="c97c6-454">Obiekty te konta do około 70 MB.</span><span class="sxs-lookup"><span data-stu-id="c97c6-454">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="c97c6-455">Pozostałe obiekty nie został zmieniony wiele.</span><span class="sxs-lookup"><span data-stu-id="c97c6-455">The remaining objects did not change much.</span></span> <span data-ttu-id="c97c6-456">Dlatego te `double[]` obiekty zostały powód, dlaczego wystąpił ten wyrzucania elementów bezużytecznych generacji 2.</span><span class="sxs-lookup"><span data-stu-id="c97c6-456">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="c97c6-457">Następnym krokiem jest, aby ustalić, dlaczego `double[]` obiekty są dostępne i dlaczego ich zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="c97c6-457">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="c97c6-458">Możesz poprosić kodu dla deweloperów, gdzie pochodzi tych obiektów, lub użyć **gcroot** polecenia.</span><span class="sxs-lookup"><span data-stu-id="c97c6-458">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="c97c6-459">Aby ustalić, czy wysokie użycie procesora CPU jest spowodowany przez wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="c97c6-459">To determine whether high CPU usage is caused by garbage collection</span></span>  
  
-   <span data-ttu-id="c97c6-460">Korelowanie `% Time in GC` wartość licznika wydajności pamięci z czasem przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="c97c6-460">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>  
  
     <span data-ttu-id="c97c6-461">Jeśli `% Time in GC` wartość gwałtowne wzrosty w tym samym czasie jako czas przetwarzania, wyrzucanie elementów bezużytecznych powoduje wysokie użycie procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="c97c6-461">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="c97c6-462">W przeciwnym razie wykonaj profilowanie aplikacji można znaleźć, gdzie występuje wysokie użycie.</span><span class="sxs-lookup"><span data-stu-id="c97c6-462">Otherwise, profile the application to find where the high usage is occurring.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97c6-463">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c97c6-463">See also</span></span>

- [<span data-ttu-id="c97c6-464">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="c97c6-464">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
