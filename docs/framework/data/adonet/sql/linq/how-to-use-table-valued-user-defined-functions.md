---
title: 'Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 31797ae7d0fe23227cc4af733fbceac5d474f779
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781446"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a>Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika
Funkcja zwracająca tabelę zwraca pojedynczy zestaw wierszy (w przeciwieństwie do procedur składowanych, które mogą zwracać wiele kształtów wynikowych). Ponieważ zwracany typ funkcji zwracającej tabelę to `Table`, można użyć funkcji zwracającej tabelę w dowolnym miejscu w języku SQL, w której można użyć tabeli. Możesz również traktować funkcję zwracającą tabelę w taki sam sposób jak tabela.  
  
## <a name="example"></a>Przykład  
 Poniższa funkcja SQL jawnie stwierdza, że zwraca `TABLE`. W związku z tym zwracana struktura zestawu wierszy jest niejawnie zdefiniowana.  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje funkcję w następujący sposób:  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod SQL pokazuje, że można dołączyć do tabeli, która zwraca funkcja, i w przeciwnym razie traktuje ją tak samo jak w przypadku każdej innej tabeli:  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie zapytanie powinno być renderowane w następujący sposób:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje zdefiniowane przez użytkownika](user-defined-functions.md)
