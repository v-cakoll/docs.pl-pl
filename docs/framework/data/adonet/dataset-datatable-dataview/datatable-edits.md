---
title: Edycje elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: a970ebda76f5bb6bdea704dabef2ee305436c613
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205018"
---
# <a name="datatable-edits"></a>Edycje elementu DataTable
Po wprowadzeniu zmian w wartościach kolumn w <xref:System.Data.DataRow>, zmiany są natychmiast umieszczane w bieżącym stanie wiersza. <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A>Następnie jest ustawiona na wartość zmodyfikowano, a zmiany zostaną zaakceptowane lub odrzucone przy użyciu metod lub obiektu DataRow. <xref:System.Data.DataRowState> Ten element **DataRow** zawiera również trzy metody, których można użyć w celu zawieszenia stanu wiersza podczas jego edytowania. Te metody to <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>i <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 W przypadku bezpośredniej modyfikacji wartości kolumn w elemencie **DataRow** element **DataRow** zarządza wartościami kolumn przy użyciu **bieżących**, **domyślnych**i **oryginalnych** wersji wiersza. Oprócz tych wersji wiersza metody **elementu BeginEdit**, **EndEdit**i **CancelEdit** używają czwartej wersji wiersza: **Proponowane**. Aby uzyskać więcej informacji o wersjach wierszy, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).  
  
 **Proponowana** wersja wiersza istnieje podczas operacji edycji rozpoczynającej się od wywołania **elementu BeginEdit** i kończącą się za pomocą **EndEdit** lub **CancelEdit** lub przez wywołanie metody **AcceptChanges** lub **RejectChanges**.  
  
 Podczas operacji edycji można zastosować logikę walidacji do poszczególnych kolumn, oceniając **ProposedValue** w zdarzeniu **ColumnChanged** **elementu DataTable**. Zdarzenie **ColumnChanged** przechowuje **DataColumnChangeEventArgs** , które zachowuje odwołanie do kolumny, która jest zmieniana, oraz do **ProposedValue**. Po obliczeniu proponowanej wartości można ją zmodyfikować lub anulować edycję. Po zakończeniu edycji wiersz jest przenoszony z proponowanego stanu.  
  
 Można potwierdzić zmiany przez wywołanie **EndEdit**lub anulować je przez wywołanie **CancelEdit**. Należy pamiętać, że podczas gdy **EndEdit** potwierdza modyfikacje, **zestaw danych** nie akceptuje zmian do momentu wywołania metody **AcceptChanges** . Należy również pamiętać, że w przypadku wywołania metody **AcceptChanges** przed zakończeniem edycji przy użyciu **EndEdit** lub **CancelEdit**, Edycja zostanie zakończona, a **proponowane** wartości wierszy są akceptowane zarówno dla **bieżącej** , jak i **oryginalnej** wersji wiersza. W ten sam sposób wywołanie **RejectChanges** powoduje zakończenie edycji i odrzucenie **bieżącej** i proponowanej wersji wiersza. Wywołanie **EndEdit** lub **CancelEdit** po wywołaniu metody **AcceptChanges** lub **RejectChanges** nie ma żadnego efektu, ponieważ edytowanie już się zakończyło.  
  
 W poniższym przykładzie pokazano, jak używać **elementu BeginEdit** z **EndEdit** i **CancelEdit**. Przykład sprawdza także **ProposedValue** w zdarzeniu **ColumnChanged** i decyduje o tym, czy anulować edycję.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [Operowanie danymi w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [Obsługa zdarzeń elementu DataTable](handling-datatable-events.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
