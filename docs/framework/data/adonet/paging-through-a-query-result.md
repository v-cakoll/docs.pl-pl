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
# <a name="paging-through-a-query-result"></a><span data-ttu-id="1119a-102">Stronicowanie za pośrednictwem wyniku zapytania</span><span class="sxs-lookup"><span data-stu-id="1119a-102">Paging Through a Query Result</span></span>
<span data-ttu-id="1119a-103">Stronicowanie za pośrednictwem wyniku kwerendy jest procesem zwracania wyników kwerendy w mniejszych podzbiorach danych lub stron.</span><span class="sxs-lookup"><span data-stu-id="1119a-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="1119a-104">Jest to powszechna praktyka wyświetlania wyników użytkownikowi w małych, łatwych w zarządzaniu fragmentów.</span><span class="sxs-lookup"><span data-stu-id="1119a-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="1119a-105">**DataAdapter** zapewnia możliwość zwracania tylko strony danych, za pośrednictwem przeciążenia **Fill** metody.</span><span class="sxs-lookup"><span data-stu-id="1119a-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="1119a-106">Jednak może to nie być najlepszym wyborem dla stronicowania za pośrednictwem wyników dużych <xref:System.Data.DataTable> <xref:System.Data.DataSet> kwerend, ponieważ mimo **dataAdapter** wypełnia miejsce docelowe lub tylko żądane rekordy, zasoby do zwrócenia całej kwerendy są nadal używane.</span><span class="sxs-lookup"><span data-stu-id="1119a-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="1119a-107">Aby zwrócić stronę danych ze źródła danych bez użycia zasobów do zwrócenia całej kwerendy, należy określić dodatkowe kryteria dla kwerendy, które zmniejszają wiersze zwracane tylko do tych wymaganych.</span><span class="sxs-lookup"><span data-stu-id="1119a-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="1119a-108">Aby użyć **Fill** metody zwracać stronę danych, należy określić **startRecord** parametru dla pierwszego rekordu na stronie danych i **maxRecords** parametr, dla liczby rekordów na stronie danych.</span><span class="sxs-lookup"><span data-stu-id="1119a-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="1119a-109">Poniższy przykład kodu pokazuje, jak użyć **Fill** metody zwracania pierwszej strony wynik kwerendy, gdzie rozmiar strony jest pięć rekordów.</span><span class="sxs-lookup"><span data-stu-id="1119a-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="1119a-110">W poprzednim przykładzie **Zestaw danych** jest wypełniony tylko pięcioma rekordami, ale zwracana jest cała **tabela Zamówienia.**</span><span class="sxs-lookup"><span data-stu-id="1119a-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="1119a-111">Aby wypełnić **Zestaw danych** tymi samymi pięcioma rekordami, ale zwracaj tylko pięć rekordów, użyj klauzul TOP i WHERE w instrukcji SQL, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1119a-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="1119a-112">Należy zauważyć, że podczas stronicowania za pośrednictwem wyników kwerendy w ten sposób, należy zachować unikatowy identyfikator, który zamawia wiersze, w celu przekazania unikatowego identyfikatora do polecenia, aby zwrócić następną stronę rekordów, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1119a-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="1119a-113">Aby zwrócić następną stronę rekordów przy użyciu przeciążenia **Fill** metody, która przyjmuje **startRecord** i **maxRecords** parametry, przyrost bieżącego indeksu rekordu o rozmiar strony i wypełnić tabelę.</span><span class="sxs-lookup"><span data-stu-id="1119a-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="1119a-114">Należy pamiętać, że serwer bazy danych zwraca wyniki całej kwerendy, nawet jeśli tylko jedna strona rekordów jest dodawana do **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="1119a-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="1119a-115">W poniższym przykładzie kodu wiersze tabeli są czyszczone przed ich wypełnieniem następnej strony danych.</span><span class="sxs-lookup"><span data-stu-id="1119a-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="1119a-116">Można zachować pewną liczbę zwróconych wierszy w lokalnej pamięci podręcznej, aby zmniejszyć liczbę podróży do serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="1119a-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="1119a-117">Aby zwrócić następną stronę rekordów bez zwracania całej kwerendy przez serwer bazy danych, należy określić restrykcyjne kryteria instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="1119a-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="1119a-118">Ponieważ w poprzednim przykładzie zachowane ostatni rekord zwrócony, można go użyć w klauzuli WHERE, aby określić punkt początkowy dla kwerendy, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1119a-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1119a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1119a-119">See also</span></span>

- [<span data-ttu-id="1119a-120">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="1119a-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="1119a-121">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1119a-121">ADO.NET Overview</span></span>](ado-net-overview.md)
