---
title: 'Porady: Korzystanie z puli wątków (C#)'
ms.date: 07/20/2015
ms.assetid: 210a9235-83a6-420b-af52-2d6a58e5133f
ms.openlocfilehash: c89093bcff82715482b2ddb822916cfa5ff8ed72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-thread-pool-c"></a>Porady: Korzystanie z puli wątków (C#)
*Pula wątków* jest formą wielowątkowości w zadania, które są dodawane do kolejki i uruchamiane automatycznie podczas tworzenia wątków. Aby uzyskać więcej informacji, zobacz [puli wątków (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md).  
  
 W poniższym przykładzie użyto puli wątków .NET Framework do obliczenia `Fibonacci` wynik dziesięć numerów od 20 do 40. Każdy `Fibonacci` wynik jest reprezentowana przez `Fibonacci` klasy, która udostępnia metodę o nazwie `ThreadPoolCallback` , która wykonuje obliczenie. Obiekt reprezentujący każdego `Fibonacci` wartość jest tworzony i `ThreadPoolCallback` metody jest przekazywany do <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, co powoduje przypisanie dostępnych wątków w puli, można wykonać metody.  
  
 Ponieważ każdy `Fibonacci` obiektu podano częściowo losowych wartości do obliczenia i ponieważ każdy wątek będzie konkurencyjnych czasu procesora, nie wiadomo, z wyprzedzeniem, jak długo trwa dla wszystkich dziesięć wyniki mają być obliczane. Dlatego każdy `Fibonacci` przekazanego wystąpienia obiektu <xref:System.Threading.ManualResetEvent> klasy podczas konstruowania. Obiekt podanego zdarzenia sygnalizuje każdego obiektu po jego zakończeniu obliczania, co pozwala na wykonanie bloku z podstawowym wątku <xref:System.Threading.WaitHandle.WaitAll%2A> do wszystkich dziesięciu `Fibonacci` obiektów obliczonych wynik. `Main` Metoda wyświetla każdy `Fibonacci` wynik.  
  
## <a name="example"></a>Przykład  
  
```csharp  
using System;  
using System.Threading;  
  
public class Fibonacci  
{  
    private int _n;  
    private int _fibOfN;  
    private ManualResetEvent _doneEvent;  
  
    public int N { get { return _n; } }  
    public int FibOfN { get { return _fibOfN; } }  
  
    // Constructor.  
    public Fibonacci(int n, ManualResetEvent doneEvent)  
    {  
        _n = n;  
        _doneEvent = doneEvent;  
    }  
  
    // Wrapper method for use with thread pool.  
    public void ThreadPoolCallback(Object threadContext)  
    {  
        int threadIndex = (int)threadContext;  
        Console.WriteLine("thread {0} started...", threadIndex);  
        _fibOfN = Calculate(_n);  
        Console.WriteLine("thread {0} result calculated...", threadIndex);  
        _doneEvent.Set();  
    }  
  
    // Recursive method that calculates the Nth Fibonacci number.  
    public int Calculate(int n)  
    {  
        if (n <= 1)  
        {  
            return n;  
        }  
  
        return Calculate(n - 1) + Calculate(n - 2);  
    }  
}  
  
public class ThreadPoolExample  
{  
    static void Main()  
    {  
        const int FibonacciCalculations = 10;  
  
        // One event is used for each Fibonacci object.  
        ManualResetEvent[] doneEvents = new ManualResetEvent[FibonacciCalculations];  
        Fibonacci[] fibArray = new Fibonacci[FibonacciCalculations];  
        Random r = new Random();  
  
        // Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations);  
        for (int i = 0; i < FibonacciCalculations; i++)  
        {  
            doneEvents[i] = new ManualResetEvent(false);  
            Fibonacci f = new Fibonacci(r.Next(20, 40), doneEvents[i]);  
            fibArray[i] = f;  
            ThreadPool.QueueUserWorkItem(f.ThreadPoolCallback, i);  
        }  
  
        // Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents);  
        Console.WriteLine("All calculations are complete.");  
  
        // Display the results.  
        for (int i= 0; i<FibonacciCalculations; i++)  
        {  
            Fibonacci f = fibArray[i];  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN);  
        }  
    }  
}  
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
 [Wątku puli (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [Wątkowość (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Zabezpieczenia](../../../../standard/security/index.md)
