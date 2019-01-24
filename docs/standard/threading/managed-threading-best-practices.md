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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 907e85d2622ea07ddbb61092f439583ed72e0c50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560038"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="f14cf-102">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f14cf-102">Managed threading best practices</span></span>
<span data-ttu-id="f14cf-103">Wielowątkowość wymaga starannego programowania.</span><span class="sxs-lookup"><span data-stu-id="f14cf-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="f14cf-104">W przypadku większości zadań mogą zmniejszyć złożoność przez kolejkowanie żądania do wykonania, wątków z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="f14cf-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="f14cf-105">Ten temat dotyczy trudniejsze sytuacjach, takich jak koordynowanie pracy wielu wątków i obsługi wątki tego bloku.</span><span class="sxs-lookup"><span data-stu-id="f14cf-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f14cf-106">Począwszy od programu .NET Framework 4 w bibliotece równoległych zadań i PLINQ zapewniają interfejsy API, zmniejszyć niektóre złożoność i ryzyko programowanie wielowątkowe.</span><span class="sxs-lookup"><span data-stu-id="f14cf-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="f14cf-107">Aby uzyskać więcej informacji, zobacz [programowania równoległego w .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="f14cf-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="f14cf-108">Zakleszczeń i sytuacje wyścigu</span><span class="sxs-lookup"><span data-stu-id="f14cf-108">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="f14cf-109">Wielowątkowość rozwiązuje problemy z przepływności i czasu odpowiedzi, ale w ten sposób wprowadza nowe problemy: zakleszczeń i sytuacje wyścigu.</span><span class="sxs-lookup"><span data-stu-id="f14cf-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="f14cf-110">Zakleszczenia</span><span class="sxs-lookup"><span data-stu-id="f14cf-110">Deadlocks</span></span>  
 <span data-ttu-id="f14cf-111">Zakleszczenie występuje, gdy każda z dwoma wątkami próbuje zablokować zasobu, do którego innych został już zablokowany.</span><span class="sxs-lookup"><span data-stu-id="f14cf-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="f14cf-112">Żadna wątku można wprowadzać żadnych dalszych postępów.</span><span class="sxs-lookup"><span data-stu-id="f14cf-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="f14cf-113">Wiele metod klas wątków zarządzanych zapewniają limity czasu, aby ułatwić wykrywanie zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="f14cf-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="f14cf-114">Na przykład, poniższy kod próbuje uzyskać blokadę obiektu o nazwie `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="f14cf-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="f14cf-115">Jeśli blokada nie zostanie uzyskana w milisekundach 300 <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="f14cf-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
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
  
