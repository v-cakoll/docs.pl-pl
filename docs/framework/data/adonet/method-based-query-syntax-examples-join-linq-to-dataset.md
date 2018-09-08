---
title: Przykłady składni zapytania oparte na metodzie sprzężenia (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 6ec65cad0070bdbd1d510bcc822f3b71f9cf69dc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195296"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="63035-102">Przykłady składni zapytania oparte na metodzie sprzężenia (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="63035-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="63035-103">Łączenie jest operacją ważne w zapytaniach, przeznaczonych dla źródeł danych, które mają żadnych relacji można nawigować do siebie nawzajem, takich jak tabel relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="63035-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="63035-104">Przyłączenia dwóch źródeł danych jest skojarzenie obiektów w jednym źródle danych przy użyciu obiektów mających wspólny atrybut w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="63035-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="63035-105">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="63035-105">For more information, see [Standard Query Operators Overview](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="63035-106">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Join%2A> metody zapytania <xref:System.Data.DataSet> za pomocą składni zapytania metody.</span><span class="sxs-lookup"><span data-stu-id="63035-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="63035-107">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="63035-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="63035-108">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="63035-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="63035-109">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="63035-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="63035-110">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika LINQ to DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="63035-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="63035-111">Łączenie</span><span class="sxs-lookup"><span data-stu-id="63035-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="63035-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="63035-112">Example</span></span>  
 <span data-ttu-id="63035-113">W tym przykładzie wykonuje sprzężenie `Contact` i `SalesOrderHeader` tabel.</span><span class="sxs-lookup"><span data-stu-id="63035-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="63035-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="63035-114">Example</span></span>  
 <span data-ttu-id="63035-115">W tym przykładzie wykonuje sprzężenie `Contact` i `SalesOrderHeader` tabel, grupowanie wyników według identyfikatora. Skontaktuj się z</span><span class="sxs-lookup"><span data-stu-id="63035-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="63035-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63035-116">See Also</span></span>  
 [<span data-ttu-id="63035-117">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="63035-117">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="63035-118">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="63035-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="63035-119">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="63035-119">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [<span data-ttu-id="63035-120">Dołącz do przykładów</span><span class="sxs-lookup"><span data-stu-id="63035-120">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)  
 [<span data-ttu-id="63035-121">Przykłady zestawu danych</span><span class="sxs-lookup"><span data-stu-id="63035-121">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
