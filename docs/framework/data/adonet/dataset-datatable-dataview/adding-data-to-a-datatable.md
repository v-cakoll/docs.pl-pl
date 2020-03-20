---
title: Dodawanie danych do elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 02d7f94259cc56513be404c5539ca7015d5f3533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151536"
---
# <a name="adding-data-to-a-datatable"></a>Dodawanie danych do elementu DataTable
Po utworzeniu <xref:System.Data.DataTable> i zdefiniowaniu jego struktury przy użyciu kolumn i ograniczeń można dodać nowe wiersze danych do tabeli. Aby dodać nowy wiersz, zadeklaruj nową zmienną jako typ <xref:System.Data.DataRow>. Nowy obiekt **DataRow** jest zwracany <xref:System.Data.DataTable.NewRow%2A> po wywołaniu metody. **DataTable** następnie tworzy **DataRow** obiektu na podstawie struktury tabeli, <xref:System.Data.DataColumnCollection>zgodnie z definicją .  
  
 W poniższym przykładzie pokazano, jak utworzyć nowy wiersz, wywołując **NewRow** metody.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Następnie można manipulować nowo dodany wiersz przy użyciu indeksu lub nazwy kolumny, jak pokazano w poniższym przykładzie.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Po wstawieniu danych do nowego wiersza, **Add** metoda <xref:System.Data.DataRowCollection>jest używana do dodawania wiersza do , pokazano w poniższym kodzie.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Można również wywołać **Add** metody, aby dodać nowy wiersz, przekazując <xref:System.Object>w tablicy wartości, wpisane jako , jak pokazano w poniższym przykładzie.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Przekazywanie tablicy wartości wpisanych jako **Object**do **Metody Dodaj** tworzy nowy wiersz wewnątrz tabeli i ustawia jego wartości kolumn na wartości w tablicy obiektów. Należy zauważyć, że wartości w tablicy są dopasowywać sekwencyjnie do kolumn, na podstawie kolejności, w jakiej pojawiają się w tabeli.  
  
 W poniższym przykładzie dodano 10 wierszy do nowo utworzonej tabeli **Klienci.**  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Operowanie na danych w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
