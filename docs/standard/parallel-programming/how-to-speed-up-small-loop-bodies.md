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
ms.openlocfilehash: 29d7fa8200ddd972c1a5c98ea6f30a7c8ff732e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139750"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Porady: przyspieszanie małych jednostek pętli
Gdy <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętla ma małe treści, może działać wolniej niż równoważne pętli sekwencyjnej, takich jak [for](../../csharp/language-reference/keywords/for.md) pętli w języku C# i [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) pętli w języku Visual Basic. Wolniejsza wydajność jest spowodowana obciążeniem związanym z partycjonowaniem danych i kosztem wywoływania delegata w każdej iteracji pętli. Aby rozwiązać takie scenariusze, <xref:System.Collections.Concurrent.Partitioner> <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> klasa udostępnia metodę, która umożliwia zapewnienie pętli sekwencyjnej dla treści delegata, tak aby delegat jest wywoływany tylko raz na partycję, zamiast raz na iterację. Aby uzyskać więcej informacji, zobacz [Partycjonery niestandardowe dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Podejście przedstawione w tym przykładzie jest przydatne, gdy pętla wykonuje minimalną ilość pracy. W miarę jak praca staje się bardziej kosztowna obliczeniowo, prawdopodobnie <xref:System.Threading.Tasks.Parallel.For%2A> uzyskasz taką samą lub lepszą wydajność przy użyciu lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli z domyślnym partycjonowaniem.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Iterytory (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Iteratory (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
