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
ms.openlocfilehash: 8168c89a6edecd5f7e33a710c9a89c92a6f82005
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588227"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Porady: pisanie niestandardowej funkcji agregowania w PLINQ
W tym przykładzie <xref:System.Linq.ParallelEnumerable.Aggregate%2A> pokazano, jak użyć metody, aby zastosować funkcję agregacji niestandardowej do sekwencji źródłowej.  
  
> [!WARNING]
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład oblicza odchylenie standardowe sekwencji liczby całkowite.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 W tym przykładzie użyto przeciążenia operatora zapytania agregacji standardowej, który jest unikatowy dla PLINQ. To przeciążenie <xref:System.Func%603?displayProperty=nameWithType> ma dodatkowe jako trzeci parametr wejściowy. Ten delegat łączy wyniki ze wszystkich wątków, zanim wykona ostateczne obliczenia na zagregowane wyniki. W tym przykładzie sumujemy sumy ze wszystkich wątków.  
  
 Należy zauważyć, że gdy wyrażenie lambda treści składa się <xref:System.Func%602?displayProperty=nameWithType> z pojedynczego wyrażenia, zwracana wartość delegata jest wartością wyrażenia.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
