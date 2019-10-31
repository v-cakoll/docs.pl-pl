---
title: Współdziałanie z innymi wzorcami asynchronicznymi i typami
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: f9fe33bb46f0ba78756c4172032dfbaf45d6fc89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123979"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="98f79-102">Współdziałanie z innymi wzorcami asynchronicznymi i typami</span><span class="sxs-lookup"><span data-stu-id="98f79-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="98f79-103">W .NET Framework 1,0 wprowadzono wzorzec <xref:System.IAsyncResult>, w przeciwnym razie znany jako [asynchroniczny model programowania (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)lub wzorzec `Begin/End`.</span><span class="sxs-lookup"><span data-stu-id="98f79-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="98f79-104">.NET Framework 2,0 został dodany [wzorzec asynchroniczny oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="98f79-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="98f79-105">Począwszy od .NET Framework 4, [wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) zastępuje zarówno APM, jak i EAP, ale umożliwia łatwe tworzenie procedur migracji z wcześniejszych wzorców.</span><span class="sxs-lookup"><span data-stu-id="98f79-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="98f79-106">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="98f79-106">In this topic:</span></span>  
  
- <span data-ttu-id="98f79-107">[Zadania i APM](#APM) ([z poziomu APM do TAP](#ApmToTap) lub [z TAP do APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="98f79-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
- [<span data-ttu-id="98f79-108">Zadania i protokół EAP</span><span class="sxs-lookup"><span data-stu-id="98f79-108">Tasks and EAP</span></span>](#EAP)  
  
- <span data-ttu-id="98f79-109">[Zadania i uchwyty oczekiwania](#WaitHandles) ([od dojścia oczekiwania do naciśnięcia](#WHToTap) lub [od naciśnij do uchwytów](#TapToWH)oczekiwania)</span><span class="sxs-lookup"><span data-stu-id="98f79-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="98f79-110">Zadania i model programowania asynchronicznego (APM)</span><span class="sxs-lookup"><span data-stu-id="98f79-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="98f79-111">Z usługi APM do NACIŚNIĘCIa</span><span class="sxs-lookup"><span data-stu-id="98f79-111">From APM to TAP</span></span>  
 <span data-ttu-id="98f79-112">Ze względu na to, że wzorzec [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) jest bardzo strukturalny, można łatwo utworzyć otokę, aby uwidocznić implementację APM jako implementację TAP.</span><span class="sxs-lookup"><span data-stu-id="98f79-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="98f79-113">W rzeczywistości .NET Framework, zaczynając od .NET Framework 4, zawiera procedury pomocnika w postaci przeciążeń metody <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> w celu zapewnienia tego tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="98f79-113">In fact, the .NET Framework, starting with .NET Framework 4, includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="98f79-114">Rozważmy klasę <xref:System.IO.Stream> i jej <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A> metody reprezentujące odpowiedniki APM do synchronicznej metody <xref:System.IO.Stream.Read%2A>:</span><span class="sxs-lookup"><span data-stu-id="98f79-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="98f79-115">Za pomocą metody <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> można zaimplementować otokę TAP dla tej operacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="98f79-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="98f79-116">Ta implementacja jest podobna do następującej:</span><span class="sxs-lookup"><span data-stu-id="98f79-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="98f79-117">Od TAP do APM</span><span class="sxs-lookup"><span data-stu-id="98f79-117">From TAP to APM</span></span>  
 <span data-ttu-id="98f79-118">Jeśli istniejąca infrastruktura oczekuje wzorca APM, należy również wykonać implementację TAP i użyć jej, w której oczekiwana jest implementacja APM.</span><span class="sxs-lookup"><span data-stu-id="98f79-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="98f79-119">Ponieważ zadania mogą być złożone, a Klasa <xref:System.Threading.Tasks.Task> implementuje <xref:System.IAsyncResult>, można użyć prostej funkcji pomocnika.</span><span class="sxs-lookup"><span data-stu-id="98f79-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="98f79-120">Poniższy kod używa rozszerzenia klasy <xref:System.Threading.Tasks.Task%601>, ale można użyć prawie identycznej funkcji dla zadań innych niż ogólne.</span><span class="sxs-lookup"><span data-stu-id="98f79-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="98f79-121">Teraz Rozważmy przypadek, w którym masz następującą implementację TAP:</span><span class="sxs-lookup"><span data-stu-id="98f79-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="98f79-122">i chcesz zapewnić tę implementację APM:</span><span class="sxs-lookup"><span data-stu-id="98f79-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="98f79-123">Poniższy przykład ilustruje jedną migrację do APM:</span><span class="sxs-lookup"><span data-stu-id="98f79-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="98f79-124">Zadania i wzorzec asynchroniczny oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="98f79-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="98f79-125">Otoka implementacji [wzorca asynchronicznego opartego na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) jest większa niż otoka wzorca APM, ponieważ wzorzec protokołu EAP ma większą odmianę i mniejszą strukturę niż wzorzec APM.</span><span class="sxs-lookup"><span data-stu-id="98f79-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="98f79-126">Aby przedstawić, poniższy kod otacza metodę `DownloadStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="98f79-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="98f79-127">`DownloadStringAsync` akceptuje identyfikator URI, wywołuje zdarzenie `DownloadProgressChanged` podczas pobierania, aby raportować wiele statystyk w toku i wywołuje zdarzenie `DownloadStringCompleted` po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="98f79-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="98f79-128">Końcowy wynik jest ciągiem zawierającym zawartość strony o określonym identyfikatorze URI.</span><span class="sxs-lookup"><span data-stu-id="98f79-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="98f79-129">Zadania i uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="98f79-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="98f79-130">Z uchwytów oczekiwania na NACIŚNIĘCIe</span><span class="sxs-lookup"><span data-stu-id="98f79-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="98f79-131">Chociaż uchwyty oczekiwania nie implementują wzorca asynchronicznego, zaawansowani deweloperzy mogą używać klasy <xref:System.Threading.WaitHandle> i metody <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> na potrzeby powiadomień asynchronicznych po ustawieniu dojścia oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="98f79-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="98f79-132">Możesz zawinąć metodę <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A>, aby włączyć alternatywną dla zadań funkcję dla dowolnego synchronicznego oczekiwania na dojście oczekiwania:</span><span class="sxs-lookup"><span data-stu-id="98f79-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="98f79-133">Za pomocą tej metody można używać istniejących implementacji <xref:System.Threading.WaitHandle> w metodach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="98f79-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="98f79-134">Na przykład jeśli chcesz ograniczyć liczbę operacji asynchronicznych wykonywanych w dowolnym określonym czasie, możesz użyć semafora (<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> obiektu).</span><span class="sxs-lookup"><span data-stu-id="98f79-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="98f79-135">Można ograniczyć do *n* liczbę operacji, które są uruchamiane współbieżnie, inicjując liczbę semaforów na *n*, czekając na semafor w dowolnym momencie, gdy chcesz wykonać operację, i zwolnij semafor po wykonaniu operacji:</span><span class="sxs-lookup"><span data-stu-id="98f79-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="98f79-136">Można również utworzyć semafor asynchroniczny, który nie bazuje na dojściach oczekiwania i zamiast tego działa całkowicie z zadaniami.</span><span class="sxs-lookup"><span data-stu-id="98f79-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="98f79-137">Aby to zrobić, można użyć technik takich jak omówione w temacie [konsumowanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) w celu kompilowania struktur danych na <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="98f79-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="98f79-138">Od NACIŚNIĘCIa do uchwytów oczekiwania</span><span class="sxs-lookup"><span data-stu-id="98f79-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="98f79-139">Jak wspomniano wcześniej, Klasa <xref:System.Threading.Tasks.Task> implementuje <xref:System.IAsyncResult>, a ta implementacja ujawnia Właściwość <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A>, która zwraca dojście oczekiwania, który zostanie ustawiony po zakończeniu <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="98f79-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="98f79-140"><xref:System.Threading.WaitHandle> <xref:System.Threading.Tasks.Task> można uzyskać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="98f79-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="98f79-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98f79-141">See also</span></span>

- [<span data-ttu-id="98f79-142">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="98f79-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="98f79-143">Implementowanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="98f79-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="98f79-144">Wykorzystywanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="98f79-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
