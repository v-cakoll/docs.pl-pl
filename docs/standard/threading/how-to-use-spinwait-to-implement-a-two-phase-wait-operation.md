---
title: 'Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="d1ff8-102">Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania</span><span class="sxs-lookup"><span data-stu-id="d1ff8-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="d1ff8-103">Poniższy przykład przedstawia użycie <xref:System.Threading.SpinWait?displayProperty=nameWithType> obiektu do implementacji dwufazowej operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="d1ff8-104">W pierwszej fazie obiektu synchronizacji `Latch`, obraca przez kilka cykli podczas sprawdza, czy blokada stał się dostępny.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="d1ff8-105">W drugim etapie, jeśli blokada staje się dostępny a następnie `Wait` metoda zwraca bez użycia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> przeprowadzić jego oczekiwania; w przeciwnym razie `Wait` wykonuje czas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1ff8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1ff8-106">Example</span></span>  
 <span data-ttu-id="d1ff8-107">Ten przykład przedstawia bardzo proste implementacja synchronizacji zatrzaśnięcia pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="d1ff8-108">Można użyć tej struktury danych, gdy powinny być bardzo krótki czas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="d1ff8-109">W tym przykładzie jest tylko w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="d1ff8-110">Jeśli potrzebujesz zatrzaśnięcia typu funkcji w programie, należy rozważyć użycie <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="d1ff8-111">Używa zatrzaśnięcia <xref:System.Threading.SpinWait> obiektu się w miejscu tylko do następnego wywołania `SpinOnce` powoduje, że <xref:System.Threading.SpinWait> umożliwiające uzyskanie przedział czasu wątku.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="d1ff8-112">W tym momencie zatrzaśnięcia powoduje jego własnej przełączenie kontekstu wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> i przekazywanie w pozostałej części wartość limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="d1ff8-113">Dane wyjściowe rejestrowania pokazuje, jak często zatrzaśnięcia mógł zwiększenia wydajności, uzyskiwanie blokady bez użycia <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="d1ff8-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ff8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1ff8-114">See Also</span></span>  
 [<span data-ttu-id="d1ff8-115">Metody SpinWait</span><span class="sxs-lookup"><span data-stu-id="d1ff8-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="d1ff8-116">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="d1ff8-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
