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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137944"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="cf8d4-102">Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania</span><span class="sxs-lookup"><span data-stu-id="cf8d4-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="cf8d4-103">Poniższy przykład pokazuje, jak używać obiektu <xref:System.Threading.SpinWait?displayProperty=nameWithType> do implementowania wielofazowej operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="cf8d4-104">W pierwszej fazie obiekt synchronizacji, `Latch`, obraca się dla kilku cykli podczas sprawdzania, czy blokada stanie się dostępna.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="cf8d4-105">W drugiej fazie, jeśli blokada zostanie udostępniona, Metoda `Wait` zwraca bez użycia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> do wykonania oczekiwania; w przeciwnym razie `Wait` wykonuje oczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf8d4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf8d4-106">Example</span></span>  
 <span data-ttu-id="cf8d4-107">W tym przykładzie przedstawiono bardzo podstawową implementację elementu pierwotnego synchronizacji zamka.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="cf8d4-108">Tej struktury danych można użyć, gdy czasy oczekiwania są bardzo krótkie.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="cf8d4-109">Ten przykład służy tylko do celów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="cf8d4-110">Jeśli w programie jest wymagana funkcja typu zatrzaśnięcia, należy rozważyć użycie <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="cf8d4-111">Zamk używa obiektu <xref:System.Threading.SpinWait>, aby obracać się tylko do momentu następnego wywołania do `SpinOnce` powoduje, że <xref:System.Threading.SpinWait> uzyskać wycinka czasu wątku.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="cf8d4-112">W tym momencie zamk wywołuje swój własny przełącznik kontekstu przez wywołanie <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> i przekazanie w pozostałej części wartości limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="cf8d4-113">Dane wyjściowe rejestrowania pokazują, jak często zatrzaśnięcie było w stanie zwiększyć wydajność dzięki uzyskaniu blokady bez użycia <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="cf8d4-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8d4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf8d4-114">See also</span></span>

- [<span data-ttu-id="cf8d4-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="cf8d4-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)
- [<span data-ttu-id="cf8d4-116">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="cf8d4-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
