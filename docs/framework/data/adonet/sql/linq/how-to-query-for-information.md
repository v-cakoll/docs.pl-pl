---
title: 'Porady: Kwerenda dotycząca informacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ae369cb6aaabfdf116f43629a0acb4ad9f7af8c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="0b32f-102">Porady: Kwerenda dotycząca informacji</span><span class="sxs-lookup"><span data-stu-id="0b32f-102">How to: Query for Information</span></span>
<span data-ttu-id="0b32f-103">Zapytania w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używać tej samej składni jak zapytania w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b32f-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="0b32f-104">Jedyną różnicą jest to, że obiekty przywoływane w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania są mapowane do elementów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0b32f-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="0b32f-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="0b32f-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0b32f-106"> tłumaczy zapytania zostanie zapisany na równoważne zapytania SQL, a następnie wysyła je do serwera w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="0b32f-106"> translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="0b32f-107">Niektóre funkcje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytań może być konieczne szczególną uwagę w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b32f-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="0b32f-108">Aby uzyskać więcej informacji, zobacz [pojęcia zapytania](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="0b32f-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b32f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b32f-109">Example</span></span>  
 <span data-ttu-id="0b32f-110">Następujące zapytanie zapyta, aby uzyskać listę klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="0b32f-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="0b32f-111">W tym przykładzie `Customers` jest tabela w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0b32f-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0b32f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b32f-112">See Also</span></span>  
 [<span data-ttu-id="0b32f-113">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="0b32f-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="0b32f-114">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="0b32f-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="0b32f-115">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="0b32f-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
