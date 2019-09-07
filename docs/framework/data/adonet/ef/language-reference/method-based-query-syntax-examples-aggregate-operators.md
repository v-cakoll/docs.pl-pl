---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory agregacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 17d3a5e221fc5f917e9e266b3af4fb844c6fd85e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397502"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="290bb-102">Przykłady składni zapytania oparte na metodzie: Operatory agregacji</span><span class="sxs-lookup"><span data-stu-id="290bb-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="290bb-103">W przykładach w tym temacie przedstawiono <xref:System.Linq.Enumerable.Aggregate%2A>sposób użycia metod, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.LongCount%2A> <xref:System.Linq.Enumerable.Min%2A>,,, i <xref:System.Linq.Enumerable.Sum%2A> do wysyłania zapytań do [modelu sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) przy użyciu Składnia zapytania oparta na metodzie.</span><span class="sxs-lookup"><span data-stu-id="290bb-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="290bb-104">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="290bb-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="290bb-105">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="290bb-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="290bb-106">Average</span><span class="sxs-lookup"><span data-stu-id="290bb-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="290bb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-107">Example</span></span>  
 <span data-ttu-id="290bb-108">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Average%2A> metodę, aby znaleźć średnią cenę cennika produktów.</span><span class="sxs-lookup"><span data-stu-id="290bb-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-109">Example</span></span>  
 <span data-ttu-id="290bb-110">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Average%2A> metodę w celu wyszukania średniej ceny za produkty poszczególnych stylów.</span><span class="sxs-lookup"><span data-stu-id="290bb-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-111">Example</span></span>  
 <span data-ttu-id="290bb-112">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Average%2A> metodę, aby znaleźć średnią należną kwotę.</span><span class="sxs-lookup"><span data-stu-id="290bb-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-113">Example</span></span>  
 <span data-ttu-id="290bb-114">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Average%2A> metodę, aby uzyskać średnią łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="290bb-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-115">Example</span></span>  
 <span data-ttu-id="290bb-116">Poniższy przykład używa metody, <xref:System.Linq.Enumerable.Average%2A> Aby uzyskać zamówienia z średnią sumą należną dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="290bb-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="290bb-117">Count</span><span class="sxs-lookup"><span data-stu-id="290bb-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="290bb-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-118">Example</span></span>  
 <span data-ttu-id="290bb-119">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Count%2A> metodę, aby zwrócić liczbę produktów w tabeli Product.</span><span class="sxs-lookup"><span data-stu-id="290bb-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="290bb-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-120">Example</span></span>  
 <span data-ttu-id="290bb-121">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Count%2A> metodę, aby zwrócić listę identyfikatorów kontaktu oraz liczbę zamówień, które każdy z nich ma.</span><span class="sxs-lookup"><span data-stu-id="290bb-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="290bb-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-122">Example</span></span>  
 <span data-ttu-id="290bb-123">Poniższy przykład grupuje produkty według koloru i używa <xref:System.Linq.Enumerable.Count%2A> metody do zwrócenia liczby produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="290bb-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="290bb-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="290bb-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="290bb-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-125">Example</span></span>  
 <span data-ttu-id="290bb-126">Poniższy przykład pobiera liczbę kontaktów jako długą liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="290bb-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="290bb-127">Maks.</span><span class="sxs-lookup"><span data-stu-id="290bb-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="290bb-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-128">Example</span></span>  
 <span data-ttu-id="290bb-129">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Max%2A> metodę w celu uzyskania największej wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="290bb-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-130">Example</span></span>  
 <span data-ttu-id="290bb-131">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Max%2A> metodę w celu uzyskania największego łącznego terminu dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="290bb-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-132">Example</span></span>  
 <span data-ttu-id="290bb-133">Poniższy przykład używa metody, <xref:System.Linq.Enumerable.Max%2A> Aby uzyskać zamówienia z największą sumą należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="290bb-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="290bb-134">Min.</span><span class="sxs-lookup"><span data-stu-id="290bb-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="290bb-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-135">Example</span></span>  
 <span data-ttu-id="290bb-136">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Min%2A> metodę w celu uzyskania najmniejszej wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="290bb-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-137">Example</span></span>  
 <span data-ttu-id="290bb-138">Poniższy przykład używa <xref:System.Linq.Enumerable.Min%2A> metody, aby uzyskać najmniejszą łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="290bb-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-139">Example</span></span>  
 <span data-ttu-id="290bb-140">Poniższy przykład używa metody, <xref:System.Linq.Enumerable.Min%2A> Aby uzyskać zamówienia o najmniejszej łącznej wartości należnej dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="290bb-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="290bb-141">Suma</span><span class="sxs-lookup"><span data-stu-id="290bb-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="290bb-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-142">Example</span></span>  
 <span data-ttu-id="290bb-143">Poniższy przykład używa metody, <xref:System.Linq.Enumerable.Sum%2A> Aby uzyskać łączną liczbę ilości zamówienia w tabeli SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="290bb-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="290bb-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="290bb-144">Example</span></span>  
 <span data-ttu-id="290bb-145">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Sum%2A> metodę, aby uzyskać łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="290bb-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="290bb-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="290bb-146">See also</span></span>

- [<span data-ttu-id="290bb-147">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="290bb-147">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
