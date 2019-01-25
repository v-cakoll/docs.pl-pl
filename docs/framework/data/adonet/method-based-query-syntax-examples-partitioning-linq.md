---
title: 'Przykłady składni zapytania oparte na metodzie: Partycjonowanie (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: a18f19ead84d3b91b3ddd724360f3800abe286b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524744"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="1feee-102">Przykłady składni zapytania oparte na metodzie: Partycjonowanie (LINQ</span><span class="sxs-lookup"><span data-stu-id="1feee-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>
<span data-ttu-id="1feee-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, i <xref:System.Linq.Enumerable.TakeWhile%2A> metod do wykonywania zapytań <xref:System.Data.DataSet> przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="1feee-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="1feee-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="1feee-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="1feee-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1feee-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1feee-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1feee-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="1feee-107">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu LINQ to DataSet w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1feee-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="1feee-108">Skip</span><span class="sxs-lookup"><span data-stu-id="1feee-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="1feee-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1feee-109">Example</span></span>  
 <span data-ttu-id="1feee-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.Skip%2A> metodę, aby uzyskać wszystkie, ale pięciu pierwszych kontakty `Contact` tabeli.</span><span class="sxs-lookup"><span data-stu-id="1feee-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="1feee-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="1feee-111">Example</span></span>  
 <span data-ttu-id="1feee-112">W tym przykładzie użyto <xref:System.Linq.Enumerable.Skip%2A> metodę, aby uzyskać wszystkie, ale pierwsze dwa adresy w Seattle.</span><span class="sxs-lookup"><span data-stu-id="1feee-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="1feee-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="1feee-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="1feee-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1feee-114">Example</span></span>  
 <span data-ttu-id="1feee-115">W tym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> i <xref:System.Linq.Enumerable.SkipWhile%2A> metody zwracają produkty z `Product` tabelę z cennika większa niż 300.00.</span><span class="sxs-lookup"><span data-stu-id="1feee-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="1feee-116">Take</span><span class="sxs-lookup"><span data-stu-id="1feee-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="1feee-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="1feee-117">Example</span></span>  
 <span data-ttu-id="1feee-118">W tym przykładzie użyto <xref:System.Linq.Enumerable.Take%2A> metodę, aby uzyskać tylko pięć pierwszych kontaktuje się z `Contact` tabeli.</span><span class="sxs-lookup"><span data-stu-id="1feee-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="1feee-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="1feee-119">Example</span></span>  
 <span data-ttu-id="1feee-120">W tym przykładzie użyto <xref:System.Linq.Enumerable.Take%2A> metodę, aby uzyskać pierwszych trzech adresów w Seattle.</span><span class="sxs-lookup"><span data-stu-id="1feee-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="1feee-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="1feee-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="1feee-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="1feee-122">Example</span></span>  
 <span data-ttu-id="1feee-123">W tym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> i <xref:System.Linq.Enumerable.TakeWhile%2A> do zwrócenia produkty z `Product` tabeli z ceną listy mniejszą niż 300.00.</span><span class="sxs-lookup"><span data-stu-id="1feee-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1feee-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1feee-124">See also</span></span>
- [<span data-ttu-id="1feee-125">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1feee-125">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="1feee-126">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1feee-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="1feee-127">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="1feee-127">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
