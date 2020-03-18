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
ms.openlocfilehash: f80e6ae520ab03c0f5f4edc30c0b7102193ee6c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139818"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="6bfd0-102">Wykorzystywanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="6bfd0-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="6bfd0-103">Korzystając z wzorca asynchronicznego (TAP) opartego na zadaniach do pracy z operacjami asynchronicznymi, można użyć wywołań wywołania wstecznego w celu osiągnięcia oczekiwania bez blokowania.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="6bfd0-104">W przypadku zadań jest to osiągane za pomocą takich metod, jak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6bfd0-105">Obsługa asynchroniczna oparta na języku ukrywa wywołania wywołania wywołań, umożliwiając operacje asynchroniczne, które mają być oczekiwane w ramach normalnego przepływu sterowania, a kod wygenerowany przez kompilator zapewnia tę samą obsługę na poziomie interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="6bfd0-106">Zawieszanie realizacji z await</span><span class="sxs-lookup"><span data-stu-id="6bfd0-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="6bfd0-107">Począwszy od .NET Framework 4.5, można użyć [await](../../csharp/language-reference/operators/await.md) słowa kluczowego w języku C# <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> i [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic asynchronicznie await i obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-107">Starting with the .NET Framework 4.5, you can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="6bfd0-108">Gdy oczekujesz na <xref:System.Threading.Tasks.Task>wyrażenie, `await` jest `void`typu .</span><span class="sxs-lookup"><span data-stu-id="6bfd0-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="6bfd0-109">Gdy oczekujesz na <xref:System.Threading.Tasks.Task%601>wyrażenie, `await` jest `TResult`typu .</span><span class="sxs-lookup"><span data-stu-id="6bfd0-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="6bfd0-110">Wyrażenie `await` musi występować wewnątrz treści metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="6bfd0-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="6bfd0-112">Pod okładkami funkcja await instaluje wywołanie odwetowe zadania przy użyciu kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="6bfd0-113">To wywołanie wsteczne wznawia metodę asynchroniczną w punkcie zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="6bfd0-114">Po wznowieniu metody asynchronicznej, jeśli oczekiwana operacja została ukończona pomyślnie i została zwrócona, <xref:System.Threading.Tasks.Task%601>jej `TResult` jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="6bfd0-115">Jeśli <xref:System.Threading.Tasks.Task> lub, <xref:System.Threading.Tasks.Task%601> że oczekiwano <xref:System.Threading.Tasks.TaskStatus.Canceled> zakończył się <xref:System.OperationCanceledException> w stanie, wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="6bfd0-116">Jeśli <xref:System.Threading.Tasks.Task> lub, <xref:System.Threading.Tasks.Task%601> że oczekiwano <xref:System.Threading.Tasks.TaskStatus.Faulted> zakończył się w stanie, wyjątek, który spowodował jego błąd jest generowany.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="6bfd0-117">A `Task` może błąd w wyniku wielu wyjątków, ale tylko jeden z tych wyjątków jest propagowane.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="6bfd0-118">Jednak <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.AggregateException> wyjątek, który zawiera wszystkie błędy.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="6bfd0-119">Jeśli kontekst synchronizacji<xref:System.Threading.SynchronizationContext> (obiekt) jest skojarzony z wątku, który był wykonywania metody asynchronicznej w czasie zawieszenia (na przykład, jeśli <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> właściwość nie `null`jest <xref:System.Threading.SynchronizationContext.Post%2A> ), metoda asynchroniczna wznawia w tym samym kontekście synchronizacji przy użyciu metody kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="6bfd0-120">W przeciwnym razie opiera się<xref:System.Threading.Tasks.TaskScheduler> na harmonogram zadań (obiekt), który był bieżący w momencie zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="6bfd0-121">Zazwyczaj jest to domyślny harmonogram zadań<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>( ), który jest przeznaczony dla puli wątków.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="6bfd0-122">Ten harmonogram zadań określa, czy oczekiwana operacja asynchroniczna powinna zostać wznowiona tam, gdzie została ukończona, czy też należy zaplanować wznowienie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="6bfd0-123">Domyślny harmonogram zazwyczaj umożliwia kontynuacji do uruchomienia w wątku, który oczekiwaną operację zakończone.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="6bfd0-124">Gdy wywoływana jest metoda asynchroniczna, synchronicznie wykonuje treść funkcji aż do pierwszego wyrażenia await w oczekiwanym wystąpieniu, które nie zostało jeszcze zakończone, w którym to momencie wywołanie zwraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="6bfd0-125">Jeśli metoda asynchroniczna `void`nie <xref:System.Threading.Tasks.Task> zwraca <xref:System.Threading.Tasks.Task%601> , a lub obiekt jest zwracany do reprezentowania bieżących obliczeń.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="6bfd0-126">W metodzie asynchronicznej nievoid, jeśli zostanie napotkana instrukcja zwrotu lub zostanie osiągnięty koniec <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> treści metody, zadanie zostanie ukończone w stanie końcowym.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="6bfd0-127">Jeśli nieobsługiwany wyjątek powoduje, że formant opuści treść metody asynchronicznej, <xref:System.Threading.Tasks.TaskStatus.Faulted> zadanie kończy się w stanie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="6bfd0-128">Jeśli ten wyjątek <xref:System.OperationCanceledException>jest , zadanie <xref:System.Threading.Tasks.TaskStatus.Canceled> zamiast kończy się w stanie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="6bfd0-129">W ten sposób wynik lub wyjątek jest ostatecznie publikowany.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="6bfd0-130">Istnieje kilka ważnych odmian tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="6bfd0-131">Ze względu na wydajność, jeśli zadanie zostało już ukończone do czasu oczekiwania na zadanie, kontrola nie jest ustępowana, a funkcja jest nadal wykonywana.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="6bfd0-132">Ponadto powrót do oryginalnego kontekstu nie zawsze jest żądanym zachowaniem i można je zmienić; jest to opisane bardziej szczegółowo w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="6bfd0-133">Konfigurowanie zawieszenia i wznowienia z wydajnością i configureawait</span><span class="sxs-lookup"><span data-stu-id="6bfd0-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="6bfd0-134">Kilka metod zapewnia większą kontrolę nad wykonaniem metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="6bfd0-135">Na przykład można użyć <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metody, aby wprowadzić punkt wydajności do metody asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="6bfd0-136">Jest to równoważne asynchronicznie księgowania lub planowania z powrotem do bieżącego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

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

 <span data-ttu-id="6bfd0-137">Można również użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metody lepszej kontroli nad zawieszeniem i wznowienie w metodzie asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="6bfd0-138">Jak wspomniano wcześniej, domyślnie bieżący kontekst jest przechwytywany w momencie, gdy metoda asynchroniczna jest zawieszona i że przechwycony kontekst jest używany do wywoływania kontynuacji metody asynchronicznej po wznowieniu.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="6bfd0-139">W wielu przypadkach jest to dokładne zachowanie, które chcesz.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="6bfd0-140">W innych przypadkach może nie dbać o kontekście kontynuacji i można osiągnąć lepszą wydajność, unikając takich wpisów z powrotem do oryginalnego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="6bfd0-141">Aby to włączyć, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> należy użyć metody, aby poinformować oczekiwaną operację nie do przechwytywania i wznowienia w kontekście, ale kontynuować wykonywanie wszędzie tam, gdzie operacja asynchroniczna, która była oczekiwana ukończona:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="6bfd0-142">Anulowanie operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="6bfd0-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="6bfd0-143">Począwszy od .NET Framework 4, metody TAP, które obsługują anulowanie zapewniają<xref:System.Threading.CancellationToken> co najmniej jedno przeciążenie, które akceptuje token anulowania (obiekt).</span><span class="sxs-lookup"><span data-stu-id="6bfd0-143">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="6bfd0-144">Token anulowania jest tworzony za pośrednictwem<xref:System.Threading.CancellationTokenSource> źródła tokenu anulowania (obiektu).</span><span class="sxs-lookup"><span data-stu-id="6bfd0-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="6bfd0-145"><xref:System.Threading.CancellationTokenSource.Token%2A> Właściwość źródła zwraca token anulowania, który zostanie zasygnalizowany, <xref:System.Threading.CancellationTokenSource.Cancel%2A> gdy wywoływana jest metoda źródła.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="6bfd0-146">Na przykład, jeśli chcesz pobrać pojedynczą stronę sieci Web i chcesz mieć <xref:System.Threading.CancellationTokenSource> możliwość anulowania operacji, utwórz obiekt, przekaż jego <xref:System.Threading.CancellationTokenSource.Cancel%2A> token do metody TAP, a następnie wywołaj metodę źródła, gdy będziesz gotowy do anulowania operacji:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="6bfd0-147">Aby anulować wiele wywołań asynchronicznych, można przekazać ten sam token do wszystkich wywołań:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="6bfd0-148">Można również przekazać ten sam token selektywnemu podzbiorowi operacji:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="6bfd0-149">Żądania anulowania mogą być inicjowane z dowolnego wątku.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="6bfd0-150">Można przekazać <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> wartość do dowolnej metody, która akceptuje token anulowania, aby wskazać, że anulowanie nigdy nie będzie wymagane.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="6bfd0-151">Powoduje to, <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> że `false`właściwość do zwrócenia , a wywoływana metoda może odpowiednio zoptymalizować.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="6bfd0-152">Do celów testowych można również przekazać w pre-anulowane token anulowania, który jest tworzony przy użyciu konstruktora, który akceptuje wartość logiczną, aby wskazać, czy token powinien być uruchamiany w stanie już anulowane lub nie można anulować.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="6bfd0-153">Takie podejście do anulowania ma kilka zalet:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="6bfd0-154">Ten sam token anulowania można przekazać do dowolnej liczby operacji asynchronicznych i synchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="6bfd0-155">To samo żądanie anulowania może być mnożyć się do dowolnej liczby słuchaczy.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="6bfd0-156">Deweloper asynchronicznego interfejsu API ma pełną kontrolę nad tym, czy można zażądać anulowania i kiedy może ono wejść w życie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="6bfd0-157">Kod, który zużywa interfejs API może selektywnie określić wywołania asynchroniczne, do których będą propagowane żądania anulowania.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="6bfd0-158">Postęp monitorowania</span><span class="sxs-lookup"><span data-stu-id="6bfd0-158">Monitoring Progress</span></span>
 <span data-ttu-id="6bfd0-159">Niektóre metody asynchroniczne uwidaczniają postęp za pośrednictwem interfejsu postępu przekazywanego do metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="6bfd0-160">Na przykład należy wziąć pod uwagę funkcję, która asynchronicznie pobiera ciąg tekstu, a po drodze wywołuje aktualizacje postępu, które zawierają procent pobierania, który został ukończony do tej pory.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="6bfd0-161">Taka metoda może być używany w aplikacji Windows Presentation Foundation (WPF) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

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
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="6bfd0-162">Korzystanie z wbudowanych kombinatorów zadaniowych</span><span class="sxs-lookup"><span data-stu-id="6bfd0-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="6bfd0-163">Obszar <xref:System.Threading.Tasks> nazw zawiera kilka metod tworzenia i pracy z zadaniami.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="6bfd0-164">Task.run</span><span class="sxs-lookup"><span data-stu-id="6bfd0-164">Task.Run</span></span>
 <span data-ttu-id="6bfd0-165">Klasa <xref:System.Threading.Tasks.Task> zawiera <xref:System.Threading.Tasks.Task.Run%2A> kilka metod, które umożliwiają łatwe <xref:System.Threading.Tasks.Task> odciążanie pracy jako lub <xref:System.Threading.Tasks.Task%601> do puli wątków, na przykład:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

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

 <span data-ttu-id="6bfd0-166">Niektóre z <xref:System.Threading.Tasks.Task.Run%2A> tych metod, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> takich jak przeciążenie, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> istnieją jako skrót dla metody.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="6bfd0-167">Inne przeciążenia, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>takie jak , umożliwiają korzystanie z await w odciążonej pracy, na przykład:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

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

 <span data-ttu-id="6bfd0-168">Takie przeciążenia są logicznie <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> równoważne przy <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> użyciu metody w połączeniu z metodą rozszerzenia w bibliotece równoległej zadania.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="6bfd0-169">Zadanie.FromResult</span><span class="sxs-lookup"><span data-stu-id="6bfd0-169">Task.FromResult</span></span>
 <span data-ttu-id="6bfd0-170">Użyj <xref:System.Threading.Tasks.Task.FromResult%2A> metody w scenariuszach, w których dane mogą być już dostępne i po prostu <xref:System.Threading.Tasks.Task%601>musi zostać zwrócony z metody zwracania zadań zniesione do:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

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

