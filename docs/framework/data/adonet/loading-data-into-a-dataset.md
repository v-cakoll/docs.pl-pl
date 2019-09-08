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
# <a name="loading-data-into-a-dataset"></a>Ładowanie danych do zestawu danych
Aby można było wykonać zapytanie dotyczące obiektuprzyużyciuLINQtoDataSet,należynajpierwwypełnićobiekt.<xref:System.Data.DataSet> Istnieje kilka różnych sposobów wypełnienia <xref:System.Data.DataSet>. Na przykład można użyć [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] programu do wysyłania zapytań do bazy danych i załadowania wyników <xref:System.Data.DataSet>do. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](./sql/linq/index.md).  
  
 Innym typowym sposobem ładowania danych do programu <xref:System.Data.DataSet> jest <xref:System.Data.Common.DataAdapter> użycie klasy do pobierania danych z bazy danych. Jest to zilustrowane w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa <xref:System.Data.Common.DataAdapter> się do wysyłania zapytań do bazy danych AdventureWorks o informacje o sprzedaży z roku 2002 i ładowania wyników do <xref:System.Data.DataSet>programu. <xref:System.Data.DataSet> Po wypełnieniu można napisać zapytania do niego przy użyciu LINQ to DataSet. Metoda w tym przykładzie jest używana w przykładowych kwerendach [LINQ to DataSet przykładów.](linq-to-dataset-examples.md) `FillDataSet` Aby uzyskać więcej informacji, zobacz [wykonywanie zapytania dotyczącego zestawów danych](querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie LINQ to DataSet](linq-to-dataset-overview.md)
- [Wykonywanie zapytania do zestawów danych](querying-datasets-linq-to-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
