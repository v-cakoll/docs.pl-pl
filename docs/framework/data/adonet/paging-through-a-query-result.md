---
title: "Stronicowanie za pośrednictwem wyników z kwerendy"
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
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 506458eab146614f505a5558cd3535f06aecb83c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="59a1d-102">Stronicowanie za pośrednictwem wyników z kwerendy</span><span class="sxs-lookup"><span data-stu-id="59a1d-102">Paging Through a Query Result</span></span>
<span data-ttu-id="59a1d-103">Stronicowanie za pośrednictwem wyników z kwerendy jest proces zwracania wyników zapytania w mniejszych podzbiór danych lub strony.</span><span class="sxs-lookup"><span data-stu-id="59a1d-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="59a1d-104">To jest typowym rozwiązaniem do wyświetlania wyników z kontem użytkownika w małych, łatwe w zarządzaniu fragmentów.</span><span class="sxs-lookup"><span data-stu-id="59a1d-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="59a1d-105">**Element DataAdapter** zwracanie tylko strony danych za pomocą przeciążenia metody zawiera obiekt **wypełnienia** metody.</span><span class="sxs-lookup"><span data-stu-id="59a1d-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="59a1d-106">Jednak może to nie być najlepszym wyborem umożliwiającym stronicowania za pośrednictwem wyników zapytania duża, ponieważ mimo że **element DataAdapter** wypełnia obiekt docelowy <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> tylko gdy żądane rekordy, zasoby do zwrócenia cała kwerenda są nadal używane.</span><span class="sxs-lookup"><span data-stu-id="59a1d-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="59a1d-107">Aby przywrócić strony danych ze źródła danych bez użycia zasobów do zwrócenia całego zapytania, należy określić dodatkowe kryteria zapytania, zmniejszających wierszy zwracanych tylko wymaganych.</span><span class="sxs-lookup"><span data-stu-id="59a1d-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="59a1d-108">Do użycia **wypełnienia** Określ metodę, aby powrócić do strony danych, **elementu startRecord** parametr pierwszy rekord na stronie danych, a **maxRecords** parametru liczby rekordy w strony danych.</span><span class="sxs-lookup"><span data-stu-id="59a1d-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="59a1d-109">Poniższy przykładowy kod przedstawia sposób użycia **wypełnienia** metody do zwrócenia na pierwszej stronie w wyniku zapytania, gdy rozmiar strony jest pięć rekordów.</span><span class="sxs-lookup"><span data-stu-id="59a1d-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="59a1d-110">W poprzednim przykładzie **DataSet** tylko wypełnionej pięć rekordy, ale cały **zamówień** zwracana jest tabela.</span><span class="sxs-lookup"><span data-stu-id="59a1d-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="59a1d-111">Aby wypełnić **DataSet** z tego samego pięć rekordy, ale zwrócić tylko pięć rekordów, użyj GÓRNEJ i klauzulach WHERE w instrukcji SQL, tak jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="59a1d-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="59a1d-112">Należy pamiętać, że podczas stronicowania wyników kwerendy w ten sposób, można zachować Unikatowy identyfikator, który porządkuje wiersze, aby przekazać do polecenia, aby zwrócić następnej strony rekordów, unikatowy identyfikator, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="59a1d-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="59a1d-113">Aby powrócić do następnej strony rekordów za pomocą przeciążenia **wypełnienia** metody pobierającej **elementu startRecord** i **maxRecords** parametrów, zwiększyć bieżącego indeksu rekordu przez rozmiar strony i wypełnienia tabeli.</span><span class="sxs-lookup"><span data-stu-id="59a1d-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="59a1d-114">Należy pamiętać, że serwer bazy danych zwraca wyniki zapytania całego, mimo że tylko jedna strona rekordów jest dodawany do **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="59a1d-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="59a1d-115">W poniższym przykładzie kodu wiersze tabeli zostaną wyczyszczone przed są wypełniane następnej strony danych.</span><span class="sxs-lookup"><span data-stu-id="59a1d-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="59a1d-116">Możesz zachować określonej liczby wierszy zwracanych w lokalnej pamięci podręcznej w celu ograniczenia komunikacji dwustronnej z serwerem bazy danych.</span><span class="sxs-lookup"><span data-stu-id="59a1d-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="59a1d-117">Aby powrócić na następnej stronie rekordy nie zwracać zapytanie cały serwer bazy danych, określ kryteria ograniczające instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="59a1d-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="59a1d-118">Ponieważ poprzednim przykładzie zachowywane ostatni rekord zwrócony, można go w klauzuli WHERE, aby określić punkt początkowy dla zapytania, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="59a1d-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59a1d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59a1d-119">See Also</span></span>  
 [<span data-ttu-id="59a1d-120">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="59a1d-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="59a1d-121">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="59a1d-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
