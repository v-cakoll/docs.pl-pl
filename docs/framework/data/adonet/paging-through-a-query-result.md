---
title: Stronicowanie wyników zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 11bf7e1021c3bb65e4d736e83d2631ae05c274f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630427"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="cff41-102">Stronicowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="cff41-102">Paging Through a Query Result</span></span>
<span data-ttu-id="cff41-103">Stronicowanie za pośrednictwem wyników z zapytania jest proces zwracania wyników zapytania w mniejszy podzbiór danych lub strony.</span><span class="sxs-lookup"><span data-stu-id="cff41-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="cff41-104">Jest to powszechną praktyką do wyświetlania wyników użytkownikowi we fragmentach małe, łatwy w zarządzaniu.</span><span class="sxs-lookup"><span data-stu-id="cff41-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="cff41-105">**DataAdapter** przewiduje zwracanie tylko strony danych za pomocą przeciążenia funkcji **wypełnienia** metody.</span><span class="sxs-lookup"><span data-stu-id="cff41-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="cff41-106">Jednak może to nie być najlepszym wyborem dla stronicowanie wyników dużych zapytania, ponieważ mimo że **DataAdapter** wypełnia obiekt docelowy <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> tylko żądane rekordy zasobów do zwrócenia całe zapytanie są nadal używane.</span><span class="sxs-lookup"><span data-stu-id="cff41-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="cff41-107">Aby przywrócić strony danych ze źródła danych bez użycia zasobów, aby zwrócić całe zapytanie, określić dodatkowe kryteria dla zapytania, które zmniejszają wierszy zwracanych do tylko wymaganych.</span><span class="sxs-lookup"><span data-stu-id="cff41-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="cff41-108">Aby użyć **wypełnienia** Określ metodę, aby powrócić do strony danych, **startRecord** parametr dla pierwszego rekordu w strony danych i **maxRecords** parametru, liczby rekordy w strony danych.</span><span class="sxs-lookup"><span data-stu-id="cff41-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="cff41-109">Poniższy przykład kodu pokazuje sposób użycia **wypełnienia** metodę do zwracania pierwszej strony wyników zapytania, których rozmiar strony jest pięć rekordów.</span><span class="sxs-lookup"><span data-stu-id="cff41-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="cff41-110">W poprzednim przykładzie **DataSet** tylko wypełnionej pięć rekordów, ale cały **zamówienia** zwracana jest tabela.</span><span class="sxs-lookup"><span data-stu-id="cff41-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="cff41-111">Aby wypełnić **DataSet** przy użyciu tych samych pięciu rekordy, ale zwrócić tylko pięć rekordów, użyj GÓRNEJ i klauzulach WHERE w instrukcji SQL, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="cff41-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="cff41-112">Należy pamiętać, że gdy stronicowanie wyników zapytania w ten sposób, należy zachować Unikatowy identyfikator, która porządkuje wierszy, aby można było przekazać Unikatowy identyfikator polecenia do zwrócenia na następnej stronie rekordy, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="cff41-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="cff41-113">Aby powrócić do następnej strony rekordów za pomocą przeciążenia **wypełnienia** metody, która przyjmuje **startRecord** i **maxRecords** parametrów, Zwiększ bieżący indeks rekordu przez rozmiar strony i wypełnienia tabeli.</span><span class="sxs-lookup"><span data-stu-id="cff41-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="cff41-114">Należy pamiętać, że serwer bazy danych zwraca wyniki zapytania całego, mimo że tylko jedna strona rekordów jest dodawany do **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="cff41-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="cff41-115">W poniższym przykładzie kodu wiersze tabeli zostaną wyczyszczone, zanim są wypełnione następnej strony danych.</span><span class="sxs-lookup"><span data-stu-id="cff41-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="cff41-116">Być może chcesz zachować niektórych liczba zwracanych wierszy w lokalnej pamięci podręcznej, aby zmniejszyć do serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cff41-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="cff41-117">Aby przywrócić następnej strony rekordów bez serwera bazy danych, zwraca całe zapytanie, określ kryteria ograniczające instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="cff41-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="cff41-118">Ponieważ poprzedni przykład zachowywane ostatni rekord zwracane, można użyć go w klauzuli WHERE, aby określić punkt początkowy dla zapytania, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="cff41-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cff41-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cff41-119">See also</span></span>
- [<span data-ttu-id="cff41-120">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="cff41-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="cff41-121">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="cff41-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
