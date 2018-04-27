---
title: Wykorzystywanie wzorca asynchronicznego opartego na zadaniach
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eb1b73af4ccdc22e811988450824123c0055d9e6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="ac8a7-102">Wykorzystywanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="ac8a7-102">Consuming the Task-based Asynchronous Pattern</span></span>
<span data-ttu-id="ac8a7-103">Gdy używasz opartego na zadaniach asynchronicznej wzorca (TAP) do pracy z operacji asynchronicznych służy wywołań zwrotnych do osiągnięcia oczekiwania bez blokowania.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="ac8a7-104">W przypadku zadań to odbywa się za pośrednictwem metody takie jak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac8a7-105">Obsługa komunikacji asynchronicznej opartych na języku ukrywa wywołania zwrotne zezwalając operacji asynchronicznych do dokumentów, w ramach przepływu sterowania normalne i kod wygenerowany przez kompilator obsługuje ten sam poziom interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>  
  
## <a name="suspending-execution-with-await"></a><span data-ttu-id="ac8a7-106">Wstrzymywanie wykonywania z Await</span><span class="sxs-lookup"><span data-stu-id="ac8a7-106">Suspending Execution with Await</span></span>  
 <span data-ttu-id="ac8a7-107">Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], można użyć [await](~/docs/csharp/language-reference/keywords/await.md) — słowo kluczowe języka C# i [operatora Await](~/docs/visual-basic/language-reference/operators/await-operator.md) w języku Visual Basic asynchronicznie oczekują na <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-107">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can use the [await](~/docs/csharp/language-reference/keywords/await.md) keyword in C# and the [Await Operator](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="ac8a7-108">Gdy jest oczekiwanie na <xref:System.Threading.Tasks.Task>, `await` wyrażenie jest typu `void`.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="ac8a7-109">Gdy jest oczekiwanie na <xref:System.Threading.Tasks.Task%601>, `await` wyrażenie jest typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="ac8a7-110">`await` Wyrażenie musi wystąpić w treści metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="ac8a7-111">Aby uzyskać więcej informacji na temat języka C# i Visual Basic obsługuje w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobacz specyfikacje języka C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-111">For more information about C# and Visual Basic language support in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see the C# and Visual Basic language specifications.</span></span>  
  
 <span data-ttu-id="ac8a7-112">W obszarze obejmuje funkcje await instaluje wywołanie zwrotne zadania za pomocą utrzymania.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="ac8a7-113">To wywołanie zwrotne wznawia metod asynchronicznych w punkcie zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="ac8a7-114">Po wznowieniu metod asynchronicznych Jeśli oczekiwano operacja zakończyła się pomyślnie i został <xref:System.Threading.Tasks.Task%601>, jego `TResult` jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="ac8a7-115">Jeśli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> który oczekiwany zakończone w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu, <xref:System.OperationCanceledException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="ac8a7-116">Jeśli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> który oczekiwany zakończone w <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu jest zwracany wyjątek, który spowodował błąd.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="ac8a7-117">A `Task` można błędów wyniku wiele wyjątków, ale tylko jeden z tych wyjątków są propagowane.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="ac8a7-118">Jednak <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> zwraca <xref:System.AggregateException> wyjątek, który zawiera wszystkie błędy.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>  
  
 <span data-ttu-id="ac8a7-119">Jeśli kontekst synchronizacji (<xref:System.Threading.SynchronizationContext> obiektu) jest skojarzony z wątkiem wykonywanej metody asynchronicznej w chwili zawieszenia (na przykład, jeśli <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> właściwość nie jest `null`), metoda asynchroniczna wznawia na tym tego samego kontekstu synchronizacji przy użyciu kontekstu <xref:System.Threading.SynchronizationContext.Post%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="ac8a7-120">W przeciwnym razie polega na harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler> obiektu) który były aktualne w chwili zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="ac8a7-121">Zazwyczaj jest to domyślny harmonogram zadań (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), który jest przeznaczony dla puli wątków.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="ac8a7-122">Ten harmonogram zadania określa, czy Oczekiwano operacji asynchronicznej powinien wznowić, gdy zakończy pracę, lub czy powinny zostać zaplanowane wznowienie.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="ac8a7-123">Domyślny harmonogram umożliwia zwykle kontynuacji do uruchamiania w wątku, który zakończył Oczekiwano operacji.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>  
  
 <span data-ttu-id="ac8a7-124">Po wywołaniu metody asynchronicznej synchronicznie wykonywania treści funkcji dopóki pierwsza await wyrażenia na oczekujący wystąpienie, które nie zostało jeszcze zakończone, w którym wywołanie zwraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="ac8a7-125">Jeśli metoda asynchroniczna nie zwraca `void`, <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiekt jest zwracany do reprezentowania trwającą obliczeń.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="ac8a7-126">W metodzie asynchronicznej niż void, jeśli instrukcja return lub jest osiągnięty koniec treści metody, zadanie zostanie ukończone w <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stan końcowy.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="ac8a7-127">Jeśli wystąpił nieobsługiwany wyjątek powoduje, że formant opuścić tekstu metody asynchronicznej, zadanie kończy się <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="ac8a7-128">Jeśli ten wyjątek jest <xref:System.OperationCanceledException>, zamiast tego zadania kończy się na <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="ac8a7-129">W ten sposób wynik lub wyjątek ostatecznie jest opublikowana.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-129">In this manner, the result or exception is eventually published.</span></span>  
  
 <span data-ttu-id="ac8a7-130">Istnieje kilka ważnych zmian tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="ac8a7-131">Ze względu na wydajność Jeśli zadanie zostało już ukończone w czasie zadania jest oczekiwane, formantu nie jest uzyskane i kontynuuje wykonywanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="ac8a7-132">Ponadto wracając do oryginalnego kontekstu nie zawsze jest zamierzone zachowanie i może zostać zmieniona; jest to opisane bardziej szczegółowo w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="ac8a7-133">Konfigurowanie zawieszenia i wznowienia z wydajności i ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="ac8a7-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>  
 <span data-ttu-id="ac8a7-134">Kilka metod zapewniają większą kontrolę nad wykonanie metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="ac8a7-135">Na przykład można użyć <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> metody wprowadzenie punktu yield do metod asynchronicznych:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 <span data-ttu-id="ac8a7-136">Jest to równoważne asynchronicznie księgowej lub planowania bieżącego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-137">Można również użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metody dla lepszej kontroli nad zawieszenia i wznowienia w metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="ac8a7-138">Jak wspomniano wcześniej, domyślnie bieżącego kontekstu jest przechwytywany w momencie metody asynchronicznej jest wstrzymana, a tego kontekstu przechwyconych służy do wywoływania metody asynchronicznej kontynuacji po wznowieniu.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="ac8a7-139">W wielu przypadkach to zachowanie dokładne, który ma.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="ac8a7-140">W innych przypadkach może nie zależy Ci kontekstu kontynuacji, a można osiągnąć lepszą wydajność dzięki unikaniu takie stanowiska wstecz do oryginalnego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="ac8a7-141">Aby włączyć tę opcję, należy użyć <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> metodę, aby poinformować operacji await nie do przechwytywania i wznowić w kontekście, ale do kontynuowania wykonywania wszędzie tam, gdzie ukończyć operację asynchroniczną, która jest oczekiwany:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="ac8a7-142">Anulowanie operacji asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="ac8a7-142">Canceling an Asynchronous Operation</span></span>  
 <span data-ttu-id="ac8a7-143">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], NACIŚNIJ metody, które obsługuje anulowania Podaj co najmniej jedno przeciążenie akceptuje token anulowania (<xref:System.Threading.CancellationToken> obiektu).</span><span class="sxs-lookup"><span data-stu-id="ac8a7-143">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>  
  
 <span data-ttu-id="ac8a7-144">Token anulowania jest tworzony przez źródło token anulowania (<xref:System.Threading.CancellationTokenSource> obiektu).</span><span class="sxs-lookup"><span data-stu-id="ac8a7-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="ac8a7-145">Źródło <xref:System.Threading.CancellationTokenSource.Token%2A> właściwość zwraca token anulowania, który zostanie zasygnalizowane podczas źródła <xref:System.Threading.CancellationTokenSource.Cancel%2A> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="ac8a7-146">Na przykład, jeśli chcesz pobrać pojedyncza strona sieci Web i chcesz mieć możliwość anulowania operacji, należy utworzyć <xref:System.Threading.CancellationTokenSource> obiektów, Przekaż token jej do metody NACIŚNIJ, a następnie wywołać źródła <xref:System.Threading.CancellationTokenSource.Cancel%2A> metody, gdy wszystko jest gotowe do anulowania operacji:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 <span data-ttu-id="ac8a7-147">Aby anulować wiele wywołań asynchronicznych, można przekazać tego samego tokenu do wszystkich wywołań:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 <span data-ttu-id="ac8a7-148">Lub można przekazać tego samego tokenu do selektywnego podzbiór operacje:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-148">Or, you can pass the same token to a selective subset of operations:</span></span>  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 <span data-ttu-id="ac8a7-149">Żądania anulowania można zainicjować z dowolnego wątku.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-149">Cancellation requests may be initiated from any thread.</span></span>  
  
 <span data-ttu-id="ac8a7-150">Można przekazać <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> wartość do dowolnej metody, która akceptuje token anulowania, aby wskazać, że anulowania nigdy nie będzie wymagane.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="ac8a7-151">Powoduje to <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> właściwości do zwrócenia `false`, i odpowiednio zoptymalizować wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="ac8a7-152">Do celów testowych można również przekazać token anulowania wstępnie anulowane, który zostanie uruchomiony przy użyciu konstruktora, który akceptuje wartość logiczna wskazująca, czy token powinna uruchomić się w stanie już anulowana lub nie można anulować.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>  
  
 <span data-ttu-id="ac8a7-153">Takie podejście do anulowania ma kilka zalet:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-153">This approach to cancellation has several advantages:</span></span>  
  
