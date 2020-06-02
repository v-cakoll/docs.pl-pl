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
ms.openlocfilehash: 4983cafb9d4a72262dc7a6a6c37fab23937b3274
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288085"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Instrukcje: Przyspieszanie małych jednostek pętli
Gdy <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> Pętla ma małą treść, może działać wolniej niż równoważna pętla sekwencyjna, taka jak pętla [for](../../csharp/language-reference/keywords/for.md) w C# i pętla [for](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) w Visual Basic. Mniejsza wydajność wynika z obciążenia związanego z partycjonowaniem danych i kosztem wywołania delegata dla każdej iteracji pętli. Aby rozwiązać takie scenariusze, <xref:System.Collections.Concurrent.Partitioner> Klasa udostępnia <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodę, która umożliwia wykonywanie pętli sekwencyjnej dla treści delegata, tak aby delegat został wywołany tylko raz na partycję, a nie raz na iterację. Aby uzyskać więcej informacji, zobacz [niestandardowe partycje dla PLINQ i TPL](custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Podejście przedstawione w tym przykładzie jest przydatne, gdy pętla wykonuje minimalną ilość pracy. Gdy prace staną się bardziej kosztowne, prawdopodobnie będziesz mieć taką samą lub lepszą wydajność przy użyciu <xref:System.Threading.Tasks.Parallel.For%2A> <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli lub z domyślną partycją.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](data-parallelism-task-parallel-library.md)
- [Niestandardowe partycje dla PLINQ i TPL](custom-partitioners-for-plinq-and-tpl.md)
- [Iteratory (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Iteratory (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Wyrażenia lambda w PLINQ i TPL](lambda-expressions-in-plinq-and-tpl.md)
