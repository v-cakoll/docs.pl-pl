---
title: "Porady: używanie struktury SpinLock do synchronizacji niskiego poziomu"
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
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 11d41a1fd04039fd08d945a72a37a479f79449a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="b8ca5-102">Porady: używanie struktury SpinLock do synchronizacji niskiego poziomu</span><span class="sxs-lookup"><span data-stu-id="b8ca5-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="b8ca5-103">W poniższym przykładzie pokazano sposób użycia <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8ca5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8ca5-104">Example</span></span>  
 <span data-ttu-id="b8ca5-105">W tym przykładzie sekcja krytyczna wykonuje minimalnego czasu pracy, dzięki czemu odpowiednimi kandydatami do <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="b8ca5-106">Praca niewielkie zwiększeniu wydajności <xref:System.Threading.SpinLock> w porównaniu do standardowych blokady.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="b8ca5-107">Istnieje jednak punkt, jaką struktury SpinLock staje się droższe niż standardowe blokady.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="b8ca5-108">Aby zobaczyć, jaki rodzaj blokady zapewnia lepszą wydajność w programie, można użyć profilowania funkcji w narzędziach profilowania współbieżności.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="b8ca5-109">Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="b8ca5-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="b8ca5-110"><xref:System.Threading.SpinLock>mogą być przydatne, jeśli Blokada zasobu udostępnionego nie będzie można przechowywać na bardzo długi.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="b8ca5-111">W takich przypadkach na komputerach z procesorami wielordzeniowymi może być wydajne na pokrętła przez kilka cykli do czasu zwolnienia blokady zablokowanych wątku.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="b8ca5-112">Przez Obracająca, wątek nie zablokowanie, które jest procesem użycie Procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="b8ca5-113"><xref:System.Threading.SpinLock>przestanie Obracająca pewnych warunkach, aby uniknąć zablokowania procesorów logicznych lub odwracanie priorytet w systemach z funkcją Hyper-Threading.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="b8ca5-114">W tym przykładzie użyto <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> klasy, która wymaga synchronizacji użytkowników dla wielowątkowych dostęp.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="b8ca5-115">W aplikacjach przeznaczonych dla platformy .NET Framework w wersji 4, inną opcją jest użycie <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, co nie wymaga żadnych blokady użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="b8ca5-116">Zwróć uwagę na użycie `false` (`False` w języku Visual Basic) w wywołaniu <xref:System.Threading.SpinLock.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="b8ca5-117">To zapewnia najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-117">This provides the best performance.</span></span> <span data-ttu-id="b8ca5-118">Określ `true` (`True`) na IA64 architektury do użycia ogrodzenia pamięci, które opróżnienia buforów zapisu, aby upewnić się, że blokady są teraz dostępne dla innych wątków zakończyć.</span><span class="sxs-lookup"><span data-stu-id="b8ca5-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ca5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8ca5-119">See Also</span></span>  
 [<span data-ttu-id="b8ca5-120">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="b8ca5-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
