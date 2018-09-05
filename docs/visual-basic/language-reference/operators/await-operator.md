---
title: Await — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 2094ba308ba384feb8542e896cb1eafcf645947c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524469"
---
# <a name="await-operator-visual-basic"></a>Await — Operator (Visual Basic)
Należy zastosować `Await` operatora do argumentu operacji w asynchronicznej metody lub wyrażenia lambda wstrzymać wykonywanie metody, dopóki nie zakończy się oczekiwane zadanie. Zadanie reprezentuje pracę w toku.  
  
 Metody, w którym `Await` służy musi mieć [Async](../../../visual-basic/language-reference/modifiers/async.md) modyfikator. Taka metoda, zdefiniowana za pomocą `Async` modyfikator i zwykle zawierająca co najmniej jeden `Await` wyrażeń, jest określany jako *metody asynchronicznej*.  
  
> [!NOTE]
>  `Async` i `Await` słowa kluczowe zostały wprowadzone w programie Visual Studio 2012. Wprowadzenie do programowania asynchronicznego, zobacz [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Zwykle zadania, do którego zastosowano `Await` operator jest wartością zwracaną z wywołania do metody, która implementuje [wzorca asynchronicznego opartego na zadaniach](https://go.microsoft.com/fwlink/?LinkId=204847), która jest <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.  
  
 W poniższym kodzie <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> zwraca `getContentsTask`, `Task(Of Byte())`. Zadanie jest obietnicą utworzenia rzeczywistej tablicy bajtowej, po zakończeniu operacji. `Await` Operator jest stosowany do `getContentsTask` w celu wstrzymania wykonywania w metodzie `SumPageSizesAsync` aż `getContentsTask` zostało zakończone. W międzyczasie formant zostaje zwrócony do obiektu wywołującego `SumPageSizesAsync`. Gdy `getContentsTask` został zakończony, `Await` wynikiem wyrażenia jest tablicą bajtów.  
  
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
>  Aby uzyskać kompletny przykład, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Możesz pobrać próbkę z [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) w witrynie internetowej firmy Microsoft. Przykład znajduje się w projekcie AsyncWalkthrough_HttpClient.  
  
 Jeśli `Await` jest stosowany do wyniku wywołania metody, która zwraca `Task(Of TResult)`, typ `Await` wyrażenie jest TResult. Jeśli `Await` jest stosowany do wyniku wywołania metody, która zwraca `Task`, `Await` wyrażenie nie zwraca wartości. Poniższy przykład ilustruje tę różnicę.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 `Await` Wyrażenia lub instrukcji nie blokuje wątku, na którym jest wykonywany. Zamiast tego należy go powoduje, że kompilator pozostałą metodę asynchronicznej po `Await` wyrażenia jako kontynuację w oczekiwane zadanie. Formant powraca do obiektu wywołującego metody asynchronicznej. Po zakończeniu zadania wywołuje jego kontynuację, a wykonywanie metody asynchronicznej zostaje wznowione tam, gdzie ją przerwaliśmy.  
  
 `Await` Wyrażenie może wystąpić tylko w treści bezpośrednio otaczającej metody lub wyrażenia lambda, oznaczonej przez `Async` modyfikator. Termin *Await* służy jako słowo kluczowe tylko w tym kontekście. Gdzie indziej będzie interpretowany jako identyfikator. W ramach asynchronicznej metody lub wyrażenia lambda `Await` wyrażenia nie może wystąpić w wyrażeniu zapytania w `catch` lub `finally` bloku [spróbuj... CATCH... Na koniec](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) instrukcji w pętli kontroli zmiennej wyrażeniu `For` lub `For Each` pętli, lub w treści [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji.  
  
## <a name="exceptions"></a>Wyjątki  
 Większości metod asynchronicznych zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Właściwości zwracanego zadania przenoszą informacje o jego stanie i historii, takich jak tego, czy zadanie zostało ukończone, czy metoda async spowodowała wyjątek lub została anulowana i jaki jest wynik końcowy. `Await` Operator uzyskuje dostęp do tych właściwości.  
  
 Jeśli włączysz zwracającą zadanie metodę asynchroniczną, która powoduje wyjątek `Await` operator ponownie zgłasza wyjątek.  
  
 Jeśli włączysz zwracającą zadanie metody asynchronicznej, która została anulowana, `Await` ponownie zgłasza operator <xref:System.OperationCanceledException>.  
  
 Pojedynczego zadania, które jest w stanie błędnym może odzwierciedlać wiele wyjątków.  Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. W przypadku takiego zadania, ponownie zgłasza operacji await, tylko jeden z wyjątków. Jednak nie można przewidzieć, który z tych wyjątków jest zgłaszany ponownie.  
  
 Aby uzyskać przykłady obsługi błędów w metodach asynchronicznych, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład Windows Forms ilustruje użycie `Await` w metodzie asynchronicznej, `WaitAsynchronouslyAsync`. Porównaj zachowanie tej metody z zachowaniem `WaitSynchronously`. Bez `Await` operatora `WaitSynchronously` działa synchronicznie, mimo zastosowania `Async` modyfikator w jej definicji i wywołania <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w jej treści.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Przewodnik: uzyskiwanie dostępu do sieci za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Async](../../../visual-basic/language-reference/modifiers/async.md)
