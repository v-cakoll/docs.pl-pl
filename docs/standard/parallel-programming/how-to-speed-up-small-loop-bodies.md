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
ms.openlocfilehash: fde68d0a938ed04380bf0e99cc0c544793571d77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682979"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Instrukcje: Przyspieszanie małych jednostek pętli
Gdy <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętli ma mały treść, jego może działać wolniej niż równoważna pętli sekwencyjnej, takich jak [dla](../../csharp/language-reference/keywords/for.md) pętli w języku C# i [dla](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) pętli w języku Visual Basic. Przyczyną jest obciążenie związane z partycjonowania danych i koszt wywoływania delegata w każdej iteracji pętli niższej wydajności. Do takich scenariuszy <xref:System.Collections.Concurrent.Partitioner> klasa udostępnia <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody, która pozwala na dostarczenie pętli sekwencyjnej jednostka delegata, tak, aby obiekt delegowany jest wywoływany tylko raz w jednej partycji, a nie raz dla iteracji. Aby uzyskać więcej informacji, zobacz [niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 To podejście pokazano w tym przykładzie jest przydatne, gdy pętla wykonuje minimalnego czasu pracy. Praca staje się bardziej obliczeniowo kosztowne, prawdopodobnie otrzymasz tej samej lub lepszej wydajności przy użyciu <xref:System.Threading.Tasks.Parallel.For%2A> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli za pomocą partycjonera domyślne.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Iteratory (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Iteratory (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
