---
title: "Synchronizacja wątku (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2b51775eac5221ec8c723d89323d1f4f542d2453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="thread-synchronization-c"></a><span data-ttu-id="3bbc7-102">Synchronizacja wątku (C#)</span><span class="sxs-lookup"><span data-stu-id="3bbc7-102">Thread Synchronization (C#)</span></span>
<span data-ttu-id="3bbc7-103">W poniższych sekcjach opisano funkcje i klasy, które mogą służyć do synchronizowania dostęp do zasobów w aplikacjach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-103">The following sections describe features and classes that can be used to synchronize access to resources in multithreaded applications.</span></span>  
  
 <span data-ttu-id="3bbc7-104">Jedną z korzyści wynikające ze stosowania wiele wątków w aplikacji jest asynchronicznie wykonuje każdy wątek.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-104">One of the benefits of using multiple threads in an application is that each thread executes asynchronously.</span></span> <span data-ttu-id="3bbc7-105">Dla aplikacji systemu Windows dzięki temu czasochłonnych zadań wykonywanych w tle podczas okna aplikacji a formanty pozostają reakcji.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-105">For Windows applications, this allows time-consuming tasks to be performed in the background while the application window and controls remain responsive.</span></span> <span data-ttu-id="3bbc7-106">Dla serwera aplikacji wielowątkowość udostępnia możliwość obsługi każdego żądania przychodzącego z innego wątku.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-106">For server applications, multithreading provides the ability to handle each incoming request with a different thread.</span></span> <span data-ttu-id="3bbc7-107">W przeciwnym razie wartość każdego nowego żądania nie będą uzyskać obsługiwane, dopóki nie zostały całkowicie spełnione poprzedniego żądania.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-107">Otherwise, each new request would not get serviced until the previous request had been fully satisfied.</span></span>  
  
 <span data-ttu-id="3bbc7-108">Jednak charakter asynchronicznych wątków oznacza, że dostęp do zasobów, takich jak dojścia do plików, połączeń sieciowych i pamięci musi być skoordynowany sposób.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-108">However, the asynchronous nature of threads means that access to resources such as file handles, network connections, and memory must be coordinated.</span></span> <span data-ttu-id="3bbc7-109">W przeciwnym razie dwie lub więcej wątków można uzyskać dostępu do tego samego zasobu w tym samym czasie, każdy zna drugiego akcje.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-109">Otherwise, two or more threads could access the same resource at the same time, each unaware of the other's actions.</span></span> <span data-ttu-id="3bbc7-110">Wynik jest uszkodzenia nieprzewidywalne danych.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-110">The result is unpredictable data corruption.</span></span>  
  
 <span data-ttu-id="3bbc7-111">Dla proste operacje na typy całkowite danych liczbowych, synchronizacja wątków można wykonywać z członkami <xref:System.Threading.Interlocked> klasy.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-111">For simple operations on integral numeric data types, synchronizing threads can be accomplished with members of the <xref:System.Threading.Interlocked> class.</span></span> <span data-ttu-id="3bbc7-112">Dla wszystkich innych danych typów i zasobów z systemem innym niż wielowątkowość wielowątkowość można bezpiecznie wykonać tylko przy użyciu konstrukcji w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-112">For all other data types and non thread-safe resources, multithreading can only be safely performed using the constructs in this topic.</span></span>  
  
 <span data-ttu-id="3bbc7-113">Aby uzyskać ogólne informacje na temat programów wielowątkowych w zobacz:</span><span class="sxs-lookup"><span data-stu-id="3bbc7-113">For background information on multithreaded programming, see:</span></span>  
  
-   [<span data-ttu-id="3bbc7-114">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="3bbc7-114">Managed Threading Basics</span></span>](../../../../standard/threading/managed-threading-basics.md)  
  
