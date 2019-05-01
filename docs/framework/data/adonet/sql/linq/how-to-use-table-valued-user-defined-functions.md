---
title: 'Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: eedc2e9b997e91ed9fe0038f260aa475d23a0627
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033595"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="a2e00-102">Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="a2e00-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="a2e00-103">Funkcja z wartościami przechowywanymi w tabeli zwraca pojedynczy zestaw wierszy (w przeciwieństwie do procedur przechowywanych, które mogą zwrócić wielu kształtów wyników).</span><span class="sxs-lookup"><span data-stu-id="a2e00-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="a2e00-104">Ponieważ zwracany typ funkcji z wartościami przechowywanymi w tabeli jest `Table`, można użyć funkcji zwracającej tabelę dowolne miejsce w języku SQL, można użyć tabeli.</span><span class="sxs-lookup"><span data-stu-id="a2e00-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="a2e00-105">Można również traktować funkcji zwracającej tabelę, tak samo jak tabeli.</span><span class="sxs-lookup"><span data-stu-id="a2e00-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2e00-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2e00-106">Example</span></span>  
 <span data-ttu-id="a2e00-107">Następujące instrukcje SQL jawnie funkcji stanów, które zwraca `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="a2e00-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="a2e00-108">W związku z tym struktura zestaw wierszy zwrócony jest niejawnie definiowany.</span><span class="sxs-lookup"><span data-stu-id="a2e00-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a2e00-109">mapuje funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a2e00-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a2e00-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2e00-110">Example</span></span>  
 <span data-ttu-id="a2e00-111">Poniższy kod SQL pokazuje, można dołączyć do tabeli, która funkcja zwraca i inaczej traktują, tak jak każdą inną tabelę:</span><span class="sxs-lookup"><span data-stu-id="a2e00-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="a2e00-112">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], zapytanie może być renderowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a2e00-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a2e00-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2e00-113">See also</span></span>

- [<span data-ttu-id="a2e00-114">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="a2e00-114">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
