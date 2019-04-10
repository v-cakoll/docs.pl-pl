---
title: Porównania wartości Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: a9e519fb8b2ca021d66adb23659d83efc571afae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222669"
---
# <a name="null-comparisons"></a>Porównania wartości Null
A `null` wartości w źródle danych wskazuje, czy wartość jest nieznany. W [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania, można sprawdzić w przypadku wartości null wartości, tak aby niektóre obliczeń lub porównania są realizowane wyłącznie na wiersze, które mają prawidłowy lub innych niż null, danych. Semantyka wartości null CLR, jednak może różnić się od semantyka wartości null, źródła danych. Większość baz danych użyć wersji przechowywanymi w trzech logiki do obsługi porównania wartości null. Oznacza to, że porównanie z wartością null nie można rozpoznać `true` lub `false`, daje w wyniku `unknown`. Często jest to implementacja ANSI na wartości null, ale nie zawsze jest to wymagane.  
  
 Domyślnie w programie SQL Server porównywanie wartości null jest równa null, zwraca wartość null. W poniższym przykładzie wiersze gdzie `ShipDate` ma wartość null są wykluczone z zestawu wyników i [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] instrukcji zwróci 0 wierszy.  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 To bardzo różni się od semantyki null CLR, gdzie porównanie wartości null jest równa null, zwraca wartość true.  
  
 Następujące zapytanie LINQ jest wyrażona w CLR, ale jest ono wykonywane w źródle danych. Ponieważ nie ma żadnej gwarancji, że semantykę środowiska CLR będzie honorowane w źródle danych, oczekiwane zachowanie jest nieokreślone.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Selektory kluczy  
 A *selektora kluczy* to funkcja używana w standardowych operatorów zapytań do wyodrębniania klucza z elementu. W funkcji selektora kluczy można porównać wyrażenia ze stałą. Semantyka wartości null CLR są wystawiane, jeśli wyrażenie jest porównywana ze stałą wartość null lub są porównywane dwie stałe wartości null. Semantyka wartości null Store są uwidocznione jeżeli porównywane są dwie kolumny z wartościami null w źródle danych. Selektory kluczy znajdują się w wielu grupowanie i kolejność standardowych operatorów zapytań, takich jak <xref:System.Linq.Queryable.GroupBy%2A>i są używane do Wybierz klucze za pomocą którego do zamówienia lub grupowanie wyników zapytania.  
  
## <a name="null-property-on-a-null-object"></a>Właściwość o wartości null w obiekcie o wartości Null  
 W [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], właściwości null obiektu ma wartość null. Przy próbie odwoływać się do właściwości obiektu o wartości null w CLR zostanie wyświetlony <xref:System.NullReferenceException>. Gdy zapytanie LINQ obejmuje właściwości obiektu o wartości null, może to spowodować niespójne zachowanie.  
  
 Na przykład w następującym zapytaniem, rzutowanie na `NewProduct` odbywa się w warstwie drzewa poleceń, co może spowodować `Introduced` właściwość on wartość null. Jeśli baza danych zdefiniowana porównania wartości null, <xref:System.DateTime> porównania jest spełniony, wiersza zostaną uwzględnione.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Przekazywanie kolekcji o wartości Null do funkcji agregacji  
 W [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], jeśli przekazujesz kolekcji, która obsługuje `IQueryable` do funkcji agregującej, operacje agregacji są wykonywane w bazie danych. Może to być różnice w wynikach zapytania, które były wykonywane w pamięci i zapytania, które zostało wykonane w bazie danych. Za pomocą zapytania w pamięci Jeśli brak dopasowań, zapytanie zwraca zero. W bazie danych, takie same zapytanie zwraca `null`. Jeśli `null` wartość jest przekazywana do funkcji agregującej LINQ, zostanie zgłoszony wyjątek. Aby zaakceptować to możliwe `null` wartości rzutowania typów i właściwości typów, które odbierają wyników zapytania do typów dopuszczających wartości null.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