-   <span data-ttu-id="ac8a7-154">Ten sam token anulowania można przekazać do dowolnej liczby operacji synchronicznego i asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>  
  
-   <span data-ttu-id="ac8a7-155">Tym samym żądanie anulowania może proliferated na dowolną liczbę odbiorników.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-155">The same cancellation request may be proliferated to any number of listeners.</span></span>  
  
-   <span data-ttu-id="ac8a7-156">Deweloper asynchronicznego interfejsu API ma pełną kontrolę nad czy anulowania można zażądać i kiedy mogą zostać zastosowane.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>  
  
-   <span data-ttu-id="ac8a7-157">Kod, który wykorzystuje interfejs API selektywnie mogą określić wywołania asynchroniczne, które żądań anulowania będzie propagowane do.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>  
  
## <a name="monitoring-progress"></a><span data-ttu-id="ac8a7-158">Postęp monitorowania</span><span class="sxs-lookup"><span data-stu-id="ac8a7-158">Monitoring Progress</span></span>  
 <span data-ttu-id="ac8a7-159">W przypadku niektórych metod asynchronicznych ujawnia postęp za pośrednictwem interfejsu postępu przekazany do metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="ac8a7-160">Na przykład należy rozważyć funkcja, która asynchronicznie pobiera ciąg tekstu i wzdłuż sposób zgłasza aktualizacje postępu, zawierające procent pobieranie, które zostało zakończone w związku z tym do tej pory.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="ac8a7-161">Taka metoda może być używana w aplikacji Windows Presentation Foundation (WPF) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>  
  
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
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="ac8a7-162">Za pomocą wbudowanych Combinators opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="ac8a7-162">Using the Built-in Task-based Combinators</span></span>  
 <span data-ttu-id="ac8a7-163"><xref:System.Threading.Tasks> Przestrzeń nazw zawiera kilka metod tworzenia i pracy z zadaniami.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>  
  
