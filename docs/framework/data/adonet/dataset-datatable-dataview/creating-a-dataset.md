---
title: Tworzenie zestawu danych
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
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16ab7a7ba65e915ec8bede1d075625c00e90960c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-dataset"></a>Tworzenie zestawu danych
Utwórz wystąpienie <xref:System.Data.DataSet> przez wywołanie metody <xref:System.Data.DataSet> konstruktora. Opcjonalnie można określić argument nazwy. Jeśli nie określisz nazwy <xref:System.Data.DataSet>, nazwa jest równa "NewDataSet".  
  
 Można również utworzyć nowy <xref:System.Data.DataSet> oparte na istniejącym <xref:System.Data.DataSet>. Nowy <xref:System.Data.DataSet> może być dokładną kopię istniejącej <xref:System.Data.DataSet>; klonu <xref:System.Data.DataSet> który kopiuje relacyjne struktury lub schematu, ale który nie zawiera żadnych danych z istniejącego <xref:System.Data.DataSet>; lub podzbiór <xref:System.Data.DataSet>, zawierający tylko zmodyfikowanych wierszy z istniejącego <xref:System.Data.DataSet> przy użyciu <xref:System.Data.DataSet.GetChanges%2A> metody. Aby uzyskać więcej informacji, zobacz [kopiowanie zawartości zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).  
  
 Poniższy przykład kodu pokazuje sposób tworzenia wystąpienia <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wypełnianie zestawu danych z element DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Zbiory danych, DataTables i DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
