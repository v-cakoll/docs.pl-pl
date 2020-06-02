---
title: 'Instrukcje: Implementowanie partycjonera dla partycjonowania statycznego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 22d2cf788d4726488512703356a75f84efd04250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278509"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="48c5e-102">Instrukcje: Implementowanie partycjonera dla partycjonowania statycznego</span><span class="sxs-lookup"><span data-stu-id="48c5e-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="48c5e-103">W poniższym przykładzie pokazano jeden ze sposobów implementacji prostego niestandardowego Partitioner dla PLINQ, który wykonuje statyczne partycjonowanie.</span><span class="sxs-lookup"><span data-stu-id="48c5e-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="48c5e-104">Ponieważ partycja nie obsługuje partycji dynamicznych, nie można jej używać <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="48c5e-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="48c5e-105">Ta konkretna partycja może dostarczyć przyspieszenie przez domyślną partycję zakresu dla źródeł danych, dla których każdy element wymaga wzrostu czasu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="48c5e-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48c5e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="48c5e-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="48c5e-107">Partycje w tym przykładzie opierają się na założeniu liniowego wzrostu czasu przetwarzania dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="48c5e-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="48c5e-108">W świecie rzeczywistym może być trudne przewidywanie czasu przetwarzania w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="48c5e-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="48c5e-109">Jeśli używasz statycznej partycji z określonym źródłem danych, możesz zoptymalizować formułę partycjonowania dla źródła, dodać logikę równoważenia obciążenia lub użyć podejścia partycjonowania fragmentu, jak pokazano w [instrukcje: implementowanie partycji dynamicznych](how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="48c5e-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c5e-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48c5e-110">See also</span></span>

- [<span data-ttu-id="48c5e-111">Niestandardowe partycje dla PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="48c5e-111">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
