---
title: "Porady: przyspieszanie małych jednostek pętli"
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
helpviewer_keywords: parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fb1c39d3eb2c0b68182f49d8aa5dcc4e652f9215
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Porady: przyspieszanie małych jednostek pętli
Gdy <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętli ma małych treści, go może działać wolniej niż równoważne pętli sekwencyjnych, takich jak [dla](~/docs/csharp/language-reference/keywords/for.md) pętli w języku C# i [dla](http://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) pętli w języku Visual Basic. Niższej wydajności jest spowodowany przez koszty związane z partycjonowanie danych i kosztów wywoływania delegata w każdej iteracji pętli. Aby rozwiązać takich scenariuszy <xref:System.Collections.Concurrent.Partitioner> klasa udostępnia <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodę, która umożliwia podanie loop sekwencyjnych jednostka delegata, tak aby delegat jest wywoływany tylko raz dla każdej partycji, zamiast raz dla iteracji. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 To rozwiązanie zostało to pokazane w tym przykładzie jest przydatne, gdy pętli wykonuje minimalnego czasu pracy. W miarę praktyce bardziej kosztowne pracy prawdopodobnie otrzymasz taką samą lub lepszą wydajnością przy użyciu <xref:System.Threading.Tasks.Parallel.For%2A> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli z partycjonera domyślne.  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
