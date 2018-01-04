---
title: 'Porady: implementowanie partycji dynamicznych'
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
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b08c387c9b10a9d6fa8728a7fce87a7894a37fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="733cf-102">Porady: implementowanie partycji dynamicznych</span><span class="sxs-lookup"><span data-stu-id="733cf-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="733cf-103">Poniższy przykład przedstawia sposób zaimplementowania niestandardowego <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> który implementuje dynamiczne partycjonowanie i mogą być używane z niektórych przeciążenia <xref:System.Threading.Tasks.Parallel.ForEach%2A> i z PLINQ.</span><span class="sxs-lookup"><span data-stu-id="733cf-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="733cf-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="733cf-104">Example</span></span>  
 <span data-ttu-id="733cf-105">Zawsze wywołuje partycji <xref:System.Collections.IEnumerator.MoveNext%2A> przez moduł wyliczający modułu wyliczającego zapewnia partycji z listy jeden element.</span><span class="sxs-lookup"><span data-stu-id="733cf-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="733cf-106">W przypadku PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A>, partycja jest <xref:System.Threading.Tasks.Task> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="733cf-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="733cf-107">Ponieważ żądania są wykonywane jednocześnie na wielu wątków, dostęp do bieżącego indeksu jest zsynchronizowany.</span><span class="sxs-lookup"><span data-stu-id="733cf-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="733cf-108">To jest przykład fragmentu partycjonowania z każdego fragmentu składające się z jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="733cf-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="733cf-109">Zapewniając więcej elementów jednocześnie, można zmniejszyć konfliktu za pośrednictwem blokady i teoretycznie osiągnąć większą wydajność.</span><span class="sxs-lookup"><span data-stu-id="733cf-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="733cf-110">W pewnym momencie większych fragmentów mogą jednak wymagać dodatkową logikę równoważenia obciążenia, aby zachować wszystkie wątki zajęty, dopóki wszystkie praca jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="733cf-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733cf-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="733cf-111">See Also</span></span>  
 [<span data-ttu-id="733cf-112">Niestandardowe partycjonery dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="733cf-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="733cf-113">Instrukcje: implementowanie partycjonera dla partycjonowania statycznego</span><span class="sxs-lookup"><span data-stu-id="733cf-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
