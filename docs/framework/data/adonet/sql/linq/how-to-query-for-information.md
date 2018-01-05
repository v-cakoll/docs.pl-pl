---
title: "Porady: Kwerenda dotycząca informacji"
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
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 527c2c1a84126bc2012779345fdd98ad832c9ceb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="ee834-102">Porady: Kwerenda dotycząca informacji</span><span class="sxs-lookup"><span data-stu-id="ee834-102">How to: Query for Information</span></span>
<span data-ttu-id="ee834-103">Zapytania w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używać tej samej składni jak zapytania w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee834-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="ee834-104">Jedyną różnicą jest to, że obiekty przywoływane w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania są mapowane do elementów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="ee834-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="ee834-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="ee834-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ee834-106">tłumaczy zapytania zostanie zapisany na równoważne zapytania SQL, a następnie wysyła je do serwera w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="ee834-106"> translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="ee834-107">Niektóre funkcje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytań może być konieczne szczególną uwagę w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee834-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="ee834-108">Aby uzyskać więcej informacji, zobacz [pojęcia zapytania](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="ee834-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee834-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee834-109">Example</span></span>  
 <span data-ttu-id="ee834-110">Następujące zapytanie zapyta, aby uzyskać listę klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="ee834-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="ee834-111">W tym przykładzie `Customers` jest tabela w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="ee834-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ee834-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee834-112">See Also</span></span>  
 [<span data-ttu-id="ee834-113">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="ee834-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="ee834-114">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="ee834-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="ee834-115">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="ee834-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
