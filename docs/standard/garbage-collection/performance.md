---
title: Odzyskiwanie pamięci i wydajność
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 1d9c72a64d172dcadf1bff1b1edf3050ca5f7d05
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287626"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="5147e-102">Odzyskiwanie pamięci i wydajność</span><span class="sxs-lookup"><span data-stu-id="5147e-102">Garbage Collection and Performance</span></span>

<span data-ttu-id="5147e-103">W tym temacie opisano problemy związane z wyrzucaniem elementów bezużytecznych i użyciem pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="5147e-104">Rozwiązuje on problemy związane z zarządzanym stertą i wyjaśnia, jak zminimalizować efekt wyrzucania elementów bezużytecznych w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="5147e-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="5147e-105">Każdy problem zawiera linki do procedur, których można użyć do badania problemów.</span><span class="sxs-lookup"><span data-stu-id="5147e-105">Each issue has links to procedures that you can use to investigate problems.</span></span>

## <a name="performance-analysis-tools"></a><span data-ttu-id="5147e-106">Narzędzia do analizy wydajności</span><span class="sxs-lookup"><span data-stu-id="5147e-106">Performance Analysis Tools</span></span>

<span data-ttu-id="5147e-107">W poniższych sekcjach opisano narzędzia, które są dostępne do badania problemów dotyczących użycia pamięci i wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-107">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="5147e-108">[Procedury](#performance-check-procedures) opisane w dalszej części tego tematu odnoszą się do tych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="5147e-108">The [procedures](#performance-check-procedures) provided later in this topic refer to these tools.</span></span>

### <a name="memory-performance-counters"></a><span data-ttu-id="5147e-109">Liczniki wydajności pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-109">Memory Performance Counters</span></span>

