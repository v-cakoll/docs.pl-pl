---
title: Dodawanie danych do elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: adf2378cead054efcef10a73bfd00ef541940949
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494123"
---
# <a name="adding-data-to-a-datatable"></a>Dodawanie danych do elementu DataTable
Po utworzeniu <xref:System.Data.DataTable> i zdefiniuj strukturę przy użyciu kolumn i ograniczeń, można dodać nowe wiersze danych do tabeli. Aby dodać nowy wiersz, należy zadeklarować nową zmienną jako typ <xref:System.Data.DataRow>. Nowy **DataRow** obiekt jest zwracany po wywołaniu <xref:System.Data.DataTable.NewRow%2A> metody. **DataTable** utworzy **DataRow** obiektu na podstawie struktury tabeli, zgodnie z definicją <xref:System.Data.DataColumnCollection>.  
  
 Poniższy przykład przedstawia sposób tworzenia nowego wiersza, wywołując **NewRow** metody.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Możesz następnie manipulować wiersz nowo dodane przy użyciu indeksu lub nazwa kolumny, jak pokazano w poniższym przykładzie.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Po wstawieniu danych do nowego wiersza **Dodaj** metoda służy do dodawania wierszy do <xref:System.Data.DataRowCollection>, jak pokazano w poniższym kodzie.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Można również wywołać **Dodaj** metodę, aby dodać nowy wiersz, przekazując tablicę wartości, wpisanych w formie <xref:System.Object>, jak pokazano w poniższym przykładzie.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Przekazując tablicę wartości, wpisanych w formie **obiektu**, **Dodaj** metoda tworzy nowy wiersz w tabeli i ustawia jego wartości kolumny wartości w tablicy obiektu. Należy pamiętać, że wartości w tablicy są dopasowywane sekwencyjnie do kolumn, w kolejności, w jakiej są wyświetlane w tabeli.  
  
 Poniższy przykład dodaje 10 wierszy do nowo utworzonego **klientów** tabeli.  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
