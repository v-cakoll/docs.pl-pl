---
title: "Informacje o błędzie wiersza"
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
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3e8b2e486f33cbe3851b0d24911f5976a1a4b3c6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="row-error-information"></a><span data-ttu-id="c0146-102">Informacje o błędzie wiersza</span><span class="sxs-lookup"><span data-stu-id="c0146-102">Row Error Information</span></span>
<span data-ttu-id="c0146-103">Aby uniknąć konieczności odpowiadanie na wiersz błędy podczas edycji wartości <xref:System.Data.DataTable>, można dodać informacje o błędzie do wiersza do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="c0146-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="c0146-104"><xref:System.Data.DataRow> Zawiera obiekt <xref:System.Data.DataRow.RowError%2A> właściwości w każdym wierszu do tego celu.</span><span class="sxs-lookup"><span data-stu-id="c0146-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="c0146-105">Dodawanie danych do **RowError** właściwość **DataRow** ustawia <xref:System.Data.DataRow.HasErrors%2A> właściwość **DataRow** do **true**.</span><span class="sxs-lookup"><span data-stu-id="c0146-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="c0146-106">Jeśli **DataRow** jest częścią **DataTable**, i **DataRow.HasErrors** jest **true**, **DataTable.HasErrors** właściwość jest również **true**.</span><span class="sxs-lookup"><span data-stu-id="c0146-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="c0146-107">Dotyczy to również do **DataSet** do której **DataTable** należy.</span><span class="sxs-lookup"><span data-stu-id="c0146-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="c0146-108">Testowanie pod kątem błędów, można sprawdzić **HasErrors** właściwości w celu określenia, czy informacje o błędzie został dodany do wszystkich wierszy.</span><span class="sxs-lookup"><span data-stu-id="c0146-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="c0146-109">Jeśli **HasErrors** jest **true**, można użyć <xref:System.Data.DataTable.GetErrors%2A> metody **DataTable** aby wrócić i sprawdź, czy tylko wiersze z błędami, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c0146-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0146-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0146-110">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="c0146-111">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="c0146-111">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="c0146-112">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="c0146-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
