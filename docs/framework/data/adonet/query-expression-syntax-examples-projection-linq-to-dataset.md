---
title: "Przykłady składni wyrażeń zapytania: Projekcji (LINQ do DataSet)"
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
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9aab649eebdccc480f4681da5e3d9499cb62eab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="43d30-102">Przykłady składni wyrażeń zapytania: Projekcji (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="43d30-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="43d30-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Select%2A> i <xref:System.Linq.Enumerable.SelectMany%2A> metod do badania <xref:System.Data.DataSet> przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="43d30-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="43d30-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="43d30-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="43d30-105">Przykłady w tym temacie można użyć kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabel w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="43d30-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="43d30-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="43d30-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="43d30-107">Aby uzyskać więcej informacji, zobacz [porady: tworzenie LINQ do DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="43d30-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="43d30-108">Wybierz</span><span class="sxs-lookup"><span data-stu-id="43d30-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="43d30-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="43d30-109">Example</span></span>  
 <span data-ttu-id="43d30-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> metodę zwracanie wszystkich wierszy z `Product` tabelę i wyświetlić nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="43d30-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="43d30-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="43d30-111">Example</span></span>  
 <span data-ttu-id="43d30-112">W tym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> do zwrócenia sekwencję tylko nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="43d30-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="43d30-113">Operacja SelectMany</span><span class="sxs-lookup"><span data-stu-id="43d30-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="43d30-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="43d30-114">Example</span></span>  
 <span data-ttu-id="43d30-115">W tym przykładzie użyto `From …, …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metody) aby wybrać wszystkie porządkuje where `TotalDue` jest mniejsza niż 500,00.</span><span class="sxs-lookup"><span data-stu-id="43d30-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="43d30-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="43d30-116">Example</span></span>  
 <span data-ttu-id="43d30-117">W tym przykładzie użyto `From …, …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metody) do wybrania wszystkich zleceń, których kolejność została wprowadzona w 1 października 2002 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="43d30-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="43d30-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="43d30-118">Example</span></span>  
 <span data-ttu-id="43d30-119">W tym przykładzie użyto `From …, …` (odpowiednikiem <xref:System.Linq.Enumerable.SelectMany%2A> — metoda) do wszystkich zleceń, których kolejność całkowita liczba jest większa niż 10000.00 i używa wybierz `From` przypisania, aby uniknąć żąda łączną dwa razy.</span><span class="sxs-lookup"><span data-stu-id="43d30-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="43d30-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43d30-120">See Also</span></span>  
 [<span data-ttu-id="43d30-121">Podczas ładowania danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="43d30-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="43d30-122">LINQ do DataSet przykłady</span><span class="sxs-lookup"><span data-stu-id="43d30-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="43d30-123">Operatory standardowe zapytań — omówienie</span><span class="sxs-lookup"><span data-stu-id="43d30-123">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
