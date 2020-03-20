---
title: Edycje elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151263"
---
# <a name="datatable-edits"></a>Edycje elementu DataTable
Po wprowadzeniu zmian w wartościach kolumn w <xref:System.Data.DataRow>, zmiany są natychmiast umieszczane w bieżącym stanie wiersza. Następnie <xref:System.Data.DataRowState> ustawiono na **Zmodyfikowane,** a zmiany są akceptowane <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> lub odrzucane przy użyciu lub metod **DataRow**. **DataRow** zawiera również trzy metody, których można użyć do zawieszenia stanu wiersza podczas edytowania go. Metody te <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A>są <xref:System.Data.DataRow.CancelEdit%2A>, i .  
  
 Podczas modyfikowania wartości kolumn bezpośrednio w **datarowy** **datarowy, DataRow** zarządza wartościami kolumn przy użyciu **bieżących,** **domyślnych**i **oryginalnych** wersji wierszy. Oprócz tych wersji wiersza, **BeginEdit**, **EndEdit**i **CancelEdit** metody użyć wersji czwartego **wiersza: Proponowane**. Aby uzyskać więcej informacji na temat wersji wierszy, zobacz [Stany wierszy i Wersje wierszy](row-states-and-row-versions.md).  
  
 **Proponowana** wersja wiersza istnieje podczas operacji edycji, która rozpoczyna się od wywołania **BeginEdit** i która kończy się za pomocą **EndEdit** lub **CancelEdit** lub wywołując **AcceptChanges** lub **RejectChanges**.  
  
 Podczas operacji edycji można zastosować logikę sprawdzania poprawności do poszczególnych kolumn, oceniając **proposedValue** w **columnchanged** zdarzenia **DataTable**. **Zdarzenie ColumnChanged** zawiera **dane DataColumnChangeEventArgs,** które zachowują odwołanie do kolumny, która się zmienia, oraz do **wartości ProposedValue**. Po dokonaniu oceny proponowanej wartości można ją zmodyfikować lub anulować. Po zakończeniu edycji wiersz zostanie przeniesiony ze stanu **Proponowane.**  
  
 Możesz potwierdzić zmiany, dzwoniąc do **EndEdit**lub możesz je anulować, dzwoniąc do **CancelEdit**. Należy zauważyć, że podczas **endedit** potwierdzić zmiany, **DataSet** faktycznie nie akceptuje zmian, dopóki **AcceptChanges** jest wywoływana. Należy również zauważyć, że jeśli wywołasz **AcceptChanges** przed zakończeniem edycji z **EndEdit** lub **CancelEdit**, edycja zostanie zakończona, a wartości **wiersza Proponowane** zostaną zaakceptowane zarówno dla wersji **wiersza Bieżący,** jak i **Oryginalny.** W ten sam sposób wywołanie **RejectChanges** kończy edycję i odrzuca **bieżące** i **proponowane** wersje wierszy. Wywołanie **EndEdit** lub **CancelEdit** po wywołaniu **AcceptChanges** lub **RejectChanges** nie ma wpływu, ponieważ edycja została już zakończona.  
  
 W poniższym przykładzie pokazano, jak używać **BeginEdit** z **EndEdit** i **CancelEdit**. W przykładzie sprawdza również **ProposedValue** w **ColumnChanged** zdarzenia i decyduje, czy anulować edycję.  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [Operowanie na danych w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [Obsługa zdarzeń elementu DataTable](handling-datatable-events.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
