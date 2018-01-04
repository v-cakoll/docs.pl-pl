---
title: "Porady: wywołanie wbudowane funkcje zdefiniowane przez użytkownika"
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
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ff5d344c5c6f8c580dd521ffc97274f00935b434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="2a85c-102">Porady: wywołanie wbudowane funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="2a85c-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="2a85c-103">Mimo że można wywołać wbudowane funkcje zdefiniowane przez użytkownika, funkcji, które są uwzględnione w zapytaniu, których wykonanie została odroczona nie są wykonywane, dopóki zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="2a85c-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="2a85c-104">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="2a85c-104">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="2a85c-105">Podczas wywoływania tej samej funkcji poza zapytaniem, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy prostego zapytania z wyrażenia wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="2a85c-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="2a85c-106">Oto składnia SQL (parametr `@p0` jest powiązany ze stałą przekazano):</span><span class="sxs-lookup"><span data-stu-id="2a85c-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2a85c-107">tworzy następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2a85c-107"> creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="2a85c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a85c-108">Example</span></span>  
 <span data-ttu-id="2a85c-109">W następujących [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania, zostanie wyświetlony wbudowanego wywołanie metody generowanej funkcji zdefiniowanej przez użytkownika `ReverseCustName`.</span><span class="sxs-lookup"><span data-stu-id="2a85c-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="2a85c-110">Funkcja nie została wykonana natychmiast, ponieważ wykonywanie zapytania została odroczona.</span><span class="sxs-lookup"><span data-stu-id="2a85c-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="2a85c-111">SQL zbudowanych dla tego zapytania przekłada się na wywołanie funkcji zdefiniowanej przez użytkownika w bazie danych (zobacz kod SQL następującej kwerendy).</span><span class="sxs-lookup"><span data-stu-id="2a85c-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a85c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a85c-112">See Also</span></span>  
 [<span data-ttu-id="2a85c-113">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="2a85c-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