### <a name="taskwhenall"></a><span data-ttu-id="6bfd0-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="6bfd0-171">Task.WhenAll</span></span>
 <span data-ttu-id="6bfd0-172"><xref:System.Threading.Tasks.Task.WhenAll%2A> Użyj metody, aby asynchronicznie czekać na wiele operacji asynchronicznych, które są reprezentowane jako zadania.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="6bfd0-173">Metoda ma wiele przeciążeń, które obsługują zestaw zadań nieogólnych lub niejednolity zestaw zadań ogólnych (na przykład asynchronicznie oczekiwanie na wiele operacji zwracania void lub asynchronicznie oczekiwanie na wiele metod zwracania wartości, gdzie każda wartość `TResult`może mieć inny typ) i do obsługi jednolitego zestawu zadań ogólnych (takich jak asynchronicznie oczekujących na wiele metod zwracania wartości).</span><span class="sxs-lookup"><span data-stu-id="6bfd0-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="6bfd0-174">Załóżmy, że chcesz wysyłać wiadomości e-mail do kilku klientów.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="6bfd0-175">Możesz nakładać się na wysyłanie wiadomości, aby nie czekać na zakończenie jednej wiadomości przed wysłaniem następnej.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="6bfd0-176">Można również dowiedzieć się, kiedy operacje wysyłania zostały zakończone i czy wystąpiły błędy:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="6bfd0-177">Ten kod nie jawnie obsługiwać wyjątki, które mogą wystąpić, ale `await` pozwala wyjątki <xref:System.Threading.Tasks.Task.WhenAll%2A>propagowane z na wynikowe zadanie z .</span><span class="sxs-lookup"><span data-stu-id="6bfd0-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="6bfd0-178">Aby obsłużyć wyjątki, można użyć kodu, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-178">To handle the exceptions, you can use code such as the following:</span></span>

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

 <span data-ttu-id="6bfd0-179">W takim przypadku jeśli jakakolwiek operacja asynchroniczna nie powiedzie się, wszystkie wyjątki zostaną skonsolidowane w wyjątku, <xref:System.AggregateException> który jest przechowywany <xref:System.Threading.Tasks.Task> w, który jest zwracany z <xref:System.Threading.Tasks.Task.WhenAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="6bfd0-180">Jednak tylko jeden z tych wyjątków `await` jest propagowany przez słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="6bfd0-181">Jeśli chcesz sprawdzić wszystkie wyjątki, możesz przepisać poprzedni kod w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

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

 <span data-ttu-id="6bfd0-182">Rozważmy przykład pobierania wielu plików z sieci web asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="6bfd0-183">W takim przypadku wszystkie operacje asynchroniczne mają jednorodne typy wyników i łatwo jest uzyskać dostęp do wyników:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="6bfd0-184">Można użyć tych samych technik obsługi wyjątków omówiono w poprzednim scenariuszu zwracania unieważnienia:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

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

