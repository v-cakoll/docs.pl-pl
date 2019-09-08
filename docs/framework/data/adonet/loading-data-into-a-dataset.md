---
title: Ładowanie danych do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794957"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="f83d5-102">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="f83d5-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="f83d5-103">Aby można było wykonać zapytanie dotyczące obiektuprzyużyciuLINQtoDataSet,należynajpierwwypełnićobiekt.<xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="f83d5-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="f83d5-104">Istnieje kilka różnych sposobów wypełnienia <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f83d5-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f83d5-105">Na przykład można użyć [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] programu do wysyłania zapytań do bazy danych i załadowania wyników <xref:System.Data.DataSet>do.</span><span class="sxs-lookup"><span data-stu-id="f83d5-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f83d5-106">Aby uzyskać więcej informacji, zobacz [LINQ to SQL](./sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="f83d5-106">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="f83d5-107">Innym typowym sposobem ładowania danych do programu <xref:System.Data.DataSet> jest <xref:System.Data.Common.DataAdapter> użycie klasy do pobierania danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f83d5-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="f83d5-108">Jest to zilustrowane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f83d5-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f83d5-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f83d5-109">Example</span></span>  
 <span data-ttu-id="f83d5-110">W tym przykładzie używa <xref:System.Data.Common.DataAdapter> się do wysyłania zapytań do bazy danych AdventureWorks o informacje o sprzedaży z roku 2002 i ładowania wyników do <xref:System.Data.DataSet>programu.</span><span class="sxs-lookup"><span data-stu-id="f83d5-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f83d5-111"><xref:System.Data.DataSet> Po wypełnieniu można napisać zapytania do niego przy użyciu LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="f83d5-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="f83d5-112">Metoda w tym przykładzie jest używana w przykładowych kwerendach [LINQ to DataSet przykładów.](linq-to-dataset-examples.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="f83d5-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="f83d5-113">Aby uzyskać więcej informacji, zobacz [wykonywanie zapytania dotyczącego zestawów danych](querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="f83d5-113">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="f83d5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f83d5-114">See also</span></span>

- [<span data-ttu-id="f83d5-115">Omówienie LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f83d5-115">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="f83d5-116">Wykonywanie zapytania do zestawów danych</span><span class="sxs-lookup"><span data-stu-id="f83d5-116">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="f83d5-117">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f83d5-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
