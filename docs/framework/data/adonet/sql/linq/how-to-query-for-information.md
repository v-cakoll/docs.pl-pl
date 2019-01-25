---
title: 'Instrukcje: Zapytanie dotyczące informacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 9476144d84454aedc331214a55c77547697c378f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608417"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="81fe7-102">Instrukcje: Zapytanie dotyczące informacji</span><span class="sxs-lookup"><span data-stu-id="81fe7-102">How to: Query for Information</span></span>
<span data-ttu-id="81fe7-103">Zapytania w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] należy użyć tej samej składni jako zapytania w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81fe7-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="81fe7-104">Jedyną różnicą jest to, że obiekty do którego odwołuje się [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania są mapowane do elementów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="81fe7-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="81fe7-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="81fe7-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="81fe7-106">przekłada zapytania, który zapisane na równoważne zapytania SQL, a następnie wysyła je do serwera w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="81fe7-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="81fe7-107">Niektóre funkcje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania mogą potrzebować szczególną uwagę w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="81fe7-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="81fe7-108">Aby uzyskać więcej informacji, zobacz [kwestie dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="81fe7-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81fe7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="81fe7-109">Example</span></span>  
 <span data-ttu-id="81fe7-110">Następujące zapytanie pyta, czy lista klienci z Londynu.</span><span class="sxs-lookup"><span data-stu-id="81fe7-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="81fe7-111">W tym przykładzie `Customers` jest tabela w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="81fe7-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="81fe7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81fe7-112">See also</span></span>
- [<span data-ttu-id="81fe7-113">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="81fe7-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="81fe7-114">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="81fe7-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="81fe7-115">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="81fe7-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
