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
ms.openlocfilehash: 86011cff71fabed5e47e085f91b1759238638c9a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588490"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Porady: sterowanie szeregowaniem w zapytaniu PLINQ
Te przykłady pokazują, jak kontrolować kolejność w kwerendzie <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> PLINQ przy użyciu metody rozszerzenia.  
  
> [!WARNING]
> Te przykłady są przeznaczone przede wszystkim do wykazania użycia i może lub nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerend obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zachowuje kolejność sekwencji źródłowej. Czasami jest to konieczne; na przykład niektóre operatory zapytań wymagają uporządkowanej sekwencji źródłowej do uzyskania poprawnych wyników.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje niektóre operatory zapytań, których sekwencja źródło prawdopodobnie oczekuje się, że zostanie uporządkowany. Te operatory będą pracować nad sekwencjami nieuiarszowanymi, ale mogą one przynieść nieoczekiwane wyniki.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zachować kolejność dla pierwszej części kwerendy, a następnie usunąć kolejność, aby zwiększyć wydajność klauzuli sprzężenia, a następnie ponownie zasądzenie kolejności do sekwencji wyników końcowych.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
