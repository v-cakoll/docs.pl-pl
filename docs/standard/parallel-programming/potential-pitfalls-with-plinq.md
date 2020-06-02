---
title: Potencjalna pułapek z PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: b4d58734fba4b834d5f5819a6bf19da0b7b7e8db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285316"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="f01bd-102">Potencjalna pułapek z PLINQ</span><span class="sxs-lookup"><span data-stu-id="f01bd-102">Potential pitfalls with PLINQ</span></span>

<span data-ttu-id="f01bd-103">W wielu przypadkach PLINQ może zapewnić znaczną poprawę wydajności w stosunku do sekwencyjnych zapytań LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="f01bd-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="f01bd-104">Jednak w pracy przekształcają wykonywania zapytania wprowadzono złożoność, która może prowadzić do problemów, które w sekwencyjnym kodzie nie są zgodne lub nie są w ogóle obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f01bd-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="f01bd-105">Ten temat zawiera wskazówki, które należy unikać podczas pisania zapytań PLINQ.</span><span class="sxs-lookup"><span data-stu-id="f01bd-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="dont-assume-that-parallel-is-always-faster"></a><span data-ttu-id="f01bd-106">Nie zakładaj, że równoległy jest zawsze szybszy</span><span class="sxs-lookup"><span data-stu-id="f01bd-106">Don't assume that parallel is always faster</span></span>

<span data-ttu-id="f01bd-107">Przetwarzanie równoległe czasami powoduje spowolnienie działania zapytania PLINQ niż jego odpowiednik LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="f01bd-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="f01bd-108">Podstawowa zasada kciuka polega na tym, że zapytania, które mają kilka elementów źródłowych i szybkich delegatów użytkowników, prawdopodobnie nie przyspieszenie dużo.</span><span class="sxs-lookup"><span data-stu-id="f01bd-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="f01bd-109">Jednak ze względu na to, że wiele czynników jest związanych z wydajnością, zalecamy zmierzenie rzeczywistych wyników przed podjęciem decyzji o tym, czy używać PLINQ.</span><span class="sxs-lookup"><span data-stu-id="f01bd-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="f01bd-110">Aby uzyskać więcej informacji, zobacz temat [Omówienie przyspieszenie w PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f01bd-110">For more information, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="f01bd-111">Unikaj zapisywania w lokalizacjach pamięci współdzielonej</span><span class="sxs-lookup"><span data-stu-id="f01bd-111">Avoid writing to shared memory locations</span></span>

<span data-ttu-id="f01bd-112">W sekwencyjnym kodzie nie jest mało typowe odczytywanie z lub zapisywanie do zmiennych statycznych lub pól klas.</span><span class="sxs-lookup"><span data-stu-id="f01bd-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="f01bd-113">Jeśli jednak wiele wątków uzyskuje dostęp do takich zmiennych jednocześnie, istnieje duże prawdopodobieństwo dla warunków wyścigu.</span><span class="sxs-lookup"><span data-stu-id="f01bd-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="f01bd-114">Mimo że można użyć blokad do synchronizowania dostępu do zmiennej, koszt synchronizacji może obniżyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="f01bd-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="f01bd-115">W związku z tym zalecamy uniknięcie lub ograniczenie dostępu do udostępnionego stanu w kwerendzie PLINQ.</span><span class="sxs-lookup"><span data-stu-id="f01bd-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="f01bd-116">Unikaj nadmiernego przetwarzanie równoległe</span><span class="sxs-lookup"><span data-stu-id="f01bd-116">Avoid over-parallelization</span></span>

