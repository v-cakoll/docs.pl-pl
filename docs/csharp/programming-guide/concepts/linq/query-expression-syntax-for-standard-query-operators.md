---
title: Składnia wyrażeń dla standardowych operatorów zapytań (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: 48ca1173439559832ac7e578eac1e11c2bf34be2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Składnia wyrażeń dla standardowych operatorów zapytań (C#)
Niektóre z często używanych standardowych operatorów zapytań są wyposażone w dedykowane C# — słowo kluczowe składni języka umożliwiający ich można wywołać w ramach *zapytania wyrażenia*. Wyrażenia zapytania jest inny, bardziej czytelny formularz wyrażenia zapytania niż jego *oparte na metodzie* równoważne. Klauzule wyrażenia zapytania są przekształcane na wywołania metody zapytań w czasie kompilacji.  
  
## <a name="query-expression-syntax-table"></a>Tabela składni wyrażeń zapytania  
 W poniższej tabeli wymieniono standardowych operatorów zapytań zawierających klauzule wyrażenia zapytania równoważne.  
  
|Metoda|Składnia wyrażenia zapytania C#|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Można użyć zmiennej zakresu jawnie typu, na przykład:<br /><br /> `from int i in numbers`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli from](../../../../csharp/language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> —lub—<br /><br /> `group … by … into …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli group](../../../../csharp/language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Wiele `from` klauzul.<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzuli from](../../../../csharp/language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Aby uzyskać więcej informacji, zobacz [klauzula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Aby uzyskać więcej informacji, zobacz [gdzie klauzuli](../../../../csharp/language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
