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
# <a name="datarows-and-datarowviews"></a>Elementy DataRow i DataRowView
A <xref:System.Data.DataView> udostępnia wyliczalną <xref:System.Data.DataRowView> kolekcję obiektów. **Obiekty DataRowView** uwidaczniają wartości jako tablice obiektów, które są indeksowane przez nazwę lub odwołanie porządkowe kolumny w tabeli podstawowej. Można uzyskać <xref:System.Data.DataRow> dostęp do tego, który jest <xref:System.Data.DataRowView.Row%2A> widoczna przez **DataRowView** przy użyciu właściwości **DataRowView**.  
  
 Podczas wyświetlania wartości przy użyciu **DataRowView,** <xref:System.Data.DataView.RowStateFilter%2A> właściwość **DataView** określa, która wersja wiersza podstawowej **DataRow** jest narażony. Aby uzyskać informacje dotyczące uzyskiwania dostępu do różnych wersji wierszy przy użyciu **funkcji DataRow,** zobacz [Stany wierszy i Wersje wierszy](row-states-and-row-versions.md).  
  
 Poniższy przykład kodu wyświetla wszystkie bieżące i oryginalne wartości w tabeli.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [Elementy DataView](dataviews.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
