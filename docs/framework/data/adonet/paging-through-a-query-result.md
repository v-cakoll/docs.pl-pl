---
title: Stronicowanie za pośrednictwem wyników z kwerendy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 73475f8521b4112929339cc7f1116e36ffebedb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358971"
---
# <a name="paging-through-a-query-result"></a>Stronicowanie za pośrednictwem wyników z kwerendy
Stronicowanie za pośrednictwem wyników z kwerendy jest proces zwracania wyników zapytania w mniejszych podzbiór danych lub strony. To jest typowym rozwiązaniem do wyświetlania wyników z kontem użytkownika w małych, łatwe w zarządzaniu fragmentów.  
  
 **Element DataAdapter** zwracanie tylko strony danych za pomocą przeciążenia metody zawiera obiekt **wypełnienia** metody. Jednak może to nie być najlepszym wyborem umożliwiającym stronicowania za pośrednictwem wyników zapytania duża, ponieważ mimo że **element DataAdapter** wypełnia obiekt docelowy <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> tylko gdy żądane rekordy, zasoby do zwrócenia cała kwerenda są nadal używane. Aby przywrócić strony danych ze źródła danych bez użycia zasobów do zwrócenia całego zapytania, należy określić dodatkowe kryteria zapytania, zmniejszających wierszy zwracanych tylko wymaganych.  
  
 Do użycia **wypełnienia** Określ metodę, aby powrócić do strony danych, **elementu startRecord** parametr pierwszy rekord na stronie danych, a **maxRecords** parametru liczby rekordy w strony danych.  
  
 Poniższy przykładowy kod przedstawia sposób użycia **wypełnienia** metody do zwrócenia na pierwszej stronie w wyniku zapytania, gdy rozmiar strony jest pięć rekordów.  
  
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
  
 W poprzednim przykładzie **DataSet** tylko wypełnionej pięć rekordy, ale cały **zamówień** zwracana jest tabela. Aby wypełnić **DataSet** z tego samego pięć rekordy, ale zwrócić tylko pięć rekordów, użyj GÓRNEJ i klauzulach WHERE w instrukcji SQL, tak jak w poniższym przykładzie kodu.  
  
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
  
 Należy pamiętać, że podczas stronicowania wyników kwerendy w ten sposób, można zachować Unikatowy identyfikator, który porządkuje wiersze, aby przekazać do polecenia, aby zwrócić następnej strony rekordów, unikatowy identyfikator, jak pokazano w poniższym przykładzie kodu.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Aby powrócić do następnej strony rekordów za pomocą przeciążenia **wypełnienia** metody pobierającej **elementu startRecord** i **maxRecords** parametrów, zwiększyć bieżącego indeksu rekordu przez rozmiar strony i wypełnienia tabeli. Należy pamiętać, że serwer bazy danych zwraca wyniki zapytania całego, mimo że tylko jedna strona rekordów jest dodawany do **zestawu danych**. W poniższym przykładzie kodu wiersze tabeli zostaną wyczyszczone przed są wypełniane następnej strony danych. Możesz zachować określonej liczby wierszy zwracanych w lokalnej pamięci podręcznej w celu ograniczenia komunikacji dwustronnej z serwerem bazy danych.  
  
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
  
 Aby powrócić na następnej stronie rekordy nie zwracać zapytanie cały serwer bazy danych, określ kryteria ograniczające instrukcji SELECT. Ponieważ poprzednim przykładzie zachowywane ostatni rekord zwrócony, można go w klauzuli WHERE, aby określić punkt początkowy dla zapytania, jak pokazano w poniższym przykładzie kodu.  
  
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
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
