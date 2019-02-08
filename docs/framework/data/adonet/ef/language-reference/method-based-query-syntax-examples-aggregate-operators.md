---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory agregacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 69bc2d1ae64ee4aaa016a70f6b46ac1f26dcf563
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825566"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="d3375-102">Przykłady składni zapytania oparte na metodzie: Operatory agregacji</span><span class="sxs-lookup"><span data-stu-id="d3375-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="d3375-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> metod do wykonywania zapytań [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) za pomocą składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="d3375-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="d3375-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d3375-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d3375-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d3375-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="d3375-106">Średnia</span><span class="sxs-lookup"><span data-stu-id="d3375-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3375-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-107">Example</span></span>  
 <span data-ttu-id="d3375-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średnia cena listy produktów.</span><span class="sxs-lookup"><span data-stu-id="d3375-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-109">Example</span></span>  
 <span data-ttu-id="d3375-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średnia cena listy produktów każdego stylu.</span><span class="sxs-lookup"><span data-stu-id="d3375-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-111">Example</span></span>  
 <span data-ttu-id="d3375-112">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia Średnia łączna liczba powodu.</span><span class="sxs-lookup"><span data-stu-id="d3375-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-113">Example</span></span>  
 <span data-ttu-id="d3375-114">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> identyfikatora metodę, aby uzyskać Średnia łączna liczba powodu dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="d3375-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-115">Example</span></span>  
 <span data-ttu-id="d3375-116">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metodę, aby uzyskać zamówień ze średnią całkowita powodu dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="d3375-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="d3375-117">Licznik</span><span class="sxs-lookup"><span data-stu-id="d3375-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3375-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-118">Example</span></span>  
 <span data-ttu-id="d3375-119">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> metodę, aby zwrócić liczbę produktów w tabeli Product.</span><span class="sxs-lookup"><span data-stu-id="d3375-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="d3375-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-120">Example</span></span>  
 <span data-ttu-id="d3375-121">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> ma metodę, aby zwrócić listę skontaktuj się z identyfikatorów i jak wiele zamówień, każdy.</span><span class="sxs-lookup"><span data-stu-id="d3375-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="d3375-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-122">Example</span></span>  
 <span data-ttu-id="d3375-123">W poniższym przykładzie grupuje produkty według kolorów i używa <xref:System.Linq.Enumerable.Count%2A> metodę, aby zwrócić liczbę produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="d3375-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="d3375-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="d3375-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3375-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-125">Example</span></span>  
 <span data-ttu-id="d3375-126">Poniższy przykład pobiera liczba kontaktu jako liczba całkowita typu long.</span><span class="sxs-lookup"><span data-stu-id="d3375-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="d3375-127">Maks.</span><span class="sxs-lookup"><span data-stu-id="d3375-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3375-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-128">Example</span></span>  
 <span data-ttu-id="d3375-129">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać największy termin całkowitej.</span><span class="sxs-lookup"><span data-stu-id="d3375-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-130">Example</span></span>  
 <span data-ttu-id="d3375-131">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać największy termin całkowita dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="d3375-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-132">Example</span></span>  
 <span data-ttu-id="d3375-133">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać zamówień za pomocą programu Największa całkowita termin dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="d3375-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="d3375-134">Min.</span><span class="sxs-lookup"><span data-stu-id="d3375-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3375-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-135">Example</span></span>  
 <span data-ttu-id="d3375-136">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać najmniejszy całkowita termin.</span><span class="sxs-lookup"><span data-stu-id="d3375-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-137">Example</span></span>  
 <span data-ttu-id="d3375-138">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać najmniejszy termin całkowitą dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="d3375-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-139">Example</span></span>  
 <span data-ttu-id="d3375-140">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać zamówienia z sumą najmniejszy termin dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="d3375-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="d3375-141">Suma</span><span class="sxs-lookup"><span data-stu-id="d3375-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3375-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-142">Example</span></span>  
 <span data-ttu-id="d3375-143">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby uzyskać sumę ilości zamówienia w tabeli Szczegóły zamówienia sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="d3375-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3375-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3375-144">Example</span></span>  
 <span data-ttu-id="d3375-145">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby uzyskać całkowity termin dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="d3375-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="d3375-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3375-146">See also</span></span>
- [<span data-ttu-id="d3375-147">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d3375-147">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
