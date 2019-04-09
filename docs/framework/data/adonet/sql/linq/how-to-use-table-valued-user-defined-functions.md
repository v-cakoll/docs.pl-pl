---
title: 'Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: eedc2e9b997e91ed9fe0038f260aa475d23a0627
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186839"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a>Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika
Funkcja z wartościami przechowywanymi w tabeli zwraca pojedynczy zestaw wierszy (w przeciwieństwie do procedur przechowywanych, które mogą zwrócić wielu kształtów wyników). Ponieważ zwracany typ funkcji z wartościami przechowywanymi w tabeli jest `Table`, można użyć funkcji zwracającej tabelę dowolne miejsce w języku SQL, można użyć tabeli. Można również traktować funkcji zwracającej tabelę, tak samo jak tabeli.  
  
## <a name="example"></a>Przykład  
 Następujące instrukcje SQL jawnie funkcji stanów, które zwraca `TABLE`. W związku z tym struktura zestaw wierszy zwrócony jest niejawnie definiowany.  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje funkcji w następujący sposób:  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod SQL pokazuje, można dołączyć do tabeli, która funkcja zwraca i inaczej traktują, tak jak każdą inną tabelę:  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], zapytanie może być renderowany w następujący sposób:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
