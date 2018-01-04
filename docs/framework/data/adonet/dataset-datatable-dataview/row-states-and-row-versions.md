---
title: Stany wiersza i wersje wiersza
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
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a56cae8b8e300b22a07184cdb69f2c876b101f72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="row-states-and-row-versions"></a>Stany wiersza i wersje wiersza
ADO.NET zarządza wierszy w tabelach przy użyciu stany wiersza i wersje. Stan wiersz wskazuje stan wiersza; wersje wiersza Obsługa wartościami przechowywanymi w wierszu jako jego modyfikacji, w tym bieżące, oryginalny i wartości domyślnych. Na przykład po dokonaniu zmiany z kolumną w wierszu wiersza zostanie mają stan wiersza `Modified`, i wiersza dwie wersje: `Current`, zawierającą bieżące wartości wiersza i `Original`, który zawiera wartości wierszy przed kolumny zmodyfikowane.  
  
 Każdy <xref:System.Data.DataRow> obiekt ma <xref:System.Data.DataRow.RowState%2A> właściwości, które można sprawdzić, aby określić stan bieżącego wiersza. W poniższej tabeli przedstawiono krótki opis każdego `RowState` wartości wyliczenia.  
  
|Wartość RowState|Opis|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|Żadne zmiany nie zostały wprowadzone od czasu ostatniego wywołania `AcceptChanges` lub ponieważ wiersz został utworzony przez `DataAdapter.Fill`.|  
|<xref:System.Data.DataRowState.Added>|Wiersz został dodany do tabeli, ale `AcceptChanges` nie została wywołana.|  
|<xref:System.Data.DataRowState.Modified>|Niektóre elementu wiersz został zmieniony.|  
|<xref:System.Data.DataRowState.Deleted>|Wiersz został usunięty z tabeli, a `AcceptChanges` nie została wywołana.|  
|<xref:System.Data.DataRowState.Detached>|Wiersza nie jest częścią żadnego `DataRowCollection`. `RowState` Nowo utworzony wiersza jest ustawiony na wartość `Detached`. Po nowe `DataRow` jest dodawany do `DataRowCollection` przez wywołanie metody `Add` metody, wartość `RowState` właściwość jest ustawiona na `Added`.<br /><br /> `Detached`zostanie również ustawiona dla wiersza, który został usunięty z `DataRowCollection` przy użyciu `Remove` metody, lub `Delete` następuje — metoda `AcceptChanges` metody.|  
  
 Gdy `AcceptChanges` jest wywoływana na <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , lub <xref:System.Data.DataRow>, wszystkie wiersze ze stanem wiersza `Deleted` zostaną usunięte. Pozostałe wiersze są podane stan wiersza `Unchanged`i wartościami w `Original` wersja wiersza zostaną zastąpione `Current` wiersz wartości wersji. Gdy `RejectChanges` jest nazywany wszystkie wiersze ze stanem wiersza `Added` zostaną usunięte. Pozostałe wiersze są podane stan wiersza `Unchanged`i wartościami w `Current` wersja wiersza zostaną zastąpione `Original` wiersz wartości wersji.  
  
 Można wyświetlić wersji innego wiersza wiersza przez przekazanie <xref:System.Data.DataRowVersion> parametru z odwołania do kolumny, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 W poniższej tabeli przedstawiono krótki opis każdego `DataRowVersion` wartości wyliczenia.  
  
|Wartość DataRowVersion|Opis|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Bieżące wartości wiersza. Ta wersja wiersz nie istnieje dla wiersze z `RowState` z `Deleted`.|  
|<xref:System.Data.DataRowVersion.Default>|Wersja domyślna wiersza dla określonego wiersza. Wersja domyślna wiersza dla `Added`, `Modified`, lub `Unchanged` wiersz jest `Current`. Wersja domyślna wiersza dla `Deleted` wiersz jest `Original`. Wersja domyślna wiersza dla `Detached` wiersz jest `Proposed`.|  
|<xref:System.Data.DataRowVersion.Original>|Oryginalnych wartości wiersza. Ta wersja wiersz nie istnieje dla wiersze z `RowState` z `Added`.|  
|<xref:System.Data.DataRowVersion.Proposed>|Proponowane wartości wiersza. Ta wersja wiersz istnieje podczas operacji edycji wiersza lub wiersza, który nie jest częścią `DataRowCollection`.|  
  
 Można sprawdzić, czy `DataRow` ma wersję określonego wiersza przez wywołanie metody <xref:System.Data.DataRow.HasVersion%2A> — metoda i przekazywanie `DataRowVersion` jako argument. Na przykład `DataRow.HasVersion(DataRowVersion.Original)` zwróci `false` dla nowo dodanych wierszy przed `AcceptChanges` została wywołana.  
  
 Poniższy przykładowy kod przedstawia wartości w usuniętych wierszy w tabeli. `Deleted`wiersze nie mają `Current` wersja wiersza, więc należy przekazać `DataRowVersion.Original` podczas uzyskiwania dostępu do wartości w kolumnie.  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Elementy DataAdapter i DataReaders](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
