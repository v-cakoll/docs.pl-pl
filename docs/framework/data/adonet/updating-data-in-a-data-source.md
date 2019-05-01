---
title: Aktualizowanie danych w źródle danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: a12fa587d5df0ed95dd0f15ccfbe2ef886185b9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934124"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="2b797-102">Aktualizowanie danych w źródle danych</span><span class="sxs-lookup"><span data-stu-id="2b797-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="2b797-103">Instrukcje SQL, które modyfikują dane (takie jak INSERT, UPDATE lub DELETE) zwraca wiersze.</span><span class="sxs-lookup"><span data-stu-id="2b797-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="2b797-104">Podobnie wiele procedur składowanych wykonaj akcję, ale nie zwracać wiersze.</span><span class="sxs-lookup"><span data-stu-id="2b797-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="2b797-105">Do wykonywania poleceń, które nie zwrócą wierszy, należy utworzyć **polecenia** obiektu za pomocą odpowiedniego polecenia SQL i **połączenia**, wraz ze wszystkimi wymagane **parametry**.</span><span class="sxs-lookup"><span data-stu-id="2b797-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="2b797-106">Wykonanie polecenia za pomocą **ExecuteNonQuery** metody **polecenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="2b797-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="2b797-107">**ExecuteNonQuery** metoda zwraca wartość całkowitą reprezentującą liczbę wierszy objętych instrukcji lub procedury składowanej, który został wykonany.</span><span class="sxs-lookup"><span data-stu-id="2b797-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="2b797-108">Jeśli są wykonywane wiele instrukcji, wartość zwracana jest sumą zmodyfikowanych przez wszystkie instrukcje wykonywane rekordów.</span><span class="sxs-lookup"><span data-stu-id="2b797-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b797-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b797-109">Example</span></span>  
 <span data-ttu-id="2b797-110">Poniższy kod wykonuje instrukcję INSERT, do wstawienia rekordu do bazy danych za pomocą **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="2b797-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 <span data-ttu-id="2b797-111">Poniższy kod wykonuje procedurę składowaną, utworzone przez przykładowy kod [wykonywanie operacji katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2b797-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span></span> <span data-ttu-id="2b797-112">Nie zwrócono żadnych wierszy przez procedurę składowaną, więc **ExecuteNonQuery** używana jest metoda, ale procedura składowana odbierania parametr wejściowy i zwraca parametr wyjściowy i wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="2b797-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="2b797-113">Dla <xref:System.Data.OleDb.OleDbCommand> obiektu **ReturnValue** parametr musi zostać dodany do **parametry** kolekcji pierwszy.</span><span class="sxs-lookup"><span data-stu-id="2b797-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b797-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b797-114">See also</span></span>

- [<span data-ttu-id="2b797-115">Używanie poleceń do modyfikacji danych</span><span class="sxs-lookup"><span data-stu-id="2b797-115">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [<span data-ttu-id="2b797-116">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="2b797-116">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="2b797-117">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="2b797-117">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="2b797-118">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2b797-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
