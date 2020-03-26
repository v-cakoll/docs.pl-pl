---
title: Porównania wartości Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 697c933daeb3c68fb4ea89a957b639a79a9407f8
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249659"
---
# <a name="null-comparisons"></a>Porównania wartości Null
Wartość `null` w źródle danych wskazuje, że wartość jest nieznana. W linq do jednostek kwerendy, można sprawdzić wartości null, tak aby niektóre obliczenia lub porównania są wykonywane tylko w wierszach, które mają prawidłowe lub inne niż null, danych. Semantyka null CLR może jednak różnić się od semantyki null źródła danych. Większość baz danych używa wersji logiki o trzech wartościach do obsługi porównań wartości null. Oznacza to, że porównanie z wartością `true` `false`null nie ocenia `unknown`lub , ocenia . Często jest to implementacja ansi nulls, ale nie zawsze tak jest.  
  
 Domyślnie w programie SQL Server porównanie null-equals-null zwraca wartość null. W poniższym przykładzie wiersze, w których `ShipDate` jest null są wykluczone z zestawu wyników, a instrukcja Transact-SQL zwróci 0 wierszy.  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 To bardzo różni się od semantyki null CLR, gdzie null-equals-null porównanie zwraca true.  
  
 Następujące zapytanie LINQ jest wyrażona w clr, ale jest wykonywany w źródle danych. Ponieważ nie ma żadnej gwarancji, że semantyka CLR będą honorowane w źródle danych, oczekiwane zachowanie jest nieokreślony.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Selektory klawiszy  
 Selektor *kluczy* jest funkcją używaną w standardowych operatorach zapytań do wyodrębniania klucza z elementu. W funkcji selektora klawiszy wyrażenie można porównać ze stałą. Semantyka null CLR są wystawiane, jeśli wyrażenie jest porównywany do stałej zerowej lub jeśli dwie stałe null są porównywane. Przechowywanie semantyki null są wystawiane, jeśli dwie kolumny z wartościami null w źródle danych są porównywane. Selektory kluczy znajdują się w wielu standardowych operatorach zapytań grupowania i zamawiania, takich jak <xref:System.Linq.Queryable.GroupBy%2A>, i są używane do wybierania kluczy, za pomocą których można zamówić lub zgrupować wyniki kwerendy.  
  
## <a name="null-property-on-a-null-object"></a>Null Właściwość na null object  
 W ramach encji właściwości obiektu null mają wartość null. Podczas próby odwoływania się do właściwości obiektu null w clr, otrzymasz <xref:System.NullReferenceException>. Gdy kwerenda LINQ obejmuje właściwość obiektu null, może to spowodować niespójne zachowanie.  
  
 Na przykład w poniższej kwerendzie `NewProduct` rzutowania odbywa się w warstwie `Introduced` drzewa poleceń, co może spowodować, że właściwość jest null. Jeśli baza danych zdefiniowane null <xref:System.DateTime> porównania takie, że porównanie ocenia true, wiersz zostanie uwzględniony.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Przekazywanie kolekcji null do funkcji agregujących  
 W LINQ do jednostek, po przedyszeniu kolekcji, która obsługuje `IQueryable` do funkcji agregacji, operacje agregacji są wykonywane w bazie danych. Mogą występować różnice w wynikach kwerendy, która została wykonana w pamięci i kwerendy, która została wykonana w bazie danych. W przypadku kwerendy w pamięci, jeśli nie ma żadnych dopasowań, kwerenda zwraca zero. W bazie danych zwraca `null`tę samą kwerendę . Jeśli `null` wartość jest przekazywana do funkcji agregacji LINQ, zostanie zgłoszony wyjątek. Aby zaakceptować możliwe `null` wartości, rzutuj typy i właściwości typów, które odbierają wyniki kwerendy do typów wartości nullable.  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia w zapytaniach składnika LINQ to Entities](expressions-in-linq-to-entities-queries.md)
