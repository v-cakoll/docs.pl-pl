---
title: Edycje elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 1d9321a1db4f68195fb914f271fb98f904d2f963
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733355"
---
# <a name="datatable-edits"></a>Edycje elementu DataTable
Podczas wprowadzania zmian do wartości kolumn <xref:System.Data.DataRow>, zmiany od razu są umieszczane w bieżącym stanie wiersza. <xref:System.Data.DataRowState> Zostanie następnie ustawiona **zmodyfikowane**, a zmiany są akceptowane lub odrzucone, za pomocą <xref:System.Data.DataRow.AcceptChanges%2A> lub <xref:System.Data.DataRow.RejectChanges%2A> metody **DataRow**. **DataRow** udostępnia trzy metody, które można użyć do zawieszenia stan wiersza podczas edytowania go. Te metody są <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, i <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Po zmodyfikowaniu wartości kolumn **DataRow** bezpośrednio **DataRow** zarządza wartości kolumny za pomocą **bieżącego**, **domyślne**, i **Oryginalnego** wersje wierszy. Oprócz tych wersji wierszy **BeginEdit**, **EndEdit —**, i **CancelEdit** metody za pomocą wersji czwarty wiersz: **proponowane**. Aby uzyskać więcej informacji na temat wersji wierszy, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 **Proponowane** istnieje wersja wierszy podczas operacji edycji, który rozpoczyna się przez wywołanie metody **BeginEdit** i który kończy się za pomocą **EndEdit —** lub **CancelEdit,**  lub przez wywołanie **AcceptChanges** lub **RejectChanges**.  
  
 Podczas operacji edycji można zastosować logikę walidacji do poszczególnych kolumn, oceniając **ProposedValue** w **ColumnChanged** zdarzenia **DataTable**. **ColumnChanged** przechowuje zdarzenia **DataColumnChangeEventArgs** , utrzymywać odwołania do kolumny, która zmienia się i **ProposedValue**. Po przeprowadzeniu oceny proponowana wartość, można go modyfikować lub anulowania edycji. Po zakończeniu edycji, wiersz przenosi się z **proponowane** stanu.  
  
 Możesz sprawdzić zmiany przez wywołanie metody **EndEdit —**, lub można go anulować, wywołując **CancelEdit**. Należy pamiętać, że podczas **EndEdit —** upewnij się, edytowania, **zestawu danych** faktycznie nie akceptuje zmian do momentu **AcceptChanges** jest wywoływana. Należy zauważyć, że jeśli wywołasz **AcceptChanges** przed Zakończono edytowanie za pomocą **EndEdit —** lub **CancelEdit**, edycji zostanie zakończona i **proponowane** wartości wierszy są akceptowane dla obu **bieżącego** i **oryginalnego** wersje wierszy. W ten sam sposób wywoływania **RejectChanges** kończy edycji i odrzuca **bieżącego** i **proponowane** wersje wierszy. Wywoływanie **EndEdit —** lub **CancelEdit** po wywołaniu **AcceptChanges** lub **RejectChanges** nie obowiązuje, ponieważ Edycja zawiera już została zakończona.  
  
 Poniższy przykład pokazuje sposób użycia **BeginEdit** z **EndEdit —** i **CancelEdit**. Przykład sprawdza również **ProposedValue** w **ColumnChanged** zdarzeń i decyduje o tym, czy anulować edycji.  
  
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
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Obsługa zdarzeń elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
