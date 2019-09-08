---
title: Stronicowanie za pośrednictwem wyniku zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 1dbaa159314bf7bb05ff75287f601f619834fd7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794611"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="339a4-102">Stronicowanie za pośrednictwem wyniku zapytania</span><span class="sxs-lookup"><span data-stu-id="339a4-102">Paging Through a Query Result</span></span>
<span data-ttu-id="339a4-103">Stronicowanie za pomocą wyniku zapytania jest procesem zwracającym wyniki zapytania w mniejszych podzestawach danych lub stronach.</span><span class="sxs-lookup"><span data-stu-id="339a4-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="339a4-104">Jest to typowa metoda wyświetlania wyników dla użytkownika w małych i łatwych do zarządzania fragmentach.</span><span class="sxs-lookup"><span data-stu-id="339a4-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="339a4-105">Obiekt **DataAdapter** udostępnia funkcję do zwracania tylko strony danych, przez przeciążenia metody **Fill** .</span><span class="sxs-lookup"><span data-stu-id="339a4-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="339a4-106">Jednak może to nie być najlepszym wyborem w przypadku stronicowania za pomocą dużych wyników zapytania, ponieważ, chociaż element **DataAdapter** wypełnia <xref:System.Data.DataTable> obiekt <xref:System.Data.DataSet> docelowy lub tylko z żądanymi rekordami, zasoby, które mają zwrócić całe zapytanie, są nadal używane .</span><span class="sxs-lookup"><span data-stu-id="339a4-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="339a4-107">Aby zwrócić stronę danych ze źródła danych bez użycia zasobów do zwrócenia całego zapytania, należy określić dodatkowe kryteria dla zapytania, które zmniejszają liczbę zwracanych wierszy tylko do wymaganych.</span><span class="sxs-lookup"><span data-stu-id="339a4-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="339a4-108">Aby użyć metody **Fill** do zwrócenia strony danych, należy określić parametr **startRecord** dla pierwszego rekordu na stronie danych oraz parametr **MaxRecords** , dla liczby rekordów na stronie danych.</span><span class="sxs-lookup"><span data-stu-id="339a4-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="339a4-109">Poniższy przykład kodu pokazuje, jak używać metody **Fill** do zwrócenia pierwszej strony wyniku zapytania, gdzie rozmiar strony jest pięcioma rekordami.</span><span class="sxs-lookup"><span data-stu-id="339a4-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="339a4-110">W poprzednim przykładzie **zestaw danych** zawiera tylko pięć rekordów, ale zwracana jest cała tabela **Orders** .</span><span class="sxs-lookup"><span data-stu-id="339a4-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="339a4-111">Aby wypełnić **zestaw danych** tymi samymi pięcioma rekordami, ale zwróć tylko pięć rekordów, użyj klauzul Top i WHERE w instrukcji języka SQL, jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="339a4-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="339a4-112">Należy pamiętać, że podczas tworzenia stronicowania w wyniku zapytania w ten sposób należy zachować unikatowy identyfikator, który porządkuje wiersze, aby przekazać unikatowy identyfikator do polecenia w celu zwrócenia następnej strony rekordów, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="339a4-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="339a4-113">Aby zwrócić następną stronę rekordów przy użyciu przeciążenia metody **Fill** , która przyjmuje parametry **startRecord** i **MaxRecords** , zwiększ bieżący indeks rekordu przez rozmiar strony i wypełnij tabelę.</span><span class="sxs-lookup"><span data-stu-id="339a4-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="339a4-114">Należy pamiętać, że serwer bazy danych zwraca całe wyniki zapytania, nawet wtedy, gdy tylko jedna strona rekordów jest dodawana do **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="339a4-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="339a4-115">W poniższym przykładzie kodu wiersze tabeli są czyszczone, zanim zostaną wypełnione następną stroną danych.</span><span class="sxs-lookup"><span data-stu-id="339a4-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="339a4-116">Możesz chcieć zachować określoną liczbę zwracanych wierszy w lokalnej pamięci podręcznej, aby zredukować podróże do serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="339a4-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="339a4-117">Aby zwrócić następną stronę rekordów bez konieczności zwrócenia przez serwer bazy danych całego zapytania, określ kryteria ograniczające do instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="339a4-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="339a4-118">Ponieważ w powyższym przykładzie zachowano ostatni zwrócony rekord, można go użyć w klauzuli WHERE, aby określić punkt początkowy zapytania, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="339a4-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="339a4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="339a4-119">See also</span></span>

- [<span data-ttu-id="339a4-120">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="339a4-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="339a4-121">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="339a4-121">ADO.NET Overview</span></span>](ado-net-overview.md)