### <a name="taskrun"></a><span data-ttu-id="ac8a7-164">Task.Run</span><span class="sxs-lookup"><span data-stu-id="ac8a7-164">Task.Run</span></span>  
 <span data-ttu-id="ac8a7-165"><xref:System.Threading.Tasks.Task> Klasy zawiera kilka <xref:System.Threading.Tasks.Task.Run%2A> metod, które pozwalają łatwo odciążania pracy jako <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> do puli wątków, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-166">Niektóre z nich <xref:System.Threading.Tasks.Task.Run%2A> metod, takich jak <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> przeciążenia, istnieje jako skrócona forma <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="ac8a7-167">Overloads innych, takie jak <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, Włącz można używać operatora await w ramach Odciążone pracy, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-168">Takie przeciążenia są logicznie równoważne użyciu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> w połączeniu z metody <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> — metoda rozszerzenia w bibliotece równoległych zadań.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>  
  
### <a name="taskfromresult"></a><span data-ttu-id="ac8a7-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="ac8a7-169">Task.FromResult</span></span>  
 <span data-ttu-id="ac8a7-170">Użyj <xref:System.Threading.Tasks.Task.FromResult%2A> metody w scenariuszach, w których dane mogą być już dostępne, a tylko musi zwracaną z metody umożliwiające zwracanie zadań unosiło do <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>  
  
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
  
