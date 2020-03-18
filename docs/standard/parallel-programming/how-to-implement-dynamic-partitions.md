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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091422"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="9f7d3-102">Porady: implementowanie partycji dynamicznych</span><span class="sxs-lookup"><span data-stu-id="9f7d3-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="9f7d3-103">W poniższym przykładzie pokazano, jak zaimplementować niestandardowe, <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> który implementuje partycjonowanie dynamiczne i może służyć z niektórych przeciążeń <xref:System.Threading.Tasks.Parallel.ForEach%2A> i z PLINQ.</span><span class="sxs-lookup"><span data-stu-id="9f7d3-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f7d3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f7d3-104">Example</span></span>

<span data-ttu-id="9f7d3-105">Za każdym razem <xref:System.Collections.IEnumerator.MoveNext%2A> partycji wywołuje wyliczacza, wyliczacz udostępnia partycji z jednym elementem listy.</span><span class="sxs-lookup"><span data-stu-id="9f7d3-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="9f7d3-106">W przypadku PLINQ <xref:System.Threading.Tasks.Parallel.ForEach%2A>i , partycja jest wystąpieniem. <xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="9f7d3-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="9f7d3-107">Ponieważ żądania są dzieje się jednocześnie na wielu wątków, dostęp do bieżącego indeksu jest synchronizowany.</span><span class="sxs-lookup"><span data-stu-id="9f7d3-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="9f7d3-108">Jest to przykład partycjonowania fragmentu, z każdym fragmentem składającym się z jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="9f7d3-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="9f7d3-109">Dostarczając więcej elementów naraz, można zmniejszyć rywalizację o blokadę i teoretycznie osiągnąć szybszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="9f7d3-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="9f7d3-110">Jednak w pewnym momencie większe fragmenty mogą wymagać dodatkowej logiki równoważenia obciążenia, aby wszystkie wątki były zajęte, dopóki nie zostanie wykonana cała praca.</span><span class="sxs-lookup"><span data-stu-id="9f7d3-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f7d3-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f7d3-111">See also</span></span>

* [<span data-ttu-id="9f7d3-112">Niestandardowe partycjonery dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="9f7d3-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="9f7d3-113">Porady: implementowanie partycjonera dla partycjonowania statycznego</span><span class="sxs-lookup"><span data-stu-id="9f7d3-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
