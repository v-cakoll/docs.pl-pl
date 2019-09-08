---
title: Metody AcceptChanges i RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: c537fa808fc6ba4c740e71bfd70fe9cd1f3bd31a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785573"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="a3d80-102">Metody AcceptChanges i RejectChanges</span><span class="sxs-lookup"><span data-stu-id="a3d80-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="a3d80-103">Po sprawdzeniu dokładności zmian wprowadzonych w danych w programie <xref:System.Data.DataTable>można zaakceptować zmiany <xref:System.Data.DataRow.AcceptChanges%2A> przy użyciu metody <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataSet>, która ustawi **bieżące** wartości **wierszy jako Oryginalne** wartości i ustawi właściwość **RowState** na wartość **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="a3d80-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="a3d80-104">Akceptowanie lub odrzucanie zmian czyści wszystkie informacje **RowError** i ustawia właściwość **HasErrors** na **false**.</span><span class="sxs-lookup"><span data-stu-id="a3d80-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="a3d80-105">Akceptowanie lub odrzucanie zmian może również mieć wpływ na aktualizowanie danych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a3d80-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="a3d80-106">Aby uzyskać więcej informacji, zobacz [Aktualizowanie źródeł danych za pomocą kart DataAdapters](../updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="a3d80-106">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="a3d80-107">Jeśli istnieją ograniczenia klucza obcego w **elemencie DataTable**, zmiany zaakceptowane lub odrzucone przy użyciu metody **AcceptChanges** i **RejectChanges** są propagowane do wierszy podrzędnych obiektu **DataRow** zgodnie **z Element ForeignKeyConstraint. AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="a3d80-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="a3d80-108">Aby uzyskać więcej informacji, zobacz temat [ograniczenia DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="a3d80-108">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="a3d80-109">Poniższy przykład sprawdza w poszukiwaniu wierszy z błędami, rozwiązuje błędy, jeśli ma to zastosowanie, i odrzuca wiersze, w których nie można rozpoznać błędu.</span><span class="sxs-lookup"><span data-stu-id="a3d80-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="a3d80-110">Należy pamiętać, że w przypadku rozwiązanych błędów wartość **RowError** jest resetowana do pustego ciągu, powodując, że właściwość **HasErrors** ma wartość **false**.</span><span class="sxs-lookup"><span data-stu-id="a3d80-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="a3d80-111">Gdy wszystkie wiersze z błędami zostały rozwiązane lub odrzucone, Metoda **AcceptChanges** jest wywoływana, aby akceptować wszystkie zmiany dla całej **tabeli DataTable**.</span><span class="sxs-lookup"><span data-stu-id="a3d80-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3d80-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3d80-112">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="a3d80-113">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="a3d80-113">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="a3d80-114">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a3d80-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
