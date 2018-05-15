---
title: Bariera (.NET Framework)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864571262d1c9c060235840424542856187341df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="barrier-net-framework"></a><span data-ttu-id="1aa9b-102">Bariera (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="1aa9b-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="1aa9b-103">A *bariery* jest zdefiniowane przez użytkownika prymitywu synchronizacji, który umożliwia wiele wątków (nazywane *uczestników*) nad jednocześnie algorytm w fazach.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="1aa9b-104">Uczestnik wykonuje, dopóki nie osiągnie punkt bariery w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="1aa9b-105">Bariera reprezentuje koniec jedną fazą pracy.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="1aa9b-106">Gdy uczestnika osiągnie bariery, blokuje aż do osiągnięcia wszystkich uczestników ma tego samego bariery.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="1aa9b-107">Po wszystkich uczestników osiągnęły bariery, opcjonalnie można wywołać akcję po fazie.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="1aa9b-108">Ta faza po akcja może zostać użyta do wykonania akcji przez pojedynczy wątek, podczas gdy inne wątki nadal są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="1aa9b-109">Po wykonaniu akcji, uczestników są wszystkie odblokowane.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="1aa9b-110">Poniższy fragment kodu przedstawia wzorzec bariery podstawowe.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="1aa9b-111">Pełny przykład, zobacz [porady: synchronizowanie jednoczesnych operacji za pomocą bariery](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="1aa9b-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="1aa9b-112">Dodawanie i usuwanie uczestników</span><span class="sxs-lookup"><span data-stu-id="1aa9b-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="1aa9b-113">Po utworzeniu <xref:System.Threading.Barrier>, określ liczbę uczestników.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="1aa9b-114">Można dodać lub usunąć uczestników dynamicznie w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="1aa9b-115">Na przykład, jeśli jednego uczestnika rozwiązuje jego część problemu, można przechowywać wynik, Zatrzymaj wykonywanie na wątku i Wywołaj <xref:System.Threading.Barrier.RemoveParticipant%2A> Aby zmniejszyć liczbę uczestników bariera.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="1aa9b-116">Po dodaniu uczestnika przez wywołanie metody <xref:System.Threading.Barrier.AddParticipant%2A>, zwracana wartość Określa numer Bieżąca faza, które mogą być przydatne w celu zainicjowania pracy nowego uczestnika.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="1aa9b-117">Przerwane bariery</span><span class="sxs-lookup"><span data-stu-id="1aa9b-117">Broken Barriers</span></span>  
 <span data-ttu-id="1aa9b-118">Zakleszczenie może wystąpić, jeśli jednego uczestnika nie może uzyskać dostęp do zapory.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="1aa9b-119">Aby uniknąć tych zakleszczenia, użyj przeciążeń <xref:System.Threading.Barrier.SignalAndWait%2A> metodę, aby określić limit czasu i token anulowania.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="1aa9b-120">Te zwracane przeciążenia wartość logiczna, która co uczestnika można sprawdzić przed nią nadal do następnej fazy.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="1aa9b-121">Wyjątki po fazie</span><span class="sxs-lookup"><span data-stu-id="1aa9b-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="1aa9b-122">Jeśli delegat po fazie zgłasza wyjątek, jest ujęte w <xref:System.Threading.BarrierPostPhaseException> obiektu, który jest następnie propagowany do wszystkich uczestników.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="1aa9b-123">Bariera i ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="1aa9b-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="1aa9b-124">Bariery są szczególnie przydatne wątków wykonywania faz w pętli.</span><span class="sxs-lookup"><span data-stu-id="1aa9b-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="1aa9b-125">Jeśli kod wymaga tylko jednego lub dwóch faz, należy rozważyć, czy ma być używany <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiekty z dowolnego rodzaju niejawne sprzężenia, w tym:</span><span class="sxs-lookup"><span data-stu-id="1aa9b-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="1aa9b-126">Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="1aa9b-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa9b-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1aa9b-127">See Also</span></span>  
 [<span data-ttu-id="1aa9b-128">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="1aa9b-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="1aa9b-129">Instrukcje: synchronizacja jednoczesnych operacji za pomocą elementu Barrier</span><span class="sxs-lookup"><span data-stu-id="1aa9b-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
