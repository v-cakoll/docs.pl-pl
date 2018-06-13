---
title: Aktualizowanie danych w źródle danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 11c3faa85d6d0b77c4e606815aa8252188b6f67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357796"
---
# <a name="updating-data-in-a-data-source"></a>Aktualizowanie danych w źródle danych
Instrukcje SQL, które modyfikują dane (takie jak INSERT, UPDATE lub DELETE) zwraca wiersze. Podobnie wiele procedur składowanych wykonywania akcji, ale nie zwraca wiersze. Do wykonania polecenia, które niezwracanie wierszy, Utwórz **polecenia** obiektu za pomocą odpowiedniego polecenia SQL i **połączenia**, wraz ze wszystkimi wymagane **parametry**. Wykonaj polecenie z **ExecuteNonQuery** metody **polecenia** obiektu.  
  
 **ExecuteNonQuery** metoda zwraca liczbę całkowitą reprezentującą liczbę wierszy instrukcji lub procedury przechowywanej, która została wykonana. Jeśli wiele instrukcji są wykonywane, wartość zwracana jest sumą zmodyfikowanych przez wszystkie instrukcje wykonywane rekordów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykonuje instrukcję do wstawienia rekordu do bazy danych przy użyciu **ExecuteNonQuery**.  
  
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
  
 Poniższy przykład kodu wykonuje procedurę składowaną utworzone przez przykładowy kod [wykonywanie operacji katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md). Żadne wiersze są zwracane przez procedurę składowaną, więc **ExecuteNonQuery** metoda jest używana, ale procedury składowanej odbierania parametr wejściowy i zwraca parametr wyjściowy i wartości zwracanej.  
  
 Dla <xref:System.Data.OleDb.OleDbCommand> obiektu **ReturnValue** parametr musi zostać dodany do **parametry** kolekcji pierwszej.  
  
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
 [Używanie poleceń do modyfikacji danych](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
