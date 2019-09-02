---
title: Znajdowanie wierszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 2ff2b6b6d00c854d07f36d37986268a388c7f31b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203718"
---
# <a name="finding-rows"></a>Znajdowanie wierszy
Wiersze można wyszukiwać według ich wartości klucza sortowania przy użyciu <xref:System.Data.DataView.Find%2A> metod <xref:System.Data.DataView>i <xref:System.Data.DataView.FindRows%2A> . Wielkość liter w wartościach wyszukiwania w metodach **Find** i **FindRows** jest określana przez właściwość **CaseSensitive** elementu bazowego <xref:System.Data.DataTable>. Wartości wyszukiwania muszą być zgodne z istniejącymi wartościami klucza sortowania w całości w celu zwrócenia wyniku.  
  
 Metoda **Find** zwraca liczbę całkowitą z indeksem <xref:System.Data.DataRowView> odpowiadającym kryteriom wyszukiwania. Jeśli więcej niż jeden wiersz pasuje do kryteriów wyszukiwania, zwracany jest tylko indeks pierwszego pasującej **DataRowView** . Jeśli nie znaleziono żadnych dopasowań, **Znajdź** zwraca wartość-1.  
  
 Aby zwrócić wyniki wyszukiwania pasujące do wielu wierszy, użyj metody **FindRows** . **FindRows** działa podobnie jak Metoda **Find** , z tą różnicą, że zwraca tablicę **DataRowView** , która odwołuje się do wszystkich pasujących wierszy w **widoku**danych. Jeśli nie zostaną znalezione żadne dopasowania, tablica **DataRowView** będzie pusta.  
  
 Aby użyć metody **Find** lub **FindRows** , należy określić kolejność sortowania przez ustawienie **ApplyDefaultSort** na **true** lub przy użyciu właściwości **sort** . Jeśli kolejność sortowania nie zostanie określona, zostanie zgłoszony wyjątek.  
  
 Metody **Find** i **FindRows** pobierają tablicę wartości jako dane wejściowe, których długość jest zgodna z liczbą kolumn w kolejności sortowania. W przypadku sortowania pojedynczej kolumny można przekazać pojedynczą wartość. W przypadku zamówień sortowania zawierających wiele kolumn należy przekazać tablicę obiektów. Należy pamiętać, że w przypadku sortowania dla wielu kolumn wartości w tablicy obiektów muszą być zgodne z kolejnością kolumn określonych we właściwości **sort** elementu **DataView**.  
  
 Poniższy przykład kodu pokazuje metodę **Find** wywoływaną względem elementu **DataView** z kolejnością sortowania pojedynczej kolumny.  
  
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
  
 Jeśli właściwość **sortowania** określa wiele kolumn, należy przekazać tablicę obiektów z wartościami wyszukiwania dla każdej kolumny w kolejności określonej przez właściwość **sort** , jak w poniższym przykładzie kodu.  
  
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
- [Elementy DataView](dataviews.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
