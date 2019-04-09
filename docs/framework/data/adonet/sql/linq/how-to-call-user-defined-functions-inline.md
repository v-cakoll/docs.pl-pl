---
title: 'Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: ed8071352902b8f97445cbfa5ff0ebe8fead9bb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163712"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="b9d94-102">Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="b9d94-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="b9d94-103">Mimo że można wywołać wbudowanych funkcji zdefiniowanych przez użytkownika, funkcji, które są uwzględnione w zapytaniu, których wykonanie jest odroczone nie są wykonywane, dopóki zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="b9d94-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="b9d94-104">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="b9d94-104">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="b9d94-105">Po wywołaniu tej samej funkcji poza zapytaniem, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy proste zapytanie na podstawie wyrażenia wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="b9d94-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="b9d94-106">Poniżej przedstawiono składnię SQL (parametr `@p0` jest powiązana ze stałą przekazanej):</span><span class="sxs-lookup"><span data-stu-id="b9d94-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b9d94-107">tworzy następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b9d94-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="b9d94-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9d94-108">Example</span></span>  
 <span data-ttu-id="b9d94-109">W następującym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania, możesz zobaczyć wbudowany wywołanie do metody w generowanej funkcji zdefiniowanych przez użytkownika `ReverseCustName`.</span><span class="sxs-lookup"><span data-stu-id="b9d94-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="b9d94-110">Funkcja nie jest wykonywane natychmiast, ponieważ wykonanie zapytania jest odroczone.</span><span class="sxs-lookup"><span data-stu-id="b9d94-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="b9d94-111">SQL opracowana z myślą o tej kwerendy przekłada się na wywołanie funkcji zdefiniowanych przez użytkownika w bazie danych (zobacz kod SQL, następujące zapytanie).</span><span class="sxs-lookup"><span data-stu-id="b9d94-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9d94-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9d94-112">See also</span></span>

- [<span data-ttu-id="b9d94-113">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="b9d94-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
