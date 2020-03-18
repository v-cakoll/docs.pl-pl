---
title: Składnia wyrażenia kwerendy dla standardowych operatorów kwerend (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: dac63ae165b88924cb0e91336571173f764569ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591428"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Składnia wyrażenia kwerendy dla standardowych operatorów kwerend (C#)
Niektóre z najczęściej używanych standardowych operatorów zapytań mają dedykowaną składnię słów kluczowych języka C#, która umożliwia ich wywoływanie jako część *wyrażenia zapytania*. Wyrażenie kwerendy jest inną, bardziej czytelną formą wyrażania zapytania niż jego odpowiednik *oparty na metodach.* Klauzule wyrażenia kwerendy są tłumaczone na wywołania metod kwerendy w czasie kompilacji.  
  
## <a name="query-expression-syntax-table"></a>Tabela składni wyrażenia kwerendy  
 W poniższej tabeli wymieniono standardowe operatory kwerend, które mają równoważne klauzule wyrażenia kwerendy.  
  
|Metoda|Składnia wyrażenia kwerendy c#|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Użyj jawnie wpisanej zmiennej zakresu, na przykład:<br /><br /> `from int i in numbers`<br /><br /> (Aby uzyskać więcej informacji, zobacz [z klauzuli](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> — lub —<br /><br /> `group … by … into …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [group klauzuli](../../../language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [join klauzuli](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [join klauzuli](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Aby uzyskać więcej informacji, zobacz [select klauzuli](../../../language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Wiele `from` klauzul.<br /><br /> (Aby uzyskać więcej informacji, zobacz [z klauzuli](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../../../language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [Klasyfikacja standardowych operatorów zapytań według sposobu wykonania (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
