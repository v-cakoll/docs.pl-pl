---
title: "Porady: Użyj przechowywanymi w tabeli funkcji zdefiniowanej przez użytkownika"
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
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58a1803618845e3914d57d425a1b3d1e5e857aac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-table-valued-user-defined-functions"></a>Porady: Użyj przechowywanymi w tabeli funkcji zdefiniowanej przez użytkownika
Funkcja przechowywanymi w tabeli zwraca pojedynczy zestaw wierszy (w przeciwieństwie do procedur składowanych, które można zwrócić wielu kształtów wyników). Ponieważ typ zwracany funkcji zwracającej tabelę jest `Table`, można użyć funkcji zwracającej tabelę dowolne miejsce w języku SQL, których można używać tabeli. Można również traktować funkcji zwracającej tabelę, tak jak w tabeli.  
  
## <a name="example"></a>Przykład  
 Następujące instrukcje SQL jawnie funkcji stanów, które zwraca `TABLE`. W związku z tym struktury zestaw wierszy zwrócony niejawnie jest zdefiniowany.  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje funkcji w następujący sposób:  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod SQL przedstawia można dołączyć do tabeli, która zwraca funkcję i inaczej traktować jak w przypadku innych tabeli:  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], zapytanie może być renderowane w następujący sposób:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
