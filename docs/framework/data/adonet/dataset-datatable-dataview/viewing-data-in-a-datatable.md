---
title: Wyświetlanie danych w elemencie DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: ea92b8a5e46bdaa8e94756cd28a3fbcb2789d7b3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204388"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="5c003-102">Wyświetlanie danych w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="5c003-102">Viewing Data in a DataTable</span></span>

<span data-ttu-id="5c003-103">Można uzyskać <xref:System.Data.DataTable> dostęp do zawartości a przy użyciu kolekcji **wierszy** i **kolumn** **tabeli DataTable**.</span><span class="sxs-lookup"><span data-stu-id="5c003-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="5c003-104">Można również użyć metody, <xref:System.Data.DataTable.Select%2A> aby zwrócić podzbiory danych w **elemencie DataTable** zgodnie z kryteriami wyszukiwania, kolejności sortowania i stanem wiersza.</span><span class="sxs-lookup"><span data-stu-id="5c003-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="5c003-105">Ponadto można użyć <xref:System.Data.DataRowCollection.Find%2A> metody obiektu DataRowCollection podczas wyszukiwania określonego wiersza przy użyciu wartości klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5c003-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>

<span data-ttu-id="5c003-106">Metoda **SELECT** obiektu **DataTable** zwraca zestaw <xref:System.Data.DataRow> obiektów spełniających określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="5c003-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="5c003-107">**Wybierz** pobiera opcjonalne argumenty wyrażenia filtru, wyrażenie sortowania i **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="5c003-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="5c003-108">Wyrażenie filtru identyfikuje wiersze do zwrócenia na podstawie wartości **kolumn DataColumn** , takich jak `LastName = 'Smith'`.</span><span class="sxs-lookup"><span data-stu-id="5c003-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="5c003-109">Wyrażenie sortowania stosuje się do standardowych konwencji SQL w celu porządkowania kolumn, `LastName ASC, FirstName ASC`na przykład.</span><span class="sxs-lookup"><span data-stu-id="5c003-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="5c003-110">Aby uzyskać reguły dotyczące pisania wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość klasy DataColumn.</span><span class="sxs-lookup"><span data-stu-id="5c003-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>

> [!TIP]
> <span data-ttu-id="5c003-111">W przypadku wykonywania wielu wywołań metody **SELECT** **elementu DataTable**można zwiększyć wydajność, tworząc najpierw element <xref:System.Data.DataView> dla **elementu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="5c003-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="5c003-112">Utworzenie elementu **DataView** indeksuje wiersze tabeli.</span><span class="sxs-lookup"><span data-stu-id="5c003-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="5c003-113">Metoda **SELECT** używa tego indeksu znacznie skraca czas generowania wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="5c003-113">The **Select** method then uses that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="5c003-114">Aby uzyskać informacje na temat tworzenia elementu **DataView** dla **elementu DataTable**, zobacz temat DataViews. [](dataviews.md)</span><span class="sxs-lookup"><span data-stu-id="5c003-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](dataviews.md).</span></span>

<span data-ttu-id="5c003-115">Metoda **SELECT** określa, która wersja wierszy ma być wyświetlana lub manipulowana na podstawie <xref:System.Data.DataViewRowState>.</span><span class="sxs-lookup"><span data-stu-id="5c003-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="5c003-116">W poniższej tabeli opisano możliwe wartości wyliczenia **DataViewRowState** .</span><span class="sxs-lookup"><span data-stu-id="5c003-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>

