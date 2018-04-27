---
title: Partycjonowanie danych (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e4e6d6db07a520b97911de5388b8e42b7e1acc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="partitioning-data-visual-basic"></a>Partycjonowanie danych (Visual Basic)
Podział na partycje w składniku LINQ odwołuje się do funkcjonowania dzielenie sekwencji wejściowych na dwie sekcje bez zmienianie rozmieszczenia elementów, a następnie zwraca w sekcji.  
  
 Na poniższej ilustracji przedstawiono wyniki trzech różnych partycjonowania operacji na sekwencję znaków. Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji. Druga operacja pomija pierwszych trzech elementów i zwraca wszystkie pozostałe elementy. Trzeci operacji pomija pierwsze dwa elementy w sekwencji i zwraca trzech kolejnych elementów.  
  
 ![LINQ partycjonowania operacji](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Metody operator standardowej kwerendy, które partycji sekwencje są wymienione w poniższej sekcji.  
  
## <a name="operators"></a>Operatory  
  
|Nazwa operatora|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|Pomija elementy do określonej pozycji w sekwencji.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Pomija elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Pobiera elementy do określonej pozycji w sekwencji.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|takeWhile|Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="skip"></a>Skip  
 Poniższy przykład kodu wykorzystuje `Skip` klauzuli w języku Visual Basic, aby pominąć pierwsze cztery ciągów w tablicy ciągów przed zwróceniem pozostałe ciągi w tablicy.  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Poniższy przykład kodu wykorzystuje `Skip While` klauzuli w języku Visual Basic można pominąć ciągów w tablicy, gdy jest pierwszą literę ciągu "". Pozostałe ciągów w tablicy są zwracane.  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 Poniższy przykład kodu wykorzystuje `Take` klauzuli w języku Visual Basic, aby powrócić do pierwsze dwa ciągi w tablicy ciągów.  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>takeWhile  
 Poniższy przykład kodu wykorzystuje `Take While` klauzuli w języku Visual Basic do zwrócenia z tablicy ciągów, gdy długość ciągu jest pięć lub mniej.  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Skip, klauzula](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Skip While, klauzula](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take, klauzula](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [Take While, klauzula](../../../../visual-basic/language-reference/queries/take-while-clause.md)
