---
title: Przykłady operatorów specyficznych dla zestawu danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 6a9dc82e0bb065b455c0208daaf2d28a74cd7e34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784202"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="d3fed-102">Przykłady operatorów specyficznych dla zestawu danych (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d3fed-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="d3fed-103">W przykładach w tym temacie pokazano, jak używać <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody <xref:System.Data.DataRowComparer> i klasy.</span><span class="sxs-lookup"><span data-stu-id="d3fed-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="d3fed-104">Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="d3fed-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="d3fed-105">W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d3fed-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d3fed-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="d3fed-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="d3fed-107">Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d3fed-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="d3fed-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="d3fed-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3fed-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3fed-109">Example</span></span>  
 <span data-ttu-id="d3fed-110">Ten przykład ładuje <xref:System.Data.DataTable> wyniki zapytania przy <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="d3fed-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="d3fed-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="d3fed-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3fed-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3fed-112">Example</span></span>  
 <span data-ttu-id="d3fed-113">Ten przykład porównuje dwa różne wiersze danych przy <xref:System.Data.DataRowComparer>użyciu.</span><span class="sxs-lookup"><span data-stu-id="d3fed-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="d3fed-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3fed-114">See also</span></span>

- [<span data-ttu-id="d3fed-115">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d3fed-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="d3fed-116">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d3fed-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
