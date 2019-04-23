---
title: Informacje o błędzie wiersza
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 89889c5543e6518046bb59b59646ecba715f5e03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152727"
---
# <a name="row-error-information"></a>Informacje o błędzie wiersza
Aby uniknąć konieczności reagować na błędy wierszy podczas edycji wartości <xref:System.Data.DataTable>, można dodać informacje o błędzie do wiersza w celu późniejszego użycia. <xref:System.Data.DataRow> Obiektu <xref:System.Data.DataRow.RowError%2A> właściwość w każdym wierszu, w tym celu. Dodawanie danych do **RowError** właściwość **DataRow** ustawia <xref:System.Data.DataRow.HasErrors%2A> właściwość **DataRow** do **true**. Jeśli **DataRow** jest częścią **DataTable**, i **DataRow.HasErrors** jest **true**, **DataTable.HasErrors** właściwość jest również **true**. Dotyczy to także do **DataSet** do której **DataTable** należy. Testowanie pod kątem błędów, można sprawdzić **HasErrors** właściwości w celu określenia, jeśli dodano informacje o błędzie do wszystkich wierszy. Jeśli **HasErrors** jest **true**, możesz użyć <xref:System.Data.DataTable.GetErrors%2A> metody **DataTable** powrócić do zbadania tylko wiersze z błędami, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
