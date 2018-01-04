---
title: "Porównania wartości null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b29caeed4bf60a5a7ad723ffd46520a89a5bd87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="null-comparisons"></a>Porównania wartości null
A `null` wartość w źródle danych wskazuje, że wartość jest nieznany. W [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] kwerendy, można sprawdzić, tak aby niektóre obliczenia wartości null lub porównania są realizowane wyłącznie na wiersze, które mają prawidłowy lub inną niż null, danych. Semantyka null CLR, jednak mogą się różnić od null semantykę źródła danych. Większość baz danych używa wersji przechowywanymi w trzech logiki do obsługi porównania wartości null. Oznacza to, że porównanie z wartością null nie zostało oszacowane jako `true` lub `false`, daje w wyniku `unknown`. Często jest to implementacja ANSI wartości null, ale nie zawsze jest wielkość liter.  
  
 Domyślnie w programie SQL Server porównanie wartości null jest równa null, zwraca wartość null. W poniższym przykładzie wiersze gdzie `ShipDate` ma wartość null, są wykluczane z zestawu wyników i [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] instrukcji zwróci 0 wierszy.  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 To bardzo różni się od CLR semantyki wartości null, gdzie porównanie wartości null jest równa null, zwraca wartość true.  
  
 Następujące zapytanie LINQ jest wyrażona w środowisku CLR, ale jest wykonywana w źródle danych. Ponieważ nie ma żadnej gwarancji, że będą honorowane semantyki CLR w źródle danych, oczekiwane zachowanie jest nieokreślony.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Selektory kluczy  
 A *selektora kluczy* to funkcja używana w standardowych operatorów zapytań można wyodrębnić klucza z elementu. W funkcji selektora kluczy wyrażenie może być porównywana ze stałą. Semantyka null CLR są wystawiane, jeśli wyrażenie jest porównywana ze stałą wartość null lub są porównywane dwie stałe wartości null. Semantyka null magazynu są wystawiane, jeśli dwie kolumny o wartości null w źródle danych są porównywane. Selektory kluczy znajdują się w wielu grupowanie i porządkowanie standardowych operatorów zapytań, takich jak <xref:System.Linq.Queryable.GroupBy%2A>i służą do Wybierz klucze za pomocą którego porządek lub grupowanie wyników zapytania.  
  
## <a name="null-property-on-a-null-object"></a>Właściwość o wartości null na obiekt zerowy  
 W [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], właściwości obiektu null mają wartość null. Podczas próby odwołania właściwości obiektu null w środowisku CLR, otrzymasz <xref:System.NullReferenceException>. Gdy zapytania LINQ obejmuje właściwości obiektu null, może to spowodować niespójne działanie.  
  
 Na przykład w następującej kwerendy, rzutowanie na `NewProduct` odbywa się na warstwie drzewa polecenia, co może spowodować `Introduced` właściwości jest null. Jeśli bazy danych zdefiniowany porównania wartości null tak, aby <xref:System.DateTime> porównania zwraca wartość true, wiersza zostaną uwzględnione.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Przekazywanie Null kolekcje w celu funkcje agregujące  
 W [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], podczas przekazywania kolekcji, która obsługuje `IQueryable` do funkcji agregującej, operacje agregacji są wykonywane na bazie danych. Mogą wystąpić różnice w wynikach zapytania, które było wykonywane w pamięci i kwerendę, która została wykonana w bazie danych. Jeśli nie ma żadnych wyników z kwerendy w pamięci, zapytanie zwraca zero. W bazie danych, takie same zapytanie zwraca `null`. Jeśli `null` wartość jest przekazywana do funkcji agregującej LINQ, zostanie wygenerowany wyjątek. Aby zaakceptować możliwe `null` rzutowania wartości, typy i właściwości typów, które odbierania wyników zapytania do typów dopuszczających wartości zerowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
