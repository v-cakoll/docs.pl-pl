---
title: 'Przykłady składni wyrażeń zapytania: Operatory agregujące (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: 44e38a53823cb52040a612d4762e33283f90e1d1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794526"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="27846-102">Przykłady składni wyrażeń zapytania: Operatory agregujące (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="27846-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="27846-103">W <xref:System.Linq.Enumerable.Average%2A>przykładach w tym temacie przedstawiono sposób użycia metod, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> do wykonywania zapytań <xref:System.Data.DataSet> dotyczących danych i agregowania ich przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="27846-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="27846-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="27846-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="27846-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="27846-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="27846-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="27846-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="27846-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="27846-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="27846-108">Average</span><span class="sxs-lookup"><span data-stu-id="27846-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="27846-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-109">Example</span></span>  
 <span data-ttu-id="27846-110">W tym przykładzie zastosowano <xref:System.Linq.Enumerable.Average%2A> metodę w celu wyszukania średniej ceny za produkty poszczególnych stylów.</span><span class="sxs-lookup"><span data-stu-id="27846-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="27846-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-111">Example</span></span>  
 <span data-ttu-id="27846-112">Ten przykład używa <xref:System.Linq.Enumerable.Average%2A> , aby uzyskać średnią łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="27846-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="27846-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-113">Example</span></span>  
 <span data-ttu-id="27846-114">Ten przykład używa <xref:System.Linq.Enumerable.Average%2A> , aby uzyskać zamówienia z średnią `TotalDue` dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="27846-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="27846-115">Count</span><span class="sxs-lookup"><span data-stu-id="27846-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="27846-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-116">Example</span></span>  
 <span data-ttu-id="27846-117">Ten przykład używa <xref:System.Linq.Enumerable.Count%2A> do zwracania listy identyfikatorów kontaktu oraz liczby zamówień, z których każdy ma.</span><span class="sxs-lookup"><span data-stu-id="27846-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="27846-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-118">Example</span></span>  
 <span data-ttu-id="27846-119">Ten przykład grupuje produkty według koloru i <xref:System.Linq.Enumerable.Count%2A> używa do zwracania liczby produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="27846-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="27846-120">Maks.</span><span class="sxs-lookup"><span data-stu-id="27846-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="27846-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-121">Example</span></span>  
 <span data-ttu-id="27846-122">W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Max%2A> Aby uzyskać największą łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="27846-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="27846-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-123">Example</span></span>  
 <span data-ttu-id="27846-124">Ten przykład używa metody <xref:System.Linq.Enumerable.Max%2A> , aby uzyskać zamówienia o największych `TotalDue` dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="27846-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="27846-125">Min.</span><span class="sxs-lookup"><span data-stu-id="27846-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="27846-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-126">Example</span></span>  
 <span data-ttu-id="27846-127">Ten przykład używa <xref:System.Linq.Enumerable.Min%2A> metody, aby uzyskać najmniejszą łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="27846-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="27846-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-128">Example</span></span>  
 <span data-ttu-id="27846-129">Ten przykład używa metody <xref:System.Linq.Enumerable.Min%2A> , aby uzyskać zamówienia z najmniejszą łączną należną dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="27846-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="27846-130">Suma</span><span class="sxs-lookup"><span data-stu-id="27846-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="27846-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="27846-131">Example</span></span>  
 <span data-ttu-id="27846-132">Ten przykład używa metody <xref:System.Linq.Enumerable.Sum%2A> , aby uzyskać łączną ilość należną dla każdego identyfikatora osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="27846-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="27846-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27846-133">See also</span></span>

- [<span data-ttu-id="27846-134">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="27846-134">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="27846-135">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="27846-135">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="27846-136">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="27846-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="27846-137">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27846-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