### <a name="taskwhenany"></a><span data-ttu-id="6bfd0-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="6bfd0-185">Task.WhenAny</span></span>
 <span data-ttu-id="6bfd0-186"><xref:System.Threading.Tasks.Task.WhenAny%2A> Metoda służy do asynchronicznego oczekiwania tylko na jedną z wielu operacji asynchronicznych reprezentowanych jako zadania do wykonania.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="6bfd0-187">Ta metoda służy cztery podstawowe przypadki użycia:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="6bfd0-188">Nadmiarowość: wykonywanie operacji wiele razy i wybieranie tej, która kończy się jako pierwsza (na przykład skontaktowanie się z wieloma usługami sieci Web ofert giełdowych, które przyniosą pojedynczy wynik, i wybranie tego, który zakończy najszybszą).</span><span class="sxs-lookup"><span data-stu-id="6bfd0-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="6bfd0-189">Przeplatanie: Rozpoczęcie wielu operacji i oczekiwanie na ich zakończenie, ale przetwarzanie ich po ich zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="6bfd0-190">Ograniczanie przepustowości: umożliwienie rozpoczęcia dodatkowych operacji w miarę ukończenia innych.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="6bfd0-191">Jest to rozszerzenie scenariusza przeplotu.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="6bfd0-192">Wczesne ratowanie: Na przykład operacja reprezentowana przez zadanie t1 <xref:System.Threading.Tasks.Task.WhenAny%2A> może być pogrupowana w zadaniu <xref:System.Threading.Tasks.Task.WhenAny%2A> z innym zadaniem t2 i można poczekać na zadanie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="6bfd0-193">Zadanie t2 może reprezentować uchyłek czasu lub <xref:System.Threading.Tasks.Task.WhenAny%2A> anulowanie lub inny sygnał, który powoduje zakończenie zadania przed zakończeniem t1.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="6bfd0-194">Nadmiarowość</span><span class="sxs-lookup"><span data-stu-id="6bfd0-194">Redundancy</span></span>
 <span data-ttu-id="6bfd0-195">Rozważmy przypadek, w którym chcesz podjąć decyzję o tym, czy kupić akcje.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="6bfd0-196">Istnieje kilka usług sieci Web rekomendacji giełdowych, które ufasz, ale w zależności od codziennego obciążenia, każda usługa może skończyć się powolne w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="6bfd0-197">Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody, aby otrzymywać powiadomienia po zakończeniu dowolnej operacji:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

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

 <span data-ttu-id="6bfd0-198">W <xref:System.Threading.Tasks.Task.WhenAll%2A>przeciwieństwie do , który zwraca nieopakowane wyniki <xref:System.Threading.Tasks.Task.WhenAny%2A> wszystkich zadań, które zakończyły się pomyślnie, zwraca zadanie, które zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="6bfd0-199">Jeśli zadanie nie powiedzie się, ważne jest, aby wiedzieć, że nie powiodło się, a jeśli zadanie zakończy się pomyślnie, ważne jest, aby wiedzieć, z którym zadaniem jest skojarzona wartość zwracana.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="6bfd0-200">W związku z tym należy uzyskać dostęp do wyniku zwróconego zadania lub dalej czekać na niego, jak pokazano w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="6bfd0-201">Podobnie <xref:System.Threading.Tasks.Task.WhenAll%2A>jak w przypadku , musisz być w stanie pomieścić wyjątki.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="6bfd0-202">Ponieważ otrzymasz ukończone zadanie z powrotem, można oczekiwać na zwrócone `try/catch` zadanie, aby błędy propagowane i odpowiednio je; na przykład:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

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

 <span data-ttu-id="6bfd0-203">Ponadto nawet jeśli pierwsze zadanie zakończy się pomyślnie, kolejne zadania mogą zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="6bfd0-204">W tym momencie masz kilka opcji radzenia sobie z wyjątkami: Możesz poczekać, aż wszystkie uruchomione zadania <xref:System.Threading.Tasks.Task.WhenAll%2A> zostały zakończone, w którym to przypadku można użyć metody, lub można zdecydować, że wszystkie wyjątki są ważne i muszą być rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="6bfd0-205">W tym celu można użyć kontynuacji, aby otrzymywać powiadomienia, gdy zadania zostały zakończone asynchronicznie:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="6bfd0-206">lub:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="6bfd0-207">lub nawet:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-207">or even:</span></span>

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

 <span data-ttu-id="6bfd0-208">Na koniec można anulować wszystkie pozostałe operacje:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-208">Finally, you may want to cancel all the remaining operations:</span></span>

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

