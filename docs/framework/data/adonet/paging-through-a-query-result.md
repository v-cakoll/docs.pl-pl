---
title: Stronicowanie za pośrednictwem wyniku zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 2e7fb97e5c0cb42deff43c411f47e8d30e2257ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149391"
---
# <a name="paging-through-a-query-result"></a>Stronicowanie za pośrednictwem wyniku zapytania
Stronicowanie za pośrednictwem wyniku kwerendy jest procesem zwracania wyników kwerendy w mniejszych podzbiorach danych lub stron. Jest to powszechna praktyka wyświetlania wyników użytkownikowi w małych, łatwych w zarządzaniu fragmentów.  
  
 **DataAdapter** zapewnia możliwość zwracania tylko strony danych, za pośrednictwem przeciążenia **Fill** metody. Jednak może to nie być najlepszym wyborem dla stronicowania za pośrednictwem wyników dużych <xref:System.Data.DataTable> <xref:System.Data.DataSet> kwerend, ponieważ mimo **dataAdapter** wypełnia miejsce docelowe lub tylko żądane rekordy, zasoby do zwrócenia całej kwerendy są nadal używane. Aby zwrócić stronę danych ze źródła danych bez użycia zasobów do zwrócenia całej kwerendy, należy określić dodatkowe kryteria dla kwerendy, które zmniejszają wiersze zwracane tylko do tych wymaganych.  
  
 Aby użyć **Fill** metody zwracać stronę danych, należy określić **startRecord** parametru dla pierwszego rekordu na stronie danych i **maxRecords** parametr, dla liczby rekordów na stronie danych.  
  
 Poniższy przykład kodu pokazuje, jak użyć **Fill** metody zwracania pierwszej strony wynik kwerendy, gdzie rozmiar strony jest pięć rekordów.  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 W poprzednim przykładzie **Zestaw danych** jest wypełniony tylko pięcioma rekordami, ale zwracana jest cała **tabela Zamówienia.** Aby wypełnić **Zestaw danych** tymi samymi pięcioma rekordami, ale zwracaj tylko pięć rekordów, użyj klauzul TOP i WHERE w instrukcji SQL, jak w poniższym przykładzie kodu.  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 Należy zauważyć, że podczas stronicowania za pośrednictwem wyników kwerendy w ten sposób, należy zachować unikatowy identyfikator, który zamawia wiersze, w celu przekazania unikatowego identyfikatora do polecenia, aby zwrócić następną stronę rekordów, jak pokazano w poniższym przykładzie kodu.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Aby zwrócić następną stronę rekordów przy użyciu przeciążenia **Fill** metody, która przyjmuje **startRecord** i **maxRecords** parametry, przyrost bieżącego indeksu rekordu o rozmiar strony i wypełnić tabelę. Należy pamiętać, że serwer bazy danych zwraca wyniki całej kwerendy, nawet jeśli tylko jedna strona rekordów jest dodawana do **zestawu danych**. W poniższym przykładzie kodu wiersze tabeli są czyszczone przed ich wypełnieniem następnej strony danych. Można zachować pewną liczbę zwróconych wierszy w lokalnej pamięci podręcznej, aby zmniejszyć liczbę podróży do serwera bazy danych.  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 Aby zwrócić następną stronę rekordów bez zwracania całej kwerendy przez serwer bazy danych, należy określić restrykcyjne kryteria instrukcji SELECT. Ponieważ w poprzednim przykładzie zachowane ostatni rekord zwrócony, można go użyć w klauzuli WHERE, aby określić punkt początkowy dla kwerendy, jak pokazano w poniższym przykładzie kodu.  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a>Zobacz też

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Omówienie ADO.NET](ado-net-overview.md)
