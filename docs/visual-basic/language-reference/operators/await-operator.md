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
# <a name="await-operator-visual-basic"></a>Await — Operator (Visual Basic)
Należy zastosować `Await` operatora operandu w asynchronicznej metody lub wyrażenia lambda wstrzymania wykonywanie metody do momentu ukończenia zadania oczekiwano. Zadanie reprezentuje pracy w toku.  
  
 Metoda, w którym `Await` służy musi mieć [Async](../../../visual-basic/language-reference/modifiers/async.md) modyfikator. Taka metoda, zdefiniowany przy użyciu `Async` modyfikator i zazwyczaj zawierającego co najmniej jeden `Await` wyrażenia, jest określany jako *metody asynchronicznej*.  
  
> [!NOTE]
>  `Async` i `Await` słowa kluczowe wprowadzono w programie Visual Studio 2012. Aby obejrzeć wprowadzenie do programowania asynchronicznego Zobacz [programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Zwykle zadania, do którego należy zastosować `Await` operator jest wartością zwracaną przez wywołanie do metody, która implementuje [wzorca asynchronicznego opartego na zadaniach](http://go.microsoft.com/fwlink/?LinkId=204847), która jest <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.  
  
 W poniższym kodzie <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> zwraca `getContentsTask`, `Task(Of Byte())`. Zadanie jest obietnicę w celu utworzenia tablicy bajtowej rzeczywiste po zakończeniu operacji. `Await` Operator jest stosowany do `getContentsTask` wstrzymania wykonywania w `SumPageSizesAsync` do momentu `getContentsTask` została ukończona. Tymczasem zwróceniem sterowania do wywołującego `SumPageSizesAsync`. Gdy `getContentsTask` zostało zakończone, `Await` wyrażenie na tablicę bajtów.  
  
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
>  Aby uzyskać pełny przykład, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Możesz pobrać próbki z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) w witrynie firmy Microsoft. Przykładem jest w projekcie AsyncWalkthrough_HttpClient.  
  
 Jeśli `Await` jest stosowany do wyniku wywołania metody, która zwraca `Task(Of TResult)`, typ `Await` wyrażenie jest TResult. Jeśli `Await` jest stosowany do wyniku wywołania metody, która zwraca `Task`, `Await` wyrażenie nie zwraca wartości. Poniższy przykład przedstawia różnicy.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 `Await` Wyrażenia lub instrukcji nie są blokowane w wątku, na którym jest wykonywany. Zamiast tego należy go powoduje, że kompilator rejestracja pozostałe metody asynchronicznej po `Await` jako kontynuacji zadania Oczekiwano wyrażenia. Formant zwraca do obiektu wywołującego metody asynchronicznej. Po ukończeniu zadania wywołuje kontynuacji i wykonywania wznawia metody asynchronicznej miejsca, w którym.  
  
 `Await` Wyrażenie może wystąpić tylko w treści natychmiastowo otaczającą metody lub wyrażenia lambda oznaczonym za `Async` modyfikator. Termin *Await* służy jako słowo kluczowe tylko w tym kontekście. W innym miejscu jest interpretowany jako identyfikator. W ramach asynchronicznej metody lub wyrażenia lambda `Await` wyrażenia nie może wystąpić w wyrażeniu zapytania w `catch` lub `finally` zablokować z [spróbuj... CATCH... Na koniec](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) instrukcji w pętli sterowania zmiennej wyrażeniu `For` lub `For Each` pętli lub w treści [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji.  
  
## <a name="exceptions"></a>Wyjątki  
 Zwraca większości metod asynchronicznych <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Właściwości zadania zwróconego zawierać informacje o jego stan i Historia, na przykład tego, czy zadanie zostało ukończone, czy metoda asynchroniczna spowodowała wyjątek lub została anulowana i jakie wynik końcowy jest. `Await` Operator uzyskuje dostęp do tych właściwości.  
  
 Jeśli await umożliwiające zwracanie zadań metoda asynchroniczna, która powoduje zgłoszenie wyjątku `Await` operator ponownie zgłasza wyjątek.  
  
 Jeśli await umożliwiające zwracanie zadań metoda asynchroniczna, która została anulowana, `Await` operator ponownie zgłasza wyjątek <xref:System.OperationCanceledException>.  
  
 Pojedyncze zadanie, który jest stan można odzwierciedlać wiele wyjątków.  Na przykład zadanie może być wynikiem wywołania do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Gdy await takie zadania, ponownie zgłasza operacji await tylko jeden z wyjątków. Jednak nie można przewidzieć który wyjątki jest zgłoszony.  
  
 Przykłady obsługi błędów w metodach asynchronicznych, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie formularzy systemu Windows ilustruje użycie `Await` w metodzie asynchronicznej `WaitAsynchronouslyAsync`. Natomiast zachowanie tej metody z zachowaniem `WaitSynchronously`. Bez `Await` operatora, `WaitSynchronously` synchronicznie działa niezależnie od stosowania `Async` modyfikator w swojej definicji i wywołanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w jego treści.  
  
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
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Asynchroniczne](../../../visual-basic/language-reference/modifiers/async.md)