#### <a name="interleaving"></a><span data-ttu-id="6bfd0-209">Przeplataniem</span><span class="sxs-lookup"><span data-stu-id="6bfd0-209">Interleaving</span></span>
 <span data-ttu-id="6bfd0-210">Rozważmy przypadek, w którym pobierasz obrazy z sieci Web i przetwarzasz każdy obraz (na przykład dodając obraz do kontrolki interfejsu użytkownika).</span><span class="sxs-lookup"><span data-stu-id="6bfd0-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="6bfd0-211">Musisz wykonać przetwarzanie sekwencyjnie w wątku interfejsu użytkownika, ale chcesz pobrać obrazy tak równocześnie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="6bfd0-212">Ponadto nie chcesz wstrzymywać dodawania obrazów do interfejsu, dopóki nie zostaną pobrane — chcesz dodać je po ich zakończeniu:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

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

 <span data-ttu-id="6bfd0-213">Można również zastosować przeplot do scenariusza, który obejmuje <xref:System.Threading.ThreadPool> obliczeniowo intensywne przetwarzanie na pobranych obrazów; na przykład:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

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

#### <a name="throttling"></a><span data-ttu-id="6bfd0-214">Ograniczanie przepływności</span><span class="sxs-lookup"><span data-stu-id="6bfd0-214">Throttling</span></span>
 <span data-ttu-id="6bfd0-215">Należy wziąć pod uwagę przykład przeplotu, z tą różnicą, że użytkownik pobiera tak wiele obrazów, że pliki do pobrania muszą być ograniczane; na przykład chcesz, aby tylko określona liczba pobrań odbywała się jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="6bfd0-216">Aby to osiągnąć, można uruchomić podzbiór operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="6bfd0-217">Po zakończeniu operacji można rozpocząć dodatkowe operacje, aby zająć ich miejsce:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-217">As operations complete, you can start additional operations to take their place:</span></span>

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

