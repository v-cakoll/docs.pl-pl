---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: aaf5a95edb9cba9726163be3925b006a7641597c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040857"
---
# <a name="async-visual-basic"></a><span data-ttu-id="43471-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43471-102">Async (Visual Basic)</span></span>

<span data-ttu-id="43471-103">Modyfikator `Async` wskazuje, że metoda lub [wyrażenie lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) , które modyfikuje jest asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="43471-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="43471-104">Takie metody są nazywane *metodami asynchronicznymi*.</span><span class="sxs-lookup"><span data-stu-id="43471-104">Such methods are referred to as *async methods*.</span></span>

<span data-ttu-id="43471-105">Metoda async zapewnia wygodny sposób wykonywania potencjalnie długotrwałych zadań bez blokowania wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="43471-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="43471-106">Obiekt wywołujący metodę Async może wznowić swoją pracę bez oczekiwania na zakończenie metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="43471-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="43471-107">Słowa kluczowe `Async` i `Await` zostały wprowadzone w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="43471-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="43471-108">Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="43471-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="43471-109">Poniższy przykład pokazuje strukturę metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="43471-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="43471-110">Według Konwencji nazwy metod asynchronicznych kończą się na "Async".</span><span class="sxs-lookup"><span data-stu-id="43471-110">By convention, async method names end in "Async."</span></span>

```vb
Public Async Function ExampleMethodAsync() As Task(Of Integer)
    ' . . .

    ' At the Await expression, execution in this method is suspended and,
    ' if AwaitedProcessAsync has not already finished, control returns
    ' to the caller of ExampleMethodAsync. When the awaited task is
    ' completed, this method resumes execution.
    Dim exampleInt As Integer = Await AwaitedProcessAsync()

    ' . . .

    ' The return statement completes the task. Any method that is
    ' awaiting ExampleMethodAsync can now get the integer result.
    Return exampleInt
End Function
```

<span data-ttu-id="43471-111">Typowo, Metoda modyfikowana przez słowo kluczowe `Async` zawiera co najmniej jedno wyrażenie lub instrukcję [await](../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="43471-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span></span> <span data-ttu-id="43471-112">Metoda jest uruchamiana synchronicznie do momentu osiągnięcia pierwszego `Await`, w którym moment zostanie wstrzymany do momentu ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="43471-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="43471-113">W międzyczasie formant jest zwracany do obiektu wywołującego metody.</span><span class="sxs-lookup"><span data-stu-id="43471-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="43471-114">Jeśli metoda nie zawiera wyrażenia `Await` lub instrukcji, metoda nie jest wstrzymana i jest wykonywana jako metoda synchroniczna.</span><span class="sxs-lookup"><span data-stu-id="43471-114">If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="43471-115">Ostrzeżenie kompilatora ostrzega użytkownika o wszelkich metodach asynchronicznych, które nie zawierają `Await`, ponieważ taka sytuacja może wskazywać na błąd.</span><span class="sxs-lookup"><span data-stu-id="43471-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="43471-116">Aby uzyskać więcej informacji, zobacz [błąd kompilatora](../error-messages/bc42358.md).</span><span class="sxs-lookup"><span data-stu-id="43471-116">For more information, see the [compiler error](../error-messages/bc42358.md).</span></span>

<span data-ttu-id="43471-117">Słowo kluczowe `Async` jest niezastrzeżonym słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="43471-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="43471-118">Jest to słowo kluczowe, gdy modyfikuje metodę lub wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="43471-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="43471-119">We wszystkich innych kontekstach jest interpretowana jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="43471-119">In all other contexts, it is interpreted as an identifier.</span></span>

## <a name="return-types"></a><span data-ttu-id="43471-120">Typy zwracane</span><span class="sxs-lookup"><span data-stu-id="43471-120">Return Types</span></span>

<span data-ttu-id="43471-121">Metoda async to procedura [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) [lub procedura,](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) która ma zwracany typ <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="43471-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="43471-122">Metoda nie może deklarować żadnych parametrów [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="43471-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="43471-123">Należy określić `Task(Of TResult)` dla zwracanego typu metody asynchronicznej, jeśli instrukcja [Return](../../../visual-basic/language-reference/statements/return-statement.md) metody ma operand typu TResult.</span><span class="sxs-lookup"><span data-stu-id="43471-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="43471-124">Należy używać `Task`, jeśli podczas kończenia metody nie zostanie zwrócona wartość znacząca.</span><span class="sxs-lookup"><span data-stu-id="43471-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="43471-125">Oznacza to, że wywołanie metody zwraca `Task`, ale gdy `Task` zostanie ukończona, każda instrukcja `Await`, która oczekuje na `Task`, nie tworzy wartości wynikowej.</span><span class="sxs-lookup"><span data-stu-id="43471-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>

<span data-ttu-id="43471-126">Procedury podrzędne są używane głównie do definiowania programów obsługi zdarzeń, gdy wymagana jest procedura `Sub`.</span><span class="sxs-lookup"><span data-stu-id="43471-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="43471-127">Obiekt wywołujący procedury asynchronicznej nie może w tej chwili oczekiwać i nie może przechwytywać wyjątków, które metoda zgłasza.</span><span class="sxs-lookup"><span data-stu-id="43471-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="43471-128">Aby uzyskać więcej informacji i przykładów, zobacz [asynchroniczne typy zwracane](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="43471-128">For more information and examples, see [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="43471-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="43471-129">Example</span></span>

<span data-ttu-id="43471-130">W poniższych przykładach przedstawiono asynchroniczną procedurę obsługi zdarzeń, asynchroniczne wyrażenie lambda i metodę asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="43471-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="43471-131">Aby zapoznać się z pełnym przykładem korzystającym z tych elementów, zobacz [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="43471-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="43471-132">Możesz pobrać kod instruktażowy z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="43471-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

```vb
' An event handler must be a Sub procedure.
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click
    textBox1.Clear()
    ' SumPageSizesAsync is a method that returns a Task.
    Await SumPageSizesAsync()
    textBox1.Text = vbCrLf & "Control returned to button1_Click."
End Sub

' The following async lambda expression creates an equivalent anonymous
' event handler.
AddHandler button1.Click, Async Sub(sender, e)
                              textBox1.Clear()
                              ' SumPageSizesAsync is a method that returns a Task.
                              Await SumPageSizesAsync()
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."
                          End Sub

' The following async method returns a Task(Of T).
' A typical call awaits the Byte array result:
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

    ' The downloaded resource ends up in the variable named content.
    Dim content = New MemoryStream()

    ' Initialize an HttpWebRequest for the current URL.
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

    ' Send the request to the Internet resource and wait for
    ' the response.
    Using response As WebResponse = Await webReq.GetResponseAsync()
        ' Get the data stream that is associated with the specified URL.
        Using responseStream As Stream = response.GetResponseStream()
            ' Read the bytes in responseStream and copy them to content.
            ' CopyToAsync returns a Task, not a Task<T>.
            Await responseStream.CopyToAsync(content)
        End Using
    End Using

    ' Return the result as a byte array.
    Return content.ToArray()
End Function
```

## <a name="see-also"></a><span data-ttu-id="43471-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43471-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="43471-134">Await, operator</span><span class="sxs-lookup"><span data-stu-id="43471-134">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="43471-135">Programowanie asynchroniczne z Async i Await</span><span class="sxs-lookup"><span data-stu-id="43471-135">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="43471-136">Przewodnik: uzyskiwanie dostępu do sieci za pomocą Async i Await</span><span class="sxs-lookup"><span data-stu-id="43471-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
