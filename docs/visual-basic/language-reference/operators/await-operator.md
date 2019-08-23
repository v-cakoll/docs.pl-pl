---
title: Await — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: d3bfafaa696955422c381aa1c17bc96591b44985
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961998"
---
# <a name="await-operator-visual-basic"></a>Await — Operator (Visual Basic)
`Await` Operator jest stosowany do operandu w metodzie asynchronicznej lub wyrażeniu lambda, aby wstrzymać wykonywanie metody do momentu ukończenia zadania. Zadanie reprezentuje trwającą prace.  
  
 Używana metoda `Await` musi mieć Modyfikator [Async](../../../visual-basic/language-reference/modifiers/async.md) . Takie metody, zdefiniowane za pomocą `Async` modyfikatora i zwykle zawierające co najmniej jeden `Await` wyrażenie, są określane jako *Metoda async*.  
  
> [!NOTE]
> Słowa kluczowe `Await` i zostały wprowadzone w programie Visual Studio 2012. `Async` Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Zwykle zadanie, do którego `Await` zastosowano operator, jest wartością zwracaną z wywołania metody implementującej [wzorzec asynchroniczny oparty na zadaniach](https://go.microsoft.com/fwlink/?LinkId=204847), czyli a <xref:System.Threading.Tasks.Task> lub. <xref:System.Threading.Tasks.Task%601>  
  
 W poniższym kodzie <xref:System.Net.Http.HttpClient> Metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> zwraca `getContentsTask`, a `Task(Of Byte())`. Zadanie to obietnica do tworzenia rzeczywistej tablicy bajtowej po zakończeniu operacji. Operator zostanie zastosowany do `getContentsTask` wstrzymania wykonywania w `SumPageSizesAsync` programie `getContentsTask` do momentu ukończenia. `Await` W międzyczasie formant jest zwracany do obiektu wywołującego `SumPageSizesAsync`. Po `getContentsTask` zakończeniu`Await` wyrażenie daje w wyniku tablicę bajtów.  
  
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
> Aby zapoznać się z kompletnym [przykładem, zobacz Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)Async i await. Możesz pobrać przykład z [przykładów kodu dla deweloperów](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) w witrynie sieci Web firmy Microsoft. Przykład znajduje się w projekcie AsyncWalkthrough_HttpClient.  
  
 Jeśli `Await` jest stosowany do wyniku wywołania metody, które `Task(Of TResult)`zwraca `Await` , typ wyrażenia jest TResult. Jeśli `Await` jest stosowany do wyniku wywołania metody, które `Task`zwraca, `Await` wyrażenie nie zwraca wartości. Poniższy przykład ilustruje różnicę.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 `Await` Wyrażenie lub instrukcja nie blokuje wątku, w którym jest wykonywane. Zamiast tego powoduje, że kompilator rejestruje resztę metody asynchronicznej, po `Await` wyrażeniu, jako kontynuację w oczekiwanym zadaniu. Następnie formant wraca do obiektu wywołującego metody asynchronicznej. Po zakończeniu zadania wywołuje jego kontynuację i wykonywanie metody asynchronicznej zostaje wznowione w miejscu, w którym została przerwana.  
  
 Wyrażenie może wystąpić tylko w treści bezpośrednio otaczającej metody lub wyrażenia lambda, które jest oznaczone `Async` modyfikatorem. `Await` Termin *await* służy jako słowo kluczowe tylko w tym kontekście. W innym miejscu jest interpretowana jako identyfikator. W metodzie asynchronicznej lub wyrażeniu `Await` lambda wyrażenie nie może wystąpić w wyrażeniu `catch` zapytania lub `finally` bloku [try... Catch... Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) , w wyrażeniu `For` zmiennej kontrolki pętli lub `For Each` w treści instrukcji [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) .  
  
## <a name="exceptions"></a>Wyjątki  
 Większość metod asynchronicznych zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Właściwości zwróconego zadania zawierają informacje o jego stanie i historii, na przykład o tym, czy zadanie zostało ukończone, czy Metoda asynchroniczna spowodowała wyjątek, czy została anulowana, oraz jaki jest wynik końcowy. `Await` Operator uzyskuje dostęp do tych właściwości.  
  
 Jeśli czekasz na metodę asynchroniczną zwracającą zadanie, która powoduje wyjątek, `Await` operator ponownie zgłosi wyjątek.  
  
 Jeśli oczekujesz, że Metoda asynchroniczna zwracająca zadanie została anulowana `Await` , operator <xref:System.OperationCanceledException>ponownie zgłosi.  
  
 Pojedyncze zadanie, które jest w stanie awarii może odzwierciedlać wiele wyjątków.  Na przykład zadanie może być wynikiem wywołania metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Po oczekiwaniu na takie zadanie Operacja await ponownie zgłosi tylko jeden z wyjątków. Nie można jednak przewidzieć, które wyjątki są ponownie zgłaszane.  
  
 Przykłady obsługi błędów w metodach asynchronicznych znajdują się w temacie [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład Windows Forms ilustruje użycie `Await` `WaitAsynchronouslyAsync`metody w metodzie asynchronicznej. Różnice w zachowaniu tej metody z zachowaniem `WaitSynchronously`. Bez operatora, wykonywane `WaitSynchronously` synchronicznie `Async` , pomimo użycia modyfikatora w jego definicji i wywołania do <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w swojej treści. `Await`  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../../../visual-basic/language-reference/modifiers/async.md)
