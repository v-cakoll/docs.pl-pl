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
ms.openlocfilehash: 46b0add67fc6bc139ef02e09190670870749d4c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874779"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="847ad-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="847ad-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="847ad-103">`dangerousThreadingAPI` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> metoda jest wywoływana z wątku innego niż bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="847ad-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="847ad-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="847ad-104">Symptoms</span></span>  
 <span data-ttu-id="847ad-105">Aplikacja nie odpowiada lub zawiesza się na czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="847ad-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="847ad-106">Dane systemu lub aplikacji może pozostać w nieprzewidywalnym stanie tymczasowo, lub nawet po zakończeniu zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="847ad-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="847ad-107">Niektóre operacje nie są wykonywane zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="847ad-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="847ad-108">Objawy mogą się znacznie zmieniać z powodu losowości związane z problemem.</span><span class="sxs-lookup"><span data-stu-id="847ad-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="847ad-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="847ad-109">Cause</span></span>  
 <span data-ttu-id="847ad-110">Wątek asynchronicznie została zawieszona przez inny wątek przy użyciu <xref:System.Threading.Thread.Suspend%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="847ad-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="847ad-111">Nie istnieje żaden sposób, aby określić, kiedy jest bezpieczne wstrzymania innego wątku, która może być w trakcie wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="847ad-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="847ad-112">Zawieszanie wątków może spowodować uszkodzenie danych lub dzieleniu invariants.</span><span class="sxs-lookup"><span data-stu-id="847ad-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="847ad-113">Wątek będzie umieszczona w stanie wstrzymania i wznowienia nigdy nie przy użyciu <xref:System.Threading.Thread.Resume%2A> metody, aplikację można odłożyć na czas nieokreślony i potencjalnie uszkodzić dane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="847ad-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="847ad-114">Tych metod oznaczono jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="847ad-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="847ad-115">Jeśli podstawowych synchronizacji są przechowywane przez wątek docelowy, pozostaną one konsekwencje na gruncie podczas zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="847ad-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="847ad-116">Może to prowadzić do zakleszczenia powinien innego wątku, na przykład wątek wykonywania <xref:System.Threading.Thread.Suspend%2A>, próba uzyskania blokady na element pierwotny.</span><span class="sxs-lookup"><span data-stu-id="847ad-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="847ad-117">W takiej sytuacji problem w sytuacji, jak zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="847ad-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="847ad-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="847ad-118">Resolution</span></span>  
 <span data-ttu-id="847ad-119">Unikaj projektów, które korzystają z <xref:System.Threading.Thread.Suspend%2A> i <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="847ad-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="847ad-120">Współpracy między wątkami, użyj elementów podstawowych synchronizacji takich jak <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, lub C# `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="847ad-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="847ad-121">Jeśli musisz użyć następujących metod, przedział czasu i minimalizując zakres ilość kodu, który jest wykonywany, gdy wątek jest w stanie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="847ad-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="847ad-122">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="847ad-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="847ad-123">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="847ad-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="847ad-124">Informuje jedynie dane o niebezpieczne operacje na wątkach.</span><span class="sxs-lookup"><span data-stu-id="847ad-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="847ad-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="847ad-125">Output</span></span>  
 <span data-ttu-id="847ad-126">MDA identyfikuje niebezpiecznych metodę wątkowości, który spowodował zostanie uaktywniony.</span><span class="sxs-lookup"><span data-stu-id="847ad-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="847ad-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="847ad-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="847ad-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="847ad-128">Example</span></span>  
 <span data-ttu-id="847ad-129">Poniższy przykład kodu demonstruje wywołanie <xref:System.Threading.Thread.Suspend%2A> metodę, która powoduje, że aktywacja `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="847ad-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="847ad-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="847ad-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="847ad-131">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="847ad-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="847ad-132">lock, instrukcja</span><span class="sxs-lookup"><span data-stu-id="847ad-132">lock Statement</span></span>](~/docs/csharp/language-reference/keywords/lock-statement.md)
