---
title: 'Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 26eafb9a6ea1a0b416d205e94b0e420b0f4059d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941072"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika
Chociaż można wywołać funkcje zdefiniowane przez użytkownika w tekście, funkcje, które są uwzględnione w zapytaniu, którego wykonywanie zostało odroczone, nie są wykonywane, dopóki zapytanie nie zostanie wykonane. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Po wywołaniu tej samej funkcji poza kwerendą, program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy proste zapytanie z wyrażenia wywołania metody. Poniżej przedstawiono składnię języka SQL (parametr `@p0` jest powiązany z przekazaną stałą):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tworzy następujące elementy:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Przykład  
 W poniższym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytaniu można zobaczyć wbudowane wywołanie do wygenerowanej metody `ReverseCustName`funkcji zdefiniowanej przez użytkownika. Funkcja nie jest wykonywana natychmiast, ponieważ wykonywanie zapytania zostało odroczone. Baza danych SQL opracowana dla tego zapytania tłumaczy na wywołanie funkcji zdefiniowanej przez użytkownika w bazie kodu (Zobacz kod SQL po zapytaniu).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
