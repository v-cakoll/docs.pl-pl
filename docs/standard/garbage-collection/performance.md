---
title: "Odzyskiwanie pamięci i wydajność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13f89749a4df3496b8c169e67c2f221a940568bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="07903-102">Odzyskiwanie pamięci i wydajność</span><span class="sxs-lookup"><span data-stu-id="07903-102">Garbage Collection and Performance</span></span>
<a name="top"></a><span data-ttu-id="07903-103">W tym temacie opisano problemy związane z użycia pamięci kolekcji i pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="07903-104">Rozwiązuje problemy, które odnoszą się do sterty zarządzanej, a wyjaśniono sposób zminimalizować wpływ operacji wyrzucania elementów bezużytecznych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07903-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="07903-105">Każde wydanie zawiera łącza do procedur, które służy do badania problemów.</span><span class="sxs-lookup"><span data-stu-id="07903-105">Each issue has links to procedures that you can use to investigate problems.</span></span>  
  
 <span data-ttu-id="07903-106">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="07903-106">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="07903-107">Narzędzia analizy wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-107">Performance Analysis Tools</span></span>](#performance_analysis_tools)  
  
-   [<span data-ttu-id="07903-108">Rozwiązywanie problemów z wydajnością</span><span class="sxs-lookup"><span data-stu-id="07903-108">Troubleshooting Performance Issues</span></span>](#troubleshooting_performance_issues)  
  
-   [<span data-ttu-id="07903-109">Wskazówki dotyczące rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="07903-109">Troubleshooting Guidelines</span></span>](#troubleshooting_guidelines)  
  
-   [<span data-ttu-id="07903-110">Procedury sprawdzania wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-110">Performance Check Procedures</span></span>](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a><span data-ttu-id="07903-111">Narzędzia analizy wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-111">Performance Analysis Tools</span></span>  
 <span data-ttu-id="07903-112">W poniższych sekcjach opisano narzędzia, które są dostępne do badania problemów kolekcji użycia i odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-112">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="07903-113">[Procedury](#performance_check_procedures) podane w dalszej części tego tematu odwoływać się do tych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="07903-113">The [procedures](#performance_check_procedures) provided later in this topic refer to these tools.</span></span>  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a><span data-ttu-id="07903-114">Liczniki wydajności pamięci</span><span class="sxs-lookup"><span data-stu-id="07903-114">Memory Performance Counters</span></span>  
 <span data-ttu-id="07903-115">Liczniki wydajności służy do zbierania danych wydajności.</span><span class="sxs-lookup"><span data-stu-id="07903-115">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="07903-116">Aby uzyskać instrukcje, zobacz [profilowanie środowiska uruchomieniowego](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="07903-116">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="07903-117">Kategoria .NET CLR pamięci liczników wydajności, zgodnie z opisem w [liczników wydajności w programie .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), informacje na temat modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="07903-117">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a><span data-ttu-id="07903-118">Debugowanie za pomocą SOS</span><span class="sxs-lookup"><span data-stu-id="07903-118">Debugging with SOS</span></span>  
 <span data-ttu-id="07903-119">Można użyć [debugera systemu Windows (WinDbg)](http://go.microsoft.com/fwlink/?LinkId=186482) do zbadania obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-119">You can use the [Windows Debugger (WinDbg)](http://go.microsoft.com/fwlink/?LinkId=186482) to inspect objects on the managed heap.</span></span>  
  
 <span data-ttu-id="07903-120">Aby zainstalować WinDbg, zainstalować narzędzi debugowania dla systemu Windows z [WDK i Developer Tools w sieci Web](http://go.microsoft.com/fwlink/?LinkID=103787).</span><span class="sxs-lookup"><span data-stu-id="07903-120">To install WinDbg, install Debugging Tools for Windows from the [WDK and Developer Tools Web site](http://go.microsoft.com/fwlink/?LinkID=103787).</span></span>  
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a><span data-ttu-id="07903-121">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="07903-121">Garbage Collection ETW Events</span></span>  
 <span data-ttu-id="07903-122">Śledzenie zdarzeń systemu Windows (ETW) to system śledzenia, który uzupełnia profilowania i obsługa w programie .NET Framework — profilowanie.</span><span class="sxs-lookup"><span data-stu-id="07903-122">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="07903-123">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [zdarzenia ETW wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md) przechwytywania przydatne informacje dotyczące analizowania sterty zarządzanej z punktu widzenia statystycznych.</span><span class="sxs-lookup"><span data-stu-id="07903-123">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="07903-124">Na przykład `GCStart_V1` zdarzenie, które jest wywoływane, gdy ma wystąpić wyrzucania elementów bezużytecznych, zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="07903-124">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>  
  
-   <span data-ttu-id="07903-125">Zbierane są które generowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-125">Which generation of objects is being collected.</span></span>  
  
-   <span data-ttu-id="07903-126">Co wyzwoliło wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-126">What triggered the garbage collection.</span></span>  
  
-   <span data-ttu-id="07903-127">Typ operacji wyrzucania elementów bezużytecznych (równoczesnych lub nie równoczesnych).</span><span class="sxs-lookup"><span data-stu-id="07903-127">Type of garbage collection (concurrent or not concurrent).</span></span>  
  
 <span data-ttu-id="07903-128">Rejestrowanie zdarzeń ETW jest wydajne i nie będzie maskował wszelkie problemy z wydajnością skojarzone z wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-128">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="07903-129">Proces może udostępniać swoje własne zdarzenia w połączeniu z zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="07903-129">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="07903-130">Podczas rejestrowania, zarówno zdarzeń aplikacji, jak i zdarzenia wyrzucania elementów bezużytecznych może zostać skorelowane ustalenie, jak i kiedy sterty problemów.</span><span class="sxs-lookup"><span data-stu-id="07903-130">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="07903-131">Na przykład aplikacja serwera może dostarczyć zdarzenia na początku i na końcu żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="07903-131">For example, a server application could provide events at the start and end of a client request.</span></span>  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a><span data-ttu-id="07903-132">Interfejsu API profilowania</span><span class="sxs-lookup"><span data-stu-id="07903-132">The Profiling API</span></span>  
 <span data-ttu-id="07903-133">Wspólnych interfejsów profilowania środowiska uruchomieniowego (języka wspólnego CLR) języka zawierają szczegółowe informacje o obiektach, które miały wpływ podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-133">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="07903-134">Profiler może otrzymać powiadomienie, gdy wyrzucania elementów bezużytecznych uruchamia i kończy się.</span><span class="sxs-lookup"><span data-stu-id="07903-134">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="07903-135">Może udostępnić raporty dotyczące obiektów na stercie zarządzanej, w tym identyfikację obiektów w każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="07903-135">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="07903-136">Aby uzyskać więcej informacji, zobacz [Przegląd profilowania](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="07903-136">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>  
  
 <span data-ttu-id="07903-137">Profilery zapewniają szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="07903-137">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="07903-138">Jednak złożonych profilowania potencjalnie można zmodyfikować zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07903-138">However, complex profilers can potentially modify an application's behavior.</span></span>  
  
### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="07903-139">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="07903-139">Application Domain Resource Monitoring</span></span>  
 <span data-ttu-id="07903-140">Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zasobów domen aplikacji monitorowania (ARM) umożliwia hostom monitorowanie użycia procesora CPU i pamięci według domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07903-140">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="07903-141">Aby uzyskać więcej informacji, zobacz [monitorowania zasobów domen aplikacji](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="07903-141">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>  
  
 [<span data-ttu-id="07903-142">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="07903-142">Back to top</span></span>](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="07903-143">Rozwiązywanie problemów z wydajnością</span><span class="sxs-lookup"><span data-stu-id="07903-143">Troubleshooting Performance Issues</span></span>  
 <span data-ttu-id="07903-144">Pierwszym krokiem jest [ustalić, czy problem jest rzeczywiście wyrzucanie elementów bezużytecznych](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="07903-144">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="07903-145">Jeśli okaże się, że jest, wybierz z poniższej listy, aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="07903-145">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>  
  
-   [<span data-ttu-id="07903-146">Wyjątek braku pamięci</span><span class="sxs-lookup"><span data-stu-id="07903-146">An out-of-memory exception is thrown</span></span>](#Issue_OOM)  
  
-   [<span data-ttu-id="07903-147">Proces używa zbyt dużej ilości pamięci</span><span class="sxs-lookup"><span data-stu-id="07903-147">The process uses too much memory</span></span>](#Issue_TooMuchMemory)  
  
-   [<span data-ttu-id="07903-148">Moduł zbierający elementy bezużyteczne nie odzyskać obiektów tyle szybko</span><span class="sxs-lookup"><span data-stu-id="07903-148">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)  
  
-   [<span data-ttu-id="07903-149">Sterta zarządzana za jest pofragmentowana.</span><span class="sxs-lookup"><span data-stu-id="07903-149">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)  
  
-   [<span data-ttu-id="07903-150">Wyrzucanie elementów kolekcji pauzy jest zbyt długa</span><span class="sxs-lookup"><span data-stu-id="07903-150">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)  
  
-   [<span data-ttu-id="07903-151">Generacji 0 jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="07903-151">Generation 0 is too big</span></span>](#Issue_Gen0)  
  
-   [<span data-ttu-id="07903-152">Użycie Procesora podczas wyrzucania elementów bezużytecznych jest zbyt wysoka</span><span class="sxs-lookup"><span data-stu-id="07903-152">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="07903-153">Problem: Zgłoszono wyjątek braku pamięci</span><span class="sxs-lookup"><span data-stu-id="07903-153">Issue: An Out-of-Memory Exception Is Thrown</span></span>  
 <span data-ttu-id="07903-154">Istnieją dwa uzasadnione przypadki dla zarządzanego <xref:System.OutOfMemoryException> zostanie wygenerowany:</span><span class="sxs-lookup"><span data-stu-id="07903-154">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>  
  
-   <span data-ttu-id="07903-155">Zaczyna brakować pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="07903-155">Running out of virtual memory.</span></span>  
  
     <span data-ttu-id="07903-156">Moduł zbierający elementy bezużyteczne przydziela pamięć z systemu w segmentach wstępnie ustalony rozmiar.</span><span class="sxs-lookup"><span data-stu-id="07903-156">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="07903-157">Alokacja wymaga dodatkowych segmentu, ale nie nie ciągłego wolnego bloku pozostanie w obszarze pamięci wirtualnej procesu, alokacji sterty zarządzanej zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="07903-157">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>  
  
-   <span data-ttu-id="07903-158">Nie ma wystarczającej ilości pamięci fizycznej do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="07903-158">Not having enough physical memory to allocate.</span></span>  
  
|<span data-ttu-id="07903-159">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-159">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="07903-160">Ustal, czy jest zarządzany wyjątek braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-160">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="07903-161">Określ ilość pamięci wirtualnej może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="07903-161">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="07903-162">Ustal, czy jest wystarczająca ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="07903-162">Determine whether there is enough physical memory.</span></span>](#Physical)|  
  
 <span data-ttu-id="07903-163">Jeśli okaże się, że wyjątku nie jest uzasadnione, skontaktuj się z pomocą Microsoft dział obsługi klienta i pomocy technicznej następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="07903-163">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>  
  
-   <span data-ttu-id="07903-164">Stos o zarządzanym wyjątku braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-164">The stack with the managed out-of-memory exception.</span></span>  
  
-   <span data-ttu-id="07903-165">Pełny zrzut pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-165">Full memory dump.</span></span>  
  
-   <span data-ttu-id="07903-166">Dane, gdy okaże się, że nie jest uzasadnione wyjątku braku pamięci, włącznie z danymi, pokazujący pamięci, wirtualny lub fizyczny nie jest rozwiązaniem problemu.</span><span class="sxs-lookup"><span data-stu-id="07903-166">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="07903-167">Problem: Proces używa zbyt dużej ilości pamięci</span><span class="sxs-lookup"><span data-stu-id="07903-167">Issue: The Process Uses Too Much Memory</span></span>  
 <span data-ttu-id="07903-168">Typowe zakłada się, że użycie pamięci wyświetlane na **wydajności** kartę Menedżera zadań systemu Windows można wskazać, kiedy używana jest zbyt dużej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-168">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="07903-169">Jednakże które wyświetlają odnoszą się do zestawu roboczego; nie dostarcza informacje na temat użycia pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="07903-169">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>  
  
 <span data-ttu-id="07903-170">Jeśli okaże się, że przyczyną problemu jest sterty zarządzanej, musi pomiarów sterty zarządzanej w celu określenia wszelkich wzorce.</span><span class="sxs-lookup"><span data-stu-id="07903-170">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>  
  
 <span data-ttu-id="07903-171">Jeśli okaże się, że problem nie jest spowodowany przez sterty zarządzanej, należy użyć debugowanie natywne.</span><span class="sxs-lookup"><span data-stu-id="07903-171">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>  
  
|<span data-ttu-id="07903-172">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-172">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="07903-173">Określ ilość pamięci wirtualnej może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="07903-173">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="07903-174">Określ, ile pamięci sterty zarządzanej zatwierdza.</span><span class="sxs-lookup"><span data-stu-id="07903-174">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="07903-175">Określ, ile pamięci sterty zarządzanej rezerwuje.</span><span class="sxs-lookup"><span data-stu-id="07903-175">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="07903-176">Określ dużych obiektów podczas generowania 2.</span><span class="sxs-lookup"><span data-stu-id="07903-176">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="07903-177">Określ odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-177">Determine references to objects.</span></span>](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="07903-178">Problem: Moduł zbierający elementy bezużyteczne nie odzyskać obiektów tyle szybko</span><span class="sxs-lookup"><span data-stu-id="07903-178">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>  
 <span data-ttu-id="07903-179">Wygląda na to, jak obiekty nie są odzyskane zgodnie z oczekiwaniami dotyczącymi wyrzucanie elementów bezużytecznych, należy ustalić, czy istnieją silne odwołań do tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-179">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>  
  
 <span data-ttu-id="07903-180">Może również wystąpi ten problem, jeśli nie było żadnych wyrzucanie elementów bezużytecznych generacji, która zawiera obiekt martwy, co oznacza, że finalizatora dla obiekt martwy nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="07903-180">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="07903-181">Na przykład jest to możliwe po uruchomieniu aplikacji jednowątkowego apartamentu (STA) i wątku tej usługi, których nie można wywołać w kolejce finalizatora do niego.</span><span class="sxs-lookup"><span data-stu-id="07903-181">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>  
  
|<span data-ttu-id="07903-182">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-182">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="07903-183">Sprawdź odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-183">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="07903-184">Ustal, czy finalizator został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="07903-184">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="07903-185">Ustal, czy istnieją obiekty oczekujące na sfinalizowana.</span><span class="sxs-lookup"><span data-stu-id="07903-185">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="07903-186">Problem: Zarządzane sterty jest zbyt pofragmentowana.</span><span class="sxs-lookup"><span data-stu-id="07903-186">Issue: The Managed Heap Is Too fragmented</span></span>  
 <span data-ttu-id="07903-187">Poziom fragmentacji jest obliczana jako stosunek wolnego miejsca za pośrednictwem całkowitej ilości pamięci przydzielony do generowania.</span><span class="sxs-lookup"><span data-stu-id="07903-187">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="07903-188">Generacji 2 akceptowalnego poziomu fragmentacji jest nie więcej niż 20%.</span><span class="sxs-lookup"><span data-stu-id="07903-188">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="07903-189">Ponieważ generacji 2 można uzyskać bardzo duży stopień fragmentacji ma większe znaczenie niż wartość bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="07903-189">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>  
  
 <span data-ttu-id="07903-190">Mających duże ilości wolnego miejsca w generacji 0 nie jest problem, ponieważ jest generowanie gdzie nowe obiekty są przydzielone.</span><span class="sxs-lookup"><span data-stu-id="07903-190">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>  
  
 <span data-ttu-id="07903-191">Fragmentacja zawsze występuje w sterty dużego obiektu, ponieważ nie jest skompaktować.</span><span class="sxs-lookup"><span data-stu-id="07903-191">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="07903-192">Bezpłatne obiektów, które znajdują się obok siebie naturalnie są zwijane do jednego miejsca do spełnienia żądań alokacji dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="07903-192">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>  
  
 <span data-ttu-id="07903-193">Fragmentacja może stać się problemem w generacji 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="07903-193">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="07903-194">Jeśli te generacje po wyrzucania elementów bezużytecznych znajduje się duża ilość wolnego miejsca, użycie obiektu aplikacji może wymagać modyfikacji i należy rozważyć ponownej oceny okresu istnienia obiektów długoterminowej.</span><span class="sxs-lookup"><span data-stu-id="07903-194">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>  
  
 <span data-ttu-id="07903-195">Przypinanie nadmiernego obiektów można zwiększyć fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="07903-195">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="07903-196">Jeśli fragmentacji jest wysoka, można przypięty za dużo obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-196">If fragmentation is high, too many objects could be pinned.</span></span>  
  
 <span data-ttu-id="07903-197">Jeśli fragmentacji pamięci wirtualnej uniemożliwia Dodawanie segmentów moduł garbage collector, przyczyn może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="07903-197">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>  
  
-   <span data-ttu-id="07903-198">Częste ładowanie i zwalnianie wiele małych zestawów.</span><span class="sxs-lookup"><span data-stu-id="07903-198">Frequent loading and unloading of many small assemblies.</span></span>  
  
-   <span data-ttu-id="07903-199">Zawierający zbyt wiele odwołań do obiektów COM, gdy współdziałanie z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="07903-199">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>  
  
-   <span data-ttu-id="07903-200">Tworzenie dużych obiektów przejściowy, co powoduje, że sterty dużego obiektu można przydzielić i często bez sterty segmentów.</span><span class="sxs-lookup"><span data-stu-id="07903-200">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>  
  
     <span data-ttu-id="07903-201">Gdy hostingu środowiska CLR, aplikacja może zażądać zachowanie modułu zbierającego elementy bezużyteczne jego segmentów.</span><span class="sxs-lookup"><span data-stu-id="07903-201">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="07903-202">Pozwala to zmniejszyć częstotliwość alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="07903-202">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="07903-203">Jest to zrobić za pomocą flagi STARTUP_HOARD_GC_VM w [STARTUP_FLAGS — wyliczenie](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="07903-203">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
|<span data-ttu-id="07903-204">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-204">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="07903-205">Określ ilość wolnego miejsca na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-205">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="07903-206">Określ liczbę unieruchomionych obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-206">Determine the number of pinned objects.</span></span>](#Pinned)|  
  
 <span data-ttu-id="07903-207">Jeśli uważasz, że nie stanowi uzasadnionych fragmentacji, skontaktuj się z obsługi klienta firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="07903-207">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="07903-208">Problem: Pauzy kolekcji pamięci jest zbyt długa</span><span class="sxs-lookup"><span data-stu-id="07903-208">Issue: Garbage Collection Pauses Are Too Long</span></span>  
 <span data-ttu-id="07903-209">Wyrzucanie elementów bezużytecznych działa w czasie rzeczywistym miękkie, więc aplikacja musi mieć możliwość tolerować niektórych pauzy.</span><span class="sxs-lookup"><span data-stu-id="07903-209">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="07903-210">Kryterium nietrwałego czasu rzeczywistego jest, że 95% operacji musi zostać zakończone na czas.</span><span class="sxs-lookup"><span data-stu-id="07903-210">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>  
  
 <span data-ttu-id="07903-211">W współbieżne odzyskiwanie pamięci zarządzanych wątków mogą być uruchamiane podczas zbierania, co oznacza, że pauzy są minimalne.</span><span class="sxs-lookup"><span data-stu-id="07903-211">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>  
  
 <span data-ttu-id="07903-212">Tylko kilka milisekund ostatni tymczasowych wyrzucania (generacji 0 i 1), więc zmniejszenie pauzy zwykle nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="07903-212">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="07903-213">Można jednak zmniejszyć pauzy w kolekcjach generacji 2, zmieniając wzorzec żądań alokacji przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="07903-213">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>  
  
 <span data-ttu-id="07903-214">Inny, bardziej precyzyjne metoda polega na użyciu [zdarzenia ETW wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="07903-214">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="07903-215">Chronometraż dla kolekcji można znaleźć, dodając różnice sygnatury czasowe sekwencji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="07903-215">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="07903-216">Sekwencja całą kolekcję obejmuje zawieszenie aparat wykonywania, wyrzucanie elementów bezużytecznych sam i wznowienie aparat wykonywania.</span><span class="sxs-lookup"><span data-stu-id="07903-216">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>  
  
 <span data-ttu-id="07903-217">Można użyć [powiadomienia dotyczące odzyskiwania pamięci](../../../docs/standard/garbage-collection/notifications.md) można określić, czy serwer ma mieć kolekcji generacji 2 i określa, czy Przekierowanie żądania do innego serwera można zmniejszyć problemów z pauzy.</span><span class="sxs-lookup"><span data-stu-id="07903-217">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>  
  
|<span data-ttu-id="07903-218">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-218">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="07903-219">Określ czas w wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-219">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="07903-220">Określ, co spowodowało wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-220">Determine what caused a garbage collection.</span></span>](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="07903-221">Problem: Generacji 0 jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="07903-221">Issue: Generation 0 Is Too Big</span></span>  
 <span data-ttu-id="07903-222">Generowanie 0 jest mogą mieć większą liczbę obiektów w systemie 64-bitowym, szczególnie w przypadku odzyskiwanie pamięci na serwerze można użyć zamiast stacji roboczej wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-222">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="07903-223">To dlatego próg do wyzwolenia generacji 0 wyrzucania elementów bezużytecznych jest wyższy w tych środowiskach, a kolekcje generacji 0 mogą pobrać znacznie większe.</span><span class="sxs-lookup"><span data-stu-id="07903-223">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="07903-224">Zwiększona wydajność aplikacji przydziela pamięć więcej wywoła wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-224">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="07903-225">Problem: Użycie Procesora podczas wyrzucania elementów bezużytecznych jest zbyt wysoka</span><span class="sxs-lookup"><span data-stu-id="07903-225">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>  
 <span data-ttu-id="07903-226">Użycie procesora CPU będzie wysoka podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-226">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="07903-227">Jeśli znaczną ilość czasu procesu jest przeznaczony na wyrzucanie elementów bezużytecznych, liczby kolekcji jest zbyt częste lub kolekcji jest zbyt długo trwające.</span><span class="sxs-lookup"><span data-stu-id="07903-227">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="07903-228">Wyrzucanie elementów bezużytecznych do częściej powoduje, że alokacji większa liczba obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-228">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="07903-229">Zmniejsz częstotliwość przydzielania zmniejsza częstotliwość odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-229">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>  
  
 <span data-ttu-id="07903-230">Stawki alokacji można monitorować za pomocą `Allocated Bytes/second` licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="07903-230">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="07903-231">Aby uzyskać więcej informacji, zobacz [liczników wydajności w programie .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="07903-231">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>  
  
 <span data-ttu-id="07903-232">Czas trwania kolekcji się głównie liczba obiektów, które pozostają aktualne po po alokacji.</span><span class="sxs-lookup"><span data-stu-id="07903-232">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="07903-233">Moduł zbierający elementy bezużyteczne musi przechodzić przez dużą ilość pamięci, jeśli wiele obiektów mają być zbierane.</span><span class="sxs-lookup"><span data-stu-id="07903-233">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="07903-234">Praca kompaktowania przy życiu jest czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="07903-234">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="07903-235">Aby ustalić, ile obiekty zostały obsłużone podczas zbierania, należy ustawić punkt przerwania w debugerze po zakończeniu wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="07903-235">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>  
  
|<span data-ttu-id="07903-236">Testy wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-236">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="07903-237">Ustal, jeśli przyczyną wysokiego użycia procesora CPU jest wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-237">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="07903-238">Ustaw punkt przerwania po zakończeniu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-238">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|  
  
 [<span data-ttu-id="07903-239">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="07903-239">Back to top</span></span>](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a><span data-ttu-id="07903-240">Wskazówki dotyczące rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="07903-240">Troubleshooting Guidelines</span></span>  
 <span data-ttu-id="07903-241">W tej sekcji opisano wskazówki, które należy wziąć pod uwagę rozpoczęciem badań sieci.</span><span class="sxs-lookup"><span data-stu-id="07903-241">This section describes guidelines that you should consider as you begin your investigations.</span></span>  
  
### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="07903-242">Stacji roboczej lub serwera wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="07903-242">Workstation or Server Garbage Collection</span></span>  
 <span data-ttu-id="07903-243">Określają, czy używasz poprawnego typu wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-243">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="07903-244">Jeśli aplikacja używa wielu wątków i wystąpienia obiektów, użyj odzyskiwanie pamięci na serwerze zamiast stacji roboczej wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-244">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="07903-245">Odzyskiwanie pamięci na serwerze działa na wielu wątków stacji roboczej wyrzucanie elementów bezużytecznych wymaga wiele wystąpień aplikacji do ich własnych wątków kolekcji pamięci i konkurują o czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="07903-245">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>  
  
 <span data-ttu-id="07903-246">Aplikacja z niskim obciążeniu, rzadko w tle, na przykład usługi, która wykonuje zadania może użyć stacji roboczej wyrzucanie elementów bezużytecznych z współbieżne odzyskiwanie pamięci wyłączone.</span><span class="sxs-lookup"><span data-stu-id="07903-246">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>  
  
### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="07903-247">Kiedy do mierzenia rozmiaru sterty zarządzanej</span><span class="sxs-lookup"><span data-stu-id="07903-247">When to Measure the Managed Heap Size</span></span>  
 <span data-ttu-id="07903-248">Jeśli nie używasz profilera, będzie musiał utworzyć spójne wzorzec pomiaru skutecznie zdiagnozować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="07903-248">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="07903-249">Należy rozważyć następujące kwestie do ustanawiania harmonogramu:</span><span class="sxs-lookup"><span data-stu-id="07903-249">Consider the following points to establish a schedule:</span></span>  
  
-   <span data-ttu-id="07903-250">Jeśli mierzonych po wyrzucania elementów bezużytecznych generacji 2 całego sterty zarządzanej będzie bezpłatna pamięci (martwy obiektów).</span><span class="sxs-lookup"><span data-stu-id="07903-250">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>  
  
-   <span data-ttu-id="07903-251">Jeśli mierzonych natychmiast po wyrzucania elementów bezużytecznych generacji 0 obiektów pokolenia 1 i 2 nie będą zbierane jeszcze.</span><span class="sxs-lookup"><span data-stu-id="07903-251">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>  
  
-   <span data-ttu-id="07903-252">Jeśli mierzonych bezpośrednio przed wyrzucania elementów bezużytecznych będzie zmierzyć tyle alokacji, jak to możliwe, przed rozpoczęciem wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-252">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>  
  
-   <span data-ttu-id="07903-253">Pomiaru podczas wyrzucania elementów bezużytecznych jest powodować problemów, ponieważ moduł zbierający elementy bezużyteczne struktur danych nie znajdują się w nieprawidłowym stanie dla operacji przechodzenia i nie można udzielić, wyświetlenie pełnych wyników.</span><span class="sxs-lookup"><span data-stu-id="07903-253">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="07903-254">To jest celowe.</span><span class="sxs-lookup"><span data-stu-id="07903-254">This is by design.</span></span>  
  
-   <span data-ttu-id="07903-255">Używając stacji roboczej wyrzucanie elementów bezużytecznych z współbieżne odzyskiwanie pamięci, regeneracji obiekty nie są kompaktowanie, dlatego rozmiar stosu może być taka sama lub większa (fragmentacja można wydawać będzie większy).</span><span class="sxs-lookup"><span data-stu-id="07903-255">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>  
  
-   <span data-ttu-id="07903-256">Współbieżne odzyskiwanie pamięci na generacji 2 jest opóźnione, gdy zbyt duże obciążenie pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="07903-256">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>  
  
 <span data-ttu-id="07903-257">W poniższej procedurze opisano, jak ustawić punkt przerwania, dzięki czemu można zmierzyć sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-257">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="07903-258">Aby ustawić punkt przerwania po zakończeniu wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="07903-258">To set a breakpoint at the end of garbage collection</span></span>  
  
-   <span data-ttu-id="07903-259">W WinDbg z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="07903-259">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="07903-260">**BP mscorwks! WKS::GCHeap::RestartEE "j (dwo (mscorwks! WKS::GCHeap::GcCondemnedGeneration) == 2) "kb"; " g ""**</span><span class="sxs-lookup"><span data-stu-id="07903-260">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>  
  
     <span data-ttu-id="07903-261">gdzie **GcCondemnedGeneration** ma ustawioną wartość odpowiednią generacji.</span><span class="sxs-lookup"><span data-stu-id="07903-261">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="07903-262">To polecenie wymaga symboli prywatnych.</span><span class="sxs-lookup"><span data-stu-id="07903-262">This command requires private symbols.</span></span>  
  
     <span data-ttu-id="07903-263">To polecenie wymusza podziału, jeśli **RestartEE** jest wykonywana po odzyskano obiektów pokolenia 2 dla wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-263">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>  
  
     <span data-ttu-id="07903-264">W pamięci serwera, wymaga tylko jednego wątku **RestartEE**, więc punkt przerwania zostanie przeprowadzona tylko raz podczas generowania 2 wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-264">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>  
  
 [<span data-ttu-id="07903-265">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="07903-265">Back to top</span></span>](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a><span data-ttu-id="07903-266">Procedury sprawdzania wydajności</span><span class="sxs-lookup"><span data-stu-id="07903-266">Performance Check Procedures</span></span>  
 <span data-ttu-id="07903-267">W tej sekcji opisano następujące procedury, aby ustalić przyczynę problemu z wydajnością:</span><span class="sxs-lookup"><span data-stu-id="07903-267">This section describes the following procedures to isolate the cause of your performance issue:</span></span>  
  
-   [<span data-ttu-id="07903-268">Ustal, czy przyczyną problemu jest wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-268">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)  
  
-   [<span data-ttu-id="07903-269">Ustal, czy jest zarządzany wyjątek braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-269">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)  
  
-   [<span data-ttu-id="07903-270">Określ ilość pamięci wirtualnej może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="07903-270">Determine how much virtual memory can be reserved.</span></span>](#GetVM)  
  
-   [<span data-ttu-id="07903-271">Ustal, czy jest wystarczająca ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="07903-271">Determine whether there is enough physical memory.</span></span>](#Physical)  
  
-   [<span data-ttu-id="07903-272">Określ, ile pamięci sterty zarządzanej zatwierdza.</span><span class="sxs-lookup"><span data-stu-id="07903-272">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)  
  
-   [<span data-ttu-id="07903-273">Określ, ile pamięci sterty zarządzanej rezerwuje.</span><span class="sxs-lookup"><span data-stu-id="07903-273">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)  
  
-   [<span data-ttu-id="07903-274">Określ dużych obiektów podczas generowania 2.</span><span class="sxs-lookup"><span data-stu-id="07903-274">Determine large objects in generation 2.</span></span>](#ExamineGen2)  
  
-   [<span data-ttu-id="07903-275">Określ odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-275">Determine references to objects.</span></span>](#ObjRef)  
  
-   [<span data-ttu-id="07903-276">Ustal, czy finalizator został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="07903-276">Determine whether a finalizer has been run.</span></span>](#Induce)  
  
-   [<span data-ttu-id="07903-277">Ustal, czy istnieją obiekty oczekujące na sfinalizowana.</span><span class="sxs-lookup"><span data-stu-id="07903-277">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)  
  
-   [<span data-ttu-id="07903-278">Określ ilość wolnego miejsca na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-278">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)  
  
-   [<span data-ttu-id="07903-279">Określ liczbę unieruchomionych obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-279">Determine the number of pinned objects.</span></span>](#Pinned)  
  
-   [<span data-ttu-id="07903-280">Określ czas w wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-280">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)  
  
-   [<span data-ttu-id="07903-281">Określ, co wyzwoliło wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-281">Determine what triggered a garbage collection.</span></span>](#Triggered)  
  
-   [<span data-ttu-id="07903-282">Ustal, czy przyczyną wysokiego użycia procesora CPU jest wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-282">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="07903-283">Aby określić, czy przyczyną problemu jest wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="07903-283">To determine whether the problem is caused by garbage collection</span></span>  
  
-   <span data-ttu-id="07903-284">Sprawdź następujące liczniki wydajności pamięci dwóch:</span><span class="sxs-lookup"><span data-stu-id="07903-284">Examine the following two memory performance counters:</span></span>  
  
    -   <span data-ttu-id="07903-285">**% Czasu potrzebnego na Odzyskiwanie**.</span><span class="sxs-lookup"><span data-stu-id="07903-285">**% Time in GC**.</span></span> <span data-ttu-id="07903-286">Wyświetla procent minionego czasu, jaki był poświęcony na operację wyrzucania od ostatniego cyklu wyrzucania elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="07903-286">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="07903-287">Ten licznik umożliwia określenie, czy moduł zbierający elementy bezużyteczne zużywa zbyt dużo czasu, aby udostępnić miejsce na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-287">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="07903-288">Jeśli czas spędzony w pamięci jest stosunkowo niska, który może wskazywać na problem zasobów poza sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-288">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="07903-289">Ten licznik nie może być niedokładna, gdy są one jednoczesnych lub uczestniczy odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="07903-289">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>  
  
    -   <span data-ttu-id="07903-290">**# Całkowita liczba Zadeklarowane bajty**.</span><span class="sxs-lookup"><span data-stu-id="07903-290">**# Total committed Bytes**.</span></span> <span data-ttu-id="07903-291">Wyświetlana jest ilość pamięci wirtualnej zarezerwowanej aktualnie przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="07903-291">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="07903-292">Ten licznik umożliwia określenie, czy pamięci używane przez moduł garbage collector jest nadmierne część pamięci, która korzysta z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07903-292">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>  
  
     <span data-ttu-id="07903-293">Większość liczników wydajności pamięci jest aktualizowany po zakończeniu każdej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-293">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="07903-294">W związku z tym nie mogą one uwzględniać bieżącego warunki, które chcesz uzyskać informacje.</span><span class="sxs-lookup"><span data-stu-id="07903-294">Therefore, they may not reflect the current conditions that you want information about.</span></span>  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="07903-295">Aby określić, czy wyjątek braku pamięci jest zarządzany</span><span class="sxs-lookup"><span data-stu-id="07903-295">To determine whether the out-of-memory exception is managed</span></span>  
  
1.  <span data-ttu-id="07903-296">W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadować typu wyjątku wydruku (**pe**) polecenia:</span><span class="sxs-lookup"><span data-stu-id="07903-296">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>  
  
     <span data-ttu-id="07903-297">**! pe**</span><span class="sxs-lookup"><span data-stu-id="07903-297">**!pe**</span></span>  
  
     <span data-ttu-id="07903-298">Jeśli wyjątek jest zarządzany, <xref:System.OutOfMemoryException> jest wyświetlana jako typ wyjątku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="07903-298">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2.  <span data-ttu-id="07903-299">Dane wyjściowe nie określony wyjątek, należy ustalić, który wątek wyjątku braku pamięci jest z.</span><span class="sxs-lookup"><span data-stu-id="07903-299">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="07903-300">Wpisz następujące polecenie w debugerze, aby wyświetlić wszystkie wątki z ich stosy wywołań:</span><span class="sxs-lookup"><span data-stu-id="07903-300">Type the following command in the debugger to show all the threads with their call stacks:</span></span>  
  
     <span data-ttu-id="07903-301">**~\*KB**</span><span class="sxs-lookup"><span data-stu-id="07903-301">**~\*kb**</span></span>  
  
     <span data-ttu-id="07903-302">Wątek ze stosu, który ma wywołań wyjątków jest określane przez `RaiseTheException` argumentu.</span><span class="sxs-lookup"><span data-stu-id="07903-302">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="07903-303">To jest obiektem zarządzanym wyjątku.</span><span class="sxs-lookup"><span data-stu-id="07903-303">This is the managed exception object.</span></span>  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3.  <span data-ttu-id="07903-304">Następujące polecenie służy do zrzutu wyjątków zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="07903-304">You can use the following command to dump nested exceptions.</span></span>  
  
     <span data-ttu-id="07903-305">**! pe-zagnieżdżonych**</span><span class="sxs-lookup"><span data-stu-id="07903-305">**!pe -nested**</span></span>  
  
     <span data-ttu-id="07903-306">Jeśli nie znajdziesz żadnych wyjątków, wyjątek braku pamięci pochodzi z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="07903-306">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="07903-307">Aby określić ilość pamięci wirtualnej może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="07903-307">To determine how much virtual memory can be reserved</span></span>  
  
-   <span data-ttu-id="07903-308">W WinDbg z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie, aby pobrać największego wolnego regionu:</span><span class="sxs-lookup"><span data-stu-id="07903-308">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>  
  
     <span data-ttu-id="07903-309">**! adresów — podsumowanie**</span><span class="sxs-lookup"><span data-stu-id="07903-309">**!address -summary**</span></span>  
  
     <span data-ttu-id="07903-310">Największego wolnego regionu jest wyświetlana, jak pokazano w następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="07903-310">The largest free region is displayed as shown in the following output.</span></span>  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     <span data-ttu-id="07903-311">W tym przykładzie rozmiar największego wolnego obszaru to około 24000 KB (3A980 w formacie szesnastkowym).</span><span class="sxs-lookup"><span data-stu-id="07903-311">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="07903-312">Ten region jest znacznie mniejszy niż moduł zbierający elementy bezużyteczne wymagań segment.</span><span class="sxs-lookup"><span data-stu-id="07903-312">This region is much smaller than what the garbage collector needs for a segment.</span></span>  
  
     <span data-ttu-id="07903-313">—lub—</span><span class="sxs-lookup"><span data-stu-id="07903-313">-or-</span></span>  
  
-   <span data-ttu-id="07903-314">Użyj **vmstat** polecenia:</span><span class="sxs-lookup"><span data-stu-id="07903-314">Use the **vmstat** command:</span></span>  
  
     <span data-ttu-id="07903-315">**! vmstat**</span><span class="sxs-lookup"><span data-stu-id="07903-315">**!vmstat**</span></span>  
  
     <span data-ttu-id="07903-316">Największego wolnego regionu jest największą wartość w kolumnie maksymalna, jak pokazano w następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="07903-316">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>  
  
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
##### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="07903-317">Aby ustalić, czy jest wystarczająca ilość fizycznej pamięci</span><span class="sxs-lookup"><span data-stu-id="07903-317">To determine whether there is enough physical memory</span></span>  
  
1.  <span data-ttu-id="07903-318">Uruchom Menedżera zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="07903-318">Start Windows Task Manager.</span></span>  
  
2.  <span data-ttu-id="07903-319">Na **wydajności** pozycję przyjrzeć się wartość zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="07903-319">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="07903-320">(W systemie Windows 7, obejrzyj **zatwierdzić (KB)** w **grupy systemu**.)</span><span class="sxs-lookup"><span data-stu-id="07903-320">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>  
  
     <span data-ttu-id="07903-321">Jeśli **całkowita** jest blisko **Limit**, możesz zaczyna brakować pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="07903-321">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="07903-322">Aby określić, ile pamięci zatwierdza sterty zarządzanej</span><span class="sxs-lookup"><span data-stu-id="07903-322">To determine how much memory the managed heap is committing</span></span>  
  
-   <span data-ttu-id="07903-323">Użyj `# Total committed bytes` licznika wydajności pamięci, aby uzyskać liczbę bajtów, które zatwierdza sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-323">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="07903-324">Moduł zbierający elementy bezużyteczne przekazuje fragmentów w segmencie, zgodnie z potrzebami, nie wszystkie w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="07903-324">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07903-325">Nie używaj `# Bytes in all Heaps` licznika wydajności, ponieważ nie reprezentuje aktualnego stanu użycia pamięci przez sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="07903-325">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="07903-326">Rozmiar generacji znajduje się w tej wartości i jest rzeczywiście jego rozmiar progu, oznacza to, rozmiar, który wywołuje wyrzucania elementów bezużytecznych, jeśli Generowanie jest wypełniony obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-326">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="07903-327">W związku z tym ta wartość jest zazwyczaj zero.</span><span class="sxs-lookup"><span data-stu-id="07903-327">Therefore, this value is usually zero.</span></span>  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="07903-328">Aby określić, ile pamięci rezerwuje sterty zarządzanej</span><span class="sxs-lookup"><span data-stu-id="07903-328">To determine how much memory the managed heap reserves</span></span>  
  
-   <span data-ttu-id="07903-329">Użyj `# Total reserved bytes` licznika wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-329">Use the `# Total reserved bytes` memory performance counter.</span></span>  
  
     <span data-ttu-id="07903-330">Moduł zbierający elementy bezużyteczne zastrzega pamięć w segmentach i można określić, gdzie segment uruchamia się za pomocą **eeheap** polecenia.</span><span class="sxs-lookup"><span data-stu-id="07903-330">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="07903-331">Mimo że możesz określić ilość pamięci przez moduł garbage collector przydziela dla każdego segmentu, rozmiar segmentu jest konkretnej implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="07903-331">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="07903-332">Aplikacji nigdy nie może dokonać założeń dotyczących lub zależą od rozmiaru określonego segmentu nie powinny podejmować próby skonfiguruj ilość pamięci dostępnej dla segmentu alokacji.</span><span class="sxs-lookup"><span data-stu-id="07903-332">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
-   <span data-ttu-id="07903-333">W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="07903-333">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="07903-334">**! eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="07903-334">**!eeheap -gc**</span></span>  
  
     <span data-ttu-id="07903-335">Wynik ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="07903-335">The result is as follows.</span></span>  
  
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
  
     <span data-ttu-id="07903-336">Adresy wskazywanym przez "segmentu" adresów początkowy segmentów.</span><span class="sxs-lookup"><span data-stu-id="07903-336">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="07903-337">W celu ustalenia, duże obiekty generacji 2</span><span class="sxs-lookup"><span data-stu-id="07903-337">To determine large objects in generation 2</span></span>  
  
-   <span data-ttu-id="07903-338">W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="07903-338">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="07903-339">**! dumpheap — stan**</span><span class="sxs-lookup"><span data-stu-id="07903-339">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="07903-340">Jeśli sterty zarządzanej jest duży, **dumpheap** może zająć trochę czasu, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="07903-340">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>  
  
     <span data-ttu-id="07903-341">Analizowanie danych w ciągu ostatnich kilku wierszy danych wyjściowych, można uruchomić, ponieważ ich listy obiektów, które najwięcej miejsca.</span><span class="sxs-lookup"><span data-stu-id="07903-341">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="07903-342">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="07903-342">For example:</span></span>  
  
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
  
     <span data-ttu-id="07903-343">Ostatni obiekt na liście jest ciągiem i zajmuje najwięcej miejsca.</span><span class="sxs-lookup"><span data-stu-id="07903-343">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="07903-344">Można sprawdzić w aplikacji, aby zobaczyć, jak mogą być optymalizowane obiektów w postaci ciągów.</span><span class="sxs-lookup"><span data-stu-id="07903-344">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="07903-345">Aby wyświetlić ciągów, które należą do zakresu od 150 do 200 bajtów, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="07903-345">To see strings that are between 150 and 200 bytes, type the following:</span></span>  
  
     <span data-ttu-id="07903-346">**! dumpheap — wpisz 150 - max -min System.String 200**</span><span class="sxs-lookup"><span data-stu-id="07903-346">**!dumpheap -type System.String -min 150 -max 200**</span></span>  
  
     <span data-ttu-id="07903-347">Przykład wyników ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="07903-347">An example of the results is as follows.</span></span>  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     <span data-ttu-id="07903-348">Może być skuteczniejsza za pomocą całkowitą zamiast ciągu dla Identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="07903-348">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="07903-349">Jeśli ten sam ciąg jest zajdą tysięcy razy, należy wziąć pod uwagę interning ciągu.</span><span class="sxs-lookup"><span data-stu-id="07903-349">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="07903-350">Aby uzyskać więcej informacji na temat interning ciągu, zobacz temat informacje dla <xref:System.String.Intern%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="07903-350">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a><span data-ttu-id="07903-351">Aby określić odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="07903-351">To determine references to objects</span></span>  
  
-   <span data-ttu-id="07903-352">W WinDbg z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie, aby listy odwołania do obiektów:</span><span class="sxs-lookup"><span data-stu-id="07903-352">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>  
  
     <span data-ttu-id="07903-353">**! gcroot**</span><span class="sxs-lookup"><span data-stu-id="07903-353">**!gcroot**</span></span>  
  
     `-or-`  
  
-   <span data-ttu-id="07903-354">Aby określić odwołania dla konkretnego obiektu, należy uwzględnić adres:</span><span class="sxs-lookup"><span data-stu-id="07903-354">To determine the references for a specific object, include the address:</span></span>  
  
     <span data-ttu-id="07903-355">**! gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="07903-355">**!gcroot 1c37b2ac**</span></span>  
  
     <span data-ttu-id="07903-356">Certyfikaty główne na stosy może być fałszywych alarmów.</span><span class="sxs-lookup"><span data-stu-id="07903-356">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="07903-357">Aby uzyskać więcej informacji, użyj polecenia `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="07903-357">For more information, use the command `!help gcroot`.</span></span>  
  
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
  
     <span data-ttu-id="07903-358">**Gcroot** polecenia może zająć dużo czasu, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="07903-358">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="07903-359">Każdy obiekt, który nie jest odzyskana przez odzyskiwanie pamięci jest obiektem na żywo.</span><span class="sxs-lookup"><span data-stu-id="07903-359">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="07903-360">Oznacza to, że niektóre główny jest bezpośrednio lub pośrednio zawierający na obiekt, więc **gcroot** powinny zostać zwrócone informacje ścieżki do obiektu.</span><span class="sxs-lookup"><span data-stu-id="07903-360">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="07903-361">Należy sprawdzić wykresy zwrócił i zobacz, dlaczego te obiekty są nadal odwołuje się do.</span><span class="sxs-lookup"><span data-stu-id="07903-361">You should examine the graphs returned and see why these objects are still referenced.</span></span>  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="07903-362">Aby określić, czy przeprowadzono finalizator</span><span class="sxs-lookup"><span data-stu-id="07903-362">To determine whether a finalizer has been run</span></span>  
  
-   <span data-ttu-id="07903-363">Uruchom program test, który zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="07903-363">Run a test program that contains the following code:</span></span>  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     <span data-ttu-id="07903-364">Jeśli test zostanie rozwiązany, oznacza to, że moduł zbierający elementy bezużyteczne nie został odzyskiwanie obiektów, ponieważ została wstrzymana finalizatory dla tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="07903-364">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="07903-365"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metody umożliwia finalizatory do wykonywania swoich zadań i rozwiązuje problem.</span><span class="sxs-lookup"><span data-stu-id="07903-365">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="07903-366">Aby określić, czy istnieją obiekty oczekujące na sfinalizowana</span><span class="sxs-lookup"><span data-stu-id="07903-366">To determine whether there are objects waiting to be finalized</span></span>  
  
1.  <span data-ttu-id="07903-367">W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="07903-367">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="07903-368">**! finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="07903-368">**!finalizequeue**</span></span>  
  
     <span data-ttu-id="07903-369">Sprawdź liczbę obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="07903-369">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="07903-370">Jeśli liczba jest wysokie, należy zbadać dlaczego te finalizatory nie postępu na wszystkich lub nie postępu szybkiego wystarczająco.</span><span class="sxs-lookup"><span data-stu-id="07903-370">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>  
  
2.  <span data-ttu-id="07903-371">Aby uzyskać dane wyjściowe wątków, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="07903-371">To get an output of threads, type the following command:</span></span>  
  
     <span data-ttu-id="07903-372">**wątki — specjalne**</span><span class="sxs-lookup"><span data-stu-id="07903-372">**threads -special**</span></span>  
  
     <span data-ttu-id="07903-373">To polecenie dostarcza dane wyjściowe podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="07903-373">This command provides output such as the following.</span></span>  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     <span data-ttu-id="07903-374">Wątek finalizatora wskazuje, które finalizator, jeśli istnieje, jest aktualnie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="07903-374">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="07903-375">Kiedy wątku finalizatora nie jest uruchomiona żadnych finalizatory, oczekuje na zdarzenia, aby wykonać swoją pracę.</span><span class="sxs-lookup"><span data-stu-id="07903-375">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="07903-376">W większości przypadków zobaczysz wątku finalizatora w tym stanie ponieważ powinien na zakończenie działania finalizatory, jeśli taki występuje i jest uruchamiane w THREAD_HIGHEST_PRIORITY bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="07903-376">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="07903-377">Aby określić ilość wolnego miejsca na stercie zarządzanej</span><span class="sxs-lookup"><span data-stu-id="07903-377">To determine the amount of free space in the managed heap</span></span>  
  
-   <span data-ttu-id="07903-378">W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="07903-378">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="07903-379">**! dumpheap — wpisz bezpłatne — stan**</span><span class="sxs-lookup"><span data-stu-id="07903-379">**!dumpheap -type Free -stat**</span></span>  
  
     <span data-ttu-id="07903-380">To polecenie wyświetla całkowity rozmiar wszystkich obiektów wolnego na stercie zarządzanej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="07903-380">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   <span data-ttu-id="07903-381">Aby określić ilość wolnego miejsca podczas generowania 0, wpisz następujące polecenie dla informacji o użyciu pamięci przez generowanie:</span><span class="sxs-lookup"><span data-stu-id="07903-381">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>  
  
     <span data-ttu-id="07903-382">**! eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="07903-382">**!eeheap -gc**</span></span>  
  
     <span data-ttu-id="07903-383">To polecenie wyświetla dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="07903-383">This command displays output similar to the following.</span></span> <span data-ttu-id="07903-384">Ostatni wiersz zawiera tymczasowych segmentu.</span><span class="sxs-lookup"><span data-stu-id="07903-384">The last line shows the ephemeral segment.</span></span>  
  
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
  
-   <span data-ttu-id="07903-385">Obliczyć miejsca na dysku używane przez generacji 0:</span><span class="sxs-lookup"><span data-stu-id="07903-385">Calculate the space used by generation 0:</span></span>  
  
     <span data-ttu-id="07903-386">**? 49e05d04 0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="07903-386">**? 49e05d04-0x49521f8c**</span></span>  
  
     <span data-ttu-id="07903-387">Wynik ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="07903-387">The result is as follows.</span></span> <span data-ttu-id="07903-388">Generacji 0 to około 9 MB.</span><span class="sxs-lookup"><span data-stu-id="07903-388">Generation 0 is approximately 9 MB.</span></span>  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   <span data-ttu-id="07903-389">Polecenie zrzuty ilość wolnego miejsca w zakresie generacji 0:</span><span class="sxs-lookup"><span data-stu-id="07903-389">The following command dumps the free space within the generation 0 range:</span></span>  
  
     <span data-ttu-id="07903-390">**! dumpheap-bezpłatne — wpisz 49e05d04 stat 0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="07903-390">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>  
  
     <span data-ttu-id="07903-391">Wynik ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="07903-391">The result is as follows.</span></span>  
  
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
  
     <span data-ttu-id="07903-392">Te dane wyjściowe pokazuje, że część sterty pokolenia 0 za pomocą 9 MB miejsca dla obiektów i ma 7 MB wolnego.</span><span class="sxs-lookup"><span data-stu-id="07903-392">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="07903-393">Analiza wskazuje zakres generacji 0 przyczynia się do fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="07903-393">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="07903-394">Ilość użycia sterty powinien rabatem niż suma jako przyczyna fragmentacji przez obiekty długoterminowej.</span><span class="sxs-lookup"><span data-stu-id="07903-394">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="07903-395">Aby określić liczbę unieruchomionych obiektów</span><span class="sxs-lookup"><span data-stu-id="07903-395">To determine the number of pinned objects</span></span>  
  
-   <span data-ttu-id="07903-396">W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="07903-396">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="07903-397">**! związane**</span><span class="sxs-lookup"><span data-stu-id="07903-397">**!gchandles**</span></span>  
  
     <span data-ttu-id="07903-398">Statystyki, wyświetlane obejmuje liczby dojść przypiętych, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="07903-398">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="07903-399">Aby określić czas w wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="07903-399">To determine the length of time in a garbage collection</span></span>  
  
-   <span data-ttu-id="07903-400">Sprawdź `% Time in GC` licznika wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="07903-400">Examine the `% Time in GC` memory performance counter.</span></span>  
  
     <span data-ttu-id="07903-401">Wartość jest obliczana przy użyciu interwałów próbkowania.</span><span class="sxs-lookup"><span data-stu-id="07903-401">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="07903-402">Ponieważ liczniki jest aktualizowany po zakończeniu każdej operacji wyrzucania elementów bezużytecznych, bieżący próbki ma taką samą wartość jak poprzedni przykład, jeśli żadne kolekcje wystąpił w interwale.</span><span class="sxs-lookup"><span data-stu-id="07903-402">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>  
  
     <span data-ttu-id="07903-403">Czas zbierania mnożąc interwałów próbkowania o wartości procentowej.</span><span class="sxs-lookup"><span data-stu-id="07903-403">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>  
  
     <span data-ttu-id="07903-404">Następujące dane zawiera cztery interwałami próbkowania dwóch sekund, badanie 8 sekundy.</span><span class="sxs-lookup"><span data-stu-id="07903-404">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="07903-405">`Gen0`, `Gen1`, I `Gen2` kolumny zawierają liczbę wyrzucania, które wystąpiły podczas tego interwału dla tej generacji.</span><span class="sxs-lookup"><span data-stu-id="07903-405">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     <span data-ttu-id="07903-406">Te informacje nie są wyświetlane, gdy wystąpił wyrzucanie elementów bezużytecznych, ale można określić liczbę wyrzucania, które wystąpiły w odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="07903-406">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="07903-407">Zakładając, że najgorszego, dziesiątego bezużytecznych generacji 0 zakończono na początku Drugi interwał i jedenastego bezużytecznych generacji 0 zakończono na końcu piątej interwału.</span><span class="sxs-lookup"><span data-stu-id="07903-407">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="07903-408">Czas między koniec dziesiątego i na końcu jedenastego wyrzucanie elementów bezużytecznych jest około 2 sekundy, i licznik wydajności przedstawia 3%, więc trwało jedenastego wyrzucanie elementów bezużytecznych generacji 0 (% s 2 * 3 = 60ms).</span><span class="sxs-lookup"><span data-stu-id="07903-408">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds * 3% = 60ms).</span></span>  
  
     <span data-ttu-id="07903-409">W tym przykładzie są 5 okresów.</span><span class="sxs-lookup"><span data-stu-id="07903-409">In this example, there are 5 periods.</span></span>  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     <span data-ttu-id="07903-410">Drugiej generacji 2 wyrzucanie elementów bezużytecznych rozpoczęcia interwale trzeci i zakończenia w piątym odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="07903-410">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="07903-411">Zakładając, że najgorszego, ostatni wyrzucanie elementów bezużytecznych był zakończenia na początku Drugi interwał kolekcji generacji 0, a generacji 2 wyrzucanie elementów bezużytecznych Zakończono na końcu piątej interwał.</span><span class="sxs-lookup"><span data-stu-id="07903-411">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="07903-412">W związku z tym czas od zakończenia operacji wyrzucania elementów bezużytecznych generacji 0 i na końcu wyrzucanie elementów bezużytecznych generacji 2 jest 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="07903-412">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="07903-413">Ponieważ `% Time in GC` licznika wynosi 20%, maksymalną ilość czasu generowania można miały 2 wyrzucanie elementów bezużytecznych (4 sekundy * 20% = 800ms).</span><span class="sxs-lookup"><span data-stu-id="07903-413">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds * 20% = 800ms).</span></span>  
  
-   <span data-ttu-id="07903-414">Alternatywnie można określić długości wyrzucania elementów bezużytecznych przy użyciu [zdarzenia ETW wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md)i analizowania informacji, aby określić czas trwania operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-414">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>  
  
     <span data-ttu-id="07903-415">Na przykład następujące dane przedstawiono sekwencję zdarzeń, który wystąpił podczas niewspółbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-415">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>  
  
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
  
     <span data-ttu-id="07903-416">Zawieszanie wątków zarządzanych trwało 26us (`GCSuspendEEEnd` — `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="07903-416">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>  
  
     <span data-ttu-id="07903-417">Rzeczywiste wyrzucanie elementów bezużytecznych trwało 4.8ms (`GCEnd_V1` — `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="07903-417">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>  
  
     <span data-ttu-id="07903-418">Wznawianie wątków zarządzanych trwało 21us (`GCRestartEEEnd` — `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="07903-418">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>  
  
     <span data-ttu-id="07903-419">Następujące dane wyjściowe zawiera przykład odzyskiwanie pamięci w tle, a obejmują procesu, wątku i pola zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="07903-419">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="07903-420">(Nie wszystkie dane są wyświetlane).</span><span class="sxs-lookup"><span data-stu-id="07903-420">(Not all data is shown.)</span></span>  
  
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
  
     <span data-ttu-id="07903-421">`GCStart_V1` Zdarzenia przy 42504816 wskazuje, że jest Odzyskiwanie pamięci w tle, ponieważ ostatnie pole `1`.</span><span class="sxs-lookup"><span data-stu-id="07903-421">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="07903-422">Staje się on wyrzucanie elementów bezużytecznych przycisk nie.</span><span class="sxs-lookup"><span data-stu-id="07903-422">This becomes garbage collection No.</span></span> <span data-ttu-id="07903-423">102019.</span><span class="sxs-lookup"><span data-stu-id="07903-423">102019.</span></span>  
  
     <span data-ttu-id="07903-424">`GCStart` Wystąpi zdarzenie, ponieważ nie istnieje potrzeba tymczasowych wyrzucanie elementów bezużytecznych przed rozpoczęciem odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="07903-424">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="07903-425">Staje się on wyrzucanie elementów bezużytecznych przycisk nie.</span><span class="sxs-lookup"><span data-stu-id="07903-425">This becomes garbage collection No.</span></span> <span data-ttu-id="07903-426">102020.</span><span class="sxs-lookup"><span data-stu-id="07903-426">102020.</span></span>  
  
     <span data-ttu-id="07903-427">W 42514170, wyrzucanie elementów bezużytecznych nie.</span><span class="sxs-lookup"><span data-stu-id="07903-427">At 42514170, garbage collection No.</span></span> <span data-ttu-id="07903-428">Zakończenie 102020.</span><span class="sxs-lookup"><span data-stu-id="07903-428">102020 finishes.</span></span> <span data-ttu-id="07903-429">Zarządzane wątki są ponownie uruchamiane w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="07903-429">The managed threads are restarted at this point.</span></span> <span data-ttu-id="07903-430">To pole jest wypełniane w wątku 4372, która wywołała to odzyskiwanie pamięci w tle.</span><span class="sxs-lookup"><span data-stu-id="07903-430">This is completed on thread 4372, which triggered this background garbage collection.</span></span>  
  
     <span data-ttu-id="07903-431">W wątku 4744 zawieszenia występuje.</span><span class="sxs-lookup"><span data-stu-id="07903-431">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="07903-432">Jest to tylko czas, w którym odzyskiwanie pamięci w tle musi wstrzymać wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="07903-432">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="07903-433">Ten czas trwania to około 99ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="07903-433">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>  
  
     <span data-ttu-id="07903-434">`GCEnd` Jest zdarzenie dla tła wyrzucanie elementów bezużytecznych w 89931423.</span><span class="sxs-lookup"><span data-stu-id="07903-434">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="07903-435">Oznacza to, że tło wyrzucanie elementów bezużytecznych trwała o 47seconds ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="07903-435">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>  
  
     <span data-ttu-id="07903-436">Uruchomionej zarządzane wątki widać dowolną liczbę tymczasowych wyrzucania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="07903-436">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="07903-437">Aby określić, co wyzwoliło wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="07903-437">To determine what triggered a garbage collection</span></span>  
  
-   <span data-ttu-id="07903-438">W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie, aby wyświetlić wszystkie wątki z ich stosy wywołań:</span><span class="sxs-lookup"><span data-stu-id="07903-438">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>  
  
     <span data-ttu-id="07903-439">**~\*KB**</span><span class="sxs-lookup"><span data-stu-id="07903-439">**~\*kb**</span></span>  
  
     <span data-ttu-id="07903-440">To polecenie wyświetla dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="07903-440">This command displays output similar to the following.</span></span>  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     <span data-ttu-id="07903-441">Wyrzucanie elementów bezużytecznych spowodowane przez powiadomienie o małej ilości pamięci systemu operacyjnego, stos wywołań jest podobny, z wyjątkiem tego, że wątek znajduje się wątek finalizatora.</span><span class="sxs-lookup"><span data-stu-id="07903-441">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="07903-442">Wątek finalizatora pobiera wiadomość z powiadomieniem asynchroniczne małej ilości pamięci i wywołuje wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-442">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>  
  
     <span data-ttu-id="07903-443">Jeśli wyrzucanie elementów bezużytecznych spowodowane przez alokacji pamięci stosu wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="07903-443">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>  
  
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
  
     <span data-ttu-id="07903-444">Pomocnik just in time (`JIT_New*`) wywołuje na końcu `GCHeap::GarbageCollectGeneration`.</span><span class="sxs-lookup"><span data-stu-id="07903-444">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="07903-445">Jeśli okaże się wyrzucania generacji 2 są spowodowane alokacji, należy określić obiekty, które mają być zbierane przez generacji 2 wyrzucania elementów bezużytecznych i sposobu ich uniknięcie.</span><span class="sxs-lookup"><span data-stu-id="07903-445">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="07903-446">Oznacza to, że chcesz obliczenia różnicy między początkową i końcową generacji 2 wyrzucania elementów bezużytecznych i obiekty, które spowodowało kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="07903-446">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>  
  
     <span data-ttu-id="07903-447">Na przykład wpisz następujące polecenie w debugerze umożliwiające wyświetlanie na początku kolekcji generacji 2:</span><span class="sxs-lookup"><span data-stu-id="07903-447">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>  
  
     <span data-ttu-id="07903-448">**! dumpheap — stan**</span><span class="sxs-lookup"><span data-stu-id="07903-448">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="07903-449">Przykład danych wyjściowych (skróconej informacji wyświetlenie obiektów, które używają najwięcej miejsca):</span><span class="sxs-lookup"><span data-stu-id="07903-449">Example output (abridged to show the objects that use the most space):</span></span>  
  
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
  
     <span data-ttu-id="07903-450">Powtórz polecenie na końcu generacji 2:</span><span class="sxs-lookup"><span data-stu-id="07903-450">Repeat the command at the end of generation 2:</span></span>  
  
     <span data-ttu-id="07903-451">**! dumpheap — stan**</span><span class="sxs-lookup"><span data-stu-id="07903-451">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="07903-452">Przykład danych wyjściowych (skróconej informacji wyświetlenie obiektów, które używają najwięcej miejsca):</span><span class="sxs-lookup"><span data-stu-id="07903-452">Example output (abridged to show the objects that use the most space):</span></span>  
  
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
  
     <span data-ttu-id="07903-453">`double[]` Obiektów zniknęła na końcu danych wyjściowych, co oznacza, że zostały zebrane.</span><span class="sxs-lookup"><span data-stu-id="07903-453">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="07903-454">Obiekty te konta do około 70 MB.</span><span class="sxs-lookup"><span data-stu-id="07903-454">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="07903-455">Pozostałe obiekty nie został zmieniony znacznie.</span><span class="sxs-lookup"><span data-stu-id="07903-455">The remaining objects did not change much.</span></span> <span data-ttu-id="07903-456">W związku z tym te `double[]` obiekty zostały Przyczyna przyczynę wystąpienia tej generacji 2 wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07903-456">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="07903-457">Następnym krokiem jest ustalenie, dlaczego `double[]` obiekty są dostępne i dlaczego ich zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="07903-457">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="07903-458">Można skontaktuj się z deweloperem kodu, w którym pochodzeniu tych obiektów, lub skorzystać z **gcroot** polecenia.</span><span class="sxs-lookup"><span data-stu-id="07903-458">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="07903-459">Aby określić, czy przyczyną wysokiego użycia procesora CPU jest wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="07903-459">To determine whether high CPU usage is caused by garbage collection</span></span>  
  
-   <span data-ttu-id="07903-460">Korelowanie `% Time in GC` wartość licznika wydajności pamięci w czasie procesu.</span><span class="sxs-lookup"><span data-stu-id="07903-460">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>  
  
     <span data-ttu-id="07903-461">Jeśli `% Time in GC` wartość wzrósł w tym samym czasie jako czas przetwarzania, wyrzucanie elementów bezużytecznych jest przyczyną wysokiego użycia procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="07903-461">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="07903-462">W przeciwnym razie profilu aplikacji można znaleźć, gdzie występuje wysokiego użycia.</span><span class="sxs-lookup"><span data-stu-id="07903-462">Otherwise, profile the application to find where the high usage is occurring.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07903-463">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07903-463">See Also</span></span>  
 [<span data-ttu-id="07903-464">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="07903-464">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
