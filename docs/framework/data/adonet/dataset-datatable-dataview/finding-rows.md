---
title: Znajdowanie wierszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151146"
---
# <a name="finding-rows"></a>Znajdowanie wierszy
Wiersze można wyszukiwać zgodnie z ich wartościami <xref:System.Data.DataView.FindRows%2A> klucza <xref:System.Data.DataView>sortowania przy użyciu <xref:System.Data.DataView.Find%2A> metod i metody programu . Wielkość liter wartości wyszukiwania w find **and** **FindRows** metody jest określana przez **CaseSensitive** właściwość podstawowej <xref:System.Data.DataTable>. Wartości wyszukiwania muszą być zgodne z istniejącymi wartościami klucza sortowania w całości, aby uzyskać wynik.  
  
 **Find** Metoda zwraca liczbę całkowitą z indeksem, <xref:System.Data.DataRowView> który odpowiada kryteriom wyszukiwania. Jeśli więcej niż jeden wiersz spełnia kryteria wyszukiwania, zwracany jest tylko indeks pierwszego pasującego **datarowview.** Jeśli nie zostaną znalezione żadne dopasowania, **funkcja Znajdź** zwraca wartość -1.  
  
 Aby zwrócić wyniki wyszukiwania, które pasują do wielu wierszy, użyj **Metody FindRows.** **Funkcja FindRows** działa podobnie jak metoda **Find,** z tą różnicą, że zwraca tablicę **DataRowView,** która odwołuje się do wszystkich pasujących wierszy w **pliku DataView**. Jeśli nie zostaną znalezione żadne dopasowania, **datarowview** tablica będzie pusta.  
  
 Aby użyć **find** lub **FindRows** metody należy określić kolejność sortowania albo przez ustawienie **ApplyDefaultSort** **true** lub za pomocą **Sort właściwości.** Jeśli nie określono kolejności sortowania, zgłaszany jest wyjątek.  
  
 **Find** i **FindRows** metody wziąć tablicę wartości jako dane wejściowe, których długość odpowiada liczbie kolumn w kolejności sortowania. W przypadku sortowania w jednej kolumnie można przekazać pojedynczą wartość. W przypadku zamówień sortowania zawierających wiele kolumn należy przekazać tablicę obiektów. Należy zauważyć, że w przypadku sortowania w wielu kolumnach wartości w tablicy obiektów muszą być zgodne z kolejnością kolumn określonych we właściwości **Sortowanie** **widoku DataView**.  
  
 Poniższy przykład kodu pokazuje **Find** metoda wywoływana dla **DataView** z kolejnością sortowania pojedynczej kolumny.  
  
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
  
 Jeśli właściwość **Sort** określa wiele kolumn, należy przekazać tablicę obiektów z wartościami wyszukiwania dla każdej kolumny w kolejności określonej przez **sortowanie** właściwości, jak w poniższym przykładzie kodu.  
  
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

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Elementy DataView](dataviews.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
