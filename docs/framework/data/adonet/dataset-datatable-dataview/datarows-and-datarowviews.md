---
title: "Elementów DataRows i DataRowViews"
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
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ac8209432cd975539983226cfba51f229d696bd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="63b6e-102">Elementów DataRows i DataRowViews</span><span class="sxs-lookup"><span data-stu-id="63b6e-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="63b6e-103">A <xref:System.Data.DataView> udostępnia kolekcję wyliczalny <xref:System.Data.DataRowView> obiektów.</span><span class="sxs-lookup"><span data-stu-id="63b6e-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="63b6e-104">**DataRowView** obiektów uwidocznić wartości jako tablice obiektów, które są indeksowane według nazwy lub odwołania liczby porządkowej kolumny w tabeli podstawowej.</span><span class="sxs-lookup"><span data-stu-id="63b6e-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="63b6e-105">Dostęp można uzyskać <xref:System.Data.DataRow> widoczne przy **DataRowView** za pomocą <xref:System.Data.DataRowView.Row%2A> właściwość **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="63b6e-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="63b6e-106">Podczas wyświetlania wartości przy użyciu **DataRowView**, <xref:System.Data.DataView.RowStateFilter%2A> właściwość **DataView** Określa wersję wiersza podstawowych **DataRow** jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="63b6e-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="63b6e-107">Uzyskać informacji na temat uzyskiwania dostępu do wersji innego wiersza przy użyciu **DataRow**, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="63b6e-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="63b6e-108">Poniższy przykładowy kod przedstawia wszystkich bieżących i oryginalnych wartości w tabeli.</span><span class="sxs-lookup"><span data-stu-id="63b6e-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63b6e-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63b6e-109">See Also</span></span>  
 <xref:System.Data.DataRowVersion>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="63b6e-110">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="63b6e-110">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="63b6e-111">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="63b6e-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
