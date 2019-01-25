---
title: Składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)
ms.date: 07/20/2015
ms.assetid: eb978d86-d3b5-497b-95ce-a054bea8f510
ms.openlocfilehash: 49a0b9d70022ee655d87b34a3bb044e1f60b308d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549681"
---
# <a name="query-expression-syntax-for-standard-query-operators-visual-basic"></a>Składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)
Niektóre z często używanych standardowych operatorów zapytań są wyposażone w dedykowane składni — słowo kluczowe języka Visual Basic, który pozwoli na można wywołać w ramach *wyrażeniu zapytania*. Wyrażenie zapytania jest inny, bardziej czytelny formularz wyrażenia kwerendy niż jego *oparte na metodzie* równoważne. Klauzule wyrażenia zapytania są tłumaczone na wywołania do metody zapytania w czasie kompilacji.  
  
## <a name="query-expression-syntax-table"></a>Tabela składni wyrażeń zapytania  
 W poniższej tabeli wymieniono standardowych operatorów zapytań, które mają klauzule wyrażenia zapytania równoważne.  
  
|Metoda|Składnia wyrażeń języka Visual Basic|  
|------------|------------------------------------------|  
|<xref:System.Linq.Enumerable.All%2A>|`Aggregate … In … Into All(…)`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Any%2A>|`Aggregate … In … Into Any()`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Average%2A>|`Aggregate … In … Into Average()`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Cast%2A>|`From … As …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Count%2A>|`Aggregate … In … Into Count()`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Distinct%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|`Distinct`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Distinct — klauzula](../../../../visual-basic/language-reference/queries/distinct-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`Group … By … Into …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [grupy przez klauzulę](../../../../visual-basic/language-reference/queries/group-by-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`Group Join … In … On …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Group Join — klauzula](../../../../visual-basic/language-reference/queries/group-join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`From x In …, y In … Where x.a = b.a`<br /><br /> —lub—<br /><br /> `Join … [As …]In … On …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli Join](../../../../visual-basic/language-reference/queries/join-clause.md).)|  
|<xref:System.Linq.Enumerable.LongCount%2A>|`Aggregate … In … Into LongCount()`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Max%2A>|`Aggregate … In … Into Max()`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Min%2A>|`Aggregate … In … Into Min()`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By … Descending`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`Select`<br /><br /> (Aby uzyskać więcej informacji, zobacz [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Wiele `From` klauzule<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Skip%2A>|`Skip`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Skip — klauzula](../../../../visual-basic/language-reference/queries/skip-clause.md).)|  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|`Skip While`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Skip While — klauzula](../../../../visual-basic/language-reference/queries/skip-while-clause.md).)|  
|<xref:System.Linq.Enumerable.Sum%2A>|`Aggregate … In … Into Sum()`<br /><br /> (Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Take%2A>|`Take`<br /><br /> (Aby uzyskać więcej informacji, zobacz [zająć klauzuli](../../../../visual-basic/language-reference/queries/take-clause.md).)|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>|`Take While`<br /><br /> (Aby uzyskać więcej informacji, zobacz [zająć While — klauzula](../../../../visual-basic/language-reference/queries/take-while-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, … Descending`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`Where`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md).)|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
