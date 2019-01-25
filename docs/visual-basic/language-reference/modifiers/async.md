---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 654c397918f564bbba9ce91ebd8135b14dd7abb1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561455"
---
# <a name="async-visual-basic"></a>Async (Visual Basic)
`Async` Modyfikator wskazuje, że metoda lub [wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) że modyfikuje jest asynchroniczna. Metody te są nazywane *metod asynchronicznych*.  
  
 Metoda asynchroniczna zapewnia wygodny sposób do potencjalnie długotrwałej pracy bez blokowania wątku obiektu wywołującego. Obiekt wywołujący metodę komunikacji asynchronicznej może wznowić swoją pracę bez oczekiwania na zakończenie metody asynchronicznej.  
  
> [!NOTE]
>  `Async` i `Await` słowa kluczowe zostały wprowadzone w programie Visual Studio 2012. Wprowadzenie do programowania asynchronicznego, zobacz [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Poniższy przykład pokazuje strukturę metody asynchronicznej. Według Konwencji nazwy metody async kończy się "Async".  
  
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
  
 Zazwyczaj metoda zmodyfikowane przez `Async` — słowo kluczowe zawiera co najmniej jeden [Await](../../../visual-basic/language-reference/modifiers/async.md) wyrażenia lub instrukcji. Metoda działa synchronicznie, dopóki nie zostanie osiągnięty pierwszy `Await`, w tym momencie wstrzymuje, dopóki nie zakończy się oczekiwane zadanie. W międzyczasie zwróceniem sterowania do obiektu wywołującego metody. Jeśli metoda nie zawiera `Await` wyrażenia lub instrukcji, metoda nie jest wstrzymana i jest wykonywana jak metoda synchroniczna. Ostrzeżenia kompilatora ostrzega przed wszystkimi metodami asynchronicznymi, które nie zawierają `Await` , ponieważ taka sytuacja może wskazywać na błąd. Aby uzyskać więcej informacji, zobacz [błąd kompilatora](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 `Async` — Słowo kluczowe jest niezastrzeżone słowa kluczowego. Gdy modyfikuje metodę, lub wyrażenie lambda jest słowem kluczowym. W innych kontekstach jest interpretowane jako identyfikator.  
  
## <a name="return-types"></a>Typy zwracane  
 Jest to metoda asynchroniczna [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedury lub [funkcja](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedury, która ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Metoda nie może deklarować [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametrów.  
  
 Należy określić `Task(Of TResult)` dla zwracanego typu metody asynchronicznej Jeśli [zwracają](../../../visual-basic/language-reference/statements/return-statement.md) instrukcja metody zawiera operandę typu TResult. Możesz użyć `Task` Jeśli żadna mająca znaczenie wartość jest zwracana, gdy metoda zostanie zakończona. Oznacza to, że wywołanie metody zwraca `Task`, ale gdy `Task` zostanie zakończona, wszelkie `Await` instrukcję, która oczekuje na `Task` nie generuje wartości wyniku.  
  
 Asynchroniczne procedur są używane głównie do definiowania programów obsługi zdarzeń gdzie `Sub` procedura jest wymagana. Obiekt wywołujący podprocedury async nie może oczekiwać i nie może przechwytywać wyjątków, które metoda wygeneruje.  
  
 Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano program obsługi zdarzeń asynchronicznych, asynchroniczne Wyrażenie lambda i metody asynchronicznej. Aby uzyskać pełny przykład, który korzysta z tych elementów, zobacz [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Możesz pobrać kod przejściowy z [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Await, operator](../../../visual-basic/language-reference/operators/await-operator.md)
- [Programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
