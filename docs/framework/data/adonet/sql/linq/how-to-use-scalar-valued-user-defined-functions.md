---
title: "Porady: Użyj funkcji skalarnej zdefiniowanej przez użytkownika"
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
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a70d46362ef8b2be0533a1530c79124c464375af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Porady: Użyj funkcji skalarnej zdefiniowanej przez użytkownika
Zdefiniowany w klasie w funkcji zdefiniowanej przez użytkownika przy użyciu metody klienta można mapować <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu. Należy pamiętać, że treść metody tworzy wyrażenie, które znajdują się próba wywołania metody i przekazuje tego wyrażenia do <xref:System.Data.Linq.DataContext> tłumaczenia i wykonywania.  
  
> [!NOTE]
>  Bezpośrednie wykonywanie występuje tylko wtedy, gdy funkcja jest wywoływana poza zapytaniem. Aby uzyskać więcej informacji, zobacz [porady: wbudowane funkcje Call User-Defined](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).  
  
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
  
 Czy mapy metodę klienta, takich jak dla tego kodu:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
