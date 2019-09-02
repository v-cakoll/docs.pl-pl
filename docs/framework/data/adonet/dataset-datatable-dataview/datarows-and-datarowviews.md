---
title: Elementy DataRow i DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 8a98dc44eda9ebda09235193c58bd831fc52d04d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205093"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="1748e-102">Elementy DataRow i DataRowView</span><span class="sxs-lookup"><span data-stu-id="1748e-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="1748e-103">A <xref:System.Data.DataView> uwidacznia wyliczalną <xref:System.Data.DataRowView> kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="1748e-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="1748e-104">Obiekty **DataRowView** uwidaczniają wartości jako tablice obiektów, które są indeksowane przez nazwę lub odwołanie porządkowe kolumny w tabeli źródłowej.</span><span class="sxs-lookup"><span data-stu-id="1748e-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="1748e-105">Możesz uzyskać dostęp do <xref:System.Data.DataRow> programu, który jest udostępniany przez **DataRowView** , <xref:System.Data.DataRowView.Row%2A> przy użyciu właściwości **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="1748e-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="1748e-106">Podczas wyświetlania wartości przy użyciu **DataRowView** <xref:System.Data.DataView.RowStateFilter%2A> Właściwość **widoku** danych określa, która wersja wiersza podstawowego elementu **DataRow** jest uwidoczniona.</span><span class="sxs-lookup"><span data-stu-id="1748e-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="1748e-107">Aby uzyskać informacje o uzyskiwaniu dostępu do różnych wersji wierszy przy użyciu elementu **DataRow**, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="1748e-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="1748e-108">Poniższy przykład kodu wyświetla wszystkie bieżące i oryginalne wartości w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1748e-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1748e-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1748e-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="1748e-110">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="1748e-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="1748e-111">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1748e-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
