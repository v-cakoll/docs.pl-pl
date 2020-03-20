---
title: Elementy DataRow i DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 14e7e1ccb051410c351e49afee9f2d6809264833
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151302"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="0139b-102">Elementy DataRow i DataRowView</span><span class="sxs-lookup"><span data-stu-id="0139b-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="0139b-103">A <xref:System.Data.DataView> udostępnia wyliczalną <xref:System.Data.DataRowView> kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="0139b-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="0139b-104">**Obiekty DataRowView** uwidaczniają wartości jako tablice obiektów, które są indeksowane przez nazwę lub odwołanie porządkowe kolumny w tabeli podstawowej.</span><span class="sxs-lookup"><span data-stu-id="0139b-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="0139b-105">Można uzyskać <xref:System.Data.DataRow> dostęp do tego, który jest <xref:System.Data.DataRowView.Row%2A> widoczna przez **DataRowView** przy użyciu właściwości **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="0139b-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="0139b-106">Podczas wyświetlania wartości przy użyciu **DataRowView,** <xref:System.Data.DataView.RowStateFilter%2A> właściwość **DataView** określa, która wersja wiersza podstawowej **DataRow** jest narażony.</span><span class="sxs-lookup"><span data-stu-id="0139b-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="0139b-107">Aby uzyskać informacje dotyczące uzyskiwania dostępu do różnych wersji wierszy przy użyciu **funkcji DataRow,** zobacz [Stany wierszy i Wersje wierszy](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="0139b-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="0139b-108">Poniższy przykład kodu wyświetla wszystkie bieżące i oryginalne wartości w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0139b-108">The following code example displays all the current and original values in a table.</span></span>  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0139b-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0139b-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="0139b-110">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="0139b-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="0139b-111">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0139b-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
