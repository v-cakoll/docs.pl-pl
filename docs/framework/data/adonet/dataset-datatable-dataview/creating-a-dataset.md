---
title: Tworzenie zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 3c48b430b1a087a79db37398b2c68014b8077c55
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
 [Wypełnianie zestawu danych z elementu DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
