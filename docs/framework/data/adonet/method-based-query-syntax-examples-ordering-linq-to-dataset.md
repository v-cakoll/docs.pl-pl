---
title: "Przykłady składni zapytania oparte na metodzie: Porządkowanie (LINQ do DataSet)"
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
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 11ab18d16c9c6e3dd62dafd26f309fd940fbc244
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="fc1fa-102">Przykłady składni zapytania oparte na metodzie: Porządkowanie (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="fc1fa-102">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="fc1fa-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, i <xref:System.Linq.Enumerable.ThenBy%2A> metod do badania <xref:System.Data.DataSet> i kolejność wyniki za pomocą składni zapytania metody.</span><span class="sxs-lookup"><span data-stu-id="fc1fa-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="fc1fa-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="fc1fa-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="fc1fa-105">Przykłady w tym temacie można użyć kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabel w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fc1fa-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fc1fa-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="fc1fa-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="fc1fa-107">Aby uzyskać więcej informacji, zobacz [porady: tworzenie LINQ do DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="fc1fa-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="fc1fa-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="fc1fa-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="fc1fa-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc1fa-109">Example</span></span>  
 <span data-ttu-id="fc1fa-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> metody o niestandardowych moduł porównujący sortowania bez uwzględniania wielkości liter nazwisk zrobić.</span><span class="sxs-lookup"><span data-stu-id="fc1fa-110">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="fc1fa-111">Reverse</span><span class="sxs-lookup"><span data-stu-id="fc1fa-111">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="fc1fa-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc1fa-112">Example</span></span>  
 <span data-ttu-id="fc1fa-113">W tym przykładzie użyto <xref:System.Linq.Enumerable.Reverse%2A> metodę, aby utworzyć listę zleceń, gdzie `OrderDate` jest starsza niż 20 luty 2002.</span><span class="sxs-lookup"><span data-stu-id="fc1fa-113">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="fc1fa-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="fc1fa-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="fc1fa-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc1fa-115">Example</span></span>  
 <span data-ttu-id="fc1fa-116">W tym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> i <xref:System.Linq.Enumerable.ThenBy%2A> metody o niestandardowej funkcji porównującej pierwszy sortować cennika, a następnie wykonaj malejącym bez uwzględniania wielkości liter nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="fc1fa-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="fc1fa-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc1fa-117">See Also</span></span>  
 [<span data-ttu-id="fc1fa-118">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="fc1fa-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="fc1fa-119">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="fc1fa-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="fc1fa-120">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="fc1fa-120">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
