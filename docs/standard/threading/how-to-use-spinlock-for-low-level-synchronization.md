---
title: 'Porady: używanie struktury SpinLock do synchronizacji niskiego poziomu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 216480e893f6dbebbb204cbf2bfebae8dc139ec4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135175"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="7cfa9-102">Porady: używanie struktury SpinLock do synchronizacji niskiego poziomu</span><span class="sxs-lookup"><span data-stu-id="7cfa9-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="7cfa9-103">Poniższy przykład pokazuje sposób użycia <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cfa9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cfa9-104">Example</span></span>  
 <span data-ttu-id="7cfa9-105">W tym przykładzie sekcję krytyczną wykonuje minimalnego czasu pracy, które ułatwia dobrym kandydatem do <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="7cfa9-106">Zwiększanie pracę małą ilością zwiększa wydajność <xref:System.Threading.SpinLock> w porównaniu do standardowych blokady.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="7cfa9-107">Jednak znajduje się punkt, w jakim struktury SpinLock staje się bardziej kosztowne niż standardowe blokady.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="7cfa9-108">Można użyć profilowania funkcji w narzędziach profilowania współbieżności, aby zobaczyć, jakiego typu blokady zapewnia lepszą wydajność w programie.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="7cfa9-109">Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="7cfa9-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="7cfa9-110"><xref:System.Threading.SpinLock> mogą być przydatne, gdy nie ma blokady zasobu udostępnionego dla bardzo długi.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="7cfa9-111">W takich przypadkach na komputerach z wielordzeniowymi procesorami może być zablokowany wątek Cię w kilka cykli, dopóki blokada jest zwalniana wydajny.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="7cfa9-112">Która pozwala na, wątek nie stać się blokowane, czyli procesu mocy procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="7cfa9-113"><xref:System.Threading.SpinLock> przestanie rotowania w pewnych okolicznościach, aby uniknąć zablokowania procesorów logicznych lub odwracanie priorytet w systemach z funkcją Hyper-Threading.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="7cfa9-114">W tym przykładzie użyto <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> klasy, która wymaga synchronizacji użytkowników dla dostępu wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="7cfa9-115">W aplikacjach przeznaczonych dla platformy .NET Framework w wersji 4, innym rozwiązaniem jest użycie <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, co nie wymaga żadnych blokady użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="7cfa9-116">Zwróć uwagę na użycie `false` (`False` w języku Visual Basic) w wywołaniu <xref:System.Threading.SpinLock.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="7cfa9-117">Dzięki temu można uzyskać najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-117">This provides the best performance.</span></span> <span data-ttu-id="7cfa9-118">Określ `true` (`True`) na architektury IA64 używania horyzontu pamięci, która opróżnia buforów zapisu, aby upewnić się, czy blokada jest teraz dostępna dla innych wątków zakończyć pracę.</span><span class="sxs-lookup"><span data-stu-id="7cfa9-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfa9-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cfa9-119">See also</span></span>

- [<span data-ttu-id="7cfa9-120">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="7cfa9-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
