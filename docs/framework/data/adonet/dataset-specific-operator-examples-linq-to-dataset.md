---
title: Przykłady operatorów specyficznych dla zestawu danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 27a48b7ffe5466c52f19f15cf3c1a6cb558028b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097345"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="5e8d5-102">Przykłady operatorów specyficznych dla zestawu danych (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="5e8d5-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="5e8d5-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody i <xref:System.Data.DataRowComparer> klasy.</span><span class="sxs-lookup"><span data-stu-id="5e8d5-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="5e8d5-104">`FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5e8d5-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="5e8d5-105">Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5e8d5-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5e8d5-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="5e8d5-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="5e8d5-107">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu LINQ to DataSet w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5e8d5-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="5e8d5-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="5e8d5-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e8d5-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e8d5-109">Example</span></span>  
 <span data-ttu-id="5e8d5-110">W tym przykładzie ładuje <xref:System.Data.DataTable> z wynikami zapytania przy użyciu <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5e8d5-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="5e8d5-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="5e8d5-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e8d5-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e8d5-112">Example</span></span>  
 <span data-ttu-id="5e8d5-113">W tym przykładzie porównano dwa wiersze z różnymi danymi za pomocą <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="5e8d5-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="5e8d5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e8d5-114">See also</span></span>

- [<span data-ttu-id="5e8d5-115">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5e8d5-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="5e8d5-116">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5e8d5-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
