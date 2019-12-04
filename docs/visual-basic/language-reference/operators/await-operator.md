---
title: Await — Operator
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: e0c617ce32f80bdde1bcfda31da40ae610e07452
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712350"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="f23c9-102">Await — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23c9-102">Await Operator (Visual Basic)</span></span>

<span data-ttu-id="f23c9-103">Zastosuj operator `Await` do operandu w metodzie asynchronicznej lub wyrażeniu lambda, aby wstrzymać wykonywanie metody do momentu ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="f23c9-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="f23c9-104">Zadanie reprezentuje trwającą prace.</span><span class="sxs-lookup"><span data-stu-id="f23c9-104">The task represents ongoing work.</span></span>

<span data-ttu-id="f23c9-105">Metoda, w której jest używana `Await`, musi mieć Modyfikator [Async](../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="f23c9-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="f23c9-106">Taka metoda, zdefiniowana za pomocą modyfikatora `Async`, która zwykle zawiera co najmniej jedno wyrażenie `Await`, jest określana jako *Metoda asynchroniczna*.</span><span class="sxs-lookup"><span data-stu-id="f23c9-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>

> [!NOTE]
> <span data-ttu-id="f23c9-107">Słowa kluczowe `Async` i `Await` zostały wprowadzone w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f23c9-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="f23c9-108">Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="f23c9-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="f23c9-109">Zwykle zadanie, do którego zastosowano operator `Await`, jest wartością zwracaną z wywołania metody implementującej [wzorzec asynchroniczny oparty na zadaniach](https://www.microsoft.com/download/details.aspx?id=19957), czyli <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f23c9-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://www.microsoft.com/download/details.aspx?id=19957), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="f23c9-110">W poniższym kodzie Metoda <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> zwraca `getContentsTask``Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="f23c9-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="f23c9-111">Zadanie to obietnica do tworzenia rzeczywistej tablicy bajtowej po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="f23c9-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="f23c9-112">Operator `Await` jest stosowany do `getContentsTask` w celu wstrzymania wykonywania w `SumPageSizesAsync` do momentu ukończenia `getContentsTask`.</span><span class="sxs-lookup"><span data-stu-id="f23c9-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="f23c9-113">W międzyczasie formant jest zwracany do obiektu wywołującego `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="f23c9-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="f23c9-114">Po zakończeniu `getContentsTask` wyrażenie `Await` szacuje tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="f23c9-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>

```vb
Private Async Function SumPageSizesAsync() As Task

    ' To use the HttpClient type in desktop apps, you must include a using directive and add a
    ' reference for the System.Net.Http namespace.
    Dim client As HttpClient = New HttpClient()
    ' . . .
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    Dim urlContents As Byte() = Await getContentsTask

    ' Equivalently, now that you see how it works, you can write the same thing in a single line.
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ' . . .
End Function
```

> [!IMPORTANT]
> <span data-ttu-id="f23c9-115">Pełny przykład można znaleźć w temacie [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="f23c9-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="f23c9-116">Możesz pobrać przykład z [przykładów kodu dla deweloperów](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) w witrynie sieci Web firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f23c9-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="f23c9-117">Przykład znajduje się w projekcie AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="f23c9-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>

<span data-ttu-id="f23c9-118">Jeśli `Await` jest stosowany do wyniku wywołania metody, które zwraca `Task(Of TResult)`, typem wyrażenia `Await` jest TResult.</span><span class="sxs-lookup"><span data-stu-id="f23c9-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="f23c9-119">Jeśli `Await` jest stosowany do wyniku wywołania metody, które zwraca `Task`, wyrażenie `Await` nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="f23c9-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="f23c9-120">Poniższy przykład ilustruje różnicę.</span><span class="sxs-lookup"><span data-stu-id="f23c9-120">The following example illustrates the difference.</span></span>

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

<span data-ttu-id="f23c9-121">Wyrażenie `Await` lub instrukcja nie blokuje wątku, w którym jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="f23c9-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="f23c9-122">Zamiast tego powoduje, że kompilator rejestruje resztę metody asynchronicznej, po wyrażeniu `Await`, jako kontynuację dla oczekującego zadania.</span><span class="sxs-lookup"><span data-stu-id="f23c9-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="f23c9-123">Następnie formant wraca do obiektu wywołującego metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="f23c9-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="f23c9-124">Po zakończeniu zadania wywołuje jego kontynuację i wykonywanie metody asynchronicznej zostaje wznowione w miejscu, w którym została przerwana.</span><span class="sxs-lookup"><span data-stu-id="f23c9-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>

<span data-ttu-id="f23c9-125">Wyrażenie `Await` może wystąpić tylko w treści bezpośrednio otaczającej metody lub wyrażenia lambda, które jest oznaczone za pomocą modyfikatora `Async`.</span><span class="sxs-lookup"><span data-stu-id="f23c9-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="f23c9-126">Termin *await* służy jako słowo kluczowe tylko w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="f23c9-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="f23c9-127">W innym miejscu jest interpretowana jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="f23c9-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="f23c9-128">W metodzie asynchronicznej lub wyrażeniu lambda wyrażenie `Await` nie może wystąpić w wyrażeniu zapytania w bloku `catch` lub `finally` [try... Catch... Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) , w wyrażeniu zmiennej sterującej pętli `For` lub `For Each` lub w treści instrukcji [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="f23c9-128">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>

## <a name="exceptions"></a><span data-ttu-id="f23c9-129">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="f23c9-129">Exceptions</span></span>

<span data-ttu-id="f23c9-130">Większość metod asynchronicznych zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f23c9-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f23c9-131">Właściwości zwróconego zadania zawierają informacje o jego stanie i historii, na przykład o tym, czy zadanie zostało ukończone, czy Metoda asynchroniczna spowodowała wyjątek, czy została anulowana, oraz jaki jest wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="f23c9-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="f23c9-132">Operator `Await` uzyskuje dostęp do tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="f23c9-132">The `Await` operator accesses those properties.</span></span>

<span data-ttu-id="f23c9-133">Jeśli czekasz na metodę asynchroniczną zwracającą zadanie, która powoduje wyjątek, operator `Await` ponownie zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f23c9-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>

<span data-ttu-id="f23c9-134">Jeśli oczekujesz, że Metoda asynchroniczna zwracająca zadanie została anulowana, operator `Await` ponownie zgłosi <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="f23c9-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="f23c9-135">Pojedyncze zadanie, które jest w stanie awarii może odzwierciedlać wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f23c9-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="f23c9-136">Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f23c9-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f23c9-137">Po oczekiwaniu na takie zadanie Operacja await ponownie zgłosi tylko jeden z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f23c9-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="f23c9-138">Nie można jednak przewidzieć, które wyjątki są ponownie zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="f23c9-138">However, you can't predict which of the exceptions is rethrown.</span></span>

<span data-ttu-id="f23c9-139">Przykłady obsługi błędów w metodach asynchronicznych znajdują się w temacie [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f23c9-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="f23c9-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="f23c9-140">Example</span></span>

<span data-ttu-id="f23c9-141">Poniższy przykład Windows Forms ilustruje użycie `Await` w metodzie asynchronicznej `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="f23c9-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="f23c9-142">Różnice w zachowaniu tej metody z zachowaniem `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="f23c9-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="f23c9-143">Bez operatora `Await`, `WaitSynchronously` działa synchronicznie pomimo użycia modyfikatora `Async` w definicji i wywołania do <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w swojej treści.</span><span class="sxs-lookup"><span data-stu-id="f23c9-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>

```vb
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    ' Call the method that runs asynchronously.
    Dim result As String = Await WaitAsynchronouslyAsync()

    ' Call the method that runs synchronously.
    'Dim result As String = Await WaitSynchronously()

    ' Display the result.
    TextBox1.Text &= result
End Sub

' The following method runs asynchronously. The UI thread is not
' blocked during the delay. You can move or resize the Form1 window
' while Task.Delay is running.
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)
    Await Task.Delay(10000)
    Return "Finished"
End Function

' The following method runs synchronously, despite the use of Async.
' You cannot move or resize the Form1 window while Thread.Sleep
' is running because the UI thread is blocked.
Public Async Function WaitSynchronously() As Task(Of String)
    ' Import System.Threading for the Sleep method.
    Thread.Sleep(10000)
    Return "Finished"
End Function
```

## <a name="see-also"></a><span data-ttu-id="f23c9-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f23c9-144">See also</span></span>

- [<span data-ttu-id="f23c9-145">Programowanie asynchroniczne z Async i Await</span><span class="sxs-lookup"><span data-stu-id="f23c9-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f23c9-146">Przewodnik: uzyskiwanie dostępu do sieci za pomocą Async i Await</span><span class="sxs-lookup"><span data-stu-id="f23c9-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="f23c9-147">Async</span><span class="sxs-lookup"><span data-stu-id="f23c9-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
