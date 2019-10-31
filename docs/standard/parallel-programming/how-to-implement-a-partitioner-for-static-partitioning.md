---
title: 'Porady: implementowanie partycjonera dla partycjonowania statycznego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091532"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="b394d-102">Porady: implementowanie partycjonera dla partycjonowania statycznego</span><span class="sxs-lookup"><span data-stu-id="b394d-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="b394d-103">W poniższym przykładzie pokazano jeden ze sposobów implementacji prostego niestandardowego Partitioner dla PLINQ, który wykonuje statyczne partycjonowanie.</span><span class="sxs-lookup"><span data-stu-id="b394d-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="b394d-104">Ponieważ partycja nie obsługuje partycji dynamicznych, nie można jej używać z <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b394d-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b394d-105">Ta konkretna partycja może dostarczyć przyspieszenie przez domyślną partycję zakresu dla źródeł danych, dla których każdy element wymaga wzrostu czasu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b394d-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b394d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b394d-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="b394d-107">Partycje w tym przykładzie opierają się na założeniu liniowego wzrostu czasu przetwarzania dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="b394d-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="b394d-108">W świecie rzeczywistym może być trudne przewidywanie czasu przetwarzania w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="b394d-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="b394d-109">Jeśli używasz statycznej partycji z określonym źródłem danych, możesz zoptymalizować formułę partycjonowania dla źródła, dodać logikę równoważenia obciążenia lub użyć podejścia partycjonowania fragmentu, jak pokazano w [instrukcje: implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="b394d-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b394d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b394d-110">See also</span></span>

- [<span data-ttu-id="b394d-111">Niestandardowe partycjonery dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="b394d-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
