---
title: Metody AcceptChanges i RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: 30b2c303b1823430c480f0706500f8f7e7053c4c
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873141"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="afa80-102">Metody AcceptChanges i RejectChanges</span><span class="sxs-lookup"><span data-stu-id="afa80-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="afa80-103">Po sprawdzeniu dokładności zmian wprowadzonych w danych w <xref:System.Data.DataTable>, możesz zaakceptować zmiany, używając <xref:System.Data.DataRow.AcceptChanges%2A> metody <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataSet>, który ustawi **bieżącego** wiersza wartości, które mają być **oryginalnego** wartości i ustawi **RowState** właściwości **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="afa80-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="afa80-104">Akceptowanie lub odrzucanie zmian czyści jakąkolwiek **RowError** informacji i zestawy **HasErrors** właściwości **false**.</span><span class="sxs-lookup"><span data-stu-id="afa80-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="afa80-105">Akceptowanie lub odrzucanie zmian może również wpływać na aktualizowanie danych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="afa80-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="afa80-106">Aby uzyskać więcej informacji, zobacz [aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="afa80-106">For more information, see [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="afa80-107">Jeśli istnieją ograniczenia klucza obcego, na **DataTable**, zmiany zaakceptowane lub odrzucone, za pomocą **AcceptChanges** i **RejectChanges** są propagowane do podrzędnych wiersze  **DataRow** zgodnie z opisem w **ForeignKeyConstraint.AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="afa80-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="afa80-108">Aby uzyskać więcej informacji, zobacz [ograniczenia elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="afa80-108">For more information, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="afa80-109">Poniższy przykład sprawdza wiersze z błędami, rozwiązuje błędy, jeśli ma to zastosowanie i odrzuca wiersze, w którym ten błąd nie można rozpoznać.</span><span class="sxs-lookup"><span data-stu-id="afa80-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="afa80-110">Należy pamiętać, że dla rozwiązane błędy, **RowError** jest ustawiany na pusty ciąg, powodując **HasErrors** właściwość należy ustawić **false**.</span><span class="sxs-lookup"><span data-stu-id="afa80-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="afa80-111">Gdy wszystkie wiersze z błędami zostały rozwiązane lub odrzucone, **AcceptChanges** jest wywoływana, aby zaakceptować wszystkie zmiany dla całego **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="afa80-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="afa80-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afa80-112">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="afa80-113">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="afa80-113">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="afa80-114">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="afa80-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