-   [<span data-ttu-id="3bbc7-115">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="3bbc7-115">Using Threads and Threading</span></span>](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [<span data-ttu-id="3bbc7-116">Zarządzana wątkowość — najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="3bbc7-116">Managed Threading Best Practices</span></span>](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a><span data-ttu-id="3bbc7-117">Lock — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="3bbc7-117">The lock Keyword</span></span>  
 <span data-ttu-id="3bbc7-118">C# `lock` instrukcja może być używana przez inne wątki aby upewnić się, że bloku kodu jest uruchamiane w celu ukończenia bez przeszkód.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-118">The C# `lock` statement can be used to ensure that a block of code runs to completion without interruption by other threads.</span></span> <span data-ttu-id="3bbc7-119">Jest to osiągane przez uzyskanie blokady wzajemnego wykluczeń dla danego obiektu w czasie trwania blok kodu.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-119">This is accomplished by obtaining a mutual-exclusion lock for a given object for the duration of the code block.</span></span>  
  
 <span data-ttu-id="3bbc7-120">A `lock` instrukcji jest podawana jako argument obiektu i następuje blok kodu, który ma zostać wykonana tylko jednego wątku naraz.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-120">A `lock` statement is given an object as an argument, and is followed by a code block that is to be executed by only one thread at a time.</span></span> <span data-ttu-id="3bbc7-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3bbc7-121">For example:</span></span>  
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 <span data-ttu-id="3bbc7-122">Argument dostarczony do `lock` — słowo kluczowe musi być obiektem typu odwołania i służy do definiowania zakresu blokady.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-122">The argument provided to the `lock` keyword must be an object based on a reference type, and is used to define the scope of the lock.</span></span> <span data-ttu-id="3bbc7-123">W powyższym przykładzie zakres blokady jest ograniczony do tej funkcji, ponieważ nie odwołania do obiektu `lockThis` istnieje poza funkcją.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-123">In the example above, the lock scope is limited to this function because no references to the object `lockThis` exist outside the function.</span></span> <span data-ttu-id="3bbc7-124">Odniesienie został znaleziony, może rozszerzyć zakres blokady do tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-124">If such a reference did exist, lock scope would extend to that object.</span></span> <span data-ttu-id="3bbc7-125">Mówiąc ściślej dostarczony obiekt jest używany wyłącznie do unikatowego identyfikowania udostępnianego między wiele wątków, więc można instancji klasy dowolnego zasobu.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-125">Strictly speaking, the object provided is used solely to uniquely identify the resource being shared among multiple threads, so it can be an arbitrary class instance.</span></span> <span data-ttu-id="3bbc7-126">W praktyce jednak ten obiekt zazwyczaj reprezentuje zasobów, dla których wątku synchronizacji jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-126">In practice, however, this object usually represents the resource for which thread synchronization is necessary.</span></span> <span data-ttu-id="3bbc7-127">Na przykład w przypadku obiektu kontenera ma być używany przez wiele wątków, następnie kontenera mogą zostać przekazane do zablokowania i blok kodu zsynchronizowane po blokady może uzyskać dostępu do kontenera.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-127">For example, if a container object is to be used by multiple threads, then the container can be passed to lock, and the synchronized code block following the lock would access the container.</span></span> <span data-ttu-id="3bbc7-128">Tak długo, jak inne wątki blokuje na tym samym zawierają przed uzyskaniem dostępu do, a następnie bezpiecznie jest zsynchronizowany dostęp do obiektu.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-128">As long as other threads locks on the same contain before accessing it, then access to the object is safely synchronized.</span></span>  
  
 <span data-ttu-id="3bbc7-129">Ogólnie rzecz biorąc, zaleca się unikać blokowania na `public` typu, lub do obiektów poza kontrolą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-129">Generally, it is best to avoid locking on a `public` type, or on object instances beyond the control of your application.</span></span> <span data-ttu-id="3bbc7-130">Na przykład `lock(this)` może być problemem, jeśli wystąpienie jest dostępny publicznie, ponieważ kod poza kontrolą może zablokować obiektu również.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-130">For example, `lock(this)` can be problematic if the instance can be accessed publicly, because code beyond your control may lock on the object as well.</span></span> <span data-ttu-id="3bbc7-131">To może utworzyć zakleszczenie sytuacji, gdy dwa lub więcej wątków oczekiwania na zwolnienie tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-131">This could create deadlock situations where two or more threads wait for the release of the same object.</span></span> <span data-ttu-id="3bbc7-132">Blokowanie typu publicznego danych, w przeciwieństwie do obiektu może spowodować problemy z tego samego powodu.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-132">Locking on a public data type, as opposed to an object, can cause problems for the same reason.</span></span> <span data-ttu-id="3bbc7-133">Blokowanie na ciągi literału jest szczególnie ryzykowne, ponieważ ciągi literału *interned* przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="3bbc7-133">Locking on literal strings is especially risky because literal strings are *interned* by the common language runtime (CLR).</span></span> <span data-ttu-id="3bbc7-134">Oznacza to, że istnieje jedno wystąpienie dowolnego ciągu literału dla całego programu, dokładnie tego samego obiektu reprezentuje literał we wszystkich uruchomionych domen aplikacji na wszystkie wątki.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-134">This means that there is one instance of any given string literal for the entire program, the exact same object represents the literal in all running application domains, on all threads.</span></span> <span data-ttu-id="3bbc7-135">W związku z tym zablokować ciągu z tej samej zawartości dowolne miejsce w blokad procesu aplikacji wszystkich wystąpień tego ciągu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-135">As a result, a lock placed on a string with the same contents anywhere in the application process locks all instances of that string in the application.</span></span> <span data-ttu-id="3bbc7-136">W związku z tym najlepiej do blokowania nie jest interned członkiem prywatne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-136">As a result, it is best to lock a private or protected member that is not interned.</span></span> <span data-ttu-id="3bbc7-137">Niektóre klasy Podaj członków specjalnie z myślą o blokowania.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-137">Some classes provide members specifically for locking.</span></span> <span data-ttu-id="3bbc7-138"><xref:System.Array> Typu, na przykład zawiera <xref:System.Array.SyncRoot%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-138">The <xref:System.Array> type, for example, provides <xref:System.Array.SyncRoot%2A>.</span></span> <span data-ttu-id="3bbc7-139">Podaj wiele typów kolekcji `SyncRoot` również elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-139">Many collection types provide a `SyncRoot` member as well.</span></span>  
  
 <span data-ttu-id="3bbc7-140">Aby uzyskać więcej informacji na temat `lock` instrukcji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="3bbc7-140">For more information about the `lock` statement, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3bbc7-141">Lock — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3bbc7-141">lock Statement</span></span>](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a><span data-ttu-id="3bbc7-142">Monitory</span><span class="sxs-lookup"><span data-stu-id="3bbc7-142">Monitors</span></span>  
 <span data-ttu-id="3bbc7-143">Podobnie jak `lock` — słowo kluczowe, monitory zapobiec bloki kodu z jednoczesne wykonywanie przez wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-143">Like the `lock` keyword, monitors prevent blocks of code from simultaneous execution by multiple threads.</span></span> <span data-ttu-id="3bbc7-144"><xref:System.Threading.Monitor.Enter%2A> Metoda pozwala jeden i tylko jeden wątek przejść do następujących instrukcji; wątki są zablokowane do czasu wykonywania wywołań wątku <xref:System.Threading.Monitor.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-144">The <xref:System.Threading.Monitor.Enter%2A> method allows one and only one thread to proceed into the following statements; all other threads are blocked until the executing thread calls <xref:System.Threading.Monitor.Exit%2A>.</span></span> <span data-ttu-id="3bbc7-145">Jest to tak samo jak przy użyciu `lock` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-145">This is just like using the `lock` keyword.</span></span> <span data-ttu-id="3bbc7-146">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3bbc7-146">For example:</span></span>  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 <span data-ttu-id="3bbc7-147">Jest to równoważne:</span><span class="sxs-lookup"><span data-stu-id="3bbc7-147">This is equivalent to:</span></span>  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 <span data-ttu-id="3bbc7-148">Przy użyciu `lock` — słowo kluczowe jest zazwyczaj preferowane przy użyciu <xref:System.Threading.Monitor> bezpośrednio, klasa, zarówno ponieważ `lock` jest bardziej zwięzły i dlatego `lock` temu zwolnienie monitora źródłowego, nawet jeśli chroniony kod powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-148">Using the `lock` keyword is generally preferred over using the <xref:System.Threading.Monitor> class directly, both because `lock` is more concise, and because `lock` insures that the underlying monitor is released, even if the protected code throws an exception.</span></span> <span data-ttu-id="3bbc7-149">Jest to realizowane przy użyciu `finally` — słowo kluczowe, który wykonuje jego blok kodu skojarzone niezależnie od tego, czy jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-149">This is accomplished with the `finally` keyword, which executes its associated code block regardless of whether an exception is thrown.</span></span>  
  
## <a name="synchronization-events-and-wait-handles"></a><span data-ttu-id="3bbc7-150">Zdarzenia synchronizacji i uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="3bbc7-150">Synchronization Events and Wait Handles</span></span>  
 <span data-ttu-id="3bbc7-151">Przy użyciu blokady lub monitor jest przydatne w przypadku uniemożliwia jednoczesne wykonywanie wątku wrażliwych bloki kodu, ale te konstrukcji nie zezwalaj na jeden wątek, aby komunikować się zdarzenia do innego.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-151">Using a lock or monitor is useful for preventing the simultaneous execution of thread-sensitive blocks of code, but these constructs do not allow one thread to communicate an event to another.</span></span> <span data-ttu-id="3bbc7-152">Wymaga to *zdarzenia synchronizacji*, które są obiektów, które mają jeden z dwóch stanów sygnałowego i cofanie sygnałowego, który może służyć do aktywowania i wstrzymać wątków.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-152">This requires *synchronization events*, which are objects that have one of two states, signaled and un-signaled, that can be used to activate and suspend threads.</span></span> <span data-ttu-id="3bbc7-153">Wątki może zostać zawieszone przez wykonywane oczekiwania na zdarzenie synchronizacji unsignaled i można aktywować, zmieniając stanu zdarzenia do sygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-153">Threads can be suspended by being made to wait on a synchronization event that is unsignaled, and can be activated by changing the event state to signaled.</span></span> <span data-ttu-id="3bbc7-154">Próba oczekiwania na zdarzenie, które zostało już zasygnalizowane przez wątek wątek kontynuuje wykonywanie bez opóźnień.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-154">If a thread attempts to wait on an event that is already signaled, then the thread continues to execute without delay.</span></span>  
  
 <span data-ttu-id="3bbc7-155">Istnieją dwa rodzaje zdarzeń synchronizacji: <xref:System.Threading.AutoResetEvent>, i <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-155">There are two kinds of synchronization events: <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.ManualResetEvent>.</span></span> <span data-ttu-id="3bbc7-156">Różnią się tylko w tym <xref:System.Threading.AutoResetEvent> zmiany z sygnalizowane do unsignaled automatycznie każdy razem aktywuje wątku.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-156">They differ only in that <xref:System.Threading.AutoResetEvent> changes from signaled to unsignaled automatically any time it activates a thread.</span></span> <span data-ttu-id="3bbc7-157">Z drugiej strony <xref:System.Threading.ManualResetEvent> umożliwia dowolną liczbę wątków, aby być aktywowany przez stanu sygnałowego i tylko powróci do unsignaled jeśli jego <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-157">Conversely, a <xref:System.Threading.ManualResetEvent> allows any number of threads to be activated by its signaled state, and will only revert to an unsignaled state when its <xref:System.Threading.EventWaitHandle.Reset%2A> method is called.</span></span>  
  
 <span data-ttu-id="3bbc7-158">Wątków jest możliwe oczekiwanie na zdarzenia przez wywołanie metody oczekiwania, takich jak <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, lub <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-158">Threads can be made to wait on events by calling one of the wait methods, such as <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, or <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span> <span data-ttu-id="3bbc7-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>powoduje, że wątek poczekać, aż sygnalizowane staje się pojedyncze zdarzenie, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blokuje wątku, dopóki co najmniej jednego zdarzenia wskazanych stają się sygnalizuje, i <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blokuje wątek, dopóki wszystkie zdarzenia wskazanych stają się sygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> causes the thread to wait until a single event becomes signaled, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blocks a thread until one or more indicated events become signaled, and <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blocks the thread until all of the indicated events become signaled.</span></span> <span data-ttu-id="3bbc7-160">Zdarzenie jest sygnalizowane po jego <xref:System.Threading.EventWaitHandle.Set%2A> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-160">An event becomes signaled when its <xref:System.Threading.EventWaitHandle.Set%2A> method is called.</span></span>  
  
 <span data-ttu-id="3bbc7-161">W poniższym przykładzie jest tworzony i uruchomione przez wątek `Main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-161">In the following example, a thread is created and started by the `Main` function.</span></span> <span data-ttu-id="3bbc7-162">Nowego wątku oczekiwania na zdarzenie przy użyciu <xref:System.Threading.WaitHandle.WaitOne%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-162">The new thread waits on an event using the <xref:System.Threading.WaitHandle.WaitOne%2A> method.</span></span> <span data-ttu-id="3bbc7-163">Wątek jest zawieszony aż do zdarzenia staje się zgłoszony przez podstawowy wątku, który jest wykonywany `Main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-163">The thread is suspended until the event becomes signaled by the primary thread that is executing the `Main` function.</span></span> <span data-ttu-id="3bbc7-164">Gdy zdarzenie jest sygnalizowane, zwraca wątek pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-164">Once the event becomes signaled, the auxiliary thread returns.</span></span> <span data-ttu-id="3bbc7-165">W takim przypadku ponieważ zdarzenie jest używana tylko jeden wątek aktywacji, albo <xref:System.Threading.AutoResetEvent> lub <xref:System.Threading.ManualResetEvent> klasy może być używane.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-165">In this case, because the event is only used for one thread activation, either the <xref:System.Threading.AutoResetEvent> or <xref:System.Threading.ManualResetEvent> classes could be used.</span></span>  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a><span data-ttu-id="3bbc7-166">Obiekt mutex</span><span class="sxs-lookup"><span data-stu-id="3bbc7-166">Mutex Object</span></span>  
 <span data-ttu-id="3bbc7-167">A *obiektu mutex* jest podobny do monitora; uniemożliwia jednoczesne wykonywanie bloku kodu przez więcej niż jeden wątek na raz.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-167">A *mutex* is similar to a monitor; it prevents the simultaneous execution of a block of code by more than one thread at a time.</span></span> <span data-ttu-id="3bbc7-168">W rzeczywistości nazwy "mutex" jest skrócona forma termin "wykluczają się wzajemnie."</span><span class="sxs-lookup"><span data-stu-id="3bbc7-168">In fact, the name "mutex" is a shortened form of the term "mutually exclusive."</span></span> <span data-ttu-id="3bbc7-169">W przeciwieństwie do monitorów jednak obiektu mutex umożliwia synchronizację wątków procesów.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-169">Unlike monitors, however, a mutex can be used to synchronize threads across processes.</span></span> <span data-ttu-id="3bbc7-170">Obiektu mutex jest reprezentowana przez <xref:System.Threading.Mutex> klasy.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-170">A mutex is represented by the <xref:System.Threading.Mutex> class.</span></span>  
  
 <span data-ttu-id="3bbc7-171">W przypadku synchronizacji między procesami obiektu mutex jest nazywany *nazwanego obiektu mutex* ponieważ jest do użycia w innej aplikacji, i dlatego nie można udostępnić za pomocą zmiennej globalnej lub statycznej.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-171">When used for inter-process synchronization, a mutex is called a *named mutex* because it is to be used in another application, and therefore it cannot be shared by means of a global or static variable.</span></span> <span data-ttu-id="3bbc7-172">Musi ona zawierać nazwę, aby obie aplikacje mają dostęp do tego samego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-172">It must be given a name so that both applications can access the same mutex object.</span></span>  
  
 <span data-ttu-id="3bbc7-173">Chociaż wątek wewnątrz procesu synchronizacji można użyć obiektu mutex, przy użyciu <xref:System.Threading.Monitor> jest zazwyczaj preferowana, ponieważ monitory zostały zaprojektowane specjalnie dla programu .NET Framework i w związku z tym należy lepszego wykorzystania zasobów.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-173">Although a mutex can be used for intra-process thread synchronization, using <xref:System.Threading.Monitor> is generally preferred, because monitors were designed specifically for the .NET Framework and therefore make better use of resources.</span></span> <span data-ttu-id="3bbc7-174">Z kolei <xref:System.Threading.Mutex> klasy jest otoką elementu do konstrukcji Win32.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-174">In contrast, the <xref:System.Threading.Mutex> class is a wrapper to a Win32 construct.</span></span> <span data-ttu-id="3bbc7-175">Mimo że jest bardziej efektywne niż monitor, obiektu mutex wymaga międzyoperacyjnego przejścia, które są w praktyce bardziej kosztowne niż wymagane przez <xref:System.Threading.Monitor> klasy.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-175">While it is more powerful than a monitor, a mutex requires interop transitions that are more computationally expensive than those required by the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="3bbc7-176">Na przykład za pomocą obiektu mutex, zobacz [muteksy](../../../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="3bbc7-176">For an example of using a mutex, see [Mutexes](../../../../standard/threading/mutexes.md).</span></span>  
  
## <a name="interlocked-class"></a><span data-ttu-id="3bbc7-177">Interlocked — klasa</span><span class="sxs-lookup"><span data-stu-id="3bbc7-177">Interlocked Class</span></span>  
 <span data-ttu-id="3bbc7-178">Można użyć metody <xref:System.Threading.Interlocked> klasy, aby uniknąć problemów, które mogą wystąpić, gdy wiele wątków próbują jednocześnie aktualizacji lub porównywania taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-178">You can use the methods of the <xref:System.Threading.Interlocked> class to prevent problems that can occur when multiple threads attempt to simultaneously update or compare the same value.</span></span> <span data-ttu-id="3bbc7-179">Metody tej klasy pozwala bezpiecznie przyrostu, zmniejszyć programu exchange i porównuje wartości z dowolnego wątku.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-179">The methods of this class let you safely increment, decrement, exchange, and compare values from any thread.</span></span>  
  
## <a name="readerwriter-locks"></a><span data-ttu-id="3bbc7-180">ReaderWriter blokad</span><span class="sxs-lookup"><span data-stu-id="3bbc7-180">ReaderWriter Locks</span></span>  
 <span data-ttu-id="3bbc7-181">W niektórych przypadkach można zablokować zasobu tylko wtedy, gdy dane są zapisywane i zezwolenie na wielu klientów jednocześnie odczytać danych, gdy dane nie są aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-181">In some cases, you may want to lock a resource only when data is being written and permit multiple clients to simultaneously read data when data is not being updated.</span></span> <span data-ttu-id="3bbc7-182"><xref:System.Threading.ReaderWriterLock> Klasy wymusza wyłącznego dostępu do zasobu, gdy wątek modyfikuje zasobu, ale pozwala dostępu otwarty podczas odczytu zasobu.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-182">The <xref:System.Threading.ReaderWriterLock> class enforces exclusive access to a resource while a thread is modifying the resource, but it allows non-exclusive access when reading the resource.</span></span> <span data-ttu-id="3bbc7-183">ReaderWriter blokady są przydatne alternatywą dla blokady na wyłączność, które powodują inne wątki oczekiwania, nawet gdy te wątków nie trzeba aktualizacji danych.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-183">ReaderWriter locks are a useful alternative to exclusive locks, which cause other threads to wait, even when those threads do not need to update data.</span></span>  
  
## <a name="deadlocks"></a><span data-ttu-id="3bbc7-184">Zakleszczenie</span><span class="sxs-lookup"><span data-stu-id="3bbc7-184">Deadlocks</span></span>  
 <span data-ttu-id="3bbc7-185">Synchronizacja wątku jest nieocenione w aplikacjach wielowątkowych, ale zawsze zagrożenia tworzenia `deadlock`, gdzie wiele wątków oczekuje na siebie i pochodzi aplikacji do zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-185">Thread synchronization is invaluable in multithreaded applications, but there is always the danger of creating a `deadlock`, where multiple threads are waiting for each other and the application comes to a halt.</span></span> <span data-ttu-id="3bbc7-186">Zakleszczenie jest analogiczna do sytuacji, w której samochodów zostały zatrzymane w ograniczniku czterech sposób i czeka na innych przejść każda osoba.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-186">A deadlock is analogous to a situation in which cars are stopped at a four-way stop and each person is waiting for the other to go.</span></span> <span data-ttu-id="3bbc7-187">Unikanie zakleszczenie jest ważne; klucz jest dokładne planowanie.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-187">Avoiding deadlocks is important; the key is careful planning.</span></span> <span data-ttu-id="3bbc7-188">Zakleszczenie sytuacjach można często prognozowania przez tworzenie diagramów aplikacje wielowątkowe, przed rozpoczęciem kodowania.</span><span class="sxs-lookup"><span data-stu-id="3bbc7-188">You can often predict deadlock situations by diagramming multithreaded applications before you start coding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bbc7-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bbc7-189">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.WaitHandle.WaitOne%2A>  
 <xref:System.Threading.WaitHandle.WaitAny%2A>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.Thread.Join%2A>  
 <xref:System.Threading.Thread.Start%2A>  
 <xref:System.Threading.Thread.Sleep%2A>  
 <xref:System.Threading.Monitor>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="3bbc7-190">Aplikacje wielowątkowe (C#)</span><span class="sxs-lookup"><span data-stu-id="3bbc7-190">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="3bbc7-191">Lock — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3bbc7-191">lock Statement</span></span>](../../../../csharp/language-reference/keywords/lock-statement.md)  
 [<span data-ttu-id="3bbc7-192">Muteksy</span><span class="sxs-lookup"><span data-stu-id="3bbc7-192">Mutexes</span></span>](../../../../standard/threading/mutexes.md)  
 [<span data-ttu-id="3bbc7-193">Operacje blokowane</span><span class="sxs-lookup"><span data-stu-id="3bbc7-193">Interlocked Operations</span></span>](../../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="3bbc7-194">Autoresetevent —</span><span class="sxs-lookup"><span data-stu-id="3bbc7-194">AutoResetEvent</span></span>](../../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="3bbc7-195">Synchronizowanie danych na potrzeby wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="3bbc7-195">Synchronizing Data for Multithreading</span></span>](../../../../standard/threading/synchronizing-data-for-multithreading.md)
