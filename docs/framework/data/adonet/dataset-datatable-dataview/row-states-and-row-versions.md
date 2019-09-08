---
title: Stany wiersza i wersje wiersza
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 70596d6acb62fa01092e5e55dd3b6c84eb162b5d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784331"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="23aee-102">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="23aee-102">Row States and Row Versions</span></span>
<span data-ttu-id="23aee-103">ADO.NET zarządza wierszami w tabelach przy użyciu stanów i wersji wiersza.</span><span class="sxs-lookup"><span data-stu-id="23aee-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="23aee-104">Stan wiersza wskazuje stan wiersza; wersje wierszy obsługują wartości przechowywane w wierszu w miarę ich modyfikacji, w tym bieżące, oryginalne i domyślne wartości.</span><span class="sxs-lookup"><span data-stu-id="23aee-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="23aee-105">Na przykład po wprowadzeniu modyfikacji do kolumny w wierszu wiersz będzie miał stan `Modified`wiersza i dwie wersje wierszy: `Current`, które zawierają wartości bieżącego wiersza, i `Original`, które zawierają wartości wierszy przed kolumną Modyfikacja.</span><span class="sxs-lookup"><span data-stu-id="23aee-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="23aee-106">Każdy <xref:System.Data.DataRow> obiekt<xref:System.Data.DataRow.RowState%2A> ma właściwość, którą można sprawdzić w celu określenia bieżącego stanu wiersza.</span><span class="sxs-lookup"><span data-stu-id="23aee-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="23aee-107">W poniższej tabeli przedstawiono krótki opis każdej `RowState` wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="23aee-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="23aee-108">RowState wartość</span><span class="sxs-lookup"><span data-stu-id="23aee-108">RowState value</span></span>|<span data-ttu-id="23aee-109">Opis</span><span class="sxs-lookup"><span data-stu-id="23aee-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="23aee-110">Od momentu ostatniego wywołania `AcceptChanges` lub od momentu `DataAdapter.Fill`utworzenia wiersza nie wprowadzono żadnych zmian.</span><span class="sxs-lookup"><span data-stu-id="23aee-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="23aee-111">Wiersz został dodany do tabeli, ale `AcceptChanges` nie został wywołany.</span><span class="sxs-lookup"><span data-stu-id="23aee-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="23aee-112">Jakiś element wiersza został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="23aee-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="23aee-113">Wiersz został usunięty z tabeli i `AcceptChanges` nie został wywołany.</span><span class="sxs-lookup"><span data-stu-id="23aee-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="23aee-114">Wiersz nie jest częścią żadnego `DataRowCollection`elementu.</span><span class="sxs-lookup"><span data-stu-id="23aee-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="23aee-115">Nowo utworzony wiersz jest ustawiony na `Detached`. `RowState`</span><span class="sxs-lookup"><span data-stu-id="23aee-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="23aee-116">Po dodaniu `DataRow` nowego `DataRowCollection` do obiektu przez wywołanie `Add` metody, wartość `RowState` właściwości jest ustawiona na `Added`.</span><span class="sxs-lookup"><span data-stu-id="23aee-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="23aee-117">`Detached`jest również ustawiony dla wiersza, `DataRowCollection` który został usunięty z `Remove` `Delete` metody lub przez metodę, a następnie `AcceptChanges` metodę.</span><span class="sxs-lookup"><span data-stu-id="23aee-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="23aee-118">Gdy `AcceptChanges` jest wywoływana <xref:System.Data.DataSet>w, <xref:System.Data.DataTable> , lub <xref:System.Data.DataRow>, wszystkie wiersze ze stanem `Deleted` wiersza są usuwane.</span><span class="sxs-lookup"><span data-stu-id="23aee-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="23aee-119">W pozostałych wierszach jest przyznany stan `Unchanged`wiersza, a wartości `Original` w wierszu wersji `Current` są zastępowane wartościami wersji wiersza.</span><span class="sxs-lookup"><span data-stu-id="23aee-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="23aee-120">Gdy `RejectChanges` jest wywoływana, wszystkie wiersze ze `Added` stanem wiersza są usuwane.</span><span class="sxs-lookup"><span data-stu-id="23aee-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="23aee-121">W pozostałych wierszach jest przyznany stan `Unchanged`wiersza, a wartości `Current` w wierszu wersji `Original` są zastępowane wartościami wersji wiersza.</span><span class="sxs-lookup"><span data-stu-id="23aee-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="23aee-122">Możesz wyświetlić różne wersje wierszy wiersza, przekazując <xref:System.Data.DataRowVersion> parametr z odwołaniem do kolumny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="23aee-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="23aee-123">W poniższej tabeli przedstawiono krótki opis każdej `DataRowVersion` wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="23aee-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="23aee-124">DataRowVersion wartość</span><span class="sxs-lookup"><span data-stu-id="23aee-124">DataRowVersion value</span></span>|<span data-ttu-id="23aee-125">Opis</span><span class="sxs-lookup"><span data-stu-id="23aee-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="23aee-126">Bieżące wartości dla wiersza.</span><span class="sxs-lookup"><span data-stu-id="23aee-126">The current values for the row.</span></span> <span data-ttu-id="23aee-127">Ta wersja wiersza nie istnieje dla wierszy z `RowState`. `Deleted`</span><span class="sxs-lookup"><span data-stu-id="23aee-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="23aee-128">Domyślna wersja wiersza dla konkretnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="23aee-128">The default row version for a particular row.</span></span> <span data-ttu-id="23aee-129">Domyślna wersja wiersza dla `Added`elementu, `Modified`, lub `Deleted` jest `Current`.</span><span class="sxs-lookup"><span data-stu-id="23aee-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="23aee-130">Domyślna wersja wiersza dla `Detached` wiersza to. `Proposed`</span><span class="sxs-lookup"><span data-stu-id="23aee-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="23aee-131">Oryginalne wartości dla wiersza.</span><span class="sxs-lookup"><span data-stu-id="23aee-131">The original values for the row.</span></span> <span data-ttu-id="23aee-132">Ta wersja wiersza nie istnieje dla wierszy z `RowState`. `Added`</span><span class="sxs-lookup"><span data-stu-id="23aee-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="23aee-133">Proponowane wartości dla wiersza.</span><span class="sxs-lookup"><span data-stu-id="23aee-133">The proposed values for the row.</span></span> <span data-ttu-id="23aee-134">Ta wersja wiersza istnieje podczas operacji edycji w wierszu lub dla wiersza, który nie jest częścią `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="23aee-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="23aee-135">Możesz sprawdzić, czy `DataRow` ma określoną wersję wiersza, <xref:System.Data.DataRow.HasVersion%2A> wywołując metodę i przekazując `DataRowVersion` jako argument.</span><span class="sxs-lookup"><span data-stu-id="23aee-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="23aee-136">Na przykład `DataRow.HasVersion(DataRowVersion.Original)` program zwróci `false` dla nowo dodanych wierszy przed `AcceptChanges` wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="23aee-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="23aee-137">Poniższy przykład kodu wyświetla wartości we wszystkich usuniętych wierszach tabeli.</span><span class="sxs-lookup"><span data-stu-id="23aee-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="23aee-138">`Deleted`wiersze nie mają `Current` wersji wiersza, dlatego należy je przekazać `DataRowVersion.Original` podczas uzyskiwania dostępu do wartości kolumn.</span><span class="sxs-lookup"><span data-stu-id="23aee-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23aee-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23aee-139">See also</span></span>

- [<span data-ttu-id="23aee-140">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="23aee-140">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="23aee-141">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="23aee-141">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="23aee-142">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="23aee-142">DataAdapters and DataReaders</span></span>](../dataadapters-and-datareaders.md)
- [<span data-ttu-id="23aee-143">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="23aee-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
