---
title: Ładowanie danych do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: cb5578d790e5d3f54f75f964bb3288d861c9d7c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074056"
---
# <a name="loading-data-into-a-dataset"></a>Ładowanie danych do zestawu danych
A <xref:System.Data.DataSet> obiektu najpierw muszą być wypełnione, zanim można tworzyć zapytania nad nim za pomocą [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Istnieje kilka różnych sposobów, aby wypełnić <xref:System.Data.DataSet>. Na przykład, można użyć [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] w bazie danych i ładuje wyniki do <xref:System.Data.DataSet>. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Inny typowy sposób ładowania danych do <xref:System.Data.DataSet> jest użycie <xref:System.Data.Common.DataAdapter> klasy do pobrania danych z bazy danych. Jest to zilustrowane w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Data.Common.DataAdapter> kwerendy bazy danych AdventureWorks, aby uzyskać informacji o sprzedaży z roku 2002 i ładuje wyniki do <xref:System.Data.DataSet>. Po <xref:System.Data.DataSet> została wypełniona, możesz pisać zapytania względem go za pomocą [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. `FillDataSet` Metoda w tym przykładzie jest używana w przykładowych zapytań w [przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Aby uzyskać więcej informacji, zobacz [podczas badania zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [Wykonywanie zapytania do zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
