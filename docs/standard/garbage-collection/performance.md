---
title: Odzyskiwanie pamięci i wydajność
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 72cf742aae26f9441229b355dc6e70da7a5fc9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75900582"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="97652-102">Odzyskiwanie pamięci i wydajność</span><span class="sxs-lookup"><span data-stu-id="97652-102">Garbage Collection and Performance</span></span>

<span data-ttu-id="97652-103">W tym temacie opisano problemy związane z wyrzucaniem elementów bezużytecznych i użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="97652-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="97652-104">Rozwiązuje problemy, które odnoszą się do zarządzanego sterty i wyjaśnia, jak zminimalizować wpływ wyrzucania elementów bezużytecznych na aplikacje.</span><span class="sxs-lookup"><span data-stu-id="97652-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="97652-105">Każdy problem ma łącza do procedur, których można użyć do zbadania problemów.</span><span class="sxs-lookup"><span data-stu-id="97652-105">Each issue has links to procedures that you can use to investigate problems.</span></span>

## <a name="performance-analysis-tools"></a><span data-ttu-id="97652-106">Narzędzia do analizy wydajności</span><span class="sxs-lookup"><span data-stu-id="97652-106">Performance Analysis Tools</span></span>

<span data-ttu-id="97652-107">W poniższych sekcjach opisano narzędzia, które są dostępne do badania użycia pamięci i problemów z wyrzucaniem elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-107">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="97652-108">[Procedury](#performance-check-procedures) przedstawione w dalszej części tego tematu odnoszą się do tych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="97652-108">The [procedures](#performance-check-procedures) provided later in this topic refer to these tools.</span></span>

### <a name="memory-performance-counters"></a><span data-ttu-id="97652-109">Liczniki wydajności pamięci</span><span class="sxs-lookup"><span data-stu-id="97652-109">Memory Performance Counters</span></span>

