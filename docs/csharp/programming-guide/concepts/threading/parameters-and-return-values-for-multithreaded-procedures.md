---
title: Parametry i wartości zwracane dla procedur wielowątkowości (C#)
ms.date: 07/20/2015
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
ms.openlocfilehash: 218e297d192d37d55ff391045342262d7bf66a0c
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875134"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a><span data-ttu-id="9fc19-102">Parametry i wartości zwracane dla procedur wielowątkowości (C#)</span><span class="sxs-lookup"><span data-stu-id="9fc19-102">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>
<span data-ttu-id="9fc19-103">Dostarczanie i zwracanie wartości w aplikacji wielowątkowych jest skomplikowane, ponieważ Konstruktor klasy wątku muszą zostać przekazane odwołanie do procedury, która nie przyjmuje żadnych argumentów i nie zwraca żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="9fc19-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="9fc19-104">W poniższych sekcjach opisano niektóre upraszczają podać parametry i zwracane wartości z procedury w oddzielnych wątkach.</span><span class="sxs-lookup"><span data-stu-id="9fc19-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="9fc19-105">Podając parametry dla procedur wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="9fc19-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="9fc19-106">Najlepszym sposobem podać parametry w celu wywołania metody wielowątkowe jest zawijany do metody docelowej w klasie i definiowania pól dla tej klasy, która będzie służyć jako parametry dla nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="9fc19-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="9fc19-107">Zaletą tego podejścia jest, że można utworzyć nowe wystąpienie klasy, z własną parametrami za każdym razem, gdy chcesz rozpocząć nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="9fc19-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="9fc19-108">Na przykład załóżmy, że funkcja obliczający pole trójkąt, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="9fc19-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 <span data-ttu-id="9fc19-109">Można napisać klasę, która otacza `CalcArea` działać, a następnie tworzy pola do przechowywania parametrów wejściowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9fc19-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
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
  
 <span data-ttu-id="9fc19-110">Aby użyć `AreaClass`, możesz utworzyć `AreaClass` obiektu, a następnie ustaw `Base` i `Height` właściwości, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="9fc19-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
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
  
 <span data-ttu-id="9fc19-111">Należy zauważyć, że `TestArea` procedury nie sprawdza wartość `Area` pola po wywołaniu `CalcArea` metody.</span><span class="sxs-lookup"><span data-stu-id="9fc19-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="9fc19-112">Ponieważ `CalcArea` działa w oddzielnym wątku `Area` pole nie jest gwarantowana można ustawić, jeśli zaznaczysz natychmiast po wywołaniu `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="9fc19-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="9fc19-113">W następnej sekcji omówiono lepszy sposób, aby zwrócić wartości z procedur wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="9fc19-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="9fc19-114">Zwracanie wartości z procedur wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="9fc19-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="9fc19-115">Zwracanie wartości z procedury, które są uruchamiane w oddzielnych wątkach jest skomplikowane faktem, że procedury nie może być funkcji i nie można użyć `ByRef` argumentów.</span><span class="sxs-lookup"><span data-stu-id="9fc19-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="9fc19-116">Najprostszym sposobem, aby zwrócić wartości jest użycie <xref:System.ComponentModel.BackgroundWorker> składnik do zarządzania wątki i wywołać zdarzenie, gdy zadanie jest wykonywane i przetworzyć wyniki za pomocą programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9fc19-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="9fc19-117">Poniższy przykład zwraca wartość przez podnoszenie zdarzenia z procedury uruchomione w oddzielnym wątku:</span><span class="sxs-lookup"><span data-stu-id="9fc19-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
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
  
 <span data-ttu-id="9fc19-118">Można podać parametry i zwracane wartości dla wątków w puli wątków przy użyciu opcjonalnego `ByVal` zmiennej obiektu stanu <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9fc19-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="9fc19-119">Wątków czasomierza wątku obsługują także obiekt stanu, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="9fc19-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="9fc19-120">Aby uzyskać informacje na korzystanie z puli wątków i czasomierze wątków, zobacz [korzystanie z puli wątków (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) i [czasomierzy](../../../../standard/threading/timers.md).</span><span class="sxs-lookup"><span data-stu-id="9fc19-120">For information on thread pooling and thread timers, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) and [Timers](../../../../standard/threading/timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc19-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fc19-121">See Also</span></span>  
 [<span data-ttu-id="9fc19-122">Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (C#)</span><span class="sxs-lookup"><span data-stu-id="9fc19-122">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="9fc19-123">Wątek puli (C#)</span><span class="sxs-lookup"><span data-stu-id="9fc19-123">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="9fc19-124">Synchronizacja wątku (C#)</span><span class="sxs-lookup"><span data-stu-id="9fc19-124">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="9fc19-125">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="9fc19-125">Events</span></span>](../../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="9fc19-126">Aplikacje wielowątkowe (C#)</span><span class="sxs-lookup"><span data-stu-id="9fc19-126">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="9fc19-127">Delegaci</span><span class="sxs-lookup"><span data-stu-id="9fc19-127">Delegates</span></span>](../../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="9fc19-128">Wielowątkowość w składnikach</span><span class="sxs-lookup"><span data-stu-id="9fc19-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
