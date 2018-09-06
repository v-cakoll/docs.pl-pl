---
title: 'Porady: implementowanie partycjonera dla partycjonowania statycznego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 302d7d98d04e528d205edf38c3fa13bb3f2b2252
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863076"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="e50c8-102">Porady: implementowanie partycjonera dla partycjonowania statycznego</span><span class="sxs-lookup"><span data-stu-id="e50c8-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="e50c8-103">Poniższy przykład przedstawia sposób implementować proste niestandardowego partycjonera dla PLINQ, który wykonuje partycjonowania statycznego.</span><span class="sxs-lookup"><span data-stu-id="e50c8-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="e50c8-104">Ponieważ partycjonera nie obsługuje partycji dynamicznych, nie jest może być używany przez <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e50c8-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e50c8-105">Tego konkretnego partycjonera udostępniać przyspieszenie za pośrednictwem partycjonera zakresu domyślnego źródła danych, dla których każdy element wymaga zwiększa ilość czasu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="e50c8-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e50c8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e50c8-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="e50c8-107">Partycje w tym przykładzie są oparte na założeniu liniowy wzrost czas przetwarzania dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="e50c8-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="e50c8-108">W świecie rzeczywistym może być trudne do przewidzenia czas przetwarzania w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="e50c8-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="e50c8-109">Jeśli statycznego partycjonera korzystają z określonego źródła danych, można zoptymalizować partycjonowania formułę dla źródła, Dodaj logikę równoważenia obciążenia lub używanie fragmentów, partycjonowanie podejście, jak pokazano w [porady: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="e50c8-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e50c8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e50c8-110">See also</span></span>

- [<span data-ttu-id="e50c8-111">Niestandardowe partycjonery dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="e50c8-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
