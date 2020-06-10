---
title: Zarządzana wątkowość — najlepsze rozwiązania
description: Uzyskaj informacje o zarządzanych wątkach najlepszych rozwiązań w programie .NET. Pracuj z trudnymi sytuacjami, takimi jak koordynowanie wielu wątków lub obsługa wątków blokujących.
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
ms.openlocfilehash: fa0af1461ba568583127316934b9d55577dd4c5a
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662826"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="a355e-104">Zarządzane wątki z najlepszymi rozwiązaniami</span><span class="sxs-lookup"><span data-stu-id="a355e-104">Managed threading best practices</span></span>
<span data-ttu-id="a355e-105">Wielowątkowość wymaga starannego programowania.</span><span class="sxs-lookup"><span data-stu-id="a355e-105">Multithreading requires careful programming.</span></span> <span data-ttu-id="a355e-106">W przypadku większości zadań można zmniejszyć złożoność przez kolejkowanie żądań na potrzeby wykonywania przez wątki puli wątków.</span><span class="sxs-lookup"><span data-stu-id="a355e-106">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="a355e-107">Ten temat dotyczy trudniejszych sytuacji, takich jak koordynacja pracy wielu wątków lub obsługa wątków, które blokują.</span><span class="sxs-lookup"><span data-stu-id="a355e-107">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a355e-108">Począwszy od .NET Framework 4, Biblioteka zadań równoległych i PLINQ zapewniają interfejsy API, które zmniejszają część złożoności i zagrożeń związanych z programowaniem wielowątkowym.</span><span class="sxs-lookup"><span data-stu-id="a355e-108">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="a355e-109">Aby uzyskać więcej informacji, zobacz [programowanie równoległe w programie .NET](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="a355e-109">For more information, see [Parallel Programming in .NET](../parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="a355e-110">Zakleszczenia i sytuacje wyścigu</span><span class="sxs-lookup"><span data-stu-id="a355e-110">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="a355e-111">Wielowątkowość rozwiązuje problemy dotyczące przepływności i czasu reakcji, ale w ten sposób wprowadza nowe problemy: zakleszczenie i sytuacje wyścigu.</span><span class="sxs-lookup"><span data-stu-id="a355e-111">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="a355e-112">Zakleszczenia</span><span class="sxs-lookup"><span data-stu-id="a355e-112">Deadlocks</span></span>  
 <span data-ttu-id="a355e-113">Zakleszczenie występuje, gdy każdy z dwóch wątków próbuje zablokować zasób, drugi został już zablokowany.</span><span class="sxs-lookup"><span data-stu-id="a355e-113">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="a355e-114">Żaden wątek nie może wykonywać żadnych dalszych postępów.</span><span class="sxs-lookup"><span data-stu-id="a355e-114">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="a355e-115">Wiele metod klas zarządzanych wątków zapewnia przekroczenia limitu czasu, aby pomóc w wykrywaniu zakleszczenii.</span><span class="sxs-lookup"><span data-stu-id="a355e-115">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="a355e-116">Na przykład poniższy kod próbuje uzyskać blokadę obiektu o nazwie `lockObject` .</span><span class="sxs-lookup"><span data-stu-id="a355e-116">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="a355e-117">Jeśli blokada nie zostanie uzyskana w 300 milisekundach, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> zwraca `false` .</span><span class="sxs-lookup"><span data-stu-id="a355e-117">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
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
  
