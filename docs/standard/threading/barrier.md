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
ms.openlocfilehash: 385e370f205851630f809b285a93c2609220efeb
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137112"
---
# <a name="barrier-net-framework"></a><span data-ttu-id="1bba7-102">Bariera (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="1bba7-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="1bba7-103">A *barierę* jest zdefiniowane przez użytkownika synchronizacji, który umożliwia wielu wątków (nazywane *uczestników*) pracować jednocześnie na algorytm w fazach.</span><span class="sxs-lookup"><span data-stu-id="1bba7-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="1bba7-104">Każdy uczestnik wykonuje aż do napotkania punktu barierę w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1bba7-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="1bba7-105">Bariera oznacza koniec jedną fazą pracy.</span><span class="sxs-lookup"><span data-stu-id="1bba7-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="1bba7-106">Gdy uczestnika, który osiągnie barierę, blokuje to, aż wszyscy uczestnicy osiągnęły barierę tego samego.</span><span class="sxs-lookup"><span data-stu-id="1bba7-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="1bba7-107">Po wszystkich uczestników osiągnęły barierę, możesz opcjonalnie wywołać akcję po fazie.</span><span class="sxs-lookup"><span data-stu-id="1bba7-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="1bba7-108">Tę fazę po okresie akcji może służyć do wykonywania akcji przez pojedynczy wątek, podczas gdy inne wątki nadal są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="1bba7-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="1bba7-109">Po wykonaniu akcji uczestnicy są wszystkie odblokowane.</span><span class="sxs-lookup"><span data-stu-id="1bba7-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="1bba7-110">Poniższy fragment kodu przedstawia wzorzec barierę podstawowe.</span><span class="sxs-lookup"><span data-stu-id="1bba7-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="1bba7-111">Aby uzyskać kompletny przykład, zobacz [porady: synchronizowanie jednoczesnych operacji za pomocą bariery](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="1bba7-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="1bba7-112">Dodawanie i usuwanie uczestników</span><span class="sxs-lookup"><span data-stu-id="1bba7-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="1bba7-113">Po utworzeniu <xref:System.Threading.Barrier>, określ liczbę uczestników.</span><span class="sxs-lookup"><span data-stu-id="1bba7-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="1bba7-114">Można dodawać lub usuwać uczestników dynamicznie w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="1bba7-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="1bba7-115">Na przykład, jeśli jeden uczestnik rozwiązuje jego część problemu, możesz zapisać wynik, Zatrzymaj wykonywanie na wątku, a następnie wywołaj <xref:System.Threading.Barrier.RemoveParticipant%2A> zmniejszyć liczbę uczestników barierę.</span><span class="sxs-lookup"><span data-stu-id="1bba7-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="1bba7-116">Po dodaniu uczestnikiem, wywołując <xref:System.Threading.Barrier.AddParticipant%2A>, wartość zwracana określa numer Bieżąca faza, który może być przydatne w celu zainicjowania pracy nowych uczestników.</span><span class="sxs-lookup"><span data-stu-id="1bba7-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="1bba7-117">Przerwane bariery</span><span class="sxs-lookup"><span data-stu-id="1bba7-117">Broken Barriers</span></span>  
 <span data-ttu-id="1bba7-118">Zakleszczenie może wystąpić, jeśli jednego uczestnika nie uda się połączyć do zapory.</span><span class="sxs-lookup"><span data-stu-id="1bba7-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="1bba7-119">Aby uniknąć tych zakleszczenia, użyj przeciążeń <xref:System.Threading.Barrier.SignalAndWait%2A> metodę, aby określić limit czasu i token anulowania.</span><span class="sxs-lookup"><span data-stu-id="1bba7-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="1bba7-120">Te przeciążenia, które są zwracane wartość logiczną, każdy uczestnik można sprawdzić przed dalszym przeprowadzenia kolejnej fazy.</span><span class="sxs-lookup"><span data-stu-id="1bba7-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="1bba7-121">Wyjątki po fazie</span><span class="sxs-lookup"><span data-stu-id="1bba7-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="1bba7-122">Jeśli delegat po fazie zgłasza wyjątek, jest opakowana w <xref:System.Threading.BarrierPostPhaseException> obiektu, który jest następnie propagowany do wszystkich uczestników.</span><span class="sxs-lookup"><span data-stu-id="1bba7-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="1bba7-123">Zapory i ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="1bba7-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="1bba7-124">Bariery są szczególnie przydatne podczas wykonywania wielu faz wątki w pętli.</span><span class="sxs-lookup"><span data-stu-id="1bba7-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="1bba7-125">Jeśli kod wymaga tylko jednego lub dwóch faz, rozważ użycie <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiekty z dowolnego rodzaju niejawne łączenia, w tym:</span><span class="sxs-lookup"><span data-stu-id="1bba7-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="1bba7-126">Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="1bba7-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bba7-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bba7-127">See also</span></span>

- [<span data-ttu-id="1bba7-128">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="1bba7-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="1bba7-129">Instrukcje: synchronizacja jednoczesnych operacji za pomocą elementu Barrier</span><span class="sxs-lookup"><span data-stu-id="1bba7-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
