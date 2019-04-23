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
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="75b39-102">Instrukcje: Używanie funkcji skalarnej zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="75b39-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="75b39-103">Można mapować metoda klienta zdefiniowana w klasie funkcji zdefiniowanych przez użytkownika przy użyciu <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="75b39-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="75b39-104">Należy pamiętać, że treść metody tworzy wyrażenie, które przechwytuje celem wywołania metody i przekazuje to wyrażenie do <xref:System.Data.Linq.DataContext> w celu tłumaczenia i wykonania.</span><span class="sxs-lookup"><span data-stu-id="75b39-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75b39-105">Bezpośrednie jest wykonywany tylko wtedy, gdy funkcja jest wywoływana poza zapytania.</span><span class="sxs-lookup"><span data-stu-id="75b39-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="75b39-106">Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="75b39-106">For more information, see [How to: Call User-Defined Functions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75b39-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="75b39-107">Example</span></span>  
 <span data-ttu-id="75b39-108">Następujący kod SQL stanowi funkcji skalarnej zdefiniowanej przez użytkownika `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="75b39-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
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
  
 <span data-ttu-id="75b39-109">Mapującej metodę klienta dla tego kodu podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="75b39-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="75b39-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75b39-110">See also</span></span>

- [<span data-ttu-id="75b39-111">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="75b39-111">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