#### <a name="early-bailout"></a><span data-ttu-id="6bfd0-218">Wczesne ratowanie</span><span class="sxs-lookup"><span data-stu-id="6bfd0-218">Early Bailout</span></span>
 <span data-ttu-id="6bfd0-219">Należy wziąć pod uwagę, że oczekujesz asynchronicznie na operację, aby zakończyć jednocześnie odpowiadając na żądanie anulowania użytkownika (na przykład użytkownik kliknął przycisk anuluj).</span><span class="sxs-lookup"><span data-stu-id="6bfd0-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="6bfd0-220">Poniższy kod ilustruje ten scenariusz:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-220">The following code illustrates this scenario:</span></span>

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

 <span data-ttu-id="6bfd0-221">Ta implementacja ponownie włącza interfejs użytkownika, gdy tylko zdecydujesz się na ratowanie, ale nie anuluje podstawowych operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="6bfd0-222">Inną alternatywą byłoby anulowanie oczekujących operacji, gdy zdecydujesz się na ratowanie, ale nie ponowne ustanowienie interfejsu użytkownika, dopóki operacje faktycznie nie zostaną zakończone, potencjalnie z powodu wcześniejszego zakończenia z powodu żądania anulowania:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

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

 <span data-ttu-id="6bfd0-223">Innym przykładem wczesnego ratowania <xref:System.Threading.Tasks.Task.WhenAny%2A> polega na <xref:System.Threading.Tasks.Task.Delay%2A> użyciu metody w połączeniu z metodą, jak omówiono w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="6bfd0-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="6bfd0-224">Task.Delay</span></span>
 <span data-ttu-id="6bfd0-225">Metoda służy <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> do wprowadzania pauz y do wykonania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="6bfd0-226">Jest to przydatne w przypadku wielu rodzajów funkcji, w tym tworzenia pętli sondowania i opóźniania obsługi danych wejściowych użytkownika przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="6bfd0-227">Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> może być również przydatne <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> w połączeniu z implementacji uchyliń czasu na czeka.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="6bfd0-228">Jeśli zadanie, które jest częścią większej operacji asynchronicznej (na przykład ASP.NET usługi sieci web) trwa zbyt długo, aby zakończyć, ogólna operacja może ucierpieć, zwłaszcza jeśli nigdy nie ukończ.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="6bfd0-229">Z tego powodu ważne jest, aby mieć możliwość uchylania się czasu podczas oczekiwania na operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="6bfd0-230">Synchroniczne <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody akceptują wartości czasu uporu, ale odpowiednie <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> i wcześniej wymienione <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody nie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="6bfd0-231">Zamiast tego można <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> użyć i w połączeniu zaimplementować uchył.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="6bfd0-232">Na przykład w aplikacji interfejsu użytkownika załóżmy, że chcesz pobrać obraz i wyłączyć interfejs użytkownika podczas pobierania obrazu.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="6bfd0-233">Jeśli jednak pobieranie trwa zbyt długo, chcesz ponownie włączyć ui i odrzucić pobieranie:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

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

 <span data-ttu-id="6bfd0-234">To samo dotyczy wielu pobrań, ponieważ <xref:System.Threading.Tasks.Task.WhenAll%2A> zwraca zadanie:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

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

