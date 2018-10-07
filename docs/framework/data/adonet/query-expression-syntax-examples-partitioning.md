---
title: 'Przykłady składni wyrażeń zapytania: Partycjonowania (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 456e4289af2c71ee2ef96f48939dc9f7b70c6bc0
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842336"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="0570f-102">Przykłady składni wyrażeń zapytania: Partycjonowania (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0570f-102">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>
<span data-ttu-id="0570f-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> metod do wykonywania zapytań <xref:System.Data.DataSet> przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="0570f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="0570f-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="0570f-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0570f-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0570f-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0570f-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="0570f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0570f-107">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika LINQ to DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0570f-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="0570f-108">Skip</span><span class="sxs-lookup"><span data-stu-id="0570f-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="0570f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0570f-109">Example</span></span>  
 <span data-ttu-id="0570f-110">W tym przykładzie użyto <xref:System.Linq.Enumerable.Skip%2A> metodę, aby uzyskać wszystkie, ale pierwsze dwa adresy w Seattle.</span><span class="sxs-lookup"><span data-stu-id="0570f-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="0570f-111">Take</span><span class="sxs-lookup"><span data-stu-id="0570f-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="0570f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0570f-112">Example</span></span>  
 <span data-ttu-id="0570f-113">W tym przykładzie użyto <xref:System.Linq.Enumerable.Take%2A> metodę, aby uzyskać pierwszych trzech adresów w Seattle.</span><span class="sxs-lookup"><span data-stu-id="0570f-113">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="0570f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0570f-114">See Also</span></span>  
 [<span data-ttu-id="0570f-115">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="0570f-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="0570f-116">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0570f-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="0570f-117">Standardowe operatory zapytań — przegląd</span><span class="sxs-lookup"><span data-stu-id="0570f-117">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
