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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139750"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Porady: przyspieszanie małych jednostek pętli
Gdy pętla <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ma małą treść, może działać wolniej niż równoważna pętla sekwencyjna, taka jak pętla [for](../../csharp/language-reference/keywords/for.md) w C# i pętla [for](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) w Visual Basic. Mniejsza wydajność wynika z obciążenia związanego z partycjonowaniem danych i kosztem wywołania delegata dla każdej iteracji pętli. Aby rozwiązać takie scenariusze, Klasa <xref:System.Collections.Concurrent.Partitioner> udostępnia metodę <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>, która umożliwia tworzenie pętli sekwencyjnej dla treści delegata, tak aby delegat został wywołany tylko raz na partycję, a nie raz na iterację. Aby uzyskać więcej informacji, zobacz [niestandardowe partycje dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Podejście przedstawione w tym przykładzie jest przydatne, gdy pętla wykonuje minimalną ilość pracy. Gdy prace staną się bardziej kosztowne, prawdopodobnie będzie to taka sama lub lepsza wydajność przy użyciu pętli <xref:System.Threading.Tasks.Parallel.For%2A> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> z domyślną partycją.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Iteratory (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Iteratory (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
