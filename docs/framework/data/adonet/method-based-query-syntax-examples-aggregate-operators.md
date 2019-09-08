---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory agregujące (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: 348070663e414f2768b6b57d880c41d4da6c7bb2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794931"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="72047-102">Przykłady składni zapytania oparte na metodzie: Operatory agregujące (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="72047-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="72047-103">W przykładach w tym temacie <xref:System.Linq.Enumerable.Aggregate%2A>pokazano <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Count%2A>, jak używać operatorów, <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.LongCount%2A>,,,, i <xref:System.Linq.Enumerable.Sum%2A> do wykonywania zapytań <xref:System.Data.DataSet> i agregowania danych przy użyciu zapytania metody obowiązuje.</span><span class="sxs-lookup"><span data-stu-id="72047-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="72047-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="72047-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="72047-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="72047-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="72047-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="72047-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="72047-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="72047-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="72047-108">Agregowanie</span><span class="sxs-lookup"><span data-stu-id="72047-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="72047-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-109">Example</span></span>  
 <span data-ttu-id="72047-110">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Aggregate%2A> aby pobrać 5 pierwszych kontaktów `Contact` z tabeli i utworzyć rozdzielaną przecinkami listę nazwisk.</span><span class="sxs-lookup"><span data-stu-id="72047-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="72047-111">Average</span><span class="sxs-lookup"><span data-stu-id="72047-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="72047-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-112">Example</span></span>  
 <span data-ttu-id="72047-113">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Average%2A> aby znaleźć średnią cenę cennika produktów.</span><span class="sxs-lookup"><span data-stu-id="72047-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-114">Example</span></span>  
 <span data-ttu-id="72047-115">W tym przykładzie zastosowano <xref:System.Linq.Enumerable.Average%2A> metodę w celu wyszukania średniej ceny za produkty poszczególnych stylów.</span><span class="sxs-lookup"><span data-stu-id="72047-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-116">Example</span></span>  
 <span data-ttu-id="72047-117">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Average%2A> aby znaleźć średnią należną kwotę.</span><span class="sxs-lookup"><span data-stu-id="72047-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-118">Example</span></span>  
 <span data-ttu-id="72047-119">Ten przykład używa metody <xref:System.Linq.Enumerable.Average%2A> , aby uzyskać średnią łączną liczbę należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="72047-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-120">Example</span></span>  
 <span data-ttu-id="72047-121">Ten przykład używa metody <xref:System.Linq.Enumerable.Average%2A> , aby uzyskać zamówienia z średnią `TotalDue` dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="72047-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="72047-122">Count</span><span class="sxs-lookup"><span data-stu-id="72047-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="72047-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-123">Example</span></span>  
 <span data-ttu-id="72047-124">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Count%2A> aby zwrócić liczbę produktów w tabeli.`Product`</span><span class="sxs-lookup"><span data-stu-id="72047-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="72047-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-125">Example</span></span>  
 <span data-ttu-id="72047-126">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Count%2A> aby zwrócić listę identyfikatorów kontaktu oraz liczbę zamówień, które każdy z nich ma.</span><span class="sxs-lookup"><span data-stu-id="72047-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="72047-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-127">Example</span></span>  
 <span data-ttu-id="72047-128">Ten przykład grupuje produkty według koloru i używa <xref:System.Linq.Enumerable.Count%2A> metody do zwrócenia liczby produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="72047-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="72047-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="72047-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="72047-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-130">Example</span></span>  
 <span data-ttu-id="72047-131">Ten przykład pobiera liczbę kontaktów jako długą liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="72047-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="72047-132">Maks.</span><span class="sxs-lookup"><span data-stu-id="72047-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="72047-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-133">Example</span></span>  
 <span data-ttu-id="72047-134">W tym przykładzie zastosowano <xref:System.Linq.Enumerable.Max%2A> metodę w celu uzyskania największej wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="72047-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-135">Example</span></span>  
 <span data-ttu-id="72047-136">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Max%2A> Aby uzyskać największą łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="72047-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-137">Example</span></span>  
 <span data-ttu-id="72047-138">Ten przykład używa metody <xref:System.Linq.Enumerable.Max%2A> , aby uzyskać zamówienia o największych `TotalDue` dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="72047-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="72047-139">Min.</span><span class="sxs-lookup"><span data-stu-id="72047-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="72047-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-140">Example</span></span>  
 <span data-ttu-id="72047-141">W tym przykładzie zastosowano <xref:System.Linq.Enumerable.Min%2A> metodę w celu uzyskania najmniejszej liczby zaległych.</span><span class="sxs-lookup"><span data-stu-id="72047-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-142">Example</span></span>  
 <span data-ttu-id="72047-143">Ten przykład używa <xref:System.Linq.Enumerable.Min%2A> metody, aby uzyskać najmniejszą łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="72047-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-144">Example</span></span>  
 <span data-ttu-id="72047-145">Ten przykład używa metody <xref:System.Linq.Enumerable.Min%2A> , aby uzyskać zamówienia z najmniejszą łączną należną dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="72047-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="72047-146">Suma</span><span class="sxs-lookup"><span data-stu-id="72047-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="72047-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-147">Example</span></span>  
 <span data-ttu-id="72047-148">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Sum%2A> Aby uzyskać łączną liczbę wielkości zamówienia w tabeli.`SalesOrderDetail`</span><span class="sxs-lookup"><span data-stu-id="72047-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="72047-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="72047-149">Example</span></span>  
 <span data-ttu-id="72047-150">Ten przykład używa metody <xref:System.Linq.Enumerable.Sum%2A> , aby uzyskać łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="72047-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="72047-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72047-151">See also</span></span>

- [<span data-ttu-id="72047-152">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="72047-152">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="72047-153">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="72047-153">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="72047-154">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="72047-154">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="72047-155">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72047-155">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
