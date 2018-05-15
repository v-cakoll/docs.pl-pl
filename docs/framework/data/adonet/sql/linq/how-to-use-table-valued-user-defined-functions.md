---
title: 'Porady: Użyj przechowywanymi w tabeli funkcji zdefiniowanej przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: e0199bb0a783f54931885053681c48d288012404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="9f622-102">Porady: Użyj przechowywanymi w tabeli funkcji zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="9f622-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="9f622-103">Funkcja przechowywanymi w tabeli zwraca pojedynczy zestaw wierszy (w przeciwieństwie do procedur składowanych, które można zwrócić wielu kształtów wyników).</span><span class="sxs-lookup"><span data-stu-id="9f622-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="9f622-104">Ponieważ typ zwracany funkcji zwracającej tabelę jest `Table`, można użyć funkcji zwracającej tabelę dowolne miejsce w języku SQL, których można używać tabeli.</span><span class="sxs-lookup"><span data-stu-id="9f622-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="9f622-105">Można również traktować funkcji zwracającej tabelę, tak jak w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9f622-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f622-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f622-106">Example</span></span>  
 <span data-ttu-id="9f622-107">Następujące instrukcje SQL jawnie funkcji stanów, które zwraca `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="9f622-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="9f622-108">W związku z tym struktury zestaw wierszy zwrócony niejawnie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="9f622-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9f622-109"> mapuje funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9f622-109"> maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9f622-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f622-110">Example</span></span>  
 <span data-ttu-id="9f622-111">Poniższy kod SQL przedstawia można dołączyć do tabeli, która zwraca funkcję i inaczej traktować jak w przypadku innych tabeli:</span><span class="sxs-lookup"><span data-stu-id="9f622-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="9f622-112">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], zapytanie może być renderowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9f622-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9f622-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f622-113">See Also</span></span>  
 [<span data-ttu-id="9f622-114">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="9f622-114">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
