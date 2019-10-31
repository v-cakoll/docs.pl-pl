---
title: 'Porady: pisanie niestandardowej funkcji agregowania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 7bb4cc1b69f0b6b97c1cf6255ded5341304f3ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106768"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Porady: pisanie niestandardowej funkcji agregowania w PLINQ
W tym przykładzie pokazano, jak za pomocą metody <xref:System.Linq.ParallelEnumerable.Aggregate%2A> zastosować niestandardową funkcję agregacji do sekwencji źródłowej.  
  
> [!WARNING]
> Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład oblicza odchylenie standardowe sekwencji liczb całkowitych.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 W tym przykładzie użyto przeciążenia standardowego operatora kwerendy agregującej, który jest unikatowy dla PLINQ. To Przeciążenie pobiera dodatkowe <xref:System.Func%603?displayProperty=nameWithType> jako trzeci parametr wejściowy. Ten delegat łączy wyniki ze wszystkich wątków przed wykonaniem obliczenia końcowego na zagregowanych wynikach. W tym przykładzie dodamy razem kwoty ze wszystkich wątków.  
  
 Należy zauważyć, że gdy treść wyrażenia lambda składa się z pojedynczego wyrażenia, wartość zwracana <xref:System.Func%602?displayProperty=nameWithType> delegata to wartość wyrażenia.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