### <a name="taskwhenall"></a><span data-ttu-id="ac8a7-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="ac8a7-171">Task.WhenAll</span></span>  
 <span data-ttu-id="ac8a7-172">Użyj <xref:System.Threading.Tasks.Task.WhenAll%2A> metody asynchronicznie oczekiwania na wiele operacji asynchronicznych, które są reprezentowane jako zadania.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="ac8a7-173">Metoda ma kilka przeciążeń, które obsługuje zestaw zadań nierodzajową lub zestawu niejednolitego ogólnych zadań (na przykład asynchronicznie oczekiwanie na wiele operacji zwracające typ void lub asynchronicznie oczekiwanie na wiele metod zwracających wartość gdzie Każda wartość może być innego typu) która obsługuje jednolitego zestaw ogólnych zadań (takich jak asynchronicznie oczekiwanie na wielu `TResult`-zwracanie metody).</span><span class="sxs-lookup"><span data-stu-id="ac8a7-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>  
  
 <span data-ttu-id="ac8a7-174">Załóżmy, że chcesz wysyłać wiadomości e-mail do wielu klientów.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="ac8a7-175">Możesz mogą nakładać się na wysyłanie wiadomości, więc nie oczekiwania dla jednego komunikatu do wykonania przed wysłaniem następnego.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="ac8a7-176">Można również sprawdzić po ukończeniu operacji wysyłania i określa, czy wystąpiły błędy:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 <span data-ttu-id="ac8a7-177">Ten kod nie jawnie obsługi wyjątków, które mogą wystąpić, ale umożliwia propagowanie poza wyjątkami `await` w zadaniu wynikowym z <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="ac8a7-178">Do obsługi wyjątków, można użyć kodu, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-178">To handle the exceptions, you can use code such as the following:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-179">W tym przypadku jeśli żadnej operacji asynchronicznych nie powiedzie się, wszystkie wyjątki zostaną skonsolidowane w w <xref:System.AggregateException> wyjątek, który jest przechowywany w <xref:System.Threading.Tasks.Task> zwracanego z <xref:System.Threading.Tasks.Task.WhenAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="ac8a7-180">Jednak tylko jeden z tych wyjątków są propagowane przy `await` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="ac8a7-181">Jeśli chcesz sprawdzić wszystkie wyjątki, poprzedni kod można przepisać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-182">Zastanówmy się z przykładem asynchronicznie pobrania wiele plików w sieci web.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="ac8a7-183">W takim przypadku wszystkich operacji asynchronicznych mają typy wyników jednorodne i łatwo uzyskać dostępu do wyników:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 <span data-ttu-id="ac8a7-184">Można używać tych samych metod obsługi wyjątków, które omówiono w poprzednim scenariuszu zwracające typ void:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>  
  
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
  
### <a name="taskwhenany"></a><span data-ttu-id="ac8a7-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="ac8a7-185">Task.WhenAny</span></span>  
 <span data-ttu-id="ac8a7-186">Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody asynchronicznie oczekuje tylko jednego z wielu operacji asynchronicznych reprezentowane jako zadania do wykonania.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="ac8a7-187">Ta metoda służy cztery przypadki użycia głównej:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-187">This method serves four primary use cases:</span></span>  
  
-   <span data-ttu-id="ac8a7-188">Nadmiarowość: Wykonywanie operacji wielokrotnie i wybierania odpowiedniego zakończeniu pierwszego (na przykład kontaktowania się z wielu usług sieci web giełdowych powodującymi jeden wynik i wybierania odpowiedniego kończące najszybsze).</span><span class="sxs-lookup"><span data-stu-id="ac8a7-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>  
  
-   <span data-ttu-id="ac8a7-189">Z przeplotem: Uruchamianie wielu operacji i Oczekiwanie na ich zakończenie wszystkich, ale przetwarzanie ich w chwili zakończenia.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>  
  
-   <span data-ttu-id="ac8a7-190">Ograniczanie: Stosowanie dodatkowe operacje rozpocząć w innym zakończenia.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="ac8a7-191">To rozszerzenie interleaving scenariusza.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-191">This is an extension of the interleaving scenario.</span></span>  
  
-   <span data-ttu-id="ac8a7-192">Wczesne podejmowano: na przykład operacji reprezentowany przez t1 zadania można grupować w <xref:System.Threading.Tasks.Task.WhenAny%2A> zadań z innym t2 zadań, a może czekać <xref:System.Threading.Tasks.Task.WhenAny%2A> zadań.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="ac8a7-193">Zadanie t2 może reprezentować limit czasu lub anulowania lub innych sygnał, który powoduje, że <xref:System.Threading.Tasks.Task.WhenAny%2A> zadań do wykonania przed zakończeniem t1.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>  
  
