---
title: 'Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 31797ae7d0fe23227cc4af733fbceac5d474f779
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781446"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="1c3b0-102">Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1c3b0-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="1c3b0-103">Funkcja zwracająca tabelę zwraca pojedynczy zestaw wierszy (w przeciwieństwie do procedur składowanych, które mogą zwracać wiele kształtów wynikowych).</span><span class="sxs-lookup"><span data-stu-id="1c3b0-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="1c3b0-104">Ponieważ zwracany typ funkcji zwracającej tabelę to `Table`, można użyć funkcji zwracającej tabelę w dowolnym miejscu w języku SQL, w której można użyć tabeli.</span><span class="sxs-lookup"><span data-stu-id="1c3b0-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="1c3b0-105">Możesz również traktować funkcję zwracającą tabelę w taki sam sposób jak tabela.</span><span class="sxs-lookup"><span data-stu-id="1c3b0-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c3b0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c3b0-106">Example</span></span>  
 <span data-ttu-id="1c3b0-107">Poniższa funkcja SQL jawnie stwierdza, że zwraca `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="1c3b0-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="1c3b0-108">W związku z tym zwracana struktura zestawu wierszy jest niejawnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="1c3b0-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1c3b0-109">mapuje funkcję w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1c3b0-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="1c3b0-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c3b0-110">Example</span></span>  
 <span data-ttu-id="1c3b0-111">Poniższy kod SQL pokazuje, że można dołączyć do tabeli, która zwraca funkcja, i w przeciwnym razie traktuje ją tak samo jak w przypadku każdej innej tabeli:</span><span class="sxs-lookup"><span data-stu-id="1c3b0-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="1c3b0-112">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie zapytanie powinno być renderowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1c3b0-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1c3b0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c3b0-113">See also</span></span>

- [<span data-ttu-id="1c3b0-114">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1c3b0-114">User-Defined Functions</span></span>](user-defined-functions.md)
