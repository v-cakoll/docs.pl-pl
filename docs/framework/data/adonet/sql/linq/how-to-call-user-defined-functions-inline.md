---
title: 'Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: e9808856543e20b8904be812b15b32154eab56e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782110"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="00fbe-102">Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="00fbe-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="00fbe-103">Chociaż można wywołać funkcje zdefiniowane przez użytkownika w tekście, funkcje, które są uwzględnione w zapytaniu, którego wykonywanie zostało odroczone, nie są wykonywane, dopóki zapytanie nie zostanie wykonane.</span><span class="sxs-lookup"><span data-stu-id="00fbe-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="00fbe-104">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="00fbe-104">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="00fbe-105">Po wywołaniu tej samej funkcji poza kwerendą, program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy proste zapytanie z wyrażenia wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="00fbe-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="00fbe-106">Poniżej przedstawiono składnię języka SQL (parametr `@p0` jest powiązany z przekazaną stałą):</span><span class="sxs-lookup"><span data-stu-id="00fbe-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="00fbe-107">tworzy następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="00fbe-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="00fbe-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="00fbe-108">Example</span></span>  
 <span data-ttu-id="00fbe-109">W poniższym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytaniu można zobaczyć wbudowane wywołanie do wygenerowanej metody `ReverseCustName`funkcji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="00fbe-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="00fbe-110">Funkcja nie jest wykonywana natychmiast, ponieważ wykonywanie zapytania zostało odroczone.</span><span class="sxs-lookup"><span data-stu-id="00fbe-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="00fbe-111">Baza danych SQL opracowana dla tego zapytania tłumaczy na wywołanie funkcji zdefiniowanej przez użytkownika w bazie kodu (Zobacz kod SQL po zapytaniu).</span><span class="sxs-lookup"><span data-stu-id="00fbe-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="00fbe-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00fbe-112">See also</span></span>

- [<span data-ttu-id="00fbe-113">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="00fbe-113">User-Defined Functions</span></span>](user-defined-functions.md)
