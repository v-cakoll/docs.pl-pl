---
title: "Czasomierze wątków (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 809cba93-cc93-4e21-afda-f299f9a39818
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b828476301424ca767e2b581c173d6a2dcd184ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="thread-timers-visual-basic"></a>Czasomierze wątków (Visual Basic)
<xref:System.Threading.Timer?displayProperty=nameWithType> Klasy jest przydatne w przypadku okresowo uruchamianie zadania w oddzielnym wątku. Można na przykład użyć czasomierza wątku, sprawdź stan i integralności bazy danych lub utworzyć kopię zapasową plików krytycznych.  
  
## <a name="thread-timer-example"></a>Przykład czasomierza wątku  
 W poniższym przykładzie uruchamia zadanie, co dwie sekundy i używa flagę zainicjować <xref:System.IDisposable.Dispose%2A> metodę, która zatrzymuje czasomierza. W tym przykładzie wpisów stanu w oknie danych wyjściowych.  
  
```vb  
Private Class StateObjClass  
    ' Used to hold parameters for calls to TimerTask.  
    Public SomeValue As Integer  
    Public TimerReference As System.Threading.Timer  
    Public TimerCanceled As Boolean  
End Class  
  
Public Sub RunTimer()  
    Dim StateObj As New StateObjClass  
    StateObj.TimerCanceled = False  
    StateObj.SomeValue = 1  
    Dim TimerDelegate As New System.Threading.TimerCallback(AddressOf TimerTask)  
    ' Create a timer that calls a procedure every 2 seconds.  
    ' Note: There is no Start method; the timer starts running as soon as   
    ' the instance is created.  
    Dim TimerItem As New System.Threading.Timer(TimerDelegate, StateObj,  
                                                2000, 2000)  
    ' Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem  
  
    ' Run for ten loops.  
    While StateObj.SomeValue < 10  
        ' Wait one second.  
        System.Threading.Thread.Sleep(1000)  
    End While  
  
    ' Request Dispose of the timer object.  
    StateObj.TimerCanceled = True  
End Sub  
  
Private Sub TimerTask(ByVal StateObj As Object)  
    Dim State As StateObjClass = CType(StateObj, StateObjClass)  
    ' Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(State.SomeValue)  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " & Now.ToString)  
    If State.TimerCanceled Then  
        ' Dispose Requested.  
        State.TimerReference.Dispose()  
        System.Diagnostics.Debug.WriteLine("Done  " & Now)  
    End If  
End Sub  
```  
  
 Czasomierze wątków są szczególnie przydatne, gdy <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> obiekt jest niedostępny, takie jak podczas tworzenia aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading>  
 [Aplikacje wielowątkowe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)
