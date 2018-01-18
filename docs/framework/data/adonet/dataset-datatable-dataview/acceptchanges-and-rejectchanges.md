---
title: Metoda AcceptChanges i RejectChanges
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
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4c7d86aed61957d15d9c37f494bf80088b164dea
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="acceptchanges-and-rejectchanges"></a>Metoda AcceptChanges i RejectChanges
Po sprawdzeniu dokładności zmiany wprowadzone w danych w <xref:System.Data.DataTable>, możesz zaakceptować zmiany przy użyciu <xref:System.Data.DataRow.AcceptChanges%2A> metody <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataSet>, który ustawi **bieżącego** wiersza wartości były **oryginalnego** wartości i ustawi **RowState** właściwości **Unchanged**. Akceptowanie lub odrzucanie zmiany czyści jakąkolwiek **RowError** informacji i zestawy **HasErrors** właściwości **false**. Akceptowanie lub odrzucanie zmiany mogą wpłynąć na aktualizowanie danych w źródle danych. Aby uzyskać więcej informacji, zobacz [aktualizowanie źródła danych z obiektów DataAdapter](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Jeśli istnieje ograniczeń klucza obcego w **DataTable**, zmiany zaakceptowane lub odrzucone, za pomocą **AcceptChanges** i **RejectChanges** są propagowane do wierszy podrzędnych  **Element DataRow** zgodnie z **ForeignKeyConstraint.AcceptRejectRule**. Aby uzyskać więcej informacji, zobacz [ograniczenia DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Poniższy przykład sprawdza, czy wiersze z błędami, usuwa błędy, jeśli to możliwe i odrzuca wierszy, gdy błąd nie można rozpoznać. Należy pamiętać, że aby rozwiązane błędów, **RowError** jest ustawiany na pusty ciąg, co powoduje **HasErrors** właściwości należy ustawić **false**. Gdy wszystkie wiersze z błędami zostały rozwiązane lub odrzucone, **AcceptChanges** jest wywoływana, aby zaakceptować wszystkie zmiany dla całego **DataTable**.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
