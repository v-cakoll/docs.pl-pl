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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05b53016712f75e45636979d77bfd27116ce8e14
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44510067"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="dc800-102">Współdziałanie z innymi wzorcami asynchronicznymi i typami</span><span class="sxs-lookup"><span data-stu-id="dc800-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="dc800-103">.NET Framework 1.0, wprowadzono <xref:System.IAsyncResult> wzorzec, znanych także jako [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), lub `Begin/End` wzorca.</span><span class="sxs-lookup"><span data-stu-id="dc800-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="dc800-104">.NET Framework 2.0, dodano [oparte na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="dc800-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="dc800-105">Począwszy od programu .NET Framework 4, [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) zastępuje zarówno APM, jak i EAP, ale pozwala na łatwe tworzenie procedury migracji z wcześniejszych wzorców.</span><span class="sxs-lookup"><span data-stu-id="dc800-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="dc800-106">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="dc800-106">In this topic:</span></span>  
  
-   <span data-ttu-id="dc800-107">[Zadania i APM](#APM) ([z APM do wzorca TAP](#ApmToTap) lub [z NACIŚNIJ, aby APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="dc800-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
-   [<span data-ttu-id="dc800-108">Zadania i protokołu EAP</span><span class="sxs-lookup"><span data-stu-id="dc800-108">Tasks and EAP</span></span>](#EAP)  
  
-   <span data-ttu-id="dc800-109">[Zadania i uchwyty oczekiwania](#WaitHandles) ([z uchwytami oczekiwania do wzorca TAP](#WHToTap) lub [z NACIŚNIJ, aby uchwyty oczekiwania](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="dc800-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="dc800-110">Zadania i Model programowania asynchronicznego (APM)</span><span class="sxs-lookup"><span data-stu-id="dc800-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="dc800-111">Z APM do wzorca TAP</span><span class="sxs-lookup"><span data-stu-id="dc800-111">From APM to TAP</span></span>  
 <span data-ttu-id="dc800-112">Ponieważ [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) wzorzec jest bardzo ze strukturą, tworzenie otoki, aby udostępnić implementację APM jako implementacja wzorca TAP jest bardzo łatwe.</span><span class="sxs-lookup"><span data-stu-id="dc800-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="dc800-113">W rzeczywistości, .NET Framework, począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obejmuje procedury pomocnika w formie <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> przeciążenia metody, aby zapewnić to tłumaczenie.</span><span class="sxs-lookup"><span data-stu-id="dc800-113">In fact, the .NET Framework, starting with [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="dc800-114">Należy wziąć pod uwagę <xref:System.IO.Stream> klasy i jego <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A> metody, które reprezentują synchronicznego odpowiednika APM <xref:System.IO.Stream.Read%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="dc800-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="dc800-115">Możesz użyć <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody do zaimplementowania wzorca TAP otokę dla tej operacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dc800-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="dc800-116">Ta implementacja jest podobna do następującej:</span><span class="sxs-lookup"><span data-stu-id="dc800-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="dc800-117">Z NACIŚNIJ, aby APM</span><span class="sxs-lookup"><span data-stu-id="dc800-117">From TAP to APM</span></span>  
 <span data-ttu-id="dc800-118">Jeśli istniejącej infrastruktury oczekuje wzorzec APM, również należy podjąć implementacja wzorca TAP i używać go, których oczekuje się implementację APM.</span><span class="sxs-lookup"><span data-stu-id="dc800-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="dc800-119">Ponieważ zadania mogą być składane i <xref:System.Threading.Tasks.Task> klasy implementuje <xref:System.IAsyncResult>, można użyć funkcji pomocnika proste, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="dc800-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="dc800-120">W poniższym kodzie użyto rozszerzenie <xref:System.Threading.Tasks.Task%601> klasy, ale można użyć funkcji niemal identyczne dla zadań innych niż ogólne.</span><span class="sxs-lookup"><span data-stu-id="dc800-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="dc800-121">Rozważmy przypadek, w którym masz następujące implementacja wzorca TAP:</span><span class="sxs-lookup"><span data-stu-id="dc800-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="dc800-122">i chcesz udostępnić tę implementację APM:</span><span class="sxs-lookup"><span data-stu-id="dc800-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="dc800-123">Poniższy przykład przedstawia jedną migrację do APM:</span><span class="sxs-lookup"><span data-stu-id="dc800-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="dc800-124">Zadania i oparte na zdarzeniach wzorca asynchronicznego (EAP)</span><span class="sxs-lookup"><span data-stu-id="dc800-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="dc800-125">Zawijanie [oparte na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementacja jest bardziej skomplikowane niż zawijania wzorzec APM, ponieważ wzorzec EAP ma więcej zmian i struktury, mniej niż wzorzec APM.</span><span class="sxs-lookup"><span data-stu-id="dc800-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="dc800-126">Aby zademonstrować, poniższy kod jest zawijany `DownloadStringAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="dc800-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="dc800-127">`DownloadStringAsync` akceptuje identyfikator URI, zgłasza `DownloadProgressChanged` zdarzenia podczas pobierania, aby wiele statystyki sporządzić raport na temat postępu i zgłasza `DownloadStringCompleted` zdarzenie, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="dc800-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="dc800-128">Wynik końcowy to ciąg, który zawiera zawartość strony o określonym identyfikatorze URI.</span><span class="sxs-lookup"><span data-stu-id="dc800-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="dc800-129">Zadania i uchwytami oczekiwania</span><span class="sxs-lookup"><span data-stu-id="dc800-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="dc800-130">Z uchwytami oczekiwania do wzorca TAP</span><span class="sxs-lookup"><span data-stu-id="dc800-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="dc800-131">Mimo że uchwyty oczekiwania na nie implementuje wzorca asynchronicznego, zaawansowane deweloperzy mogą użyć <xref:System.Threading.WaitHandle> klasy i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metodę dla powiadomień asynchronicznych, gdy ustawiono dojście oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="dc800-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="dc800-132">Można opakować <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> metodę, aby włączyć zadanie alternatywa wszelkie synchroniczne oczekiwanie na dojście oczekiwania:</span><span class="sxs-lookup"><span data-stu-id="dc800-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="dc800-133">Przy użyciu tej metody można użyć istniejącej <xref:System.Threading.WaitHandle> implementacje metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="dc800-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="dc800-134">Na przykład, jeśli chcesz ograniczyć liczbę operacji asynchronicznych, które są wykonywane w danym momencie, możesz użyć semafor ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> obiektu).</span><span class="sxs-lookup"><span data-stu-id="dc800-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="dc800-135">Możesz ograniczyć do *N* liczby operacji działać współbieżnie przez inicjowania semafora count *N*, trwa oczekiwanie na semafora w dowolnym momencie, którą chcesz wykonać operację i zwolnieniem Semafor po zakończeniu operacji:</span><span class="sxs-lookup"><span data-stu-id="dc800-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="dc800-136">Można także utworzyć semafora asynchronicznego, nie zależą od uchwytami oczekiwania, która działa w całkowicie z zadaniami.</span><span class="sxs-lookup"><span data-stu-id="dc800-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="dc800-137">Aby to zrobić, należy użyć technik, takich jak omawiany w [wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) do tworzenia struktur danych, w górnej części <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="dc800-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="dc800-138">Z NACIŚNIJ, aby uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="dc800-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="dc800-139">Jak wcześniej wspomniano, <xref:System.Threading.Tasks.Task> klasy implementuje <xref:System.IAsyncResult>, i udostępnia tę implementację <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> właściwość, która zwraca dojście oczekiwania, który będzie można ustawić podczas <xref:System.Threading.Tasks.Task> kończy.</span><span class="sxs-lookup"><span data-stu-id="dc800-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="dc800-140">Możesz uzyskać <xref:System.Threading.WaitHandle> dla <xref:System.Threading.Tasks.Task> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dc800-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="dc800-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc800-141">See also</span></span>

- [<span data-ttu-id="dc800-142">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="dc800-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
- [<span data-ttu-id="dc800-143">Implementowanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="dc800-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
- [<span data-ttu-id="dc800-144">Wykorzystywanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="dc800-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
