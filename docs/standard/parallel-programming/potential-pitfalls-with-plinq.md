---
title: Potencjalne pułapki z PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 44f40d6caad9187376a790f9a0ed09e22c861e37
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588601"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="79df8-102">Potencjalne pułapki z PLINQ</span><span class="sxs-lookup"><span data-stu-id="79df8-102">Potential pitfalls with PLINQ</span></span>

<span data-ttu-id="79df8-103">W wielu przypadkach PLINQ może zapewnić znaczną poprawę wydajności w porównaniu z sekwencyjnym LINQ do zapytań obiektów.</span><span class="sxs-lookup"><span data-stu-id="79df8-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="79df8-104">Jednak praca równoległości wykonywania kwerendy wprowadza złożoność, która może prowadzić do problemów, które w kodzie sekwencyjnym nie są tak powszechne lub nie są w ogóle napotkane.</span><span class="sxs-lookup"><span data-stu-id="79df8-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="79df8-105">W tym temacie wymieniono niektóre praktyki, których należy unikać podczas pisania zapytań PLINQ.</span><span class="sxs-lookup"><span data-stu-id="79df8-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="dont-assume-that-parallel-is-always-faster"></a><span data-ttu-id="79df8-106">Nie zakładaj, że równoległe jest zawsze szybsze</span><span class="sxs-lookup"><span data-stu-id="79df8-106">Don't assume that parallel is always faster</span></span>

<span data-ttu-id="79df8-107">Równoległość czasami powoduje, że kwerenda PLINQ działać wolniej niż jego LINQ do obiektów równoważne.</span><span class="sxs-lookup"><span data-stu-id="79df8-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="79df8-108">Podstawową zasadą jest to, że kwerendy, które mają kilka elementów źródłowych i szybkie delegatów użytkownika jest mało prawdopodobne, aby przyspieszyć znacznie.</span><span class="sxs-lookup"><span data-stu-id="79df8-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="79df8-109">Jednak ponieważ wiele czynników są zaangażowane w wydajność, zaleca się zmierzyć rzeczywiste wyniki przed podjęciem decyzji, czy używać PLINQ.</span><span class="sxs-lookup"><span data-stu-id="79df8-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="79df8-110">Aby uzyskać więcej informacji, zobacz [Opis przyspieszenia w PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="79df8-110">For more information, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="79df8-111">Unikaj pisania do lokalizacji pamięci współużytkowanej</span><span class="sxs-lookup"><span data-stu-id="79df8-111">Avoid writing to shared memory locations</span></span>

<span data-ttu-id="79df8-112">W kodzie sekwencyjnym nie jest rzadkością odczytywanie lub zapisywanie zmiennych statycznych lub pól klasy.</span><span class="sxs-lookup"><span data-stu-id="79df8-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="79df8-113">Jednak za każdym razem, gdy wiele wątków uzyskuje dostęp do takich zmiennych jednocześnie, istnieje duży potencjał dla warunków wyścigu.</span><span class="sxs-lookup"><span data-stu-id="79df8-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="79df8-114">Mimo że można użyć blokad do synchronizacji dostępu do zmiennej, koszt synchronizacji może zaszkodzić wydajności.</span><span class="sxs-lookup"><span data-stu-id="79df8-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="79df8-115">W związku z tym zaleca się, aby uniknąć lub przynajmniej ograniczyć dostęp do stanu udostępnionego w kwerendzie PLINQ jak najwięcej.</span><span class="sxs-lookup"><span data-stu-id="79df8-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="79df8-116">Unikanie nadmiernej równoległości</span><span class="sxs-lookup"><span data-stu-id="79df8-116">Avoid over-parallelization</span></span>

