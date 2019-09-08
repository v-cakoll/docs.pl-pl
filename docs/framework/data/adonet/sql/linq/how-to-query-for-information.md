---
title: 'Instrukcje: Zapytanie dotyczące informacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ed32bbe7d27357cbed7d77dd235b698a65c0e29e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793536"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="1eb91-102">Instrukcje: Zapytanie dotyczące informacji</span><span class="sxs-lookup"><span data-stu-id="1eb91-102">How to: Query for Information</span></span>
<span data-ttu-id="1eb91-103">Zapytania w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] programie używają tej samej składni co zapytania [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]w.</span><span class="sxs-lookup"><span data-stu-id="1eb91-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="1eb91-104">Jedyną różnicą jest to, że obiekty, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do których odwołują się zapytania, są mapowane na elementy w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="1eb91-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="1eb91-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="1eb91-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1eb91-106">tłumaczy zapytania zapisane w równoważne zapytania SQL i wysyła je do serwera w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="1eb91-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="1eb91-107">Niektóre funkcje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytań mogą wymagać specjalnej uwagi w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="1eb91-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="1eb91-108">Aby uzyskać więcej informacji, zobacz [pojęcia dotyczące zapytań](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="1eb91-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eb91-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1eb91-109">Example</span></span>  
 <span data-ttu-id="1eb91-110">Poniższe zapytanie pyta o listę klientów z usługi Londyn.</span><span class="sxs-lookup"><span data-stu-id="1eb91-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="1eb91-111">W tym przykładzie `Customers` jest to tabela w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="1eb91-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1eb91-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1eb91-112">See also</span></span>

- [<span data-ttu-id="1eb91-113">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="1eb91-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="1eb91-114">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="1eb91-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="1eb91-115">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="1eb91-115">Querying the Database</span></span>](querying-the-database.md)
