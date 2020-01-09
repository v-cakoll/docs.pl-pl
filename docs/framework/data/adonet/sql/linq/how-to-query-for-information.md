---
title: 'Instrukcje: zapytanie o informacje'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 3380b486da33a5dc083ed51f6705e666978df197
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634654"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="843a2-102">Instrukcje: zapytanie o informacje</span><span class="sxs-lookup"><span data-stu-id="843a2-102">How to: Query for Information</span></span>
<span data-ttu-id="843a2-103">Zapytania w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używają tej samej składni co zapytania w LINQ.</span><span class="sxs-lookup"><span data-stu-id="843a2-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="843a2-104">Jedyną różnicą jest to, że obiekty, do których odwołują się zapytania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] są mapowane na elementy w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="843a2-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="843a2-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="843a2-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="843a2-106">tłumaczy zapytania zapisane w równoważne zapytania SQL i wysyła je do serwera w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="843a2-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="843a2-107">Niektóre funkcje zapytań LINQ mogą wymagać specjalnej uwagi w aplikacjach [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="843a2-107">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="843a2-108">Aby uzyskać więcej informacji, zobacz [pojęcia dotyczące zapytań](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="843a2-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="843a2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="843a2-109">Example</span></span>  
 <span data-ttu-id="843a2-110">Poniższe zapytanie pyta o listę klientów z usługi Londyn.</span><span class="sxs-lookup"><span data-stu-id="843a2-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="843a2-111">W tym przykładzie `Customers` jest tabelą w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="843a2-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="843a2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="843a2-112">See also</span></span>

- [<span data-ttu-id="843a2-113">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="843a2-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="843a2-114">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="843a2-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="843a2-115">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="843a2-115">Querying the Database</span></span>](querying-the-database.md)