#### <a name="redundancy"></a><span data-ttu-id="ac8a7-194">Nadmiarowość</span><span class="sxs-lookup"><span data-stu-id="ac8a7-194">Redundancy</span></span>  
 <span data-ttu-id="ac8a7-195">Rozważmy, której chcesz podjęcie decyzji o tym, czy kupić zasobu.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="ac8a7-196">Istnieje kilka usług sieci web standardowych zalecenie zaufanych, ale w zależności od obciążenia codzienne każdej usługi można przechodzili powolnych w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="ac8a7-197">Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody, aby otrzymać powiadomienie po zakończeniu każdej operacji:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-198">W odróżnieniu od <xref:System.Threading.Tasks.Task.WhenAll%2A>, które zwraca wyniki bez otoki wszystkich zadań, które ukończone pomyślnie, <xref:System.Threading.Tasks.Task.WhenAny%2A> zwraca zadania, które wykonane.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="ac8a7-199">Jeśli zadanie nie powiedzie się, należy wiedzieć, że nie powiodło się, a jeśli zadanie zakończy się powodzeniem, ważne jest, aby wiedzieć, które zadanie wartość zwracana jest skojarzony z.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="ac8a7-200">Należy więc dostęp do wyniku zadania zwróconego lub dalsze await, jak pokazano na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>  
  
 <span data-ttu-id="ac8a7-201">Jak <xref:System.Threading.Tasks.Task.WhenAll%2A>, muszą być w stanie wyjątkami.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="ac8a7-202">Ponieważ zostanie wyświetlony ponownie ukończonego zadania, można zdefiniować oczekiwania zadanie zwrócone błędy propagacji i `try/catch` ich odpowiednio; na przykład:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-203">Ponadto nawet jeśli pierwsze zadanie zostało ukończone pomyślnie, kolejne zadania może się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="ac8a7-204">W tym momencie możesz używać na kilka sposobów postępowania z wyjątkami: należy poczekać do czasu uruchomionego zadania zostały ukończone w takim przypadku można użyć <xref:System.Threading.Tasks.Task.WhenAll%2A> metody, lub można zdecydować, czy wszystkie wyjątki są ważne i muszą być rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="ac8a7-205">W tym celu można użyć kontynuacje aby otrzymać powiadomienie po zakończeniu zadania asynchronicznie:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => { if (t.IsFaulted) Log(t.Exception); });  
}  
```  
  
 <span data-ttu-id="ac8a7-206">lub:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-206">or:</span></span>  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);  
}  
```  
  
 <span data-ttu-id="ac8a7-207">a nawet:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-207">or even:</span></span>  
  
