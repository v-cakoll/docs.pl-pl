---
title: 'Porady: sterowanie szeregowaniem w zapytaniu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: d38c039fa99433d9476d62c1e96dff7e306fd766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123121"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Porady: sterowanie szeregowaniem w zapytaniu PLINQ
W tych przykładach przedstawiono sposób kontrolowania kolejności w kwerendzie PLINQ przy użyciu metody <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> rozszerzenia.  
  
> [!WARNING]
> Te przykłady są przeznaczone głównie do wykazania użycia i może lub nie może działać szybciej niż równoważne sekwencyjne LINQ do obiektów zapytań.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zachowuje kolejność sekwencji źródłowej. Czasami jest to konieczne; na przykład niektóre operatory kwerend wymagają uporządkowanej sekwencji źródłowych w celu uzyskania poprawnych wyników.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono niektóre operatory zapytań, których sekwencja źródłowa prawdopodobnie ma zostać zamówiona. Te operatory będą działać na sekwencje nieuporządkowane, ale mogą one powodować nieoczekiwane wyniki.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [próbki danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zachować kolejność dla pierwszej części kwerendy, a następnie usunąć kolejność, aby zwiększyć wydajność join klauzuli, a następnie ponownie zastosować kolejność do końcowej sekwencji wyników.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [próbki danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