<span data-ttu-id="f01bd-117">Korzystając z `AsParallel` metody, naliczane są koszty narzutu partycjonowania kolekcji źródłowej i synchronizowanie wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="f01bd-117">By using the `AsParallel` method, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="f01bd-118">Zalety przetwarzanie równoległe są bardziej ograniczone przez liczbę procesorów na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f01bd-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="f01bd-119">Nie ma przyspieszenie do uzyskania, uruchamiając wiele wątków powiązanych z obliczeniami tylko na jednym procesorze.</span><span class="sxs-lookup"><span data-stu-id="f01bd-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="f01bd-120">W związku z tym należy zachować ostrożność, aby nie zrównoleglanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="f01bd-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="f01bd-121">Najbardziej typowym scenariuszem, w którym może wystąpić zbyt przetwarzanie równoległe, jest zapytanie zagnieżdżone, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="f01bd-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="f01bd-122">W takim przypadku najlepiej zrównoleglanie tylko zewnętrzne źródło danych (klienci), chyba że zostanie spełniony co najmniej jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="f01bd-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="f01bd-123">Wewnętrzne źródło danych (odbiorcy. Zamówienia) są znane jako bardzo długie.</span><span class="sxs-lookup"><span data-stu-id="f01bd-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="f01bd-124">Wykonujesz kosztowne obliczenia dla każdego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="f01bd-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="f01bd-125">(Operacja pokazana w przykładzie nie jest kosztowna).</span><span class="sxs-lookup"><span data-stu-id="f01bd-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="f01bd-126">System docelowy ma wystarczającą ilość procesorów do obsługi liczby wątków, które zostaną utworzone przez przekształcają zapytania `cust.Orders` .</span><span class="sxs-lookup"><span data-stu-id="f01bd-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="f01bd-127">We wszystkich przypadkach najlepszym sposobem określenia optymalnego kształtu zapytania jest przetestowanie i pomiar.</span><span class="sxs-lookup"><span data-stu-id="f01bd-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="f01bd-128">Aby uzyskać więcej informacji, zobacz [How to: Measure PLINQ Query Performance](how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="f01bd-128">For more information, see [How to: Measure PLINQ Query Performance](how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="f01bd-129">Unikaj wywołań metod niebezpiecznych dla wątków</span><span class="sxs-lookup"><span data-stu-id="f01bd-129">Avoid calls to non-thread-safe methods</span></span>

<span data-ttu-id="f01bd-130">Zapis w metodach wystąpienia niebezpiecznego dla wątków z zapytania PLINQ może prowadzić do uszkodzenia danych, które mogą lub nie zostać wykryte w programie.</span><span class="sxs-lookup"><span data-stu-id="f01bd-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="f01bd-131">Może to również prowadzić do wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f01bd-131">It can also lead to exceptions.</span></span> <span data-ttu-id="f01bd-132">W poniższym przykładzie wiele wątków próbuje wywołać `FileStream.Write` metodę jednocześnie, co nie jest obsługiwane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="f01bd-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="f01bd-133">Ogranicz wywołania metod bezpiecznych dla wątków</span><span class="sxs-lookup"><span data-stu-id="f01bd-133">Limit calls to thread-safe methods</span></span>

<span data-ttu-id="f01bd-134">Większość metod statycznych w .NET Framework są bezpieczne dla wątków i może być wywoływana z wielu wątków jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="f01bd-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="f01bd-135">Jednak nawet w takich przypadkach Synchronizacja może prowadzić do znacznego spowolnienia w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="f01bd-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="f01bd-136">Możesz przetestować ten sposób, wstawiając kilka wywołań do <xref:System.Console.WriteLine%2A> zapytania.</span><span class="sxs-lookup"><span data-stu-id="f01bd-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="f01bd-137">Mimo że ta metoda jest używana w przykładach dokumentacji w celach demonstracyjnych, nie należy używać jej w zapytaniach PLINQ.</span><span class="sxs-lookup"><span data-stu-id="f01bd-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="f01bd-138">Unikaj niepotrzebnych operacji porządkowania</span><span class="sxs-lookup"><span data-stu-id="f01bd-138">Avoid unnecessary ordering operations</span></span>

