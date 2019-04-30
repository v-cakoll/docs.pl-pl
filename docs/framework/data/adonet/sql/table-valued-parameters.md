---
title: Parametry o wartościach tabelowych
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: d1d52e048ee54ce967215ad134d5bcff2983103e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758083"
---
# <a name="table-valued-parameters"></a>Parametry o wartościach tabelowych
Parametry z wartościami przechowywanymi w tabeli zawierają łatwy sposób organizowania wielu wierszy danych z aplikacji klienckiej programu SQL Server, bez konieczności wielu wystąpień komunikacji dwustronnej lub specjalne logiki po stronie serwera związane z przetwarzaniem danych. Parametry z wartościami przechowywanymi w tabeli można użyć do hermetyzacji wierszy danych w aplikacji klienckiej i wysyłania danych do serwera za pomocą jednego polecenia sparametryzowanych. Przychodzące wiersze danych są przechowywane w zmiennej tabeli, która może być eksploatowana przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].  
  
 Wartości parametrów z wartościami przechowywanymi w tabeli kolumn można uzyskać dostęp przy użyciu standardu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji "SELECT". Parametry z wartościami przechowywanymi w tabeli są silnie typizowane i ich struktury jest automatycznie weryfikowana. Rozmiar parametrów z wartościami przechowywanymi w tabeli jest ograniczony tylko ilością pamięci serwera.  
  
