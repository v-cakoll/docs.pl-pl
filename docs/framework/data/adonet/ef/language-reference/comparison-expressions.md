---
title: Wyrażenia porównania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: 4b0d7e668526fd71943513db2fc3c076c8bd3bad
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539931"
---
# <a name="comparison-expressions"></a><span data-ttu-id="c3329-102">Wyrażenia porównania</span><span class="sxs-lookup"><span data-stu-id="c3329-102">Comparison Expressions</span></span>
<span data-ttu-id="c3329-103">Wyrażenie porównania sprawdza, czy stałą wartość, wartość właściwości lub metody powodują jest równe, nie równe, większe niż lub mniejsze niż inną wartość.</span><span class="sxs-lookup"><span data-stu-id="c3329-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="c3329-104">Jeśli w danym porównaniu jest nieprawidłowy dla programu LINQ to Entities, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c3329-104">If a particular comparison is not valid for LINQ to Entities, an exception will be thrown.</span></span> <span data-ttu-id="c3329-105">Wszystkie porównania niejawne i jawne, wymagają, że wszystkie składniki są porównywalne w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="c3329-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="c3329-106">Porównywanie wyrażeń są często stosowane w `Where` klauzule ograniczania wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="c3329-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="c3329-107">W składni wyrażenia zapytania poniższy kod przedstawia zapytanie, które zwraca wyniki, gdzie numer zamówienia sprzedaży jest równa "SO43663":</span><span class="sxs-lookup"><span data-stu-id="c3329-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="c3329-108">W składni zapytania oparte na metodzie poniższy kod przedstawia zapytanie, które zwraca wyniki, gdzie numer zamówienia sprzedaży jest równa "SO43663":</span><span class="sxs-lookup"><span data-stu-id="c3329-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="c3329-109">W składni wyrażenia zapytania poniższy kod przedstawia zapytanie, które zwraca informację o zamówieniu sprzedaży, w których daty jest równa 8 lipca 2001:</span><span class="sxs-lookup"><span data-stu-id="c3329-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="c3329-110">W składni zapytania oparte na metodzie poniższy kod przedstawia zapytanie, które zwraca informację o zamówieniu sprzedaży, w których daty jest równa 8 lipca 2001:</span><span class="sxs-lookup"><span data-stu-id="c3329-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="c3329-111">Wyrażeń, które stałą są konwertowane na serwerze, a próba czy ocena lokalna jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="c3329-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="c3329-112">W poniższym przykładzie użyto wyrażenia w `Where` klauzula, która zapewni stałą.</span><span class="sxs-lookup"><span data-stu-id="c3329-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="c3329-113">Składnik LINQ to Entities nie obsługuje używania klasy użytkownika jako stała.</span><span class="sxs-lookup"><span data-stu-id="c3329-113">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="c3329-114">Jednak odwołaniem do właściwości w klasie użytkownika jest uznawany za stałą, zostanie przekonwertowane na wyrażeniu stałym drzewa poleceń i wykonywane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="c3329-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="c3329-115">Metody, które zwracają wyrażenie stałe nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3329-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="c3329-116">Poniższy przykład zawiera metody w `Where` klauzula, która zwraca wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="c3329-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="c3329-117">W tym przykładzie spowoduje zgłoszenie wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c3329-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="c3329-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3329-118">See also</span></span>

- [<span data-ttu-id="c3329-119">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c3329-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
