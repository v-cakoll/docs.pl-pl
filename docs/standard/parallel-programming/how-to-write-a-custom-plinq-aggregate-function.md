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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106768"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Porady: pisanie niestandardowej funkcji agregowania w PLINQ
W tym przykładzie pokazano, jak użyć <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metody, aby zastosować niestandardową funkcję agregacji do sekwencji źródłowej.  
  
> [!WARNING]
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie oblicza odchylenie standardowe sekwencji liczb całkowitych.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 W tym przykładzie użyto przeciążenia operatora zagregowanej kwerendy standardowej, który jest unikatowy dla PLINQ. To przeciążenie <xref:System.Func%603?displayProperty=nameWithType> ma dodatkowe jako trzeci parametr wejściowy. Ten pełnomocnik łączy wyniki ze wszystkich wątków, zanim wykona ostateczne obliczenia na zagregowanych wynikach. W tym przykładzie dodajemy razem sumy ze wszystkich wątków.  
  
 Należy zauważyć, że gdy obiekt wyrażenia lambda składa się <xref:System.Func%602?displayProperty=nameWithType> z pojedynczego wyrażenia, zwracana wartość delegata jest wartością wyrażenia.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
