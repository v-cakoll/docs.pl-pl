---
title: 'Instrukcje: Pisanie niestandardowej funkcji agregowania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 644d6b6f929e040a0fe688c18c774de6f434c4b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290775"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Instrukcje: Pisanie niestandardowej funkcji agregowania w PLINQ
Ten przykład pokazuje, jak używać <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metody do zastosowania niestandardowej funkcji agregacji do sekwencji źródłowej.  
  
> [!WARNING]
> Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład oblicza odchylenie standardowe sekwencji liczb całkowitych.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 W tym przykładzie użyto przeciążenia standardowego operatora kwerendy agregującej, który jest unikatowy dla PLINQ. To Przeciążenie pobiera dodatkowy <xref:System.Func%603?displayProperty=nameWithType> jako trzeci parametr wejściowy. Ten delegat łączy wyniki ze wszystkich wątków przed wykonaniem obliczenia końcowego na zagregowanych wynikach. W tym przykładzie dodamy razem kwoty ze wszystkich wątków.  
  
 Należy zauważyć, że gdy treść wyrażenia lambda składa się z pojedynczego wyrażenia, wartość zwracana <xref:System.Func%602?displayProperty=nameWithType> delegata to wartość wyrażenia.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](introduction-to-plinq.md)
