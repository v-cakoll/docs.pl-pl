---
title: Aktualizowanie danych w źródle danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 0926e3c6513a698ae47b9983d0e6ad195394a4df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780613"
---
# <a name="updating-data-in-a-data-source"></a>Aktualizowanie danych w źródle danych
Instrukcje SQL, które modyfikują dane (takie jak INSERT, UPDATE lub DELETE) nie zwracają wierszy. Podobnie wiele procedur składowanych wykonuje akcję, ale nie zwraca wierszy. Aby wykonać polecenia, które nie zwracają wierszy, Utwórz obiekt **polecenia** z odpowiednim poleceniem SQL i **połączeniem**, włącznie z wymaganymi **parametrami**. Wykonaj polecenie za pomocą metody **ExecuteNonQuery** obiektu **Command** .  
  
 Metoda **ExecuteNonQuery** zwraca liczbę całkowitą, która odpowiada liczbie wierszy objętych instrukcją lub procedury składowanej, która została wykonana. W przypadku wykonywania wielu instrukcji zwracana wartość jest sumą rekordów, których dotyczą wszystkie wykonane instrukcje.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykonuje instrukcję INSERT, aby wstawić rekord do bazy danych przy użyciu **ExecuteNonQuery**.  
  
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
  
 Poniższy przykład kodu wykonuje procedurę przechowywaną utworzoną przez przykładowy kod podczas [wykonywania operacji katalogu](performing-catalog-operations.md). Procedura składowana nie zwraca żadnych wierszy, więc metoda **ExecuteNonQuery** jest używana, ale procedura składowana otrzymuje parametr wejściowy i zwraca parametr wyjściowy oraz wartość zwracaną.  
  
 Dla obiektu należy najpierw dodać parametr **ReturnValue** do kolekcji **Parameters.** <xref:System.Data.OleDb.OleDbCommand>  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Używanie poleceń do modyfikacji danych](using-commands-to-modify-data.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](updating-data-sources-with-dataadapters.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Omówienie ADO.NET](ado-net-overview.md)
