---
title: Partycjonowanie danych
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 34749f9d7b137bade66b6103650871246c3cc532
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406849"
---
# <a name="partitioning-data-visual-basic"></a>Partycjonowanie danych (Visual Basic)
Partycjonowanie w LINQ odwołuje się do operacji dzielenia sekwencji wejściowej na dwie sekcje, bez konieczności ponownej rozmieszczania elementów, a następnie zwrócenia jednej z sekcji.  
  
 Na poniższej ilustracji przedstawiono wyniki trzech różnych operacji partycjonowania na sekwencji znaków. Pierwsza operacja zwraca trzy pierwsze elementy w sekwencji. Druga operacja pomija pierwsze trzy elementy i zwraca pozostałe elementy. Trzecia operacja pomija pierwsze dwa elementy w sekwencji i zwraca następne trzy elementy.  
  
 ![Ilustracja przedstawiająca trzy operacje partycjonowania LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Standardowe metody operatorów zapytań, które są sekwencje partycji, są wymienione w poniższej sekcji.  
  
## <a name="operators"></a>Operatory  
  
|Nazwa operatora|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Pomiń|Pomija elementy do określonej pozycji w sekwencji.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile —|Pomija elementy na podstawie funkcji predykatu, dopóki element nie spełnia warunku.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Pobiera elementy do określonej pozycji w sekwencji.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile —|Pobiera elementy na podstawie funkcji predykatu, dopóki element nie spełnia warunku.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="skip"></a>Pomiń  
 Poniższy przykład kodu używa `Skip` klauzuli w Visual Basic, aby pominąć pierwsze cztery ciągi w tablicy ciągów przed zwróceniem pozostałych ciągów w tablicy.  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a>SkipWhile —  
 Poniższy przykład kodu używa `Skip While` klauzuli w Visual Basic, aby pominąć ciągi w tablicy, podczas gdy pierwsza litera ciągu ma wartość "a". Zwracane są pozostałe ciągi w tablicy.  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a>Take  
 Poniższy przykład kodu używa `Take` klauzuli w Visual Basic, aby zwrócić pierwsze dwa ciągi w tablicy ciągów.  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a>TakeWhile —  
 Poniższy przykład kodu używa `Take While` klauzuli w Visual Basic, aby zwrócić ciągi z tablicy, gdy długość ciągu jest pięć lub mniej.  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [Skip, klauzula](../../../language-reference/queries/skip-clause.md)
- [Skip While, klauzula](../../../language-reference/queries/skip-while-clause.md)
- [Take, klauzula](../../../language-reference/queries/take-clause.md)
- [Take While, klauzula](../../../language-reference/queries/take-while-clause.md)
