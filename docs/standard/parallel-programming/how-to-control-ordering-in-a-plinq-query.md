---
title: 'Instrukcje: Sterowanie szeregowaniem w zapytaniu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: 80e199d75471eba219f1f3da12d307b6cd1d90cf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285459"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Instrukcje: Sterowanie szeregowaniem w zapytaniu PLINQ
W poniższych przykładach pokazano, jak kontrolować porządkowanie w kwerendzie PLINQ przy użyciu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> metody rozszerzenia.  
  
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
  
 Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [przykład danych PLINQ Data](plinq-data-sample.md) i naciśnij klawisz F5.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zachować kolejność dla pierwszej części zapytania, a następnie usunąć kolejność, aby zwiększyć wydajność klauzuli join, a następnie ponownie zastosować porządkowanie do końcowej sekwencji wyników.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Aby uruchomić tę metodę, wklej ją do klasy PLINQDataSample w projekcie [przykład danych PLINQ Data](plinq-data-sample.md) i naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](introduction-to-plinq.md)
