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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123121"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Porady: sterowanie szeregowaniem w zapytaniu PLINQ
W poniższych przykładach pokazano, jak kontrolować porządkowanie w kwerendzie PLINQ przy użyciu metody rozszerzenia <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
> [!WARNING]
> Te przykłady są przeznaczone głównie do zademonstrowania użycia i mogą być uruchamiane szybciej niż równoważne zapytania sekwencyjne LINQ to Objects.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zachowuje kolejność sekwencji źródłowej. Jest to czasami konieczne; na przykład niektóre operatory zapytań wymagają uporządkowanej sekwencji źródłowej, aby generować poprawne wyniki.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono niektóre operatory zapytań, których sekwencja źródłowa prawdopodobnie powinna być uporządkowana. Te operatory będą działały w sekwencjach nieuporządkowanych, ale mogą generować nieoczekiwane wyniki.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [przykład danych PLINQ Data](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zachować kolejność dla pierwszej części zapytania, a następnie usunąć kolejność, aby zwiększyć wydajność klauzuli join, a następnie ponownie zastosować porządkowanie do końcowej sekwencji wyników.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [przykład danych PLINQ Data](../../../docs/standard/parallel-programming/plinq-data-sample.md) i naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