> [!NOTE]
>  Parametr z wartościami przechowywanymi w tabeli nie może zwrócić danych. Parametry z wartościami przechowywanymi w tabeli są tylko wejściowym; dane wyjściowe — słowo kluczowe nie jest obsługiwane.  
  
 Aby uzyskać więcej informacji na temat parametrów z wartościami przechowywanymi w tabeli zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Parametry z wartościami przechowywanymi w tabeli (aparat bazy danych)](https://go.microsoft.com/fwlink/?LinkId=98363) w SQL Server — książki Online|W tym artykule opisano sposób tworzenia i używania parametrów z wartościami przechowywanymi w tabeli.|  
|[Typy tabel zdefiniowane przez użytkownika](https://go.microsoft.com/fwlink/?LinkId=98364) w SQL Server — książki Online|W tym artykule opisano typy tabel zdefiniowane przez użytkownika, które są używane do deklarowania parametry z wartościami przechowywanymi w tabeli.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Przekazywanie wielu wierszy w poprzednich wersjach programu SQL Server  
 Zanim parametry z wartościami przechowywanymi w tabeli zostały wprowadzone do programu SQL Server 2008, opcji przekazywania wielu wierszy danych do procedury składowanej lub sparametryzowanego polecenia SQL były ograniczone. Deweloper może wybrać spośród następujących opcji przekazywania wiele wierszy do serwera:  
  
- Użyj szereg poszczególne parametry do reprezentowania wartości w wielu kolumn i wierszy danych. Ilość danych, który może być przekazywany przy użyciu tej metody jest ograniczona przez liczbę parametry są niedozwolone. Procedury programu SQL Server może mieć co najwyżej 2100 parametrów. Logiki po stronie serwera jest wymagany do budowania tych poszczególne wartości do zmiennej tabeli lub tabeli tymczasowej do przetworzenia.  
  
- Pakietu wiele wartości danych do ciągów rozdzielanych lub dokumentów XML, a następnie przekazać te wartości tekstowych do procedury lub instrukcji. Wymaga to procedury lub instrukcję, aby uwzględnić logikę niezbędną do zweryfikowania struktur danych oraz wydzielenie wartości.  
  
- Utwórz serie pojedyncze instrukcje SQL dla modyfikacji danych, które wpływają na wiele wierszy, takich jak te utworzone przez wywołanie metody `Update` metody <xref:System.Data.SqlClient.SqlDataAdapter>. Zmiany można przesłać na serwer indywidualnie lub partii w grupy. Jednak nawet wtedy, gdy przesyłany w partiach, które zawierają wiele instrukcji, każda instrukcja jest wykonywana oddzielnie na serwerze.  
  
- Użyj `bcp` programu narzędziowego lub <xref:System.Data.SqlClient.SqlBulkCopy> obiekt, aby załadować wiele wierszy danych do tabeli. Chociaż ta technika jest bardzo wydajny, nie obsługuje przetwarzania po stronie serwera, chyba, że dane są ładowane do tabeli tymczasowej lub zmiennej tabeli.  
  
## <a name="creating-table-valued-parameter-types"></a>Tworzenie typów parametru z wartościami przechowywanymi w tabeli  
 Parametry z wartościami przechowywanymi w tabeli zależą od struktury silnie typizowane tabel, które są zdefiniowane przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji CREATE TYPE. Masz typ tabeli na utworzenie i zdefiniowanie struktury w programie SQL Server, zanim użyjesz parametry z wartościami przechowywanymi w tabeli w aplikacjach klienckich. Aby uzyskać więcej informacji na temat tworzenia użytkownika, typach tabel zobacz [typy tabel zdefiniowane przez użytkownika](https://go.microsoft.com/fwlink/?LinkID=98364) w dokumentacji SQL Server — książki Online.  
  
 Poniższa instrukcja umożliwia utworzenie tabeli o nazwie CategoryTableType, który składa się z identyfikatorem kategorii i CategoryName kolumn:  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Po utworzeniu tabeli, możesz deklarować parametry z wartościami przechowywanymi w tabeli na podstawie tego typu. Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment przedstawia sposób deklarowania parametrem z wartościami przechowywanymi w tabeli, w definicji procedury składowanej. Należy pamiętać, że READONLY — słowo kluczowe jest wymagany do deklarowania parametr z wartościami przechowywanymi w tabeli.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modyfikowanie danych za pomocą parametrów z wartościami przechowywanymi w tabeli (Transact-SQL)  
 Parametry z wartościami przechowywanymi w tabeli może służyć w zmiany na podstawie zestawu danych, które mają wpływ na wiele wierszy, wykonując pojedynczej instrukcji. Na przykład można wybrać wszystkie wiersze w parametr z wartościami przechowywanymi w tabeli i wstawianie tabeli bazy danych lub można utworzyć instrukcji update, dołączając do parametru z wartościami przechowywanymi w tabeli do tabeli, które chcesz zaktualizować.  
  
 Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji UPDATE pokazuje sposób użycia parametru z wartościami przechowywanymi w tabeli przez dołączenie go do tabeli Kategorie. Korzystając z parametru z wartościami przechowywanymi w tabeli ze sprzężeniem w klauzuli FROM, musisz mieć również aliasu, jak pokazano w tym miejscu, gdzie parametr z wartościami przechowywanymi w tabeli ma alias "WE":  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 To [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] przykład pokazuje, jak w celu wybrania wierszy z wartościami przechowywanymi w tabeli parametru przeprowadzić WSTAWIANIA w ramach jednej operacji na podstawie zestawu.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Ograniczenia dotyczące parametrów z wartościami przechowywanymi w tabeli  
 Istnieje również kilka ograniczeń do parametrów z wartościami przechowywanymi w tabeli:  
  
- Nie można przekazać parametry wartościami przechowywanymi w tabeli [funkcje zdefiniowane przez użytkownika CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).  
  
- Parametry z wartościami przechowywanymi w tabeli mogą być indeksowane tylko do obsługi ograniczenia UNIQUE i PRIMARY KEY. Program SQL Server nie są zachowywane dane statystyczne dotyczące parametrów z wartościami przechowywanymi w tabeli.  
  
- Parametry z wartościami przechowywanymi w tabeli są tylko do odczytu w [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kodu. Nie można zaktualizować wartości w kolumnach w wierszach parametr z wartościami przechowywanymi w tabeli i nie można wstawić lub usuwania wierszy. Aby zmodyfikować danych, który jest przekazywany do procedury składowanej lub sparametryzowanych instrukcji w parametr z wartościami przechowywanymi w tabeli, należy wstawić dane do tabeli tymczasowej lub zmiennej tabeli.  
  
- Nie można użyć instrukcji ALTER TABLE, aby zmodyfikować projekt parametrów z wartościami przechowywanymi w tabeli.  
  
## <a name="configuring-a-sqlparameter-example"></a>Konfigurowanie przykładzie parametr SqlParameter  
 <xref:System.Data.SqlClient> obsługuje wypełniania wartościami przechowywanymi w tabeli Parametry z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> lub <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> obiektów. Należy określić nazwę typu dla parametru z wartościami przechowywanymi w tabeli, używając <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwość <xref:System.Data.SqlClient.SqlParameter>. `TypeName` Musi pasować do nazwy zgodne z typem wcześniej utworzony na serwerze. Poniższy fragment kodu pokazuje, jak skonfigurować <xref:System.Data.SqlClient.SqlParameter> wstawiania danych.  
 
W poniższym przykładzie `addedCategories` zmienna zawiera <xref:System.Data.DataTable>. Aby dowiedzieć się, jak zmienna jest wypełniana, zobacz przykłady w następnej sekcji [przekazywania parametru Table-Valued do procedury składowanej](#passing).

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 Można również użyć dowolnego obiektu pochodzącego z <xref:System.Data.Common.DbDataReader> do wierszy strumień danych do parametru wartościami przechowywanymi w tabeli, jak pokazano w tym fragmencie:  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing"></a> Przekazywanie parametru z wartościami przechowywanymi w tabeli do procedury składowanej  
 W tym przykładzie pokazano, jak przekazać parametr z wartościami przechowywanymi w tabeli dane do procedury składowanej. Kod wyodrębnia dodanymi wierszami w nowym <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTable.GetChanges%2A> metody. W kodzie następnie zdefiniowano <xref:System.Data.SqlClient.SqlCommand>, ustawiając <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> właściwość <xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlParameter> Jest wypełniana przy użyciu <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metody i <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ustawiono `Structured`. <xref:System.Data.SqlClient.SqlCommand> Są następnie wykonywane za pomocą <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Przekazywanie parametru z wartościami przechowywanymi w tabeli do instrukcji SQL — sparametryzowane  
 Poniższy przykład pokazuje, jak wstawić dane do dbo. Tabela kategorie za pomocą instrukcji INSERT podzapytania SELECT, która ma parametr z wartościami przechowywanymi w tabeli jako źródła danych. Podczas przekazywania parametru z wartościami przechowywanymi w tabeli do sparametryzowanych instrukcji SQL, należy określić nazwę typu dla parametru z wartościami przechowywanymi w tabeli za pomocą nowego <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwość <xref:System.Data.SqlClient.SqlParameter>. To `TypeName` musi pasować do nazwy zgodne z typem wcześniej utworzony na serwerze. W kodzie, w tym przykładzie użyto `TypeName` właściwości w celu odwołania struktury typ zdefiniowany w dbo. CategoryTableType.  
  
> [!NOTE]
>  Jeśli podana wartość dla kolumny tożsamości w parametr z wartościami przechowywanymi w tabeli, należy wygenerować instrukcji USTAWIONY atrybut IDENTITY_INSERT dla sesji.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a>Wiersze przesyłania strumieniowego przy użyciu elementu DataReader  
 Można również użyć dowolnego obiektu pochodzącego z <xref:System.Data.Common.DbDataReader> do wierszy strumień danych do parametru z wartościami przechowywanymi w tabeli. Poniższy fragment kodu przedstawia pobieranie danych z bazy danych Oracle przy użyciu <xref:System.Data.OracleClient.OracleCommand> i <xref:System.Data.OracleClient.OracleDataReader>. Kod następnie konfiguruje <xref:System.Data.SqlClient.SqlCommand> do wywołania procedury składowanej z jednego parametru wejściowego. <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Właściwość <xref:System.Data.SqlClient.SqlParameter> ustawiono `Structured`. <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Przekazuje `OracleDataReader` zestawu wyników procedury składowanej jako parametr z wartościami przechowywanymi w tabeli.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Polecenia i parametry](../../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Parametry elementu DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [Operacje danych serwera SQL w ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
