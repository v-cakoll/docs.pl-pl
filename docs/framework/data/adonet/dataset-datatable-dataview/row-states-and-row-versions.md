---
title: Stany wiersza i wersje wiersza
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 629e8b0bea1cd5c1dd80409acd7c03e0e033b5bc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195010"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="43c53-102">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="43c53-102">Row States and Row Versions</span></span>
<span data-ttu-id="43c53-103">ADO.NET zarządza wierszy w tabelach przy użyciu stany wiersza i wersje.</span><span class="sxs-lookup"><span data-stu-id="43c53-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="43c53-104">Stan wiersz wskazuje stan wiersza; wersje wiersza Obsługa wartości przechowywane w wierszu, zgodnie z jego modyfikacji, tym bieżące, oryginalne i wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="43c53-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="43c53-105">Na przykład, po dokonaniu modyfikacji z kolumną w wierszu wiersza będzie mają stan wiersza `Modified`, i dwie wersje wierszy: `Current`, zawierającą bieżące wartości wiersza i `Original`, zawierającą wartości wiersza przed kolumny zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="43c53-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="43c53-106">Każdy <xref:System.Data.DataRow> obiekt ma <xref:System.Data.DataRow.RowState%2A> właściwości, które można sprawdzić, aby ustalić stan bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="43c53-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="43c53-107">W poniższej tabeli przedstawiono krótki opis każdego `RowState` wartość wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="43c53-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="43c53-108">Wartość RowState</span><span class="sxs-lookup"><span data-stu-id="43c53-108">RowState value</span></span>|<span data-ttu-id="43c53-109">Opis</span><span class="sxs-lookup"><span data-stu-id="43c53-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="43c53-110">Nie zostały zmienione od czasu ostatniego wywołania do `AcceptChanges` lub ponieważ wiersz został utworzony przez `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="43c53-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="43c53-111">Wiersz został dodany do tabeli, ale `AcceptChanges` nie została wywołana.</span><span class="sxs-lookup"><span data-stu-id="43c53-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="43c53-112">Pewien element wiersz został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="43c53-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="43c53-113">Wiersz został usunięty z tabeli, a `AcceptChanges` nie została wywołana.</span><span class="sxs-lookup"><span data-stu-id="43c53-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="43c53-114">Wiersz nie jest częścią żadnego `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="43c53-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="43c53-115">`RowState` Nowo utworzonego wiersza jest równa `Detached`.</span><span class="sxs-lookup"><span data-stu-id="43c53-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="43c53-116">Po nowym `DataRow` jest dodawany do `DataRowCollection` przez wywołanie metody `Add` metody, wartość `RowState` właściwość jest ustawiona na `Added`.</span><span class="sxs-lookup"><span data-stu-id="43c53-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="43c53-117">`Detached` jest również ustawiona dla wiersza, który został usunięty z `DataRowCollection` przy użyciu `Remove` metody lub `Delete` metody następuje `AcceptChanges` metody.</span><span class="sxs-lookup"><span data-stu-id="43c53-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="43c53-118">Gdy `AcceptChanges` jest wywoływana w <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , lub <xref:System.Data.DataRow>, wszystkie wiersze ze stanem wiersz `Deleted` są usuwane.</span><span class="sxs-lookup"><span data-stu-id="43c53-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="43c53-119">Pozostałe wiersze są podane stan wiersza `Unchanged`i wartości w `Original` wiersza wersji zostaną zastąpione `Current` wiersz wartości wersji.</span><span class="sxs-lookup"><span data-stu-id="43c53-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="43c53-120">Gdy `RejectChanges` jest wywoływana, wszystkie wiersze ze stanem wiersz `Added` są usuwane.</span><span class="sxs-lookup"><span data-stu-id="43c53-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="43c53-121">Pozostałe wiersze są podane stan wiersza `Unchanged`i wartości w `Current` wiersza wersji zostaną zastąpione `Original` wiersz wartości wersji.</span><span class="sxs-lookup"><span data-stu-id="43c53-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="43c53-122">Możesz wyświetlić wiersz różne wersje wiersza, przekazując <xref:System.Data.DataRowVersion> parametru odwołania do kolumny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="43c53-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="43c53-123">W poniższej tabeli przedstawiono krótki opis każdego `DataRowVersion` wartość wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="43c53-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="43c53-124">Wartość DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="43c53-124">DataRowVersion value</span></span>|<span data-ttu-id="43c53-125">Opis</span><span class="sxs-lookup"><span data-stu-id="43c53-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="43c53-126">Wartości bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="43c53-126">The current values for the row.</span></span> <span data-ttu-id="43c53-127">Ta wersja wiersz nie istnieje dla wierszy z `RowState` z `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="43c53-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="43c53-128">Domyślna wersja wiersza dla konkretnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="43c53-128">The default row version for a particular row.</span></span> <span data-ttu-id="43c53-129">Domyślna wersja wiersza dla `Added`, `Modified`, lub `Deleted` wiersz jest `Current`.</span><span class="sxs-lookup"><span data-stu-id="43c53-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="43c53-130">Domyślna wersja wiersza dla `Detached` wiersz jest `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="43c53-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="43c53-131">Oryginalnych wartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="43c53-131">The original values for the row.</span></span> <span data-ttu-id="43c53-132">Ta wersja wiersz nie istnieje dla wierszy z `RowState` z `Added`.</span><span class="sxs-lookup"><span data-stu-id="43c53-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="43c53-133">Proponowana wartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="43c53-133">The proposed values for the row.</span></span> <span data-ttu-id="43c53-134">Ta wersja wiersz istnieje podczas operacji Edytuj wiersz lub dla wiersza, który nie jest częścią `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="43c53-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="43c53-135">Można sprawdzić, czy `DataRow` ma wersję określonego wiersza przez wywołanie metody <xref:System.Data.DataRow.HasVersion%2A> metody i przekazywanie `DataRowVersion` jako argument.</span><span class="sxs-lookup"><span data-stu-id="43c53-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="43c53-136">Na przykład `DataRow.HasVersion(DataRowVersion.Original)` zwróci `false` dla nowo dodanych wierszy przed `AcceptChanges` została wywołana.</span><span class="sxs-lookup"><span data-stu-id="43c53-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="43c53-137">Poniższy przykład kodu wyświetla wartości w usunięte wiersze w tabeli.</span><span class="sxs-lookup"><span data-stu-id="43c53-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="43c53-138">`Deleted` wiersze nie mają `Current` wersji wierszy, więc należy przekazać `DataRowVersion.Original` podczas uzyskiwania dostępu do wartości w kolumnach.</span><span class="sxs-lookup"><span data-stu-id="43c53-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43c53-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43c53-139">See Also</span></span>  
 [<span data-ttu-id="43c53-140">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="43c53-140">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="43c53-141">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="43c53-141">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="43c53-142">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="43c53-142">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="43c53-143">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="43c53-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