<span data-ttu-id="97652-110">Liczniki wydajności służy do zbierania danych wydajności.</span><span class="sxs-lookup"><span data-stu-id="97652-110">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="97652-111">Aby uzyskać instrukcje, zobacz [Profilowanie w czasie wykonywania](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="97652-111">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="97652-112">Kategoria pamięci CLR .NET liczników wydajności, zgodnie z opisem w [licznikach wydajności w ramach .NET Framework,](../../../docs/framework/debug-trace-profile/performance-counters.md)zawiera informacje o modułodarze pamięci.</span><span class="sxs-lookup"><span data-stu-id="97652-112">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

### <a name="debugging-with-sos"></a><span data-ttu-id="97652-113">Debugowanie za pomocą SOS</span><span class="sxs-lookup"><span data-stu-id="97652-113">Debugging with SOS</span></span>

<span data-ttu-id="97652-114">Za pomocą [debugera systemu Windows (WinDbg)](/windows-hardware/drivers/debugger/index) można sprawdzić obiekty na zarządzanym stercie.</span><span class="sxs-lookup"><span data-stu-id="97652-114">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="97652-115">Aby zainstalować usługę WinDbg, zainstaluj narzędzia debugowania dla systemu Windows ze strony Narzędzia do [pobierania debugowania dla systemu Windows.](/windows-hardware/drivers/debugger/debugger-download-tools)</span><span class="sxs-lookup"><span data-stu-id="97652-115">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="97652-116">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="97652-116">Garbage Collection ETW Events</span></span>

<span data-ttu-id="97652-117">Śledzenie zdarzeń dla systemu Windows (ETW) jest systemem śledzenia, który uzupełnia profilowanie i debugowanie pomocy technicznej świadczonej przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97652-117">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="97652-118">Począwszy od .NET Framework 4, [wyrzucanie elementów bezużytecznych zdarzenia ETW](../../../docs/framework/performance/garbage-collection-etw-events.md) przechwytywania przydatnych informacji do analizowania sterty zarządzanej z statystycznego punktu widzenia.</span><span class="sxs-lookup"><span data-stu-id="97652-118">Starting with the .NET Framework 4, [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="97652-119">Na przykład `GCStart_V1` zdarzenie, które jest wywoływane, gdy wyrzucanie elementów bezużytecznych ma wystąpić, zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="97652-119">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="97652-120">Która generacja obiektów jest zbierana.</span><span class="sxs-lookup"><span data-stu-id="97652-120">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="97652-121">Co wyzwoliło wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-121">What triggered the garbage collection.</span></span>

- <span data-ttu-id="97652-122">Typ wyrzucania elementów bezużytecznych (równoczesny lub niewspółbieżny).</span><span class="sxs-lookup"><span data-stu-id="97652-122">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="97652-123">Rejestrowanie zdarzeń ETW jest efektywne i nie będzie maskować żadnych problemów z wydajnością związanych z wyrzucaniem elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-123">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="97652-124">Proces może dostarczyć własne zdarzenia w połączeniu ze zdarzeniami ETW.</span><span class="sxs-lookup"><span data-stu-id="97652-124">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="97652-125">Po zalogowaniu zarówno zdarzenia aplikacji, jak i zdarzenia wyrzucania elementów bezużytecznych mogą być skorelowane, aby określić, jak i kiedy występują problemy ze stertami.</span><span class="sxs-lookup"><span data-stu-id="97652-125">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="97652-126">Na przykład aplikacja serwera może zapewnić zdarzenia na początku i na końcu żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="97652-126">For example, a server application could provide events at the start and end of a client request.</span></span>

### <a name="the-profiling-api"></a><span data-ttu-id="97652-127">Interfejs API profilowania</span><span class="sxs-lookup"><span data-stu-id="97652-127">The Profiling API</span></span>

<span data-ttu-id="97652-128">Interfejsy profilowania języka wspólnego (CLR) zawierają szczegółowe informacje o obiektach, których dotyczy problem podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-128">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="97652-129">Profiler może być powiadamiany, gdy wyrzucanie elementów bezużytecznych rozpoczyna się i kończy.</span><span class="sxs-lookup"><span data-stu-id="97652-129">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="97652-130">Może dostarczać raporty dotyczące obiektów na zarządzanym stercie, w tym identyfikację obiektów w każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="97652-130">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="97652-131">Aby uzyskać więcej informacji, zobacz [Omówienie profilowania](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="97652-131">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="97652-132">Profilerzy mogą dostarczyć wyczerpujących informacji.</span><span class="sxs-lookup"><span data-stu-id="97652-132">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="97652-133">Jednak złożone profilery mogą potencjalnie modyfikować zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="97652-133">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="97652-134">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="97652-134">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="97652-135">Począwszy od .NET Framework 4, Monitorowanie zasobów domeny aplikacji (ARM) umożliwia hostom monitorowanie użycia procesora CPU i pamięci według domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="97652-135">Starting with the .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="97652-136">Aby uzyskać więcej informacji, zobacz [Monitorowanie zasobów domeny aplikacji](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="97652-136">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="97652-137">Rozwiązywanie problemów z wydajnością</span><span class="sxs-lookup"><span data-stu-id="97652-137">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="97652-138">Pierwszym krokiem jest [ustalenie, czy problem jest rzeczywiście wyrzucania elementów bezużytecznych](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="97652-138">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="97652-139">Jeśli okaże się, że jest, wybierz z poniższej listy, aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="97652-139">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="97652-140">Wyjątek poza pamięcią jest generowany</span><span class="sxs-lookup"><span data-stu-id="97652-140">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="97652-141">Proces zużywa zbyt dużo pamięci</span><span class="sxs-lookup"><span data-stu-id="97652-141">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="97652-142">Moduł zbierający elementy bezużyteczne nie odzyskuje obiektów wystarczająco szybko</span><span class="sxs-lookup"><span data-stu-id="97652-142">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="97652-143">Zarządzana sterta jest zbyt rozdrobniona</span><span class="sxs-lookup"><span data-stu-id="97652-143">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="97652-144">Przerwy w wyrzucaniu elementów bezużytecznych są zbyt długie</span><span class="sxs-lookup"><span data-stu-id="97652-144">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="97652-145">Generacja 0 jest zbyt duża</span><span class="sxs-lookup"><span data-stu-id="97652-145">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="97652-146">Użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt wysokie</span><span class="sxs-lookup"><span data-stu-id="97652-146">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="97652-147">Problem: Wyjątek braku pamięci jest generowany</span><span class="sxs-lookup"><span data-stu-id="97652-147">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="97652-148">Istnieją dwa uzasadnione przypadki, <xref:System.OutOfMemoryException> w których udało się wywalić:</span><span class="sxs-lookup"><span data-stu-id="97652-148">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="97652-149">Zabraknie pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="97652-149">Running out of virtual memory.</span></span>

  <span data-ttu-id="97652-150">Moduł zbierający elementy bezużyteczne przydziela pamięć z systemu w segmentach o wstępnie określonym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="97652-150">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="97652-151">Jeśli alokacja wymaga dodatkowego segmentu, ale w przestrzeni pamięci wirtualnej procesu nie ma ciągłego wolnego bloku, alokacja zarządzanego stosu zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="97652-151">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="97652-152">Nie mając wystarczającej ilości pamięci fizycznej do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="97652-152">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="97652-153">Kontrole wydajności</span><span class="sxs-lookup"><span data-stu-id="97652-153">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="97652-154">Określ, czy wyjątek braku pamięci jest zarządzany.</span><span class="sxs-lookup"><span data-stu-id="97652-154">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="97652-155">Określ, ile pamięci wirtualnej można zarezerwować.</span><span class="sxs-lookup"><span data-stu-id="97652-155">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="97652-156">Określ, czy jest wystarczająca ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="97652-156">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="97652-157">Jeśli ustalisz, że wyjątek nie jest zgodny z prawem, skontaktuj się z działem obsługi klienta i pomocy technicznej firmy Microsoft, aby uzyskać następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="97652-157">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="97652-158">Stos z zarządzanym wyjątkiem braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="97652-158">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="97652-159">Zrzut pełnej pamięci.</span><span class="sxs-lookup"><span data-stu-id="97652-159">Full memory dump.</span></span>

- <span data-ttu-id="97652-160">Dane, które udowadniają, że nie jest to uzasadniony wyjątek braku pamięci, w tym dane, które pokazują, że pamięć wirtualna lub fizyczna nie jest problemem.</span><span class="sxs-lookup"><span data-stu-id="97652-160">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="97652-161">Problem: Proces zużywa zbyt dużo pamięci</span><span class="sxs-lookup"><span data-stu-id="97652-161">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="97652-162">Typowym założeniem jest, że wyświetlanie użycia pamięci na karcie **Wydajność** Menedżera zadań systemu Windows może wskazywać, kiedy jest używana zbyt dużo pamięci.</span><span class="sxs-lookup"><span data-stu-id="97652-162">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="97652-163">Jednak ten wyświetlacz odnosi się do zestawu roboczego; nie dostarcza informacji o wykorzystaniu pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="97652-163">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="97652-164">Jeśli stwierdzisz, że problem jest spowodowany przez zarządzane sterty, należy zmierzyć zarządzane sterty w czasie, aby określić wszelkie wzorce.</span><span class="sxs-lookup"><span data-stu-id="97652-164">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="97652-165">Jeśli stwierdzisz, że problem nie jest spowodowany przez zarządzane sterty, należy użyć debugowania macierzystego.</span><span class="sxs-lookup"><span data-stu-id="97652-165">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="97652-166">Kontrole wydajności</span><span class="sxs-lookup"><span data-stu-id="97652-166">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="97652-167">Określ, ile pamięci wirtualnej można zarezerwować.</span><span class="sxs-lookup"><span data-stu-id="97652-167">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="97652-168">Określ, ile pamięci zatwierdza zarządzana sterta.</span><span class="sxs-lookup"><span data-stu-id="97652-168">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="97652-169">Określ, ile pamięci rezerwuje zarządzany stos.</span><span class="sxs-lookup"><span data-stu-id="97652-169">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="97652-170">Określ duże obiekty w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="97652-170">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="97652-171">Określ odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="97652-171">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="97652-172">Problem: Moduł zbierający elementy bezużyteczne nie odzyskuje wystarczająco szybko obiektów</span><span class="sxs-lookup"><span data-stu-id="97652-172">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="97652-173">Gdy wydaje się, że obiekty nie są odzyskiwane zgodnie z oczekiwaniami dla wyrzucania elementów bezużytecznych, należy określić, czy istnieją silne odwołania do tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="97652-173">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="97652-174">Ten problem może również wystąpić, jeśli nie było wyrzucania elementów bezużytecznych dla generacji, która zawiera martwy obiekt, co oznacza, że finalizator dla martwego obiektu nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="97652-174">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="97652-175">Na przykład jest to możliwe, gdy używasz aplikacji jednowątkowego mieszkania (STA) i wątku, który usług kolejki finalizatora nie można wywołać do niego.</span><span class="sxs-lookup"><span data-stu-id="97652-175">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="97652-176">Kontrole wydajności</span><span class="sxs-lookup"><span data-stu-id="97652-176">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="97652-177">Sprawdź odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="97652-177">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="97652-178">Określ, czy finalizator został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="97652-178">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="97652-179">Określ, czy istnieją obiekty oczekujące na sfinalizowanie.</span><span class="sxs-lookup"><span data-stu-id="97652-179">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="97652-180">Problem: Sterta zarządzana jest zbyt rozdrobniona</span><span class="sxs-lookup"><span data-stu-id="97652-180">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="97652-181">Poziom fragmentacji jest obliczany jako stosunek wolnego miejsca do całkowitej przydzielonej pamięci dla generacji.</span><span class="sxs-lookup"><span data-stu-id="97652-181">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="97652-182">W przypadku generacji 2 dopuszczalny poziom fragmentacji wynosi nie więcej niż 20%.</span><span class="sxs-lookup"><span data-stu-id="97652-182">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="97652-183">Ponieważ generacja 2 może być bardzo duża, stosunek fragmentacji jest ważniejszy niż wartość bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="97652-183">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="97652-184">Posiadanie dużej ilości wolnego miejsca w generacji 0 nie stanowi problemu, ponieważ jest to generacja, w której przydzielane są nowe obiekty.</span><span class="sxs-lookup"><span data-stu-id="97652-184">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="97652-185">Fragmentacja zawsze występuje w stercie dużych obiektów, ponieważ nie jest skompaktowany.</span><span class="sxs-lookup"><span data-stu-id="97652-185">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="97652-186">Wolne obiekty, które sąsiadują są naturalnie zwinięte w jednym miejscu, aby zaspokoić żądania alokacji dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="97652-186">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="97652-187">Fragmentacja może stać się problemem w generacji 1 i generacji 2.</span><span class="sxs-lookup"><span data-stu-id="97652-187">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="97652-188">Jeśli te generacje mają dużą ilość wolnego miejsca po wyrzucania elementów bezużytecznych, użycie obiektu aplikacji może wymagać modyfikacji i należy rozważyć ponownej oceny okresu istnienia obiektów długoterminowych.</span><span class="sxs-lookup"><span data-stu-id="97652-188">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="97652-189">Nadmierne przypinanie obiektów może zwiększyć fragmentację.</span><span class="sxs-lookup"><span data-stu-id="97652-189">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="97652-190">Jeśli fragmentacja jest wysoka, zbyt wiele obiektów można było przypiąć.</span><span class="sxs-lookup"><span data-stu-id="97652-190">If fragmentation is high, too many objects could have been pinned.</span></span>

<span data-ttu-id="97652-191">Jeśli fragmentacja pamięci wirtualnej uniemożliwia modułowi odśmiecania pamięci dodawanie segmentów, przyczyny mogą być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="97652-191">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="97652-192">Częste załadunek i rozładunek wielu małych zespołów.</span><span class="sxs-lookup"><span data-stu-id="97652-192">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="97652-193">Przechowywanie zbyt wielu odwołań do obiektów COM podczas współdziałania z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="97652-193">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="97652-194">Tworzenie dużych obiektów przejściowych, co powoduje, że sterty dużych obiektów do przydzielenia i wolne segmenty sterty często.</span><span class="sxs-lookup"><span data-stu-id="97652-194">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="97652-195">Podczas hostowania CLR, aplikacja może zażądać, aby moduł zbierający elementy bezużyteczne zachował swoje segmenty.</span><span class="sxs-lookup"><span data-stu-id="97652-195">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="97652-196">Zmniejsza to częstotliwość alokacji segmentów.</span><span class="sxs-lookup"><span data-stu-id="97652-196">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="97652-197">Jest to realizowane przy użyciu flagi STARTUP_HOARD_GC_VM w [wyliczeniu STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="97652-197">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="97652-198">Kontrole wydajności</span><span class="sxs-lookup"><span data-stu-id="97652-198">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="97652-199">Określ ilość wolnego miejsca w zarządzanym stercie.</span><span class="sxs-lookup"><span data-stu-id="97652-199">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="97652-200">Określ liczbę przypiętych obiektów.</span><span class="sxs-lookup"><span data-stu-id="97652-200">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="97652-201">Jeśli uważasz, że nie ma uzasadnionej przyczyny fragmentacji, skontaktuj się z działem obsługi klienta i pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="97652-201">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="97652-202">Problem: Przerwy w wyrzucaniu elementów bezużytecznych są zbyt długie</span><span class="sxs-lookup"><span data-stu-id="97652-202">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="97652-203">Wyrzucanie elementów bezużytecznych działa w miękkim czasie rzeczywistym, więc aplikacja musi być w stanie tolerować niektóre przerwy.</span><span class="sxs-lookup"><span data-stu-id="97652-203">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="97652-204">Kryterium dla miękkiego czasu rzeczywistego jest to, że 95% operacji musi zakończyć się na czas.</span><span class="sxs-lookup"><span data-stu-id="97652-204">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="97652-205">W równoczesnych wyrzucania elementów bezużytecznych zarządzanych wątków mogą być uruchamiane podczas zbierania, co oznacza, że pauzy są bardzo minimalne.</span><span class="sxs-lookup"><span data-stu-id="97652-205">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="97652-206">Efemericzne wyrzucania elementów bezużytecznych (generacje 0 i 1) trwają tylko kilka milisekund, więc zmniejszanie pauz zwykle nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="97652-206">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="97652-207">Jednak można zmniejszyć pauzy w kolekcji generacji 2, zmieniając wzorzec żądań alokacji przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="97652-207">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="97652-208">Inną, dokładniejsza, metoda jest użycie [wyrzucania elementów bezużytecznych ETW zdarzeń](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="97652-208">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="97652-209">Chronometraż kolekcji można znaleźć, dodając różnice sygnatury czasowej dla sekwencji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="97652-209">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="97652-210">Cała sekwencja kolekcji zawiera zawieszenie aparatu wykonywania, samego wyrzucania elementów bezużytecznych i wznowienie aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="97652-210">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="97652-211">Za pomocą [powiadomień o wyrzucaniu elementów bezużytecznych](../../../docs/standard/garbage-collection/notifications.md) można określić, czy serwer ma mieć kolekcję 2 generacji i czy przekierowanie żądań do innego serwera może ułatwić wszelkie problemy z przerwami.</span><span class="sxs-lookup"><span data-stu-id="97652-211">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="97652-212">Kontrole wydajności</span><span class="sxs-lookup"><span data-stu-id="97652-212">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="97652-213">Określ czas w wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-213">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="97652-214">Określ, co spowodowało wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-214">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="97652-215">Problem: Generacja 0 jest zbyt duża</span><span class="sxs-lookup"><span data-stu-id="97652-215">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="97652-216">Generacja 0 może mieć większą liczbę obiektów w systemie 64-bitowym, szczególnie w przypadku korzystania z wyrzucania elementów bezużytecznych serwera zamiast wyrzucania elementów bezużytecznych stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="97652-216">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="97652-217">Jest tak, ponieważ próg wyzwalania generacji 0 wyrzucania elementów bezużytecznych jest wyższa w tych środowiskach, a kolekcji generacji 0 można uzyskać znacznie większe.</span><span class="sxs-lookup"><span data-stu-id="97652-217">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="97652-218">Wydajność jest zwiększona, gdy aplikacja przydziela więcej pamięci przed wyzwoleniewyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-218">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="97652-219">Problem: Użycie procesora PODCZAS wyrzucania elementów bezużytecznych jest zbyt wysokie</span><span class="sxs-lookup"><span data-stu-id="97652-219">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="97652-220">Użycie procesora CPU będzie wysokie podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-220">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="97652-221">Jeśli znaczna ilość czasu procesu jest spędzana w wyrzucania elementów bezużytecznych, liczba kolekcji jest zbyt częste lub kolekcji trwa zbyt długo.</span><span class="sxs-lookup"><span data-stu-id="97652-221">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="97652-222">Zwiększony wskaźnik alokacji obiektów na zarządzanym stercie powoduje, że wyrzucanie elementów bezużytecznych występuje częściej.</span><span class="sxs-lookup"><span data-stu-id="97652-222">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="97652-223">Zmniejszenie szybkości alokacji zmniejsza częstotliwość wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-223">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="97652-224">Stawki alokacji można `Allocated Bytes/second` monitorować przy użyciu licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="97652-224">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="97652-225">Aby uzyskać więcej informacji, zobacz [liczniki wydajności w platformie .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="97652-225">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="97652-226">Czas trwania kolekcji jest przede wszystkim czynnikiem liczby obiektów, które przetrwać po alokacji.</span><span class="sxs-lookup"><span data-stu-id="97652-226">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="97652-227">Moduł zbierający elementy bezużyteczne musi przejść przez dużą ilość pamięci, jeśli wiele obiektów pozostaje do zebrania.</span><span class="sxs-lookup"><span data-stu-id="97652-227">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="97652-228">Praca nad zagęszczeniem ocalałych jest czasochłonna.</span><span class="sxs-lookup"><span data-stu-id="97652-228">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="97652-229">Aby określić, ile obiektów zostały obsłużone podczas zbierania, ustaw punkt przerwania w debugerze na końcu wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="97652-229">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="97652-230">Kontrole wydajności</span><span class="sxs-lookup"><span data-stu-id="97652-230">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="97652-231">Określ, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-231">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="97652-232">Ustaw punkt przerwania na końcu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-232">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="97652-233">Wskazówki dotyczące rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="97652-233">Troubleshooting Guidelines</span></span>

<span data-ttu-id="97652-234">W tej sekcji opisano wskazówki, które należy wziąć pod uwagę podczas rozpoczynania dochodzenia.</span><span class="sxs-lookup"><span data-stu-id="97652-234">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="97652-235">Stacja robocza lub wyrzucanie elementów bezużytecznych serwera</span><span class="sxs-lookup"><span data-stu-id="97652-235">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="97652-236">Określ, czy używasz poprawnego typu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-236">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="97652-237">Jeśli aplikacja używa wielu wątków i wystąpień obiektów, należy użyć wyrzucania elementów bezużytecznych serwera zamiast wyrzucania elementów bezużytecznych stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="97652-237">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="97652-238">Wyrzucanie elementów bezużytecznych serwera działa na wiele wątków, podczas gdy wyrzucanie elementów bezużytecznych stacji roboczej wymaga wielu wystąpień aplikacji do uruchamiania własnych wątków wyrzucania elementów bezużytecznych i konkurowania o czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="97652-238">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="97652-239">Aplikacja, która ma niskie obciążenie i która wykonuje zadania rzadko w tle, takich jak usługa, można użyć wyrzucania elementów bezużytecznych stacji roboczej z równoczesnych wyrzucania elementów bezużytecznych wyłączone.</span><span class="sxs-lookup"><span data-stu-id="97652-239">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="97652-240">Kiedy mierzyć rozmiar zarządzanej sterty</span><span class="sxs-lookup"><span data-stu-id="97652-240">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="97652-241">Chyba że używasz profilera, trzeba będzie ustalić spójny wzór pomiaru, aby skutecznie diagnozować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="97652-241">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="97652-242">Należy wziąć pod uwagę następujące punkty, aby ustanowić harmonogram:</span><span class="sxs-lookup"><span data-stu-id="97652-242">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="97652-243">Jeśli zmierzysz po generacji 2 wyrzucania elementów bezużytecznych, cały zarządzany sterty będzie wolny od śmieci (martwe obiekty).</span><span class="sxs-lookup"><span data-stu-id="97652-243">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="97652-244">Jeśli zmierzysz natychmiast po generacji 0 wyrzucania elementów bezużytecznych, obiekty w generacji 1 i 2 nie będą jeszcze zbierane.</span><span class="sxs-lookup"><span data-stu-id="97652-244">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="97652-245">Jeśli zmierzysz bezpośrednio przed wyrzucania elementów bezużytecznych, będzie zmierzyć jak najwięcej alokacji, jak to możliwe przed rozpoczęciem wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-245">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="97652-246">Pomiar podczas wyrzucania elementów bezużytecznych jest problematyczny, ponieważ struktury danych modułu odśmiecania elementów bezużytecznych nie są w prawidłowym stanie dla przechodzenia i mogą nie być w stanie podać pełnych wyników.</span><span class="sxs-lookup"><span data-stu-id="97652-246">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="97652-247">Jest to celowe.</span><span class="sxs-lookup"><span data-stu-id="97652-247">This is by design.</span></span>

- <span data-ttu-id="97652-248">Gdy używasz wyrzucania elementów bezużytecznych stacji roboczej z równoczesnym wyrzucaniem elementów bezużytecznych, odzyskane obiekty nie są kompaktowane, więc rozmiar sterty może być taki sam lub większy (fragmentacja może sprawić, że będzie większa).</span><span class="sxs-lookup"><span data-stu-id="97652-248">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="97652-249">Równoczesne wyrzucanie elementów bezużytecznych w generacji 2 jest opóźnione, gdy obciążenie pamięci fizycznej jest zbyt wysokie.</span><span class="sxs-lookup"><span data-stu-id="97652-249">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="97652-250">W poniższej procedurze opisano sposób ustawiania punktu przerwania, dzięki czemu można zmierzyć zarządzany stos.</span><span class="sxs-lookup"><span data-stu-id="97652-250">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="97652-251">Aby ustawić punkt przerwania na końcu wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="97652-251">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="97652-252">W usyliwiu WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="97652-252">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="97652-253">**bp mscorwks! WKS::GCHeap::RestartEE "j (dwo(mscorwks! WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';' g'"**</span><span class="sxs-lookup"><span data-stu-id="97652-253">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="97652-254">gdzie **GcCondemnedGeneration** jest ustawiony na żądane pokolenie.</span><span class="sxs-lookup"><span data-stu-id="97652-254">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="97652-255">To polecenie wymaga symboli prywatnych.</span><span class="sxs-lookup"><span data-stu-id="97652-255">This command requires private symbols.</span></span>

  <span data-ttu-id="97652-256">To polecenie wymusza przerwę, jeśli **RestartEE** jest wykonywany po generacji 2 obiekty zostały odzyskane do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-256">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="97652-257">W wyrzucania elementów bezużytecznych serwera tylko jeden wątek wywołuje **RestartEE**, więc punkt przerwania wystąpi tylko raz podczas wyrzucania elementów bezużytecznych generacji 2.</span><span class="sxs-lookup"><span data-stu-id="97652-257">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

## <a name="performance-check-procedures"></a><span data-ttu-id="97652-258">Procedury sprawdzania wydajności</span><span class="sxs-lookup"><span data-stu-id="97652-258">Performance Check Procedures</span></span>

<span data-ttu-id="97652-259">W tej sekcji opisano następujące procedury wyizolowania przyczyny problemu z wydajnością:</span><span class="sxs-lookup"><span data-stu-id="97652-259">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="97652-260">Określ, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-260">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="97652-261">Określ, czy wyjątek braku pamięci jest zarządzany.</span><span class="sxs-lookup"><span data-stu-id="97652-261">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="97652-262">Określ, ile pamięci wirtualnej można zarezerwować.</span><span class="sxs-lookup"><span data-stu-id="97652-262">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="97652-263">Określ, czy jest wystarczająca ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="97652-263">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="97652-264">Określ, ile pamięci zatwierdza zarządzana sterta.</span><span class="sxs-lookup"><span data-stu-id="97652-264">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="97652-265">Określ, ile pamięci rezerwuje zarządzany stos.</span><span class="sxs-lookup"><span data-stu-id="97652-265">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="97652-266">Określ duże obiekty w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="97652-266">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="97652-267">Określ odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="97652-267">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="97652-268">Określ, czy finalizator został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="97652-268">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="97652-269">Określ, czy istnieją obiekty oczekujące na sfinalizowanie.</span><span class="sxs-lookup"><span data-stu-id="97652-269">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="97652-270">Określ ilość wolnego miejsca w zarządzanym stercie.</span><span class="sxs-lookup"><span data-stu-id="97652-270">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="97652-271">Określ liczbę przypiętych obiektów.</span><span class="sxs-lookup"><span data-stu-id="97652-271">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="97652-272">Określ czas w wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-272">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="97652-273">Określ, co wyzwoliło wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-273">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="97652-274">Określ, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-274">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="97652-275">Aby ustalić, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="97652-275">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="97652-276">Sprawdź następujące dwa liczniki wydajności pamięci:</span><span class="sxs-lookup"><span data-stu-id="97652-276">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="97652-277">**% czasu w GC**.</span><span class="sxs-lookup"><span data-stu-id="97652-277">**% Time in GC**.</span></span> <span data-ttu-id="97652-278">Wyświetla procent czasu, który upłynął, który został poświęcony na wykonywanie wyrzucania elementów bezużytecznych po ostatnim cyklu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-278">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="97652-279">Ten licznik służy do określenia, czy moduł zbierający elementy bezużyteczne spędza zbyt dużo czasu, aby udostępnić miejsce na zarządzanych sterty.</span><span class="sxs-lookup"><span data-stu-id="97652-279">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="97652-280">Jeśli czas spędzony w wyrzucania elementów bezużytecznych jest stosunkowo niski, może to wskazywać na problem z zasobem poza zarządzanym stertą.</span><span class="sxs-lookup"><span data-stu-id="97652-280">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="97652-281">Ten licznik może nie być dokładne, gdy równoczesnych lub w tle wyrzucania elementów bezużytecznych jest zaangażowany.</span><span class="sxs-lookup"><span data-stu-id="97652-281">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="97652-282">**# Całkowita suma zatwierdzonych bajtów**.</span><span class="sxs-lookup"><span data-stu-id="97652-282">**# Total committed Bytes**.</span></span> <span data-ttu-id="97652-283">Wyświetla ilość pamięci wirtualnej aktualnie zatwierdzone przez moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="97652-283">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="97652-284">Ten licznik służy do określenia, czy pamięć zużywana przez moduł zbierający elementy bezużyteczne jest nadmierną częścią pamięci używanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="97652-284">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="97652-285">Większość liczników wydajności pamięci są aktualizowane na końcu każdego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-285">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="97652-286">W związku z tym mogą nie odzwierciedlać bieżące warunki, o których chcesz uzyskać informacje.</span><span class="sxs-lookup"><span data-stu-id="97652-286">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="97652-287">Aby ustalić, czy wyjątek braku pamięci jest zarządzany</span><span class="sxs-lookup"><span data-stu-id="97652-287">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="97652-288">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz polecenie wyjątek drukowania **(pe):**</span><span class="sxs-lookup"><span data-stu-id="97652-288">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="97652-289">**!pe**</span><span class="sxs-lookup"><span data-stu-id="97652-289">**!pe**</span></span>

    <span data-ttu-id="97652-290">Jeśli wyjątek jest <xref:System.OutOfMemoryException> zarządzany, jest wyświetlany jako typ wyjątku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="97652-290">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="97652-291">Jeśli dane wyjściowe nie określają wyjątek, należy określić, który wątek wyjątek poza pamięcią jest z.</span><span class="sxs-lookup"><span data-stu-id="97652-291">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="97652-292">Wpisz następujące polecenie w debugerze, aby wyświetlić wszystkie wątki z ich stosami wywołań:</span><span class="sxs-lookup"><span data-stu-id="97652-292">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="97652-293">**~\*Kb**</span><span class="sxs-lookup"><span data-stu-id="97652-293">**~\*kb**</span></span>

    <span data-ttu-id="97652-294">Wątek ze stosem, który ma `RaiseTheException` wywołania wyjątków jest wskazywany przez argument.</span><span class="sxs-lookup"><span data-stu-id="97652-294">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="97652-295">Jest to obiekt wyjątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="97652-295">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="97652-296">Za pomocą następującego polecenia można zrzucić zagnieżdżone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="97652-296">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="97652-297">**!pe -zagnieżdżone**</span><span class="sxs-lookup"><span data-stu-id="97652-297">**!pe -nested**</span></span>

    <span data-ttu-id="97652-298">Jeśli nie znajdziesz żadnych wyjątków, wyjątek braku pamięci pochodzi z kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="97652-298">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="97652-299">Aby określić, ile pamięci wirtualnej można zarezerwować</span><span class="sxs-lookup"><span data-stu-id="97652-299">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="97652-300">W usyliwiu WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby uzyskać największy wolny region:</span><span class="sxs-lookup"><span data-stu-id="97652-300">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="97652-301">**!adres -podsumowanie**</span><span class="sxs-lookup"><span data-stu-id="97652-301">**!address -summary**</span></span>

  <span data-ttu-id="97652-302">Największy wolny region jest wyświetlany, jak pokazano na poniższym wyjściu.</span><span class="sxs-lookup"><span data-stu-id="97652-302">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="97652-303">W tym przykładzie rozmiar największego wolnego regionu wynosi około 24000 KB (3A980 w szesnastkowej).</span><span class="sxs-lookup"><span data-stu-id="97652-303">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="97652-304">Ten region jest znacznie mniejszy niż to, czego potrzebuje moduł zbierający elementy bezużyteczne dla segmentu.</span><span class="sxs-lookup"><span data-stu-id="97652-304">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="97652-305">— lub —</span><span class="sxs-lookup"><span data-stu-id="97652-305">-or-</span></span>

- <span data-ttu-id="97652-306">Użyj polecenia **vmstat:**</span><span class="sxs-lookup"><span data-stu-id="97652-306">Use the **vmstat** command:</span></span>

  <span data-ttu-id="97652-307">**!vmstat**</span><span class="sxs-lookup"><span data-stu-id="97652-307">**!vmstat**</span></span>

  <span data-ttu-id="97652-308">Największy wolny region jest największą wartością w kolumnie MAXIMUM, jak pokazano na poniższym wyjściu.</span><span class="sxs-lookup"><span data-stu-id="97652-308">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="97652-309">Aby ustalić, czy jest wystarczająca ilość pamięci fizycznej</span><span class="sxs-lookup"><span data-stu-id="97652-309">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="97652-310">Uruchom Menedżera zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="97652-310">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="97652-311">Na karcie **Wydajność** przyjrzyj się wartości zatwierdzonej.</span><span class="sxs-lookup"><span data-stu-id="97652-311">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="97652-312">(W systemie Windows 7 przyjrzyj **się zatwierdzeniu (KB)** w **grupie System.**</span><span class="sxs-lookup"><span data-stu-id="97652-312">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="97652-313">Jeśli **wartość Suma** jest zbliżony do **limitu**, zaczyna brakować pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="97652-313">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="97652-314">Aby określić ilość pamięci, jaką zatwierdza zarządzana sterta</span><span class="sxs-lookup"><span data-stu-id="97652-314">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="97652-315">Użyj `# Total committed bytes` licznika wydajności pamięci, aby uzyskać liczbę bajtów, które zatwierdza sterty zarządzane.</span><span class="sxs-lookup"><span data-stu-id="97652-315">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="97652-316">Moduł zbierający elementy bezużyteczne zatwierdza fragmenty w segmencie zgodnie z potrzebami, nie wszystkie w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="97652-316">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="97652-317">Nie należy `# Bytes in all Heaps` używać licznika wydajności, ponieważ nie reprezentuje rzeczywiste użycie pamięci przez zarządzane sterty.</span><span class="sxs-lookup"><span data-stu-id="97652-317">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="97652-318">Rozmiar generacji jest uwzględniony w tej wartości i jest faktycznie jego rozmiar progu, to znaczy rozmiar, który wywołuje wyrzucania elementów bezużytecznych, jeśli generacji jest wypełniona obiektów.</span><span class="sxs-lookup"><span data-stu-id="97652-318">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="97652-319">W związku z tym ta wartość jest zwykle zero.</span><span class="sxs-lookup"><span data-stu-id="97652-319">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="97652-320">Aby określić ilość pamięci rezerwowanej sterty zarządzanej</span><span class="sxs-lookup"><span data-stu-id="97652-320">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="97652-321">Użyj `# Total reserved bytes` licznika wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="97652-321">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="97652-322">Moduł zbierający elementy bezużyteczne rezerwuje pamięć w segmentach i można określić, gdzie segment rozpoczyna się za pomocą polecenia **eeheap.**</span><span class="sxs-lookup"><span data-stu-id="97652-322">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="97652-323">Chociaż można określić ilość pamięci moduł zbierający elementy bezużyteczne przydziela dla każdego segmentu, rozmiar segmentu jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="97652-323">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="97652-324">Aplikacja nigdy nie należy zakładać o lub zależy od określonego rozmiaru segmentu, ani nie należy próbować skonfigurować ilość pamięci dostępnej dla alokacji segmentów.</span><span class="sxs-lookup"><span data-stu-id="97652-324">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="97652-325">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="97652-325">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="97652-326">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="97652-326">**!eeheap -gc**</span></span>

  <span data-ttu-id="97652-327">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="97652-327">The result is as follows.</span></span>

  ```console
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

  <span data-ttu-id="97652-328">Adresy oznaczone przez "segment" są adresami początkowymi segmentów.</span><span class="sxs-lookup"><span data-stu-id="97652-328">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="97652-329">Aby określić duże obiekty w generacji 2</span><span class="sxs-lookup"><span data-stu-id="97652-329">To determine large objects in generation 2</span></span>

- <span data-ttu-id="97652-330">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="97652-330">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="97652-331">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="97652-331">**!dumpheap –stat**</span></span>

  <span data-ttu-id="97652-332">Jeśli zarządzana sterta jest duża, **dumpheap** może zająć trochę czasu, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="97652-332">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="97652-333">Można rozpocząć analizowanie z ostatnich kilku wierszy danych wyjściowych, ponieważ lista obiektów, które używają najwięcej miejsca.</span><span class="sxs-lookup"><span data-stu-id="97652-333">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="97652-334">Przykład:</span><span class="sxs-lookup"><span data-stu-id="97652-334">For example:</span></span>

  ```console
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

  <span data-ttu-id="97652-335">Ostatni wymieniony obiekt jest ciągiem i zajmuje najwięcej miejsca.</span><span class="sxs-lookup"><span data-stu-id="97652-335">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="97652-336">Można zbadać aplikacji, aby zobaczyć, jak można zoptymalizować obiekty ciągu.</span><span class="sxs-lookup"><span data-stu-id="97652-336">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="97652-337">Aby wyświetlić ciągi o przedziale od 150 do 200 bajtów, wpisz następujące ciągi:</span><span class="sxs-lookup"><span data-stu-id="97652-337">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="97652-338">**!dumpheap -type System.String -min 150 -max 200**</span><span class="sxs-lookup"><span data-stu-id="97652-338">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="97652-339">Przykład wyników jest następujący.</span><span class="sxs-lookup"><span data-stu-id="97652-339">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="97652-340">Użycie liczby całkowitej zamiast ciągu dla identyfikatora może być bardziej efektywne.</span><span class="sxs-lookup"><span data-stu-id="97652-340">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="97652-341">Jeśli ten sam ciąg jest powtarzany tysiące razy, należy wziąć pod uwagę internowanie ciągu.</span><span class="sxs-lookup"><span data-stu-id="97652-341">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="97652-342">Aby uzyskać więcej informacji na temat internowania <xref:System.String.Intern%2A?displayProperty=nameWithType> ciągów, zobacz temat odwołania dla metody.</span><span class="sxs-lookup"><span data-stu-id="97652-342">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="97652-343">Aby określić odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="97652-343">To determine references to objects</span></span>

- <span data-ttu-id="97652-344">W usyliwiu WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby wyświetlić odwołania do obiektów:</span><span class="sxs-lookup"><span data-stu-id="97652-344">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="97652-345">**!gcroot**</span><span class="sxs-lookup"><span data-stu-id="97652-345">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="97652-346">Aby określić odwołania dla określonego obiektu, należy podać adres:</span><span class="sxs-lookup"><span data-stu-id="97652-346">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="97652-347">**!gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="97652-347">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="97652-348">Korzenie znalezione na stosach mogą być fałszywie dodatnie.</span><span class="sxs-lookup"><span data-stu-id="97652-348">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="97652-349">Aby uzyskać więcej informacji, użyj polecenia `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="97652-349">For more information, use the command `!help gcroot`.</span></span>

  ```console
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

  <span data-ttu-id="97652-350">Polecenie **gcroot** może zająć dużo czasu, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="97652-350">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="97652-351">Każdy obiekt, który nie jest odzyskiwany przez wyrzucanie elementów bezużytecznych jest obiektem na żywo.</span><span class="sxs-lookup"><span data-stu-id="97652-351">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="97652-352">Oznacza to, że niektóre root jest bezpośrednio lub pośrednio przytrzymuje na obiekcie, więc **gcroot** powinien zwrócić informacje o ścieżce do obiektu.</span><span class="sxs-lookup"><span data-stu-id="97652-352">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="97652-353">Należy zbadać wykresy zwrócone i zobaczyć, dlaczego te obiekty są nadal odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="97652-353">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="97652-354">Aby ustalić, czy finalizator został uruchomiony</span><span class="sxs-lookup"><span data-stu-id="97652-354">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="97652-355">Uruchom program testowy zawierający następujący kod:</span><span class="sxs-lookup"><span data-stu-id="97652-355">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="97652-356">Jeśli test rozwiązuje problem, oznacza to, że moduł zbierający elementy bezużyteczne nie odzyskuje obiektów, ponieważ finalizatory dla tych obiektów zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="97652-356">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="97652-357">Metoda <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> umożliwia finalizatorów, aby zakończyć swoje zadania i rozwiązuje problem.</span><span class="sxs-lookup"><span data-stu-id="97652-357">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="97652-358">Aby ustalić, czy istnieją obiekty oczekujące na finalizacje</span><span class="sxs-lookup"><span data-stu-id="97652-358">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="97652-359">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="97652-359">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="97652-360">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="97652-360">**!finalizequeue**</span></span>

    <span data-ttu-id="97652-361">Spójrz na liczbę obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="97652-361">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="97652-362">Jeśli liczba jest wysoka, należy zbadać, dlaczego te finalizatorów nie może postępu w ogóle lub nie może poczyć wystarczająco szybko.</span><span class="sxs-lookup"><span data-stu-id="97652-362">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="97652-363">Aby uzyskać dane wyjściowe wątków, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="97652-363">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="97652-364">**nici -specjalne**</span><span class="sxs-lookup"><span data-stu-id="97652-364">**threads -special**</span></span>

    <span data-ttu-id="97652-365">To polecenie zapewnia dane wyjściowe, takie jak następujące.</span><span class="sxs-lookup"><span data-stu-id="97652-365">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="97652-366">Finalizator wątku wskazuje, który finalizator, jeśli istnieje, jest obecnie uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="97652-366">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="97652-367">Gdy wątek finalizatora nie jest uruchomiony żadnych finalizatorów, oczekuje na zdarzenie, aby powiedzieć mu, aby wykonać swoją pracę.</span><span class="sxs-lookup"><span data-stu-id="97652-367">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="97652-368">W większości czasu zobaczysz wątku finalizatora w tym stanie, ponieważ działa na THREAD_HIGHEST_PRIORITY i ma zakończyć uruchamianie finalizatorów, jeśli w ogóle, bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="97652-368">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="97652-369">Aby określić ilość wolnego miejsca w zarządzanym stercie</span><span class="sxs-lookup"><span data-stu-id="97652-369">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="97652-370">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="97652-370">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="97652-371">**!dumpheap -type Free -stat**</span><span class="sxs-lookup"><span data-stu-id="97652-371">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="97652-372">To polecenie wyświetla całkowity rozmiar wszystkich wolnych obiektów na zarządzanym stercie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="97652-372">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="97652-373">Aby określić wolne miejsce w generacji 0, wpisz następujące polecenie dla informacji o zużyciu pamięci według generacji:</span><span class="sxs-lookup"><span data-stu-id="97652-373">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="97652-374">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="97652-374">**!eeheap -gc**</span></span>

  <span data-ttu-id="97652-375">To polecenie wyświetla dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="97652-375">This command displays output similar to the following.</span></span> <span data-ttu-id="97652-376">Ostatni wiersz pokazuje segment efemeryczny.</span><span class="sxs-lookup"><span data-stu-id="97652-376">The last line shows the ephemeral segment.</span></span>

  ```console
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

- <span data-ttu-id="97652-377">Oblicz przestrzeń używaną przez generację 0:</span><span class="sxs-lookup"><span data-stu-id="97652-377">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="97652-378">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="97652-378">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="97652-379">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="97652-379">The result is as follows.</span></span> <span data-ttu-id="97652-380">Generacja 0 wynosi około 9 MB.</span><span class="sxs-lookup"><span data-stu-id="97652-380">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="97652-381">Następujące polecenie zrzuca wolne miejsce w zakresie generacji 0:</span><span class="sxs-lookup"><span data-stu-id="97652-381">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="97652-382">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="97652-382">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="97652-383">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="97652-383">The result is as follows.</span></span>

  ```console
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

  <span data-ttu-id="97652-384">To dane wyjściowe pokazuje, że część generacji 0 sterty używa 9 MB miejsca dla obiektów i ma 7 MB wolnego.</span><span class="sxs-lookup"><span data-stu-id="97652-384">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="97652-385">Analiza ta pokazuje, w jakim stopniu generacja 0 przyczynia się do fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="97652-385">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="97652-386">Ta kwota użycia sterty powinny być dyskontowane od całkowitej kwoty jako przyczyna fragmentacji przez obiekty długoterminowe.</span><span class="sxs-lookup"><span data-stu-id="97652-386">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="97652-387">Aby określić liczbę przypiętych obiektów</span><span class="sxs-lookup"><span data-stu-id="97652-387">To determine the number of pinned objects</span></span>

- <span data-ttu-id="97652-388">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="97652-388">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="97652-389">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="97652-389">**!gchandles**</span></span>

  <span data-ttu-id="97652-390">Wyświetlane statystyki obejmują liczbę przypiętych uchwytów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="97652-390">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="97652-391">Aby określić czas w wyrzucaniu elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="97652-391">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="97652-392">Sprawdź `% Time in GC` licznik wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="97652-392">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="97652-393">Wartość jest obliczana przy użyciu czasu interwału próbki.</span><span class="sxs-lookup"><span data-stu-id="97652-393">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="97652-394">Ponieważ liczniki są aktualizowane na końcu każdego wyrzucania elementów bezużytecznych, bieżący przykład będzie miał taką samą wartość jak poprzedni przykład, jeśli nie wystąpiły żadne kolekcje podczas interwału.</span><span class="sxs-lookup"><span data-stu-id="97652-394">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="97652-395">Czas zbierania jest uzyskiwany przez pomnożenie czasu interwału próbki z wartością procentową.</span><span class="sxs-lookup"><span data-stu-id="97652-395">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="97652-396">Poniższe dane pokazują cztery interwały próbkowania po dwie sekundy dla 8-sekundowego badania.</span><span class="sxs-lookup"><span data-stu-id="97652-396">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="97652-397">, `Gen0` `Gen1`i `Gen2` kolumny pokazują liczbę wyrzucań elementów bezużytecznych, które wystąpiły w tym przedziale dla tej generacji.</span><span class="sxs-lookup"><span data-stu-id="97652-397">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="97652-398">Te informacje nie są wyświetlane, gdy wystąpił wyrzucania elementów bezużytecznych, ale można określić liczbę wyrzucania elementów bezużytecznych, które wystąpiły w przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="97652-398">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="97652-399">Zakładając, że w najgorszym przypadku dziesiątej generacji 0 wyrzucania elementów bezużytecznych zakończeniu na początku drugiego interwału, a jedenasta generacja 0 wyrzucania elementów bezużytecznych zakończył się na końcu piątego interwału.</span><span class="sxs-lookup"><span data-stu-id="97652-399">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="97652-400">Czas między końcem dziesiątej i końca jedenastego wyrzucania elementów bezużytecznych wynosi około 2 sekund, a licznik wydajności pokazuje 3%, więc czas trwania kolekcji elementów bezużytecznych jedenastej generacji 0 był (2 sekundy \* 3% = 60 ms).</span><span class="sxs-lookup"><span data-stu-id="97652-400">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="97652-401">W tym przykładzie istnieje 5 okresów.</span><span class="sxs-lookup"><span data-stu-id="97652-401">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="97652-402">Druga generacja 2 wyrzucania elementów bezużytecznych rozpoczęła się w trzecim interwale i zakończył się w piątym przedziale.</span><span class="sxs-lookup"><span data-stu-id="97652-402">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="97652-403">Zakładając, że najgorszy przypadek, ostatni wyrzucania elementów bezużytecznych był dla kolekcji generacji 0, który zakończył się na początku drugiego interwału i generacji 2 wyrzucania elementów bezużytecznych zakończeniu na koniec piątego interwału.</span><span class="sxs-lookup"><span data-stu-id="97652-403">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="97652-404">W związku z tym czas między końcem generacji 0 wyrzucania elementów bezużytecznych i koniec generacji 2 wyrzucania elementów bezużytecznych jest 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="97652-404">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="97652-405">Ponieważ `% Time in GC` licznik wynosi 20%, maksymalny czas, jaki mogło wziąć wyrzucanie elementów bezużytecznych generacji 2, wynosi (4 sekundy \* 20% = 800 ms).</span><span class="sxs-lookup"><span data-stu-id="97652-405">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="97652-406">Alternatywnie można określić długość wyrzucania elementów bezużytecznych przy użyciu [wyrzucania elementów bezużytecznych ETW zdarzeń](../../../docs/framework/performance/garbage-collection-etw-events.md)i analizować informacje w celu określenia czasu trwania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-406">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="97652-407">Na przykład następujące dane pokazuje sekwencję zdarzeń, które wystąpiły podczas nierównoczesnych wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-407">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  <span data-ttu-id="97652-408">Zawieszenie zarządzanego wątku zajęło`GCSuspendEEEnd` 26us ( – `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="97652-408">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="97652-409">Rzeczywista wyrzucanie śmieci trwała 4,8 ms (`GCEnd_V1` – `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="97652-409">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="97652-410">Wznowienie zarządzanych wątków zajęło 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="97652-410">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="97652-411">Następujące dane wyjściowe zawiera przykład wyrzucania elementów bezużytecznych w tle i zawiera proces, wątki i pola zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="97652-411">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="97652-412">(Nie wszystkie dane są wyświetlane).</span><span class="sxs-lookup"><span data-stu-id="97652-412">(Not all data is shown.)</span></span>

  ```console
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

  <span data-ttu-id="97652-413">Zdarzenie `GCStart_V1` na 42504816 wskazuje, że jest to wyrzucanie elementów `1`bezużytecznych w tle, ponieważ ostatnim polem jest .</span><span class="sxs-lookup"><span data-stu-id="97652-413">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="97652-414">Staje się to nr wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-414">This becomes garbage collection No.</span></span> <span data-ttu-id="97652-415">102019.</span><span class="sxs-lookup"><span data-stu-id="97652-415">102019.</span></span>

  <span data-ttu-id="97652-416">Zdarzenie `GCStart` występuje, ponieważ istnieje potrzeba efemerycznego wyrzucania elementów bezużytecznych przed rozpoczęciem wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="97652-416">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="97652-417">Staje się to nr wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-417">This becomes garbage collection No.</span></span> <span data-ttu-id="97652-418">102020.</span><span class="sxs-lookup"><span data-stu-id="97652-418">102020.</span></span>

  <span data-ttu-id="97652-419">Na 42514170, nr wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="97652-419">At 42514170, garbage collection No.</span></span> <span data-ttu-id="97652-420">102020 kończy.</span><span class="sxs-lookup"><span data-stu-id="97652-420">102020 finishes.</span></span> <span data-ttu-id="97652-421">Zarządzane wątki są ponownie uruchamiane w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="97652-421">The managed threads are restarted at this point.</span></span> <span data-ttu-id="97652-422">Jest to zakończone w wątku 4372, który wyzwolił to wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="97652-422">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="97652-423">Na nitce 4744 występuje zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="97652-423">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="97652-424">Jest to jedyny czas, w którym wyrzucanie elementów bezużytecznych w tle musi zawiesić zarządzane wątki.</span><span class="sxs-lookup"><span data-stu-id="97652-424">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="97652-425">Ten czas trwania wynosi około 99 ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="97652-425">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="97652-426">Zdarzenie `GCEnd` dla wyrzucania elementów bezużytecznych w tle jest na 89931423.</span><span class="sxs-lookup"><span data-stu-id="97652-426">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="97652-427">Oznacza to, że wyrzucanie elementów bezużytecznych w tle trwało około 47 sekund ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="97652-427">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="97652-428">Podczas uruchamiania zarządzanych wątków, można zobaczyć dowolną liczbę tymczasowych wyrzucania elementów bezużytecznych występujących.</span><span class="sxs-lookup"><span data-stu-id="97652-428">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="97652-429">Aby ustalić, co wyzwoliło wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="97652-429">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="97652-430">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby wyświetlić wszystkie wątki z ich stosami wywołań:</span><span class="sxs-lookup"><span data-stu-id="97652-430">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="97652-431">**~\*Kb**</span><span class="sxs-lookup"><span data-stu-id="97652-431">**~\*kb**</span></span>

  <span data-ttu-id="97652-432">To polecenie wyświetla dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="97652-432">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="97652-433">Jeśli wyrzucanie elementów bezużytecznych została spowodowana przez powiadomienie o małej ilości pamięci z systemu operacyjnego, stos wywołań jest podobny, z tą różnicą, że wątek jest wątkiem finalizatora.</span><span class="sxs-lookup"><span data-stu-id="97652-433">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="97652-434">Finalizator wątku pobiera asynchroniczne powiadomienie o niskiej pamięci i wywołuje wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97652-434">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="97652-435">Jeśli wyrzucanie elementów bezużytecznych zostało spowodowane przez alokację pamięci, stos jest wyświetlany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="97652-435">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

  ```console
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

  <span data-ttu-id="97652-436">Just-in-time pomocnika (`JIT_New*`) `GCHeap::GarbageCollectGeneration`w końcu dzwoni .</span><span class="sxs-lookup"><span data-stu-id="97652-436">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="97652-437">Jeśli stwierdzisz, że generacji 2 wyrzucania elementów bezużytecznych są spowodowane przez alokacje, należy określić, które obiekty są zbierane przez wyrzucanie elementów bezużytecznych generacji 2 i jak ich uniknąć.</span><span class="sxs-lookup"><span data-stu-id="97652-437">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="97652-438">Oznacza to, że chcesz określić różnicę między początku i końca generacji 2 wyrzucania elementów bezużytecznych i obiektów, które spowodowały kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="97652-438">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="97652-439">Na przykład wpisz następujące polecenie w debugerze, aby wyświetlić początek kolekcji 2 generacji:</span><span class="sxs-lookup"><span data-stu-id="97652-439">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="97652-440">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="97652-440">**!dumpheap –stat**</span></span>

  <span data-ttu-id="97652-441">Przykładowe dane wyjściowe (skrócone, aby pokazać obiekty, które zajmują najwięcej miejsca):</span><span class="sxs-lookup"><span data-stu-id="97652-441">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
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

  <span data-ttu-id="97652-442">Powtórz polecenie na końcu generacji 2:</span><span class="sxs-lookup"><span data-stu-id="97652-442">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="97652-443">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="97652-443">**!dumpheap –stat**</span></span>

  <span data-ttu-id="97652-444">Przykładowe dane wyjściowe (skrócone, aby pokazać obiekty, które zajmują najwięcej miejsca):</span><span class="sxs-lookup"><span data-stu-id="97652-444">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
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

  <span data-ttu-id="97652-445">Obiekty `double[]` zniknęły z końca danych wyjściowych, co oznacza, że zostały zebrane.</span><span class="sxs-lookup"><span data-stu-id="97652-445">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="97652-446">Obiekty te stanowią około 70 MB.</span><span class="sxs-lookup"><span data-stu-id="97652-446">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="97652-447">Pozostałe obiekty nie zmieniły się zbytnio.</span><span class="sxs-lookup"><span data-stu-id="97652-447">The remaining objects did not change much.</span></span> <span data-ttu-id="97652-448">W związku `double[]` z tym te obiekty były przyczyną tej generacji 2 wyrzucania elementów bezużytecznych wystąpił.</span><span class="sxs-lookup"><span data-stu-id="97652-448">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="97652-449">Następnym krokiem jest ustalenie, `double[]` dlaczego obiekty są tam i dlaczego zginęły.</span><span class="sxs-lookup"><span data-stu-id="97652-449">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="97652-450">Możesz zapytać programistę kodu, skąd pochodzą te obiekty, lub użyć polecenia **gcroot.**</span><span class="sxs-lookup"><span data-stu-id="97652-450">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="97652-451">Aby ustalić, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="97652-451">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="97652-452">Skoreluj wartość licznika `% Time in GC` wydajności pamięci z czasem procesu.</span><span class="sxs-lookup"><span data-stu-id="97652-452">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="97652-453">Jeśli `% Time in GC` wartość wzrasta w tym samym czasie co czas procesu, wyrzucanie elementów bezużytecznych powoduje wysokie użycie procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="97652-453">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="97652-454">W przeciwnym razie profil aplikacji, aby znaleźć miejsce wysokiego użycia występuje.</span><span class="sxs-lookup"><span data-stu-id="97652-454">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="97652-455">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97652-455">See also</span></span>

- [<span data-ttu-id="97652-456">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="97652-456">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
