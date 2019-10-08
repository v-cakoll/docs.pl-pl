---
title: 'Instrukcje: korzystanie z funkcji zdefiniowanych przez użytkownika z wartościami przechowywanymi w tabeli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: c4b5290e4f1aa69c7f55951d526ccb303a5a95ec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003186"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="60c77-102">Instrukcje: korzystanie z funkcji zdefiniowanych przez użytkownika z wartościami przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="60c77-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="60c77-103">Funkcja zwracająca tabelę zwraca pojedynczy zestaw wierszy (w przeciwieństwie do procedur składowanych, które mogą zwracać wiele kształtów wynikowych).</span><span class="sxs-lookup"><span data-stu-id="60c77-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="60c77-104">Ponieważ zwracany typ funkcji zwracającej tabelę to `Table`, można użyć funkcji zwracającej tabelę w dowolnym miejscu w języku SQL, w której można użyć tabeli.</span><span class="sxs-lookup"><span data-stu-id="60c77-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="60c77-105">Możesz również traktować funkcję zwracającą tabelę w taki sam sposób jak tabela.</span><span class="sxs-lookup"><span data-stu-id="60c77-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60c77-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="60c77-106">Example</span></span>  
 <span data-ttu-id="60c77-107">Poniższa funkcja SQL jawnie stwierdza, że zwraca `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="60c77-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="60c77-108">W związku z tym zwracana struktura zestawu wierszy jest niejawnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="60c77-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="60c77-109">mapuje funkcję w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="60c77-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="60c77-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="60c77-110">Example</span></span>  
 <span data-ttu-id="60c77-111">Poniższy kod SQL pokazuje, że można dołączyć do tabeli, która zwraca funkcja, i w przeciwnym razie traktuje ją tak samo jak w przypadku każdej innej tabeli:</span><span class="sxs-lookup"><span data-stu-id="60c77-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="60c77-112">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytanie powinno być renderowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="60c77-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="60c77-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60c77-113">See also</span></span>

- [<span data-ttu-id="60c77-114">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="60c77-114">User-Defined Functions</span></span>](user-defined-functions.md)