## <a name="building-task-based-combinators"></a><span data-ttu-id="6bfd0-235">Tworzenie kombinatorów opartych na zadaniach</span><span class="sxs-lookup"><span data-stu-id="6bfd0-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="6bfd0-236">Ponieważ zadanie jest w stanie całkowicie reprezentować operację asynchroniczną i zapewnić synchroniczne i asynchroniczne możliwości łączenia się z operacją, pobieranie jej wyników itd., można tworzyć przydatne biblioteki kombinatorów, które rekomponują zadania do tworzyć większe wzory.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="6bfd0-237">Jak omówiono w poprzedniej sekcji .NET Framework zawiera kilka wbudowanych kombinatorów, ale można również tworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="6bfd0-238">W poniższych sekcjach podano kilka przykładów potencjalnych metod i typów kombinatora.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="6bfd0-239">Ponowiony błąd</span><span class="sxs-lookup"><span data-stu-id="6bfd0-239">RetryOnFault</span></span>
 <span data-ttu-id="6bfd0-240">W wielu sytuacjach można ponowić próbę wykonania operacji, jeśli poprzednia próba nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="6bfd0-241">W przypadku kodu synchronicznego można utworzyć metodę `RetryOnFault` pomocnika, na przykład w poniższym przykładzie, aby to osiągnąć:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

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

 <span data-ttu-id="6bfd0-242">Można utworzyć prawie identyczną metodę pomocnika dla operacji asynchronicznych, które są implementowane za pomocą tap, a tym samym zwracać zadania:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

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

 <span data-ttu-id="6bfd0-243">Następnie można użyć tego kombinatora do kodowania ponownych prób do logiki aplikacji; na przykład:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="6bfd0-244">Można rozszerzyć `RetryOnFault` funkcję dalej.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="6bfd0-245">Na przykład funkcja może `Func<Task>` zaakceptować inny, który zostanie wywołany między ponownych prób, aby określić, kiedy ponownie spróbować wykonać operację; na przykład:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

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

 <span data-ttu-id="6bfd0-246">Następnie można użyć funkcji w następujący sposób czekać na sekundę przed ponowieniem próby operacji:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="6bfd0-247">NeedOnlyOne (NeedOnlyOne)</span><span class="sxs-lookup"><span data-stu-id="6bfd0-247">NeedOnlyOne</span></span>
 <span data-ttu-id="6bfd0-248">Czasami można skorzystać z nadmiarowości, aby zwiększyć opóźnienie operacji i szanse na powodzenie.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="6bfd0-249">Należy wziąć pod uwagę wiele usług internetowych, które zapewniają notowania giełdowe, ale o różnych porach dnia, każda usługa może zapewnić różne poziomy jakości i czasu reakcji.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="6bfd0-250">Aby poradzić sobie z tymi wahaniami, możesz wysyłać żądania do wszystkich usług sieci web, a gdy tylko otrzymasz odpowiedź od jednego, anuluj pozostałe żądania.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="6bfd0-251">Można zaimplementować funkcję pomocnika, aby ułatwić implementowanie tego wspólnego wzorca uruchamiania wielu operacji, oczekiwanie na dowolne, a następnie anulowanie reszty.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="6bfd0-252">Funkcja `NeedOnlyOne` w poniższym przykładzie ilustruje ten scenariusz:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

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

 <span data-ttu-id="6bfd0-253">Następnie można użyć tej funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="6bfd0-254">Operacje z przeplotem</span><span class="sxs-lookup"><span data-stu-id="6bfd0-254">Interleaved Operations</span></span>
 <span data-ttu-id="6bfd0-255">Istnieje potencjalny problem z wydajnością przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> metody do obsługi scenariusza przeplotu podczas pracy z bardzo dużymi zestawami zadań.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span> <span data-ttu-id="6bfd0-256">Każde wywołanie powoduje <xref:System.Threading.Tasks.Task.WhenAny%2A> kontynuacji są rejestrowane z każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="6bfd0-257">W przypadku N liczby zadań powoduje to kontynuacje O(N<sup>2)</sup>utworzone przez cały okres istnienia operacji przeplotu.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-257">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="6bfd0-258">Jeśli pracujesz z dużym zestawem zadań, możesz użyć`Interleaved` kombinatora (w poniższym przykładzie) w celu rozwiązania problemu z wydajnością:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-258">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

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

 <span data-ttu-id="6bfd0-259">Następnie można użyć kombinatora do przetwarzania wyników zadań podczas ich wykonywania; na przykład:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="6bfd0-260">WhenAllOrFirstException (Pierwszy wyjątek od WhenAllOrFirstException)</span><span class="sxs-lookup"><span data-stu-id="6bfd0-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="6bfd0-261">W niektórych scenariuszach scatter/gather można poczekać na wszystkie zadania w zestawie, chyba że jeden z nich błędy, w którym to przypadku chcesz przestać czekać, jak tylko wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="6bfd0-262">Można to osiągnąć za pomocą metody `WhenAllOrFirstException` kombinatora, takich jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

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