```  
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
  
 <span data-ttu-id="ac8a7-208">Na koniec można anulować wszystkie pozostałe operacje:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-208">Finally, you may want to cancel all the remaining operations:</span></span>  
  
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
  
#### <a name="interleaving"></a><span data-ttu-id="ac8a7-209">Z przeplotem</span><span class="sxs-lookup"><span data-stu-id="ac8a7-209">Interleaving</span></span>  
 <span data-ttu-id="ac8a7-210">Rozważmy przykład, gdzie jest pobieranie obrazów z sieci web i przetwarzania każdego obrazu (np. Dodawanie obrazu do formantu interfejsu użytkownika).</span><span class="sxs-lookup"><span data-stu-id="ac8a7-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="ac8a7-211">Musisz wykonać przetwarzania sekwencyjnie w wątku interfejsu użytkownika, ale chcesz pobrać obrazy jednocześnie jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="ac8a7-212">Ponadto użytkownik nie chce utrzymanie Dodawanie obrazów do interfejsu użytkownika, dopóki wszystkie pobraniu — Aby dodać ich w chwili zakończenia:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-213">Można także zastosować naprzemiennego wykonywania na potrzeby scenariusza, która obejmuje w praktyce znacznym przetwarzania <xref:System.Threading.ThreadPool> pobrany obrazów, np.:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>  
  
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
  
#### <a name="throttling"></a><span data-ttu-id="ac8a7-214">Dławienie</span><span class="sxs-lookup"><span data-stu-id="ac8a7-214">Throttling</span></span>  
 <span data-ttu-id="ac8a7-215">Rozważmy przykład interleaving, z wyjątkiem tego, że użytkownik pobiera tak wiele obrazów, że ograniczenie; pliki do pobrania Możesz na przykład określoną liczbę pobrań wykonywane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="ac8a7-216">Aby to osiągnąć, możesz uruchomić podzbiór operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="ac8a7-217">Jak wykonać operacji, można uruchomić dodatkowe operacje ich odbywa się:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-217">As operations complete, you can start additional operations to take their place:</span></span>  
  
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
  
#### <a name="early-bailout"></a><span data-ttu-id="ac8a7-218">Wczesne podejmowano</span><span class="sxs-lookup"><span data-stu-id="ac8a7-218">Early Bailout</span></span>  
 <span data-ttu-id="ac8a7-219">Należy wziąć pod uwagę, że czekasz asynchronicznie operacji do wykonania podczas jednocześnie odpowiedzi na żądanie anulowania przez użytkownika (na przykład użytkownik kliknął przycisk Anuluj).</span><span class="sxs-lookup"><span data-stu-id="ac8a7-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="ac8a7-220">Poniższy kod ilustruje tego scenariusza:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-220">The following code illustrates this scenario:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-221">Ta implementacja włączające interfejs użytkownika natychmiast podjąć decyzję o poręczenie, ale nie Anuluj podstawowych operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="ac8a7-222">Alternatywą jest anulowania oczekujących operacji, jeśli zdecydujesz się poręczenie, ale nie przywrócić interfejs użytkownika do faktycznie pełną potencjalnie z powodu zakończenia wczesne ze względu na żądanie anulowania operacji:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-223">Innym przykładem wczesne podejmowano polega na użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> w połączeniu z metody <xref:System.Threading.Tasks.Task.Delay%2A> metody, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>  
  
### <a name="taskdelay"></a><span data-ttu-id="ac8a7-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="ac8a7-224">Task.Delay</span></span>  
 <span data-ttu-id="ac8a7-225">Można użyć <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> metody wprowadzenie wstrzymuje działanie do wykonania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="ac8a7-226">Jest to przydatne w przypadku wielu rodzajów funkcje, w tym tworzenie pętli sondowania i obsługi danych wejściowych użytkownika przez ustalonej czas opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="ac8a7-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda może być również przydatne w połączeniu z <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> dla wykonania przekroczeń limitu czasu na oczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>  
  
 <span data-ttu-id="ac8a7-228">Jeśli zadanie, które jest częścią większej operację asynchroniczną (na przykład usługi sieci web programu ASP.NET) trwa zbyt długo, ogólną operacji może pogorszyć, zwłaszcza, jeśli nie powiedzie się nigdy zakończyć.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="ac8a7-229">Dlatego jest ważne można było upłynął limit czasu podczas oczekiwania na operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="ac8a7-230">Synchroniczne <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody zaakceptować wartości limitu czasu, ale odpowiadający mu <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> i to wymienione wcześniej <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>nie metody.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="ac8a7-231">Zamiast tego można użyć <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> w połączeniu do zaimplementowania limit czasu.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>  
  
 <span data-ttu-id="ac8a7-232">Na przykład w aplikacji interfejsu użytkownika, załóżmy, że chcesz pobranie obrazu i wyłączyć interfejsu użytkownika podczas pobierania obrazu.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="ac8a7-233">Jednak jeśli pobieranie trwa zbyt długo, chcesz ponownie włączyć interfejsu użytkownika i odrzucić pobierania:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-234">To samo dotyczy pobranie wielu materiałów, ponieważ <xref:System.Threading.Tasks.Task.WhenAll%2A> zwraca zadania:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>  
  
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
  
## <a name="building-task-based-combinators"></a><span data-ttu-id="ac8a7-235">Tworzenie Combinators opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="ac8a7-235">Building Task-based Combinators</span></span>  
 <span data-ttu-id="ac8a7-236">Ponieważ zadanie jest w stanie całkowicie reprezentują operację asynchroniczną i podaj synchroniczne i asynchroniczne możliwości łączenia z operacją, podczas pobierania wyników i tak dalej, można tworzyć przydatne bibliotek combinators tworzące zadań Tworzenie większej wzorce.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="ac8a7-237">Zgodnie z opisem w poprzedniej sekcji, .NET Framework zawiera kilka wbudowanych combinators, ale można również tworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="ac8a7-238">Kilka przykładów potencjalnych metod kombinatorem i typów można znaleźć w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-238">The following sections provide several examples of potential combinator methods and types.</span></span>  
  
### <a name="retryonfault"></a><span data-ttu-id="ac8a7-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="ac8a7-239">RetryOnFault</span></span>  
 <span data-ttu-id="ac8a7-240">W wielu sytuacjach możesz ponowić próbę wykonania operacji, jeśli poprzednia próba nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="ac8a7-241">Synchroniczne kodu może zbudować metody pomocnika takich jak `RetryOnFault` w poniższym przykładzie w tym celu:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-242">Można utworzyć metody pomocnika niemal identyczny dla asynchronicznych operacji, które są wykonywane przy wybierz, w związku z tym zwracać zadań:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-243">Następnie można ten kombinatorem kodowanie ponownych prób do aplikacji logiki; na przykład:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 <span data-ttu-id="ac8a7-244">Można rozszerzyć `RetryOnFault` więcej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="ac8a7-245">Na przykład funkcja może akceptować innego `Func<Task>` który zostanie wywołany, między kolejnymi próbami do określenia, kiedy i spróbuj wykonać operację ponownie, np.:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-246">Można następnie użyć funkcji w następujący sposób oczekiwania na chwilę przed ponowieniem operacji:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a><span data-ttu-id="ac8a7-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="ac8a7-247">NeedOnlyOne</span></span>  
 <span data-ttu-id="ac8a7-248">Czasami użytkownik może korzystać z nadmiarowość, aby poprawić opóźnienia i prawdopodobieństwo powodzenia operacji.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="ac8a7-249">Należy wziąć pod uwagę wiele usług sieci web, które zapewniają giełdowych, ale w różnych porach dnia, każda usługa może zapewnia różne poziomy jakości i czasy odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="ac8a7-250">Radzenia sobie z tymi zmianami, mogą wysyłać żądania do wszystkich usług sieci web i jak uzyskać odpowiedzi od jednego, Anuluj pozostałych żądań.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="ac8a7-251">Można zaimplementować funkcji pomocnika, aby ułatwić implementacji tego wspólnego wzorca uruchamianie wielu operacji, oczekiwania i następnie anulowanie pozostałych.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="ac8a7-252">`NeedOnlyOne` Funkcji w poniższym przykładzie przedstawiono w tym scenariuszu:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-253">Następnie można użyć tej funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-253">You can then use this function as follows:</span></span>  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async("msft", ct),  
    ct => GetCurrentPriceFromServer2Async("msft", ct),  
    ct => GetCurrentPriceFromServer3Async("msft", ct));  
```  
  
