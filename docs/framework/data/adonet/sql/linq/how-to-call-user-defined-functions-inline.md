---
title: 'Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: e9808856543e20b8904be812b15b32154eab56e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782110"
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

- [Funkcje zdefiniowane przez użytkownika](user-defined-functions.md)
