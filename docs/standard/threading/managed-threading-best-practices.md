---
title: Zarządzana wątkowość — najlepsze rozwiązania
ms.date: 11/30/2017
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
ms.openlocfilehash: 15261291f40b6a41e0d6033fb92e1b23b4042019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="fde86-102">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fde86-102">Managed Threading Best Practices</span></span>
<span data-ttu-id="fde86-103">Wielowątkowość wymaga zachować ostrożność podczas programowania.</span><span class="sxs-lookup"><span data-stu-id="fde86-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="fde86-104">W przypadku większości zadań można zmniejszyć złożoność kolejkowania wiadomości żądania do wykonania przez wątków z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="fde86-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="fde86-105">Ten temat dotyczy sytuacji trudniej, takich jak koordynowanie pracy wiele wątków, lub obsługa wątki tego bloku.</span><span class="sxs-lookup"><span data-stu-id="fde86-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fde86-106">Począwszy od programu .NET Framework 4, w bibliotece równoległych zadań i PLINQ Podaj interfejsów API, które zmniejszyć niektóre złożoność i ryzyko programów wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="fde86-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="fde86-107">Aby uzyskać więcej informacji, zobacz [Programowanie równoległe w .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="fde86-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="fde86-108">Zakleszczenie i sytuacja wyścigu</span><span class="sxs-lookup"><span data-stu-id="fde86-108">Deadlocks and Race Conditions</span></span>  
 <span data-ttu-id="fde86-109">Wielowątkowość rozwiązuje problemy z przepływność i elastyczność, jednak w ten sposób wprowadza nowe problemy: zakleszczenie i sytuacja wyścigu.</span><span class="sxs-lookup"><span data-stu-id="fde86-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="fde86-110">Zakleszczenie</span><span class="sxs-lookup"><span data-stu-id="fde86-110">Deadlocks</span></span>  
 <span data-ttu-id="fde86-111">Zakleszczenie występuje, gdy każdy z dwoma wątkami próbuje zablokować zasobu, do którego innych został już zablokowany.</span><span class="sxs-lookup"><span data-stu-id="fde86-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="fde86-112">Wątek nie może poczyniła żadnego postępu dalsze.</span><span class="sxs-lookup"><span data-stu-id="fde86-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="fde86-113">Wiele metod klasy wątkowości zarządzane Podaj limity czasu, co ułatwia wykrywanie zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="fde86-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="fde86-114">Na przykład następujący kod próbuje uzyskać blokady obiektu o nazwie `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="fde86-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="fde86-115">Jeżeli nie uzyskano blokady w milisekundach 300 <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="fde86-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
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
  
### <a name="race-conditions"></a><span data-ttu-id="fde86-116">Warunki wyścigu</span><span class="sxs-lookup"><span data-stu-id="fde86-116">Race Conditions</span></span>  
 <span data-ttu-id="fde86-117">Sytuacja wyścigu jest usterkę, która występuje, gdy wynik programu zależy od tego, który dwa lub więcej wątków najpierw osiągnie bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="fde86-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="fde86-118">Program działa wiele razy daje różne wyniki, a nie można przewidzieć wynik dowolnym danym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="fde86-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="fde86-119">Prosty przykład sytuacja wyścigu jest zwiększenie pola.</span><span class="sxs-lookup"><span data-stu-id="fde86-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="fde86-120">Załóżmy, że klasa ma prywatnej **statycznych** pola (**Shared** w języku Visual Basic) który jest zwiększany za każdym razem, gdy tworzone jest wystąpienie klasy, takich jak przy użyciu kodu `objCt++;` (C#) lub `objCt += 1` () Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="fde86-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="fde86-121">Ta operacja wymaga ładowania wartość `objCt` w rejestrze, zwiększając wartość, a następnie zapisanie jej w `objCt`.</span><span class="sxs-lookup"><span data-stu-id="fde86-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="fde86-122">W aplikacji wielowątkowych wątku, który został załadowany i zwiększana wartość może być wywłaszczony przez inny wątek, który wykonuje wszystkie trzy kroki; Po pierwszym wątkiem wznawia wykonywania i przechowuje wartość, zastępuje on `objCt` bez biorąc pod uwagę fakt, że wartość została zmieniona w tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="fde86-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="fde86-123">Łatwo uniknąć sytuacja wyścigu określonego za pomocą metody <xref:System.Threading.Interlocked> klas, takich jak <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fde86-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fde86-124">Aby uzyskać informacje dotyczące innych technik synchronizowania danych między wiele wątków, zobacz [synchronizowanie danych Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="fde86-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="fde86-125">Warunki wyścigu może również wystąpić podczas synchronizowania działania wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="fde86-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="fde86-126">Zawsze, gdy zapisywania wiersza kodu, należy rozważyć co może się zdarzyć, jeśli wątek zostały wywłaszczone przed wykonaniem wiersza (lub przed każdą instrukcji poszczególnych maszyn, które składają się na wiersz), a inny wątek podbili go.</span><span class="sxs-lookup"><span data-stu-id="fde86-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="number-of-processors"></a><span data-ttu-id="fde86-127">Liczba procesorów</span><span class="sxs-lookup"><span data-stu-id="fde86-127">Number of Processors</span></span>  
 <span data-ttu-id="fde86-128">Większość komputerów już wielu procesorów (nazywanych również rdzenie) nawet małych urządzeń, takich jak tablety i telefony.</span><span class="sxs-lookup"><span data-stu-id="fde86-128">Most computers now have multiple processors (also called cores), even small devices such as tablets and phones.</span></span> <span data-ttu-id="fde86-129">Jeśli wiesz, że projektujesz oprogramowania, które zostanie też uruchomiony na komputerach z jednym procesorem, należy zwrócić uwagę że wielowątkowość rozwiązuje różne problemy dla komputerów z jednym procesorem i komputerach wieloprocesorowych.</span><span class="sxs-lookup"><span data-stu-id="fde86-129">If you know you're developing software that will also run on single-processor computers, you should be aware that multithreading solves different problems for single-processor computers and multiprocessor computers.</span></span>  
  
