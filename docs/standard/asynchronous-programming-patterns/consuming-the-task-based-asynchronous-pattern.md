---
title: Wykorzystywanie wzorca asynchronicznego opartego na zadaniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eac5f9f6c8b47a6f14898eac2505ecc890015010
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870048"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="6d7eb-102">Wykorzystywanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="6d7eb-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="6d7eb-103">Gdy używasz opartego na zadaniach asynchronicznej wzorca (TAP) do pracy z operacji asynchronicznych, możesz korzystać z wywołań zwrotnych do osiągnięcia oczekiwania bez blokowania.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="6d7eb-104">W przypadku zadań jest to realizowane przez metody takie jak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d7eb-105">Obsługa komunikacji asynchronicznej opartych na języku ukrywa wywołań zwrotnych, umożliwiając operacji asynchronicznych Oczekiwanie w ramach normalnych sterowanie przepływem i kod generowany przez kompilator obsługuje ten sam poziom interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="6d7eb-106">Zawieszenie wykonywania za pomocą Await</span><span class="sxs-lookup"><span data-stu-id="6d7eb-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="6d7eb-107">Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], możesz użyć [await](~/docs/csharp/language-reference/keywords/await.md) — słowo kluczowe w języku C# i [operatora Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic asynchronicznie oczekują na <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-107">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can use the [await](~/docs/csharp/language-reference/keywords/await.md) keyword in C# and the [Await Operator](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="6d7eb-108">Jeśli masz oczekujące na <xref:System.Threading.Tasks.Task>, `await` wyrażenie jest typu `void`.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="6d7eb-109">Jeśli masz oczekujące na <xref:System.Threading.Tasks.Task%601>, `await` wyrażenie jest typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="6d7eb-110">`await` Wyrażenie musi wystąpić w treści metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="6d7eb-111">Aby uzyskać więcej informacji na temat języka C# i Visual Basic obsługują w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobacz temat specyfikacji języka C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-111">For more information about C# and Visual Basic language support in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="6d7eb-112">Dzieje się w tle funkcje await instaluje wywołanie zwrotne do zadania za pomocą kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="6d7eb-113">To wywołanie zwrotne wznawia metody asynchronicznej w punkcie zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="6d7eb-114">Po wznowieniu metody asynchronicznej Jeśli oczekiwane działanie, zakończyło się pomyślnie i został <xref:System.Threading.Tasks.Task%601>, jego `TResult` jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="6d7eb-115">Jeśli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> , oczekiwany zostało zakończone w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu, <xref:System.OperationCanceledException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="6d7eb-116">Jeśli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> , oczekiwany zostało zakończone w <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu, jest zgłaszany wyjątek, który spowodował jego błędów.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="6d7eb-117">A `Task` błędów wyniku wiele wyjątków może, ale tylko jeden z tych wyjątków jest propagowany.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="6d7eb-118">Jednak <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.AggregateException> wyjątek, który zawiera wszystkie błędy.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="6d7eb-119">Jeśli kontekst synchronizacji (<xref:System.Threading.SynchronizationContext> obiektu) jest skojarzony z wątkiem, wykonywanej metody asynchronicznej w chwili zawieszenia (na przykład, jeśli <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> właściwość nie jest `null`), metoda asynchroniczna wznawia na tym Ten sam kontekst synchronizacji przy użyciu kontekstu <xref:System.Threading.SynchronizationContext.Post%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="6d7eb-120">W przeciwnym razie opiera się na harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler> obiektu) było aktualne w chwili zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="6d7eb-121">Zazwyczaj jest to domyślny harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), który jest przeznaczony dla puli wątków.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="6d7eb-122">Ten harmonogram zadań określa, czy operacji asynchronicznej powinna zostać wznowiona, gdzie ukończone lub tego, czy powinna zostać zaplanowana wznowienia.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="6d7eb-123">Domyślnego harmonogramu zezwala zazwyczaj na kontynuację uruchamiać w wątku, który, oczekiwane operacja zakończona.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="6d7eb-124">Gdy wywoływana jest metoda asynchroniczna, synchronicznie wykonuje treści funkcji do czasu pierwszy operator await, wyrażenie na oczekujący wystąpienie, które nie zostało jeszcze zakończone, w tym momencie wywołania powraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="6d7eb-125">Jeśli metoda asynchroniczna zwraca `void`, <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiekt jest zwracany do reprezentowania trwającą obliczeń.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="6d7eb-126">W metodzie asynchronicznej, innym niż void, jeśli zostanie osiągnięty instrukcji return lub osiągnięty zostanie koniec treści metody, zadanie zostało ukończone w <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stan końcowy.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="6d7eb-127">Jeśli nieobsługiwany wyjątek powoduje, że formant opuścić tekstu metody asynchronicznej, zadanie kończy się <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="6d7eb-128">Jeśli wyjątkiem jest sytuacja, <xref:System.OperationCanceledException>, zadanie kończy się zamiast tego na <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="6d7eb-129">W ten sposób wynik lub wyjątek po pewnym czasie została opublikowana.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="6d7eb-130">Istnieje kilka ważnych zmian, to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="6d7eb-131">Ze względu na wydajność Jeśli zadanie zostało już ukończone do czasu trwa oczekiwanie na zadanie, kontrolki nie jest uzyskane i kontynuuje wykonywanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="6d7eb-132">Ponadto powrotu do oryginalnego kontekstu nie zawsze są żądane zachowanie i można ją zmienić; to jest opisany bardziej szczegółowo w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="6d7eb-133">Konfigurowanie zawieszenia i wznowienia przy użyciu produktywności i ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="6d7eb-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="6d7eb-134">Kilka metod zapewniają większą kontrolę nad wykonywaniem metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="6d7eb-135">Na przykład, można użyć <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metodę, aby wprowadzić punkt yield do metod asynchronicznych:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="6d7eb-136">Jest to równoważne do asynchronicznego przesyłania lub harmonogramów bieżącego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="6d7eb-137">Można również użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metody dla lepszej kontroli nad zawieszenia i wznowienia w metodzie asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="6d7eb-138">Jak już wspomniano, domyślnie bieżącego kontekstu są przechwytywane w czasie, które metody asynchronicznej jest wstrzymana, a ten kontekście przechwyconym służy do wywoływania metody asynchronicznej kontynuacji po wznowieniu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="6d7eb-139">W wielu przypadkach jest dokładne zachowanie, które chcesz.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="6d7eb-140">W innych przypadkach może nie interesujące Cię kontekst kontynuacji i lepszą wydajność można uzyskać, unikając takie wpisy powrót do oryginalnego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="6d7eb-141">Aby włączyć tę opcję, należy użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodę, aby poinformować operacji await nie w celu przechwycenia i wznowić w kontekście, ale kontynuuje wykonywanie, wszędzie tam, gdzie ukończyć operację asynchroniczną, która jest oczekiwany:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="6d7eb-142">Anulowanie operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="6d7eb-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="6d7eb-143">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], metody wzorca TAP obsługuje anulowanie Podaj co najmniej jeden przeciążenia, które akceptuje token odwołania (<xref:System.Threading.CancellationToken> obiektu).</span><span class="sxs-lookup"><span data-stu-id="6d7eb-143">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="6d7eb-144">Token anulowania jest tworzony przez źródło tokenu anulowania (<xref:System.Threading.CancellationTokenSource> obiektu).</span><span class="sxs-lookup"><span data-stu-id="6d7eb-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="6d7eb-145">Źródło <xref:System.Threading.CancellationTokenSource.Token%2A> właściwość zwraca token anulowania, który zostanie zasygnalizowane podczas źródła <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="6d7eb-146">Na przykład, jeśli chcesz pobrać pojedynczej strony sieci Web i chcesz mieć możliwość anulować operację, należy utworzyć <xref:System.Threading.CancellationTokenSource> obiektu, przekazać token jej do metody wzorca TAP, a następnie wywołaj źródła <xref:System.Threading.CancellationTokenSource.Cancel%2A> metody, gdy wszystko będzie gotowe anulować operację:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="6d7eb-147">Aby anulować wielu wywołań asynchronicznych, można przekazać tego samego tokenu do wywołania wszystkich:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="6d7eb-148">Alternatywnie można przekazać tego samego tokenu do podzbioru selektywne operacje:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="6d7eb-149">Może zostać zainicjowane żądań anulowania z żadnym z wątków.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="6d7eb-150">Możesz przekazać <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> wartość do dowolnej metody, które akceptuje token anulowania, aby wskazać, że anulowanie nigdy nie będzie wymagane.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="6d7eb-151">Powoduje to, że <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> właściwości do zwrócenia `false`, i odpowiednio zoptymalizować wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="6d7eb-152">Do celów testowych można również przekazać token anulowania wstępnie anulowane, który zostanie uruchomiony przy użyciu konstruktora, który przyjmuje wartość logiczną, aby wskazać, czy token powinna uruchomić się w stanie już anulowana lub nie można anulować.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="6d7eb-153">Takie podejście do anulowania ma kilka zalet:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="6d7eb-154">Można przekazać ten sam token odwołania do dowolnej liczby operacji synchronicznego i asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="6d7eb-155">Tego samego żądania anulowania może proliferated do dowolnej liczby odbiorników.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="6d7eb-156">Deweloper asynchronicznego interfejsu API jest pełną kontrolę nad tego, czy można żądać anulowania i kiedy może obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="6d7eb-157">Kod, który wykorzystuje interfejs API może określić selektywnie wywołania asynchroniczne, które będzie propagowane żądań anulowania.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="6d7eb-158">Postęp monitorowania</span><span class="sxs-lookup"><span data-stu-id="6d7eb-158">Monitoring Progress</span></span>
 <span data-ttu-id="6d7eb-159">Niektóre metody asynchronicznej uwidocznić postęp za pomocą interfejsu postępu, przekazywane do metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="6d7eb-160">Na przykład należy wziąć pod uwagę, że funkcja, która asynchronicznie pobiera ciągu tekstu, a po drodze zgłasza aktualizacji w toku, obejmujących procent do pobrania, które zostało ukończone w związku z tym daleko.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="6d7eb-161">Taka metoda może być używane w aplikacji Windows Presentation Foundation (WPF) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="6d7eb-162">Za pomocą wbudowanych kombinacji opartych na zadaniach</span><span class="sxs-lookup"><span data-stu-id="6d7eb-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="6d7eb-163"><xref:System.Threading.Tasks> Przestrzeń nazw zawiera kilka metod tworzenia i pracy z zadaniami.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="6d7eb-164">Task.Run</span><span class="sxs-lookup"><span data-stu-id="6d7eb-164">Task.Run</span></span>
 <span data-ttu-id="6d7eb-165"><xref:System.Threading.Tasks.Task> Klasy zawiera kilka <xref:System.Threading.Tasks.Task.Run%2A> metod, które pozwalają na łatwe odciążania pracę jako <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> do puli wątków, na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="6d7eb-166">Niektóre z nich <xref:System.Threading.Tasks.Task.Run%2A> metod, takich jak <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> przeciążenia, istnieje jako skrót dla <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="6d7eb-167">Inne przeciążenia, takich jak <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, Włącz przy użyciu await Odciążone utworu, na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="6d7eb-168">Takimi przeciążeniami są logicznie równoważne użyciu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody w połączeniu z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia w bibliotece zadań równoległych.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="6d7eb-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="6d7eb-169">Task.FromResult</span></span>
 <span data-ttu-id="6d7eb-170">Użyj <xref:System.Threading.Tasks.Task.FromResult%2A> metoda w scenariuszach, w którym dane mogą być już dostępne i po prostu musi być zwracane przez metodę zwracającą zadanie podniesiony do <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="6d7eb-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="6d7eb-171">Task.WhenAll</span></span>
 <span data-ttu-id="6d7eb-172">Użyj <xref:System.Threading.Tasks.Task.WhenAll%2A> metoda asynchronicznie oczekiwania na wiele operacji asynchronicznych, które są reprezentowane jako zadania.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="6d7eb-173">Metoda ma wiele przeciążeń, które obsługują zestaw zadań innych niż ogólne lub zestaw obsługuje technologię niejednolitego ogólnych zadań (na przykład asynchronicznie oczekuje na wiele operacji zwracającą typ void lub asynchronicznie oczekuje dla wielu metod, zwracając wartość gdzie Każda wartość może mieć inny typ) i jednolity zbiór zadań rodzajowych obsługujących (takie jak asynchronicznie oczekuje wielu `TResult`— metody zwracające typ).</span><span class="sxs-lookup"><span data-stu-id="6d7eb-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="6d7eb-174">Załóżmy, że użytkownik chce wysyłać wiadomości e-mail do wielu klientów.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="6d7eb-175">Użytkownik może nakładać się na wysyłanie wiadomości, więc nie oczekiwania na ukończenie przed wysłaniem następnego jednej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="6d7eb-176">Można również znaleźć się po zakończeniu operacji wysyłania i tego, czy wystąpiły błędy:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="6d7eb-177">Ten kod nie obsługuje jawnie wyjątków, które mogą wystąpić, ale umożliwia wyjątki dostawały się z `await` w zadanie wynikowe z <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="6d7eb-178">Aby obsłużyć wyjątki, można użyć kodu, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-178">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="6d7eb-179">W tym przypadku jeśli żadnych operacji asynchronicznej zakończy się niepowodzeniem, wszystkie wyjątki zostaną skonsolidowane w w <xref:System.AggregateException> wyjątek, który jest przechowywany w <xref:System.Threading.Tasks.Task> zwrócone z <xref:System.Threading.Tasks.Task.WhenAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="6d7eb-180">Jednak tylko jeden z tych wyjątków są rozprowadzane przez `await` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="6d7eb-181">Jeśli chcesz sprawdzić wszystkie wyjątki, można napisać ponownie poprzedniego kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="6d7eb-182">Rozważmy przykład pobierane jest kilka plików z sieci web asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="6d7eb-183">W takim przypadku wszystkie operacje asynchroniczne mają typy wyników jednorodnych i łatwo uzyskiwać dostęp do wyników:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="6d7eb-184">Można użyć tych samych technik obsługi wyjątków, które omówiono w poprzednim scenariuszu zwracającą typ void:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="6d7eb-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="6d7eb-185">Task.WhenAny</span></span>
 <span data-ttu-id="6d7eb-186">Możesz użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metoda asynchronicznie czekać na co najmniej jeden wiele operacji asynchronicznych w postaci zadania do wykonania.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="6d7eb-187">Ta metoda służy cztery główne przypadki użycia:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="6d7eb-188">Nadmiarowość:  Wykonuje operację wielokrotnie i wybierania odpowiedniego kończące się pierwszym (na przykład, kontaktując się z wielu usług sieci web giełdowych generujących jeden wynik i wybierania odpowiedniego kończące najszybsza).</span><span class="sxs-lookup"><span data-stu-id="6d7eb-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="6d7eb-189">Technologia:  Uruchamianie wielu operacji oczekiwania na wszystkich z nich, aby zakończyć, a ich przetwarzania, po ich zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="6d7eb-190">Ograniczanie:  Umożliwiając dodatkowych operacji w celu rozpoczęcia po zakończeniu przez inne osoby.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="6d7eb-191">Jest to rozszerzenie interleaving scenariusza.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="6d7eb-192">Wczesne podejmowano:  Na przykład operacji reprezentowany przez t1 zadania mogą być grupowane w <xref:System.Threading.Tasks.Task.WhenAny%2A> zadania za pomocą innej t2 zadań, a także możesz poczekać <xref:System.Threading.Tasks.Task.WhenAny%2A> zadania.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="6d7eb-193">Zadanie t2 może reprezentować limit czasu anulowania i/lub inne sygnał, który powoduje, że <xref:System.Threading.Tasks.Task.WhenAny%2A> zadań do wykonania przed zakończeniem t1.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="6d7eb-194">Nadmiarowość</span><span class="sxs-lookup"><span data-stu-id="6d7eb-194">Redundancy</span></span>
 <span data-ttu-id="6d7eb-195">Należy rozważyć przypadek, w której chcesz podjąć decyzję o tym, czy na kupowaniu akcji.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="6d7eb-196">Istnieje kilka usług sieci web podstawowe zalecenia, którym ufasz, ale w zależności od obciążenia dziennego każda usługa może wystąpić powolnych w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="6d7eb-197">Możesz użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody, aby otrzymać powiadomienie po zakończeniu każdej operacji:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="6d7eb-198">W odróżnieniu od <xref:System.Threading.Tasks.Task.WhenAll%2A>, która zwraca nieopakowane wyniki wszystkich zadań, które zostało ukończone pomyślnie, <xref:System.Threading.Tasks.Task.WhenAny%2A> zwraca zadanie, które zakończona.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="6d7eb-199">Jeśli zadanie zakończy się niepowodzeniem, należy wiedzieć, że nie powiodło się, a jeśli zadanie zakończy się powodzeniem, ważne jest, aby wiedzieć, które zadanie wartość zwracana jest skojarzona z.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="6d7eb-200">Dlatego należy dostęp do wyniku zwróconego zadania lub dodatkowo await, jak pokazano w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="6d7eb-201">Podobnie jak w przypadku <xref:System.Threading.Tasks.Task.WhenAll%2A>, muszą być w stanie obsłużyć wyjątki.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="6d7eb-202">Ponieważ pojawi się ponownie ukończonego zadania, może poczekać zwracane zadanie propagacji, błędy i `try/catch` ich odpowiednio; na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="6d7eb-203">Ponadto nawet jeśli pierwsze zadanie zakończy się pomyślnie, kolejne zadania może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="6d7eb-204">W tym momencie masz kilka opcji związanych z wyjątkami:  Możesz poczekać, aż uruchomionego zadania zostały wykonane, w którym to przypadku należy użyć <xref:System.Threading.Tasks.Task.WhenAll%2A> metody lub możesz zdecydować, czy wszystkie wyjątki są ważne i musi być zalogowany.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="6d7eb-205">W tym celu można użyć kontynuacji, aby otrzymać powiadomienie, gdy zadania zostaną zakończone asynchronicznie:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="6d7eb-206">lub:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="6d7eb-207">a nawet:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-207">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="6d7eb-208">Na koniec można anulować pozostałe operacje:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-208">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="6d7eb-209">Z przeplotem</span><span class="sxs-lookup"><span data-stu-id="6d7eb-209">Interleaving</span></span>
 <span data-ttu-id="6d7eb-210">Należy rozważyć przypadek, gdzie jesteś pobierania obrazów z sieci web i przetwarzanie każdego obrazu (na przykład dodawanie obrazu do kontrolki interfejsu użytkownika).</span><span class="sxs-lookup"><span data-stu-id="6d7eb-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="6d7eb-211">Należy wykonać przetwarzanie sekwencyjnie w wątku interfejsu użytkownika, ale chcesz pobrać obrazów jako równocześnie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="6d7eb-212">Ponadto, użytkownik nie chce wstrzymać Dodawanie obrazów do Interfejsu użytkownika, dopóki wszystkie pobraniu — mają zostać dodane po ich zakończeniu:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="6d7eb-213">Można również stosować z przeplotem do scenariusza, który obejmuje przetwarzanie wymaga dużej mocy obliczeniowej na <xref:System.Threading.ThreadPool> obrazów pobrane; na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="6d7eb-214">Dławienie</span><span class="sxs-lookup"><span data-stu-id="6d7eb-214">Throttling</span></span>
 <span data-ttu-id="6d7eb-215">Należy wziąć pod uwagę przykład interleaving, chyba że użytkownik jest pobierany tak wiele obrazów, plików do pobrania trzeba ograniczenia; na przykład chcesz określoną liczbę plików do pobrania ma być wykonywana równolegle.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="6d7eb-216">Aby to osiągnąć, można uruchomić podzestaw operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="6d7eb-217">Po zakończeniu operacji, można zacząć dodatkowych operacji w celu ich miejsce:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-217">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="6d7eb-218">Wczesne podejmowano</span><span class="sxs-lookup"><span data-stu-id="6d7eb-218">Early Bailout</span></span>
 <span data-ttu-id="6d7eb-219">Należy wziąć pod uwagę, że czekasz asynchronicznie operacji do wykonania podczas jednoczesnego odpowiedzi na żądanie anulowania przez użytkownika (na przykład użytkownik kliknął przycisk Anuluj).</span><span class="sxs-lookup"><span data-stu-id="6d7eb-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="6d7eb-220">Poniższy kod ilustruje ten scenariusz:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-220">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="6d7eb-221">Ta implementacja włączające interfejsu użytkownika, jak najszybciej podjąć decyzję o poręczenie, ale nie anuluje podstawowych operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="6d7eb-222">Inną alternatywą jest anulowania oczekujących operacji w przypadku podjęcia decyzji o poręczenie, ale nie przywraca interfejsu użytkownika do momentu faktycznie zakończeniu potencjalnie ze względu na kończenie wcześnie ze względu na żądanie anulowania operacji:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="6d7eb-223">Innym przykładem wczesne podejmowano polega na użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> metody w połączeniu z <xref:System.Threading.Tasks.Task.Delay%2A> metodę, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="6d7eb-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="6d7eb-224">Task.Delay</span></span>
 <span data-ttu-id="6d7eb-225">Możesz użyć <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metodę, aby wprowadzić wstrzymuje działanie do wykonania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="6d7eb-226">Jest to przydatne dla wielu rodzajów funkcje, w tym tworzenie pętli sondowania i opóźnienia obsługę uprzednio ustalonym czasie dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="6d7eb-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda może być również przydatne w połączeniu z <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> dla implementacji przekroczeń limitu czasu na czeka.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="6d7eb-228">Jeśli zadanie, które jest częścią większej operację asynchroniczną (na przykład usługi sieci web platformy ASP.NET) trwa zbyt długo, operację ogólną może to spowodować obniżenie, zwłaszcza, jeśli nie jest on nigdy nie zakończyć.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="6d7eb-229">Z tego powodu jest ważne móc limit czasu podczas oczekiwania na operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="6d7eb-230">Synchronicznej <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody akceptować wartości limitu czasu, ale odpowiedni <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> i wymienionych wcześniej <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>nie metody.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="6d7eb-231">Zamiast tego można użyć <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> w połączeniu, aby zaimplementować upływu limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="6d7eb-232">Na przykład w aplikacji interfejsu użytkownika, załóżmy, że chcesz pobrać obraz i Wyłącz interfejs użytkownika podczas pobierania obrazu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="6d7eb-233">Jednak jeśli pobieranie trwa zbyt długo, chcesz ponownie włączyć interfejs użytkownika i odrzucić pliki do pobrania:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="6d7eb-234">To samo dotyczy wiele plików do pobrania, ponieważ <xref:System.Threading.Tasks.Task.WhenAll%2A> zwraca klasę task:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="6d7eb-235">Tworzenie metody opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="6d7eb-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="6d7eb-236">Ponieważ zadanie jest w stanie całkowicie reprezentuje operację asynchroniczną i synchroniczne i asynchroniczne możliwości dołączania za pomocą operacji, podczas pobierania wyników i tak dalej, możesz tworzyć przydatne bibliotek kombinacji są metody, które tworzą zadania tworzenie większych wzorców.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="6d7eb-237">Zgodnie z opisem w poprzedniej sekcji, program .NET Framework zawiera kilka wbudowanych kombinacji, ale możesz również tworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="6d7eb-238">Poniższe sekcje zawierają kilka przykładów potencjalnych przedsięwzięciu combinator metody i typy.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="6d7eb-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="6d7eb-239">RetryOnFault</span></span>
 <span data-ttu-id="6d7eb-240">W wielu sytuacjach można ponowić próbę wykonania operacji, jeśli poprzednia próba nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="6d7eb-241">Dla kodu synchronicznego, możesz utworzyć metodę pomocnika takich jak `RetryOnFault` w poniższym przykładzie w tym celu:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="6d7eb-242">Możesz tworzyć metody pomocnika prawie identyczne dla asynchronicznych operacji, które są implementowane przez NACIŚNIĘCIE i dlatego zwracają zadania:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="6d7eb-243">Można następnie użyć tym przedsięwzięciu combinator do zakodowania ponownych prób w aplikacji logiki... na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="6d7eb-244">Można rozszerzyć `RetryOnFault` działać dalej.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="6d7eb-245">Na przykład funkcja może akceptować innego `Func<Task>` , zostanie wywołany, między kolejnymi próbami do określenia, kiedy i spróbuj wykonać operację ponownie, na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="6d7eb-246">Można następnie użyć funkcji w następujący sposób czekać na chwilę przed ponowieniem próby wykonania operacji:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="6d7eb-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="6d7eb-247">NeedOnlyOne</span></span>
 <span data-ttu-id="6d7eb-248">Czasami możesz korzystać z zalet nadmiarowość, aby zwiększyć opóźnienie i szanse na powodzenie operacji.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="6d7eb-249">Należy wziąć pod uwagę wiele usług sieci web, które zapewniają notowań giełdowych, ale o różnych porach dnia, każda usługa może dostarczyć różne poziomy jakości i czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="6d7eb-250">Radzenia sobie z tymi zmianami, może wysyłać żądania do wszystkich usług sieci web i tak szybko, jak uzyskać odpowiedzi z jednej, anulowanie pozostałych żądań.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="6d7eb-251">Możesz zaimplementować funkcji pomocnika, aby ułatwić zaimplementować ten wspólny wzorzec uruchamianie wielu operacji, oczekiwania, a następnie anulować pozostałe.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="6d7eb-252">`NeedOnlyOne` Funkcji w poniższym przykładzie przedstawiono w tym scenariuszu:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="6d7eb-253">Następnie można użyć tej funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="6d7eb-254">Operacje z przeplotem</span><span class="sxs-lookup"><span data-stu-id="6d7eb-254">Interleaved Operations</span></span>
 <span data-ttu-id="6d7eb-255">Brak potencjalny problem z wydajnością przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> metody w celu obsługi interleaving scenariusz, podczas pracy z bardzo dużych zestawów zadań.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span>  <span data-ttu-id="6d7eb-256">Każde wywołanie <xref:System.Threading.Tasks.Task.WhenAny%2A> wyniki w zarejestrowanej za pomocą każde zadanie kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="6d7eb-257">N liczbę zadań powoduje to kontynuacji O(N2) utworzone w okresie istnienia interleaving operacji.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-257">For N number of tasks, this results in O(N2) continuations created over the lifetime of the interleaving operation.</span></span>  <span data-ttu-id="6d7eb-258">Jeśli pracujesz z dużym zestawem zadań, możesz użyć kombinatorem (`Interleaved` w poniższym przykładzie) Aby rozwiązać problem z wydajnością:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-258">If you're working with a large set of tasks, you can use a combinator  (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="6d7eb-259">Przedsięwzięciu combinator można następnie użyć do przetwarzania wyników zadania po ich zakończeniu; na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="6d7eb-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="6d7eb-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="6d7eb-261">W niektórych scenariuszach dotyczących punktowy/zbieranie możesz chcieć poczekaj, aż wszystkie zadania w zestawie, chyba że jeden z nich błędów, w którym to przypadku chcesz zatrzymać czekających zaraz po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="6d7eb-262">Można osiągnąć, za pomocą metody przedsięwzięciu combinator takich jak `WhenAllOrFirstException` w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="6d7eb-263">Struktury danych oparta na zadaniach tworzenia</span><span class="sxs-lookup"><span data-stu-id="6d7eb-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="6d7eb-264">Oprócz możliwości tworzenia niestandardowej metody opartego na zadaniach, mających struktury danych w <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> reprezentujący wyniki operacji asynchronicznej i niezbędne synchronizacji połączyć się z nim sprawia, że bardzo zaawansowany Wpisz, na której można utworzyć struktury danych niestandardowych, które ma być używany w scenariuszach asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="6d7eb-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="6d7eb-265">AsyncCache</span></span>
 <span data-ttu-id="6d7eb-266">Jednym ważnym aspektem zadaniem jest, czy jego może można przekazać do wielu odbiorców, z których mogą oczekiwać, zarejestruj kontynuacje za ich pomocą uzyskać jego wynik lub wyjątki (w przypadku właściwości <xref:System.Threading.Tasks.Task%601>), i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="6d7eb-267">To sprawia, że <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> doskonale nadaje się do użycia w asynchronicznej infrastruktury buforowania.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="6d7eb-268">Oto przykład małego, ale zaawansowanych asynchronicznego pamięci podręcznej skompilowane na <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="6d7eb-269">[AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) jako obiekt delegowany do jej konstruktora klasy akceptuje funkcji, która przyjmuje `TKey` i zwraca <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-269">The [AsyncCache\<TKey,TValue>](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="6d7eb-270">Wszelkie wartości wcześniej używanych z pamięci podręcznej są przechowywane w wewnętrznego słownika i `AsyncCache` gwarantuje, że tylko jedno zadanie jest generowany na klucz, nawet wtedy, gdy pamięć podręczna jest uzyskiwany współbieżnie.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="6d7eb-271">Na przykład można utworzyć pamięć podręczną pobranych stron sieci web:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="6d7eb-272">Następnie można użyć tej pamięci podręcznej w metodach asynchronicznych, zawsze, gdy potrzebujesz zawartość strony sieci web.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="6d7eb-273">`AsyncCache` Klasy gwarantuje, czy są pobierane jako kilka stron, jak to możliwe i pamięci podręczne wyniki.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="6d7eb-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="6d7eb-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="6d7eb-275">Zadania umożliwia również tworzenie struktur danych koordynacji działań asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="6d7eb-276">Jednym z wzorców klasycznego równoległe projektu należy wziąć pod uwagę: producenta i odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="6d7eb-277">W tym wzorcu producentów Generowanie danych, które jest używane przez konsumentów i producentów i konsumentów mogą być wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="6d7eb-278">Na przykład Odbiorca przetwarza pozycji 1, który wcześniej został wygenerowany przez producenta, który jest teraz tworzenie pozycji 2.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="6d7eb-279">Wzorzec producenta i odbiorcy niezmiennie wymaga niektórych elementów struktury danych do przechowywania pracy utworzony przez producentów tak, aby konsumenci mogą otrzymać powiadomienie o nowe dane i znaleźć go, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="6d7eb-280">Oto prosta struktura danych utworzonych na szczycie zadań umożliwiającą metod asynchronicznych, które ma być używany jako producentów i konsumentów:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="6d7eb-281">Za pomocą tej struktury danych w miejscu można napisać kod, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-281">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="6d7eb-282"><xref:System.Threading.Tasks.Dataflow> Przestrzeń nazw zawiera <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, który można użyć w podobny sposób, ale bez konieczności tworzenia niestandardowej kolekcji typów:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="6d7eb-283"><xref:System.Threading.Tasks.Dataflow> Przestrzeni nazw jest dostępna w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] za pośrednictwem **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] through **NuGet**.</span></span> <span data-ttu-id="6d7eb-284">Aby zainstalować zestaw, który zawiera <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w programie Visual Studio, wybierz polecenie **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online pakiet Microsoft.Tpl.Dataflow.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d7eb-285">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d7eb-285">See also</span></span>

- [<span data-ttu-id="6d7eb-286">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="6d7eb-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="6d7eb-287">Implementowanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="6d7eb-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="6d7eb-288">Współdziałanie z innymi wzorcami asynchronicznymi i typami</span><span class="sxs-lookup"><span data-stu-id="6d7eb-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
