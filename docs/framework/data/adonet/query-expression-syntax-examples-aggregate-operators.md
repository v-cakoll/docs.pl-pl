---
title: "Przykłady składni wyrażeń zapytania: Operatory agregacji (LINQ do DataSet)"
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
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 93cffc4d3ae6cadb7fdeeac4e01f1a3a50812005
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="11802-102">Przykłady składni wyrażeń zapytania: Operatory agregacji (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="11802-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="11802-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> metod do badania <xref:System.Data.DataSet> i agregowanie danych przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="11802-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="11802-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="11802-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="11802-105">Przykłady w tym temacie można użyć kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabel w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="11802-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="11802-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="11802-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="11802-107">Aby uzyskać więcej informacji, zobacz [porady: tworzenie LINQ do DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="11802-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="11802-108">Średnia</span><span class="sxs-lookup"><span data-stu-id="11802-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="11802-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-109">Example</span></span>  
 <span data-ttu-id="11802-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średniej ceny listy produktów każdy styl.</span><span class="sxs-lookup"><span data-stu-id="11802-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="11802-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-111">Example</span></span>  
 <span data-ttu-id="11802-112">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> uzyskanie Średnia łączna powodu dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="11802-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="11802-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-113">Example</span></span>  
 <span data-ttu-id="11802-114">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> uzyskać zamówień ze średnią `TotalDue` dla każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="11802-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="11802-115">Liczba</span><span class="sxs-lookup"><span data-stu-id="11802-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="11802-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-116">Example</span></span>  
 <span data-ttu-id="11802-117">W tym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> aby zwrócić listę skontaktuj się z identyfikatorów i ile porządkuje każdy ma.</span><span class="sxs-lookup"><span data-stu-id="11802-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="11802-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-118">Example</span></span>  
 <span data-ttu-id="11802-119">W tym przykładzie grupy produktów przez kolor i używa <xref:System.Linq.Enumerable.Count%2A> do zwrócenia liczba produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="11802-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="11802-120">Maksymalna</span><span class="sxs-lookup"><span data-stu-id="11802-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="11802-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-121">Example</span></span>  
 <span data-ttu-id="11802-122">W tym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać największy termin całkowitą dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="11802-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="11802-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-123">Example</span></span>  
 <span data-ttu-id="11802-124">W tym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby pobrać zamówień z największych `TotalDue` dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="11802-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="11802-125">Min</span><span class="sxs-lookup"><span data-stu-id="11802-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="11802-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-126">Example</span></span>  
 <span data-ttu-id="11802-127">W tym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać najmniejszą termin całkowitą dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="11802-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="11802-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-128">Example</span></span>  
 <span data-ttu-id="11802-129">W tym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby pobrać zamówień z najmniejszą sumę do każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="11802-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="11802-130">Suma</span><span class="sxs-lookup"><span data-stu-id="11802-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="11802-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="11802-131">Example</span></span>  
 <span data-ttu-id="11802-132">W tym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby pobrać całkowitej ukończenia dla każdej skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="11802-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="11802-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11802-133">See Also</span></span>  
 [<span data-ttu-id="11802-134">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="11802-134">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="11802-135">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="11802-135">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="11802-136">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="11802-136">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