### <a name="race-conditions"></a><span data-ttu-id="a355e-118">Warunki wyścigu</span><span class="sxs-lookup"><span data-stu-id="a355e-118">Race conditions</span></span>  
 <span data-ttu-id="a355e-119">Sytuacja wyścigu jest usterką, która występuje, gdy wynik programu zależy od tego, co dwa lub więcej wątków osiągną określony blok kodu jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="a355e-119">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="a355e-120">Uruchamianie programu wiele razy daje różne wyniki, a wynik danego uruchomienia nie może być przewidywany.</span><span class="sxs-lookup"><span data-stu-id="a355e-120">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="a355e-121">Prosty przykład warunku wyścigu powoduje zwiększenie pola.</span><span class="sxs-lookup"><span data-stu-id="a355e-121">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="a355e-122">Załóżmy, że Klasa ma prywatne pole **statyczne** (**udostępniane** w Visual Basic), które jest zwiększane za każdym razem, gdy tworzone jest wystąpienie klasy, przy użyciu kodu, takiego jak `objCt++;` (C#) lub `objCt += 1` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a355e-122">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="a355e-123">Ta operacja wymaga załadowania wartości z `objCt` do rejestru, zwiększenia wartości i zapisania jej w `objCt` .</span><span class="sxs-lookup"><span data-stu-id="a355e-123">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="a355e-124">W aplikacji wielowątkowej wątek, który został załadowany i zwiększony wartość może zostać przeniesiona przez inny wątek, który wykonuje wszystkie trzy kroki; gdy pierwszy wątek wznawia wykonywanie i przechowuje jego wartość, zastępuje bez uwzględniania `objCt` faktu, że wartość została zmieniona w tymczasowym.</span><span class="sxs-lookup"><span data-stu-id="a355e-124">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="a355e-125">Ten konkretny warunek wyścigu można łatwo uniknąć przy użyciu metod <xref:System.Threading.Interlocked> klasy, takich jak <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a355e-125">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a355e-126">Aby zapoznać się z innymi technikami synchronizowania danych między wieloma wątkami, zobacz [synchronizowanie danych w celu wielowątkowości](synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="a355e-126">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="a355e-127">Sytuacje wyścigu mogą również wystąpić podczas synchronizowania działań wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="a355e-127">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="a355e-128">Za każdym razem, gdy piszesz wiersz kodu, należy wziąć pod uwagę to, co może się zdarzyć, jeśli wątek został przemieszczony przed wykonaniem wiersza (lub przed dowolnym z instrukcji poszczególnych maszyn, które składają się na linię), a inny wątek przejdzie do niego.</span><span class="sxs-lookup"><span data-stu-id="a355e-128">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="a355e-129">Statyczne elementy członkowskie i konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="a355e-129">Static members and static constructors</span></span>  
 <span data-ttu-id="a355e-130">Klasa nie została zainicjowana do momentu zakończenia działania konstruktora klasy ( `static` Konstruktor w języku C# w `Shared Sub New` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a355e-130">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="a355e-131">Aby zapobiec wykonywaniu kodu w typie, który nie został zainicjowany, środowisko uruchomieniowe języka wspólnego blokuje wszystkie wywołania z innych wątków do `static` elementów członkowskich klasy ( `Shared` elementy członkowskie w Visual Basic) do momentu zakończenia działania konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="a355e-131">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="a355e-132">Na przykład jeśli Konstruktor klasy uruchamia nowy wątek, a procedura wątku wywołuje `static` element członkowski klasy, nowy wątek jest blokowany do momentu ukończenia konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="a355e-132">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="a355e-133">Dotyczy to dowolnego typu, który może mieć `static` Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a355e-133">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="a355e-134">Liczba procesorów</span><span class="sxs-lookup"><span data-stu-id="a355e-134">Number of processors</span></span>

<span data-ttu-id="a355e-135">Bez względu na to, czy istnieje wiele procesorów, czy tylko jeden procesor dostępny w systemie może mieć wpływ na architekturę wielowątkową.</span><span class="sxs-lookup"><span data-stu-id="a355e-135">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="a355e-136">Aby uzyskać więcej informacji, zobacz [Liczba procesorów](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="a355e-136">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="a355e-137">Użyj <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> właściwości, aby określić liczbę procesorów dostępnych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a355e-137">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at run time.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="a355e-138">Ogólne zalecenia</span><span class="sxs-lookup"><span data-stu-id="a355e-138">General recommendations</span></span>  
 <span data-ttu-id="a355e-139">Podczas korzystania z wielu wątków należy wziąć pod uwagę następujące wytyczne:</span><span class="sxs-lookup"><span data-stu-id="a355e-139">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="a355e-140">Nie używaj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do kończenia innych wątków.</span><span class="sxs-lookup"><span data-stu-id="a355e-140">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="a355e-141">Wywołanie metody **Abort** w innym wątku jest zbliżone, aby zgłaszać wyjątek w tym wątku, bez znajomości tego, który punkt został osiągnięty w jego przetwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="a355e-141">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="a355e-142">Nie używaj <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> synchronizowania działań wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="a355e-142">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="a355e-143">Użyj <xref:System.Threading.Mutex> , <xref:System.Threading.ManualResetEvent> , <xref:System.Threading.AutoResetEvent> , i <xref:System.Threading.Monitor> .</span><span class="sxs-lookup"><span data-stu-id="a355e-143">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="a355e-144">Nie Kontroluj wykonywania wątków roboczych z głównego programu (na przykład przy użyciu zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="a355e-144">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="a355e-145">Zamiast tego Zaprojektuj program tak, aby wątki robocze były odpowiedzialne za oczekiwanie na dostępność, wykonanie tej operacji i powiadomienie innych części programu po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="a355e-145">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="a355e-146">Jeśli wątki robocze nie są blokowane, należy rozważyć użycie wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="a355e-146">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="a355e-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>jest przydatny w sytuacjach, w których działa blok wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="a355e-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="a355e-148">Nie używaj typów jako obiektów blokady.</span><span class="sxs-lookup"><span data-stu-id="a355e-148">Don't use types as lock objects.</span></span> <span data-ttu-id="a355e-149">Oznacza to, że należy unikać kodu, takiego jak `lock(typeof(X))` C# lub `SyncLock(GetType(X))` w Visual Basic, lub używania <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> z <xref:System.Type> obiektami.</span><span class="sxs-lookup"><span data-stu-id="a355e-149">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="a355e-150">Dla danego typu istnieje tylko jedno wystąpienie dla <xref:System.Type?displayProperty=nameWithType> każdej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a355e-150">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="a355e-151">Jeśli typ, w którym jest wykonywane zablokowanie, jest publiczny, kod inny niż własny może być na nim zablokowany, prowadząc do zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="a355e-151">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="a355e-152">Aby uzyskać dodatkowe problemy, zobacz [najlepsze rozwiązania dotyczące niezawodności](../../framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="a355e-152">For additional issues, see [Reliability Best Practices](../../framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="a355e-153">Należy zachować ostrożność podczas blokowania wystąpień, na przykład `lock(this)` w języku C# lub `SyncLock(Me)` w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a355e-153">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="a355e-154">Jeśli inny kod w aplikacji, zewnętrzny dla tego typu, przyjmuje blokadę obiektu, mogą wystąpić zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="a355e-154">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="a355e-155">Upewnij się, że wątek, który został wprowadzony do monitora, zawsze opuszcza ten monitor, nawet jeśli wystąpi wyjątek, gdy wątek jest w monitorze.</span><span class="sxs-lookup"><span data-stu-id="a355e-155">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="a355e-156">Instrukcja [Lock](../../csharp/language-reference/keywords/lock-statement.md) języka C# i instrukcja Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) umożliwiają automatyczne udostępnienie tego zachowania, przy użyciu bloku **finally** , aby upewnić się, że <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a355e-156">The C# [lock](../../csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="a355e-157">Jeśli nie można zagwarantować, że **wyjście** zostanie wywołane, Rozważ zmianę projektu w celu użycia **muteksu**.</span><span class="sxs-lookup"><span data-stu-id="a355e-157">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="a355e-158">Element mutex jest automatycznie wydawany, gdy wątek, który jest aktualnie do przerwania.</span><span class="sxs-lookup"><span data-stu-id="a355e-158">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="a355e-159">Używaj wielu wątków dla zadań, które wymagają różnych zasobów i nie należy przypisywać wielu wątków do pojedynczego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a355e-159">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="a355e-160">Na przykład każde zadanie związane z korzyściami we/wy z posiadania własnego wątku, ponieważ ten wątek zostanie zablokowany podczas operacji we/wy i w ten sposób zezwala na wykonywanie innych wątków.</span><span class="sxs-lookup"><span data-stu-id="a355e-160">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="a355e-161">Dane wejściowe użytkownika to inne zasoby, które są korzyści z dedykowanego wątku.</span><span class="sxs-lookup"><span data-stu-id="a355e-161">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="a355e-162">Na komputerze z jednym procesorem zadanie, które obejmuje intensywne obliczenia, zawiera dane wejściowe użytkownika i zadania, które obejmują operacje we/wy, ale wiele zadań intensywnie korzystających z obliczeń będą konkurować o ze sobą.</span><span class="sxs-lookup"><span data-stu-id="a355e-162">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="a355e-163">Rozważ użycie metod <xref:System.Threading.Interlocked> klasy dla prostych zmian stanu, zamiast używać `lock` instrukcji ( `SyncLock` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a355e-163">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="a355e-164">`lock`Instrukcja jest dobrym narzędziem ogólnego przeznaczenia, ale <xref:System.Threading.Interlocked> Klasa zapewnia lepszą wydajność dla aktualizacji, które muszą być niepodzielne.</span><span class="sxs-lookup"><span data-stu-id="a355e-164">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="a355e-165">Wewnętrznie wykonuje pojedynczy prefiks blokady w przypadku braku rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="a355e-165">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="a355e-166">W przeglądach kodu Obejrzyj kod podobny do przedstawionego w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="a355e-166">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="a355e-167">W pierwszym przykładzie zmienna stanu jest zwiększana:</span><span class="sxs-lookup"><span data-stu-id="a355e-167">In the first example, a state variable is incremented:</span></span>  
  
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
  
     <span data-ttu-id="a355e-168">Można zwiększyć wydajność przy użyciu <xref:System.Threading.Interlocked.Increment%2A> metody zamiast `lock` instrukcji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a355e-168">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="a355e-169">W .NET Framework 2,0 i nowszych Użyj <xref:System.Threading.Interlocked.Add%2A> metody dla przyrostów niepodzielnych większych niż 1.</span><span class="sxs-lookup"><span data-stu-id="a355e-169">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="a355e-170">W drugim przykładzie zmienna typu odwołania jest aktualizowana tylko wtedy, gdy jest to odwołanie o wartości null ( `Nothing` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a355e-170">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
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
  
     <span data-ttu-id="a355e-171">Wydajność można ulepszyć za pomocą <xref:System.Threading.Interlocked.CompareExchange%2A> metody zamiast tego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a355e-171">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="a355e-172">Począwszy od .NET Framework 2,0, <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> Przeciążenie metody zapewnia bezpieczną alternatywę typu dla typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="a355e-172">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="a355e-173">Zalecenia dotyczące bibliotek klas</span><span class="sxs-lookup"><span data-stu-id="a355e-173">Recommendations for class libraries</span></span>  
 <span data-ttu-id="a355e-174">Podczas projektowania bibliotek klas dla wielowątkowości należy wziąć pod uwagę następujące wytyczne:</span><span class="sxs-lookup"><span data-stu-id="a355e-174">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="a355e-175">Należy unikać synchronizacji, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a355e-175">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="a355e-176">Jest to szczególnie prawdziwe w przypadku silnie używanego kodu.</span><span class="sxs-lookup"><span data-stu-id="a355e-176">This is especially true for heavily used code.</span></span> <span data-ttu-id="a355e-177">Na przykład algorytm może zostać dostosowany do tolerowania warunku wyścigu zamiast go wyeliminować.</span><span class="sxs-lookup"><span data-stu-id="a355e-177">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="a355e-178">Niepotrzebna synchronizacja zmniejsza wydajność i tworzy możliwość zakleszczenia i warunków wyścigu.</span><span class="sxs-lookup"><span data-stu-id="a355e-178">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="a355e-179">Domyślnie Udostępnij statyczne dane ( `Shared` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a355e-179">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="a355e-180">Nie wykonuj domyślnego wątku danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a355e-180">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="a355e-181">Dodanie blokad do tworzenia kodu bezpiecznego wątków zmniejsza wydajność, zwiększa rywalizację o blokady i tworzy możliwość wystąpienia zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="a355e-181">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="a355e-182">W przypadku wspólnych modeli aplikacji tylko jeden wątek w danym momencie wykonuje kod użytkownika, co minimalizuje konieczność zapewnienia bezpieczeństwa wątków.</span><span class="sxs-lookup"><span data-stu-id="a355e-182">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="a355e-183">Z tego powodu biblioteki klas .NET Framework nie są bezpieczne wątkowo.</span><span class="sxs-lookup"><span data-stu-id="a355e-183">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="a355e-184">Unikaj udostępniania metod statycznych, które zmieniają stan statyczny.</span><span class="sxs-lookup"><span data-stu-id="a355e-184">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="a355e-185">W typowych scenariuszach serwera stan statyczny jest współużytkowany między żądaniami, co oznacza, że wiele wątków może wykonać ten kod w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="a355e-185">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="a355e-186">Spowoduje to otwarcie możliwości występowania błędów wątków.</span><span class="sxs-lookup"><span data-stu-id="a355e-186">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="a355e-187">Rozważ użycie wzorca projektowego, który hermetyzuje dane w wystąpieniach, które nie są współużytkowane przez żądania.</span><span class="sxs-lookup"><span data-stu-id="a355e-187">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="a355e-188">Ponadto jeśli dane statyczne są synchronizowane, wywołania między metodami statycznymi, które zmieniają stan, mogą spowodować zakleszczenia lub nadmiarowa synchronizacja, niekorzystnie wpływając na wydajność.</span><span class="sxs-lookup"><span data-stu-id="a355e-188">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a355e-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a355e-189">See also</span></span>

- [<span data-ttu-id="a355e-190">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="a355e-190">Threading</span></span>](index.md)
- [<span data-ttu-id="a355e-191">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="a355e-191">Threads and Threading</span></span>](threads-and-threading.md)
