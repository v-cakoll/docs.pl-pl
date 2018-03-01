---
title: "Await — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d639d1398c0f783fcfa40ee9ff278922fd6fc7b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="10ddb-102">Await — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10ddb-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="10ddb-103">Należy zastosować `Await` operatora operandu w asynchronicznej metody lub wyrażenia lambda wstrzymania wykonywanie metody do momentu ukończenia zadania oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="10ddb-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="10ddb-104">Zadanie reprezentuje pracy w toku.</span><span class="sxs-lookup"><span data-stu-id="10ddb-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="10ddb-105">Metoda, w którym `Await` służy musi mieć [Async](../../../visual-basic/language-reference/modifiers/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="10ddb-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="10ddb-106">Taka metoda, zdefiniowany przy użyciu `Async` modyfikator i zazwyczaj zawierającego co najmniej jeden `Await` wyrażenia, jest określany jako *metody asynchronicznej*.</span><span class="sxs-lookup"><span data-stu-id="10ddb-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10ddb-107">`Async` i `Await` słowa kluczowe wprowadzono w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="10ddb-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="10ddb-108">Aby obejrzeć wprowadzenie do programowania asynchronicznego Zobacz [programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="10ddb-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="10ddb-109">Zwykle zadania, do którego należy zastosować `Await` operator jest wartością zwracaną przez wywołanie do metody, która implementuje [wzorca asynchronicznego opartego na zadaniach](http://go.microsoft.com/fwlink/?LinkId=204847), która jest <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="10ddb-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="10ddb-110">W poniższym kodzie <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> zwraca `getContentsTask`, `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="10ddb-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="10ddb-111">Zadanie jest obietnicę w celu utworzenia tablicy bajtowej rzeczywiste po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="10ddb-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="10ddb-112">`Await` Operator jest stosowany do `getContentsTask` wstrzymania wykonywania w `SumPageSizesAsync` do momentu `getContentsTask` została ukończona.</span><span class="sxs-lookup"><span data-stu-id="10ddb-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="10ddb-113">Tymczasem zwróceniem sterowania do wywołującego `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="10ddb-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="10ddb-114">Gdy `getContentsTask` zostało zakończone, `Await` wyrażenie na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="10ddb-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
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
>  <span data-ttu-id="10ddb-115">Aby uzyskać pełny przykład, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="10ddb-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="10ddb-116">Możesz pobrać próbki z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) w witrynie firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10ddb-116">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="10ddb-117">Przykładem jest w projekcie AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="10ddb-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="10ddb-118">Jeśli `Await` jest stosowany do wyniku wywołania metody, która zwraca `Task(Of TResult)`, typ `Await` wyrażenie jest TResult.</span><span class="sxs-lookup"><span data-stu-id="10ddb-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="10ddb-119">Jeśli `Await` jest stosowany do wyniku wywołania metody, która zwraca `Task`, `Await` wyrażenie nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="10ddb-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="10ddb-120">Poniższy przykład przedstawia różnicy.</span><span class="sxs-lookup"><span data-stu-id="10ddb-120">The following example illustrates the difference.</span></span>  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 <span data-ttu-id="10ddb-121">`Await` Wyrażenia lub instrukcji nie są blokowane w wątku, na którym jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="10ddb-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="10ddb-122">Zamiast tego należy go powoduje, że kompilator rejestracja pozostałe metody asynchronicznej po `Await` jako kontynuacji zadania Oczekiwano wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="10ddb-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="10ddb-123">Formant zwraca do obiektu wywołującego metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="10ddb-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="10ddb-124">Po ukończeniu zadania wywołuje kontynuacji i wykonywania wznawia metody asynchronicznej miejsca, w którym.</span><span class="sxs-lookup"><span data-stu-id="10ddb-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="10ddb-125">`Await` Wyrażenie może wystąpić tylko w treści natychmiastowo otaczającą metody lub wyrażenia lambda oznaczonym za `Async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="10ddb-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="10ddb-126">Termin *Await* służy jako słowo kluczowe tylko w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="10ddb-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="10ddb-127">W innym miejscu jest interpretowany jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="10ddb-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="10ddb-128">W ramach asynchronicznej metody lub wyrażenia lambda `Await` wyrażenia nie może wystąpić w wyrażeniu zapytania w `catch` lub `finally` zablokować z [spróbuj... CATCH... Na koniec](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) instrukcji w pętli sterowania zmiennej wyrażeniu `For` lub `For Each` pętli lub w treści [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="10ddb-128">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="10ddb-129">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="10ddb-129">Exceptions</span></span>  
 <span data-ttu-id="10ddb-130">Zwraca większości metod asynchronicznych <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="10ddb-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="10ddb-131">Właściwości zadania zwróconego zawierać informacje o jego stan i Historia, na przykład tego, czy zadanie zostało ukończone, czy metoda asynchroniczna spowodowała wyjątek lub została anulowana i jakie wynik końcowy jest.</span><span class="sxs-lookup"><span data-stu-id="10ddb-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="10ddb-132">`Await` Operator uzyskuje dostęp do tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="10ddb-132">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="10ddb-133">Jeśli await umożliwiające zwracanie zadań metoda asynchroniczna, która powoduje zgłoszenie wyjątku `Await` operator ponownie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="10ddb-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="10ddb-134">Jeśli await umożliwiające zwracanie zadań metoda asynchroniczna, która została anulowana, `Await` operator ponownie zgłasza wyjątek <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="10ddb-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="10ddb-135">Pojedyncze zadanie, który jest stan można odzwierciedlać wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="10ddb-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="10ddb-136">Na przykład zadanie może być wynikiem wywołania do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10ddb-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="10ddb-137">Gdy await takie zadania, ponownie zgłasza operacji await tylko jeden z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="10ddb-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="10ddb-138">Jednak nie można przewidzieć który wyjątki jest zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="10ddb-138">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="10ddb-139">Przykłady obsługi błędów w metodach asynchronicznych, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="10ddb-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10ddb-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="10ddb-140">Example</span></span>  
 <span data-ttu-id="10ddb-141">W poniższym przykładzie formularzy systemu Windows ilustruje użycie `Await` w metodzie asynchronicznej `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="10ddb-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="10ddb-142">Natomiast zachowanie tej metody z zachowaniem `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="10ddb-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="10ddb-143">Bez `Await` operatora, `WaitSynchronously` synchronicznie działa niezależnie od stosowania `Async` modyfikator w swojej definicji i wywołanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w jego treści.</span><span class="sxs-lookup"><span data-stu-id="10ddb-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10ddb-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10ddb-144">See Also</span></span>  
 [<span data-ttu-id="10ddb-145">Programowanie asynchroniczne z Async i Await</span><span class="sxs-lookup"><span data-stu-id="10ddb-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="10ddb-146">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await</span><span class="sxs-lookup"><span data-stu-id="10ddb-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="10ddb-147">Asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="10ddb-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