|<span data-ttu-id="5c003-117">DataViewRowState wartość</span><span class="sxs-lookup"><span data-stu-id="5c003-117">DataViewRowState value</span></span>|<span data-ttu-id="5c003-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5c003-118">Description</span></span>|
|----------------------------|-----------------|
|<span data-ttu-id="5c003-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="5c003-119">**CurrentRows**</span></span>|<span data-ttu-id="5c003-120">Bieżące wiersze z uwzględnieniem niezmienionych, dodanych i zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="5c003-120">Current rows including unchanged, added, and modified rows.</span></span>|
|<span data-ttu-id="5c003-121">**Skasowan**</span><span class="sxs-lookup"><span data-stu-id="5c003-121">**Deleted**</span></span>|<span data-ttu-id="5c003-122">Usunięty wiersz.</span><span class="sxs-lookup"><span data-stu-id="5c003-122">A deleted row.</span></span>|
|<span data-ttu-id="5c003-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="5c003-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="5c003-124">Bieżąca wersja, która jest zmodyfikowaną wersją oryginalnych danych.</span><span class="sxs-lookup"><span data-stu-id="5c003-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="5c003-125">(Zobacz **ModifiedOriginal**).</span><span class="sxs-lookup"><span data-stu-id="5c003-125">(See **ModifiedOriginal**.)</span></span>|
|<span data-ttu-id="5c003-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="5c003-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="5c003-127">Oryginalna wersja wszystkich zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="5c003-127">The original version of all modified rows.</span></span> <span data-ttu-id="5c003-128">Bieżąca wersja jest dostępna przy użyciu **ModifiedCurrent**.</span><span class="sxs-lookup"><span data-stu-id="5c003-128">The current version is available using **ModifiedCurrent**.</span></span>|
|<span data-ttu-id="5c003-129">**Dołączony**</span><span class="sxs-lookup"><span data-stu-id="5c003-129">**Added**</span></span>|<span data-ttu-id="5c003-130">Nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="5c003-130">A new row.</span></span>|
|<span data-ttu-id="5c003-131">**Brak**</span><span class="sxs-lookup"><span data-stu-id="5c003-131">**None**</span></span>|<span data-ttu-id="5c003-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="5c003-132">None.</span></span>|
|<span data-ttu-id="5c003-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="5c003-133">**OriginalRows**</span></span>|<span data-ttu-id="5c003-134">Oryginalne wiersze, włącznie z niezmienionymi i usuniętymi wierszami.</span><span class="sxs-lookup"><span data-stu-id="5c003-134">Original rows, including unchanged and deleted rows.</span></span>|
|<span data-ttu-id="5c003-135">**Bez zmian**</span><span class="sxs-lookup"><span data-stu-id="5c003-135">**Unchanged**</span></span>|<span data-ttu-id="5c003-136">Niezmieniony wiersz.</span><span class="sxs-lookup"><span data-stu-id="5c003-136">An unchanged row.</span></span>|

<span data-ttu-id="5c003-137">W poniższym przykładzie obiekt **DataSet** jest filtrowany, dzięki czemu pracujesz tylko z wierszami, których **DataViewRowState** jest ustawiona na **CurrentRows**.</span><span class="sxs-lookup"><span data-stu-id="5c003-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>

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

<span data-ttu-id="5c003-138">Metoda **SELECT** może służyć do zwracania wierszy zawierających różne wartości **RowState** lub wartości pól.</span><span class="sxs-lookup"><span data-stu-id="5c003-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="5c003-139">Poniższy przykład zwraca tablicę **DataRow** , która odwołuje się do wszystkich wierszy, które zostały usunięte, i zwraca kolejną tablicę **DataRow** , która odwołuje się do wszystkich wierszy, uporządkowanych według **CustLName**, gdzie kolumna **CustId** jest większa niż 5.</span><span class="sxs-lookup"><span data-stu-id="5c003-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="5c003-140">Aby uzyskać informacje na temat sposobu wyświetlania informacji w **usuwanym** wierszu, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="5c003-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5c003-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c003-141">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [<span data-ttu-id="5c003-142">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="5c003-142">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="5c003-143">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="5c003-143">Row States and Row Versions</span></span>](row-states-and-row-versions.md)
- [<span data-ttu-id="5c003-144">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5c003-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
