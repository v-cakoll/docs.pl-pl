---
title: Parametry i wartości zwracane dla procedur wielowątkowości (C#)
ms.date: 07/20/2015
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
ms.openlocfilehash: e27f8e67ff03260e1d13fa633064efc2059e6bdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340219"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>Parametry i wartości zwracane dla procedur wielowątkowości (C#)
Dostarczania i wartości zwracane w aplikacji wielowątkowych jest skomplikowane, ponieważ Konstruktor w klasie wątku muszą być przekazywane odwołanie do procedury, która nie przyjmuje żadnych argumentów i nie zwraca żadnej wartości. W poniższych sekcjach przedstawiono kilka prostych sposobów Podaj parametry i zwrócić wartości z procedury w oddzielnych wątkach.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Podając parametrami dla procedur wielowątkowości  
 Najlepszy sposób, aby podać parametry w celu wywołania metody wielowątkowe jest zawijany docelowej metody w klasie i definiowanie pól dla tej klasy, która będzie służyć jako parametry dla nowego wątku. Zaletą tej metody jest, możesz utworzyć nowe wystąpienie klasy, z własnego parametrów, za każdym razem, gdy ma się rozpocząć nowego wątku. Załóżmy na przykład funkcji, która oblicza obszaru trójkąt, zgodnie z poniższym kodem:  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 Można napisać klasę, która opakowuje `CalcArea` funkcji i tworzy pola do przechowywania parametrów wejściowych, w następujący sposób:  
  
```csharp  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 Aby użyć `AreaClass`, można utworzyć `AreaClass` obiektu i ustawić `Base` i `Height` właściwości, jak pokazano w poniższym kodzie:  
  
```csharp  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 Zwróć uwagę, że `TestArea` procedury nie sprawdza wartość `Area` pole po wywołaniu `CalcArea` metody. Ponieważ `CalcArea` jest uruchamiana w oddzielnym wątku `Area` pola nie jest gwarantowana można ustawić, jeśli zaznaczysz natychmiast po wywołaniu `Thread.Start`. W następnej sekcji omówiono lepszy sposób, aby zwrócić wartości z procedur wielowątkowości.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Zwracanie wartości z procedur wielowątkowości  
 Zwracanie wartości z procedury, które są uruchamiane w oddzielnych wątkach jest złożona faktem, że procedury nie może być funkcji i nie można użyć `ByRef` argumentów. Najprostszym sposobem, aby zwrócić wartości jest użycie <xref:System.ComponentModel.BackgroundWorker> składnik do zarządzania z wątków i wywołaj zdarzenie po zakończeniu zadania i przetworzyć wyników z obsługi zdarzeń.  
  
 Poniższy przykład zwraca wartość przez wywołanie zdarzenia z systemem w oddzielnym wątku procedury:  
  
```csharp  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 Można podać parametry i wartości zwracane wątków z puli wątków przy użyciu opcjonalnego `ByVal` zmiennej obiektu stanu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody. Wątek czasomierza wątków obsługują także obiekt stanu w tym celu. Aby uzyskać informacje na korzystanie z puli wątków i czasomierze wątków, zobacz [korzystanie z puli wątków (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) i [czasomierze wątków (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Wątku puli (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [Synchronizacja wątku (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [Zdarzenia](../../../../csharp/programming-guide/events/index.md)  
 [Aplikacje wielowątkowe (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegaci](../../../../csharp/programming-guide/delegates/index.md)  
 [Wielowątkowość składników](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
