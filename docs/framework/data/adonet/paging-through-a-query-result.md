---
title: Stronicowanie za pośrednictwem wyniku zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 023efcc15d7080afc1583f4ad8984e152b86cf23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878387"
---
# <a name="paging-through-a-query-result"></a>Stronicowanie za pośrednictwem wyniku zapytania
Stronicowanie za pośrednictwem wyników z zapytania jest proces zwracania wyników zapytania w mniejszy podzbiór danych lub strony. Jest to powszechną praktyką do wyświetlania wyników użytkownikowi we fragmentach małe, łatwy w zarządzaniu.  
  
 **DataAdapter** przewiduje zwracanie tylko strony danych za pomocą przeciążenia funkcji **wypełnienia** metody. Jednak może to nie być najlepszym wyborem dla stronicowanie wyników dużych zapytania, ponieważ mimo że **DataAdapter** wypełnia obiekt docelowy <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> tylko żądane rekordy zasobów do zwrócenia całe zapytanie są nadal używane. Aby przywrócić strony danych ze źródła danych bez użycia zasobów, aby zwrócić całe zapytanie, określić dodatkowe kryteria dla zapytania, które zmniejszają wierszy zwracanych do tylko wymaganych.  
  
 Aby użyć **wypełnienia** Określ metodę, aby powrócić do strony danych, **startRecord** parametr dla pierwszego rekordu w strony danych i **maxRecords** parametru, liczby rekordy w strony danych.  
  
 Poniższy przykład kodu pokazuje sposób użycia **wypełnienia** metodę do zwracania pierwszej strony wyników zapytania, których rozmiar strony jest pięć rekordów.  
  
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
  
 W poprzednim przykładzie **DataSet** tylko wypełnionej pięć rekordów, ale cały **zamówienia** zwracana jest tabela. Aby wypełnić **DataSet** przy użyciu tych samych pięciu rekordy, ale zwrócić tylko pięć rekordów, użyj GÓRNEJ i klauzulach WHERE w instrukcji SQL, jak w poniższym przykładzie kodu.  
  
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
  
 Należy pamiętać, że gdy stronicowanie wyników zapytania w ten sposób, należy zachować Unikatowy identyfikator, która porządkuje wierszy, aby można było przekazać Unikatowy identyfikator polecenia do zwrócenia na następnej stronie rekordy, jak pokazano w poniższym przykładzie kodu.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Aby powrócić do następnej strony rekordów za pomocą przeciążenia **wypełnienia** metody, która przyjmuje **startRecord** i **maxRecords** parametrów, Zwiększ bieżący indeks rekordu przez rozmiar strony i wypełnienia tabeli. Należy pamiętać, że serwer bazy danych zwraca wyniki zapytania całego, mimo że tylko jedna strona rekordów jest dodawany do **zestawu danych**. W poniższym przykładzie kodu wiersze tabeli zostaną wyczyszczone, zanim są wypełnione następnej strony danych. Być może chcesz zachować niektórych liczba zwracanych wierszy w lokalnej pamięci podręcznej, aby zmniejszyć do serwera bazy danych.  
  
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
  
 Aby przywrócić następnej strony rekordów bez serwera bazy danych, zwraca całe zapytanie, określ kryteria ograniczające instrukcji SELECT. Ponieważ poprzedni przykład zachowywane ostatni rekord zwracane, można użyć go w klauzuli WHERE, aby określić punkt początkowy dla zapytania, jak pokazano w poniższym przykładzie kodu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
