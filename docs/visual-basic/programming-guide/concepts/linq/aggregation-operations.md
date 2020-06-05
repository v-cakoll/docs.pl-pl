---
title: Operacje agregacji
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 8e2c9698de67dc4def348a03c9d69713a6130f31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383796"
---
# <a name="aggregation-operations-visual-basic"></a>Operacje agregacji (Visual Basic)
Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości. Przykład operacji agregacji oblicza średnią dzienną temperaturę od miesięcznej wartości dziennej temperatury.  
  
 Na poniższej ilustracji przedstawiono wyniki dwóch różnych operacji agregacji w sekwencji liczb. Pierwsza operacja sumuje liczby. Druga operacja zwraca maksymalną wartość w sekwencji.  
  
 ![Ilustracja przedstawiająca operacje agregacji LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują operacje agregacji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Agregacja|Wykonuje niestandardową operację agregacji na wartościach kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Średnia|Oblicza średnią wartość kolekcji wartości.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Liczba|Zlicza elementy w kolekcji, opcjonalnie tylko te elementy, które spełniają funkcję predykatu.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Zlicza elementy w dużej kolekcji, opcjonalnie tylko te elementy, które spełniają funkcję predykatu.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks.|Określa maksymalną wartość w kolekcji.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min.|Określa minimalną wartość w kolekcji.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Suma|Oblicza sumę wartości w kolekcji.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="average"></a>Średnia  
 Poniższy przykład kodu używa `Aggregate Into Average` klauzuli w Visual Basic, aby obliczyć średnią temperaturę w tablicy liczb reprezentujących temperatury.  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>Liczba  
 Poniższy przykład kodu używa `Aggregate Into Count` klauzuli w Visual Basic, aby policzyć liczbę wartości w tablicy, która jest większa lub równa 80.  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 Poniższy przykład kodu używa klauzuli, `Aggregate Into LongCount` aby policzyć liczbę wartości w tablicy.  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>Maks.  
 Poniższy przykład kodu używa klauzuli, `Aggregate Into Max` Aby obliczyć maksymalną temperaturę w tablicy liczb reprezentujących temperatury.  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>Min.  
 Poniższy przykład kodu używa klauzuli, `Aggregate Into Min` Aby obliczyć minimalną temperaturę w tablicy liczb reprezentujących temperatury.  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>Suma  
 Poniższy przykład kodu używa klauzuli, `Aggregate Into Sum` Aby obliczyć łączną kwotę wydatków z tablicy wartości, która reprezentuje wydatki.  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [Aggregate, klauzula](../../../language-reference/queries/aggregate-clause.md)
- [Instrukcje: Obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Instrukcje: zliczanie, sumowanie lub średnie dane](../../language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [Instrukcje: Znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania](../../language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [Instrukcje: zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (Visual Basic)](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [Instrukcje: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
