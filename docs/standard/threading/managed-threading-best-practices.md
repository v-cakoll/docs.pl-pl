---
title: Zarządzana wątkowość — najlepsze rozwiązania
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
ms.openlocfilehash: a76cc40f308ac2f636a650cd4a17da0e94e23a34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160264"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="71827-102">Najlepsze rozwiązania dotyczące wątków zarządzanych</span><span class="sxs-lookup"><span data-stu-id="71827-102">Managed threading best practices</span></span>
<span data-ttu-id="71827-103">Wielowątkowość wymaga starannego programowania.</span><span class="sxs-lookup"><span data-stu-id="71827-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="71827-104">W przypadku większości zadań można zmniejszyć złożoność, kolejkując żądania do wykonania przez wątki puli wątków.</span><span class="sxs-lookup"><span data-stu-id="71827-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="71827-105">Ten temat dotyczy trudniejszych sytuacji, takich jak koordynowanie pracy wielu wątków lub obsługa wątków, które blokują.</span><span class="sxs-lookup"><span data-stu-id="71827-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71827-106">Począwszy od .NET Framework 4, biblioteka równoległa zadań i PLINQ zapewniają interfejsy API, które zmniejszają złożoność i ryzyko programowania wielowątkowego.</span><span class="sxs-lookup"><span data-stu-id="71827-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="71827-107">Aby uzyskać więcej informacji, zobacz [Programowanie równoległe w programie .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="71827-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="71827-108">Zakleszczenia i warunki wyścigu</span><span class="sxs-lookup"><span data-stu-id="71827-108">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="71827-109">Wielowątkowość rozwiązuje problemy z przepustowością i reakcją, ale w ten sposób wprowadza nowe problemy: zakleszczenia i warunki wyścigu.</span><span class="sxs-lookup"><span data-stu-id="71827-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="71827-110">Zakleszczenia</span><span class="sxs-lookup"><span data-stu-id="71827-110">Deadlocks</span></span>  
 <span data-ttu-id="71827-111">Zakleszczenie występuje, gdy każdy z dwóch wątków próbuje zablokować zasób inny już zablokowany.</span><span class="sxs-lookup"><span data-stu-id="71827-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="71827-112">Żaden wątek nie może poczynić dalszych postępów.</span><span class="sxs-lookup"><span data-stu-id="71827-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="71827-113">Wiele metod zarządzanych klas wątków zapewniają uchybienia czasu, aby ułatwić wykrywanie zakleszczeń.</span><span class="sxs-lookup"><span data-stu-id="71827-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="71827-114">Na przykład poniższy kod próbuje uzyskać blokadę `lockObject`na obiekcie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="71827-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="71827-115">Jeśli blokada nie zostanie uzyskana w <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> ciągu `false`300 milisekund, zwraca wartość .</span><span class="sxs-lookup"><span data-stu-id="71827-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="71827-116">Warunki wyścigu</span><span class="sxs-lookup"><span data-stu-id="71827-116">Race conditions</span></span>  
 <span data-ttu-id="71827-117">Stan wyścigu jest błąd, który występuje, gdy wynik programu zależy od tego, który z dwóch lub więcej wątków osiągnie określonego bloku kodu pierwszy.</span><span class="sxs-lookup"><span data-stu-id="71827-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="71827-118">Uruchamianie programu wiele razy daje różne wyniki, a wynik danego przebiegu nie może być przewidywany.</span><span class="sxs-lookup"><span data-stu-id="71827-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="71827-119">Prostym przykładem stanu wyścigu jest zwiększanie pola.</span><span class="sxs-lookup"><span data-stu-id="71827-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="71827-120">Załóżmy, że klasa ma prywatne pole **statyczne** **(Udostępnione** w języku Visual Basic), które jest zwiększane za każdym razem, gdy tworzone jest wystąpienie klasy, przy użyciu kodu, takiego jak `objCt++;` (C#) lub `objCt += 1` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="71827-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="71827-121">Ta operacja wymaga załadowania wartości z `objCt` do rejestru, zwiększania wartości i `objCt`przechowywania jej w pliku .</span><span class="sxs-lookup"><span data-stu-id="71827-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="71827-122">W aplikacji wielowątkowej wątku wątku, który został załadowany i zwiększa wartość może być wywłaszczony przez inny wątek, który wykonuje wszystkie trzy kroki; gdy pierwszy wątek wznawia wykonywanie i `objCt` przechowuje jego wartość, zastępuje bez uwzględnienia faktu, że wartość została zmieniona w międzyczasie.</span><span class="sxs-lookup"><span data-stu-id="71827-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="71827-123">Ten szczególny stan wyścigu można łatwo uniknąć <xref:System.Threading.Interlocked> za pomocą <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>metod klasy, takich jak .</span><span class="sxs-lookup"><span data-stu-id="71827-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="71827-124">Aby przeczytać o innych technikach synchronizowania danych między wieloma wątkami, zobacz [Synchronizowanie danych dla wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="71827-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="71827-125">Warunki wyścigu mogą również wystąpić podczas synchronizowania działań wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="71827-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="71827-126">Za każdym razem, gdy piszesz wiersz kodu, należy wziąć pod uwagę, co może się zdarzyć, jeśli wątek zostały wywłaszczone przed wykonaniem wiersza (lub przed którymkolwiek z instrukcji poszczególnych maszyn, które tworzą wiersz), a inny wątek wyprzedził go.</span><span class="sxs-lookup"><span data-stu-id="71827-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="71827-127">Statyczne elementy członkowskie i konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="71827-127">Static members and static constructors</span></span>  
 <span data-ttu-id="71827-128">Klasa nie jest inicjowane, dopóki`static` jego konstruktor `Shared Sub New` klasy (konstruktor w języku C#, w języku Visual Basic) został zakończony uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="71827-128">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="71827-129">Aby zapobiec wykonywaniu kodu na typ, który nie jest inicjowany, czas wykonywania języka wspólnego blokuje wszystkie wywołania z innych wątków do `static` elementów członkowskich klasy (elementy`Shared` członkowskie w języku Visual Basic), dopóki konstruktor klasy nie zakończy się uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="71827-129">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="71827-130">Na przykład jeśli konstruktor klasy uruchamia nowy wątek, `static` a procedura wątku wywołuje element członkowski klasy, nowe bloki wątku, dopóki konstruktor klasy nie zostanie ukończony.</span><span class="sxs-lookup"><span data-stu-id="71827-130">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="71827-131">Dotyczy to dowolnego typu, który `static` może mieć konstruktora.</span><span class="sxs-lookup"><span data-stu-id="71827-131">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="71827-132">Liczba przetwórców</span><span class="sxs-lookup"><span data-stu-id="71827-132">Number of processors</span></span>

<span data-ttu-id="71827-133">To, czy w systemie jest dostępnych wiele procesorów, czy tylko jeden procesor, może mieć wpływ na architekturę wielowątkową.</span><span class="sxs-lookup"><span data-stu-id="71827-133">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="71827-134">Aby uzyskać więcej informacji, zobacz [Liczba procesorów](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="71827-134">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="71827-135">Użyj <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> właściwości, aby określić liczbę procesorów dostępnych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71827-135">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at runtime.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="71827-136">Zalecenia ogólne</span><span class="sxs-lookup"><span data-stu-id="71827-136">General recommendations</span></span>  
 <span data-ttu-id="71827-137">Podczas korzystania z wielu wątków należy wziąć pod uwagę następujące wskazówki:</span><span class="sxs-lookup"><span data-stu-id="71827-137">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="71827-138">Nie należy <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> używać do zakończenia innych wątków.</span><span class="sxs-lookup"><span data-stu-id="71827-138">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="71827-139">Wywołanie **Abort** w innym wątku jest podobne do zgłaszania wyjątku w tym wątku, nie wiedząc, jaki punkt, który wątek osiągnął w jego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="71827-139">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="71827-140">Nie należy <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> używać <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> i synchronizować działania wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="71827-140">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="71827-141">Czy <xref:System.Threading.Mutex>używać <xref:System.Threading.ManualResetEvent> <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.Monitor>, i .</span><span class="sxs-lookup"><span data-stu-id="71827-141">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="71827-142">Nie należy kontrolować wykonywanie wątków roboczych z głównego programu (przy użyciu zdarzeń, na przykład).</span><span class="sxs-lookup"><span data-stu-id="71827-142">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="71827-143">Zamiast tego zaprojektuj program tak, aby wątki robocze były odpowiedzialne za oczekiwanie, aż praca będzie dostępna, wykonanie go i powiadomienie innych części programu po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="71827-143">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="71827-144">Jeśli wątki robocze nie blokują, należy rozważyć użycie wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="71827-144">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="71827-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>jest przydatne w sytuacjach, gdy blok wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="71827-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="71827-146">Nie należy używać typów jako obiektów blokady.</span><span class="sxs-lookup"><span data-stu-id="71827-146">Don't use types as lock objects.</span></span> <span data-ttu-id="71827-147">Oznacza to, że `lock(typeof(X))` należy unikać `SyncLock(GetType(X))` kodu, takich jak w <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Type> języku C# lub w języku Visual Basic lub użycia z obiektami.</span><span class="sxs-lookup"><span data-stu-id="71827-147">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="71827-148">Dla danego typu istnieje tylko jedno <xref:System.Type?displayProperty=nameWithType> wystąpienie na domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71827-148">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="71827-149">Jeśli typ wziąć blokady jest publiczny, kod inny niż własne może podjąć blokady na nim, co prowadzi do zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="71827-149">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="71827-150">Aby uzyskać dodatkowe problemy, zobacz [Najważniejsze wskazówki dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="71827-150">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="71827-151">Należy zachować ostrożność podczas blokowania `lock(this)` wystąpień, `SyncLock(Me)` na przykład w języku C# lub w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="71827-151">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="71827-152">Jeśli inny kod w aplikacji, zewnętrznego do typu, ma blokady na obiekcie, może wystąpić zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="71827-152">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="71827-153">Upewnij się, że wątek, który wszedł monitor zawsze pozostawia tego monitora, nawet jeśli wystąpi wyjątek, gdy wątek znajduje się na monitorze.</span><span class="sxs-lookup"><span data-stu-id="71827-153">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="71827-154">C# [lock](../../csharp/language-reference/keywords/lock-statement.md) instrukcji i Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji zapewniają to **finally** zachowanie automatycznie, <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> wykorzystując finally bloku, aby upewnić się, że jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="71827-154">The C# [lock](../../csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="71827-155">Jeśli nie możesz upewnić się, że **exit** zostanie wywołany, rozważ zmianę projektu na **mutex**.</span><span class="sxs-lookup"><span data-stu-id="71827-155">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="71827-156">Mutex jest automatycznie zwalniany, gdy wątek, który jest obecnie właścicielem kończy.</span><span class="sxs-lookup"><span data-stu-id="71827-156">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="71827-157">Należy używać wielu wątków dla zadań, które wymagają różnych zasobów i uniknąć przypisywania wielu wątków do jednego zasobu.</span><span class="sxs-lookup"><span data-stu-id="71827-157">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="71827-158">Na przykład każde zadanie obejmujące we/wy korzyści z posiadania własnego wątku, ponieważ ten wątek będzie blokować podczas operacji we/wy, a tym samym zezwolić na wykonywanie innych wątków.</span><span class="sxs-lookup"><span data-stu-id="71827-158">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="71827-159">Dane wejściowe użytkownika to inny zasób, który korzysta z dedykowanego wątku.</span><span class="sxs-lookup"><span data-stu-id="71827-159">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="71827-160">Na komputerze z jednym procesorem zadanie, które obejmuje intensywne obliczenia współistnieje z danymi wejściowymi użytkownika i zadaniami, które obejmują we/wy, ale wiele zadań intensywnie korzystających z obliczeń walczy ze sobą.</span><span class="sxs-lookup"><span data-stu-id="71827-160">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="71827-161">Należy rozważyć użycie <xref:System.Threading.Interlocked> metod klasy dla prostych zmian `lock` stanu, zamiast używać instrukcji (w`SyncLock` języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="71827-161">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="71827-162">Instrukcja `lock` jest dobrym narzędziem ogólnego <xref:System.Threading.Interlocked> przeznaczenia, ale klasa zapewnia lepszą wydajność dla aktualizacji, które muszą być atomowej.</span><span class="sxs-lookup"><span data-stu-id="71827-162">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="71827-163">Wewnętrznie wykonuje prefiks pojedynczej blokady, jeśli nie ma żadnych rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="71827-163">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="71827-164">W przeglądzie kodu uważaj na kod podobny do tego, który został pokazany w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="71827-164">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="71827-165">W pierwszym przykładzie zmienna stanu jest zwiększana:</span><span class="sxs-lookup"><span data-stu-id="71827-165">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="71827-166">Można zwiększyć wydajność <xref:System.Threading.Interlocked.Increment%2A> przy użyciu `lock` metody zamiast instrukcji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="71827-166">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="71827-167">W .NET Framework 2.0 i <xref:System.Threading.Interlocked.Add%2A> nowszych użyj metody przyrostów niepodzielnych większych niż 1.</span><span class="sxs-lookup"><span data-stu-id="71827-167">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="71827-168">W drugim przykładzie zmienna typu odwołania jest aktualizowana tylko`Nothing` wtedy, gdy jest to odwołanie zerowe (w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="71827-168">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            x ??= y;
        }  
    }  
    ```  
  
     <span data-ttu-id="71827-169">Wydajność można poprawić za <xref:System.Threading.Interlocked.CompareExchange%2A> pomocą metody zamiast, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="71827-169">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="71827-170">Począwszy od .NET Framework <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> 2.0 przeciążenie metody zapewnia alternatywę dla typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="71827-170">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="71827-171">Zalecenia dotyczące bibliotek klas</span><span class="sxs-lookup"><span data-stu-id="71827-171">Recommendations for class libraries</span></span>  
 <span data-ttu-id="71827-172">Podczas projektowania bibliotek klas do wielowątkowości należy wziąć pod uwagę następujące wskazówki:</span><span class="sxs-lookup"><span data-stu-id="71827-172">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="71827-173">Unikaj konieczności synchronizacji, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="71827-173">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="71827-174">Jest to szczególnie ważne dla kodu intensywnie używane.</span><span class="sxs-lookup"><span data-stu-id="71827-174">This is especially true for heavily used code.</span></span> <span data-ttu-id="71827-175">Na przykład algorytm może być dostosowane do tolerowania stanu wyścigu, a nie go wyeliminować.</span><span class="sxs-lookup"><span data-stu-id="71827-175">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="71827-176">Niepotrzebna synchronizacja zmniejsza wydajność i stwarza możliwość zakleszczenia i warunków wyścigu.</span><span class="sxs-lookup"><span data-stu-id="71827-176">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="71827-177">Ustaw domyślnie`Shared` wątek danych statycznych (w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="71827-177">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="71827-178">Nie należy domyślnie zabezpieczać wątku danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="71827-178">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="71827-179">Dodawanie blokad do tworzenia kodu bezpiecznego dla wątków zmniejsza wydajność, zwiększa rywalizację blokad i tworzy możliwość wystąpienia zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="71827-179">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="71827-180">W typowych modelach aplikacji tylko jeden wątek naraz wykonuje kod użytkownika, co minimalizuje potrzebę bezpieczeństwa wątków.</span><span class="sxs-lookup"><span data-stu-id="71827-180">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="71827-181">Z tego powodu biblioteki klas .NET Framework nie są domyślnie bezpieczne dla wątków.</span><span class="sxs-lookup"><span data-stu-id="71827-181">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="71827-182">Należy unikać podawania metod statycznych, które zmieniają stan statyczny.</span><span class="sxs-lookup"><span data-stu-id="71827-182">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="71827-183">W typowych scenariuszach serwera stan statyczny jest współużytkowany przez żądania, co oznacza, że wiele wątków może wykonać ten kod w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="71827-183">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="71827-184">Otwiera to możliwość wątków błędów.</span><span class="sxs-lookup"><span data-stu-id="71827-184">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="71827-185">Należy wziąć pod uwagę przy użyciu wzorca projektu, który hermetyzuje dane w wystąpieniach, które nie są współużytkowane przez żądania.</span><span class="sxs-lookup"><span data-stu-id="71827-185">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="71827-186">Ponadto jeśli dane statyczne są synchronizowane, wywołania między metodami statycznymi, które zmieniają stan może spowodować zakleszczenia lub nadmiarowej synchronizacji, niekorzystnie wpływając na wydajność.</span><span class="sxs-lookup"><span data-stu-id="71827-186">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71827-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71827-187">See also</span></span>

- [<span data-ttu-id="71827-188">Wątków</span><span class="sxs-lookup"><span data-stu-id="71827-188">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="71827-189">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="71827-189">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
