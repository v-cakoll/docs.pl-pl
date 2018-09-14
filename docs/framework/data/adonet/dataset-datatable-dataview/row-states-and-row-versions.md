---
title: Stany wiersza i wersje wiersza
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 629e8b0bea1cd5c1dd80409acd7c03e0e033b5bc
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560644"
---
# <a name="row-states-and-row-versions"></a>Stany wiersza i wersje wiersza
ADO.NET zarządza wierszy w tabelach przy użyciu stany wiersza i wersje. Stan wiersz wskazuje stan wiersza; wersje wiersza Obsługa wartości przechowywane w wierszu, zgodnie z jego modyfikacji, tym bieżące, oryginalne i wartości domyślne. Na przykład, po dokonaniu modyfikacji z kolumną w wierszu wiersza będzie mają stan wiersza `Modified`, i dwie wersje wierszy: `Current`, zawierającą bieżące wartości wiersza i `Original`, zawierającą wartości wiersza przed kolumny zmodyfikowane.  
  
 Każdy <xref:System.Data.DataRow> obiekt ma <xref:System.Data.DataRow.RowState%2A> właściwości, które można sprawdzić, aby ustalić stan bieżącego wiersza. W poniższej tabeli przedstawiono krótki opis każdego `RowState` wartość wyliczenia.  
  
|Wartość RowState|Opis|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|Nie zostały zmienione od czasu ostatniego wywołania do `AcceptChanges` lub ponieważ wiersz został utworzony przez `DataAdapter.Fill`.|  
|<xref:System.Data.DataRowState.Added>|Wiersz został dodany do tabeli, ale `AcceptChanges` nie została wywołana.|  
|<xref:System.Data.DataRowState.Modified>|Pewien element wiersz został zmieniony.|  
|<xref:System.Data.DataRowState.Deleted>|Wiersz został usunięty z tabeli, a `AcceptChanges` nie została wywołana.|  
|<xref:System.Data.DataRowState.Detached>|Wiersz nie jest częścią żadnego `DataRowCollection`. `RowState` Nowo utworzonego wiersza jest równa `Detached`. Po nowym `DataRow` jest dodawany do `DataRowCollection` przez wywołanie metody `Add` metody, wartość `RowState` właściwość jest ustawiona na `Added`.<br /><br /> `Detached` jest również ustawiona dla wiersza, który został usunięty z `DataRowCollection` przy użyciu `Remove` metody lub `Delete` metody następuje `AcceptChanges` metody.|  
  
 Gdy `AcceptChanges` jest wywoływana w <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , lub <xref:System.Data.DataRow>, wszystkie wiersze ze stanem wiersz `Deleted` są usuwane. Pozostałe wiersze są podane stan wiersza `Unchanged`i wartości w `Original` wiersza wersji zostaną zastąpione `Current` wiersz wartości wersji. Gdy `RejectChanges` jest wywoływana, wszystkie wiersze ze stanem wiersz `Added` są usuwane. Pozostałe wiersze są podane stan wiersza `Unchanged`i wartości w `Current` wiersza wersji zostaną zastąpione `Original` wiersz wartości wersji.  
  
 Możesz wyświetlić wiersz różne wersje wiersza, przekazując <xref:System.Data.DataRowVersion> parametru odwołania do kolumny, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 W poniższej tabeli przedstawiono krótki opis każdego `DataRowVersion` wartość wyliczenia.  
  
|Wartość DataRowVersion|Opis|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Wartości bieżącego wiersza. Ta wersja wiersz nie istnieje dla wierszy z `RowState` z `Deleted`.|  
|<xref:System.Data.DataRowVersion.Default>|Domyślna wersja wiersza dla konkretnego wiersza. Domyślna wersja wiersza dla `Added`, `Modified`, lub `Deleted` wiersz jest `Current`. Domyślna wersja wiersza dla `Detached` wiersz jest `Proposed`.|  
|<xref:System.Data.DataRowVersion.Original>|Oryginalnych wartości wiersza. Ta wersja wiersz nie istnieje dla wierszy z `RowState` z `Added`.|  
|<xref:System.Data.DataRowVersion.Proposed>|Proponowana wartości wiersza. Ta wersja wiersz istnieje podczas operacji Edytuj wiersz lub dla wiersza, który nie jest częścią `DataRowCollection`.|  
  
 Można sprawdzić, czy `DataRow` ma wersję określonego wiersza przez wywołanie metody <xref:System.Data.DataRow.HasVersion%2A> metody i przekazywanie `DataRowVersion` jako argument. Na przykład `DataRow.HasVersion(DataRowVersion.Original)` zwróci `false` dla nowo dodanych wierszy przed `AcceptChanges` została wywołana.  
  
 Poniższy przykład kodu wyświetla wartości w usunięte wiersze w tabeli. `Deleted` wiersze nie mają `Current` wersji wierszy, więc należy przekazać `DataRowVersion.Original` podczas uzyskiwania dostępu do wartości w kolumnach.  
  
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
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
