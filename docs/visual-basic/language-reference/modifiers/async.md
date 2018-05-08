---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 829128ff39c0c5e4f6cb140852228a028e39e69c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="async-visual-basic"></a>Async (Visual Basic)
`Async` Modyfikator wskazuje, że metoda lub [wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) czy modyfikuje jest asynchroniczne. Metody te są określane jako *metod asynchronicznych*.  
  
 Metoda asynchroniczna oferują wygodny sposób w pracy potencjalnie długotrwałe bez blokowania wątków obiektu wywołującego. Element wywołujący metody asynchronicznej można wznowić pracę bez oczekiwania na metoda asynchroniczna zakończyć.  
  
> [!NOTE]
>  `Async` i `Await` słowa kluczowe wprowadzono w programie Visual Studio 2012. Aby obejrzeć wprowadzenie do programowania asynchronicznego Zobacz [programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Poniższy przykład przedstawia struktury metody asynchronicznej. Konwencja nazwy metod asynchronicznych kończyć się "Async".  
  
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
  
 Zazwyczaj metodę zmodyfikowany przez `Async` — słowo kluczowe zawiera co najmniej jeden [Await](../../../visual-basic/language-reference/modifiers/async.md) wyrażenia lub instrukcji. Metoda jest uruchamiana synchronicznie, dopóki nie osiągnie pierwszy `Await`, po czym wstrzymuje dopiero po zakończeniu zadania oczekiwano. Tymczasem zwróceniem sterowania do obiektu wywołującego metody. Jeśli metoda nie zawiera `Await` wyrażenia lub instrukcji metoda nie jest wstrzymana i wykonuje jak metoda synchroniczna. Ostrzeżenie kompilatora ostrzega o dowolnej metody asynchroniczne, które nie zawierają `Await` ponieważ taka sytuacja może wskazywać na błąd. Aby uzyskać więcej informacji, zobacz [błąd kompilatora](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 `Async` — Słowo kluczowe jest bezwarunkowe — słowo kluczowe. Gdy modyfikuje metody lub wyrażenia lambda, jest słowem kluczowym. W innych kontekstach jest interpretowany jako identyfikator.  
  
## <a name="return-types"></a>Typy zwracane  
 Jest to metoda asynchroniczna [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedury lub [funkcja](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedury, która ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Metody nie można zadeklarować żadnego [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametrów.  
  
 Należy określić `Task(Of TResult)` dla zwracany typ metody asynchronicznej Jeśli [zwracać](../../../visual-basic/language-reference/statements/return-statement.md) instrukcji metody ma argumentu operacji typu TResult. Możesz użyć `Task` Jeśli nie istotnych wartość jest zwracana po zakończeniu metody. Oznacza to, zwraca wywołanie do metody `Task`, ale jeśli `Task` zostało zakończone, wszelkie `Await` instrukcji, która oczekuje na `Task` nie tworzy wartości wyniku.  
  
 Asynchronicznej podprocedury są używane głównie w celu definiowania metod obsługi zdarzeń gdzie `Sub` procedura jest wymagana. Element wywołujący asynchronicznej podprocedury nie można zdefiniować oczekiwania go i nie przechwytuje wyjątków, które metoda zgłasza.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [Async zwracać typów](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano asynchronicznej obsługi zdarzeń, asynchroniczne Wyrażenie lambda i metody asynchronicznej. Na przykład pełna, który używa tych elementów, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Możesz pobrać kod wskazówki z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [Await, operator](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Przewodnik: uzyskiwanie dostępu do sieci za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