<span data-ttu-id="79df8-117">Za pomocą `AsParallel` metody, należy ponieść koszty ogólne partycjonowania kolekcji źródłowej i synchronizacji wątków procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="79df8-117">By using the `AsParallel` method, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="79df8-118">Korzyści z równoległości są dodatkowo ograniczone przez liczbę procesorów na komputerze.</span><span class="sxs-lookup"><span data-stu-id="79df8-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="79df8-119">Nie ma żadnych przyspieszeń, które można uzyskać, uruchamiając wiele wątków związanych z obliczeniami na jednym procesorze.</span><span class="sxs-lookup"><span data-stu-id="79df8-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="79df8-120">W związku z tym należy uważać, aby nie nadmiernie zrównoleglić kwerendy.</span><span class="sxs-lookup"><span data-stu-id="79df8-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="79df8-121">Najbardziej typowym scenariuszem, w którym może wystąpić nadmierna równoległość, jest zagnieżdżone kwerendy, jak pokazano w poniższym urywek.</span><span class="sxs-lookup"><span data-stu-id="79df8-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="79df8-122">W takim przypadku najlepiej jest zrównoleglić tylko zewnętrzne źródło danych (klienci), chyba że stosuje się co najmniej jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="79df8-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="79df8-123">Wewnętrzne źródło danych (cust. zamówień) jest znany jako bardzo długi.</span><span class="sxs-lookup"><span data-stu-id="79df8-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="79df8-124">Wykonujesz kosztowne obliczenia na każdym zamówieniu.</span><span class="sxs-lookup"><span data-stu-id="79df8-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="79df8-125">(Operacja pokazana w przykładzie nie jest kosztowna).</span><span class="sxs-lookup"><span data-stu-id="79df8-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="79df8-126">Wiadomo, że system docelowy ma wystarczającą liczbę procesorów do obsługi liczby wątków, które będą produkowane przez równoległość kwerendy na `cust.Orders`.</span><span class="sxs-lookup"><span data-stu-id="79df8-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="79df8-127">We wszystkich przypadkach najlepszym sposobem określenia optymalnego kształtu zapytania jest testowanie i mierzenie.</span><span class="sxs-lookup"><span data-stu-id="79df8-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="79df8-128">Aby uzyskać więcej informacji, zobacz [Jak: Pomiar wydajności kwerendy PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="79df8-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="79df8-129">Unikaj wezwań do metod niebezwiązanych z wątkami</span><span class="sxs-lookup"><span data-stu-id="79df8-129">Avoid calls to non-thread-safe methods</span></span>

<span data-ttu-id="79df8-130">Zapisywanie do metod wystąpienia niebezwłasników z zapytania PLINQ może prowadzić do uszkodzenia danych, które mogą lub nie mogą pozostać niewykryte w programie.</span><span class="sxs-lookup"><span data-stu-id="79df8-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="79df8-131">Może to również prowadzić do wyjątków.</span><span class="sxs-lookup"><span data-stu-id="79df8-131">It can also lead to exceptions.</span></span> <span data-ttu-id="79df8-132">W poniższym przykładzie wiele wątków będzie `FileStream.Write` próbować wywołać metodę jednocześnie, która nie jest obsługiwana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="79df8-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="79df8-133">Ograniczanie połączeń do metod bezpiecznych dla wątków</span><span class="sxs-lookup"><span data-stu-id="79df8-133">Limit calls to thread-safe methods</span></span>

<span data-ttu-id="79df8-134">Większość metod statycznych w .NET Framework są bezpieczne dla wątków i mogą być wywoływane z wielu wątków jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="79df8-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="79df8-135">Jednak nawet w takich przypadkach synchronizacji zaangażowanych może prowadzić do znacznego spowolnienia w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="79df8-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="79df8-136">Możesz przetestować to samodzielnie, wstawiając niektóre wywołania <xref:System.Console.WriteLine%2A> w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="79df8-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="79df8-137">Mimo że ta metoda jest używana w przykładach dokumentacji do celów demonstracyjnych, nie należy jej używać w zapytaniach PLINQ.</span><span class="sxs-lookup"><span data-stu-id="79df8-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="79df8-138">Unikaj niepotrzebnych operacji zamawiania</span><span class="sxs-lookup"><span data-stu-id="79df8-138">Avoid unnecessary ordering operations</span></span>

<span data-ttu-id="79df8-139">Gdy PLINQ wykonuje kwerendę równolegle, dzieli sekwencję źródłową na partycje, które mogą być obsługiwane jednocześnie na wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="79df8-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="79df8-140">Domyślnie kolejność przetwarzania partycji i dostarczania wyników nie jest przewidywalna (z wyjątkiem `OrderBy`operatorów, takich jak ).</span><span class="sxs-lookup"><span data-stu-id="79df8-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="79df8-141">Można poinstruować PLINQ, aby zachować kolejność sekwencji źródłowej, ale ma to negatywny wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="79df8-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="79df8-142">Najlepszym rozwiązaniem, gdy jest to możliwe, jest struktury kwerend, tak aby nie polegać na zachowaniu kolejności.</span><span class="sxs-lookup"><span data-stu-id="79df8-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="79df8-143">Aby uzyskać więcej informacji, zobacz [Zachowanie porządku w PLINQ](order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="79df8-143">For more information, see [Order Preservation in PLINQ](order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="79df8-144">Preferuj ForAll do ForEach, gdy jest to możliwe</span><span class="sxs-lookup"><span data-stu-id="79df8-144">Prefer ForAll to ForEach when it is possible</span></span>

<span data-ttu-id="79df8-145">Chociaż PLINQ wykonuje kwerendę na wiele wątków, jeśli `foreach` zużywają wyniki w pętli (w`For Each` języku Visual Basic), a następnie wyniki kwerendy muszą być scalone z powrotem do jednego wątku i dostęp szeregowo przez moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="79df8-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="79df8-146">W niektórych przypadkach jest to nieuniknione; jednak, gdy jest to `ForAll` możliwe, użyj metody, aby umożliwić każdemu wątkowi wyprowadzanie własnych wyników, na przykład przez zapisywanie do kolekcji bezpiecznej dla wątków, takiej jak <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="79df8-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="79df8-147">Ten sam problem <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>dotyczy .</span><span class="sxs-lookup"><span data-stu-id="79df8-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="79df8-148">Innymi słowy, `source.AsParallel().Where().ForAll(...)` powinny być `Parallel.ForEach(source.AsParallel().Where(), ...)`zdecydowanie preferowane .</span><span class="sxs-lookup"><span data-stu-id="79df8-148">In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to `Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="79df8-149">Należy pamiętać o problemach z koligacjami wątków</span><span class="sxs-lookup"><span data-stu-id="79df8-149">Be aware of thread affinity issues</span></span>

<span data-ttu-id="79df8-150">Niektóre technologie, na przykład współdziałanie COM dla składników jednowątkowych apartamentów (STA), Windows Forms i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątku, które wymagają uruchomienia kodu w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="79df8-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="79df8-151">Na przykład w formularzach systemu Windows i WPF WPF formantu można uzyskać tylko w wątku, w którym został utworzony.</span><span class="sxs-lookup"><span data-stu-id="79df8-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="79df8-152">Jeśli spróbujesz uzyskać dostęp do udostępnionego stanu formantu Windows Forms w kwerendzie PLINQ, wyjątek jest wywoływany, jeśli jest uruchomiony w debugerze.</span><span class="sxs-lookup"><span data-stu-id="79df8-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="79df8-153">(To ustawienie można wyłączyć). Jednak jeśli kwerenda jest zużywana w wątku interfejsu użytkownika, `foreach` następnie można uzyskać dostęp do formantu z pętli, która wylicza wyniki kwerendy, ponieważ ten kod jest wykonywany tylko w jednym wątku.</span><span class="sxs-lookup"><span data-stu-id="79df8-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="79df8-154">Nie zakładaj, że iteracje ForEach, For i ForAll zawsze są wykonywane równolegle</span><span class="sxs-lookup"><span data-stu-id="79df8-154">Don't assume that iterations of ForEach, For, and ForAll always execute in parallel</span></span>

<span data-ttu-id="79df8-155">Ważne jest, aby pamiętać, że poszczególne <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>iteracje w , <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> pętli może, ale nie muszą wykonywać równolegle.</span><span class="sxs-lookup"><span data-stu-id="79df8-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="79df8-156">W związku z tym należy unikać pisania kodu, który zależy od poprawności na równoległe wykonywanie iteracji lub na wykonywanie iteracji w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="79df8-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="79df8-157">Na przykład ten kod może zakleszczenie:</span><span class="sxs-lookup"><span data-stu-id="79df8-157">For example, this code is likely to deadlock:</span></span>

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

<span data-ttu-id="79df8-158">W tym przykładzie jedna iteracja ustawia zdarzenie, a wszystkie inne iteracje czekają na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="79df8-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="79df8-159">Żadna z iteracji oczekiwania można wykonać, dopóki iteracja ustawienia zdarzenia nie zostanie ukończona.</span><span class="sxs-lookup"><span data-stu-id="79df8-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="79df8-160">Jednak jest możliwe, że oczekiwanie iteracji bloku wszystkie wątki, które są używane do wykonywania pętli równoległej, przed iteracji ustawienia zdarzenia miał szansę wykonać.</span><span class="sxs-lookup"><span data-stu-id="79df8-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="79df8-161">Powoduje to zakleszczenie — iteracja ustawienia zdarzeń nigdy nie zostanie wykonana, a iteracje oczekiwania nigdy nie zostaną wybudzeni.</span><span class="sxs-lookup"><span data-stu-id="79df8-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="79df8-162">W szczególności jedna iteracja pętli równoległej nigdy nie należy czekać na inną iterację pętli, aby poczynić postępy.</span><span class="sxs-lookup"><span data-stu-id="79df8-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="79df8-163">Jeśli pętla równoległa zdecyduje się zaplanować iteracje sekwencyjnie, ale w odwrotnej kolejności wystąpi zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="79df8-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="79df8-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79df8-164">See also</span></span>

- [<span data-ttu-id="79df8-165">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="79df8-165">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
