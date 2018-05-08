---
title: Parametry i wartości zwracane dla procedur wielowątkowości (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 039e9be6f174148995a83c842a442806b9409a3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Parametry i wartości zwracane dla procedur wielowątkowości (Visual Basic)
Dostarczania i wartości zwracane w aplikacji wielowątkowych jest skomplikowane, ponieważ Konstruktor w klasie wątku muszą być przekazywane odwołanie do procedury, która nie przyjmuje żadnych argumentów i nie zwraca żadnej wartości. W poniższych sekcjach przedstawiono kilka prostych sposobów Podaj parametry i zwrócić wartości z procedury w oddzielnych wątkach.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Podając parametrami dla procedur wielowątkowości  
 Najlepszy sposób, aby podać parametry w celu wywołania metody wielowątkowe jest zawijany docelowej metody w klasie i definiowanie pól dla tej klasy, która będzie służyć jako parametry dla nowego wątku. Zaletą tej metody jest, możesz utworzyć nowe wystąpienie klasy, z własnego parametrów, za każdym razem, gdy ma się rozpocząć nowego wątku. Załóżmy na przykład funkcji, która oblicza obszaru trójkąt, zgodnie z poniższym kodem:  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Można napisać klasę, która opakowuje `CalcArea` funkcji i tworzy pola do przechowywania parametrów wejściowych, w następujący sposób:  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 Aby użyć `AreaClass`, można utworzyć `AreaClass` obiektu i ustawić `Base` i `Height` właściwości, jak pokazano w poniższym kodzie:  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 Zwróć uwagę, że `TestArea` procedury nie sprawdza wartość `Area` pole po wywołaniu `CalcArea` metody. Ponieważ `CalcArea` jest uruchamiana w oddzielnym wątku `Area` pola nie jest gwarantowana można ustawić, jeśli zaznaczysz natychmiast po wywołaniu `Thread.Start`. W następnej sekcji omówiono lepszy sposób, aby zwrócić wartości z procedur wielowątkowości.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Zwracanie wartości z procedur wielowątkowości  
 Zwracanie wartości z procedury, które są uruchamiane w oddzielnych wątkach jest złożona faktem, że procedury nie może być funkcji i nie można użyć `ByRef` argumentów. Najprostszym sposobem, aby zwrócić wartości jest użycie <xref:System.ComponentModel.BackgroundWorker> składnik do zarządzania z wątków i wywołaj zdarzenie po zakończeniu zadania i przetworzyć wyników z obsługi zdarzeń.  
  
 Poniższy przykład zwraca wartość przez wywołanie zdarzenia z systemem w oddzielnym wątku procedury:  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 Można podać parametry i wartości zwracane wątków z puli wątków przy użyciu opcjonalnego `ByVal` zmiennej obiektu stanu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody. Wątek czasomierza wątków obsługują także obiekt stanu w tym celu. Aby uzyskać informacje na korzystanie z puli wątków i czasomierze wątków, zobacz [(Visual Basic) korzystanie z puli wątków](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[korzystanie z puli wątków](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) i [czasomierze wątków (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Wątku puli (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [Synchronizacja wątku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Aplikacje wielowątkowe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Wielowątkowość składników](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
