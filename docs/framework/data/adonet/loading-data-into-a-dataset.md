---
title: Trwa ładowanie danych do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 0f50638beb50220d06daef7bbd6002b319a92476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622965"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="8ee47-102">Trwa ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="8ee47-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="8ee47-103">A <xref:System.Data.DataSet> obiektu najpierw muszą być wypełnione, zanim można tworzyć zapytania nad nim za pomocą [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ee47-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="8ee47-104">Istnieje kilka różnych sposobów, aby wypełnić <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8ee47-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8ee47-105">Na przykład, można użyć [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] w bazie danych i ładuje wyniki do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8ee47-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8ee47-106">Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ee47-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="8ee47-107">Inny typowy sposób ładowania danych do <xref:System.Data.DataSet> jest użycie <xref:System.Data.Common.DataAdapter> klasy do pobrania danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8ee47-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="8ee47-108">Jest to zilustrowane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ee47-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ee47-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ee47-109">Example</span></span>  
 <span data-ttu-id="8ee47-110">W tym przykładzie użyto <xref:System.Data.Common.DataAdapter> kwerendy bazy danych AdventureWorks, aby uzyskać informacji o sprzedaży z roku 2002 i ładuje wyniki do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8ee47-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8ee47-111">Po <xref:System.Data.DataSet> została wypełniona, możesz pisać zapytania względem go za pomocą [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ee47-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="8ee47-112">`FillDataSet` Metoda w tym przykładzie jest używana w przykładowych zapytań w [przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="8ee47-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="8ee47-113">Aby uzyskać więcej informacji, zobacz [podczas badania zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8ee47-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="8ee47-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ee47-114">See also</span></span>
- [<span data-ttu-id="8ee47-115">Omówienie LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8ee47-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="8ee47-116">Wykonywanie zapytania do zestawów danych</span><span class="sxs-lookup"><span data-stu-id="8ee47-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="8ee47-117">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8ee47-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
