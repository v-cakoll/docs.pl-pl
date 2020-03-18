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
ms.openlocfilehash: 981c13c68eaf1eb0c19f95eb1b097935ea02a16d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159757"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="44764-102">Współdziałanie z innymi wzorcami asynchronicznymi i typami</span><span class="sxs-lookup"><span data-stu-id="44764-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="44764-103">.NET Framework 1.0 <xref:System.IAsyncResult> wprowadzono wzorzec, inaczej znany jako [Asynchroniczny model programowania (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)lub `Begin/End` wzorzec.</span><span class="sxs-lookup"><span data-stu-id="44764-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="44764-104">Program .NET Framework 2.0 dodał [wzorca asynchronicznego opartego na zdarzeniach (EAP).](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)</span><span class="sxs-lookup"><span data-stu-id="44764-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="44764-105">Począwszy od .NET Framework 4, [oparty na zadaniach wzorzec asynchroniczny (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) zastępuje zarówno APM, jak i EAP, ale zapewnia możliwość łatwego tworzenia procedur migracji z wcześniejszych wzorców.</span><span class="sxs-lookup"><span data-stu-id="44764-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="44764-106">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="44764-106">In this topic:</span></span>  
  
- <span data-ttu-id="44764-107">[Zadania i APM](#APM) ([od APM do TAP](#ApmToTap) lub z TAP do [APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="44764-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
- [<span data-ttu-id="44764-108">Zadania i EAP</span><span class="sxs-lookup"><span data-stu-id="44764-108">Tasks and EAP</span></span>](#EAP)  
  
- <span data-ttu-id="44764-109">[Zadania i uchwyty oczekiwania](#WaitHandles) [(od uchwytów oczekiwania do tap](#WHToTap) lub z [TAP, aby czekać uchwyty](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="44764-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="44764-110">Zadania i asynchroniczny model programowania (APM)</span><span class="sxs-lookup"><span data-stu-id="44764-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a><span data-ttu-id="44764-111">Z APM do TAP</span><span class="sxs-lookup"><span data-stu-id="44764-111">From APM to TAP</span></span>  
 <span data-ttu-id="44764-112">Ponieważ [wzorzec asynchronicznego modelu programowania (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) jest bardzo zorganizowany, dość łatwo jest utworzyć otokę, aby udostępnić implementację APM jako implementację TAP.</span><span class="sxs-lookup"><span data-stu-id="44764-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="44764-113">W rzeczywistości .NET Framework, począwszy od .NET Framework 4, zawiera <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> procedury pomocnika w postaci przeciążenia metody, aby zapewnić to tłumaczenie.</span><span class="sxs-lookup"><span data-stu-id="44764-113">In fact, the .NET Framework, starting with .NET Framework 4, includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="44764-114">Należy <xref:System.IO.Stream> wziąć pod <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> uwagę klasę i jej metody, które reprezentują <xref:System.IO.Stream.Read%2A> odpowiednik APM do metody synchronicznej:</span><span class="sxs-lookup"><span data-stu-id="44764-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="44764-115"><xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> Metoda ta służy do implementowania otoki TAP dla tej operacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="44764-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="44764-116">Ta implementacja jest podobna do następującej:</span><span class="sxs-lookup"><span data-stu-id="44764-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a><span data-ttu-id="44764-117">Od TAP do APM</span><span class="sxs-lookup"><span data-stu-id="44764-117">From TAP to APM</span></span>  
 <span data-ttu-id="44764-118">Jeśli istniejąca infrastruktura oczekuje wzorca APM, należy również podjąć implementacji TAP i używać go tam, gdzie oczekuje się implementacji apm.</span><span class="sxs-lookup"><span data-stu-id="44764-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="44764-119">Ponieważ zadania mogą być <xref:System.Threading.Tasks.Task> składane <xref:System.IAsyncResult>i implementuje klasy , można użyć funkcji pomocnika proste, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="44764-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="44764-120">Poniższy kod używa rozszerzenia <xref:System.Threading.Tasks.Task%601> klasy, ale można użyć prawie identyczną funkcję dla zadań nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="44764-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="44764-121">Teraz rozważ przypadek, w którym masz następującą implementację TAP:</span><span class="sxs-lookup"><span data-stu-id="44764-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="44764-122">i chcesz zapewnić tę implementację APM:</span><span class="sxs-lookup"><span data-stu-id="44764-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="44764-123">W poniższym przykładzie przedstawiono jedną migrację do apm:</span><span class="sxs-lookup"><span data-stu-id="44764-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="44764-124">Zadania i wzorzec asynchroniczny oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="44764-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="44764-125">Zawijanie implementacji [wzorca asynchronicznego (EAP) opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) jest bardziej zaangażowane niż zawijanie wzorca APM, ponieważ wzorzec EAP ma większą zmienność i mniejszą strukturę niż wzorzec APM.</span><span class="sxs-lookup"><span data-stu-id="44764-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="44764-126">Aby zademonstrować, poniższy `DownloadStringAsync` kod otacza metodę.</span><span class="sxs-lookup"><span data-stu-id="44764-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="44764-127">`DownloadStringAsync`akceptuje identyfikator URI, `DownloadProgressChanged` wywołuje zdarzenie podczas pobierania w celu raportowania wielu `DownloadStringCompleted` statystyk dotyczących postępu i wywołuje zdarzenie po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="44764-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="44764-128">Wynik końcowy jest ciągiem zawierającym zawartość strony przy określonym identyfikatorze URI.</span><span class="sxs-lookup"><span data-stu-id="44764-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="44764-129">Zadania i uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="44764-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="44764-130">Od uchwytów oczekiwania do tap</span><span class="sxs-lookup"><span data-stu-id="44764-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="44764-131">Mimo że dojścia oczekiwania nie implementują wzorca <xref:System.Threading.WaitHandle> asynchronicznego, zaawansowani deweloperzy mogą używać klasy i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody powiadomień asynchronicznych po ustawieniu dojścia oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="44764-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="44764-132">Można zawinąć metodę, <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> aby włączyć alternatywę dla dowolnego synchronicznego oczekiwania na dojście oczekiwania:</span><span class="sxs-lookup"><span data-stu-id="44764-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="44764-133">Za pomocą tej metody <xref:System.Threading.WaitHandle> można użyć istniejących implementacji w metodach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="44764-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="44764-134">Na przykład jeśli chcesz ograniczyć liczbę operacji asynchronicznych, które są wykonywane w danym momencie, można wykorzystać semafora <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> (obiekt).</span><span class="sxs-lookup"><span data-stu-id="44764-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="44764-135">Można ograniczyć do *N* liczbę operacji, które są uruchamiane jednocześnie, inicjując liczbę semafora do *N,* czekając na semafora w dowolnym momencie, gdy chcesz wykonać operację, i zwalniając semafor po zakończeniu operacji:</span><span class="sxs-lookup"><span data-stu-id="44764-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="44764-136">Można również utworzyć asynchroniczny semafor, który nie opiera się na uchwyty oczekiwania i zamiast tego działa całkowicie z zadaniami.</span><span class="sxs-lookup"><span data-stu-id="44764-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="44764-137">Aby to zrobić, można użyć technik, takich jak te omówione w [Korzystanie z wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) do tworzenia struktur danych na wierzchu <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="44764-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="44764-138">Od TAP do uchwytów oczekiwania</span><span class="sxs-lookup"><span data-stu-id="44764-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="44764-139">Jak wcześniej wspomniano, <xref:System.Threading.Tasks.Task> implementuje <xref:System.IAsyncResult>klasy , a <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> implementacja udostępnia właściwość, która zwraca <xref:System.Threading.Tasks.Task> dojście oczekiwania, który zostanie ustawiony po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="44764-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="44764-140">Możesz otrzymać <xref:System.Threading.WaitHandle> for <xref:System.Threading.Tasks.Task> a w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="44764-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="44764-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44764-141">See also</span></span>

- [<span data-ttu-id="44764-142">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="44764-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="44764-143">Implementacja wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="44764-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="44764-144">Wykorzystywanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="44764-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