### <a name="interleaved-operations"></a><span data-ttu-id="ac8a7-254">Operacje przeplotem</span><span class="sxs-lookup"><span data-stu-id="ac8a7-254">Interleaved Operations</span></span>  
 <span data-ttu-id="ac8a7-255">Brak potencjalny problem z wydajnością przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A> metody na potrzeby scenariusza interleaving podczas pracy z bardzo dużych zestawów zadań.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span>  <span data-ttu-id="ac8a7-256">Co wywołanie <xref:System.Threading.Tasks.Task.WhenAny%2A> powoduje kontynuację jest zarejestrowany do każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="ac8a7-257">N liczbę zadań powoduje to kontynuacje O(N2) utworzona w okresie istnienia interleaving operacji.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-257">For N number of tasks, this results in O(N2) continuations created over the lifetime of the interleaving operation.</span></span>  <span data-ttu-id="ac8a7-258">Jeśli pracujesz z dużych zestawów zadań, można użyć kombinatorze (`Interleaved` w poniższym przykładzie) Aby rozwiązać problem z wydajnością:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-258">If you're working with a large set of tasks, you can use a combinator  (`Interleaved` in the following example) to address the performance issue:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-259">Następnie można kombinatorem przetworzyć wyniki zadań w chwili zakończenia; na przykład:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a><span data-ttu-id="ac8a7-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="ac8a7-260">WhenAllOrFirstException</span></span>  
 <span data-ttu-id="ac8a7-261">W pewnych sytuacjach punktowy/zbieranie możesz chcieć poczekaj, aż wszystkie zadania w zestawie, chyba że jeden z nich błędów, w którym to przypadku należy zatrzymać oczekuje się, gdy występuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="ac8a7-262">Można uzyskać, który za pomocą metody kombinatorem takich jak `WhenAllOrFirstException` w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>  
  
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
  
## <a name="building-task-based-data-structures"></a><span data-ttu-id="ac8a7-263">Struktury danych oparty na zadaniach kompilowanie</span><span class="sxs-lookup"><span data-stu-id="ac8a7-263">Building Task-based Data Structures</span></span>  
 <span data-ttu-id="ac8a7-264">Oprócz umożliwia tworzenie niestandardowych combinators opartego na zadaniach, mających struktury danych w <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> reprezentujący wyniki operacji asynchronicznej i synchronizacji niezbędne do przyłączenia z nim sprawia, że bardzo zaawansowane Wpisz, na której można utworzyć struktur danych niestandardowych można używać w scenariuszach asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>  
  
