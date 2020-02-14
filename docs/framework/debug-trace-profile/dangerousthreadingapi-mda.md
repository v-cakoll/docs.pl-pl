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
ms.openlocfilehash: 4e7e858dfb85eeccbadb23da60d081d1407e89d8
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216672"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="9f3cf-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="9f3cf-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="9f3cf-103">Asystent debugowania zarządzanego `dangerousThreadingAPI` (MDA) jest uaktywniany, gdy metoda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> jest wywoływana w wątku innym niż bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9f3cf-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="9f3cf-104">Symptoms</span></span>  
 <span data-ttu-id="9f3cf-105">Aplikacja nie odpowiada lub zawiesza się bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="9f3cf-106">Dane systemu lub aplikacji mogą być pozostawione w stanie nieprzewidywalnym tymczasowo lub nawet po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="9f3cf-107">Niektóre operacje nie są wykonywane zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="9f3cf-108">Objawy mogą się znacznie różnić ze względu na losowość problemu.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9f3cf-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="9f3cf-109">Cause</span></span>  
 <span data-ttu-id="9f3cf-110">Wątek jest asynchronicznie zawieszony przez inny wątek przy użyciu metody <xref:System.Threading.Thread.Suspend%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="9f3cf-111">Nie istnieje sposób, aby określić, kiedy jest bezpieczny, aby zawiesić inny wątek, który może znajdować się w środku operacji.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="9f3cf-112">Zawieszenie wątku może skutkować uszkodzeniem danych lub przerwaniem niezmiennych.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="9f3cf-113">Jeśli wątek ma być umieszczony w stanie wstrzymania i nigdy nie został wznowiony przy użyciu metody <xref:System.Threading.Thread.Resume%2A>, aplikacja może zawiesić się w nieskończoność i prawdopodobnie uszkodzić dane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="9f3cf-114">Te metody zostały oznaczone jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="9f3cf-115">Jeśli elementy pierwotne synchronizacji są przechowywane przez wątek docelowy, pozostaną one zachowane podczas zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="9f3cf-116">Może to prowadzić do zakleszczenia, na przykład wątek wykonujący <xref:System.Threading.Thread.Suspend%2A>, próbuje uzyskać blokadę dla elementu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="9f3cf-117">W tej sytuacji problem występuje w manifeście jako zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9f3cf-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="9f3cf-118">Resolution</span></span>  
 <span data-ttu-id="9f3cf-119">Unikaj projektów, które wymagają używania <xref:System.Threading.Thread.Suspend%2A> i <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="9f3cf-120">W celu współpracy między wątkami należy używać prymitywów synchronizacji, takich jak <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>C# lub instrukcji `lock`.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="9f3cf-121">Jeśli musisz użyć tych metod, Zmniejsz okno czasu i Zminimalizuj ilość kodu, który jest wykonywany, gdy wątek jest w stanie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9f3cf-122">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9f3cf-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="9f3cf-123">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="9f3cf-124">Raportuje tylko dane dotyczące niebezpiecznych operacji wątkowości.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9f3cf-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9f3cf-125">Output</span></span>  
 <span data-ttu-id="9f3cf-126">MDA identyfikuje niebezpieczną metodę wątkowości, która spowodowała jej aktywowanie.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9f3cf-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="9f3cf-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9f3cf-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f3cf-128">Example</span></span>  
 <span data-ttu-id="9f3cf-129">Poniższy przykład kodu demonstruje wywołanie metody <xref:System.Threading.Thread.Suspend%2A>, która powoduje aktywację `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="9f3cf-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f3cf-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f3cf-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="9f3cf-131">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9f3cf-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9f3cf-132">lock, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9f3cf-132">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
