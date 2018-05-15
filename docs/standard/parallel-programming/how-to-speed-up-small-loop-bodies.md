---
title: 'Porady: przyspieszanie małych jednostek pętli'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bff41416dd2263c185cc94de045b2c8a26ea194d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="34540-102">Porady: przyspieszanie małych jednostek pętli</span><span class="sxs-lookup"><span data-stu-id="34540-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="34540-103">Gdy <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętli ma małych treści, go może działać wolniej niż równoważne pętli sekwencyjnych, takich jak [dla](~/docs/csharp/language-reference/keywords/for.md) pętli w języku C# i [dla](http://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) pętli w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34540-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](~/docs/csharp/language-reference/keywords/for.md) loop in C# and the [For](http://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) loop in Visual Basic.</span></span> <span data-ttu-id="34540-104">Niższej wydajności jest spowodowany przez koszty związane z partycjonowanie danych i kosztów wywoływania delegata w każdej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="34540-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="34540-105">Aby rozwiązać takich scenariuszy <xref:System.Collections.Concurrent.Partitioner> klasa udostępnia <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodę, która umożliwia podanie loop sekwencyjnych jednostka delegata, tak aby delegat jest wywoływany tylko raz dla każdej partycji, zamiast raz dla iteracji.</span><span class="sxs-lookup"><span data-stu-id="34540-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="34540-106">Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="34540-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34540-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="34540-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="34540-108">To rozwiązanie zostało to pokazane w tym przykładzie jest przydatne, gdy pętli wykonuje minimalnego czasu pracy.</span><span class="sxs-lookup"><span data-stu-id="34540-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="34540-109">W miarę praktyce bardziej kosztowne pracy prawdopodobnie otrzymasz taką samą lub lepszą wydajnością przy użyciu <xref:System.Threading.Tasks.Parallel.For%2A> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli z partycjonera domyślne.</span><span class="sxs-lookup"><span data-stu-id="34540-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34540-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34540-110">See Also</span></span>  
 [<span data-ttu-id="34540-111">Równoległość danych</span><span class="sxs-lookup"><span data-stu-id="34540-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="34540-112">Niestandardowe partycjonery dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="34540-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="34540-113">Iteratory</span><span class="sxs-lookup"><span data-stu-id="34540-113">Iterators</span></span>](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="34540-114">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="34540-114">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
