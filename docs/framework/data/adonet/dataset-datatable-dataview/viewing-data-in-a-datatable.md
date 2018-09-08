---
title: Wyświetlanie danych w elemencie DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: de745633060dd4f7b1610492d0ff57ec7a4f545b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202144"
---
# <a name="viewing-data-in-a-datatable"></a>Wyświetlanie danych w elemencie DataTable
Można uzyskać dostęp do zawartości <xref:System.Data.DataTable> przy użyciu **wierszy** i **kolumn** kolekcji **DataTable**. Można również użyć <xref:System.Data.DataTable.Select%2A> metody zwracanie podzbiorów danych w **DataTable** zgodnie z kryteriami, w tym kryteria wyszukiwania, porządek sortowania i wiersz stanu. Ponadto można użyć <xref:System.Data.DataRowCollection.Find%2A> metody **kolekcji DataRowCollection** podczas wyszukiwania określonego wiersza przy użyciu wartości klucza podstawowego.  
  
 **Wybierz** metody **DataTable** zwraca zbiór <xref:System.Data.DataRow> obiekty spełniające określone kryteria. **Wybierz** przyjmuje opcjonalne argumenty wyrażenia filtru wyrażenie sortowania i **DataViewRowState**. Wyrażenie filtru identyfikuje, które wierszy do zwrócenia na podstawie **DataColumn** wartości, takich jak `LastName = 'Smith'`. Wyrażenie sortowania zgodna z konwencjami standardowa SQL do ustalania kolejności kolumn, na przykład `LastName ASC, FirstName ASC`. Reguły dotyczące wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość **DataColumn** klasy.  
  
> [!TIP]
>  Jeśli przeprowadzasz liczba wywołań **wybierz** metody **DataTable**, może zwiększyć wydajność, tworząc pierwszy <xref:System.Data.DataView> dla **DataTable**. Tworzenie **DataView** indeksuje wiersze z tabeli. **Wybierz** metody, a następnie usees, które indeksować, znacznie skracając czas do generowania wyników kwerendy. Aby uzyskać informacje o tworzeniu **DataView** dla **DataTable**, zobacz [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 **Wybierz** Metoda określa na podstawie której wersji wierszy do wyświetlenia lub modyfikowania <xref:System.Data.DataViewRowState>. W poniższej tabeli opisano możliwe **DataViewRowState** wartości wyliczenia.  
  
|Wartość DataViewRowState|Opis|  
|----------------------------|-----------------|  
|**CurrentRows**|Bieżące wiersze, w tym bez zmian, dodano i zmodyfikowane wiersze.|  
|**Usunięto**|Usunięty wiersz.|  
|**ModifiedCurrent**|W bieżącej wersji, która to zmodyfikowana wersja oryginalnych danych. (Zobacz **ModifiedOriginal**.)|  
|**ModifiedOriginal**|Oryginalna wersja wszystkie zmodyfikowane wiersze. Bieżąca wersja jest dostępna za pomocą **ModifiedCurrent**.|  
|**Dodano**|Nowy wiersz.|  
|**Brak**|Brak.|  
|**OriginalRows**|Oryginalny wierszy, w tym bez zmian i usunięte wiersze.|  
|**bez zmian**|Niezmieniony.|  
  
 W poniższym przykładzie **DataSet** obiektu jest filtrowana, tak aby tylko pracujesz z wierszami, którego **DataViewRowState** ustawiono **CurrentRows**.  
  
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
  
 **Wybierz** metoda może służyć do zwrócenia wierszy z różniących się **RowState** wartości lub wartości pól. Poniższy przykład zwraca **DataRow** tablica, która odwołuje się do wszystkich wierszy, które zostały usunięte, a następnie zwraca innego **DataRow** tablica, która odwołuje się do wszystkich wierszy, uporządkowane według **CustLName**, gdzie **CustID** kolumny jest większa niż 5. Aby uzyskać informacje o sposobie wyświetlania informacji w **usunięte** wiersza, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
