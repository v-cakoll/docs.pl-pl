---
title: 'Przykłady składni zapytania oparte na metodzie: Join (LINQ do DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: e061c5fea0a406169ba9de29d62192dbff6fb7f6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="73ea4-102">Przykłady składni zapytania oparte na metodzie: Join (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="73ea4-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="73ea4-103">Sprzęganie jest ważne operacji w zapytaniach, które odnoszą się do źródła danych, których nie można nawigować relacje między, takich jak tabele relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="73ea4-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="73ea4-104">Sprzężenia dwóch źródeł danych jest skojarzenie obiektów w jedno źródło danych z obiektami, które mają wspólny atrybut w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="73ea4-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="73ea4-105">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="73ea4-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="73ea4-106">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Join%2A> metody query <xref:System.Data.DataSet> przy użyciu składni zapytania metody.</span><span class="sxs-lookup"><span data-stu-id="73ea4-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="73ea4-107">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="73ea4-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="73ea4-108">Przykłady w tym temacie można użyć kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabel w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="73ea4-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="73ea4-109">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="73ea4-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="73ea4-110">Aby uzyskać więcej informacji, zobacz [porady: tworzenie LINQ do DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="73ea4-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="73ea4-111">Łączenie</span><span class="sxs-lookup"><span data-stu-id="73ea4-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="73ea4-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="73ea4-112">Example</span></span>  
 <span data-ttu-id="73ea4-113">W tym przykładzie wykonuje sprzężenie za pośrednictwem `Contact` i `SalesOrderHeader` tabel.</span><span class="sxs-lookup"><span data-stu-id="73ea4-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="73ea4-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="73ea4-114">Example</span></span>  
 <span data-ttu-id="73ea4-115">W tym przykładzie wykonuje sprzężenie za pośrednictwem `Contact` i `SalesOrderHeader` tabel, grupowanie wyników według identyfikatora. Skontaktuj się z</span><span class="sxs-lookup"><span data-stu-id="73ea4-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="73ea4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73ea4-116">See Also</span></span>  
 [<span data-ttu-id="73ea4-117">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="73ea4-117">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="73ea4-118">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="73ea4-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="73ea4-119">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="73ea4-119">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [<span data-ttu-id="73ea4-120">JOIN — przykłady</span><span class="sxs-lookup"><span data-stu-id="73ea4-120">Join Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=187357)  
 [<span data-ttu-id="73ea4-121">Przykłady zestawu danych</span><span class="sxs-lookup"><span data-stu-id="73ea4-121">Dataset Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=187358)
