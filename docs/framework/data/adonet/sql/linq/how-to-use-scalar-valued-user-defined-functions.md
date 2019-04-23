---
title: 'Instrukcje: Używanie funkcji skalarnej zdefiniowanej przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: ffb24468c81cb4ec9f41645f8888c2c4ba021609
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127179"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Instrukcje: Używanie funkcji skalarnej zdefiniowanej przez użytkownika
Można mapować metoda klienta zdefiniowana w klasie funkcji zdefiniowanych przez użytkownika przy użyciu <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu. Należy pamiętać, że treść metody tworzy wyrażenie, które przechwytuje celem wywołania metody i przekazuje to wyrażenie do <xref:System.Data.Linq.DataContext> w celu tłumaczenia i wykonania.  
  
> [!NOTE]
>  Bezpośrednie jest wykonywany tylko wtedy, gdy funkcja jest wywoływana poza zapytania. Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Przykład  
 Następujący kod SQL stanowi funkcji skalarnej zdefiniowanej przez użytkownika `ReverseCustName()`.  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 Mapującej metodę klienta dla tego kodu podobny do następującego:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
