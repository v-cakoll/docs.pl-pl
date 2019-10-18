---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: fc0ae67c0ebc11a0428ffc18c8db103b619e27ec
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524804"
---
# <a name="async-visual-basic"></a>Async (Visual Basic)

Modyfikator `Async` wskazuje, że metoda lub [wyrażenie lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) , które modyfikuje jest asynchroniczne. Takie metody są nazywane *metodami asynchronicznymi*.

Metoda async zapewnia wygodny sposób wykonywania potencjalnie długotrwałych zadań bez blokowania wątku wywołującego. Obiekt wywołujący metodę Async może wznowić swoją pracę bez oczekiwania na zakończenie metody asynchronicznej.

> [!NOTE]
> Słowa kluczowe `Async` i `Await` zostały wprowadzone w programie Visual Studio 2012. Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../../visual-basic/programming-guide/concepts/async/index.md).

Poniższy przykład pokazuje strukturę metody asynchronicznej. Według Konwencji nazwy metod asynchronicznych kończą się na "Async".

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

Typowo, Metoda modyfikowana przez słowo kluczowe `Async` zawiera co najmniej jedno wyrażenie lub instrukcję [await](../../../visual-basic/language-reference/modifiers/async.md) . Metoda jest uruchamiana synchronicznie do momentu osiągnięcia pierwszego `Await`, w którym moment zostanie wstrzymany do momentu ukończenia zadania. W międzyczasie formant jest zwracany do obiektu wywołującego metody. Jeśli metoda nie zawiera wyrażenia `Await` lub instrukcji, metoda nie jest wstrzymana i jest wykonywana jako metoda synchroniczna. Ostrzeżenie kompilatora ostrzega użytkownika o wszelkich metodach asynchronicznych, które nie zawierają `Await`, ponieważ taka sytuacja może wskazywać na błąd. Aby uzyskać więcej informacji, zobacz [błąd kompilatora](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).

Słowo kluczowe `Async` jest niezastrzeżonym słowem kluczowym. Jest to słowo kluczowe, gdy modyfikuje metodę lub wyrażenie lambda. We wszystkich innych kontekstach jest interpretowana jako identyfikator.

## <a name="return-types"></a>Typy zwracane

Metoda async to procedura [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) [lub procedura,](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) która ma zwracany typ <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Metoda nie może deklarować żadnych parametrów [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .

Należy określić `Task(Of TResult)` dla zwracanego typu metody asynchronicznej, jeśli instrukcja [Return](../../../visual-basic/language-reference/statements/return-statement.md) metody ma operand typu TResult. Należy używać `Task`, jeśli podczas kończenia metody nie zostanie zwrócona wartość znacząca. Oznacza to, że wywołanie metody zwraca `Task`, ale gdy `Task` zostanie ukończona, każda instrukcja `Await`, która oczekuje na `Task`, nie tworzy wartości wynikowej.

Procedury podrzędne są używane głównie do definiowania programów obsługi zdarzeń, gdy wymagana jest procedura `Sub`. Obiekt wywołujący procedury asynchronicznej nie może w tej chwili oczekiwać i nie może przechwytywać wyjątków, które metoda zgłasza.

Aby uzyskać więcej informacji i przykładów, zobacz [asynchroniczne typy zwracane](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Przykład

W poniższych przykładach przedstawiono asynchroniczną procedurę obsługi zdarzeń, asynchroniczne wyrażenie lambda i metodę asynchroniczną. Aby zapoznać się z pełnym przykładem korzystającym z tych elementów, zobacz [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Możesz pobrać kod instruktażowy z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Await, operator](../../../visual-basic/language-reference/operators/await-operator.md)
- [Programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Przewodnik: uzyskiwanie dostępu do sieci za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
