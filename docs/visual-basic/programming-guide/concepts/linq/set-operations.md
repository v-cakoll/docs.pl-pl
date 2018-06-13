---
title: Operacje na zestawie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 2620fa02c8f1f07edbf149c3202af8ab1decc072
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652529"
---
# <a name="set-operations-visual-basic"></a>Operacje na zestawie (Visual Basic)
Operacje na zestawie w składniku LINQ odwoływać się do operacji zapytania, które wywołują zestaw wyników, który jest oparty na obecności lub braku równoważne elementów w obrębie tego samego lub oddzielne kolekcje (lub zestawy).  
  
 Metody operator standardowe zapytań, które wykonują operacje na zestawie są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|Usuwa zduplikowane wartości z kolekcji.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Z wyjątkiem|Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie są widoczne w druga kolekcja.|Nie dotyczy.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|INTERSECT|Zwraca część wspólną zestawu, co oznacza elementy, które są wyświetlane w każdym z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Union|Zwraca zestaw, co oznacza unikatowych elementów, które pojawiają się w jednym z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porównanie operacje na zestawie  
  
### <a name="distinct"></a>Distinct  
 Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody w sekwencji znaków. Zwrócony sekwencja zawiera elementy unikatowe z sekwencji wejściowych.  
  
 ![Grafika przedstawiająca zachowanie Distinct&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Różne")  
  
### <a name="except"></a>Z wyjątkiem  
 Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Zwrócony sekwencja zawiera tylko elementy z pierwszego sekwencji wejściowych, które nie znajdują się w drugim sekwencji wejściowych.  
  
 ![Grafika przedstawiająca działania z wyjątkiem&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "z wyjątkiem")  
  
### <a name="intersect"></a>INTERSECT  
 Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Zwrócony sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.  
  
 ![Grafika przedstawiająca część wspólną dwóch sekwencji. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>Union  
 Na poniższej ilustracji przedstawiono Unii operacji na dwóch sekwencji znaków. Zwrócony sekwencja zawiera elementy unikatowe z obu sekwencji wejściowych.  
  
 ![Grafika przedstawiająca złożenie dwóch sekwencji. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Unii")  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 W poniższym przykładzie użyto `Distinct` podklauzul LINQ zwracać unikatowe numery z listy liczb całkowitych.  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Distinct, klauzula](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Porady: łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [Porady: znajdowanie różnicy pomiędzy dwoma listami (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
