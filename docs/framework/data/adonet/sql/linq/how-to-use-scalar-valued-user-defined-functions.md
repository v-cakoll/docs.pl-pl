---
title: 'Instrukcje: Używanie funkcji skalarnej zdefiniowanej przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: da4e5e8fe4682191a0c8e2b0ce6a7b945fe63deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781474"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Instrukcje: Używanie funkcji skalarnej zdefiniowanej przez użytkownika
Można zmapować metodę klienta zdefiniowaną w klasie do funkcji zdefiniowanej przez użytkownika przy użyciu <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu. Należy zauważyć, że treść metody konstruuje wyrażenie, które przechwytuje zamiar wywołania metody i przekazuje to wyrażenie do <xref:System.Data.Linq.DataContext> translacji i wykonywania.  
  
> [!NOTE]
> Bezpośrednie wykonanie odbywa się tylko wtedy, gdy funkcja jest wywoływana poza zapytaniem. Aby uzyskać więcej informacji, zobacz [jak: Wywołaj wbudowane](how-to-call-user-defined-functions-inline.md)funkcje zdefiniowane przez użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy kod SQL przedstawia funkcję `ReverseCustName()`skalarną zdefiniowaną przez użytkownika.  
  
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
  
 Należy zmapować metodę klienta, na przykład następujące dla tego kodu:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje zdefiniowane przez użytkownika](user-defined-functions.md)
