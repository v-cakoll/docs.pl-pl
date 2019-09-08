---
title: Wyświetlanie danych w elemencie DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: c13f0b802b2714a17ea4014625a65ebd1b0011f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785853"
---
# <a name="viewing-data-in-a-datatable"></a>Wyświetlanie danych w elemencie DataTable

Można uzyskać <xref:System.Data.DataTable> dostęp do zawartości a przy użyciu kolekcji **wierszy** i **kolumn** **tabeli DataTable**. Można również użyć metody, <xref:System.Data.DataTable.Select%2A> aby zwrócić podzbiory danych w **elemencie DataTable** zgodnie z kryteriami wyszukiwania, kolejności sortowania i stanem wiersza. Ponadto można użyć <xref:System.Data.DataRowCollection.Find%2A> metody obiektu **DataRowCollection** podczas wyszukiwania określonego wiersza przy użyciu wartości klucza podstawowego.

Metoda **SELECT** obiektu **DataTable** zwraca zestaw <xref:System.Data.DataRow> obiektów spełniających określone kryteria. **Wybierz** pobiera opcjonalne argumenty wyrażenia filtru, wyrażenie sortowania i **DataViewRowState**. Wyrażenie filtru identyfikuje wiersze do zwrócenia na podstawie wartości **kolumn DataColumn** , takich jak `LastName = 'Smith'`. Wyrażenie sortowania stosuje się do standardowych konwencji SQL w celu porządkowania kolumn, `LastName ASC, FirstName ASC`na przykład. Aby uzyskać reguły dotyczące pisania wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość klasy **DataColumn** .

> [!TIP]
> W przypadku wykonywania wielu wywołań metody **SELECT** **elementu DataTable**można zwiększyć wydajność, tworząc najpierw element <xref:System.Data.DataView> dla **elementu DataTable**. Utworzenie elementu **DataView** indeksuje wiersze tabeli. Metoda **SELECT** używa tego indeksu znacznie skraca czas generowania wyników zapytania. Aby uzyskać informacje na temat tworzenia elementu **DataView** dla **elementu DataTable**, zobacz temat [DataViews](dataviews.md).

Metoda **SELECT** określa, która wersja wierszy ma być wyświetlana lub manipulowana na podstawie <xref:System.Data.DataViewRowState>. W poniższej tabeli opisano możliwe wartości wyliczenia **DataViewRowState** .

|DataViewRowState wartość|Opis|
|----------------------------|-----------------|
|**CurrentRows**|Bieżące wiersze z uwzględnieniem niezmienionych, dodanych i zmodyfikowanych wierszy.|
|**Skasowan**|Usunięty wiersz.|
|**ModifiedCurrent**|Bieżąca wersja, która jest zmodyfikowaną wersją oryginalnych danych. (Zobacz **ModifiedOriginal**).|
|**ModifiedOriginal**|Oryginalna wersja wszystkich zmodyfikowanych wierszy. Bieżąca wersja jest dostępna przy użyciu **ModifiedCurrent**.|
|**Dołączony**|Nowy wiersz.|
|**Brak**|Brak.|
|**OriginalRows**|Oryginalne wiersze, włącznie z niezmienionymi i usuniętymi wierszami.|
|**Bez zmian**|Niezmieniony wiersz.|

W poniższym przykładzie obiekt **DataSet** jest filtrowany, dzięki czemu pracujesz tylko z wierszami, których **DataViewRowState** jest ustawiona na **CurrentRows**.

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

Metoda **SELECT** może służyć do zwracania wierszy zawierających różne wartości **RowState** lub wartości pól. Poniższy przykład zwraca tablicę **DataRow** , która odwołuje się do wszystkich wierszy, które zostały usunięte, i zwraca kolejną tablicę **DataRow** , która odwołuje się do wszystkich wierszy, uporządkowanych według **CustLName**, gdzie kolumna **CustId** jest większa niż 5. Aby uzyskać informacje na temat sposobu wyświetlania informacji w **usuwanym** wierszu, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [Operowanie danymi w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [Stany wiersza i wersje wiersza](row-states-and-row-versions.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
