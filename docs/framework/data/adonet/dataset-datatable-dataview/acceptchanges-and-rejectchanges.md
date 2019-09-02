---
title: Metody AcceptChanges i RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: a8589b157bc2579a03d856b73802abc9a4b42855
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204079"
---
# <a name="acceptchanges-and-rejectchanges"></a>Metody AcceptChanges i RejectChanges
Po sprawdzeniu dokładności zmian wprowadzonych w danych w programie <xref:System.Data.DataTable>można zaakceptować zmiany <xref:System.Data.DataRow.AcceptChanges%2A> przy użyciu metody <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataSet>, która ustawi **bieżące** wartości **wierszy jako Oryginalne** wartości i ustawi właściwość **RowState** na wartość Unchanged. Akceptowanie lub odrzucanie zmian czyści wszystkie informacje **RowError** i ustawia właściwość **HasErrors** na **false**. Akceptowanie lub odrzucanie zmian może również mieć wpływ na aktualizowanie danych w źródle danych. Aby uzyskać więcej informacji, zobacz [Aktualizowanie źródeł danych za pomocą kart](../updating-data-sources-with-dataadapters.md)DataAdapters.  
  
 Jeśli istnieją ograniczenia klucza obcego w **elemencie DataTable**, zmiany zaakceptowane lub odrzucone przy użyciu metody **AcceptChanges** i **RejectChanges** są propagowane do wierszy podrzędnych obiektu **DataRow** zgodnie **z Element ForeignKeyConstraint. AcceptRejectRule**. Aby uzyskać więcej informacji, zobacz temat [ograniczenia DataTable](datatable-constraints.md).  
  
 Poniższy przykład sprawdza w poszukiwaniu wierszy z błędami, rozwiązuje błędy, jeśli ma to zastosowanie, i odrzuca wiersze, w których nie można rozpoznać błędu. Należy pamiętać, że w przypadku rozwiązanych błędów wartość **RowError** jest resetowana do pustego ciągu, powodując, że właściwość **HasErrors** ma wartość **false**. Gdy wszystkie wiersze z błędami zostały rozwiązane lub odrzucone, Metoda **AcceptChanges** jest wywoływana, aby akceptować wszystkie zmiany dla całej **tabeli DataTable**.  
  
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
- [Operowanie danymi w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
