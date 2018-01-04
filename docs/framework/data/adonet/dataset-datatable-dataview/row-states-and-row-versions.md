---
title: Stany wiersza i wersje wiersza
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
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a56cae8b8e300b22a07184cdb69f2c876b101f72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="8e6e2-102">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="8e6e2-102">Row States and Row Versions</span></span>
<span data-ttu-id="8e6e2-103">ADO.NET zarządza wierszy w tabelach przy użyciu stany wiersza i wersje.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="8e6e2-104">Stan wiersz wskazuje stan wiersza; wersje wiersza Obsługa wartościami przechowywanymi w wierszu jako jego modyfikacji, w tym bieżące, oryginalny i wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="8e6e2-105">Na przykład po dokonaniu zmiany z kolumną w wierszu wiersza zostanie mają stan wiersza `Modified`, i wiersza dwie wersje: `Current`, zawierającą bieżące wartości wiersza i `Original`, który zawiera wartości wierszy przed kolumny zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="8e6e2-106">Każdy <xref:System.Data.DataRow> obiekt ma <xref:System.Data.DataRow.RowState%2A> właściwości, które można sprawdzić, aby określić stan bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="8e6e2-107">W poniższej tabeli przedstawiono krótki opis każdego `RowState` wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="8e6e2-108">Wartość RowState</span><span class="sxs-lookup"><span data-stu-id="8e6e2-108">RowState value</span></span>|<span data-ttu-id="8e6e2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8e6e2-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="8e6e2-110">Żadne zmiany nie zostały wprowadzone od czasu ostatniego wywołania `AcceptChanges` lub ponieważ wiersz został utworzony przez `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="8e6e2-111">Wiersz został dodany do tabeli, ale `AcceptChanges` nie została wywołana.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="8e6e2-112">Niektóre elementu wiersz został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="8e6e2-113">Wiersz został usunięty z tabeli, a `AcceptChanges` nie została wywołana.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="8e6e2-114">Wiersza nie jest częścią żadnego `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="8e6e2-115">`RowState` Nowo utworzony wiersza jest ustawiony na wartość `Detached`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="8e6e2-116">Po nowe `DataRow` jest dodawany do `DataRowCollection` przez wywołanie metody `Add` metody, wartość `RowState` właściwość jest ustawiona na `Added`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="8e6e2-117">`Detached`zostanie również ustawiona dla wiersza, który został usunięty z `DataRowCollection` przy użyciu `Remove` metody, lub `Delete` następuje — metoda `AcceptChanges` metody.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="8e6e2-118">Gdy `AcceptChanges` jest wywoływana na <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , lub <xref:System.Data.DataRow>, wszystkie wiersze ze stanem wiersza `Deleted` zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="8e6e2-119">Pozostałe wiersze są podane stan wiersza `Unchanged`i wartościami w `Original` wersja wiersza zostaną zastąpione `Current` wiersz wartości wersji.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="8e6e2-120">Gdy `RejectChanges` jest nazywany wszystkie wiersze ze stanem wiersza `Added` zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="8e6e2-121">Pozostałe wiersze są podane stan wiersza `Unchanged`i wartościami w `Current` wersja wiersza zostaną zastąpione `Original` wiersz wartości wersji.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="8e6e2-122">Można wyświetlić wersji innego wiersza wiersza przez przekazanie <xref:System.Data.DataRowVersion> parametru z odwołania do kolumny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="8e6e2-123">W poniższej tabeli przedstawiono krótki opis każdego `DataRowVersion` wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="8e6e2-124">Wartość DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="8e6e2-124">DataRowVersion value</span></span>|<span data-ttu-id="8e6e2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8e6e2-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="8e6e2-126">Bieżące wartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-126">The current values for the row.</span></span> <span data-ttu-id="8e6e2-127">Ta wersja wiersz nie istnieje dla wiersze z `RowState` z `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="8e6e2-128">Wersja domyślna wiersza dla określonego wiersza.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-128">The default row version for a particular row.</span></span> <span data-ttu-id="8e6e2-129">Wersja domyślna wiersza dla `Added`, `Modified`, lub `Unchanged` wiersz jest `Current`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-129">The default row version for an `Added`, `Modified`, or `Unchanged` row is `Current`.</span></span> <span data-ttu-id="8e6e2-130">Wersja domyślna wiersza dla `Deleted` wiersz jest `Original`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-130">The default row version for a `Deleted` row is `Original`.</span></span> <span data-ttu-id="8e6e2-131">Wersja domyślna wiersza dla `Detached` wiersz jest `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-131">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="8e6e2-132">Oryginalnych wartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-132">The original values for the row.</span></span> <span data-ttu-id="8e6e2-133">Ta wersja wiersz nie istnieje dla wiersze z `RowState` z `Added`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-133">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="8e6e2-134">Proponowane wartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-134">The proposed values for the row.</span></span> <span data-ttu-id="8e6e2-135">Ta wersja wiersz istnieje podczas operacji edycji wiersza lub wiersza, który nie jest częścią `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-135">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="8e6e2-136">Można sprawdzić, czy `DataRow` ma wersję określonego wiersza przez wywołanie metody <xref:System.Data.DataRow.HasVersion%2A> — metoda i przekazywanie `DataRowVersion` jako argument.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-136">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="8e6e2-137">Na przykład `DataRow.HasVersion(DataRowVersion.Original)` zwróci `false` dla nowo dodanych wierszy przed `AcceptChanges` została wywołana.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-137">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="8e6e2-138">Poniższy przykładowy kod przedstawia wartości w usuniętych wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-138">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="8e6e2-139">`Deleted`wiersze nie mają `Current` wersja wiersza, więc należy przekazać `DataRowVersion.Original` podczas uzyskiwania dostępu do wartości w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="8e6e2-139">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e6e2-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e6e2-140">See Also</span></span>  
 [<span data-ttu-id="8e6e2-141">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="8e6e2-141">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="8e6e2-142">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="8e6e2-142">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="8e6e2-143">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="8e6e2-143">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="8e6e2-144">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="8e6e2-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
