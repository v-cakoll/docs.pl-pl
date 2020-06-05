---
title: Await — Operator
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 9d55ba82547dfcb0336c3a3fd12521c0dcb3eb58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371833"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="5ecc4-102">Await — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ecc4-102">Await Operator (Visual Basic)</span></span>

<span data-ttu-id="5ecc4-103">Operator jest stosowany `Await` do operandu w metodzie asynchronicznej lub wyrażeniu lambda, aby wstrzymać wykonywanie metody do momentu ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="5ecc4-104">Zadanie reprezentuje trwającą prace.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-104">The task represents ongoing work.</span></span>

<span data-ttu-id="5ecc4-105">`Await`Używana metoda musi mieć Modyfikator [Async](../modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-105">The method in which `Await` is used must have an [Async](../modifiers/async.md) modifier.</span></span> <span data-ttu-id="5ecc4-106">Takie metody, zdefiniowane za pomocą `Async` modyfikatora i zwykle zawierające co najmniej jeden `Await` wyrażenie, są określane jako *Metoda async*.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>

> [!NOTE]
> <span data-ttu-id="5ecc4-107">`Async` `Await` Słowa kluczowe i zostały wprowadzone w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="5ecc4-108">Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="5ecc4-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="5ecc4-109">Zwykle zadanie, do którego zastosowano operator, `Await` jest wartością zwracaną z wywołania metody implementującej [wzorzec asynchroniczny oparty na zadaniach](https://www.microsoft.com/download/details.aspx?id=19957), czyli a <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://www.microsoft.com/download/details.aspx?id=19957), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="5ecc4-110">W poniższym kodzie <xref:System.Net.Http.HttpClient> Metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> zwraca `getContentsTask` , a `Task(Of Byte())` .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="5ecc4-111">Zadanie to obietnica do tworzenia rzeczywistej tablicy bajtowej po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="5ecc4-112">`Await`Operator zostanie zastosowany do `getContentsTask` wstrzymania wykonywania w programie do `SumPageSizesAsync` momentu `getContentsTask` ukończenia.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="5ecc4-113">W międzyczasie formant jest zwracany do obiektu wywołującego `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="5ecc4-114">Po `getContentsTask` zakończeniu `Await` wyrażenie daje w wyniku tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>

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
> <span data-ttu-id="5ecc4-115">Pełny przykład można znaleźć w temacie [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5ecc4-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="5ecc4-116">Możesz pobrać przykład z [przykładów kodu dla deweloperów](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) w witrynie sieci Web firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="5ecc4-117">Przykład znajduje się w projekcie AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>

<span data-ttu-id="5ecc4-118">Jeśli `Await` jest stosowany do wyniku wywołania metody, które zwraca `Task(Of TResult)` , typ `Await` wyrażenia jest TResult.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="5ecc4-119">Jeśli `Await` jest stosowany do wyniku wywołania metody, które zwraca `Task` , `Await` wyrażenie nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="5ecc4-120">Poniższy przykład ilustruje różnicę.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-120">The following example illustrates the difference.</span></span>

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

<span data-ttu-id="5ecc4-121">`Await`Wyrażenie lub instrukcja nie blokuje wątku, w którym jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="5ecc4-122">Zamiast tego powoduje, że kompilator rejestruje resztę metody asynchronicznej, po `Await` wyrażeniu, jako kontynuację w oczekiwanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="5ecc4-123">Następnie formant wraca do obiektu wywołującego metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="5ecc4-124">Po zakończeniu zadania wywołuje jego kontynuację i wykonywanie metody asynchronicznej zostaje wznowione w miejscu, w którym została przerwana.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>

<span data-ttu-id="5ecc4-125">`Await`Wyrażenie może wystąpić tylko w treści bezpośrednio otaczającej metody lub wyrażenia lambda, które jest oznaczone `Async` modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="5ecc4-126">Termin *await* służy jako słowo kluczowe tylko w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="5ecc4-127">W innym miejscu jest interpretowana jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="5ecc4-128">W `Async` metodzie lub wyrażeniu lambda `Await` wyrażenie nie może wystąpić w wyrażeniu zapytania `Catch` lub `Finally` bloku [try... Catch... Finally](../statements/try-catch-finally-statement.md), w wyrażeniu zmiennej kontrolki pętli `For` lub `For Each` w treści instrukcji [SyncLock](../statements/synclock-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-128">Within the `Async` method or lambda expression, an `Await` expression cannot occur in a query expression, in the `Catch` or `Finally` block of a [Try…Catch…Finally statement](../statements/try-catch-finally-statement.md), in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../statements/synclock-statement.md) statement.</span></span>

## <a name="exceptions"></a><span data-ttu-id="5ecc4-129">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="5ecc4-129">Exceptions</span></span>

<span data-ttu-id="5ecc4-130">Większość metod asynchronicznych zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="5ecc4-131">Właściwości zwróconego zadania zawierają informacje o jego stanie i historii, na przykład o tym, czy zadanie zostało ukończone, czy Metoda asynchroniczna spowodowała wyjątek, czy została anulowana, oraz jaki jest wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="5ecc4-132">`Await`Operator uzyskuje dostęp do tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-132">The `Await` operator accesses those properties.</span></span>

<span data-ttu-id="5ecc4-133">Jeśli czekasz na metodę asynchroniczną zwracającą zadanie, która powoduje wyjątek, operator ponownie zgłosi `Await` wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>

<span data-ttu-id="5ecc4-134">Jeśli oczekujesz, że Metoda asynchroniczna zwracająca zadanie została anulowana, operator ponownie zgłosi `Await` <xref:System.OperationCanceledException> .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="5ecc4-135">Pojedyncze zadanie, które jest w stanie awarii może odzwierciedlać wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="5ecc4-136">Na przykład zadanie może być wynikiem wywołania metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5ecc4-137">Po oczekiwaniu na takie zadanie Operacja await ponownie zgłosi tylko jeden z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="5ecc4-138">Nie można jednak przewidzieć, które wyjątki są ponownie zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-138">However, you can't predict which of the exceptions is rethrown.</span></span>

<span data-ttu-id="5ecc4-139">Przykłady obsługi błędów w metodach asynchronicznych znajdują się w temacie [try... Catch... Finally — instrukcja](../statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5ecc4-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../statements/try-catch-finally-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="5ecc4-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ecc4-140">Example</span></span>

<span data-ttu-id="5ecc4-141">Poniższy przykład Windows Forms ilustruje użycie `Await` metody w metodzie asynchronicznej `WaitAsynchronouslyAsync` .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="5ecc4-142">Różnice w zachowaniu tej metody z zachowaniem `WaitSynchronously` .</span><span class="sxs-lookup"><span data-stu-id="5ecc4-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="5ecc4-143">Bez `Await` operatora, `WaitSynchronously` wykonywane synchronicznie, pomimo użycia `Async` modyfikatora w jego definicji i wywołania do <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w swojej treści.</span><span class="sxs-lookup"><span data-stu-id="5ecc4-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5ecc4-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ecc4-144">See also</span></span>

- [<span data-ttu-id="5ecc4-145">Programowanie asynchroniczne z Async i await</span><span class="sxs-lookup"><span data-stu-id="5ecc4-145">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="5ecc4-146">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await</span><span class="sxs-lookup"><span data-stu-id="5ecc4-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="5ecc4-147">Asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="5ecc4-147">Async</span></span>](../modifiers/async.md)
