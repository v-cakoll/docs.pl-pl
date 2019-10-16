---
title: Porównania wartości Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 8eca2ee1afec5662e40d4f43347c469bd538c066
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319501"
---
# <a name="null-comparisons"></a>Porównania wartości Null
Wartość `null` w źródle danych wskazuje, że wartość jest nieznana. W LINQ to Entities zapytaniach można sprawdzać wartości null, aby pewne obliczenia lub porównania były wykonywane tylko dla wierszy, które mają prawidłowe lub inne niż null dane. Semantyka języka CLR o wartości null może jednak różnić się od semantyki o wartości null źródła danych. Większość baz danych używa wersji logiki trójwarstwowej do obsługi porównań o wartości null. Oznacza to, że porównanie wartości null nie jest oceniane do `true` lub `false`, zostanie obliczone do `unknown`. Często jest to implementacja wartości null ANSI, ale nie zawsze jest to przypadek.  
  
 Domyślnie w SQL Server porównanie wartości null-Equals-NULL zwraca wartość null. W poniższym przykładzie wiersze, w których `ShipDate` ma wartość null, są wykluczone z zestawu wyników, a instrukcja języka Transact-SQL zwróci 0 wierszy.  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 Jest to bardzo różne od semantyki języka CLR o wartości null, gdzie porównanie NULL-Equals-NULL zwraca wartość true.  
  
 Poniższe zapytanie LINQ jest wyrażone w środowisku CLR, ale jest wykonywane w źródle danych. Ponieważ nie ma żadnej gwarancji, że semantyka środowiska CLR zostanie zastosowana w źródle danych, oczekiwane zachowanie jest nieokreślone.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Selektory kluczy  
 *Selektor klucza* jest funkcją używaną w standardowych operatorach zapytań do wyodrębniania klucza z elementu. W funkcji selektora kluczy wyrażenie można porównać z stałą. Semantyka wartości null CLR jest zaprezentowania, jeśli wyrażenie jest porównywane ze stałą o wartości null lub dwie stałe wartości null są porównywane. Semantyka wartości null magazynu jest zastawiona, jeśli dwie kolumny zawierające wartości null w źródle danych są porównywane. Selektory kluczy znajdują się w wielu standardowych operatorów zapytań grupowania i porządkowania, takich jak <xref:System.Linq.Queryable.GroupBy%2A> i są używane do wybierania kluczy, według których mają być uporządkowane lub grupowane wyniki zapytania.  
  
## <a name="null-property-on-a-null-object"></a>Właściwość null dla obiektu o wartości null  
 W Entity Framework właściwości obiektu null mają wartość null. Podczas próby odwołania się do właściwości obiektu o wartości null w środowisku CLR otrzymasz <xref:System.NullReferenceException>. Gdy zapytanie LINQ obejmuje właściwość obiektu o wartości null, może to spowodować niespójne zachowanie.  
  
 Na przykład w poniższym zapytaniu rzutowanie na `NewProduct` jest wykonywane w warstwie drzewa poleceń, co może spowodować, że właściwość `Introduced` ma wartość null. Jeśli baza danych określiła wartości null, takie jak porównanie <xref:System.DateTime> ma wartość true, wiersz zostanie uwzględniony.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Przekazywanie kolekcji o wartości null do funkcji agregujących  
 W LINQ to Entities, gdy przekażesz kolekcję obsługującą `IQueryable` do funkcji agregującej, operacje agregacji są wykonywane w bazie danych. W wyniku zapytania, które zostało wykonane w pamięci, i zapytania, które zostało wykonane w bazie danych, mogą wystąpić różnice. W zapytaniu w pamięci, jeśli nie ma żadnych dopasowań, zapytanie zwróci wartość zero. W bazie danych to samo zapytanie zwraca `null`. Jeśli wartość `null` jest przenoszona do funkcji agregującej LINQ, zostanie zgłoszony wyjątek. Aby zaakceptować możliwe wartości `null`, należy rzutować typy i właściwości typów, które odbierają wyniki zapytania na typy dopuszczające wartość null.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia w zapytaniach składnika LINQ to Entities](expressions-in-linq-to-entities-queries.md)
