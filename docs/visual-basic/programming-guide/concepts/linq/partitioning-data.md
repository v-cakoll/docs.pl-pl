---
title: Partycjonowanie danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: afbbd479d3dadd69b81cdd6aead0a4263b92dfe9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728271"
---
# <a name="partitioning-data-visual-basic"></a>Partycjonowanie danych (Visual Basic)
Partycjonowanie w składniku LINQ odnosi się do funkcjonowania dzielenie sekwencji wejściowych na dwie sekcje bez rozmieszczanie elementów, a następnie powrotu w sekcji.  
  
 Poniższa ilustracja przedstawia wyniki trzech różnych partycjonowania operacji na sekwencję znaków. Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji. Drugą operację pomija pierwszych trzech elementów i zwraca wszystkie pozostałe elementy. Operacja trzeci pomija pierwszych dwóch elementów w sekwencji i zwraca następne trzy elementy.  
  
 ![Partycjonowanie Operacje LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Metody standardowego operatora zapytań, partycji sekwencji, które są wymienione w poniższej sekcji.  
  
## <a name="operators"></a>Operatory  
  
|Nazwa operatora|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|Pomija elementy do określonej pozycji w sekwencji.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Pomija elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Pobiera elementy do określonej pozycji w sekwencji.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="skip"></a>Skip  
 Poniższy przykład kodu wykorzystuje `Skip` klauzuli w Visual Basic, aby pominąć pierwsze cztery ciągi w tablicy ciągów przed zwróceniem pozostałe ciągi w tablicy.  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Poniższy przykład kodu wykorzystuje `Skip While` klauzuli w Visual Basic, aby pominąć ciągów w tablicy, podczas pierwszej litery w ciągu "". Pozostałe parametry w tablicy są zwracane.  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 Poniższy przykład kodu wykorzystuje `Take` klauzuli w języku Visual Basic, aby zwrócić pierwsze dwa ciągi w tablicy ciągów.  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 Poniższy przykład kodu wykorzystuje `Take While` klauzuli w języku Visual Basic do zwrócenia z tablicy ciągów, podczas gdy długość ciągu jest pięć lub mniej.  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Skip, klauzula](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [Skip While, klauzula](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take, klauzula](../../../../visual-basic/language-reference/queries/take-clause.md)
- [Take While, klauzula](../../../../visual-basic/language-reference/queries/take-while-clause.md)
