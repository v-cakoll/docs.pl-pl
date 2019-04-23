---
title: Tworzenie elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d2d17056e6dcd29ef9b5c5e8c3024a32fce32bd5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118186"
---
# <a name="creating-a-dataset"></a>Tworzenie elementu DataSet
Utwórz wystąpienie <xref:System.Data.DataSet> przez wywołanie metody <xref:System.Data.DataSet> konstruktora. Opcjonalnie można określić argument nazwy. Jeśli nie określisz nazwę <xref:System.Data.DataSet>, nazwa jest równa "NewDataSet".  
  
 Można również utworzyć nową <xref:System.Data.DataSet> oparty na istniejącym <xref:System.Data.DataSet>. Nowy <xref:System.Data.DataSet> może być dokładną kopię istniejącego <xref:System.Data.DataSet>; klonu <xref:System.Data.DataSet> , kopiuje relacyjnej struktury lub schematu, ale która nie zawiera żadnych danych z istniejącego <xref:System.Data.DataSet>; lub być podzbiorem wartości <xref:System.Data.DataSet>, zawierająca tylko zmodyfikowane wiersze z istniejącego <xref:System.Data.DataSet> przy użyciu <xref:System.Data.DataSet.GetChanges%2A> metody. Aby uzyskać więcej informacji, zobacz [kopiowanie zawartości elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).  
  
 Poniższy przykład kodu pokazuje, jak skonstruować wystąpienia <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawu danych z elementu DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
