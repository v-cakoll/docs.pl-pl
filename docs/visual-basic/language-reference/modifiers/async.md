---
title: Async
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 35df7a464937647c6d110142a3e2801cebbea505
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373170"
---
# <a name="async-visual-basic"></a><span data-ttu-id="ff89a-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff89a-102">Async (Visual Basic)</span></span>

<span data-ttu-id="ff89a-103">`Async`Modyfikator wskazuje, że metoda lub [wyrażenie lambda](../../programming-guide/language-features/procedures/lambda-expressions.md) , które modyfikuje jest asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="ff89a-103">The `Async` modifier indicates that the method or [lambda expression](../../programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="ff89a-104">Takie metody są nazywane *metodami asynchronicznymi*.</span><span class="sxs-lookup"><span data-stu-id="ff89a-104">Such methods are referred to as *async methods*.</span></span>

<span data-ttu-id="ff89a-105">Metoda async zapewnia wygodny sposób wykonywania potencjalnie długotrwałych zadań bez blokowania wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ff89a-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="ff89a-106">Obiekt wywołujący metodę Async może wznowić swoją pracę bez oczekiwania na zakończenie metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ff89a-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="ff89a-107">`Async` `Await` Słowa kluczowe i zostały wprowadzone w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ff89a-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="ff89a-108">Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="ff89a-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="ff89a-109">Poniższy przykład pokazuje strukturę metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ff89a-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="ff89a-110">Według Konwencji nazwy metod asynchronicznych kończą się na "Async".</span><span class="sxs-lookup"><span data-stu-id="ff89a-110">By convention, async method names end in "Async."</span></span>

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

<span data-ttu-id="ff89a-111">Typowo, Metoda modyfikowana przez `Async` słowo kluczowe zawiera co najmniej jedno wyrażenie lub instrukcję [await](async.md) .</span><span class="sxs-lookup"><span data-stu-id="ff89a-111">Typically, a method modified by the `Async` keyword contains at least one [Await](async.md) expression or statement.</span></span> <span data-ttu-id="ff89a-112">Metoda jest uruchamiana synchronicznie do momentu `Await` , w którym zostanie ona zawieszać do momentu zakończenia zadania oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="ff89a-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="ff89a-113">W międzyczasie formant jest zwracany do obiektu wywołującego metody.</span><span class="sxs-lookup"><span data-stu-id="ff89a-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="ff89a-114">Jeśli metoda nie zawiera `Await` wyrażenia lub instrukcji, metoda nie jest wstrzymana i jest wykonywana jako metoda synchroniczna.</span><span class="sxs-lookup"><span data-stu-id="ff89a-114">If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="ff89a-115">Ostrzeżenie kompilatora ostrzega użytkownika o wszelkich metodach asynchronicznych, które nie zawierają `Await` , ponieważ taka sytuacja może wskazywać na błąd.</span><span class="sxs-lookup"><span data-stu-id="ff89a-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="ff89a-116">Aby uzyskać więcej informacji, zobacz [błąd kompilatora](../error-messages/bc42358.md).</span><span class="sxs-lookup"><span data-stu-id="ff89a-116">For more information, see the [compiler error](../error-messages/bc42358.md).</span></span>

<span data-ttu-id="ff89a-117">`Async`Słowo kluczowe jest niezastrzeżonym słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="ff89a-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="ff89a-118">Jest to słowo kluczowe, gdy modyfikuje metodę lub wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="ff89a-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="ff89a-119">We wszystkich innych kontekstach jest interpretowana jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="ff89a-119">In all other contexts, it is interpreted as an identifier.</span></span>

## <a name="return-types"></a><span data-ttu-id="ff89a-120">Typy zwracane</span><span class="sxs-lookup"><span data-stu-id="ff89a-120">Return Types</span></span>

<span data-ttu-id="ff89a-121">Metoda async to procedura [Sub](../../programming-guide/language-features/procedures/sub-procedures.md) [lub procedura,](../../programming-guide/language-features/procedures/function-procedures.md) która ma zwracany typ <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="ff89a-121">An async method is either a [Sub](../../programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ff89a-122">Metoda nie może deklarować żadnych parametrów [ByRef](byref.md) .</span><span class="sxs-lookup"><span data-stu-id="ff89a-122">The method cannot declare any [ByRef](byref.md) parameters.</span></span>

<span data-ttu-id="ff89a-123">Określono `Task(Of TResult)` dla zwracanego typu metody asynchronicznej, jeśli instrukcja [Return](../statements/return-statement.md) metody ma operand typu TResult.</span><span class="sxs-lookup"><span data-stu-id="ff89a-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="ff89a-124">Należy użyć, `Task` Jeśli podczas kończenia metody nie zostanie zwrócona wartość znacząca.</span><span class="sxs-lookup"><span data-stu-id="ff89a-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="ff89a-125">Oznacza to, że wywołanie metody zwraca `Task` , ale gdy `Task` zostanie zakończone, każda `Await` instrukcja oczekująca `Task` nie tworzy wartości wyniku.</span><span class="sxs-lookup"><span data-stu-id="ff89a-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>

<span data-ttu-id="ff89a-126">Procedury podrzędne są używane głównie do definiowania programów obsługi zdarzeń, gdy `Sub` wymagana jest procedura.</span><span class="sxs-lookup"><span data-stu-id="ff89a-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="ff89a-127">Obiekt wywołujący procedury asynchronicznej nie może w tej chwili oczekiwać i nie może przechwytywać wyjątków, które metoda zgłasza.</span><span class="sxs-lookup"><span data-stu-id="ff89a-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="ff89a-128">Aby uzyskać więcej informacji i przykładów, zobacz [asynchroniczne typy zwracane](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ff89a-128">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="ff89a-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff89a-129">Example</span></span>

<span data-ttu-id="ff89a-130">W poniższych przykładach przedstawiono asynchroniczną procedurę obsługi zdarzeń, asynchroniczne wyrażenie lambda i metodę asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="ff89a-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="ff89a-131">Aby zapoznać się z pełnym przykładem korzystającym z tych elementów, zobacz [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="ff89a-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="ff89a-132">Możesz pobrać kod instruktażowy z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="ff89a-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ff89a-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff89a-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="ff89a-134">Operator await</span><span class="sxs-lookup"><span data-stu-id="ff89a-134">Await Operator</span></span>](../operators/await-operator.md)
- [<span data-ttu-id="ff89a-135">Programowanie asynchroniczne z Async i await</span><span class="sxs-lookup"><span data-stu-id="ff89a-135">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="ff89a-136">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await</span><span class="sxs-lookup"><span data-stu-id="ff89a-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
