---
title: Operacje agregacji (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 5d8e5c589b19527062f7752b2f795c8396683bbd
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675643"
---
# <a name="aggregation-operations-visual-basic"></a>Operacje agregacji (Visual Basic)
Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości. Przykładem operacji agregacji obliczania średniej temperatury codzienne z miesięcznej codzienne wartości temperatury.  
  
 Poniższa ilustracja przedstawia wyniki dwie operacje różnych agregacji w sekwencji liczb. Pierwszą operacją sumuje się liczby. Druga operacja zwraca maksymalną wartość w sekwencji.  
  
 ![Ilustracja przedstawiająca operacje agregacji LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Metody standardowego operatora zapytań, które wykonują operacje agregacji są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Agregowanie|Wykonuje operację agregacji niestandardowej na podstawie wartości w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Średnia|Oblicza średnią wartość zbiór wartości.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Licznik|Liczba elementów w kolekcji, opcjonalnie tylko te elementy, które spełniają wymagania funkcji predykatu.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Liczba elementów w dużych kolekcji, opcjonalnie tylko te elementy, które spełniają wymagania funkcji predykatu.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks.|Określa maksymalną wartość w kolekcji.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min.|Określa minimalną wartość w kolekcji.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Suma|Oblicza sumę wartości w kolekcji.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="average"></a>Średnia  
 Poniższy przykład kodu wykorzystuje `Aggregate Into Average` klauzuli w języku Visual Basic, aby obliczyć średnią temperaturę w tablicy liczb, które reprezentują temperatury.  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>Licznik  
 Poniższy przykład kodu wykorzystuje `Aggregate Into Count` klauzuli w Visual Basic, aby określić liczbę wartości w tablicy, które są większe niż lub równy 80.  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 Poniższy przykład kodu wykorzystuje `Aggregate Into LongCount` klauzuli, aby określić liczbę wartości w tablicy.  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>Maks.  
 Poniższy przykład kodu wykorzystuje `Aggregate Into Max` klauzuli do obliczania maksymalna temperatura w tablicy liczb, które reprezentują temperatury.  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>Min.  
 Poniższy przykład kodu wykorzystuje `Aggregate Into Min` klauzuli do obliczania minimalna temperatura w tablicy liczb, które reprezentują temperatury.  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>Suma  
 Poniższy przykład kodu wykorzystuje `Aggregate Into Sum` klauzuli w celu obliczania wydatków łączna ilość z tablicy wartości, które reprezentują wydatki.  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Instrukcje: Obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Instrukcje: Liczba, Suma lub średnia danych](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [Instrukcje: Znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [Instrukcje: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
