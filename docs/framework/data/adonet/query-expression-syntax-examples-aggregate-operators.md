---
title: 'Przykłady składni wyrażeń zapytania: Operatory agregacji (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: fe3bd69b17b98e923c6c31fec2611e7390894e4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398540"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="5fd44-102">Przykłady składni wyrażeń zapytania: Operatory agregacji (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="5fd44-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="5fd44-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> metod do wykonywania zapytań <xref:System.Data.DataSet> i agregowanie danych przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="5fd44-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="5fd44-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5fd44-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="5fd44-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5fd44-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5fd44-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="5fd44-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="5fd44-107">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika LINQ to DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5fd44-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="5fd44-108">Średnia</span><span class="sxs-lookup"><span data-stu-id="5fd44-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="5fd44-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-109">Example</span></span>  
 <span data-ttu-id="5fd44-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średnia cena listy produktów każdego stylu.</span><span class="sxs-lookup"><span data-stu-id="5fd44-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="5fd44-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-111">Example</span></span>  
 <span data-ttu-id="5fd44-112">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> można uzyskać Średnia łączna liczba ze względu każdy skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5fd44-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="5fd44-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-113">Example</span></span>  
 <span data-ttu-id="5fd44-114">W tym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> można pobrać zamówień ze średnią `TotalDue` dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="5fd44-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="5fd44-115">Liczba</span><span class="sxs-lookup"><span data-stu-id="5fd44-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="5fd44-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-116">Example</span></span>  
 <span data-ttu-id="5fd44-117">W tym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> zwrócić listę skontaktuj się z identyfikatorów i jak wiele zamówień, każdy ma.</span><span class="sxs-lookup"><span data-stu-id="5fd44-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="5fd44-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-118">Example</span></span>  
 <span data-ttu-id="5fd44-119">W tym przykładzie grupy produktów, kolor i używa <xref:System.Linq.Enumerable.Count%2A> zwrócić wiele produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="5fd44-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="5fd44-120">Maksymalna</span><span class="sxs-lookup"><span data-stu-id="5fd44-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="5fd44-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-121">Example</span></span>  
 <span data-ttu-id="5fd44-122">W tym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać największy termin całkowita dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5fd44-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="5fd44-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-123">Example</span></span>  
 <span data-ttu-id="5fd44-124">W tym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać zamówień o największej `TotalDue` dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5fd44-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="5fd44-125">min</span><span class="sxs-lookup"><span data-stu-id="5fd44-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="5fd44-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-126">Example</span></span>  
 <span data-ttu-id="5fd44-127">W tym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać najmniejszy termin całkowitą dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5fd44-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="5fd44-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-128">Example</span></span>  
 <span data-ttu-id="5fd44-129">W tym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać zamówienia z sumą najmniejszy termin dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="5fd44-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="5fd44-130">Suma</span><span class="sxs-lookup"><span data-stu-id="5fd44-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="5fd44-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd44-131">Example</span></span>  
 <span data-ttu-id="5fd44-132">W tym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby uzyskać całkowity termin dla każdego skontaktuj się z identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5fd44-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="5fd44-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fd44-133">See Also</span></span>  
 [<span data-ttu-id="5fd44-134">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5fd44-134">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="5fd44-135">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5fd44-135">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="5fd44-136">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="5fd44-136">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
