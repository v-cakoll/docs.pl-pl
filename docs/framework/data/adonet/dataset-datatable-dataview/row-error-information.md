---
title: Informacje o błędzie wiersza
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: af000d104a3b0821e69f11c1bce1392f04fe8f5e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203240"
---
# <a name="row-error-information"></a>Informacje o błędzie wiersza
Aby uniknąć konieczności reagowania na błędy wierszy podczas edytowania wartości w <xref:System.Data.DataTable>, można dodać informacje o błędzie do wiersza w celu późniejszego użycia. <xref:System.Data.DataRow> Obiekt<xref:System.Data.DataRow.RowError%2A> zawiera właściwość dla każdego wiersza w tym celu. Dodanie danych do właściwości **RowError** obiektu **DataRow** ustawia <xref:System.Data.DataRow.HasErrors%2A> właściwość elementu **DataRow** na **wartość true**. Jeśli element **DataRow** jest częścią **elementu DataTable**, a **obiekt DataRow. HasErrors** ma **wartość true**, właściwość **DataTable. HasErrors** ma również **wartość true**. Dotyczy to również **zestawu danych** , do którego należy element **DataTable** . Podczas testowania pod kątem błędów można sprawdzić Właściwość **HasErrors** , aby określić, czy informacje o błędzie zostały dodane do dowolnych wierszy. Jeśli **HasErrors** ma **wartość true**, <xref:System.Data.DataTable.GetErrors%2A> można użyć metody **tabeli DataTable** do zwrócenia i sprawdzenia tylko wierszy z błędami, jak pokazano w poniższym przykładzie.  
  
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
- [Operowanie danymi w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
