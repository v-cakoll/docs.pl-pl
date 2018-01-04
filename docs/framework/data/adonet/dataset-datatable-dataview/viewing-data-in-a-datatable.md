---
title: "Wyświetlanie danych w DataTable"
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
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ab7a60b4195f3d8976a61e3909682b3748e30341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="viewing-data-in-a-datatable"></a>Wyświetlanie danych w DataTable
Można uzyskać dostępu do zawartości <xref:System.Data.DataTable> za pomocą **wierszy** i **kolumn** kolekcji **DataTable**. Można również użyć <xref:System.Data.DataTable.Select%2A> metodę zwracanie podzbiorów danych w **DataTable** zgodnie z kryteriami, w tym kryteria wyszukiwania, porządek sortowania i wiersza stanu. Ponadto można użyć <xref:System.Data.DataRowCollection.Find%2A> metody **kolekcji DataRowCollection** podczas wyszukiwania dla konkretnego wiersza przy użyciu wartości klucza podstawowego.  
  
 **Wybierz** metody **DataTable** obiektu zwraca zbiór <xref:System.Data.DataRow> obiektów spełniających określone kryteria. **Wybierz** przyjmuje argumenty opcjonalne wyrażenia filtru, wyrażenie sortowania i **DataViewRowState**. Wyrażenie filtru identyfikuje wiersze do zwrócenia na podstawie **DataColumn** wartości, takich jak `LastName = 'Smith'`. Wyrażenie sortowania zgodna z konwencjami standardowe SQL porządkowania kolumn, na przykład `LastName ASC, FirstName ASC`. W przypadku reguł dotyczących wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość **DataColumn** klasy.  
  
> [!TIP]
>  Jeśli przeprowadzasz liczba wywołań **wybierz** metody **DataTable**, można zwiększyć wydajność, tworząc pierwszy <xref:System.Data.DataView> dla **DataTable**. Tworzenie **DataView** indeksuje wiersze w tabeli. **Wybierz** metody, a następnie usees, które indeksu, znacznie skraca czas do generowania wyników zapytania. Aby uzyskać informacje o tworzeniu **DataView** dla **DataTable**, zobacz [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 **Wybierz** Metoda określa na podstawie wersji wierszy do wyświetlania lub modyfikowania <xref:System.Data.DataViewRowState>. W poniższej tabeli opisano możliwe **DataViewRowState** wartości wyliczenia.  
  
|Wartość DataViewRowState|Opis|  
|----------------------------|-----------------|  
|**CurrentRows**|Bieżące bez zmian, dodano i zmodyfikowanych wierszy w tym wiersze.|  
|**Usunięte**|Wiersz usunięty.|  
|**ModifiedCurrent**|W bieżącej wersji, która jest zmodyfikowanej wersji oryginalnych danych. (Zobacz **ModifiedOriginal**.)|  
|**ModifiedOriginal**|Z oryginalną wersją wszystkich zmodyfikowanych wierszy. Bieżąca wersja jest dostępna za pomocą **ModifiedCurrent**.|  
|**Dodane**|Nowy wiersz.|  
|**Brak**|Brak.|  
|**OriginalRows**|Oryginalny wiersze, w tym bez zmian i usuniętych wierszy.|  
|**Bez zmian**|Niezmieniony.|  
  
 W poniższym przykładzie **DataSet** obiektu jest filtrowany, tak aby tylko pracy z wierszami którego **DataViewRowState** ustawiono **CurrentRows**.  
  
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
  
 **Wybierz** metody umożliwia zwracanie wszystkich wierszy z różnym **RowState** wartości lub wartości pól. Poniższy przykład zwraca **DataRow** tablica, która odwołuje się do wszystkich wierszy, które zostały usunięte, a następnie zwraca innego **DataRow** tablica, która odwołuje się do wszystkich wierszy, uporządkowanych według **CustLName**, gdzie **IDKlienta** kolumny jest większa niż 5. Aby uzyskać informacje o sposobie wyświetlania informacji w **usunięte** wiersz, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
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
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
