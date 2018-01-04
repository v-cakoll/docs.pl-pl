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
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="9a4e3-102">Porady: Użyj funkcji skalarnej zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="9a4e3-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="9a4e3-103">Zdefiniowany w klasie w funkcji zdefiniowanej przez użytkownika przy użyciu metody klienta można mapować <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9a4e3-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="9a4e3-104">Należy pamiętać, że treść metody tworzy wyrażenie, które znajdują się próba wywołania metody i przekazuje tego wyrażenia do <xref:System.Data.Linq.DataContext> tłumaczenia i wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9a4e3-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a4e3-105">Bezpośrednie wykonywanie występuje tylko wtedy, gdy funkcja jest wywoływana poza zapytaniem.</span><span class="sxs-lookup"><span data-stu-id="9a4e3-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="9a4e3-106">Aby uzyskać więcej informacji, zobacz [porady: wbudowane funkcje Call User-Defined](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="9a4e3-106">For more information, see [How to: Call User-Defined Functions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a4e3-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a4e3-107">Example</span></span>  
 <span data-ttu-id="9a4e3-108">Następujący kod SQL stanowi funkcji skalarnej zdefiniowanej przez użytkownika `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="9a4e3-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
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
  
 <span data-ttu-id="9a4e3-109">Czy mapy metodę klienta, takich jak dla tego kodu:</span><span class="sxs-lookup"><span data-stu-id="9a4e3-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9a4e3-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a4e3-110">See Also</span></span>  
 [<span data-ttu-id="9a4e3-111">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="9a4e3-111">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
