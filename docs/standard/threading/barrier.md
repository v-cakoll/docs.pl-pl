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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 081a4e66462ab546bf4738b4a8b06a4a2ec91a1d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645044"
---
# <a name="barrier"></a><span data-ttu-id="f3336-102">Bariera</span><span class="sxs-lookup"><span data-stu-id="f3336-102">Barrier</span></span>

<span data-ttu-id="f3336-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> jest elementem synchronizacji, który umożliwia wielu wątków (nazywane *uczestników*) pracować jednocześnie na algorytm w fazach.</span><span class="sxs-lookup"><span data-stu-id="f3336-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="f3336-104">Każdy uczestnik wykonuje aż do napotkania punktu barierę w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f3336-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="f3336-105">Bariera oznacza koniec jedną fazą pracy.</span><span class="sxs-lookup"><span data-stu-id="f3336-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="f3336-106">Gdy uczestnika, który osiągnie barierę, blokuje to, aż wszyscy uczestnicy osiągnęły barierę tego samego.</span><span class="sxs-lookup"><span data-stu-id="f3336-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="f3336-107">Po wszystkich uczestników osiągnęły barierę, możesz opcjonalnie wywołać akcję po fazie.</span><span class="sxs-lookup"><span data-stu-id="f3336-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="f3336-108">Tę fazę po okresie akcji może służyć do wykonywania akcji przez pojedynczy wątek, podczas gdy inne wątki nadal są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="f3336-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="f3336-109">Po wykonaniu akcji uczestnicy są wszystkie odblokowane.</span><span class="sxs-lookup"><span data-stu-id="f3336-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="f3336-110">Poniższy fragment kodu przedstawia wzorzec barierę podstawowe.</span><span class="sxs-lookup"><span data-stu-id="f3336-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="f3336-111">Aby uzyskać kompletny przykład, zobacz [porady: synchronizacja jednoczesnych operacji za pomocą bariery](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="f3336-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="f3336-112">Dodawanie i usuwanie uczestników</span><span class="sxs-lookup"><span data-stu-id="f3336-112">Adding and removing participants</span></span>

 <span data-ttu-id="f3336-113">Po utworzeniu <xref:System.Threading.Barrier> wystąpienie, określ liczbę uczestników.</span><span class="sxs-lookup"><span data-stu-id="f3336-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="f3336-114">Można dodawać lub usuwać uczestników dynamicznie w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="f3336-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="f3336-115">Na przykład, jeśli jeden uczestnik rozwiązuje jego część problemu, możesz zapisać wynik, Zatrzymaj wykonywanie na wątku, a następnie wywołaj <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> zmniejszyć liczbę uczestników barierę.</span><span class="sxs-lookup"><span data-stu-id="f3336-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="f3336-116">Po dodaniu uczestnikiem, wywołując <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, wartość zwracana określa numer Bieżąca faza, który może być przydatne w celu zainicjowania pracy nowych uczestników.</span><span class="sxs-lookup"><span data-stu-id="f3336-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="f3336-117">Przerwane bariery</span><span class="sxs-lookup"><span data-stu-id="f3336-117">Broken barriers</span></span>

 <span data-ttu-id="f3336-118">Zakleszczenie może wystąpić, jeśli jednego uczestnika nie uda się połączyć do zapory.</span><span class="sxs-lookup"><span data-stu-id="f3336-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="f3336-119">Aby uniknąć tych zakleszczenia, użyj przeciążeń <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> metodę, aby określić limit czasu i token anulowania.</span><span class="sxs-lookup"><span data-stu-id="f3336-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="f3336-120">Te przeciążenia, które są zwracane wartość logiczną, każdy uczestnik można sprawdzić przed dalszym przeprowadzenia kolejnej fazy.</span><span class="sxs-lookup"><span data-stu-id="f3336-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="f3336-121">Wyjątki po fazie</span><span class="sxs-lookup"><span data-stu-id="f3336-121">Post-phase exceptions</span></span>

 <span data-ttu-id="f3336-122">Jeśli delegat po fazie zgłasza wyjątek, jest opakowana w <xref:System.Threading.BarrierPostPhaseException> obiektu, który jest następnie propagowany do wszystkich uczestników.</span><span class="sxs-lookup"><span data-stu-id="f3336-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="f3336-123">Zapory i ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="f3336-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="f3336-124">Bariery są szczególnie przydatne podczas wykonywania wielu faz wątki w pętli.</span><span class="sxs-lookup"><span data-stu-id="f3336-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="f3336-125">Jeśli kod wymaga tylko jednego lub dwóch faz, rozważ użycie <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiekty z dowolnego rodzaju niejawne łączenia, w tym:</span><span class="sxs-lookup"><span data-stu-id="f3336-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f3336-126">Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="f3336-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3336-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3336-127">See also</span></span>

- [<span data-ttu-id="f3336-128">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="f3336-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="f3336-129">Porady: synchronizacja jednoczesnych operacji za pomocą bariery</span><span class="sxs-lookup"><span data-stu-id="f3336-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
