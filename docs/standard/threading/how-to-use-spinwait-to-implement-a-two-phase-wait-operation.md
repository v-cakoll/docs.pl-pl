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
ms.openlocfilehash: 5bac174660177fd47e1f345e64581e35ae4c0ffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137944"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="f724d-102">Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania</span><span class="sxs-lookup"><span data-stu-id="f724d-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="f724d-103">W poniższym przykładzie pokazano, jak użyć <xref:System.Threading.SpinWait?displayProperty=nameWithType> obiektu do zaimplementowania operacji oczekiwania dwufazowego.</span><span class="sxs-lookup"><span data-stu-id="f724d-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="f724d-104">W pierwszej fazie obiekt synchronizacji, a `Latch`, obraca się przez kilka cykli, podczas gdy sprawdza, czy blokada stała się dostępna.</span><span class="sxs-lookup"><span data-stu-id="f724d-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="f724d-105">W drugiej fazie, jeśli blokada staje `Wait` się dostępna, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> metoda zwraca bez użycia do wykonania jego oczekiwania; w `Wait` przeciwnym razie wykonuje oczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="f724d-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f724d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f724d-106">Example</span></span>  
 <span data-ttu-id="f724d-107">W tym przykładzie przedstawiono bardzo podstawową implementację prymitywu synchronizacji zatrzasku.</span><span class="sxs-lookup"><span data-stu-id="f724d-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="f724d-108">Tej struktury danych można użyć, gdy oczekuje się, że czasy oczekiwania będą bardzo krótkie.</span><span class="sxs-lookup"><span data-stu-id="f724d-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="f724d-109">W tym przykładzie jest tylko do celów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f724d-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="f724d-110">Jeśli w programie wymagana jest funkcja typu <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>zatrzask, rozważ użycie .</span><span class="sxs-lookup"><span data-stu-id="f724d-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="f724d-111">Zatrzask używa <xref:System.Threading.SpinWait> obiektu do obracania się w `SpinOnce` miejscu <xref:System.Threading.SpinWait> tylko do następnego wywołania powoduje, że daje wycinek czasu wątku.</span><span class="sxs-lookup"><span data-stu-id="f724d-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="f724d-112">W tym momencie zatrzask powoduje własne przełącznik <xref:System.Threading.WaitHandle.WaitOne%2A> kontekstu, wywołując <xref:System.Threading.ManualResetEvent> i przekazując w pozostałej części wartości określającego czas.</span><span class="sxs-lookup"><span data-stu-id="f724d-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="f724d-113">Dane wyjściowe rejestrowania pokazuje, jak często zatrzask był w <xref:System.Threading.ManualResetEvent>stanie zwiększyć wydajność poprzez uzyskanie blokady bez użycia .</span><span class="sxs-lookup"><span data-stu-id="f724d-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f724d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f724d-114">See also</span></span>

- [<span data-ttu-id="f724d-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="f724d-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)
- [<span data-ttu-id="f724d-116">Wątkowe obiekty i operacje</span><span class="sxs-lookup"><span data-stu-id="f724d-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