### <a name="race-conditions"></a><span data-ttu-id="f14cf-116">Warunki wyścigu</span><span class="sxs-lookup"><span data-stu-id="f14cf-116">Race conditions</span></span>  
 <span data-ttu-id="f14cf-117">Sytuacja wyścigu jest błąd, który występuje, gdy wynikiem programu zależy od określonego bloku kodu, którym dwa lub więcej wątków osiągnie najpierw.</span><span class="sxs-lookup"><span data-stu-id="f14cf-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="f14cf-118">Uruchamianie programu wiele razy daje różne wyniki, a wynik dowolnym danym przebiegiem nie można przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="f14cf-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="f14cf-119">Prosty przykład sytuacja wyścigu jest zwiększenie pola.</span><span class="sxs-lookup"><span data-stu-id="f14cf-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="f14cf-120">Załóżmy, że klasa ma prywatnej **statyczne** pola (**Shared** w języku Visual Basic), jest zwiększana za każdym razem, gdy tworzone jest wystąpienie klasy, takie jak przy użyciu kodu `objCt++;` (C#) lub `objCt += 1` ( Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f14cf-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="f14cf-121">Ta operacja wymaga ładowania wartość `objCt` do rejestru, zwiększenie wartości i zapisuje ją w `objCt`.</span><span class="sxs-lookup"><span data-stu-id="f14cf-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="f14cf-122">W aplikacji wielowątkowych wątek, który został załadowany i zwiększana wartość może być wywłaszczony przez inny wątek, który wykonuje wszystkie trzy kroki; Po pierwszym wątkiem wznawia wykonanie i przechowuje wartość, zastępuje `objCt` nie biorąc pod uwagę fakt, że wartość została zmieniona w międzyczasie.</span><span class="sxs-lookup"><span data-stu-id="f14cf-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="f14cf-123">Sytuacja wyścigu określonego unika się łatwo za pomocą metody <xref:System.Threading.Interlocked> klasy, takie jak <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f14cf-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f14cf-124">Aby przeczytać o innych technik do synchronizowania danych między wieloma wątkami, zobacz [synchronizowanie danych dla wielowątkowość](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="f14cf-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="f14cf-125">Warunki wyścigu może również wystąpić podczas synchronizowania działania wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="f14cf-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="f14cf-126">Zawsze, gdy pisania choćby wiersza kodu, należy rozważyć, co może się zdarzyć, jeśli wątek były przerywane, przed wykonaniem wiersza (lub przed każdą instrukcji poszczególnych maszyn, które składają się na wiersz), a inny wątek podbili go.</span><span class="sxs-lookup"><span data-stu-id="f14cf-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="f14cf-127">Statyczne elementy członkowskie i konstruktorów statycznych</span><span class="sxs-lookup"><span data-stu-id="f14cf-127">Static members and static constructors</span></span>  
 <span data-ttu-id="f14cf-128">Klasa nie został zainicjowany aż do jej konstruktora klasy (`static` konstruktora w języku C# `Shared Sub New` w języku Visual Basic) zakończył działanie.</span><span class="sxs-lookup"><span data-stu-id="f14cf-128">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="f14cf-129">Aby uniemożliwić wykonywanie kodu na typie, który nie został zainicjowany, środowisko uruchomieniowe języka wspólnego blokuje wszystkie połączenia z innych wątków do `static` elementów członkowskich klasy (`Shared` elementów członkowskich w języku Visual Basic) do momentu zakończenia uruchamiania konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="f14cf-129">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="f14cf-130">Na przykład, jeśli Konstruktor klasy rozpoczynają nowy wątek, a następnie wywołuje procedury wątku `static` składowej klasy nowe bloki wątku do chwili zakończenia konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="f14cf-130">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="f14cf-131">Dotyczy to dowolnego typu, który może mieć `static` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f14cf-131">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="f14cf-132">Liczba procesorów</span><span class="sxs-lookup"><span data-stu-id="f14cf-132">Number of processors</span></span>

<span data-ttu-id="f14cf-133">Czy istnieją tylko jeden procesor lub kilka procesorów dostępnych w systemie może mieć wpływ na architekturę wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="f14cf-133">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="f14cf-134">Aby uzyskać więcej informacji, zobacz [liczba procesorów](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="f14cf-134">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="f14cf-135">Użyj <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> właściwości, aby określić liczbę procesorów dostępnych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f14cf-135">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at runtime.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="f14cf-136">Ogólne zalecenia</span><span class="sxs-lookup"><span data-stu-id="f14cf-136">General recommendations</span></span>  
 <span data-ttu-id="f14cf-137">Korzystając z wielu wątków, należy wziąć pod uwagę następujące wytyczne:</span><span class="sxs-lookup"><span data-stu-id="f14cf-137">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="f14cf-138">Nie używaj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zakończyć inne wątki.</span><span class="sxs-lookup"><span data-stu-id="f14cf-138">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="f14cf-139">Wywoływanie **przerwać** na inny wątek jest podobnie zostanie zgłoszony wyjątek w że wątku, nie wiedząc o tym, co punkt wątek osiągnęła w zakresie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f14cf-139">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="f14cf-140">Nie używaj <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> do synchronizowania działania wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="f14cf-140">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="f14cf-141">Należy używać <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, i <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="f14cf-141">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="f14cf-142">Nie kontrolować wykonywanie wątków roboczych programu głównego (na przykład przy użyciu zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="f14cf-142">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="f14cf-143">Zamiast tego można zaprojektować program, tak, aby wątków roboczych jest odpowiedzialny za na zakończenie pracy jest dostępna, jej wykonanie i powiadamiania innych części programu, po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f14cf-143">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="f14cf-144">Jeśli nie blokują wątki procesu roboczego, rozważ użycie wątków z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="f14cf-144">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="f14cf-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> jest przydatne w sytuacjach, w którym pracownik wątki bloku.</span><span class="sxs-lookup"><span data-stu-id="f14cf-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="f14cf-146">Nie należy używać typów jako obiekty blokady.</span><span class="sxs-lookup"><span data-stu-id="f14cf-146">Don't use types as lock objects.</span></span> <span data-ttu-id="f14cf-147">Oznacza to, takich jak Unikaj kodu `lock(typeof(X))` w języku C# lub `SyncLock(GetType(X))` w Visual Basic lub użytkowania <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> z <xref:System.Type> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f14cf-147">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="f14cf-148">Dla danego typu, jest tylko jedno wystąpienie <xref:System.Type?displayProperty=nameWithType> dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f14cf-148">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="f14cf-149">W przypadku publicznego typu, który stosuje blokadę na kod inny niż własny może blokad, co prowadzi do zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="f14cf-149">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="f14cf-150">Aby uzyskać dodatkowe problemy, zobacz [najlepsze rozwiązania dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="f14cf-150">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="f14cf-151">Należy zachować ostrożność podczas blokowania w wystąpieniach, na przykład `lock(this)` w języku C# lub `SyncLock(Me)` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f14cf-151">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="f14cf-152">Jeśli inny kod w aplikacji, zewnętrzne w stosunku do typu, przyjmuje blokadę na obiekcie, może wystąpić zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="f14cf-152">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="f14cf-153">Upewnij się, że wątku, która została wprowadzona przez monitor zawsze pozostawia tego monitora, nawet jeśli wystąpi wyjątek, gdy wątek jest w monitorze.</span><span class="sxs-lookup"><span data-stu-id="f14cf-153">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="f14cf-154">C# [blokady](~/docs/csharp/language-reference/keywords/lock-statement.md) instrukcji i Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrukcji zapewnia to zachowanie automatycznie, wykorzystujące **na koniec** bloku, aby upewnić się, że <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f14cf-154">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="f14cf-155">Jeśli nie można zapewnić, że **zakończenia** zostanie wywołana, rozważ zmianę projektu do użycia **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="f14cf-155">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="f14cf-156">Mutex automatycznie jest zwalniany, gdy kończy się wątek, który aktualnie jest właścicielem.</span><span class="sxs-lookup"><span data-stu-id="f14cf-156">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="f14cf-157">Użyj wielu wątków dla zadań, które wymagają różnych zasobów i należy unikać przypisywania wiele wątków do pojedynczego zasobu.</span><span class="sxs-lookup"><span data-stu-id="f14cf-157">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="f14cf-158">Na przykład wszystkie zadania dotyczące operacji We/Wy korzyści płynące z konieczności jego własnym wątku, ponieważ wątek będzie blokować podczas operacji We/Wy i Zezwalaj na tym samym innych wątków do wykonania.</span><span class="sxs-lookup"><span data-stu-id="f14cf-158">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="f14cf-159">Dane wejściowe użytkownika jest inny zasób, który korzysta z dedykowanego wątku.</span><span class="sxs-lookup"><span data-stu-id="f14cf-159">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="f14cf-160">Na komputerze jednoprocesorowym zadań, która obejmuje intensywnie korzystających z obliczeń będą współistnieć z danych wejściowych użytkownika i zadania, które obejmują operacje We/Wy, ale wiele zadań intensywnie korzystających z obliczeń zmagać się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="f14cf-160">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="f14cf-161">Należy wziąć pod uwagę przy użyciu metod <xref:System.Threading.Interlocked> klasy dla zmiany stanu prosty, zamiast `lock` — instrukcja (`SyncLock` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f14cf-161">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="f14cf-162">`lock` Instrukcja jest dobrym narzędziem ogólnego przeznaczenia, ale <xref:System.Threading.Interlocked> klasy zapewnia lepszą wydajność dla aktualizacji, które muszą być niepodzielna.</span><span class="sxs-lookup"><span data-stu-id="f14cf-162">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="f14cf-163">Wewnętrznie wykonuje prefiks pojedynczego blokadę, jeśli nie występuje rywalizacja.</span><span class="sxs-lookup"><span data-stu-id="f14cf-163">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="f14cf-164">W przeglądach kodu Obserwuj kod, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="f14cf-164">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="f14cf-165">W pierwszym przykładzie jest zwiększany zmiennej stanu:</span><span class="sxs-lookup"><span data-stu-id="f14cf-165">In the first example, a state variable is incremented:</span></span>  
  
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
  
     <span data-ttu-id="f14cf-166">Możesz poprawić wydajność przy użyciu <xref:System.Threading.Interlocked.Increment%2A> zamiast metody `lock` instrukcji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f14cf-166">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="f14cf-167">W programie .NET Framework 2.0 i nowszych, należy użyć <xref:System.Threading.Interlocked.Add%2A> metodę atomic przyrosty większy niż 1.</span><span class="sxs-lookup"><span data-stu-id="f14cf-167">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="f14cf-168">W drugim przykładzie zmienna typu odwołania jest aktualizowany tylko wtedy, gdy jest odwołanie o wartości null (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f14cf-168">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
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
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="f14cf-169">Można poprawić wydajność przy użyciu <xref:System.Threading.Interlocked.CompareExchange%2A> metody zamiast tego, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f14cf-169">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="f14cf-170">Począwszy od programu .NET Framework 2.0, <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> przeciążenie metody zawiera alternatywne bezpieczny dla typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="f14cf-170">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="f14cf-171">Zalecenia dotyczące bibliotek klas</span><span class="sxs-lookup"><span data-stu-id="f14cf-171">Recommendations for class libraries</span></span>  
 <span data-ttu-id="f14cf-172">Należy wziąć pod uwagę następujące wskazówki podczas projektowania bibliotek klas dla wielowątkowości:</span><span class="sxs-lookup"><span data-stu-id="f14cf-172">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="f14cf-173">Uniknięcia synchronizacji, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="f14cf-173">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="f14cf-174">Jest to szczególnie istotne dla intensywnie używanych kodu.</span><span class="sxs-lookup"><span data-stu-id="f14cf-174">This is especially true for heavily used code.</span></span> <span data-ttu-id="f14cf-175">Na przykład algorytm może dostosować tolerować wyścigu, a nie jej wyeliminowania.</span><span class="sxs-lookup"><span data-stu-id="f14cf-175">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="f14cf-176">Synchronizacja niepotrzebne zmniejsza wydajność i tworzy możliwości zakleszczeń i sytuacje wyścigu.</span><span class="sxs-lookup"><span data-stu-id="f14cf-176">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="f14cf-177">Przechowuj dane statyczne (`Shared` w języku Visual Basic) zapewnia bezpieczeństwa wątkowego domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f14cf-177">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="f14cf-178">Nie należy wprowadzać wątku danych wystąpienia bezpieczne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f14cf-178">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="f14cf-179">Dodawanie blokady, aby utworzyć kod wątkowo zmniejsza wydajność, zwiększa Rywalizacja o blokady i tworzy możliwości zakleszczenia wystąpić.</span><span class="sxs-lookup"><span data-stu-id="f14cf-179">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="f14cf-180">W typowych modeli aplikacji tylko jeden wątek jednocześnie wykonuje kod użytkownika, co minimalizuje potrzebę bezpieczeństwo wątkowe.</span><span class="sxs-lookup"><span data-stu-id="f14cf-180">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="f14cf-181">Z tego powodu biblioteki klas .NET Framework nie są wątkowo bezpieczne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f14cf-181">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="f14cf-182">Należy unikać, zapewniając metody statyczne, które zmienia stan statyczne.</span><span class="sxs-lookup"><span data-stu-id="f14cf-182">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="f14cf-183">W typowych scenariuszach serwera stanu statycznego jest współużytkowane przez wiele żądań, co oznacza, że wiele wątków można wykonać ten kod w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="f14cf-183">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="f14cf-184">Spowoduje to otwarcie możliwości wątkowości usterek.</span><span class="sxs-lookup"><span data-stu-id="f14cf-184">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="f14cf-185">Należy wziąć pod uwagę przy użyciu wzorca projektowego, który hermetyzuje danych do wystąpienia, które nie są współużytkowane przez wiele żądań.</span><span class="sxs-lookup"><span data-stu-id="f14cf-185">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="f14cf-186">Ponadto jeśli dane statyczne są synchronizowane, wywołań między metody statyczne, które zmienia stan może spowodować zakleszczenia lub nadmiarowe synchronizacji negatywnego wpływu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="f14cf-186">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f14cf-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f14cf-187">See also</span></span>

- [<span data-ttu-id="f14cf-188">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="f14cf-188">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="f14cf-189">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="f14cf-189">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
