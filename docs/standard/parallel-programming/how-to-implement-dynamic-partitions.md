---
title: 'Instrukcje: Implementowanie partycji dynamicznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 792488e53ffb7f870e21fdd1ad3ef94bf0303b1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811556"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="2c069-102">Instrukcje: Implementowanie partycji dynamicznych</span><span class="sxs-lookup"><span data-stu-id="2c069-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="2c069-103">Poniższy przykład pokazuje, jak zaimplementować niestandardowy <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> które implementuje dynamiczne partycjonowanie i mogą być używane z niektórych przeciążenia <xref:System.Threading.Tasks.Parallel.ForEach%2A> z PLINQ.</span><span class="sxs-lookup"><span data-stu-id="2c069-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c069-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c069-104">Example</span></span>  
 <span data-ttu-id="2c069-105">Zawsze wywołuje partycji <xref:System.Collections.IEnumerator.MoveNext%2A> przez moduł wyliczający modułu wyliczającego zapewnia partycji z listy jeden element.</span><span class="sxs-lookup"><span data-stu-id="2c069-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="2c069-106">W przypadku PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A>, partycja jest <xref:System.Threading.Tasks.Task> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2c069-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="2c069-107">Ponieważ żądania są wykonywane równolegle w wielu wątkach, dostęp do bieżącego indeksu są synchronizowane.</span><span class="sxs-lookup"><span data-stu-id="2c069-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="2c069-108">Jest to przykład fragmentów, partycjonowanie, z każdym fragmentem składający się z jednym elementem.</span><span class="sxs-lookup"><span data-stu-id="2c069-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="2c069-109">Przez zapewnienie im więcej elementów w danym momencie, może zmniejszyć rywalizację na blokadę, a teoretycznie osiągnąć zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="2c069-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="2c069-110">Jednak w pewnym momencie większe fragmenty mogą wymagać dodatkowej logiki równoważenia obciążenia Aby zachować wszystkie wątki zajęty, aż wszystkie zadania są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="2c069-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c069-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c069-111">See also</span></span>

- [<span data-ttu-id="2c069-112">Niestandardowe partycjonery dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="2c069-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="2c069-113">Instrukcje: Implementowanie Partycjonera dla partycjonowania statycznego</span><span class="sxs-lookup"><span data-stu-id="2c069-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
