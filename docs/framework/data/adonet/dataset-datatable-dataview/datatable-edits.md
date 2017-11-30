---
title: Zmiany elementu DataTable
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
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d33bd8900c48222142a46ed2c5bd64412d2eaab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-edits"></a>Zmiany elementu DataTable
Podczas wprowadzania zmian do wartości kolumn <xref:System.Data.DataRow>, zmiany natychmiast są umieszczane w bieżącym stanie wiersza. <xref:System.Data.DataRowState> Następnie ustawiono **zmodyfikowane**, a zmiany są akceptowane lub odrzucone, za pomocą <xref:System.Data.DataRow.AcceptChanges%2A> lub <xref:System.Data.DataRow.RejectChanges%2A> metody **DataRow**. **DataRow** również udostępnia trzy metody, które umożliwia wstrzymanie stanu wiersza podczas edytowania go. Te metody są <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, i <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Po zmodyfikowaniu wartości kolumn **DataRow** bezpośrednio, **DataRow** zarządza przy użyciu wartości w kolumnie **bieżącego**, **domyślne**, i **Oryginalnego** wiersz wersji. Oprócz tych wersji wierszy **BeginEdit**, **EndEdit**, i **metoda CancelEdit** metody Użyj wersji czwartego wiersza: **proponowany**. Aby uzyskać więcej informacji dotyczących wersji wierszy, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 **Proponowany** wersja wiersza istnieje podczas operacji edycji rozpoczynającego wywołując **BeginEdit** i który kończy się za pomocą **EndEdit** lub **metoda CancelEdit,**  , przez wywołanie **AcceptChanges** lub **RejectChanges**.  
  
 Podczas operacji edycji można zastosować logikę weryfikacji do poszczególnych kolumn wyniku obliczenia **ProposedValue** w **ColumnChanged** zdarzenie **DataTable**. **ColumnChanged** przechowuje zdarzenia **DataColumnChangeEventArgs** tym najnowsze odwołanie do kolumny, która jest zmiana i **ProposedValue**. Po przeprowadzeniu oceny proponowanej wartości, możesz go zmodyfikować lub anulować edycję. Po zakończeniu edycji wiersza są przenoszone poza **proponowany** stanu.  
  
 Można potwierdzić zmiany wywołując **EndEdit**, możesz je anulować przez wywołanie metody lub **metoda CancelEdit**. Należy pamiętać, że podczas **EndEdit** potwierdzenie edycji, **DataSet** faktycznie nie akceptuje zmian do **AcceptChanges** jest wywoływana. Należy zauważyć, że jeśli wywołujesz **AcceptChanges** przed zakończył edycję z **EndEdit** lub **metoda CancelEdit**, zakończeniu edycji i **proponowany** wartości wierszy uznane za zaakceptowane dla obu **bieżącego** i **oryginalnego** wiersz wersji. W ten sam sposób wywoływania **RejectChanges** kończy się Edycja i odrzuca **bieżącego** i **proponowany** wiersz wersji. Wywoływanie **EndEdit** lub **metoda CancelEdit** po wywołaniu **AcceptChanges** lub **RejectChanges** nie obowiązuje, ponieważ Edycja zawiera już zakończone.  
  
 W poniższym przykładzie pokazano sposób użycia **BeginEdit** z **EndEdit** i **metoda CancelEdit**. Przykład sprawdza również **ProposedValue** w **ColumnChanged** zdarzeń i decyduje o tym, czy anulować edycję.  
  
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
 [Manipulowanie danymi w DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Obsługa zdarzeń DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
