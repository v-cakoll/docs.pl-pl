---
title: Metody AcceptChanges i RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: bbcc666b99c2bade479e5ee51750b043c820845d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172903"
---
# <a name="acceptchanges-and-rejectchanges"></a>Metody AcceptChanges i RejectChanges
Po sprawdzeniu dokładności zmian wprowadzonych w danych w <xref:System.Data.DataTable>, możesz zaakceptować zmiany, używając <xref:System.Data.DataRow.AcceptChanges%2A> metody <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataSet>, który ustawi **bieżącego** wiersza wartości, które mają być **oryginalnego** wartości i ustawi **RowState** właściwości **Unchanged**. Akceptowanie lub odrzucanie zmian czyści jakąkolwiek **RowError** informacji i zestawy **HasErrors** właściwości **false**. Akceptowanie lub odrzucanie zmian może również wpływać na aktualizowanie danych w źródle danych. Aby uzyskać więcej informacji, zobacz [aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Jeśli istnieją ograniczenia klucza obcego, na **DataTable**, zmiany zaakceptowane lub odrzucone, za pomocą **AcceptChanges** i **RejectChanges** są propagowane do podrzędnych wiersze  **DataRow** zgodnie z opisem w **ForeignKeyConstraint.AcceptRejectRule**. Aby uzyskać więcej informacji, zobacz [ograniczenia elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Poniższy przykład sprawdza wiersze z błędami, rozwiązuje błędy, jeśli ma to zastosowanie i odrzuca wiersze, w którym ten błąd nie można rozpoznać. Należy pamiętać, że dla rozwiązane błędy, **RowError** jest ustawiany na pusty ciąg, powodując **HasErrors** właściwość należy ustawić **false**. Gdy wszystkie wiersze z błędami zostały rozwiązane lub odrzucone, **AcceptChanges** jest wywoływana, aby zaakceptować wszystkie zmiany dla całego **DataTable**.  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Operowanie na danych w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
