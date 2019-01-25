---
title: Znajdowanie wierszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: e5a48c5caf9239e0e7b7f2e7a3ad8ab5df168ba1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684193"
---
# <a name="finding-rows"></a>Znajdowanie wierszy
Możesz wyszukać wierszy, zgodnie z ich wartości kluczy sortowania + przy użyciu <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>. Rozróżnianie wielkości liter wyszukiwania wartości w **znaleźć** i **FindRows** metody jest określana przez **CaseSensitive** właściwości podstawowych <xref:System.Data.DataTable>. Wyszukiwanie wartości muszą być zgodne istniejącej wartości kluczy sortowania + w całości w celu zwrócenia wyników.  
  
 **Znaleźć** metoda zwraca liczbę całkowitą z indeksem <xref:System.Data.DataRowView> który pasuje do kryteriów wyszukiwania. Jeśli więcej niż jeden wiersz pasujących do kryteriów wyszukiwania, indeks pierwszego dopasowania **DataRowView** jest zwracana. W przypadku nieodnalezienia żadnych dopasowań **znaleźć** zwraca wartość -1.  
  
 Aby zwrócić wyniki wyszukiwania, które pasuje wiele wierszy, użyj **FindRows** metody. **FindRows** działa podobnie jak w przypadku **znaleźć** metody, z wyjątkiem, że zwraca **DataRowView** tablica, która odwołuje się do wszystkich zgodnych wierszy w **DataView**. W przypadku nieodnalezienia żadnych dopasowań **DataRowView** tablica jest pusta.  
  
 Do użycia **znaleźć** lub **FindRows** metody, należy określić sortowania order, albo ustawiając **ApplyDefaultSort** do **true** lub za pomocą **Sortowania** właściwości. Jeśli nie kolejność sortowania jest określony, zwracany wyjątek.  
  
 **Znaleźć** i **FindRows** metody przyjmują tablicę wartości jako dane wejściowe, którego długość jest zgodna z liczbą kolumn w porządku sortowania. W przypadku sortowania w jednej kolumnie można przekazać wartość typu single. Do sortowania, zawierających wiele kolumn należy przekazać tablicę obiektów. Należy pamiętać, że sortowania na wiele kolumn, wartości w tablicy obiektu musi odpowiadać kolejność kolumn określonych w **sortowania** właściwość **DataView**.  
  
 Poniższy kod przedstawia przykład **znaleźć** metoda jest wywoływana względem **DataView** z porządkiem sortowania jedną kolumnę.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 Jeśli Twoje **sortowania** właściwość określa wiele kolumn, należy przekazać tablicę obiektów przy użyciu wartości wyszukiwania dla każdej kolumny w kolejności określonej przez **sortowania** właściwości, jak w poniższym przykładzie kodu.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
