---
title: "Przykłady składni zapytania oparte na metodzie: filtrowania"
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
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bd11257de9696135c35db02cd411d31805bbe7ba
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-filtering"></a><span data-ttu-id="c80b9-102">Przykłady składni zapytania oparte na metodzie: filtrowania</span><span class="sxs-lookup"><span data-stu-id="c80b9-102">Method-Based Query Syntax Examples: Filtering</span></span>
<span data-ttu-id="c80b9-103">Przykłady w tym temacie przedstawiają sposób użycia `Where` i `Where…Contains` metod do badania [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="c80b9-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="c80b9-104">Uwaga: Jeżeli...`Contains`</span><span class="sxs-lookup"><span data-stu-id="c80b9-104">Note, Where…`Contains`</span></span> <span data-ttu-id="c80b9-105">Nie można użyć jako część [skompilowane zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="c80b9-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="c80b9-106">Model sprzedaży AdventureWorks używany w tym przykładzie składa się z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c80b9-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c80b9-107">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="c80b9-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="c80b9-108">Gdzie</span><span class="sxs-lookup"><span data-stu-id="c80b9-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="c80b9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c80b9-109">Example</span></span>  
 <span data-ttu-id="c80b9-110">Poniższy przykład zwraca wszystkie zamówienia online.</span><span class="sxs-lookup"><span data-stu-id="c80b9-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a><span data-ttu-id="c80b9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c80b9-111">Example</span></span>  
 <span data-ttu-id="c80b9-112">Poniższy przykład zwraca zamówienia, w których ilość zamówienia jest większa niż 2 do mniej niż 6.</span><span class="sxs-lookup"><span data-stu-id="c80b9-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a><span data-ttu-id="c80b9-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c80b9-113">Example</span></span>  
 <span data-ttu-id="c80b9-114">Poniższy przykład zwraca wszystkie produkty kolorowe czerwony.</span><span class="sxs-lookup"><span data-stu-id="c80b9-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a><span data-ttu-id="c80b9-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c80b9-115">Example</span></span>  
 <span data-ttu-id="c80b9-116">W poniższym przykładzie użyto `Where` metody do znalezienia zlecenia, które zostały dokonane po 1 grudnia 2003, a następnie używa `order.SalesOrderDetail` właściwość nawigacji, aby uzyskać szczegółowe informacje dla każdego zlecenia.</span><span class="sxs-lookup"><span data-stu-id="c80b9-116">The following example uses the `Where` method to find orders that were made after December 1, 2003 and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a><span data-ttu-id="c80b9-117">Gdzie... Zawiera</span><span class="sxs-lookup"><span data-stu-id="c80b9-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="c80b9-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c80b9-118">Example</span></span>  
 <span data-ttu-id="c80b9-119">W poniższym przykładzie użyto tablicy jako część `Where…Contains` klauzuli, aby znaleźć wszystkie produkty, które mają `ProductModelID` , które odpowiadają wartości w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c80b9-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
>  <span data-ttu-id="c80b9-120">Predykat w ramach `Where…Contains` klauzuli, można użyć <xref:System.Array>, <xref:System.Collections.Generic.List%601>, lub kolekcji dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c80b9-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="c80b9-121">Można również deklarować i zainicjuj kolekcję w zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="c80b9-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="c80b9-122">Zapoznaj się z przykładem dalej, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="c80b9-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c80b9-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="c80b9-123">Example</span></span>  
 <span data-ttu-id="c80b9-124">W poniższym przykładzie deklaruje i inicjuje tablic w `Where…Contains` klauzuli, aby znaleźć wszystkie produkty, które mają `ProductModelID` lub `Size` , które odpowiadają wartości w tablicach.</span><span class="sxs-lookup"><span data-stu-id="c80b9-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or a `Size` that matches a value in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c80b9-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c80b9-125">See Also</span></span>  
 [<span data-ttu-id="c80b9-126">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c80b9-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
