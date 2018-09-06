---
title: 'Przykłady składni wyrażeń zapytania: Porządkowanie (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: 1e3ee4372c1c2173cff0d93dfdf84c96c60130d4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43778814"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="d0820-102">Przykłady składni wyrażeń zapytania: Porządkowanie (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d0820-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="d0820-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, i <xref:System.Linq.Enumerable.ThenByDescending%2A> metod do wykonywania zapytań <xref:System.Data.DataSet> i kolejność wyników przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="d0820-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="d0820-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="d0820-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="d0820-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d0820-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d0820-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d0820-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="d0820-107">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika LINQ to DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d0820-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="d0820-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="d0820-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0820-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0820-109">Example</span></span>  
 <span data-ttu-id="d0820-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> aby powrócić do listy kontaktów, uporządkowane według nazwiska.</span><span class="sxs-lookup"><span data-stu-id="d0820-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="d0820-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0820-111">Example</span></span>  
 <span data-ttu-id="d0820-112">W tym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> Aby posortować listę kontaktów według długości nazwisko.</span><span class="sxs-lookup"><span data-stu-id="d0820-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="d0820-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="d0820-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0820-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0820-114">Example</span></span>  
 <span data-ttu-id="d0820-115">W tym przykładzie użyto `orderby… descending` (`Order By … Descending`), który jest odpowiednikiem <xref:System.Linq.Enumerable.OrderByDescending%2A> metody sortowania w cenniku, od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="d0820-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="d0820-116">zwrotny</span><span class="sxs-lookup"><span data-stu-id="d0820-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0820-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0820-117">Example</span></span>  
 <span data-ttu-id="d0820-118">W tym przykładzie użyto <xref:System.Linq.Enumerable.Reverse%2A> utworzyć listę zleceń gdzie `OrderDate` jest starsza niż 20 lutego 2002.</span><span class="sxs-lookup"><span data-stu-id="d0820-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="d0820-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="d0820-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0820-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0820-120">Example</span></span>  
 <span data-ttu-id="d0820-121">W tym przykładzie użyto `OrderBy… Descending` , który jest odpowiednikiem <xref:System.Linq.Enumerable.ThenByDescending%2A> metody, aby posortować listę produktów, najpierw według nazwy, a następnie według cennika, od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="d0820-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="d0820-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0820-122">See Also</span></span>  
 [<span data-ttu-id="d0820-123">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d0820-123">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="d0820-124">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d0820-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="d0820-125">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="d0820-125">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