### <a name="multiprocessor-computers"></a><span data-ttu-id="fde86-130">Komputerach wieloprocesorowych</span><span class="sxs-lookup"><span data-stu-id="fde86-130">Multiprocessor Computers</span></span>  
 <span data-ttu-id="fde86-131">Wielowątkowość zapewnia większą przepływność.</span><span class="sxs-lookup"><span data-stu-id="fde86-131">Multithreading provides greater throughput.</span></span> <span data-ttu-id="fde86-132">Dziesięć procesorów możliwość dziesięciokrotnie pracy jednego, ale tylko jeśli praca odbywa się tak, aby wszystkie dziesięciu mogą działać jednocześnie; wątki umożliwiają łatwe do dzielenia pracy i wykorzystać dodatkowej mocy obliczeniowej.</span><span class="sxs-lookup"><span data-stu-id="fde86-132">Ten processors can do ten times the work of one, but only if the work is divided so that all ten can be working at once; threads provide an easy way to divide the work and exploit the extra processing power.</span></span> <span data-ttu-id="fde86-133">Jeśli używasz wielowątkowości w komputerach wieloprocesorowych:</span><span class="sxs-lookup"><span data-stu-id="fde86-133">If you use multithreading on a multiprocessor computer:</span></span>  
  
-   <span data-ttu-id="fde86-134">Liczba wątków, które mogą być wykonywane jednocześnie jest ograniczona przez liczbę procesorów.</span><span class="sxs-lookup"><span data-stu-id="fde86-134">The number of threads that can execute concurrently is limited by the number of processors.</span></span>  
  
-   <span data-ttu-id="fde86-135">Wątku w tle jest wykonywana tylko wtedy, gdy liczba wątków pierwszego planu wykonania jest mniejszy niż liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="fde86-135">A background thread executes only when the number of foreground threads executing is smaller than the number of processors.</span></span>  
  
-   <span data-ttu-id="fde86-136">Podczas wywoływania <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metody w wątku, wątek może lub nie może rozpocząć wykonywania, w zależności od liczby procesorów i liczbę wątków oczekujących na wykonanie.</span><span class="sxs-lookup"><span data-stu-id="fde86-136">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread might or might not start executing immediately, depending on the number of processors and the number of threads currently waiting to execute.</span></span>  
  
-   <span data-ttu-id="fde86-137">Warunki wyścigu może być spowodowany nie tylko wątki są zastępowane nieoczekiwanie, ale ponieważ dwa wątki wykonywanych na różnych procesorów może racing do tego samego bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="fde86-137">Race conditions can occur not only because threads are preempted unexpectedly, but because two threads executing on different processors might be racing to reach the same code block.</span></span>  
  
