---
title: Wyrażenia porównania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: d0926bb1a0e35caa058f268f0a0c414e805a8674
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251171"
---
# <a name="comparison-expressions"></a><span data-ttu-id="dc945-102">Wyrażenia porównania</span><span class="sxs-lookup"><span data-stu-id="dc945-102">Comparison Expressions</span></span>
<span data-ttu-id="dc945-103">Wyrażenie porównania sprawdza, czy wartość stała, wartość właściwości lub wynik metody są równe, nie równe, większe niż lub mniejsze niż inna wartość.</span><span class="sxs-lookup"><span data-stu-id="dc945-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="dc945-104">Jeśli określone porównanie nie jest prawidłowe dla LINQ to Entities, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="dc945-104">If a particular comparison is not valid for LINQ to Entities, an exception will be thrown.</span></span> <span data-ttu-id="dc945-105">Wszystkie porównania, zarówno niejawne, jak i jawne, wymagają, aby wszystkie składniki były porównywalne w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="dc945-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="dc945-106">Wyrażenia porównania są często używane w `Where` klauzulach ograniczających wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="dc945-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="dc945-107">Poniższy przykład w składni wyrażenia zapytania pokazuje zapytanie zwracające wyniki, w przypadku których numer zamówienia sprzedaży jest równy "SO43663":</span><span class="sxs-lookup"><span data-stu-id="dc945-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="dc945-108">Poniższy przykład w składni zapytania opartej na metodzie pokazuje zapytanie, które zwraca wyniki, gdzie numer zamówienia sprzedaży jest równy "SO43663":</span><span class="sxs-lookup"><span data-stu-id="dc945-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="dc945-109">Poniższy przykład w składni wyrażenia zapytania pokazuje zapytanie, które zwraca informacje o zamówieniach sprzedaży, gdzie Data wysyłki jest równa 8 lipca 2001:</span><span class="sxs-lookup"><span data-stu-id="dc945-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="dc945-110">Poniższy przykład w składni zapytania opartej na metodzie przedstawia zapytanie, które zwraca informacje o zamówieniach sprzedaży, gdzie Data wysyłki jest równa 8 lipca 2001:</span><span class="sxs-lookup"><span data-stu-id="dc945-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="dc945-111">Wyrażenia, które zwracają stałą, są konwertowane na serwerze i nie ma konieczności przeprowadzania oceny lokalnej.</span><span class="sxs-lookup"><span data-stu-id="dc945-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="dc945-112">Poniższy przykład używa wyrażenia w `Where` klauzuli, która zwraca stałą.</span><span class="sxs-lookup"><span data-stu-id="dc945-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="dc945-113">LINQ to Entities nie obsługuje używania klasy użytkownika jako stałej.</span><span class="sxs-lookup"><span data-stu-id="dc945-113">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="dc945-114">Jednak odwołanie do właściwości w klasie użytkownika jest uznawane za stałe i zostanie przekonwertowane na wyrażenie stałe drzewa poleceń i wykonane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="dc945-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="dc945-115">Metody zwracające wyrażenie stałe nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dc945-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="dc945-116">Poniższy przykład zawiera metodę w `Where` klauzuli, która zwraca stałą.</span><span class="sxs-lookup"><span data-stu-id="dc945-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="dc945-117">Ten przykład zgłosi wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dc945-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="dc945-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc945-118">See also</span></span>

- [<span data-ttu-id="dc945-119">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="dc945-119">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
