---
title: Wyświetlanie danych w DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: 5d39d2a856a40b5ea20832a544ede360313309d3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761249"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="de95f-102">Wyświetlanie danych w DataTable</span><span class="sxs-lookup"><span data-stu-id="de95f-102">Viewing Data in a DataTable</span></span>
<span data-ttu-id="de95f-103">Można uzyskać dostępu do zawartości <xref:System.Data.DataTable> za pomocą **wierszy** i **kolumn** kolekcji **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="de95f-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="de95f-104">Można również użyć <xref:System.Data.DataTable.Select%2A> metodę zwracanie podzbiorów danych w **DataTable** zgodnie z kryteriami, w tym kryteria wyszukiwania, porządek sortowania i wiersza stanu.</span><span class="sxs-lookup"><span data-stu-id="de95f-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="de95f-105">Ponadto można użyć <xref:System.Data.DataRowCollection.Find%2A> metody **kolekcji DataRowCollection** podczas wyszukiwania dla konkretnego wiersza przy użyciu wartości klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="de95f-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>  
  
 <span data-ttu-id="de95f-106">**Wybierz** metody **DataTable** obiektu zwraca zbiór <xref:System.Data.DataRow> obiektów spełniających określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="de95f-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="de95f-107">**Wybierz** przyjmuje argumenty opcjonalne wyrażenia filtru, wyrażenie sortowania i **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="de95f-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="de95f-108">Wyrażenie filtru identyfikuje wiersze do zwrócenia na podstawie **DataColumn** wartości, takich jak `LastName = 'Smith'`.</span><span class="sxs-lookup"><span data-stu-id="de95f-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="de95f-109">Wyrażenie sortowania zgodna z konwencjami standardowe SQL porządkowania kolumn, na przykład `LastName ASC, FirstName ASC`.</span><span class="sxs-lookup"><span data-stu-id="de95f-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="de95f-110">W przypadku reguł dotyczących wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość **DataColumn** klasy.</span><span class="sxs-lookup"><span data-stu-id="de95f-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="de95f-111">Jeśli przeprowadzasz liczba wywołań **wybierz** metody **DataTable**, można zwiększyć wydajność, tworząc pierwszy <xref:System.Data.DataView> dla **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="de95f-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="de95f-112">Tworzenie **DataView** indeksuje wiersze w tabeli.</span><span class="sxs-lookup"><span data-stu-id="de95f-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="de95f-113">**Wybierz** metody, a następnie usees, które indeksu, znacznie skraca czas do generowania wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="de95f-113">The **Select** method then usees that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="de95f-114">Aby uzyskać informacje o tworzeniu **DataView** dla **DataTable**, zobacz [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span><span class="sxs-lookup"><span data-stu-id="de95f-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span></span>  
  
 <span data-ttu-id="de95f-115">**Wybierz** Metoda określa na podstawie wersji wierszy do wyświetlania lub modyfikowania <xref:System.Data.DataViewRowState>.</span><span class="sxs-lookup"><span data-stu-id="de95f-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="de95f-116">W poniższej tabeli opisano możliwe **DataViewRowState** wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="de95f-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>  
  
|<span data-ttu-id="de95f-117">Wartość DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="de95f-117">DataViewRowState value</span></span>|<span data-ttu-id="de95f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="de95f-118">Description</span></span>|  
|----------------------------|-----------------|  
|<span data-ttu-id="de95f-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="de95f-119">**CurrentRows**</span></span>|<span data-ttu-id="de95f-120">Bieżące bez zmian, dodano i zmodyfikowanych wierszy w tym wiersze.</span><span class="sxs-lookup"><span data-stu-id="de95f-120">Current rows including unchanged, added, and modified rows.</span></span>|  
|<span data-ttu-id="de95f-121">**usunięte**</span><span class="sxs-lookup"><span data-stu-id="de95f-121">**Deleted**</span></span>|<span data-ttu-id="de95f-122">Wiersz usunięty.</span><span class="sxs-lookup"><span data-stu-id="de95f-122">A deleted row.</span></span>|  
|<span data-ttu-id="de95f-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="de95f-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="de95f-124">W bieżącej wersji, która jest zmodyfikowanej wersji oryginalnych danych.</span><span class="sxs-lookup"><span data-stu-id="de95f-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="de95f-125">(Zobacz **ModifiedOriginal**.)</span><span class="sxs-lookup"><span data-stu-id="de95f-125">(See **ModifiedOriginal**.)</span></span>|  
|<span data-ttu-id="de95f-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="de95f-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="de95f-127">Z oryginalną wersją wszystkich zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="de95f-127">The original version of all modified rows.</span></span> <span data-ttu-id="de95f-128">Bieżąca wersja jest dostępna za pomocą **ModifiedCurrent**.</span><span class="sxs-lookup"><span data-stu-id="de95f-128">The current version is available using **ModifiedCurrent**.</span></span>|  
|<span data-ttu-id="de95f-129">**Dodane**</span><span class="sxs-lookup"><span data-stu-id="de95f-129">**Added**</span></span>|<span data-ttu-id="de95f-130">Nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="de95f-130">A new row.</span></span>|  
|<span data-ttu-id="de95f-131">**Brak**</span><span class="sxs-lookup"><span data-stu-id="de95f-131">**None**</span></span>|<span data-ttu-id="de95f-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="de95f-132">None.</span></span>|  
|<span data-ttu-id="de95f-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="de95f-133">**OriginalRows**</span></span>|<span data-ttu-id="de95f-134">Oryginalny wiersze, w tym bez zmian i usuniętych wierszy.</span><span class="sxs-lookup"><span data-stu-id="de95f-134">Original rows, including unchanged and deleted rows.</span></span>|  
|<span data-ttu-id="de95f-135">**Bez zmian**</span><span class="sxs-lookup"><span data-stu-id="de95f-135">**Unchanged**</span></span>|<span data-ttu-id="de95f-136">Niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="de95f-136">An unchanged row.</span></span>|  
  
 <span data-ttu-id="de95f-137">W poniższym przykładzie **DataSet** obiektu jest filtrowany, tak aby tylko pracy z wierszami którego **DataViewRowState** ustawiono **CurrentRows**.</span><span class="sxs-lookup"><span data-stu-id="de95f-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 <span data-ttu-id="de95f-138">**Wybierz** metody umożliwia zwracanie wszystkich wierszy z różnym **RowState** wartości lub wartości pól.</span><span class="sxs-lookup"><span data-stu-id="de95f-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="de95f-139">Poniższy przykład zwraca **DataRow** tablica, która odwołuje się do wszystkich wierszy, które zostały usunięte, a następnie zwraca innego **DataRow** tablica, która odwołuje się do wszystkich wierszy, uporządkowanych według **CustLName**, gdzie **IDKlienta** kolumny jest większa niż 5.</span><span class="sxs-lookup"><span data-stu-id="de95f-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="de95f-140">Aby uzyskać informacje o sposobie wyświetlania informacji w **usunięte** wiersz, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="de95f-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a><span data-ttu-id="de95f-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de95f-141">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [<span data-ttu-id="de95f-142">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="de95f-142">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="de95f-143">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="de95f-143">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="de95f-144">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="de95f-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