### <a name="asynccache"></a><span data-ttu-id="ac8a7-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="ac8a7-265">AsyncCache</span></span>  
 <span data-ttu-id="ac8a7-266">Pobierz jedną istotnym elementem zadania jest, że jej może można przekazać do wielu klientów, z których mogą poczekać na jego kontynuacje rejestru, jego wynik lub wyjątki (w przypadku liczby <xref:System.Threading.Tasks.Task%601>) i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="ac8a7-267">Dzięki temu <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> idealnie nadaje się do użycia w asynchronicznej infrastruktury buforowania.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="ac8a7-268">Oto przykład małą, ale utworzona zaawansowanych asynchroniczne pamięć podręczna nad <xref:System.Threading.Tasks.Task%601>:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-269">[AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) klasy akceptuje jak obiekt delegowany dla jego konstruktora funkcję, która przyjmuje `TKey` i zwraca <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-269">The [AsyncCache\<TKey,TValue>](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="ac8a7-270">Wszelkie wartości wcześniej używanych z pamięci podręcznej są przechowywane w słowniku wewnętrzny i `AsyncCache` gwarantuje, że tylko jedno zadanie jest generowany na klucz, nawet wtedy, gdy pamięć podręczna jest jednocześnie dostępny.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>  
  
 <span data-ttu-id="ac8a7-271">Można na przykład tworzenie pamięci podręcznej dla pobranego stron sieci web:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-271">For example, you can build a cache for downloaded web pages:</span></span>  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 <span data-ttu-id="ac8a7-272">Następnie można użyć tej pamięci podręcznej w metod asynchronicznych przy każdym zawartości strony sieci web.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="ac8a7-273">`AsyncCache` Klasy gwarantuje, że jako możliwe i pamięci podręczne wyniki są pobierane jako kilka stron.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="ac8a7-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="ac8a7-274">AsyncProducerConsumerCollection</span></span>  
 <span data-ttu-id="ac8a7-275">Zadania umożliwia również tworzenie struktur danych koordynacji działań asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="ac8a7-276">Weź pod uwagę jedną te wzorce projektowe równoległych klasycznego: producent/konsumenta.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="ac8a7-277">W tym wzorcu producentów generować dane jest używane przez konsumentów, a producenci i konsumenci może działać równolegle.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="ac8a7-278">Na przykład konsumenta przetwarza element 1, który wcześniej został wygenerowany przez producenta, który jest teraz tworzenie pozycji 2.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="ac8a7-279">Dla wzorca producent i konsument niezmiennie muszą niektóre struktury danych do przechowywania robocze tworzone przez producentów, dzięki czemu konsumentów może otrzymywać powiadomienia o nowych danych i znajdź go, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>  
  
 <span data-ttu-id="ac8a7-280">W tym miejscu jest strukturą proste danych wbudowane zadania, która umożliwia metod asynchronicznych, które mają być używane jako producenci i konsumenci:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-281">Z tej struktury danych w miejscu można napisać kod, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-281">With that data structure in place, you can write code such as the following:</span></span>  
  
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
  
 <span data-ttu-id="ac8a7-282"><xref:System.Threading.Tasks.Dataflow> Przestrzeń nazw zawiera <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> typ, którego można użyć w podobny sposób, ale bez konieczności typ kolekcji niestandardowej kompilacji:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>  
  
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
>  <span data-ttu-id="ac8a7-283"><xref:System.Threading.Tasks.Dataflow> Przestrzeń nazw jest dostępna w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] za pośrednictwem **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] through **NuGet**.</span></span> <span data-ttu-id="ac8a7-284">Aby zainstalować zestaw zawierający <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online pakiet Microsoft.Tpl.Dataflow.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8a7-285">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac8a7-285">See Also</span></span>  
 [<span data-ttu-id="ac8a7-286">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="ac8a7-286">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [<span data-ttu-id="ac8a7-287">Implementowanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="ac8a7-287">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [<span data-ttu-id="ac8a7-288">Współdziałanie z innymi wzorcami asynchronicznymi i typami</span><span class="sxs-lookup"><span data-stu-id="ac8a7-288">Interop with Other Asynchronous Patterns and Types</span></span>](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
