---
title: try-catch - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: 3d4315a09869b77b4ae8cbb43646f9a96280b678
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173474"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="e0711-102">try-catch (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e0711-102">try-catch (C# Reference)</span></span>

<span data-ttu-id="e0711-103">Try-catch instrukcja składa `try` się z bloku, a następnie jeden lub więcej `catch` klauzul, które określają programy obsługi dla różnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e0711-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

<span data-ttu-id="e0711-104">Gdy wyjątek, czas wykonywania języka wspólnego (CLR) `catch` szuka instrukcji, która obsługuje ten wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e0711-104">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="e0711-105">Jeśli aktualnie wykonywana metoda nie `catch` zawiera takiego bloku, CLR patrzy na metodę, która nazywa bieżącą metodę i tak dalej stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="e0711-105">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="e0711-106">Jeśli `catch` nie zostanie znaleziony żaden blok, clr wyświetla nieobsługiwany komunikat o wyjątku dla użytkownika i zatrzymuje wykonywanie programu.</span><span class="sxs-lookup"><span data-stu-id="e0711-106">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="e0711-107">Blok `try` zawiera kod strzeżony, który może spowodować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e0711-107">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="e0711-108">Blok jest wykonywany, dopóki nie zostanie zgłoszony wyjątek lub zostanie pomyślnie ukończony.</span><span class="sxs-lookup"><span data-stu-id="e0711-108">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="e0711-109">Na przykład następująca próba `null` rzutować <xref:System.NullReferenceException> obiekt wywołuje wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e0711-109">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="e0711-110">Mimo `catch` że klauzula może służyć bez argumentów do przechwycania dowolnego typu wyjątku, to użycie nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="e0711-110">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="e0711-111">Ogólnie rzecz biorąc należy przechwycić tylko te wyjątki, które wiesz, jak odzyskać z.</span><span class="sxs-lookup"><span data-stu-id="e0711-111">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="e0711-112">W związku z tym należy zawsze <xref:System.Exception?displayProperty=nameWithType> określić argument obiektu pochodzące z na przykład:</span><span class="sxs-lookup"><span data-stu-id="e0711-112">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="e0711-113">Istnieje możliwość użycia więcej niż `catch` jednej określonej klauzuli w tej samej instrukcji try-catch.</span><span class="sxs-lookup"><span data-stu-id="e0711-113">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="e0711-114">W takim przypadku kolejność `catch` klauzul jest ważna, ponieważ `catch` klauzule są badane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="e0711-114">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="e0711-115">Złap bardziej szczegółowe wyjątki przed mniej szczegółowymi.</span><span class="sxs-lookup"><span data-stu-id="e0711-115">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="e0711-116">Kompilator generuje błąd, jeśli zamówisz catch bloki tak, że nowszy blok nigdy nie można osiągnąć.</span><span class="sxs-lookup"><span data-stu-id="e0711-116">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="e0711-117">Za `catch` pomocą argumentów jest jednym ze sposobów filtrowania wyjątków, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="e0711-117">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="e0711-118">Można również użyć filtru wyjątków, który dodatkowo sprawdza wyjątek, aby zdecydować, czy go obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="e0711-118">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="e0711-119">Jeśli filtr wyjątków zwraca false, a następnie wyszukiwanie obsługi nadal.</span><span class="sxs-lookup"><span data-stu-id="e0711-119">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="e0711-120">Filtry wyjątków są lepsze niż przechwytywanie i wyrzucanie (wyjaśnione poniżej), ponieważ filtry pozostawiają stos bez szwanku.</span><span class="sxs-lookup"><span data-stu-id="e0711-120">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="e0711-121">Jeśli później obsługi zrzutu stosu, można zobaczyć, gdzie wyjątek pierwotnie pochodzi, a nie tylko ostatnie miejsce został ponownie wyrzucony.</span><span class="sxs-lookup"><span data-stu-id="e0711-121">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="e0711-122">Typowe użycie wyrażeń filtru wyjątków jest rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="e0711-122">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="e0711-123">Można utworzyć filtr, który zawsze zwraca false, który również dane wyjściowe do dziennika, można rejestrować wyjątki, jak przejść bez konieczności ich obsługi i rethrow.</span><span class="sxs-lookup"><span data-stu-id="e0711-123">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="e0711-124">Throw [throw](throw.md) Instrukcji może służyć `catch` w bloku, aby ponownie zgłosić wyjątek, który jest przechwycone przez instrukcję. `catch`</span><span class="sxs-lookup"><span data-stu-id="e0711-124">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="e0711-125">Poniższy przykład wyodrębnia informacje <xref:System.IO.IOException> o źródle z wyjątku, a następnie zgłasza wyjątek do metody nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e0711-125">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

<span data-ttu-id="e0711-126">Można przechwycić jeden wyjątek i zgłosić inny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e0711-126">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="e0711-127">Po złożeniu tej czynności określ wyjątek, który został przechwycony jako wyjątek wewnętrzny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e0711-127">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="e0711-128">Można również ponownie zgłosić wyjątek, gdy określony warunek jest true, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e0711-128">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> <span data-ttu-id="e0711-129">Możliwe jest również użycie filtru wyjątków, aby uzyskać podobny wynik w często czystszy sposób (a także nie modyfikować stosu, jak wyjaśniono wcześniej w tym dokumencie).</span><span class="sxs-lookup"><span data-stu-id="e0711-129">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="e0711-130">Poniższy przykład ma podobne zachowanie dla wywoływania jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e0711-130">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="e0711-131">Funkcja wyrzuca `InvalidCastException` z powrotem do `e.Data` obiektu `null`wywołującego, gdy jest .</span><span class="sxs-lookup"><span data-stu-id="e0711-131">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

<span data-ttu-id="e0711-132">Z wewnątrz `try` bloku, inicjowanie tylko zmienne, które są zadeklarowane w nim.</span><span class="sxs-lookup"><span data-stu-id="e0711-132">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="e0711-133">W przeciwnym razie może wystąpić wyjątek przed wykonaniem bloku jest zakończona.</span><span class="sxs-lookup"><span data-stu-id="e0711-133">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="e0711-134">Na przykład w poniższym przykładzie `n` kodu zmienna `try` jest inicjowana wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="e0711-134">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="e0711-135">Próba użycia tej zmiennej `try` poza `Write(n)` blokiem w instrukcji wygeneruje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e0711-135">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

<span data-ttu-id="e0711-136">Aby uzyskać więcej informacji na temat catch, zobacz [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="e0711-136">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="e0711-137">Wyjątki w metodach asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="e0711-137">Exceptions in async methods</span></span>

<span data-ttu-id="e0711-138">Metoda asynchroniczna jest oznaczona modyfikatorem [asynchronii](async.md) i zwykle zawiera jedno lub więcej wyrażeń lub instrukcji await.</span><span class="sxs-lookup"><span data-stu-id="e0711-138">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="e0711-139">Wyrażenie await stosuje operator [await](../operators/await.md) <xref:System.Threading.Tasks.Task> do <xref:System.Threading.Tasks.Task%601>a lub .</span><span class="sxs-lookup"><span data-stu-id="e0711-139">An await expression applies the [await](../operators/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="e0711-140">Gdy formant osiągnie `await` w metodzie asynchronicznej, postęp w metodzie jest zawieszony, dopóki nie zostanie ukończone oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="e0711-140">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="e0711-141">Po zakończeniu zadania wykonanie można wznowić w metodzie.</span><span class="sxs-lookup"><span data-stu-id="e0711-141">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="e0711-142">Aby uzyskać więcej informacji, zobacz [Programowanie asynchroniczne z async i await](../../programming-guide/concepts/async/index.md) i [Control Flow w programach asynchronicznych](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="e0711-142">For more information, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="e0711-143">Ukończone zadanie, `await` do którego jest stosowany może być w stanie błędnym z powodu nieobsługiwanego wyjątku w metodzie, która zwraca zadanie.</span><span class="sxs-lookup"><span data-stu-id="e0711-143">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="e0711-144">Oczekiwanie na zadanie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e0711-144">Awaiting the task throws an exception.</span></span> <span data-ttu-id="e0711-145">Zadanie może również zakończyć się w stanie anulowanym, jeśli proces asynchroniczny, który go zwraca, zostanie anulowany.</span><span class="sxs-lookup"><span data-stu-id="e0711-145">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="e0711-146">Oczekiwanie na anulowane zadanie wysuwa plik `OperationCanceledException`.</span><span class="sxs-lookup"><span data-stu-id="e0711-146">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="e0711-147">Aby uzyskać więcej informacji na temat anulowania procesu asynchronicznego, zobacz [Dostrajanie aplikacji asynchronicznej](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="e0711-147">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="e0711-148">Aby przechwycić wyjątek, poczekaj `try` na zadanie w bloku i `catch` przechwyć wyjątek w skojarzonym bloku.</span><span class="sxs-lookup"><span data-stu-id="e0711-148">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="e0711-149">Na przykład zobacz [przykładową sekcję Metoda asynchronicznej.](#async-method-example)</span><span class="sxs-lookup"><span data-stu-id="e0711-149">For an example, see the [Async method example](#async-method-example) section.</span></span>

<span data-ttu-id="e0711-150">Zadanie może być w stanie błędnym, ponieważ wystąpiło wiele wyjątków w oczekiwanej metodzie asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="e0711-150">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="e0711-151">Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0711-151">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e0711-152">Gdy oczekujesz na takie zadanie, tylko jeden z wyjątków jest przechwycone i nie można przewidzieć, który wyjątek zostanie przechwycona.</span><span class="sxs-lookup"><span data-stu-id="e0711-152">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="e0711-153">Na przykład zobacz [Task.WhenAll przykładsekcji.](#taskwhenall-example)</span><span class="sxs-lookup"><span data-stu-id="e0711-153">For an example, see the [Task.WhenAll example](#taskwhenall-example) section.</span></span>

## <a name="example"></a><span data-ttu-id="e0711-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0711-154">Example</span></span>

<span data-ttu-id="e0711-155">W poniższym `try` przykładzie blok zawiera wywołanie `ProcessString` metody, która może spowodować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e0711-155">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="e0711-156">Klauzula `catch` zawiera program obsługi wyjątków, który po prostu wyświetla komunikat na ekranie.</span><span class="sxs-lookup"><span data-stu-id="e0711-156">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="e0711-157">Gdy `throw` instrukcja jest `MyMethod`wywoływana od wewnątrz, system szuka `catch` `Exception caught`instrukcji i wyświetla komunikat .</span><span class="sxs-lookup"><span data-stu-id="e0711-157">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a><span data-ttu-id="e0711-158">Przykład dwóch bloków catch</span><span class="sxs-lookup"><span data-stu-id="e0711-158">Two catch blocks example</span></span>

<span data-ttu-id="e0711-159">W poniższym przykładzie używane są dwa bloki catch, a najbardziej szczegółowy wyjątek, który jest pierwszy, jest przechwycony.</span><span class="sxs-lookup"><span data-stu-id="e0711-159">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="e0711-160">Aby przechwycić najmniej szczegółowy wyjątek, można `ProcessString` zastąpić throw instrukcji `throw new Exception()`w następującej instrukcji: .</span><span class="sxs-lookup"><span data-stu-id="e0711-160">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="e0711-161">Jeśli w przykładzie najpierw umieścisz najmniej specyficzny blok catch, zostanie wyświetlony następujący komunikat o błędzie: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="e0711-161">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a><span data-ttu-id="e0711-162">Przykład metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="e0711-162">Async method example</span></span>

<span data-ttu-id="e0711-163">W poniższym przykładzie przedstawiono obsługę wyjątków dla metod asynchronii.</span><span class="sxs-lookup"><span data-stu-id="e0711-163">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="e0711-164">Aby przechwycić wyjątek, który zgłasza zadanie `await` asynchroniczne, umieść wyrażenie `try` w `catch` bloku i przechwyć wyjątek w bloku.</span><span class="sxs-lookup"><span data-stu-id="e0711-164">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="e0711-165">Odkomentuj `throw new Exception` wiersz w przykładzie, aby zademonstrować obsługę wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e0711-165">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="e0711-166">Właściwość zadania jest ustawiona `True`na , `Exception.InnerException` właściwość zadania jest ustawiona na wyjątek, a `catch` wyjątek jest przechwycone w bloku. `IsFaulted`</span><span class="sxs-lookup"><span data-stu-id="e0711-166">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="e0711-167">Odkomentuj `throw new OperationCanceledException` wiersz, aby zademonstrować, co się dzieje po anulowaniu procesu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="e0711-167">Uncomment the `throw new OperationCanceledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="e0711-168">`IsCanceled` Właściwość zadania jest ustawiona `true`na , a wyjątek `catch` jest przechwycone w bloku.</span><span class="sxs-lookup"><span data-stu-id="e0711-168">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="e0711-169">W niektórych warunkach, które nie mają zastosowania do `IsFaulted` tego przykładu, właściwość zadania jest ustawiona `true` na i `IsCanceled` jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="e0711-169">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a><span data-ttu-id="e0711-170">Task.WhenAll przykład</span><span class="sxs-lookup"><span data-stu-id="e0711-170">Task.WhenAll example</span></span>

<span data-ttu-id="e0711-171">W poniższym przykładzie przedstawiono obsługę wyjątków, gdzie wiele zadań może spowodować wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e0711-171">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="e0711-172">Blok `try` czeka na zadanie, które jest zwracane <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>przez wywołanie .</span><span class="sxs-lookup"><span data-stu-id="e0711-172">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e0711-173">Zadanie zostanie ukończone po zakończeniu trzech zadań, do których jest stosowana WhenAll.</span><span class="sxs-lookup"><span data-stu-id="e0711-173">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="e0711-174">Każde z trzech zadań powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e0711-174">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="e0711-175">Blok `catch` iteruje za pomocą wyjątków, `Exception.InnerExceptions` które znajdują się we właściwości <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>zadania, który został zwrócony przez .</span><span class="sxs-lookup"><span data-stu-id="e0711-175">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="e0711-176">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e0711-176">C# language specification</span></span>

<span data-ttu-id="e0711-177">Aby uzyskać więcej informacji, zobacz sekcję [instrukcja wypróbuj](~/_csharplang/spec/statements.md#the-try-statement) [specyfikację języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="e0711-177">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0711-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0711-178">See also</span></span>

- [<span data-ttu-id="e0711-179">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="e0711-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0711-180">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="e0711-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0711-181">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e0711-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e0711-182">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="e0711-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="e0711-183">throw</span><span class="sxs-lookup"><span data-stu-id="e0711-183">throw</span></span>](throw.md)
- [<span data-ttu-id="e0711-184">try-finally</span><span class="sxs-lookup"><span data-stu-id="e0711-184">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="e0711-185">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="e0711-185">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
