---
title: dangerousThreadingAPI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 02f16bd9560346cca9b24d4e5b8e760fdb3afd18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="1c3da-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="1c3da-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="1c3da-103">`dangerousThreadingAPI` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> metoda jest wywoływana w wątku innego niż bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="1c3da-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1c3da-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="1c3da-104">Symptoms</span></span>  
 <span data-ttu-id="1c3da-105">Aplikacja nie odpowiada lub zawiesza się przez nieograniczony czas.</span><span class="sxs-lookup"><span data-stu-id="1c3da-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="1c3da-106">Dane systemu lub aplikacji może pozostać w nieprzewidywalnym stanie tymczasowo lub nawet po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c3da-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="1c3da-107">Niektóre operacje nie są wykonywane zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="1c3da-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="1c3da-108">Objawy różnią może z powodu problemu związanego z używaniem losowości.</span><span class="sxs-lookup"><span data-stu-id="1c3da-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1c3da-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="1c3da-109">Cause</span></span>  
 <span data-ttu-id="1c3da-110">Wątek asynchronicznie został wstrzymany za pomocą innego wątku <xref:System.Threading.Thread.Suspend%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1c3da-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="1c3da-111">Brak nie można określić, kiedy jest bezpieczne zawiesić inny wątek, która może być w trakcie wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="1c3da-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="1c3da-112">Zawieszanie wątków może spowodować uszkodzenie danych lub dzieleniu invariants.</span><span class="sxs-lookup"><span data-stu-id="1c3da-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="1c3da-113">Należy umieścić wątku w stanie wstrzymania i wznowienia nigdy nie przy użyciu <xref:System.Threading.Thread.Resume%2A> metody, aplikacja może zostać zawieszona na nieograniczony czas i potencjalnie uszkodzić dane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c3da-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="1c3da-114">Te metody oznaczono jako przestarzały.</span><span class="sxs-lookup"><span data-stu-id="1c3da-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="1c3da-115">Jeśli elementy podstawowe synchronizacji są przechowywane przez wątek docelowy, pozostaną one przechowywanych podczas zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="1c3da-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="1c3da-116">Może to prowadzić do zakleszczenia powinien innego wątku, na przykład wątku wykonywania <xref:System.Threading.Thread.Suspend%2A>, próba uzyskania blokady na element pierwotny.</span><span class="sxs-lookup"><span data-stu-id="1c3da-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="1c3da-117">W takiej sytuacji problem sam się uwidacznia zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="1c3da-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1c3da-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="1c3da-118">Resolution</span></span>  
 <span data-ttu-id="1c3da-119">Unikaj projekty, które wymagają użycia <xref:System.Threading.Thread.Suspend%2A> i <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c3da-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="1c3da-120">Współpracy między wątkami, użyj takiego jak elementy podstawowe synchronizacji <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, C# lub `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1c3da-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="1c3da-121">Jeśli jest konieczne korzystanie z tych metod, zmniejsza okno czasu i zminimalizować ilość kodu, który wykonuje, gdy wątek jest w stanie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="1c3da-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1c3da-122">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1c3da-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="1c3da-123">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="1c3da-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="1c3da-124">Zwraca tylko dane o niebezpieczne operacje na wątkach.</span><span class="sxs-lookup"><span data-stu-id="1c3da-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1c3da-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="1c3da-125">Output</span></span>  
 <span data-ttu-id="1c3da-126">MDA identyfikuje niebezpiecznych metodę wątków, który spowodował jej uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="1c3da-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1c3da-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="1c3da-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="1c3da-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c3da-128">Example</span></span>  
 <span data-ttu-id="1c3da-129">Poniższy przykład kodu pokazuje wywołanie <xref:System.Threading.Thread.Suspend%2A> metodę, która powoduje, że aktywacji `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="1c3da-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```  
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c3da-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c3da-130">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="1c3da-131">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="1c3da-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="1c3da-132">lock, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1c3da-132">lock Statement</span></span>](~/docs/csharp/language-reference/keywords/lock-statement.md)
