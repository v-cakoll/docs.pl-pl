---
title: Bariera
ms.date: 09/14/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
ms.openlocfilehash: 5aa34f7f39f4b9b626bea29372cf984f3cefb361
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138147"
---
# <a name="barrier"></a><span data-ttu-id="72525-102">Bariera</span><span class="sxs-lookup"><span data-stu-id="72525-102">Barrier</span></span>

<span data-ttu-id="72525-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> jest prymitywem synchronizacji, który umożliwia wiele wątków (znany jako *uczestnicy)* do pracy jednocześnie na algorytm w fazach.</span><span class="sxs-lookup"><span data-stu-id="72525-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="72525-104">Każdy uczestnik wykonuje, dopóki nie osiągnie punkt bariery w kodzie.</span><span class="sxs-lookup"><span data-stu-id="72525-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="72525-105">Bariera stanowi koniec jednego etapu prac.</span><span class="sxs-lookup"><span data-stu-id="72525-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="72525-106">Gdy uczestnik osiągnie barierę, blokuje się, aż wszyscy uczestnicy osiągną tę samą barierę.</span><span class="sxs-lookup"><span data-stu-id="72525-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="72525-107">Po osiągnięciu bariery wszyscy uczestnicy mogą opcjonalnie wywołać akcję pofazie.</span><span class="sxs-lookup"><span data-stu-id="72525-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="72525-108">Ta akcja po fazie może służyć do wykonywania akcji przez jeden wątek, podczas gdy wszystkie inne wątki są nadal blokowane.</span><span class="sxs-lookup"><span data-stu-id="72525-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="72525-109">Po wykonaniu akcji wszyscy uczestnicy zostają odblokowani.</span><span class="sxs-lookup"><span data-stu-id="72525-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="72525-110">Poniższy fragment kodu pokazuje podstawowy wzorzec bariery.</span><span class="sxs-lookup"><span data-stu-id="72525-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="72525-111">Aby uzyskać pełny przykład, zobacz [Jak: synchronizować równoczesnych operacji z barierą](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="72525-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="72525-112">Dodawanie i usuwanie uczestników</span><span class="sxs-lookup"><span data-stu-id="72525-112">Adding and removing participants</span></span>

 <span data-ttu-id="72525-113">Podczas tworzenia <xref:System.Threading.Barrier> wystąpienia określ liczbę uczestników.</span><span class="sxs-lookup"><span data-stu-id="72525-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="72525-114">W dowolnym momencie można również dynamicznie dodawać lub usuwać uczestników.</span><span class="sxs-lookup"><span data-stu-id="72525-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="72525-115">Na przykład jeśli jeden uczestnik rozwiązuje jego część problemu, można przechowywać wynik, zatrzymać <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> wykonanie w tym wątku i wywołać, aby zdeterminować liczbę uczestników w barierze.</span><span class="sxs-lookup"><span data-stu-id="72525-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="72525-116">Po dodaniu uczestnika <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>przez wywołanie , wartość zwracana określa bieżący numer fazy, co może być przydatne w celu zainicjowania pracy nowego uczestnika.</span><span class="sxs-lookup"><span data-stu-id="72525-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="72525-117">Złamane bariery</span><span class="sxs-lookup"><span data-stu-id="72525-117">Broken barriers</span></span>

 <span data-ttu-id="72525-118">Zakleszczenia mogą wystąpić, jeśli jeden uczestnik nie osiągnie bariery.</span><span class="sxs-lookup"><span data-stu-id="72525-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="72525-119">Aby uniknąć tych zakleszczeń, należy <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> użyć przeciążenia metody, aby określić okres przekroczenia czasu i token anulowania.</span><span class="sxs-lookup"><span data-stu-id="72525-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="72525-120">Te przeciążenia zwracają wartość logiczną, którą każdy uczestnik może sprawdzić, zanim przejdzie do następnej fazy.</span><span class="sxs-lookup"><span data-stu-id="72525-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="72525-121">Wyjątki pofazie</span><span class="sxs-lookup"><span data-stu-id="72525-121">Post-phase exceptions</span></span>

 <span data-ttu-id="72525-122">Jeśli delegat po fazie zgłasza wyjątek, jest opakowany <xref:System.Threading.BarrierPostPhaseException> w obiekt, który jest następnie propagowane do wszystkich uczestników.</span><span class="sxs-lookup"><span data-stu-id="72525-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="72525-123">Bariera kontra ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="72525-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="72525-124">Bariery są szczególnie przydatne, gdy wątki wykonują wiele faz w pętlach.</span><span class="sxs-lookup"><span data-stu-id="72525-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="72525-125">Jeśli kod wymaga tylko jednej lub dwóch faz pracy, należy rozważyć, czy używać <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów z wszelkiego rodzaju niejawne sprzężenia, w tym:</span><span class="sxs-lookup"><span data-stu-id="72525-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="72525-126">Aby uzyskać więcej informacji, zobacz [Łączenie zadań przy użyciu zadań kontynuacji](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="72525-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72525-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72525-127">See also</span></span>

- [<span data-ttu-id="72525-128">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="72525-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="72525-129">Jak: synchronizować równoczesne operacje z barierą</span><span class="sxs-lookup"><span data-stu-id="72525-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
