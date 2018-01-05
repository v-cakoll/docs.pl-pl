---
title: "Porównywanie wyrażeń"
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
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: def78e45fa59fafbc6b8e5ffec7273f755e49d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="comparison-expressions"></a><span data-ttu-id="c56f5-102">Porównywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="c56f5-102">Comparison Expressions</span></span>
<span data-ttu-id="c56f5-103">Wyrażenie porównania sprawdza, czy stałej wartości, wartość właściwości lub metody powodują takie same, nie jest taki sam, większy niż lub mniejsza niż wartość inna.</span><span class="sxs-lookup"><span data-stu-id="c56f5-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="c56f5-104">Jeśli konkretnej porównania jest nieprawidłowa dla [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c56f5-104">If a particular comparison is not valid for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], an exception will be thrown.</span></span> <span data-ttu-id="c56f5-105">Wszystkie porównań, zarówno niejawnych i jawnych, wymagają, czy wszystkie składniki są porównywalne w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="c56f5-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="c56f5-106">Porównanie wyrażenia są często używane w `Where` klauzule ograniczające wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="c56f5-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="c56f5-107">W poniższym przykładzie w składni wyrażeń zapytania przedstawiono zapytanie, które zwraca wyniki, gdzie numer zamówienia jest równa "SO43663":</span><span class="sxs-lookup"><span data-stu-id="c56f5-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="c56f5-108">W poniższym przykładzie w składni zapytania oparte na metodzie przedstawiono zapytanie, które zwraca wyniki, gdzie numer zamówienia jest równa "SO43663":</span><span class="sxs-lookup"><span data-stu-id="c56f5-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="c56f5-109">W poniższym przykładzie w składni wyrażeń zapytania przedstawiono zapytanie zwracające informacji o zamówieniu sprzedaży, gdzie daty jest równa 8 lipca 2001:</span><span class="sxs-lookup"><span data-stu-id="c56f5-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="c56f5-110">W poniższym przykładzie w składni zapytania oparte na metodzie przedstawiono zapytanie zwracające informacji o zamówieniu sprzedaży, gdzie daty jest równa 8 lipca 2001:</span><span class="sxs-lookup"><span data-stu-id="c56f5-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="c56f5-111">Wyrażeń, które zwracają stałą są konwertowane na serwerze, a próba czy oceny lokalnej jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="c56f5-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="c56f5-112">W poniższym przykładzie użyto wyrażenia w `Where` klauzuli, która zapewni stałą.</span><span class="sxs-lookup"><span data-stu-id="c56f5-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="c56f5-113">nie obsługuje używania klasy użytkownika jako stała.</span><span class="sxs-lookup"><span data-stu-id="c56f5-113"> does not support using a user class as a constant.</span></span> <span data-ttu-id="c56f5-114">Jednak odwołania do właściwości klasy użytkownika jest uznawany za stałą i będzie można przekonwertować na stałe wyrażenie drzewa polecenia ani wykonywać w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="c56f5-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="c56f5-115">Metody zwracające wyrażenie stałe są nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c56f5-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="c56f5-116">Poniżej przedstawiono przykład zawierający metody w `Where` klauzuli, która zwraca wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="c56f5-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="c56f5-117">W tym przykładzie spowoduje zgłoszenie wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c56f5-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="c56f5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c56f5-118">See Also</span></span>  
 [<span data-ttu-id="c56f5-119">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c56f5-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
