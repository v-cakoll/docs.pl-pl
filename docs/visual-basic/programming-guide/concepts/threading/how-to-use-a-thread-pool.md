---
title: 'Porady: Korzystanie z puli wątków (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 90a0bb24-39f8-41f5-a217-b52a7d4fed0b
ms.openlocfilehash: a61defc2e40662d7fdadb40693e757fa559adb6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-thread-pool-visual-basic"></a>Porady: Korzystanie z puli wątków (Visual Basic)
*Pula wątków* jest formą wielowątkowości w zadania, które są dodawane do kolejki i uruchamiane automatycznie podczas tworzenia wątków. Aby uzyskać więcej informacji, zobacz [wątku puli (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md).  
  
 W poniższym przykładzie użyto puli wątków .NET Framework do obliczenia `Fibonacci` wynik dziesięć numerów od 20 do 40. Każdy `Fibonacci` wynik jest reprezentowana przez `Fibonacci` klasy, która udostępnia metodę o nazwie `ThreadPoolCallback` , która wykonuje obliczenie. Obiekt reprezentujący każdego `Fibonacci` wartość jest tworzony i `ThreadPoolCallback` metody jest przekazywany do <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, co powoduje przypisanie dostępnych wątków w puli, można wykonać metody.  
  
 Ponieważ każdy `Fibonacci` obiektu podano częściowo losowych wartości do obliczenia i ponieważ każdy wątek będzie konkurencyjnych czasu procesora, nie wiadomo, z wyprzedzeniem, jak długo trwa dla wszystkich dziesięć wyniki mają być obliczane. Dlatego każdy `Fibonacci` przekazanego wystąpienia obiektu <xref:System.Threading.ManualResetEvent> klasy podczas konstruowania. Obiekt podanego zdarzenia sygnalizuje każdego obiektu po jego zakończeniu obliczania, co pozwala na wykonanie bloku z podstawowym wątku <xref:System.Threading.WaitHandle.WaitAll%2A> do wszystkich dziesięciu `Fibonacci` obiektów obliczonych wynik. `Main` Metoda wyświetla każdy `Fibonacci` wynik.  
  
## <a name="example"></a>Przykład  
  
```vb  
Imports System.Threading  
  
Module Module1  
  
    Public Class Fibonacci  
        Private _n As Integer  
        Private _fibOfN  
        Private _doneEvent As ManualResetEvent  
  
        Public ReadOnly Property N() As Integer  
            Get  
                Return _n  
            End Get  
        End Property  
  
        Public ReadOnly Property FibOfN() As Integer  
            Get  
                Return _fibOfN  
            End Get  
        End Property  
  
        Sub New(ByVal n As Integer, ByVal doneEvent As ManualResetEvent)  
            _n = n  
            _doneEvent = doneEvent  
        End Sub  
  
        ' Wrapper method for use with the thread pool.  
        Public Sub ThreadPoolCallBack(ByVal threadContext As Object)  
            Dim threadIndex As Integer = CType(threadContext, Integer)  
            Console.WriteLine("thread {0} started...", threadIndex)  
            _fibOfN = Calculate(_n)  
            Console.WriteLine("thread {0} result calculated...", threadIndex)  
            _doneEvent.Set()  
        End Sub  
  
        Public Function Calculate(ByVal n As Integer) As Integer  
            If n <= 1 Then  
                Return n  
            End If  
            Return Calculate(n - 1) + Calculate(n - 2)  
        End Function  
  
    End Class  
  
    <MTAThread()>   
    Sub Main()  
        Const FibonacciCalculations As Integer = 9 ' 0 to 9  
  
        ' One event is used for each Fibonacci object  
        Dim doneEvents(FibonacciCalculations) As ManualResetEvent  
        Dim fibArray(FibonacciCalculations) As Fibonacci  
        Dim r As New Random()  
  
        ' Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations)  
  
        For i As Integer = 0 To FibonacciCalculations  
            doneEvents(i) = New ManualResetEvent(False)  
            Dim f = New Fibonacci(r.Next(20, 40), doneEvents(i))  
            fibArray(i) = f  
            ThreadPool.QueueUserWorkItem(AddressOf f.ThreadPoolCallBack, i)  
        Next  
  
        ' Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents)  
        Console.WriteLine("All calculations are complete.")  
  
        ' Display the results.  
        For i As Integer = 0 To FibonacciCalculations  
            Dim f As Fibonacci = fibArray(i)  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN)  
        Next  
    End Sub  
  
End Module  
```  
  
 Poniżej przedstawiono przykład danych wyjściowych.  
  
```  
launching 10 tasks...  
thread 0 started...  
thread 1 started...  
thread 1 result calculated...  
thread 2 started...  
thread 2 result calculated...  
thread 3 started...  
thread 3 result calculated...  
thread 4 started...  
thread 0 result calculated...  
thread 5 started...  
thread 5 result calculated...  
thread 6 started...  
thread 4 result calculated...  
thread 7 started...  
thread 6 result calculated...  
thread 8 started...  
thread 8 result calculated...  
thread 9 started...  
thread 9 result calculated...  
thread 7 result calculated...  
All calculations are complete.  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(25) = 75025  
Fibonacci(22) = 17711  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(29) = 514229  
Fibonacci(38) = 39088169  
Fibonacci(21) = 10946  
Fibonacci(27) = 196418  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [Wątku puli (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [Wątkowość (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [Zabezpieczenia](../../../../standard/security/index.md)
