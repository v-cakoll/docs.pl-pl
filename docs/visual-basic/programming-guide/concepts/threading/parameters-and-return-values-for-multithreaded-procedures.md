---
title: Parametry i wartości zwracane dla procedur wielowątkowości (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 545da3e89d44c29c67784b5f01812d87350030c6
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874614"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Parametry i wartości zwracane dla procedur wielowątkowości (Visual Basic)
Dostarczanie i zwracanie wartości w aplikacji wielowątkowych jest skomplikowane, ponieważ Konstruktor klasy wątku muszą zostać przekazane odwołanie do procedury, która nie przyjmuje żadnych argumentów i nie zwraca żadnej wartości. W poniższych sekcjach opisano niektóre upraszczają podać parametry i zwracane wartości z procedury w oddzielnych wątkach.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Podając parametry dla procedur wielowątkowości  
 Najlepszym sposobem podać parametry w celu wywołania metody wielowątkowe jest zawijany do metody docelowej w klasie i definiowania pól dla tej klasy, która będzie służyć jako parametry dla nowego wątku. Zaletą tego podejścia jest, że można utworzyć nowe wystąpienie klasy, z własną parametrami za każdym razem, gdy chcesz rozpocząć nowego wątku. Na przykład załóżmy, że funkcja obliczający pole trójkąt, zgodnie z poniższym kodem:  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Można napisać klasę, która otacza `CalcArea` działać, a następnie tworzy pola do przechowywania parametrów wejściowych w następujący sposób:  
  
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
  
 Aby użyć `AreaClass`, możesz utworzyć `AreaClass` obiektu, a następnie ustaw `Base` i `Height` właściwości, jak pokazano w poniższym kodzie:  
  
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
  
 Należy zauważyć, że `TestArea` procedury nie sprawdza wartość `Area` pola po wywołaniu `CalcArea` metody. Ponieważ `CalcArea` działa w oddzielnym wątku `Area` pole nie jest gwarantowana można ustawić, jeśli zaznaczysz natychmiast po wywołaniu `Thread.Start`. W następnej sekcji omówiono lepszy sposób, aby zwrócić wartości z procedur wielowątkowości.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Zwracanie wartości z procedur wielowątkowości  
 Zwracanie wartości z procedury, które są uruchamiane w oddzielnych wątkach jest skomplikowane faktem, że procedury nie może być funkcji i nie można użyć `ByRef` argumentów. Najprostszym sposobem, aby zwrócić wartości jest użycie <xref:System.ComponentModel.BackgroundWorker> składnik do zarządzania wątki i wywołać zdarzenie, gdy zadanie jest wykonywane i przetworzyć wyniki za pomocą programu obsługi zdarzeń.  
  
 Poniższy przykład zwraca wartość przez podnoszenie zdarzenia z procedury uruchomione w oddzielnym wątku:  
  
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
  
 Można podać parametry i zwracane wartości dla wątków w puli wątków przy użyciu opcjonalnego `ByVal` zmiennej obiektu stanu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody. Wątków czasomierza wątku obsługują także obiekt stanu, w tym celu. Aby uzyskać informacje na korzystanie z puli wątków i czasomierze wątków, zobacz [(Visual Basic) korzystanie z puli wątków](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[korzystanie z puli wątków](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) i [czasomierzy](../../../../standard/threading/timers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Wątek puli (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [Synchronizacja wątku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Aplikacje wielowątkowe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Wielowątkowość w składnikach](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