<span data-ttu-id="5147e-110">Liczników wydajności można używać do zbierania danych wydajności.</span><span class="sxs-lookup"><span data-stu-id="5147e-110">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="5147e-111">Aby uzyskać instrukcje, zobacz [profilowanie środowiska uruchomieniowego](../../framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="5147e-111">For instructions, see [Runtime Profiling](../../framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="5147e-112">Kategoria pamięci środowiska CLR platformy .NET liczników wydajności, zgodnie z opisem w [licznikach wydajności w .NET Framework](../../framework/debug-trace-profile/performance-counters.md), zawiera informacje na temat modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-112">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

### <a name="debugging-with-sos"></a><span data-ttu-id="5147e-113">Debugowanie za pomocą SOS</span><span class="sxs-lookup"><span data-stu-id="5147e-113">Debugging with SOS</span></span>

<span data-ttu-id="5147e-114">Aby sprawdzić obiekty na zarządzanym stosie, można użyć [debugera systemu Windows (WinDbg)](/windows-hardware/drivers/debugger/index) .</span><span class="sxs-lookup"><span data-stu-id="5147e-114">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="5147e-115">Aby zainstalować program WinDbg, zainstaluj narzędzia debugowania dla systemu Windows ze strony [Pobierz narzędzia debugowania dla systemu Windows](/windows-hardware/drivers/debugger/debugger-download-tools) .</span><span class="sxs-lookup"><span data-stu-id="5147e-115">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="5147e-116">Zdarzenia ETW odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-116">Garbage Collection ETW Events</span></span>

<span data-ttu-id="5147e-117">Śledzenie zdarzeń systemu Windows (ETW) to system śledzenia, który uzupełnia profilowanie i obsługę debugowania zapewniane przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5147e-117">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="5147e-118">Począwszy od .NET Framework 4, [zdarzenia ETW do wyrzucania elementów bezużytecznych](../../framework/performance/garbage-collection-etw-events.md) przechwytują przydatne informacje na potrzeby analizowania zarządzanego sterty z punktu widzenia statystycznego.</span><span class="sxs-lookup"><span data-stu-id="5147e-118">Starting with the .NET Framework 4, [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="5147e-119">Na przykład `GCStart_V1` zdarzenie, które jest zgłaszane, gdy zostanie przeprowadzone wyrzucanie elementów bezużytecznych, zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="5147e-119">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="5147e-120">Które Generowanie obiektów jest zbierane.</span><span class="sxs-lookup"><span data-stu-id="5147e-120">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="5147e-121">Co wyzwoliło wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-121">What triggered the garbage collection.</span></span>

- <span data-ttu-id="5147e-122">Typ wyrzucania elementów bezużytecznych (współbieżne lub niewspółbieżne).</span><span class="sxs-lookup"><span data-stu-id="5147e-122">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="5147e-123">Rejestrowanie zdarzeń ETW jest wydajne i nie będzie maskować żadnych problemów z wydajnością związanych z odzyskiwaniem pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-123">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="5147e-124">Proces może zapewnić własne zdarzenia w połączeniu ze zdarzeniami ETW.</span><span class="sxs-lookup"><span data-stu-id="5147e-124">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="5147e-125">Po zarejestrowaniu zarówno zdarzenia aplikacji, jak i zdarzenia wyrzucania elementów bezużytecznych mogą być skorelowane, aby określić sposób i czas wystąpienia problemów sterty.</span><span class="sxs-lookup"><span data-stu-id="5147e-125">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="5147e-126">Na przykład aplikacja serwera może zapewnić zdarzenia na początku i na końcu żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="5147e-126">For example, a server application could provide events at the start and end of a client request.</span></span>

### <a name="the-profiling-api"></a><span data-ttu-id="5147e-127">Profilowanie API</span><span class="sxs-lookup"><span data-stu-id="5147e-127">The Profiling API</span></span>

<span data-ttu-id="5147e-128">Interfejsy profilowania środowiska uruchomieniowego języka wspólnego (CLR) zawierają szczegółowe informacje o obiektach, których dotyczyły podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-128">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="5147e-129">Program profilujący może zostać powiadomiony, gdy rozpocznie się i skończy odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-129">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="5147e-130">Może ona dostarczać raporty dotyczące obiektów na zarządzanym stosie, w tym identyfikowanie obiektów w każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-130">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="5147e-131">Aby uzyskać więcej informacji, zobacz [profilowanie — Omówienie](../../framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5147e-131">For more information, see [Profiling Overview](../../framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="5147e-132">Prepliky mogą dostarczać wyczerpujące informacje.</span><span class="sxs-lookup"><span data-stu-id="5147e-132">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="5147e-133">Jednak złożone profilowania mogą potencjalnie modyfikować zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-133">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="5147e-134">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="5147e-134">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="5147e-135">Począwszy od .NET Framework 4, monitorowanie zasobów domeny aplikacji (ARM) umożliwia hostom monitorowanie użycia procesora i pamięci przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-135">Starting with the .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="5147e-136">Aby uzyskać więcej informacji, zobacz [monitorowanie zasobów domeny aplikacji](app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="5147e-136">For more information, see [Application Domain Resource Monitoring](app-domain-resource-monitoring.md).</span></span>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="5147e-137">Rozwiązywanie problemów z wydajnością</span><span class="sxs-lookup"><span data-stu-id="5147e-137">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="5147e-138">Pierwszym krokiem jest [określenie, czy problem jest w rzeczywistości odzyskiwaniem pamięci](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="5147e-138">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="5147e-139">Jeśli określisz, że jest to możliwe, wybierz z poniższej listy, aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="5147e-139">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="5147e-140">Zgłaszany jest wyjątek braku pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-140">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="5147e-141">Proces używa zbyt dużej ilości pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-141">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="5147e-142">Moduł wyrzucania elementów bezużytecznych nie odzyska obiektów wystarczająco szybko</span><span class="sxs-lookup"><span data-stu-id="5147e-142">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="5147e-143">Sterta zarządzana jest zbyt pofragmentowana</span><span class="sxs-lookup"><span data-stu-id="5147e-143">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="5147e-144">Wyrzucanie elementów bezużytecznych jest zbyt długie</span><span class="sxs-lookup"><span data-stu-id="5147e-144">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="5147e-145">Generacja 0 jest zbyt duża</span><span class="sxs-lookup"><span data-stu-id="5147e-145">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="5147e-146">Użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt duże</span><span class="sxs-lookup"><span data-stu-id="5147e-146">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="5147e-147">Problem: zgłoszono wyjątek braku pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-147">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="5147e-148">Istnieją dwa wiarygodne przypadki, w których <xref:System.OutOfMemoryException> można było zgłaszać zarządzane:</span><span class="sxs-lookup"><span data-stu-id="5147e-148">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="5147e-149">Zaczyna brakować pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="5147e-149">Running out of virtual memory.</span></span>

  <span data-ttu-id="5147e-150">Moduł wyrzucania elementów bezużytecznych przydziela pamięć z systemu w segmentach wstępnie określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="5147e-150">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="5147e-151">Jeśli alokacja wymaga dodatkowego segmentu, ale w obszarze pamięci wirtualnej procesu nie ma ciągłego wolnego bloku, alokacja dla sterty zarządzanej nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="5147e-151">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="5147e-152">Brak wystarczającej ilości pamięci fizycznej do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="5147e-152">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="5147e-153">Sprawdzanie wydajności</span><span class="sxs-lookup"><span data-stu-id="5147e-153">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="5147e-154">Ustal, czy jest zarządzany wyjątek braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-154">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="5147e-155">Określ ilość pamięci wirtualnej, która może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="5147e-155">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="5147e-156">Należy określić, czy jest dostępna wystarczająca ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="5147e-156">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="5147e-157">Jeśli ustalisz, że wyjątek nie jest wiarygodny, skontaktuj się z działem obsługi klienta i pomocy technicznej firmy Microsoft, podając następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="5147e-157">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="5147e-158">Stos z wyjątkiem zarządzanego wyjątku out-of-memory.</span><span class="sxs-lookup"><span data-stu-id="5147e-158">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="5147e-159">Pełny zrzut pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-159">Full memory dump.</span></span>

- <span data-ttu-id="5147e-160">Dane, które udowadniają, że nie jest to słuszny wyjątek braku pamięci, w tym dane, które pokazują, że pamięć wirtualna lub fizyczna nie jest problemem.</span><span class="sxs-lookup"><span data-stu-id="5147e-160">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="5147e-161">Problem: proces używa zbyt dużej ilości pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-161">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="5147e-162">Typowym założeniem jest, że użycie pamięci na karcie **wydajność** Menedżera zadań systemu Windows może wskazywać, kiedy jest zbyt dużo pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-162">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="5147e-163">Jednak te wyświetlacze odnoszą się do zestawu roboczego; nie zawiera on informacji o użyciu pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="5147e-163">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="5147e-164">Jeśli okaże się, że przyczyną problemu jest sterta zarządzana, należy zmierzyć stertę zarządzaną w miarę upływu czasu, aby określić wzorce.</span><span class="sxs-lookup"><span data-stu-id="5147e-164">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="5147e-165">W przypadku stwierdzenia, że problem nie jest spowodowany przez zarządzaną stertę, należy użyć debugowania natywnego.</span><span class="sxs-lookup"><span data-stu-id="5147e-165">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="5147e-166">Sprawdzanie wydajności</span><span class="sxs-lookup"><span data-stu-id="5147e-166">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="5147e-167">Określ ilość pamięci wirtualnej, która może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="5147e-167">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="5147e-168">Określ ilość pamięci, która jest zatwierdzana przez stertę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="5147e-168">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="5147e-169">Określ ilość pamięci, jaką rezerwuje sterta zarządza.</span><span class="sxs-lookup"><span data-stu-id="5147e-169">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="5147e-170">Określ duże obiekty w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5147e-170">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="5147e-171">Określanie odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="5147e-171">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="5147e-172">Problem: moduł zbierający elementy bezużyteczne nie odzyska obiektów wystarczająco szybko</span><span class="sxs-lookup"><span data-stu-id="5147e-172">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="5147e-173">Gdy pojawia się tak, jakby obiekty nie są odzyskiwane w oczekiwany sposób na wyrzucanie elementów bezużytecznych, należy określić, czy istnieją silne odwołania do tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5147e-173">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="5147e-174">Ten problem może również wystąpić, jeśli nie wyrzucanie elementów bezużytecznych dla generacji, która zawiera martwy obiekt, co oznacza, że finalizator dla martwego obiektu nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5147e-174">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="5147e-175">Na przykład jest to możliwe, gdy uruchamiasz aplikację jednowątkowego typu Apartment (STA) i wątek, w którym usługi kolejki finalizatora nie mogą wywoływać do niej.</span><span class="sxs-lookup"><span data-stu-id="5147e-175">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="5147e-176">Sprawdzanie wydajności</span><span class="sxs-lookup"><span data-stu-id="5147e-176">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="5147e-177">Sprawdź odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="5147e-177">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="5147e-178">Ustal, czy finalizator został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5147e-178">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="5147e-179">Ustal, czy istnieją obiekty oczekujące na sfinalizowanie.</span><span class="sxs-lookup"><span data-stu-id="5147e-179">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="5147e-180">Problem: sterta zarządzana jest zbyt pofragmentowana</span><span class="sxs-lookup"><span data-stu-id="5147e-180">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="5147e-181">Poziom fragmentacji jest obliczany jako stosunek ilości wolnego miejsca na łączną przydzieloną pamięć dla generacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-181">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="5147e-182">W przypadku generacji 2 akceptowalny poziom fragmentacji nie przekracza 20%.</span><span class="sxs-lookup"><span data-stu-id="5147e-182">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="5147e-183">Ponieważ generacja 2 może być bardzo duża, stosunek fragmentacji jest ważniejszy niż wartość bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="5147e-183">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="5147e-184">Posiadanie dużej ilości wolnego miejsca w generacji 0 nie jest problemem, ponieważ jest to generacja, w której przydzielono nowe obiekty.</span><span class="sxs-lookup"><span data-stu-id="5147e-184">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="5147e-185">Fragmentacja zawsze występuje w stercie dużego obiektu, ponieważ nie jest kompaktowana.</span><span class="sxs-lookup"><span data-stu-id="5147e-185">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="5147e-186">Wolne obiekty, które są przyległe, są naturalnie zwijane do pojedynczej przestrzeni w celu zaspokojenia żądań alokacji dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5147e-186">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="5147e-187">Fragmentacja może stać się problemem w przypadku generacji 1 i generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5147e-187">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="5147e-188">Jeśli te generacje mają dużą ilość wolnego miejsca po wyrzucaniu elementów bezużytecznych, użycie obiektu aplikacji może wymagać modyfikacji i należy rozważyć ponowne obliczenie okresu istnienia długoterminowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5147e-188">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="5147e-189">Nadmierne Przypinanie obiektów może zwiększyć fragmentację.</span><span class="sxs-lookup"><span data-stu-id="5147e-189">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="5147e-190">Jeśli fragmentacja jest wysoka, zbyt wiele obiektów mogło być przypięty.</span><span class="sxs-lookup"><span data-stu-id="5147e-190">If fragmentation is high, too many objects could have been pinned.</span></span>

<span data-ttu-id="5147e-191">Jeśli fragmentacja pamięci wirtualnej uniemożliwia dodanie segmentów przez moduł wyrzucania elementów bezużytecznych, przyczyny mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="5147e-191">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="5147e-192">Częste ładowanie i zwalnianie wielu małych zestawów.</span><span class="sxs-lookup"><span data-stu-id="5147e-192">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="5147e-193">Przechowywanie zbyt wielu odwołań do obiektów COM podczas współdziałania z niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="5147e-193">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="5147e-194">Tworzenie dużych obiektów przejściowych, co sprawia, że sterta dużych obiektów często przydziela i zwalnia segmenty sterty.</span><span class="sxs-lookup"><span data-stu-id="5147e-194">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="5147e-195">W przypadku hostowania środowiska CLR aplikacja może zażądać, aby moduł zbierający elementy bezużyteczne zachował swoje segmenty.</span><span class="sxs-lookup"><span data-stu-id="5147e-195">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="5147e-196">Zmniejsza to częstotliwość alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="5147e-196">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="5147e-197">Jest to realizowane przy użyciu flagi STARTUP_HOARD_GC_VM w [Wyliczeniu STARTUP_FLAGS](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5147e-197">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="5147e-198">Sprawdzanie wydajności</span><span class="sxs-lookup"><span data-stu-id="5147e-198">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="5147e-199">Określ ilość wolnego miejsca w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="5147e-199">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="5147e-200">Określ liczbę przypiętych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5147e-200">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="5147e-201">Jeśli uważasz, że nie istnieje uzasadniona przyczyna fragmentacji, skontaktuj się z działem obsługi klienta i pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5147e-201">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="5147e-202">Problem: wstrzymanie odzyskiwania pamięci jest zbyt długie</span><span class="sxs-lookup"><span data-stu-id="5147e-202">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="5147e-203">Wyrzucanie elementów bezużytecznych działa w czasie rzeczywistym, więc aplikacja musi być w stanie tolerować pewne przerwy.</span><span class="sxs-lookup"><span data-stu-id="5147e-203">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="5147e-204">Kryterium dla miękkiego czasu rzeczywistego jest to, że 95% operacji musi zakończyć się w czasie.</span><span class="sxs-lookup"><span data-stu-id="5147e-204">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="5147e-205">W współbieżnym wyrzucaniu elementów bezużytecznych, zarządzane wątki można uruchamiać w kolekcji, co oznacza, że pauzy są bardzo minimalne.</span><span class="sxs-lookup"><span data-stu-id="5147e-205">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="5147e-206">Tymczasowe wyrzucanie elementów bezużytecznych (generacji 0 i 1) ostatnie tylko kilka milisekund, więc zmniejszenie wstrzymania nie jest zazwyczaj możliwe.</span><span class="sxs-lookup"><span data-stu-id="5147e-206">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="5147e-207">Można jednak zmniejszyć wstrzymania w kolekcjach generacji 2, zmieniając wzorzec żądań alokacji przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="5147e-207">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="5147e-208">Innym, dokładniej, metoda polega na użyciu [zdarzeń ETW wyrzucania elementów bezużytecznych](../../framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="5147e-208">Another, more accurate, method is to use [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="5147e-209">Chronometraż kolekcji można znaleźć, dodając różnice czasu dla sekwencji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5147e-209">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="5147e-210">Cała sekwencja kolekcji obejmuje zawieszenie aparatu wykonywania, samego wyrzucania elementów bezużytecznych i wznowienie aparatu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5147e-210">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="5147e-211">Możesz użyć powiadomień o wykorzystaniu [elementów bezużytecznych](notifications.md) , aby określić, czy serwer ma kolekcję generacji 2 i czy żądania przekierowania na inny serwer mogą ułatwić rozwiązywanie problemów z wstrzymywaniem.</span><span class="sxs-lookup"><span data-stu-id="5147e-211">You can use [Garbage Collection Notifications](notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="5147e-212">Sprawdzanie wydajności</span><span class="sxs-lookup"><span data-stu-id="5147e-212">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="5147e-213">Określ długość czasu w wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-213">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="5147e-214">Określ, co spowodowało wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-214">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="5147e-215">Problem: generacja 0 jest zbyt duża</span><span class="sxs-lookup"><span data-stu-id="5147e-215">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="5147e-216">Generacja 0 może mieć większą liczbę obiektów w systemie 64-bitowym, szczególnie w przypadku używania odzyskiwania pamięci serwera zamiast wyrzucania elementów bezużytecznych stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="5147e-216">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="5147e-217">Wynika to z faktu, że próg wyzwalający wyrzucanie elementów bezużytecznych generacji 0 jest wyższy w tych środowiskach, a kolekcje generacji 0 mogą być znacznie większe.</span><span class="sxs-lookup"><span data-stu-id="5147e-217">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="5147e-218">Zwiększona wydajność, gdy aplikacja przydzieli więcej pamięci przed wyzwoleniem wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-218">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="5147e-219">Problem: użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt duże</span><span class="sxs-lookup"><span data-stu-id="5147e-219">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="5147e-220">Użycie procesora CPU będzie wysokie podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-220">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="5147e-221">Jeśli w wyrzucaniu elementów bezużytecznych jest dużo czasu procesu, liczba kolekcji jest zbyt częste lub kolekcja jest zbyt długa.</span><span class="sxs-lookup"><span data-stu-id="5147e-221">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="5147e-222">Zwiększona szybkość alokacji obiektów na stercie zarządzanym powoduje częstsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-222">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="5147e-223">Zmniejszenie szybkości alokacji zmniejsza częstotliwość wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-223">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="5147e-224">Stawki przydziału można monitorować przy użyciu `Allocated Bytes/second` licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="5147e-224">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="5147e-225">Aby uzyskać więcej informacji, zobacz [liczniki wydajności w .NET Framework](../../framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="5147e-225">For more information, see [Performance Counters in the .NET Framework](../../framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="5147e-226">Czas trwania kolekcji jest przede wszystkim czynnikiem liczby obiektów, które przeżyły po alokacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-226">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="5147e-227">Moduł wyrzucania elementów bezużytecznych musi przekroczyć dużą ilość pamięci, jeśli wiele obiektów pozostanie do zebrania.</span><span class="sxs-lookup"><span data-stu-id="5147e-227">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="5147e-228">Prace do kompaktowania pozostałego czasu są czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="5147e-228">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="5147e-229">Aby określić liczbę obiektów obsłużonych podczas zbierania, należy ustawić punkt przerwania w debugerze na końcu wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-229">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="5147e-230">Sprawdzanie wydajności</span><span class="sxs-lookup"><span data-stu-id="5147e-230">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="5147e-231">Ustal, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-231">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="5147e-232">Ustaw punkt przerwania na końcu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-232">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="5147e-233">Wskazówki dotyczące rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="5147e-233">Troubleshooting Guidelines</span></span>

<span data-ttu-id="5147e-234">W tej sekcji opisano wskazówki, które należy wziąć pod uwagę podczas rozpoczynania badań.</span><span class="sxs-lookup"><span data-stu-id="5147e-234">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="5147e-235">Stacja robocza lub odzyskiwanie pamięci serwera</span><span class="sxs-lookup"><span data-stu-id="5147e-235">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="5147e-236">Ustal, czy używasz poprawnego typu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-236">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="5147e-237">Jeśli aplikacja używa wielu wątków i wystąpień obiektów, użyj wyrzucania elementów bezużytecznych serwera zamiast wyrzucania elementów bezużytecznych stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="5147e-237">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="5147e-238">Odzyskiwanie pamięci serwera działa w wielu wątkach, podczas gdy wyrzucanie elementów bezużytecznych stacji roboczej wymaga wielu wystąpień aplikacji do uruchamiania własnych wątków odzyskiwania pamięci i konkurowania na czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="5147e-238">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="5147e-239">Aplikacja o niskim obciążeniu i wykonująca zadania rzadko w tle, taka jak usługa, może użyć wyrzucania elementów bezużytecznych stacji roboczej z wyłączonym współbieżnym wyrzucaniem elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-239">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="5147e-240">Kiedy mierzyć rozmiar sterty zarządzanej</span><span class="sxs-lookup"><span data-stu-id="5147e-240">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="5147e-241">Jeśli nie korzystasz z profilera, konieczne będzie ustanowienie spójnego wzorca pomiarów w celu efektywnego zdiagnozowania problemów z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="5147e-241">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="5147e-242">Aby określić harmonogram, należy wziąć pod uwagę następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="5147e-242">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="5147e-243">Jeśli mierzy się po wyrzucaniu elementów bezużytecznych generacji 2, cały stos zarządzany będzie wolny od elementów bezużytecznych (martwych obiektów).</span><span class="sxs-lookup"><span data-stu-id="5147e-243">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="5147e-244">W przypadku mierzenia natychmiast po wyrzucaniu elementów bezużytecznych generacji 0 obiekty w generacjach 1 i 2 nie zostaną jeszcze zebrane.</span><span class="sxs-lookup"><span data-stu-id="5147e-244">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="5147e-245">Jeśli miara jest mierzona bezpośrednio przed wyrzucaniem elementów bezużytecznych, po rozpoczęciu wyrzucania elementów bezużytecznych należy mierzyć możliwie tyle przydziału.</span><span class="sxs-lookup"><span data-stu-id="5147e-245">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="5147e-246">Pomiar podczas wyrzucania elementów bezużytecznych jest problematyczny, ponieważ struktury danych modułu wyrzucania elementów bezużytecznych są w nieprawidłowym stanie do przechodzenia i mogą nie być w stanie uzyskać pełnych wyników.</span><span class="sxs-lookup"><span data-stu-id="5147e-246">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="5147e-247">Jest to celowe.</span><span class="sxs-lookup"><span data-stu-id="5147e-247">This is by design.</span></span>

- <span data-ttu-id="5147e-248">W przypadku korzystania z wyrzucania elementów bezużytecznych stacji roboczej z współbieżnym wyrzucaniem elementów bezużytecznych obiekty odzyskiwane nie są kompaktne, dzięki czemu rozmiar sterty może być taki sam lub większy (fragmentacja może sprawiać, że jest większa).</span><span class="sxs-lookup"><span data-stu-id="5147e-248">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="5147e-249">Współbieżne wyrzucanie elementów bezużytecznych w generacji 2 jest opóźnione, gdy obciążenie pamięci fizycznej jest zbyt wysokie.</span><span class="sxs-lookup"><span data-stu-id="5147e-249">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="5147e-250">Poniższa procedura opisuje, jak ustawić punkt przerwania, aby można było zmierzyć stertę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="5147e-250">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="5147e-251">Aby ustawić punkt przerwania na końcu odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-251">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="5147e-252">W programie WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5147e-252">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="5147e-253">**mscorwks BP! WKS:: GCHeap:: RestartEE "j (dwo (mscorwks! WKS:: GCHeap:: GcCondemnedGeneration) = = 2) "KB"; " g ""**</span><span class="sxs-lookup"><span data-stu-id="5147e-253">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="5147e-254">gdzie **GcCondemnedGeneration** jest ustawiona na żądaną generację.</span><span class="sxs-lookup"><span data-stu-id="5147e-254">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="5147e-255">To polecenie wymaga symboli prywatnych.</span><span class="sxs-lookup"><span data-stu-id="5147e-255">This command requires private symbols.</span></span>

  <span data-ttu-id="5147e-256">To polecenie wymusza przerwanie, jeśli **RestartEE** jest wykonywane po odbraniu obiektów generacji 2 do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-256">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="5147e-257">W wyrzucaniu elementów bezużytecznych serwera tylko jedno wywołanie wątku **RestartEE**, więc punkt przerwania wystąpi tylko raz podczas wyrzucania elementów bezużytecznych generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5147e-257">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

## <a name="performance-check-procedures"></a><span data-ttu-id="5147e-258">Procedury sprawdzania wydajności</span><span class="sxs-lookup"><span data-stu-id="5147e-258">Performance Check Procedures</span></span>

<span data-ttu-id="5147e-259">W tej sekcji opisano następujące procedury umożliwiające odizolowanie przyczyny problemu z wydajnością:</span><span class="sxs-lookup"><span data-stu-id="5147e-259">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="5147e-260">Ustal, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-260">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="5147e-261">Ustal, czy jest zarządzany wyjątek braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-261">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="5147e-262">Określ ilość pamięci wirtualnej, która może być zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="5147e-262">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="5147e-263">Należy określić, czy jest dostępna wystarczająca ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="5147e-263">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="5147e-264">Określ ilość pamięci, która jest zatwierdzana przez stertę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="5147e-264">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="5147e-265">Określ ilość pamięci, jaką rezerwuje sterta zarządza.</span><span class="sxs-lookup"><span data-stu-id="5147e-265">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="5147e-266">Określ duże obiekty w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5147e-266">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="5147e-267">Określanie odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="5147e-267">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="5147e-268">Ustal, czy finalizator został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5147e-268">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="5147e-269">Ustal, czy istnieją obiekty oczekujące na sfinalizowanie.</span><span class="sxs-lookup"><span data-stu-id="5147e-269">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="5147e-270">Określ ilość wolnego miejsca w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="5147e-270">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="5147e-271">Określ liczbę przypiętych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5147e-271">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="5147e-272">Określ długość czasu w wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-272">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="5147e-273">Określ, co wyzwoliło wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-273">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="5147e-274">Ustal, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-274">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="5147e-275">Aby określić, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="5147e-275">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="5147e-276">Zapoznaj się z poniższymi dwoma licznikami wydajności pamięci:</span><span class="sxs-lookup"><span data-stu-id="5147e-276">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="5147e-277">**Czas (%) w usłudze GC**.</span><span class="sxs-lookup"><span data-stu-id="5147e-277">**% Time in GC**.</span></span> <span data-ttu-id="5147e-278">Wyświetla procent czasu, który upłynął podczas wykonywania wyrzucania elementów bezużytecznych po ostatnim cyklu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-278">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="5147e-279">Użyj tego licznika, aby określić, czy moduł wyrzucania elementów bezużytecznych poświęca zbyt dużo czasu na udostępnienie zarządzanej przestrzeni sterty.</span><span class="sxs-lookup"><span data-stu-id="5147e-279">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="5147e-280">Jeśli czas spędzony na wyrzucaniu elementów bezużytecznych jest stosunkowo niski, może to wskazywać na problem z zasobem poza zarządzaną stertą.</span><span class="sxs-lookup"><span data-stu-id="5147e-280">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="5147e-281">Ten licznik może nie być dokładny, gdy jest wykorzystywane współbieżne lub w tle odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-281">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="5147e-282">Liczba **bajtów zadeklarowanych łącznie**.</span><span class="sxs-lookup"><span data-stu-id="5147e-282">**# Total committed Bytes**.</span></span> <span data-ttu-id="5147e-283">Wyświetla ilość pamięci wirtualnej aktualnie zatwierdzonej przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-283">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="5147e-284">Użyj tego licznika, aby określić, czy pamięć wykorzystywana przez moduł wyrzucania elementów bezużytecznych jest nadmierną częścią pamięci używanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="5147e-284">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="5147e-285">Większość liczników wydajności pamięci jest aktualizowanych na końcu każdego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-285">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="5147e-286">W związku z tym mogą nie odzwierciedlać bieżących warunków, o których chcesz uzyskać informacje.</span><span class="sxs-lookup"><span data-stu-id="5147e-286">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="5147e-287">Aby określić, czy wyjątek braku pamięci jest zarządzany</span><span class="sxs-lookup"><span data-stu-id="5147e-287">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="5147e-288">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz polecenie Print Exception (**PE**):</span><span class="sxs-lookup"><span data-stu-id="5147e-288">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="5147e-289">**! PE**</span><span class="sxs-lookup"><span data-stu-id="5147e-289">**!pe**</span></span>

    <span data-ttu-id="5147e-290">Jeśli wyjątek jest zarządzany, <xref:System.OutOfMemoryException> jest wyświetlany jako typ wyjątku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5147e-290">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="5147e-291">Jeśli dane wyjściowe nie określają wyjątku, należy określić, z którego wątku jest wykonywany wyjątek braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-291">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="5147e-292">Wpisz następujące polecenie w debugerze, aby pokazać wszystkie wątki ze stosami wywołań:</span><span class="sxs-lookup"><span data-stu-id="5147e-292">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="5147e-293">**~\*bazy**</span><span class="sxs-lookup"><span data-stu-id="5147e-293">**~\*kb**</span></span>

    <span data-ttu-id="5147e-294">Wątek ze stosem, który zawiera wywołania wyjątku jest wskazywany przez `RaiseTheException` argument.</span><span class="sxs-lookup"><span data-stu-id="5147e-294">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="5147e-295">Jest to obiekt wyjątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5147e-295">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="5147e-296">Poniższe polecenie służy do zrzutu zagnieżdżonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5147e-296">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="5147e-297">**! PE — zagnieżdżone**</span><span class="sxs-lookup"><span data-stu-id="5147e-297">**!pe -nested**</span></span>

    <span data-ttu-id="5147e-298">Jeśli nie występują żadne wyjątki, wyjątek braku pamięci pochodzący z kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5147e-298">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="5147e-299">Aby określić ilość pamięci wirtualnej, którą można zarezerwować</span><span class="sxs-lookup"><span data-stu-id="5147e-299">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="5147e-300">W programie WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby uzyskać największy wolny region:</span><span class="sxs-lookup"><span data-stu-id="5147e-300">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="5147e-301">**! Address — podsumowanie**</span><span class="sxs-lookup"><span data-stu-id="5147e-301">**!address -summary**</span></span>

  <span data-ttu-id="5147e-302">Jest wyświetlany największy wolny region, jak pokazano w poniższych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5147e-302">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="5147e-303">W tym przykładzie rozmiar największego wolnego regionu wynosi około 24000 KB (3A980 w formacie szesnastkowym).</span><span class="sxs-lookup"><span data-stu-id="5147e-303">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="5147e-304">Ten region jest znacznie mniejszy niż to, co wymagają Moduł wyrzucania elementów bezużytecznych dla segmentu.</span><span class="sxs-lookup"><span data-stu-id="5147e-304">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="5147e-305">-lub-</span><span class="sxs-lookup"><span data-stu-id="5147e-305">-or-</span></span>

- <span data-ttu-id="5147e-306">Użyj **vmstat** polecenia:</span><span class="sxs-lookup"><span data-stu-id="5147e-306">Use the **vmstat** command:</span></span>

  <span data-ttu-id="5147e-307">**! vmstat**</span><span class="sxs-lookup"><span data-stu-id="5147e-307">**!vmstat**</span></span>

  <span data-ttu-id="5147e-308">Największy wolny region jest największą wartością w kolumnie MAXIMUM, jak pokazano w poniższych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5147e-308">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

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

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="5147e-309">Aby określić, czy jest dostępna wystarczająca ilość pamięci fizycznej</span><span class="sxs-lookup"><span data-stu-id="5147e-309">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="5147e-310">Uruchom Menedżera zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5147e-310">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="5147e-311">Na karcie **wydajność** Przyjrzyj się wartości zatwierdzonej.</span><span class="sxs-lookup"><span data-stu-id="5147e-311">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="5147e-312">(W systemie Windows 7 zapoznaj się z tematem **zatwierdzenie (KB)** w **grupie system**.)</span><span class="sxs-lookup"><span data-stu-id="5147e-312">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="5147e-313">Jeśli **Suma** zbliża się do **limitu**, zaczyna brakować pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="5147e-313">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="5147e-314">Aby określić ilość pamięci, która jest zatwierdzana przez stertę zarządzaną</span><span class="sxs-lookup"><span data-stu-id="5147e-314">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="5147e-315">Użyj `# Total committed bytes` licznika wydajności pamięci, aby uzyskać liczbę bajtów, które są zatwierdzane przez stertę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="5147e-315">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="5147e-316">Moduł zbierający elementy bezużyteczne zatwierdza fragmenty segmentów w razie konieczności, nie wszystkie w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="5147e-316">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="5147e-317">Nie należy używać `# Bytes in all Heaps` licznika wydajności, ponieważ nie reprezentuje rzeczywiste użycie pamięci przez stertę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="5147e-317">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="5147e-318">Rozmiar generacji jest uwzględniany w tej wartości i jest w rzeczywistości rozmiarem jego progu, czyli rozmiarem, który wywołuje wyrzucanie elementów bezużytecznych, jeśli generacja jest zapełniona obiektami.</span><span class="sxs-lookup"><span data-stu-id="5147e-318">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="5147e-319">W związku z tym ta wartość jest zwykle równa zero.</span><span class="sxs-lookup"><span data-stu-id="5147e-319">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="5147e-320">Aby określić ilość pamięci, jaką rezerwuje sterta zarządza</span><span class="sxs-lookup"><span data-stu-id="5147e-320">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="5147e-321">Użyj `# Total reserved bytes` licznika wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-321">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="5147e-322">Moduł wyrzucania elementów bezużytecznych rezerwuje pamięć w segmentach i można określić, gdzie zostanie uruchomiony segment przy użyciu polecenia **eeheap** .</span><span class="sxs-lookup"><span data-stu-id="5147e-322">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="5147e-323">Chociaż można określić ilość pamięci przydzielanej przez moduł wyrzucania elementów bezużytecznych dla każdego segmentu, rozmiar segmentu jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami.</span><span class="sxs-lookup"><span data-stu-id="5147e-323">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="5147e-324">Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.</span><span class="sxs-lookup"><span data-stu-id="5147e-324">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="5147e-325">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5147e-325">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="5147e-326">**! eeheap — GC**</span><span class="sxs-lookup"><span data-stu-id="5147e-326">**!eeheap -gc**</span></span>

  <span data-ttu-id="5147e-327">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="5147e-327">The result is as follows.</span></span>

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

  <span data-ttu-id="5147e-328">Adresy wskazywane przez "segment" są adresami początkowymi segmentów.</span><span class="sxs-lookup"><span data-stu-id="5147e-328">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="5147e-329">Aby określić duże obiekty w generacji 2</span><span class="sxs-lookup"><span data-stu-id="5147e-329">To determine large objects in generation 2</span></span>

- <span data-ttu-id="5147e-330">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5147e-330">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="5147e-331">**! DumpHeap — stat**</span><span class="sxs-lookup"><span data-stu-id="5147e-331">**!dumpheap –stat**</span></span>

  <span data-ttu-id="5147e-332">Jeśli zarządzana sterta jest duża, **DumpHeap** może chwilę potrwać.</span><span class="sxs-lookup"><span data-stu-id="5147e-332">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="5147e-333">Możesz rozpocząć analizowanie z ostatnich kilku wierszy danych wyjściowych, ponieważ zawierają one listę obiektów, które używają najwięcej miejsca.</span><span class="sxs-lookup"><span data-stu-id="5147e-333">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="5147e-334">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5147e-334">For example:</span></span>

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

  <span data-ttu-id="5147e-335">Ostatni wymieniony obiekt jest ciągiem i zajmuje najwięcej miejsca.</span><span class="sxs-lookup"><span data-stu-id="5147e-335">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="5147e-336">Możesz sprawdzić swoją aplikację, aby zobaczyć, jak można zoptymalizować obiekty ciągu.</span><span class="sxs-lookup"><span data-stu-id="5147e-336">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="5147e-337">Aby wyświetlić ciągi z zakresu od 150 do 200 bajtów, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5147e-337">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="5147e-338">**! DumpHeap-Type System. String — min 150 — maks 200**</span><span class="sxs-lookup"><span data-stu-id="5147e-338">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="5147e-339">Poniżej przedstawiono przykładowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="5147e-339">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="5147e-340">Użycie liczby całkowitej zamiast ciągu dla identyfikatora może być bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="5147e-340">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="5147e-341">Jeśli ten sam ciąg jest powtarzany tysiące razy, weź pod uwagę ciąg InterNIC.</span><span class="sxs-lookup"><span data-stu-id="5147e-341">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="5147e-342">Aby uzyskać więcej informacji na temat informowania o ciągach, zobacz temat referencyjny dla <xref:System.String.Intern%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5147e-342">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="5147e-343">Aby określić odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="5147e-343">To determine references to objects</span></span>

- <span data-ttu-id="5147e-344">W programie WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby wyświetlić listę odwołań do obiektów:</span><span class="sxs-lookup"><span data-stu-id="5147e-344">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="5147e-345">**!gcroot**</span><span class="sxs-lookup"><span data-stu-id="5147e-345">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="5147e-346">Aby określić odwołania dla określonego obiektu, Dołącz adres:</span><span class="sxs-lookup"><span data-stu-id="5147e-346">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="5147e-347">**!gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="5147e-347">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="5147e-348">Elementy główne znalezione na stosach mogą być fałszywie pozytywne.</span><span class="sxs-lookup"><span data-stu-id="5147e-348">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="5147e-349">Aby uzyskać więcej informacji, użyj polecenia `!help gcroot` .</span><span class="sxs-lookup"><span data-stu-id="5147e-349">For more information, use the command `!help gcroot`.</span></span>

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

  <span data-ttu-id="5147e-350">Ukończenie polecenia **gcroot** może zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="5147e-350">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="5147e-351">Wszelkie obiekty, które nie są odzyskiwane przez wyrzucanie elementów bezużytecznych, są obiektem aktywnym.</span><span class="sxs-lookup"><span data-stu-id="5147e-351">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="5147e-352">Oznacza to, że część elementu głównego jest bezpośrednio lub pośrednio umieszczana na obiekcie, więc **gcroot** powinna zwracać informacje o ścieżce do obiektu.</span><span class="sxs-lookup"><span data-stu-id="5147e-352">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="5147e-353">Należy sprawdzić, czy wykresy zostały zwrócone, i sprawdzić, dlaczego te obiekty nadal są przywoływane.</span><span class="sxs-lookup"><span data-stu-id="5147e-353">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="5147e-354">Aby określić, czy finalizator został uruchomiony</span><span class="sxs-lookup"><span data-stu-id="5147e-354">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="5147e-355">Uruchom program testowy, który zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5147e-355">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="5147e-356">Jeśli test rozwiąże problem, oznacza to, że moduł wyrzucania elementów bezużytecznych nie odzyskał obiektów, ponieważ finalizatory dla tych obiektów zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="5147e-356">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="5147e-357"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>Metoda umożliwia finalizatorom ukończenie zadań i rozwiązuje problem.</span><span class="sxs-lookup"><span data-stu-id="5147e-357">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="5147e-358">Aby określić, czy istnieją obiekty oczekujące na sfinalizowanie</span><span class="sxs-lookup"><span data-stu-id="5147e-358">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="5147e-359">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5147e-359">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="5147e-360">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="5147e-360">**!finalizequeue**</span></span>

    <span data-ttu-id="5147e-361">Przyjrzyj się liczbie obiektów, które są gotowe do finalizacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-361">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="5147e-362">Jeśli liczba jest wysoka, należy zapoznać się z tym, dlaczego tacy finalizatory nie mogą postępować w ogóle lub nie mogą postępować wystarczająco szybko.</span><span class="sxs-lookup"><span data-stu-id="5147e-362">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="5147e-363">Aby uzyskać dane wyjściowe wątków, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5147e-363">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="5147e-364">**wątki — specjalne**</span><span class="sxs-lookup"><span data-stu-id="5147e-364">**threads -special**</span></span>

    <span data-ttu-id="5147e-365">To polecenie zapewnia dane wyjściowe, takie jak poniższe.</span><span class="sxs-lookup"><span data-stu-id="5147e-365">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="5147e-366">Wątek finalizatora wskazuje, który finalizator, jeśli istnieje, jest obecnie uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="5147e-366">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="5147e-367">Gdy wątek finalizatora nie działa żadnych finalizatorów, oczekuje na zdarzenie, aby je wypowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="5147e-367">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="5147e-368">Większość czasu zobaczysz wątek finalizatora w tym stanie, ponieważ działa on w THREAD_HIGHEST_PRIORITY i będzie można zakończyć pracę finalizatorów, jeśli istnieją, bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="5147e-368">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="5147e-369">Aby określić ilość wolnego miejsca w zarządzanym stosie</span><span class="sxs-lookup"><span data-stu-id="5147e-369">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="5147e-370">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5147e-370">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="5147e-371">**! DumpHeap-Type Free-stat**</span><span class="sxs-lookup"><span data-stu-id="5147e-371">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="5147e-372">To polecenie wyświetla łączny rozmiar wszystkich wolnych obiektów na stercie zarządzanym, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5147e-372">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="5147e-373">Aby określić ilość wolnego miejsca w generacji 0, wpisz następujące polecenie, aby uzyskać informacje o zużyciu pamięci według generacji:</span><span class="sxs-lookup"><span data-stu-id="5147e-373">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="5147e-374">**! eeheap — GC**</span><span class="sxs-lookup"><span data-stu-id="5147e-374">**!eeheap -gc**</span></span>

  <span data-ttu-id="5147e-375">To polecenie wyświetla dane wyjściowe podobne do poniższego.</span><span class="sxs-lookup"><span data-stu-id="5147e-375">This command displays output similar to the following.</span></span> <span data-ttu-id="5147e-376">Ostatni wiersz przedstawia segment tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="5147e-376">The last line shows the ephemeral segment.</span></span>

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

- <span data-ttu-id="5147e-377">Oblicz miejsce używane przez generację 0:</span><span class="sxs-lookup"><span data-stu-id="5147e-377">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="5147e-378">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="5147e-378">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="5147e-379">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="5147e-379">The result is as follows.</span></span> <span data-ttu-id="5147e-380">Generacja 0 wynosi około 9 MB.</span><span class="sxs-lookup"><span data-stu-id="5147e-380">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="5147e-381">Następujące polecenie zrzuca wolne miejsce w zakresie generacji 0:</span><span class="sxs-lookup"><span data-stu-id="5147e-381">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="5147e-382">**! DumpHeap-Type Free-stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="5147e-382">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="5147e-383">Wynik jest następujący.</span><span class="sxs-lookup"><span data-stu-id="5147e-383">The result is as follows.</span></span>

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

  <span data-ttu-id="5147e-384">Te dane wyjściowe pokazują, że część generacji 0 sterty używa dla obiektów wartości 9 MB i ma 7 MB wolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="5147e-384">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="5147e-385">Ta analiza pokazuje zakres, do którego generacja 0 przyczynia się do fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-385">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="5147e-386">Ta ilość użycia sterty powinna być obniżona od łącznej kwoty jako przyczyny fragmentacji obiektów długoterminowych.</span><span class="sxs-lookup"><span data-stu-id="5147e-386">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="5147e-387">Aby określić liczbę przypiętych obiektów</span><span class="sxs-lookup"><span data-stu-id="5147e-387">To determine the number of pinned objects</span></span>

- <span data-ttu-id="5147e-388">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5147e-388">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="5147e-389">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="5147e-389">**!gchandles**</span></span>

  <span data-ttu-id="5147e-390">Wyświetlane dane statystyczne zawierają liczbę przypiętych dojść, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5147e-390">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="5147e-391">Aby określić długość czasu w wyrzucaniu elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="5147e-391">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="5147e-392">Przeanalizuj `% Time in GC` licznik wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-392">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="5147e-393">Wartość jest obliczana przy użyciu przykładowego interwału czasu.</span><span class="sxs-lookup"><span data-stu-id="5147e-393">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="5147e-394">Ponieważ liczniki są aktualizowane na końcu każdego wyrzucania elementów bezużytecznych, bieżąca próbka będzie miała taką samą wartość jak w poprzednim przykładzie, jeśli nie wystąpiły żadne kolekcje w interwale.</span><span class="sxs-lookup"><span data-stu-id="5147e-394">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="5147e-395">Czas zbierania jest uzyskiwany przez pomnożenie przykładowego czasu interwału z wartością procentową.</span><span class="sxs-lookup"><span data-stu-id="5147e-395">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="5147e-396">Poniższe dane pokazują cztery interwały próbkowania wynoszące dwie sekundy w przypadku studiów 8-sekundowych.</span><span class="sxs-lookup"><span data-stu-id="5147e-396">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="5147e-397">`Gen0`Kolumny, `Gen1` i `Gen2` zawierają liczbę wyrzucania elementów bezużytecznych, które wystąpiły w tym interwale dla tej generacji.</span><span class="sxs-lookup"><span data-stu-id="5147e-397">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="5147e-398">Te informacje nie są wyświetlane, gdy wystąpiło wyrzucanie elementów bezużytecznych, ale można określić liczbę wyrzucania elementów bezużytecznych, które wystąpiły w przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="5147e-398">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="5147e-399">Zakładając, że najgorszy przypadek, zbieranie elementów bezużytecznych dziesiątki generacji 0 zakończyło się na początku drugiego interwału, a zbieranie elementów bezużytecznych generacji 0 zakończyło się po upływie piątego interwału.</span><span class="sxs-lookup"><span data-stu-id="5147e-399">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="5147e-400">Czas między końcem dziesiątego i końca jedenastego wyrzucania elementów bezużytecznych wynosi około 2 sekundy, a licznik wydajności pokazuje 3%, więc czas trwania wyrzucania elementów bezużytecznych generacji 0 wynosi (2 sekundy \* 3% = 60ms).</span><span class="sxs-lookup"><span data-stu-id="5147e-400">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="5147e-401">W tym przykładzie wystąpiły 5 okresów.</span><span class="sxs-lookup"><span data-stu-id="5147e-401">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="5147e-402">Druga generacja elementów bezużytecznych generacji 2 rozpoczęła się w trzecim interwale i została zakończona z piątym interwałem.</span><span class="sxs-lookup"><span data-stu-id="5147e-402">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="5147e-403">Przy założeniu najgorszego przypadku ostatnie wyrzucanie elementów bezużytecznych dotyczyło kolekcji generacji 0, która została zakończona na początku drugiego interwału, a wyrzucanie elementów bezużytecznych generacji 2 zakończyło się z końcem piątego interwału.</span><span class="sxs-lookup"><span data-stu-id="5147e-403">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="5147e-404">W związku z tym czas między końcem wyrzucania elementów bezużytecznych generacji 0 a końcem wyrzucania elementów bezużytecznych generacji 2 wynosi 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="5147e-404">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="5147e-405">Ponieważ `% Time in GC` licznik jest 20%, maksymalna ilość czasu, jaką może pobrać wyrzucanie elementów bezużytecznych generacji 2, to (4 sekundy \* 20% = 800ms).</span><span class="sxs-lookup"><span data-stu-id="5147e-405">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="5147e-406">Alternatywnie można określić długość wyrzucania elementów bezużytecznych za pomocą [zdarzeń ETW wyrzucania elementów](../../framework/performance/garbage-collection-etw-events.md)bezużytecznych i analizować informacje w celu określenia czasu trwania odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="5147e-406">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="5147e-407">Na przykład następujące dane przedstawiają sekwencję zdarzeń, która wystąpiła podczas niewspółbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-407">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

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

  <span data-ttu-id="5147e-408">Wstrzymanie wątku zarządzanego zajęło 26us ( `GCSuspendEEEnd` – `GCSuspendEEBegin_V1` ).</span><span class="sxs-lookup"><span data-stu-id="5147e-408">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="5147e-409">Rzeczywista wyrzucanie elementów bezużytecznych zajęło MS ( `GCEnd_V1` – `GCStart_V1` ).</span><span class="sxs-lookup"><span data-stu-id="5147e-409">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="5147e-410">Wznowienie zarządzanych wątków trwało 21us ( `GCRestartEEEnd` – `GCRestartEEBegin` ).</span><span class="sxs-lookup"><span data-stu-id="5147e-410">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="5147e-411">Poniższe dane wyjściowe przedstawiają przykład do wyrzucania elementów bezużytecznych w tle, a także zawierają pola procesu, wątku i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5147e-411">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="5147e-412">(Nie wszystkie dane są wyświetlane).</span><span class="sxs-lookup"><span data-stu-id="5147e-412">(Not all data is shown.)</span></span>

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

  <span data-ttu-id="5147e-413">`GCStart_V1`Zdarzenie w 42504816 wskazuje, że jest to wyrzucanie elementów bezużytecznych w tle, ponieważ ostatnie pole to `1` .</span><span class="sxs-lookup"><span data-stu-id="5147e-413">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="5147e-414">To nie spowoduje odrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-414">This becomes garbage collection No.</span></span> <span data-ttu-id="5147e-415">102019.</span><span class="sxs-lookup"><span data-stu-id="5147e-415">102019.</span></span>

  <span data-ttu-id="5147e-416">`GCStart`Zdarzenie występuje, ponieważ istnieje potrzeba tymczasowej wyrzucania elementów bezużytecznych przed rozpoczęciem wyrzucania elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="5147e-416">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="5147e-417">To nie spowoduje odrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-417">This becomes garbage collection No.</span></span> <span data-ttu-id="5147e-418">102020.</span><span class="sxs-lookup"><span data-stu-id="5147e-418">102020.</span></span>

  <span data-ttu-id="5147e-419">O 42514170, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-419">At 42514170, garbage collection No.</span></span> <span data-ttu-id="5147e-420">102020 kończy się.</span><span class="sxs-lookup"><span data-stu-id="5147e-420">102020 finishes.</span></span> <span data-ttu-id="5147e-421">Zarządzane wątki są ponownie uruchamiane w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="5147e-421">The managed threads are restarted at this point.</span></span> <span data-ttu-id="5147e-422">Jest to wykonywane w wątku 4372, który wyzwolił to wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="5147e-422">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="5147e-423">W wątku 4744 następuje zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="5147e-423">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="5147e-424">Jest to jedyny czas, w którym wyrzucanie elementów bezużytecznych w tle ma wstrzymywać zarządzane wątki.</span><span class="sxs-lookup"><span data-stu-id="5147e-424">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="5147e-425">Ten czas trwania jest około 99ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="5147e-425">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="5147e-426">`GCEnd`Zdarzenie dla wyrzucania elementów bezużytecznych w tle ma wartość 89931423.</span><span class="sxs-lookup"><span data-stu-id="5147e-426">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="5147e-427">Oznacza to, że wyrzucanie elementów bezużytecznych w tle zostało ostatnio za47seconds ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="5147e-427">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="5147e-428">Gdy zarządzane wątki są uruchomione, można zobaczyć dowolną liczbę tymczasowych kolekcji elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-428">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="5147e-429">Aby określić, które wyzwolone odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-429">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="5147e-430">W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie, aby wyświetlić wszystkie wątki z stosami wywołań:</span><span class="sxs-lookup"><span data-stu-id="5147e-430">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="5147e-431">**~\*bazy**</span><span class="sxs-lookup"><span data-stu-id="5147e-431">**~\*kb**</span></span>

  <span data-ttu-id="5147e-432">To polecenie wyświetla dane wyjściowe podobne do poniższego.</span><span class="sxs-lookup"><span data-stu-id="5147e-432">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="5147e-433">Jeśli wyrzucanie elementów bezużytecznych zostało spowodowane przez powiadomienie o niskim poziomie pamięci z systemu operacyjnego, stos wywołań jest podobny, z tą różnicą, że wątek jest wątkiem finalizatora.</span><span class="sxs-lookup"><span data-stu-id="5147e-433">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="5147e-434">Wątek finalizatora pobiera asynchroniczne powiadomienie o niskiej ilości pamięci i wywołuje wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5147e-434">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="5147e-435">Jeśli wyrzucanie elementów bezużytecznych zostało spowodowane przez alokację pamięci, stos pojawia się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5147e-435">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

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

  <span data-ttu-id="5147e-436">Chwilowe wywołania pomocnika ( `JIT_New*` ) `GCHeap::GarbageCollectGeneration` .</span><span class="sxs-lookup"><span data-stu-id="5147e-436">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="5147e-437">Jeśli okaże się, że wyrzucanie elementów bezużytecznych generacji 2 jest spowodowane przez przydziały, należy określić, które obiekty są zbierane przez wyrzucanie elementów bezużytecznych generacji 2 i jak można je uniknąć.</span><span class="sxs-lookup"><span data-stu-id="5147e-437">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="5147e-438">Oznacza to, że chcesz określić różnicę między początkiem i końcem wyrzucania elementów bezużytecznych generacji 2 oraz obiektami, które spowodowały wygenerowanie kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5147e-438">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="5147e-439">Na przykład wpisz następujące polecenie w debugerze, aby wyświetlić początek kolekcji generacji 2:</span><span class="sxs-lookup"><span data-stu-id="5147e-439">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="5147e-440">**! DumpHeap — stat**</span><span class="sxs-lookup"><span data-stu-id="5147e-440">**!dumpheap –stat**</span></span>

  <span data-ttu-id="5147e-441">Przykładowe dane wyjściowe (w skrócie, aby pokazać obiekty, które używają najwięcej spacji):</span><span class="sxs-lookup"><span data-stu-id="5147e-441">Example output (abridged to show the objects that use the most space):</span></span>

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

  <span data-ttu-id="5147e-442">Powtórz polecenie na końcu generacji 2:</span><span class="sxs-lookup"><span data-stu-id="5147e-442">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="5147e-443">**! DumpHeap — stat**</span><span class="sxs-lookup"><span data-stu-id="5147e-443">**!dumpheap –stat**</span></span>

  <span data-ttu-id="5147e-444">Przykładowe dane wyjściowe (w skrócie, aby pokazać obiekty, które używają najwięcej spacji):</span><span class="sxs-lookup"><span data-stu-id="5147e-444">Example output (abridged to show the objects that use the most space):</span></span>

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

  <span data-ttu-id="5147e-445">`double[]`Obiekty zniknęły z końca danych wyjściowych, co oznacza, że zostały zebrane.</span><span class="sxs-lookup"><span data-stu-id="5147e-445">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="5147e-446">Te obiekty są uwzględniane przez około 70 MB.</span><span class="sxs-lookup"><span data-stu-id="5147e-446">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="5147e-447">Pozostałe obiekty nie zmieniły się.</span><span class="sxs-lookup"><span data-stu-id="5147e-447">The remaining objects did not change much.</span></span> <span data-ttu-id="5147e-448">W związku z tym te `double[]` obiekty były przyczyną przyczyny wyrzucania elementów bezużytecznych generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5147e-448">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="5147e-449">Następnym krokiem jest określenie, dlaczego `double[]` obiekty znajdują się tam i dlaczego zapadły.</span><span class="sxs-lookup"><span data-stu-id="5147e-449">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="5147e-450">Możesz polecić deweloperowi kodu, z którego pochodzą te obiekty, lub użyć polecenia **gcroot** .</span><span class="sxs-lookup"><span data-stu-id="5147e-450">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="5147e-451">Aby określić, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="5147e-451">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="5147e-452">Należy skorelować `% Time in GC` wartość licznika wydajności pamięci z czasem przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="5147e-452">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="5147e-453">Jeśli `% Time in GC` wartość zostanie nadana w tym samym czasie co czas procesu, wyrzucanie elementów bezużytecznych powoduje wysokie użycie procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="5147e-453">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="5147e-454">W przeciwnym razie należy profilować aplikację, aby znaleźć miejsce wystąpienia wysokiego użycia.</span><span class="sxs-lookup"><span data-stu-id="5147e-454">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="5147e-455">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5147e-455">See also</span></span>

- [<span data-ttu-id="5147e-456">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="5147e-456">Garbage Collection</span></span>](index.md)
