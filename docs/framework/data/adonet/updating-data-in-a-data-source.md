---
title: "Aktualizowanie danych w źródle danych"
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
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 91e6a5f2b956816b5e001701a7fbe4a40e7866e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="499b5-102">Aktualizowanie danych w źródle danych</span><span class="sxs-lookup"><span data-stu-id="499b5-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="499b5-103">Instrukcje SQL, które modyfikują dane (takie jak INSERT, UPDATE lub DELETE) zwraca wiersze.</span><span class="sxs-lookup"><span data-stu-id="499b5-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="499b5-104">Podobnie wiele procedur składowanych wykonywania akcji, ale nie zwraca wiersze.</span><span class="sxs-lookup"><span data-stu-id="499b5-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="499b5-105">Do wykonania polecenia, które niezwracanie wierszy, Utwórz **polecenia** obiektu za pomocą odpowiedniego polecenia SQL i **połączenia**, wraz ze wszystkimi wymagane **parametry**.</span><span class="sxs-lookup"><span data-stu-id="499b5-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="499b5-106">Wykonaj polecenie z **ExecuteNonQuery** metody **polecenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="499b5-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="499b5-107">**ExecuteNonQuery** metoda zwraca liczbę całkowitą reprezentującą liczbę wierszy instrukcji lub procedury przechowywanej, która została wykonana.</span><span class="sxs-lookup"><span data-stu-id="499b5-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="499b5-108">Jeśli wiele instrukcji są wykonywane, wartość zwracana jest sumą zmodyfikowanych przez wszystkie instrukcje wykonywane rekordów.</span><span class="sxs-lookup"><span data-stu-id="499b5-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="499b5-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="499b5-109">Example</span></span>  
 <span data-ttu-id="499b5-110">Poniższy przykład kodu wykonuje instrukcję do wstawienia rekordu do bazy danych przy użyciu **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="499b5-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="499b5-111">Poniższy przykład kodu wykonuje procedurę składowaną utworzone przez przykładowy kod [wykonywanie operacji katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="499b5-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span></span> <span data-ttu-id="499b5-112">Żadne wiersze są zwracane przez procedurę składowaną, więc **ExecuteNonQuery** metoda jest używana, ale procedury składowanej odbierania parametr wejściowy i zwraca parametr wyjściowy i wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="499b5-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="499b5-113">Dla <xref:System.Data.OleDb.OleDbCommand> obiektu **ReturnValue** parametr musi zostać dodany do **parametry** kolekcji pierwszej.</span><span class="sxs-lookup"><span data-stu-id="499b5-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="499b5-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="499b5-114">See Also</span></span>  
 [<span data-ttu-id="499b5-115">Aby zmodyfikować danych za pomocą poleceń</span><span class="sxs-lookup"><span data-stu-id="499b5-115">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="499b5-116">Aktualizowanie źródła danych za pomocą obiektów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="499b5-116">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="499b5-117">Poleceń i parametrów</span><span class="sxs-lookup"><span data-stu-id="499b5-117">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="499b5-118">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="499b5-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
