---
title: 'Porady: implementowanie partycji dynamicznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 3970566b4e3f51ce538c328d4e69b20ec22ec09b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091422"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="3177c-102">Porady: implementowanie partycji dynamicznych</span><span class="sxs-lookup"><span data-stu-id="3177c-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="3177c-103">Poniższy przykład pokazuje, jak zaimplementować niestandardowy <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>, który implementuje partycjonowanie dynamiczne i może być używany z pewnych przeciążeń <xref:System.Threading.Tasks.Parallel.ForEach%2A> i z PLINQ.</span><span class="sxs-lookup"><span data-stu-id="3177c-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3177c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3177c-104">Example</span></span>

<span data-ttu-id="3177c-105">Za każdym razem, gdy partycja wywołuje <xref:System.Collections.IEnumerator.MoveNext%2A> w module wyliczającym, moduł wyliczający tworzy partycję z jednym elementem listy.</span><span class="sxs-lookup"><span data-stu-id="3177c-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="3177c-106">W przypadku PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A>partycja jest wystąpieniem <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="3177c-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="3177c-107">Ponieważ żądania są wykonywane współbieżnie w wielu wątkach, jest synchronizowany dostęp do bieżącego indeksu.</span><span class="sxs-lookup"><span data-stu-id="3177c-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="3177c-108">Jest to przykład partycjonowania fragmentu, z każdym fragmentem składającym się z jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="3177c-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="3177c-109">Zapewniając więcej elementów naraz, można zmniejszyć rywalizację o blokadę i teoretycznie osiągnąć wyższą wydajność.</span><span class="sxs-lookup"><span data-stu-id="3177c-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="3177c-110">Jednak w pewnym momencie większe fragmenty mogą wymagać dodatkowej logiki równoważenia obciążenia, aby zapewnić, że wszystkie wątki są zajęte, dopóki wszystkie zadania nie zostaną wykonane.</span><span class="sxs-lookup"><span data-stu-id="3177c-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3177c-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3177c-111">See also</span></span>

* [<span data-ttu-id="3177c-112">Niestandardowe partycjonery dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="3177c-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="3177c-113">Instrukcje: implementowanie partycjonera dla partycjonowania statycznego</span><span class="sxs-lookup"><span data-stu-id="3177c-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
