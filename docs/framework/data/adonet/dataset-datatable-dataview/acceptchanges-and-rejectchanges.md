---
title: Metoda AcceptChanges i RejectChanges
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
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4c7d86aed61957d15d9c37f494bf80088b164dea
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="28ec8-102">Metoda AcceptChanges i RejectChanges</span><span class="sxs-lookup"><span data-stu-id="28ec8-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="28ec8-103">Po sprawdzeniu dokładności zmiany wprowadzone w danych w <xref:System.Data.DataTable>, możesz zaakceptować zmiany przy użyciu <xref:System.Data.DataRow.AcceptChanges%2A> metody <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataSet>, który ustawi **bieżącego** wiersza wartości były **oryginalnego** wartości i ustawi **RowState** właściwości **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="28ec8-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="28ec8-104">Akceptowanie lub odrzucanie zmiany czyści jakąkolwiek **RowError** informacji i zestawy **HasErrors** właściwości **false**.</span><span class="sxs-lookup"><span data-stu-id="28ec8-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="28ec8-105">Akceptowanie lub odrzucanie zmiany mogą wpłynąć na aktualizowanie danych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="28ec8-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="28ec8-106">Aby uzyskać więcej informacji, zobacz [aktualizowanie źródła danych z obiektów DataAdapter](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="28ec8-106">For more information, see [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="28ec8-107">Jeśli istnieje ograniczeń klucza obcego w **DataTable**, zmiany zaakceptowane lub odrzucone, za pomocą **AcceptChanges** i **RejectChanges** są propagowane do wierszy podrzędnych  **Element DataRow** zgodnie z **ForeignKeyConstraint.AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="28ec8-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="28ec8-108">Aby uzyskać więcej informacji, zobacz [ograniczenia DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="28ec8-108">For more information, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="28ec8-109">Poniższy przykład sprawdza, czy wiersze z błędami, usuwa błędy, jeśli to możliwe i odrzuca wierszy, gdy błąd nie można rozpoznać.</span><span class="sxs-lookup"><span data-stu-id="28ec8-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="28ec8-110">Należy pamiętać, że aby rozwiązane błędów, **RowError** jest ustawiany na pusty ciąg, co powoduje **HasErrors** właściwości należy ustawić **false**.</span><span class="sxs-lookup"><span data-stu-id="28ec8-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="28ec8-111">Gdy wszystkie wiersze z błędami zostały rozwiązane lub odrzucone, **AcceptChanges** jest wywoływana, aby zaakceptować wszystkie zmiany dla całego **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="28ec8-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a><span data-ttu-id="28ec8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28ec8-112">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="28ec8-113">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="28ec8-113">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="28ec8-114">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="28ec8-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
