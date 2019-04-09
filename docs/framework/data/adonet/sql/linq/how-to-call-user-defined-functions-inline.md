---
title: 'Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: ed8071352902b8f97445cbfa5ff0ebe8fead9bb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163712"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika
Mimo że można wywołać wbudowanych funkcji zdefiniowanych przez użytkownika, funkcji, które są uwzględnione w zapytaniu, których wykonanie jest odroczone nie są wykonywane, dopóki zapytanie jest wykonywane. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Po wywołaniu tej samej funkcji poza zapytaniem, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy proste zapytanie na podstawie wyrażenia wywołania metody. Poniżej przedstawiono składnię SQL (parametr `@p0` jest powiązana ze stałą przekazanej):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy następujące czynności:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Przykład  
 W następującym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania, możesz zobaczyć wbudowany wywołanie do metody w generowanej funkcji zdefiniowanych przez użytkownika `ReverseCustName`. Funkcja nie jest wykonywane natychmiast, ponieważ wykonanie zapytania jest odroczone. SQL opracowana z myślą o tej kwerendy przekłada się na wywołanie funkcji zdefiniowanych przez użytkownika w bazie danych (zobacz kod SQL, następujące zapytanie).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
