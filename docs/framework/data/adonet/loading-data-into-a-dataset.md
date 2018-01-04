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
# <a name="loading-data-into-a-dataset"></a>Podczas ładowania danych do zestawu danych
A <xref:System.Data.DataSet> obiektu najpierw powinno zostać zapełnione przed można zbadać nad nim z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Istnieje kilka różnych sposobów, aby wypełnić <xref:System.Data.DataSet>. Na przykład można użyć [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] w bazie danych i ładuje wyniki do <xref:System.Data.DataSet>. Aby uzyskać więcej informacji, zobacz [LINQ do SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Inny typowy sposób, aby załadować dane <xref:System.Data.DataSet> jest użycie <xref:System.Data.Common.DataAdapter> klasy można pobrać danych z bazy danych. Jest to zilustrowane w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Data.Common.DataAdapter> do informacji o sprzedaży z roku 2002, w bazie danych AdventureWorks i ładuje wyniki do <xref:System.Data.DataSet>. Po <xref:System.Data.DataSet> zostały wypełnione, można zapisać zapytania na nim przy użyciu [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. `FillDataSet` Metoda w tym przykładzie jest używana w przykładowych zapytań w [LINQ do DataSet przykłady](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Aby uzyskać więcej informacji, zobacz [zapytań zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [Wykonywanie zapytania do zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
