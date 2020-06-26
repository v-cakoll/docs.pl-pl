---
title: dangerousThreadingAPI MDA
description: Przejrzyj dangerousThreadingAPI Managed Debug Assistant (MDA), który jest uaktywniany po wywołaniu wątku. Suspend w wątku innym niż bieżący wątek.
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
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416008"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="6e442-103">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="6e442-103">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="6e442-104">`dangerousThreadingAPI`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> Metoda jest wywoływana w wątku innym niż bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="6e442-104">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6e442-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="6e442-105">Symptoms</span></span>  
 <span data-ttu-id="6e442-106">Aplikacja nie odpowiada lub zawiesza się bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="6e442-106">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="6e442-107">Dane systemu lub aplikacji mogą być pozostawione w stanie nieprzewidywalnym tymczasowo lub nawet po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e442-107">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="6e442-108">Niektóre operacje nie są wykonywane zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="6e442-108">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="6e442-109">Objawy mogą się znacznie różnić ze względu na losowość problemu.</span><span class="sxs-lookup"><span data-stu-id="6e442-109">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6e442-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="6e442-110">Cause</span></span>  
 <span data-ttu-id="6e442-111">Wątek jest asynchronicznie zawieszony przez inny wątek przy użyciu <xref:System.Threading.Thread.Suspend%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6e442-111">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="6e442-112">Nie istnieje sposób, aby określić, kiedy jest bezpieczny, aby zawiesić inny wątek, który może znajdować się w środku operacji.</span><span class="sxs-lookup"><span data-stu-id="6e442-112">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="6e442-113">Zawieszenie wątku może skutkować uszkodzeniem danych lub przerwaniem niezmiennych.</span><span class="sxs-lookup"><span data-stu-id="6e442-113">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="6e442-114">Jeśli wątek ma być umieszczony w stanie wstrzymania i nigdy nie został wznowiony przy użyciu <xref:System.Threading.Thread.Resume%2A> metody, aplikacja może zawiesić się w nieskończoność i prawdopodobnie uszkodzić dane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e442-114">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="6e442-115">Te metody zostały oznaczone jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="6e442-115">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="6e442-116">Jeśli elementy pierwotne synchronizacji są przechowywane przez wątek docelowy, pozostaną one zachowane podczas zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="6e442-116">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="6e442-117">Może to prowadzić do zakleszczenia, na przykład wątek wykonujący <xref:System.Threading.Thread.Suspend%2A> , próbuje uzyskać blokadę dla elementu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="6e442-117">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="6e442-118">W tej sytuacji problem występuje w manifeście jako zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="6e442-118">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6e442-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="6e442-119">Resolution</span></span>  
 <span data-ttu-id="6e442-120">Unikaj projektów, które wymagają używania <xref:System.Threading.Thread.Suspend%2A> i <xref:System.Threading.Thread.Resume%2A> .</span><span class="sxs-lookup"><span data-stu-id="6e442-120">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="6e442-121">Aby współdziałać między wątkami, należy użyć prymitywów synchronizacji, takich jak <xref:System.Threading.Monitor> , <xref:System.Threading.ReaderWriterLock> , <xref:System.Threading.Mutex> lub instrukcji języka C# `lock` .</span><span class="sxs-lookup"><span data-stu-id="6e442-121">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="6e442-122">Jeśli musisz użyć tych metod, Zmniejsz okno czasu i Zminimalizuj ilość kodu, który jest wykonywany, gdy wątek jest w stanie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="6e442-122">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6e442-123">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6e442-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="6e442-124">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="6e442-124">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="6e442-125">Raportuje tylko dane dotyczące niebezpiecznych operacji wątkowości.</span><span class="sxs-lookup"><span data-stu-id="6e442-125">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6e442-126">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="6e442-126">Output</span></span>  
 <span data-ttu-id="6e442-127">MDA identyfikuje niebezpieczną metodę wątkowości, która spowodowała jej aktywowanie.</span><span class="sxs-lookup"><span data-stu-id="6e442-127">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6e442-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6e442-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="6e442-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e442-129">Example</span></span>  
 <span data-ttu-id="6e442-130">Poniższy przykład kodu demonstruje wywołanie <xref:System.Threading.Thread.Suspend%2A> metody, która powoduje aktywację `dangerousThreadingAPI` .</span><span class="sxs-lookup"><span data-stu-id="6e442-130">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e442-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e442-131">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="6e442-132">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="6e442-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6e442-133">lock, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e442-133">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