### <a name="single-processor-computers"></a><span data-ttu-id="fde86-138">Komputery z jednym procesorem</span><span class="sxs-lookup"><span data-stu-id="fde86-138">Single-Processor Computers</span></span>  
 <span data-ttu-id="fde86-139">Wielowątkowość zapewnia większą elastyczność użytkowników komputera, a używa czas bezczynności dla zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="fde86-139">Multithreading provides greater responsiveness to the computer user, and uses idle time for background tasks.</span></span> <span data-ttu-id="fde86-140">Jeśli używasz wielowątkowość na komputerze z jednym procesorem:</span><span class="sxs-lookup"><span data-stu-id="fde86-140">If you use multithreading on a single-processor computer:</span></span>  
  
-   <span data-ttu-id="fde86-141">Tylko jeden wątek działa w każdej chwili.</span><span class="sxs-lookup"><span data-stu-id="fde86-141">Only one thread runs at any instant.</span></span>  
  
-   <span data-ttu-id="fde86-142">Wątku w tle jest wykonywana tylko wtedy, gdy jest bezczynny wątek użytkownika głównego.</span><span class="sxs-lookup"><span data-stu-id="fde86-142">A background thread executes only when the main user thread is idle.</span></span> <span data-ttu-id="fde86-143">Wątek pierwszego planu, który wykonuje stale starves wątki w tle czasu procesora.</span><span class="sxs-lookup"><span data-stu-id="fde86-143">A foreground thread that executes constantly starves background threads of processor time.</span></span>  
  
-   <span data-ttu-id="fde86-144">Podczas wywoływania <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metody w wątku, że wątek nie rozpocznie się wykonywanie do bieżącego wątku daje lub są zastępowane przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="fde86-144">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread does not start executing until the current thread yields or is preempted by the operating system.</span></span>  
  
