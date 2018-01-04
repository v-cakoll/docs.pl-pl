---
title: Znajdowanie wierszy
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
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9ede2dbf0718a4ca1d8025af3ce60c256afc867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="finding-rows"></a>Znajdowanie wierszy
Możesz wyszukać wierszy, zgodnie z ich wartości klucza sortowania za pomocą <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>. Uwzględniana wielkość liter wyszukiwania wartości w **znaleźć** i **FindRows** metod jest określany przez **CaseSensitive** właściwości podstawowych <xref:System.Data.DataTable>. Wartości wyszukiwania musi być zgodna istniejące wartości klucza sortowania w całości w celu zwrócony wynik.  
  
 **Znaleźć** metoda zwraca liczbę całkowitą z indeksem <xref:System.Data.DataRowView> odpowiadającego kryteriom wyszukiwania. Jeśli więcej niż jeden wiersz spełnia kryteria wyszukiwania, indeks pierwszego dopasowania **DataRowView** jest zwracany. W przypadku nieodnalezienia żadnych dopasowań **znaleźć** zwraca wartość -1.  
  
 Aby zwrócić wyników wyszukiwania, które odpowiada wiele wierszy, należy użyć **FindRows** metody. **FindRows** działa podobnie do **znaleźć** metody, z wyjątkiem, że zwraca **DataRowView** tablica, która odwołuje się do wszystkich zgodnych wierszy w **DataView**. W przypadku nieodnalezienia żadnych dopasowań **DataRowView** tablica jest pusta.  
  
 Umożliwia **znaleźć** lub **FindRows** metody sortowania należy określić kolejność, albo ustawiając **ApplyDefaultSort** do **true** lub za pomocą **Sortowania** właściwości. Jeśli określono żadnego porządku sortowania, jest zwracany wyjątek.  
  
 **Znaleźć** i **FindRows** metody przyjmują tablicy wartości jako dane wejściowe, którego długość jest zgodna z liczbą kolumn w kolejności sortowania. W przypadku sortowania w jednej kolumnie można przekazać pojedynczą wartość. Do sortowania zawierających wiele kolumn należy przekazać tablicę obiektów. Należy pamiętać, sortować na wiele kolumn, wartości w tablicy object musi odpowiadać kolejność kolumn określonych w **sortowania** właściwość **DataView**.  
  
 Poniższy kod przedstawia przykład **znaleźć** metoda jest wywoływana względem **DataView** z kolejnością sortowania jednej kolumny.  
  
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
  
 Jeśli Twoje **sortowania** właściwość określa wiele kolumn, należy przekazać tablicy obiektów o wartości wyszukiwania dla każdej kolumny w kolejności określonej przez **sortowania** właściwości, jak w poniższym przykładzie kodu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
