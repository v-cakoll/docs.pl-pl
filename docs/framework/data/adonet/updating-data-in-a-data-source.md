---
title: Aktualizowanie danych w źródle danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 18bb03e17b19243ee1bc6e3f7ebd70afb4d4c60b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174449"
---
# <a name="updating-data-in-a-data-source"></a>Aktualizowanie danych w źródle danych
Instrukcje SQL modyfikując dane (takie jak INSERT, UPDATE lub DELETE) nie zwracają wierszy. Podobnie wiele procedur przechowywanych wykonać akcję, ale nie zwracają wierszy. Aby wykonać polecenia, które nie zwracają wierszy, należy utworzyć obiekt **Command** z odpowiednim poleceniem SQL i **połączeniem**, w tym wszelkie wymagane **parametry**. Wykonaj polecenie metodą **ExecuteNonQuery** obiektu **Command.**  
  
 **ExecuteNonQuery** Metoda zwraca liczbę całkowitą, która reprezentuje liczbę wierszy, których dotyczy instrukcja lub procedura składowana, która została wykonana. Jeśli wiele instrukcji są wykonywane, zwracana wartość jest sumą rekordów, których dotyczą wszystkie instrukcje wykonane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykonuje instrukcję INSERT, aby wstawić rekord do bazy danych przy użyciu **executenonquery**.  
  
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
  
 Poniższy przykład kodu wykonuje procedurę składowaną utworzoną przez przykładowy kod w [wykonywaniu operacji wykazu](performing-catalog-operations.md). Żadne wiersze nie są zwracane przez procedurę składowaną, więc **ExecuteNonQuery** metoda jest używana, ale procedura składowana odbiera parametr wejściowy i zwraca parametr wyjściowy i wartość zwracaną.  
  
 Dla <xref:System.Data.OleDb.OleDbCommand> obiektu **ReturnValue** parametr musi zostać dodany do **parameters** kolekcji pierwszy.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Używanie poleceń do modyfikacji danych](using-commands-to-modify-data.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapter](updating-data-sources-with-dataadapters.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Omówienie ADO.NET](ado-net-overview.md)