<span data-ttu-id="f01bd-139">Gdy PLINQ wykonuje zapytanie równolegle, dzieli sekwencję źródłową na partycje, które mogą być wykonywane współbieżnie na wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="f01bd-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="f01bd-140">Domyślnie kolejność, w której są przetwarzane partycje, a wyniki są dostarczane nie jest przewidywalna (z wyjątkiem operatorów takich jak `OrderBy` ).</span><span class="sxs-lookup"><span data-stu-id="f01bd-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="f01bd-141">Można polecić PLINQ, aby zachować kolejność każdej sekwencji źródłowej, ale ma negatywny wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="f01bd-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="f01bd-142">Najlepszym rozwiązaniem, jeśli jest to możliwe, jest struktura zapytań, dzięki czemu nie są one zależne od zachowywania kolejności.</span><span class="sxs-lookup"><span data-stu-id="f01bd-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="f01bd-143">Aby uzyskać więcej informacji, zobacz temat [porządkowania zamówień w PLINQ](order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f01bd-143">For more information, see [Order Preservation in PLINQ](order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="f01bd-144">Preferuj ForAll do ForEach, gdy jest to możliwe</span><span class="sxs-lookup"><span data-stu-id="f01bd-144">Prefer ForAll to ForEach when it is possible</span></span>

<span data-ttu-id="f01bd-145">Mimo że PLINQ wykonuje zapytanie w wielu wątkach, jeśli wyniki są używane w `foreach` pętli ( `For Each` w Visual Basic), wyniki zapytania muszą zostać scalone z powrotem do jednego wątku i dostępne przez moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="f01bd-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="f01bd-146">W niektórych przypadkach jest to nieuniknione. jednak zawsze, gdy jest to możliwe, należy użyć `ForAll` metody, aby umożliwić każdemu wątkowi wyprowadzanie własnych wyników, na przykład przez zapis do kolekcji bezpiecznej dla wątków, takiej jak <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f01bd-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f01bd-147">Ten sam problem odnosi się do <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f01bd-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f01bd-148">Innymi słowy, `source.AsParallel().Where().ForAll(...)` powinny być silnie preferowane `Parallel.ForEach(source.AsParallel().Where(), ...)` .</span><span class="sxs-lookup"><span data-stu-id="f01bd-148">In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to `Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="f01bd-149">Należy pamiętać o problemach z koligacją wątków</span><span class="sxs-lookup"><span data-stu-id="f01bd-149">Be aware of thread affinity issues</span></span>

<span data-ttu-id="f01bd-150">Niektóre technologie, na przykład współdziałanie modelu COM dla składników Single-Threading Apartment (STA), Windows Forms i Windows Presentation Foundation (WPF), nakładają ograniczenia koligacji wątku, które wymagają kodu do uruchomienia w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="f01bd-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="f01bd-151">Na przykład zarówno w Windows Forms, jak i WPF, dostęp do formantu można uzyskać tylko w wątku, w którym został utworzony.</span><span class="sxs-lookup"><span data-stu-id="f01bd-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="f01bd-152">Jeśli spróbujesz uzyskać dostęp do udostępnionego stanu formantu Windows Forms w zapytaniu PLINQ, zostanie zgłoszony wyjątek w przypadku uruchamiania programu w debugerze.</span><span class="sxs-lookup"><span data-stu-id="f01bd-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="f01bd-153">(To ustawienie może być wyłączone). Jeśli jednak zapytanie jest używane w wątku interfejsu użytkownika, można uzyskać dostęp do formantu z `foreach` pętli, która wylicza wyniki zapytania, ponieważ ten kod jest wykonywany tylko dla jednego wątku.</span><span class="sxs-lookup"><span data-stu-id="f01bd-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="f01bd-154">Nie zakładaj, że iteracje ForEach, for i ForAll są zawsze wykonywane równolegle</span><span class="sxs-lookup"><span data-stu-id="f01bd-154">Don't assume that iterations of ForEach, For, and ForAll always execute in parallel</span></span>

<span data-ttu-id="f01bd-155">Należy pamiętać, że poszczególne iteracje w <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli, lub <xref:System.Linq.ParallelEnumerable.ForAll%2A> mogą, ale nie muszą być wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="f01bd-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="f01bd-156">W związku z tym należy unikać pisania kodu, który zależy do poprawnego wykonywania iteracji lub wykonywania iteracji w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="f01bd-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="f01bd-157">Na przykład ten kod może być zakleszczony:</span><span class="sxs-lookup"><span data-stu-id="f01bd-157">For example, this code is likely to deadlock:</span></span>

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

<span data-ttu-id="f01bd-158">W tym przykładzie Jedna iteracja ustawia zdarzenie, a wszystkie inne iteracje oczekują na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f01bd-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="f01bd-159">Żadna z oczekujących iteracji nie może zostać zakończona do momentu zakończenia iteracji ustawienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f01bd-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="f01bd-160">Jednak istnieje możliwość, że oczekujące iteracje blokują wszystkie wątki, które są używane do wykonywania pętli równoległej, przed wykonaniem iteracji ustawienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f01bd-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="f01bd-161">Powoduje to zakleszczenie — iteracja ustawienia zdarzenia nigdy nie zostanie wykonana, a oczekujące iteracje nigdy nie zostaną wznowione.</span><span class="sxs-lookup"><span data-stu-id="f01bd-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="f01bd-162">W szczególności jedna iteracja pętli równoległej nigdy nie powinna czekać na kolejną iterację pętli, aby wykonać postęp.</span><span class="sxs-lookup"><span data-stu-id="f01bd-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="f01bd-163">Jeśli pętla równoległa zdecyduje się na sekwencyjne planowanie iteracji, ale w kolejności odwrotnej, nastąpi zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="f01bd-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="f01bd-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f01bd-164">See also</span></span>

- [<span data-ttu-id="f01bd-165">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f01bd-165">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
