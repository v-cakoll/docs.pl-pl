---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory agregacji (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: 8d8f3cebb599eb543d569e36b294e6433a45f432
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401477"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="2c9b6-102">Przykłady składni zapytania oparte na metodzie: Operatory agregacji (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="2c9b6-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="2c9b6-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> operatorów kwerendy <xref:System.Data.DataSet> i agregowanie danych za pomocą metody zapytania Składnia.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="2c9b6-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="2c9b6-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="2c9b6-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2c9b6-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="2c9b6-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="2c9b6-107">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika LINQ to DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2c9b6-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="2c9b6-108">Agregowanie</span><span class="sxs-lookup"><span data-stu-id="2c9b6-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c9b6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-109">Example</span></span>  
 <span data-ttu-id="2c9b6-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.Aggregate%2A> metodę, aby uzyskać 5 pierwszych kontakty z `Contact` tabeli i listę rozdzielonych przecinkami nazw ostatniej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="2c9b6-111">Średnia</span><span class="sxs-lookup"><span data-stu-id="2c9b6-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c9b6-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-112">Example</span></span>  
 <span data-ttu-id="2c9b6-113">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średnia cena listy produktów.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-114">Example</span></span>  
 <span data-ttu-id="2c9b6-115">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średnia cena listy produktów każdego stylu.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-116">Example</span></span>  
 <span data-ttu-id="2c9b6-117">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia Średnia łączna liczba powodu.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-118">Example</span></span>  
 <span data-ttu-id="2c9b6-119">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> identyfikatora metodę, aby uzyskać Średnia łączna liczba powodu dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-120">Example</span></span>  
 <span data-ttu-id="2c9b6-121">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metodę, aby uzyskać zamówień ze średnią `TotalDue` dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="2c9b6-122">Liczba</span><span class="sxs-lookup"><span data-stu-id="2c9b6-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c9b6-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-123">Example</span></span>  
 <span data-ttu-id="2c9b6-124">W tym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> metodę, aby zwrócić liczbę produktów w `Product` tabeli.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-125">Example</span></span>  
 <span data-ttu-id="2c9b6-126">W tym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> ma metodę, aby zwrócić listę skontaktuj się z identyfikatorów i jak wiele zamówień, każdy.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-127">Example</span></span>  
 <span data-ttu-id="2c9b6-128">W tym przykładzie grupy produktów, kolor i używa <xref:System.Linq.Enumerable.Count%2A> metodę, aby zwrócić liczbę produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="2c9b6-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="2c9b6-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c9b6-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-130">Example</span></span>  
 <span data-ttu-id="2c9b6-131">W tym przykładzie pobiera liczbę kontaktu jako liczba całkowita typu long.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="2c9b6-132">Maksymalna</span><span class="sxs-lookup"><span data-stu-id="2c9b6-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c9b6-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-133">Example</span></span>  
 <span data-ttu-id="2c9b6-134">W tym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać największy termin całkowitej.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-135">Example</span></span>  
 <span data-ttu-id="2c9b6-136">W tym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać największy termin całkowita dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-137">Example</span></span>  
 <span data-ttu-id="2c9b6-138">W tym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać zamówień o największej `TotalDue` dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="2c9b6-139">min</span><span class="sxs-lookup"><span data-stu-id="2c9b6-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c9b6-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-140">Example</span></span>  
 <span data-ttu-id="2c9b6-141">W tym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać najmniejszy całkowita termin.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-142">Example</span></span>  
 <span data-ttu-id="2c9b6-143">W tym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać najmniejszy termin całkowitą dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-144">Example</span></span>  
 <span data-ttu-id="2c9b6-145">W tym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać zamówienia z sumą najmniejszy termin dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="2c9b6-146">Suma</span><span class="sxs-lookup"><span data-stu-id="2c9b6-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="2c9b6-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-147">Example</span></span>  
 <span data-ttu-id="2c9b6-148">W tym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby uzyskać sumę ilości zamówienia w `SalesOrderDetail` tabeli.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="2c9b6-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c9b6-149">Example</span></span>  
 <span data-ttu-id="2c9b6-150">W tym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby uzyskać całkowity termin dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="2c9b6-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="2c9b6-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c9b6-151">See Also</span></span>  
 [<span data-ttu-id="2c9b6-152">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2c9b6-152">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="2c9b6-153">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="2c9b6-153">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="2c9b6-154">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="2c9b6-154">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
