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
ms.openlocfilehash: d3fe7d11657c2f9edd1fea7ff639f878f993d6b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174774"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="3566f-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="3566f-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="3566f-103">Asystent `dangerousThreadingAPI` debugowania zarządzanego (MDA) jest <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> aktywowany, gdy metoda jest wywoływana w wątku innym niż bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="3566f-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3566f-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="3566f-104">Symptoms</span></span>  
 <span data-ttu-id="3566f-105">Aplikacja nie odpowiada lub zawiesza się na czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="3566f-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="3566f-106">Dane systemu lub aplikacji mogą być pozostawione w nieprzewidywalnym stanie tymczasowo lub nawet po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3566f-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="3566f-107">Niektóre operacje nie są zakończeniu zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="3566f-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="3566f-108">Objawy mogą się znacznie różnić ze względu na przypadkowość nieodłącznie związane z problemem.</span><span class="sxs-lookup"><span data-stu-id="3566f-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3566f-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="3566f-109">Cause</span></span>  
 <span data-ttu-id="3566f-110">Wątek jest asynchronicznie zawieszone przez <xref:System.Threading.Thread.Suspend%2A> inny wątek przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="3566f-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="3566f-111">Nie ma sposobu, aby określić, kiedy jest bezpiecznie zawiesić inny wątek, który może być w środku operacji.</span><span class="sxs-lookup"><span data-stu-id="3566f-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="3566f-112">Zawieszenie wątku może spowodować uszkodzenie danych lub złamanie invariants.</span><span class="sxs-lookup"><span data-stu-id="3566f-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="3566f-113">Jeśli wątek zostanie umieszczony w stanie wstrzymania i nigdy nie zostanie wznowiony przy użyciu <xref:System.Threading.Thread.Resume%2A> metody, aplikacja może zawiesić się na czas nieokreślony i ewentualnie uszkodzić dane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3566f-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="3566f-114">Metody te zostały oznaczone jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="3566f-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="3566f-115">Jeśli prymitywy synchronizacji są utrzymywane przez wątek docelowy, pozostają one przechowywane podczas zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="3566f-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="3566f-116">Może to prowadzić do zakleszczenia powinien inny <xref:System.Threading.Thread.Suspend%2A>wątek, na przykład wątek wykonywania , próba uzyskania blokady na prymitywne.</span><span class="sxs-lookup"><span data-stu-id="3566f-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="3566f-117">W tej sytuacji problem objawia się jako zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="3566f-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3566f-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3566f-118">Resolution</span></span>  
 <span data-ttu-id="3566f-119">Unikaj wzorów, które <xref:System.Threading.Thread.Suspend%2A> <xref:System.Threading.Thread.Resume%2A>wymagają użycia i .</span><span class="sxs-lookup"><span data-stu-id="3566f-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="3566f-120">Do <xref:System.Threading.Monitor>współpracy między wątkami należy użyć ujegłędnych synchronizacji, takich jak , <xref:System.Threading.ReaderWriterLock> <xref:System.Threading.Mutex>, lub C# `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3566f-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="3566f-121">Jeśli należy użyć tych metod, zmniejszyć okno czasu i zminimalizować ilość kodu, który wykonuje, gdy wątek jest w stanie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="3566f-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3566f-122">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="3566f-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="3566f-123">To MDA nie ma wpływu na CLR.</span><span class="sxs-lookup"><span data-stu-id="3566f-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="3566f-124">Raportuje tylko dane dotyczące niebezpiecznych operacji wątkowania.</span><span class="sxs-lookup"><span data-stu-id="3566f-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3566f-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3566f-125">Output</span></span>  
 <span data-ttu-id="3566f-126">MDA identyfikuje niebezpieczną metodę gwintowania, która spowodowała jej aktywację.</span><span class="sxs-lookup"><span data-stu-id="3566f-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3566f-127">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="3566f-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="3566f-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="3566f-128">Example</span></span>  
 <span data-ttu-id="3566f-129">Poniższy przykład kodu pokazuje wywołanie <xref:System.Threading.Thread.Suspend%2A> metody, która `dangerousThreadingAPI`powoduje aktywację .</span><span class="sxs-lookup"><span data-stu-id="3566f-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3566f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3566f-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="3566f-131">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="3566f-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3566f-132">lock — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="3566f-132">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
