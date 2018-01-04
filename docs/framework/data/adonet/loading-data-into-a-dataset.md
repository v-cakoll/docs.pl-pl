---
title: "Podczas ładowania danych do zestawu danych"
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
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 471a13b5d209def227bf8bc57b1551550b76a0c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="7efb5-102">Podczas ładowania danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7efb5-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="7efb5-103">A <xref:System.Data.DataSet> obiektu najpierw powinno zostać zapełnione przed można zbadać nad nim z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7efb5-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="7efb5-104">Istnieje kilka różnych sposobów, aby wypełnić <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="7efb5-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7efb5-105">Na przykład można użyć [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] w bazie danych i ładuje wyniki do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="7efb5-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7efb5-106">Aby uzyskać więcej informacji, zobacz [LINQ do SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="7efb5-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="7efb5-107">Inny typowy sposób, aby załadować dane <xref:System.Data.DataSet> jest użycie <xref:System.Data.Common.DataAdapter> klasy można pobrać danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7efb5-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="7efb5-108">Jest to zilustrowane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7efb5-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7efb5-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7efb5-109">Example</span></span>  
 <span data-ttu-id="7efb5-110">W tym przykładzie użyto <xref:System.Data.Common.DataAdapter> do informacji o sprzedaży z roku 2002, w bazie danych AdventureWorks i ładuje wyniki do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="7efb5-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7efb5-111">Po <xref:System.Data.DataSet> zostały wypełnione, można zapisać zapytania na nim przy użyciu [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7efb5-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="7efb5-112">`FillDataSet` Metoda w tym przykładzie jest używana w przykładowych zapytań w [LINQ do DataSet przykłady](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="7efb5-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="7efb5-113">Aby uzyskać więcej informacji, zobacz [zapytań zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="7efb5-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="7efb5-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7efb5-114">See Also</span></span>  
 [<span data-ttu-id="7efb5-115">Omówienie LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7efb5-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="7efb5-116">Wykonywanie zapytania do zestawów danych</span><span class="sxs-lookup"><span data-stu-id="7efb5-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="7efb5-117">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7efb5-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
