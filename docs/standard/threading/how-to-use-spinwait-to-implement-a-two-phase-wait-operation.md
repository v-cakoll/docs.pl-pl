---
title: 'Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb2fbf5e0a310156fdc6fac5fe736692e8ec133
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209215"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="74406-102">Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania</span><span class="sxs-lookup"><span data-stu-id="74406-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="74406-103">Poniższy przykład pokazuje, jak używać <xref:System.Threading.SpinWait?displayProperty=nameWithType> obiekt do implementacji dwufazowej operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="74406-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="74406-104">W pierwszej fazie obiekt synchronizacji `Latch`, uruchamia dla kilku cykli, podczas gdy sprawdza, czy blokada stał się dostępny.</span><span class="sxs-lookup"><span data-stu-id="74406-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="74406-105">W drugim etapie, jeśli blokada staje się dostępny a następnie `Wait` metoda zwraca bez użycia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> przeprowadzić jego oczekiwania; w przeciwnym razie `Wait` wykonuje czas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="74406-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74406-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="74406-106">Example</span></span>  
 <span data-ttu-id="74406-107">Ten przykład przedstawia bardzo podstawową implementację synchronizacji zatrzaśnięcia pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="74406-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="74406-108">Jeśli spodziewane czasy oczekiwania będą bardzo krótkie, możesz użyć tej struktury danych.</span><span class="sxs-lookup"><span data-stu-id="74406-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="74406-109">Ten przykład dotyczy tylko w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="74406-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="74406-110">Jeśli potrzebujesz funkcji zatrzaśnięcia typu w swoim programie, należy wziąć pod uwagę przy użyciu <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74406-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="74406-111">Używa zatrzaśnięcia <xref:System.Threading.SpinWait> obiektu Cię w miejscu tylko do następnego wywołania metody `SpinOnce` powoduje, że <xref:System.Threading.SpinWait> umożliwiające uzyskanie przedziału czasu wątku.</span><span class="sxs-lookup"><span data-stu-id="74406-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="74406-112">W tym momencie zatrzaśnięcia powoduje, że jego własnej przełączenie kontekstu, wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> i przekazywania w pozostałej części wartość limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="74406-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="74406-113">Dane wyjściowe rejestrowania pokazują, jak często zatrzaśnięcia był w stanie, co pozwoli zwiększyć wydajność przez uzyskanie blokady bez korzystania z <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="74406-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74406-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74406-114">See also</span></span>

- [<span data-ttu-id="74406-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="74406-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
- [<span data-ttu-id="74406-116">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="74406-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
