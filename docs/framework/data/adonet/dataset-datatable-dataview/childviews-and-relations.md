---
title: ChildViews i relacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d475d356-6abb-4701-8fd1-2906fb93dfba
ms.openlocfilehash: e55e28fd3acdb145e03f0916e3681e95cc7a041a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755386"
---
# <a name="childviews-and-relations"></a><span data-ttu-id="055b5-102">ChildViews i relacji</span><span class="sxs-lookup"><span data-stu-id="055b5-102">ChildViews and Relations</span></span>
<span data-ttu-id="055b5-103">Jeśli istnieje relacja między tabelami w <xref:System.Data.DataSet>, można utworzyć <xref:System.Data.DataView> zawierająca wiersze z tabeli podrzędnych za pomocą <xref:System.Data.DataRowView.CreateChildView%2A> metody <xref:System.Data.DataRowView> dla wierszy w tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="055b5-103">If a relationship exists between tables in a <xref:System.Data.DataSet>, you can create a <xref:System.Data.DataView> containing rows from the related child table by using the <xref:System.Data.DataRowView.CreateChildView%2A> method of the <xref:System.Data.DataRowView> for the rows in the parent table.</span></span> <span data-ttu-id="055b5-104">Na przykład poniższy kod przedstawia **kategorii** i ich pokrewnych **produktów** w kolejności alfabetycznej posortowane według **CategoryName** i **ProductName** .</span><span class="sxs-lookup"><span data-stu-id="055b5-104">For example, the following code displays **Categories** and their related **Products** in alphabetical order sorted by **CategoryName** and **ProductName**.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
Dim prodTable As DataTable = catDS.Tables("Products")  
  
' Create a relation between the Categories and Products tables.  
Dim relation As DataRelation = catDS.Relations.Add("CatProdRel", _  
  catTable.Columns("CategoryID"), _  
  prodTable.Columns("CategoryID"))  
  
' Create DataViews for the Categories and Products tables.  
Dim catView As DataView = New DataView(catTable, "", _  
  "CategoryName", DataViewRowState.CurrentRows)  
Dim prodView As DataView  
  
' Iterate through the Categories table.  
Dim catDRV, prodDRV As DataRowView  
  
For Each catDRV In catView  
  Console.WriteLine(catDRV("CategoryName"))  
  
  ' Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation)  
  prodView.Sort = "ProductName"  
  
  For Each prodDRV In prodView  
    Console.WriteLine(vbTab & prodDRV("ProductName"))  
  Next  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
DataTable prodTable = catDS.Tables["Products"];  
  
// Create a relation between the Categories and Products tables.  
DataRelation relation = catDS.Relations.Add("CatProdRel",   
  catTable.Columns["CategoryID"],  
                                                            prodTable.Columns["CategoryID"]);  
  
// Create DataViews for the Categories and Products tables.  
DataView catView = new DataView(catTable, "", "CategoryName",   
  DataViewRowState.CurrentRows);  
DataView prodView;  
  
// Iterate through the Categories table.  
foreach (DataRowView catDRV in catView)  
{  
  Console.WriteLine(catDRV["CategoryName"]);  
  
  // Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation);  
  prodView.Sort = "ProductName";  
  
  foreach (DataRowView prodDRV in prodView)  
    Console.WriteLine("\t" + prodDRV["ProductName"]);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="055b5-105">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="055b5-105">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="055b5-106">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="055b5-106">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="055b5-107">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="055b5-107">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
