---
title: 'Instrukcje: Przyspieszanie małych jednostek pętli'
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
ms.openlocfilehash: 06af0e10080977800479ed5aa444c63bde2d371e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726458"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Instrukcje: Przyspieszanie małych jednostek pętli
Gdy <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętli ma mały treść, jego może działać wolniej niż równoważna pętli sekwencyjnej, takich jak [dla](~/docs/csharp/language-reference/keywords/for.md) pętli w języku C# i [dla](https://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) pętli w języku Visual Basic. Przyczyną jest obciążenie związane z partycjonowania danych i koszt wywoływania delegata w każdej iteracji pętli niższej wydajności. Do takich scenariuszy <xref:System.Collections.Concurrent.Partitioner> klasa udostępnia <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody, która pozwala na dostarczenie pętli sekwencyjnej jednostka delegata, tak, aby obiekt delegowany jest wywoływany tylko raz w jednej partycji, a nie raz dla iteracji. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 To podejście pokazano w tym przykładzie jest przydatne, gdy pętla wykonuje minimalnego czasu pracy. Praca staje się bardziej obliczeniowo kosztowne, prawdopodobnie otrzymasz tej samej lub lepszej wydajności przy użyciu <xref:System.Threading.Tasks.Parallel.For%2A> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli za pomocą partycjonera domyślne.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Iteratory](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