-   <span data-ttu-id="fde86-145">Warunki wyścigu zwykle występuje, ponieważ programistę nie jest przewidywane fakt, że wątku może być wywłaszczony chwili nieodpowiednich czasami stosowanie inny wątek nawiązać blok kodu.</span><span class="sxs-lookup"><span data-stu-id="fde86-145">Race conditions typically occur because the programmer did not anticipate the fact that a thread can be preempted at an awkward moment, sometimes allowing another thread to reach a code block first.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="fde86-146">Statyczne elementy członkowskie i konstruktorów statycznych</span><span class="sxs-lookup"><span data-stu-id="fde86-146">Static Members and Static Constructors</span></span>  
 <span data-ttu-id="fde86-147">Nie zainicjowano klasy do jego konstruktora klasy (`static` konstruktora w języku C# `Shared Sub New` w języku Visual Basic) zakończył działanie.</span><span class="sxs-lookup"><span data-stu-id="fde86-147">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="fde86-148">Aby zapobiec wykonywanie kodu na typ, który nie został zainicjowany, środowisko uruchomieniowe języka wspólnego blokuje wywołania z innych wątków `static` elementy członkowskie klasy (`Shared` elementów członkowskich w języku Visual Basic) do momentu konstruktora klasy zakończył działanie.</span><span class="sxs-lookup"><span data-stu-id="fde86-148">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="fde86-149">Na przykład, jeśli konstruktora klasy rozpoczyna się nowego wątku i wywołuje procedurę wątku `static` elementu członkowskiego klasy nowych bloków wątku do momentu ukończenia konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="fde86-149">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="fde86-150">Dotyczy to dowolnego typu, który może mieć `static` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fde86-150">This applies to any type that can have a `static` constructor.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="fde86-151">Ogólne zalecenia</span><span class="sxs-lookup"><span data-stu-id="fde86-151">General Recommendations</span></span>  
 <span data-ttu-id="fde86-152">Korzystając z wielu wątków, należy wziąć pod uwagę następujące wytyczne:</span><span class="sxs-lookup"><span data-stu-id="fde86-152">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="fde86-153">Nie używaj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zakończyć inne wątki.</span><span class="sxs-lookup"><span data-stu-id="fde86-153">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="fde86-154">Wywoływanie **przerwać** w innym wątku jest podobnie Zgłaszanie wyjątku wątku, bez wiedzy o co punktu wątek ma osiągnięcie w jego przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="fde86-154">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="fde86-155">Nie używaj <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> do synchronizowania działania wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="fde86-155">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="fde86-156">Należy używać <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, i <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="fde86-156">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="fde86-157">Nie mają wpływu na wykonywanie wątków roboczych z programu głównego (na przykład za pomocą zdarzeń,).</span><span class="sxs-lookup"><span data-stu-id="fde86-157">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="fde86-158">Zamiast tego projektu programu tak, aby wątków roboczych są odpowiedzialne za czekając na zakończenie pracy jest dostępna, jej wykonanie i powiadamiania innych części program po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="fde86-158">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="fde86-159">Jeśli Twoje wątków roboczych nie blokują, rozważ użycie wątków z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="fde86-159">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="fde86-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> jest przydatne w sytuacjach, gdy proces roboczy wątki bloku.</span><span class="sxs-lookup"><span data-stu-id="fde86-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="fde86-161">Nie można używać typów jako obiekty blokady.</span><span class="sxs-lookup"><span data-stu-id="fde86-161">Don't use types as lock objects.</span></span> <span data-ttu-id="fde86-162">Oznacza to, takich jak uniknąć kodu `lock(typeof(X))` w języku C# lub `SyncLock(GetType(X))` w języku Visual Basic lub korzystanie z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> z <xref:System.Type> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fde86-162">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="fde86-163">Dla danego typu, jest tylko jedno wystąpienie <xref:System.Type?displayProperty=nameWithType> na domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fde86-163">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="fde86-164">Jeśli wykonywane blokady na typ jest publiczny, kodu innego niż własny może zająć blokad, co prowadzi do zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="fde86-164">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="fde86-165">Aby uzyskać dodatkowe problemy, zobacz [najlepsze rozwiązania dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="fde86-165">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="fde86-166">Należy zachować ostrożność podczas blokowania w wystąpieniach, na przykład `lock(this)` w języku C# lub `SyncLock(Me)` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fde86-166">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="fde86-167">Jeśli inny kod w aplikacji zewnętrznych do typu, przyjmuje blokady na obiekcie, może wystąpić zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="fde86-167">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="fde86-168">Upewnij się, że wątek, który wprowadził monitor zawsze pozostawia monitora, nawet jeśli wystąpi wyjątek, gdy wątek znajduje się w monitorze.</span><span class="sxs-lookup"><span data-stu-id="fde86-168">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="fde86-169">C# [blokady](~/docs/csharp/language-reference/keywords/lock-statement.md) instrukcji i Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrukcji Podaj to zachowanie automatycznie, wykorzystujących **koniec** bloku, aby upewnić się, że <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> jest wywołuje się.</span><span class="sxs-lookup"><span data-stu-id="fde86-169">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="fde86-170">Jeśli nie można zapewnić **zakończenia** zostanie wywołana, należy rozważyć zmianę projektu do użycia **obiektu Mutex**.</span><span class="sxs-lookup"><span data-stu-id="fde86-170">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="fde86-171">Obiektu mutex jest zwalniany automatycznie, gdy zakończenie wątku, który obecnie jest jego właścicielem.</span><span class="sxs-lookup"><span data-stu-id="fde86-171">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="fde86-172">Użyj wielu wątków zadań, które wymagają różnych zasobów i przypisywać wiele wątków do pojedynczego zasobu.</span><span class="sxs-lookup"><span data-stu-id="fde86-172">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="fde86-173">Na przykład wszystkie zadania dotyczące operacji We/Wy korzysta z o własnym wątku, ponieważ wątek będzie zablokować podczas operacji We/Wy i w związku z tym zezwolić na inne wątki do wykonania.</span><span class="sxs-lookup"><span data-stu-id="fde86-173">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="fde86-174">Dane wejściowe użytkownika jest inny zasób, który korzysta z dedykowanym wątku.</span><span class="sxs-lookup"><span data-stu-id="fde86-174">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="fde86-175">Na komputerze z jednym procesorem zadań, która obejmuje obliczeń obciążających współdziała z danych wejściowych użytkownika i zadaniach dotyczących operacji We/Wy, ale wiele zadań intensywnie obliczeń będą konkurować ze sobą.</span><span class="sxs-lookup"><span data-stu-id="fde86-175">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="fde86-176">Należy rozważyć użycie metody <xref:System.Threading.Interlocked> klasy zmian stanu prostego, zamiast `lock` instrukcji (`SyncLock` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="fde86-176">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="fde86-177">`lock` Instrukcja jest dobrym narzędzie ogólnego przeznaczenia, ale <xref:System.Threading.Interlocked> klasy zapewnia lepszą wydajność aktualizacji, które muszą być atomic.</span><span class="sxs-lookup"><span data-stu-id="fde86-177">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="fde86-178">Wewnętrznie wykonuje on prefiks jedną blokadą jeśli ma rywalizacji nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="fde86-178">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="fde86-179">W przeglądów kodu Obejrzyj dla kodu, takie jak przedstawionych w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="fde86-179">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="fde86-180">W pierwszym przykładzie jest zwiększany zmiennej stanu:</span><span class="sxs-lookup"><span data-stu-id="fde86-180">In the first example, a state variable is incremented:</span></span>  
  
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
  
     <span data-ttu-id="fde86-181">Wydajność można poprawić za pomocą <xref:System.Threading.Interlocked.Increment%2A> zamiast metody `lock` instrukcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fde86-181">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="fde86-182">W programie .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.Add%2A> metoda zapewnia atomic aktualizacje w przyrostach większy niż 1.</span><span class="sxs-lookup"><span data-stu-id="fde86-182">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method provides atomic updates in increments larger than 1.</span></span>  
  
     <span data-ttu-id="fde86-183">W drugim przykładzie zmienna typu odniesienia jest aktualizowany tylko wtedy, gdy jest odwołanie o wartości null (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="fde86-183">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
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
  
     <span data-ttu-id="fde86-184">Można poprawić wydajność przy użyciu <xref:System.Threading.Interlocked.CompareExchange%2A> metody zamiast tego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fde86-184">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="fde86-185">W programie .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.CompareExchange%2A> metoda ma rodzajowy przeciążenia, które umożliwia bezpieczne zastąpienie dowolnego typu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="fde86-185">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.CompareExchange%2A> method has a generic overload that can be used for type-safe replacement of any reference type.</span></span>  
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="fde86-186">Zalecenia dotyczące biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="fde86-186">Recommendations for Class Libraries</span></span>  
 <span data-ttu-id="fde86-187">Należy wziąć pod uwagę poniższe wskazówki podczas projektowania biblioteki klas dla wielowątkowości:</span><span class="sxs-lookup"><span data-stu-id="fde86-187">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="fde86-188">Uniknąć konieczności synchronizacji, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="fde86-188">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="fde86-189">Jest to szczególnie istotne dla kodu intensywnie używane.</span><span class="sxs-lookup"><span data-stu-id="fde86-189">This is especially true for heavily used code.</span></span> <span data-ttu-id="fde86-190">Algorytm może na przykład dostosowana do tolerować wyścigu, a nie jej wyeliminowania.</span><span class="sxs-lookup"><span data-stu-id="fde86-190">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="fde86-191">Niepotrzebne synchronizacji spadku wydajności i tworzy możliwości zakleszczenie i sytuacja wyścigu.</span><span class="sxs-lookup"><span data-stu-id="fde86-191">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="fde86-192">Wprowadź dane statyczne (`Shared` w języku Visual Basic) wielowątkowość domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fde86-192">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="fde86-193">Nie należy wprowadzać wątku danych wystąpienia bezpieczne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fde86-193">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="fde86-194">Dodawanie blokad, aby utworzyć kod wątkowo spadku wydajności, zwiększa rywalizacji blokad i tworzy możliwość Zakleszczenie występuje.</span><span class="sxs-lookup"><span data-stu-id="fde86-194">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="fde86-195">Wspólne modeli aplikacji tylko jeden wątek jednocześnie wykonuje kod użytkownika, co minimalizuje konieczność bezpieczeństwa wątków.</span><span class="sxs-lookup"><span data-stu-id="fde86-195">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="fde86-196">Z tego powodu bibliotek klas .NET Framework nie są wątkowo bezpieczne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fde86-196">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="fde86-197">Unikaj udostępnia metody statyczne, które zmienia stan statycznych.</span><span class="sxs-lookup"><span data-stu-id="fde86-197">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="fde86-198">W typowych scenariuszach serwera stanu statycznego jest współużytkowane przez wiele żądań, co oznacza, że wiele wątków może zostać uruchomiony ten kod w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="fde86-198">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="fde86-199">Spowoduje to otwarcie się możliwość wątkowość usterki.</span><span class="sxs-lookup"><span data-stu-id="fde86-199">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="fde86-200">Należy rozważyć użycie wzorzec projektowania, który hermetyzuje danych do wystąpienia, które nie są współużytkowane przez wiele żądań.</span><span class="sxs-lookup"><span data-stu-id="fde86-200">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="fde86-201">Ponadto jeśli dane statyczne są synchronizowane, wywołań między metod statycznych, które zmiany stanu może spowodować zakleszczenie lub nadmiarowe synchronizacji, negatywnego wpływu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="fde86-201">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde86-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fde86-202">See Also</span></span>  
 [<span data-ttu-id="fde86-203">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="fde86-203">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="fde86-204">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="fde86-204">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