## <a name="building-task-based-data-structures"></a><span data-ttu-id="6bfd0-263">Tworzenie struktur danych opartych na zadaniach</span><span class="sxs-lookup"><span data-stu-id="6bfd0-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="6bfd0-264">Oprócz możliwości tworzenia niestandardowych kombinatorów opartych na zadaniach, o strukturę danych i <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> który reprezentuje zarówno wyniki operacji asynchronicznej i niezbędne synchronizacji do przyłączenia się z nim sprawia, że bardzo zaawansowany typ, na którym do tworzenia struktur danych niestandardowych, które mają być używane w scenariuszach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="6bfd0-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="6bfd0-265">AsyncCache</span></span>
 <span data-ttu-id="6bfd0-266">Ważnym aspektem zadania jest to, że może być rozdawane wielu konsumentom, z których wszyscy mogą na niego czekać, <xref:System.Threading.Tasks.Task%601>rejestrować z nim kontynuacje, uzyskać jego wynik lub wyjątki (w przypadku ) i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="6bfd0-267">To <xref:System.Threading.Tasks.Task> sprawia, że i <xref:System.Threading.Tasks.Task%601> doskonale nadaje się do użycia w infrastrukturze buforowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="6bfd0-268">Oto przykład małej, ale potężnej asynchronicznej <xref:System.Threading.Tasks.Task%601>pamięci podręcznej zbudowanej na wierzchu:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

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

 <span data-ttu-id="6bfd0-269">[AsyncCache\<TKey, TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) klasa akceptuje jako delegat do swojego konstruktora <xref:System.Threading.Tasks.Task%601>funkcji, która przyjmuje `TKey` i zwraca .</span><span class="sxs-lookup"><span data-stu-id="6bfd0-269">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="6bfd0-270">Wszystkie wcześniej dostępne wartości z pamięci podręcznej są przechowywane `AsyncCache` w słowniku wewnętrznym, a zapewnia, że tylko jedno zadanie jest generowane na klucz, nawet jeśli pamięć podręczna jest jednocześnie dostępna.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="6bfd0-271">Na przykład można utworzyć pamięć podręczną dla pobranych stron internetowych:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="6bfd0-272">Następnie można użyć tej pamięci podręcznej w metodach asynchronicznych, gdy potrzebujesz zawartości strony sieci web.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="6bfd0-273">Klasa `AsyncCache` zapewnia, że pobierasz jak najmniej stron i buforuje wyniki.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

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

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="6bfd0-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="6bfd0-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="6bfd0-275">Za pomocą zadań można również tworzyć struktury danych do koordynowania działań asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="6bfd0-276">Rozważmy jeden z klasycznych wzorców projektowania równoległego: producent/ konsument.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="6bfd0-277">W tym wzorzec producenci generują dane, które są zużywane przez konsumentów, a producenci i konsumenci mogą działać równolegle.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="6bfd0-278">Na przykład konsument przetwarza element 1, który został wcześniej wygenerowany przez producenta, który obecnie produkuje towar 2.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="6bfd0-279">W przypadku struktury producenta/konsumenta niezmiennie potrzebna jest struktura danych do przechowywania prac stworzonych przez producentów, tak aby konsumenci mogli być powiadamiani o nowych danych i znajdować je, gdy są one dostępne.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="6bfd0-280">Oto prosta struktura danych zbudowana na zadaniach, która umożliwia metody asynchroniczne, które mają być używane jako producenci i konsumenci:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

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

 <span data-ttu-id="6bfd0-281">Dzięki tej strukturze danych w miejscu, można napisać kod, takich jak:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-281">With that data structure in place, you can write code such as the following:</span></span>

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

<span data-ttu-id="6bfd0-282">Obszar <xref:System.Threading.Tasks.Dataflow> nazw zawiera <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, którego można używać w podobny sposób, ale bez konieczności tworzenia niestandardowego typu kolekcji:</span><span class="sxs-lookup"><span data-stu-id="6bfd0-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

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
> <span data-ttu-id="6bfd0-283">Obszar <xref:System.Threading.Tasks.Dataflow> nazw jest dostępny w .NET Framework 4.5 przez **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="6bfd0-284">Aby zainstalować zestaw <xref:System.Threading.Tasks.Dataflow> zawierający obszar nazw, otwórz projekt w programie Visual Studio, wybierz polecenie **Zarządzaj pakietami NuGet** z menu Projekt i wyszukaj w trybie online pakiet Microsoft.Tpl.Dataflow.</span><span class="sxs-lookup"><span data-stu-id="6bfd0-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bfd0-285">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bfd0-285">See also</span></span>

- [<span data-ttu-id="6bfd0-286">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="6bfd0-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="6bfd0-287">Implementacja wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="6bfd0-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="6bfd0-288">Współdziałanie z innymi wzorcami asynchronicznymi i typami</span><span class="sxs-lookup"><span data-stu-id="6bfd0-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
