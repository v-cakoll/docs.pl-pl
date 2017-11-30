---
title: "Wątku puli (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b89d261aa2d038926f8c7e1832436b0cd34019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="a12b1-102">Wątku puli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a12b1-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="a12b1-103">A *puli wątków* jest kolekcją wątków, które można wykonać kilka zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="a12b1-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="a12b1-104">(Zobacz [wątki (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) informacje uzupełniające.) Spowoduje to pozostawienie podstawowy wątek wolnego asynchronicznie wykonywanie innych zadań.</span><span class="sxs-lookup"><span data-stu-id="a12b1-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="a12b1-105">Pule wątków są często stosowanych w aplikacji serwera.</span><span class="sxs-lookup"><span data-stu-id="a12b1-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="a12b1-106">Każde żądanie przychodzące jest przypisany do wątku z puli wątków, aby żądania były przetwarzane asynchronicznie, bez zajmowania podstawowy wątku lub opóźnienia przetwarzanie kolejnych żądań.</span><span class="sxs-lookup"><span data-stu-id="a12b1-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="a12b1-107">Po zakończeniu działania zadań jego wątków w puli jest zwracany do kolejki wątków oczekujących, gdzie mogą być ponownie.</span><span class="sxs-lookup"><span data-stu-id="a12b1-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="a12b1-108">Ponownemu ten umożliwia aplikacjom uniknąć kosztów tworzenia nowego wątku dla każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="a12b1-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="a12b1-109">Pule wątków zwykle mają maksymalną liczbę wątków.</span><span class="sxs-lookup"><span data-stu-id="a12b1-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="a12b1-110">Jeśli wszystkie wątki są zajęte, dopóki nie może być obsługiwany jako wątków staną się dostępne dodatkowe zadania są umieszczane w kolejce.</span><span class="sxs-lookup"><span data-stu-id="a12b1-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="a12b1-111">Można zaimplementować pulę wątków, ale jest łatwiejsze w puli wątków dostarczane przez program .NET Framework za pomocą <xref:System.Threading.ThreadPool> klasy.</span><span class="sxs-lookup"><span data-stu-id="a12b1-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="a12b1-112">Z puli wątków, należy wywołać <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> metody z delegata w procedurze, który chcesz uruchomić i Visual Basic tworzy wątku i uruchamia procedury.</span><span class="sxs-lookup"><span data-stu-id="a12b1-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="a12b1-113">Przykład Pula wątków</span><span class="sxs-lookup"><span data-stu-id="a12b1-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="a12b1-114">Poniższy przykład przedstawia sposób korzystania z wątku puli można uruchomić kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="a12b1-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 <span data-ttu-id="a12b1-115">Jedną z zalet korzystanie z puli wątków jest, że można przekazywać argumenty w obiekcie stanu do procedury zadań.</span><span class="sxs-lookup"><span data-stu-id="a12b1-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="a12b1-116">Jeśli procedury to wywołanie wymaga więcej niż jeden argument, można rzutować strukturą lub wystąpienia klasy do `Object` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="a12b1-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="a12b1-117">Wątek puli parametrów i zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="a12b1-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="a12b1-118">Zwracanie wartości z wątku puli wątków nie jest proste.</span><span class="sxs-lookup"><span data-stu-id="a12b1-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="a12b1-119">Standardowy sposób zwracania wartości z wywołania funkcji jest niedozwolona, ponieważ `Sub` procedury są jedynym typem procedury, które mogą być umieszczone w kolejce do puli wątków.</span><span class="sxs-lookup"><span data-stu-id="a12b1-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="a12b1-120">Jednym ze sposobów można podać parametry i zwracać wartości jest zawijania parametrów zwracanych wartości i metody w otoce klasy zgodnie z opisem w [parametry i zwracać wartości dla procedur wielowątkowości (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a12b1-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="a12b1-121">Sposób easer Podaj parametry i wartości zwracane jest przy użyciu opcjonalnego `ByVal` zmiennej obiektu stanu z <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a12b1-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="a12b1-122">Jeśli używasz tej zmiennej do przekazania odwołania do wystąpienia klasy elementów członkowskich wystąpienia można modyfikować w wątku puli wątków i używane jako wartości zwracanych.</span><span class="sxs-lookup"><span data-stu-id="a12b1-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="a12b1-123">Na początku może nie być oczywista, modyfikowania obiektu odwołuje się do zmiennej, która jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="a12b1-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="a12b1-124">Można to zrobić, ponieważ tylko odwołanie do obiektu jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="a12b1-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="a12b1-125">Po wprowadzeniu zmian do elementów członkowskich obiektu odwołuje się odwołanie do obiektu zmiany dotyczą wystąpienie klasy rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="a12b1-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="a12b1-126">Struktury nie można zwrócić wartości wewnątrz obiekty stanu.</span><span class="sxs-lookup"><span data-stu-id="a12b1-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="a12b1-127">Ponieważ struktury są typy wartości, zmiany, które powoduje, że proces asynchroniczny nie należy zmieniać członkami oryginalnej struktury.</span><span class="sxs-lookup"><span data-stu-id="a12b1-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="a12b1-128">Użyj struktury, aby podać parametry zwracane wartości nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="a12b1-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a12b1-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a12b1-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="a12b1-130">Porady: Korzystanie z puli wątków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a12b1-130">How to: Use a Thread Pool (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="a12b1-131">Wątkowość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a12b1-131">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="a12b1-132">Aplikacje wielowątkowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a12b1-132">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="a12b1-133">Synchronizacja wątku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a12b1-133">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
