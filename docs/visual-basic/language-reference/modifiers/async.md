---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: ad6d671a45cee7d534347d23963bb5035ecc8dac
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834593"
---
# <a name="async-visual-basic"></a><span data-ttu-id="8846f-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8846f-102">Async (Visual Basic)</span></span>
<span data-ttu-id="8846f-103">`Async` Modyfikator wskazuje, że metoda lub [wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) że modyfikuje jest asynchroniczna.</span><span class="sxs-lookup"><span data-stu-id="8846f-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="8846f-104">Metody te są nazywane *metod asynchronicznych*.</span><span class="sxs-lookup"><span data-stu-id="8846f-104">Such methods are referred to as *async methods*.</span></span>  
  
 <span data-ttu-id="8846f-105">Metoda asynchroniczna zapewnia wygodny sposób do potencjalnie długotrwałej pracy bez blokowania wątku obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8846f-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="8846f-106">Obiekt wywołujący metodę komunikacji asynchronicznej może wznowić swoją pracę bez oczekiwania na zakończenie metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8846f-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8846f-107">`Async` i `Await` słowa kluczowe zostały wprowadzone w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="8846f-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="8846f-108">Wprowadzenie do programowania asynchronicznego, zobacz [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="8846f-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="8846f-109">Poniższy przykład pokazuje strukturę metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8846f-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="8846f-110">Według Konwencji nazwy metody async kończy się "Async".</span><span class="sxs-lookup"><span data-stu-id="8846f-110">By convention, async method names end in "Async."</span></span>  
  
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
  
 <span data-ttu-id="8846f-111">Zazwyczaj metoda zmodyfikowane przez `Async` — słowo kluczowe zawiera co najmniej jeden [Await](../../../visual-basic/language-reference/modifiers/async.md) wyrażenia lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8846f-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span></span> <span data-ttu-id="8846f-112">Metoda działa synchronicznie, dopóki nie zostanie osiągnięty pierwszy `Await`, w tym momencie wstrzymuje, dopóki nie zakończy się oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="8846f-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="8846f-113">W międzyczasie zwróceniem sterowania do obiektu wywołującego metody.</span><span class="sxs-lookup"><span data-stu-id="8846f-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="8846f-114">Jeśli metoda nie zawiera `Await` wyrażenia lub instrukcji, metoda nie jest wstrzymana i jest wykonywana jak metoda synchroniczna.</span><span class="sxs-lookup"><span data-stu-id="8846f-114">If the method doesn’t contain an `Await` expression or statement, the method isn’t suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="8846f-115">Ostrzeżenia kompilatora ostrzega przed wszystkimi metodami asynchronicznymi, które nie zawierają `Await` , ponieważ taka sytuacja może wskazywać na błąd.</span><span class="sxs-lookup"><span data-stu-id="8846f-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="8846f-116">Aby uzyskać więcej informacji, zobacz [błąd kompilatora](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="8846f-116">For more information, see the [compiler error](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).</span></span>  
  
 <span data-ttu-id="8846f-117">`Async` — Słowo kluczowe jest niezastrzeżone słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="8846f-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="8846f-118">Gdy modyfikuje metodę, lub wyrażenie lambda jest słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="8846f-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="8846f-119">W innych kontekstach jest interpretowane jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="8846f-119">In all other contexts, it is interpreted as an identifier.</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="8846f-120">Typy zwracane</span><span class="sxs-lookup"><span data-stu-id="8846f-120">Return Types</span></span>  
 <span data-ttu-id="8846f-121">Jest to metoda asynchroniczna [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedury lub [funkcja](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedury, która ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="8846f-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="8846f-122">Metoda nie może deklarować [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="8846f-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="8846f-123">Należy określić `Task(Of TResult)` dla zwracanego typu metody asynchronicznej Jeśli [zwracają](../../../visual-basic/language-reference/statements/return-statement.md) instrukcja metody zawiera operandę typu TResult.</span><span class="sxs-lookup"><span data-stu-id="8846f-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="8846f-124">Możesz użyć `Task` Jeśli żadna mająca znaczenie wartość jest zwracana, gdy metoda zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="8846f-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="8846f-125">Oznacza to, że wywołanie metody zwraca `Task`, ale gdy `Task` zostanie zakończona, wszelkie `Await` instrukcję, która oczekuje na `Task` nie generuje wartości wyniku.</span><span class="sxs-lookup"><span data-stu-id="8846f-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>  
  
 <span data-ttu-id="8846f-126">Asynchroniczne procedur są używane głównie do definiowania programów obsługi zdarzeń gdzie `Sub` procedura jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="8846f-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="8846f-127">Obiekt wywołujący podprocedury async nie może oczekiwać i nie może przechwytywać wyjątków, które metoda wygeneruje.</span><span class="sxs-lookup"><span data-stu-id="8846f-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="8846f-128">Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="8846f-128">For more information and examples, see [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8846f-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="8846f-129">Example</span></span>  
 <span data-ttu-id="8846f-130">W poniższych przykładach pokazano program obsługi zdarzeń asynchronicznych, asynchroniczne Wyrażenie lambda i metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8846f-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="8846f-131">Aby uzyskać pełny przykład, który korzysta z tych elementów, zobacz [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="8846f-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="8846f-132">Możesz pobrać kod przejściowy z [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="8846f-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
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
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
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
  
## <a name="see-also"></a><span data-ttu-id="8846f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8846f-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="8846f-134">Await, operator</span><span class="sxs-lookup"><span data-stu-id="8846f-134">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="8846f-135">Programowanie asynchroniczne z Async i Await</span><span class="sxs-lookup"><span data-stu-id="8846f-135">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="8846f-136">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await</span><span class="sxs-lookup"><span data-stu-id="8846f-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
