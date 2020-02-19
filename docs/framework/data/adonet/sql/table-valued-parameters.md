---
title: Parametry o wartościach tabelowych
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: d99cea1641dc61c1cae6d6b1634359211ce788ae
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452308"
---
# <a name="table-valued-parameters"></a>Parametry o wartościach tabelowych
Parametry z wartościami przechowywanymi w tabeli umożliwiają łatwe kierowanie wielu wierszy danych z aplikacji klienckiej w celu SQL Server bez konieczności wykonywania wielu operacji rundy lub specjalnej logiki po stronie serwera do przetwarzania danych. Parametry z wartościami przechowywanymi w tabeli służą do hermetyzowania wierszy danych w aplikacji klienckiej i wysyłania danych na serwer w jednym sparametryzowanym poleceniu. Przychodzące wiersze danych są przechowywane w zmiennej tabeli, która może być następnie obsługiwana przy użyciu języka Transact-SQL.  
  
 Wartości kolumn w parametrach z wartościami przechowywanymi w tabeli są dostępne za pomocą standardowych instrukcji SELECT języka Transact-SQL. Parametry z wartościami przechowywanymi w tabeli są jednoznacznie wpisane i ich struktura jest automatycznie sprawdzana. Rozmiar parametrów z wartościami przechowywanymi w tabeli jest ograniczony tylko do pamięci serwera.  
  
> [!NOTE]
> Nie można zwrócić danych w parametrze z wartościami przechowywanymi w tabeli. Parametry z wartościami przechowywanymi w tabeli są tylko danymi wejściowymi. słowo kluczowe OUTPUT nie jest obsługiwane.  
  
 Aby uzyskać więcej informacji na temat parametrów z wartościami przechowywanymi w tabeli, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Używanie parametrów z wartościami przechowywanymi w tabeli (aparat bazy danych)](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|Opisuje sposób tworzenia i używania parametrów z wartościami przechowywanymi w tabeli.|  
|[Typy tabel zdefiniowane przez użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))|Opisuje typy tabel zdefiniowane przez użytkownika, które są używane do deklarowania parametrów z wartościami przechowywanymi w tabeli.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Przekazywanie wielu wierszy w poprzednich wersjach SQL Server  
 Przed wprowadzeniem parametrów z wartościami przechowywanymi w tabeli do SQL Server 2008 opcje przekazywania wielu wierszy danych do procedury składowanej lub sparametryzowanego polecenia SQL były ograniczone. Deweloper może wybrać jedną z następujących opcji przekazywania wielu wierszy do serwera:  
  
- Użyj szeregu poszczególnych parametrów do reprezentowania wartości w wielu kolumnach i wierszach danych. Ilość danych, które mogą być przesyłane za pomocą tej metody, jest ograniczona przez liczbę dozwolonych parametrów. Procedury SQL Server mogą mieć co najwyżej 2100 parametrów. Logika po stronie serwera jest wymagana do złożenia tych pojedynczych wartości w zmiennej tabeli lub tymczasowej tabeli do przetwarzania.  
  
- Należy powiązać wiele wartości danych z rozdzielanymi ciągami lub dokumentami XML, a następnie przekazać te wartości tekstowe do procedury lub instrukcji. Wymaga to wykonania procedury lub instrukcji w celu uwzględnienia logiki niezbędnej do walidacji struktur danych i oddzielania wartości.  
  
- Utwórz serię pojedynczych instrukcji SQL na potrzeby modyfikacji danych, które mają wpływ na wiele wierszy, takich jak te utworzone przez wywołanie metody `Update` <xref:System.Data.SqlClient.SqlDataAdapter>. Zmiany mogą być przesyłane do serwera pojedynczo lub wsadowo do grup. Jednak nawet w przypadku przesyłania w partiach zawierających wiele instrukcji każda instrukcja jest wykonywana osobno na serwerze.  
  
- Użyj narzędzia `bcp` lub <xref:System.Data.SqlClient.SqlBulkCopy> obiektu do załadowania wielu wierszy danych do tabeli. Chociaż ta technika jest bardzo wydajna, nie obsługuje przetwarzania po stronie serwera, chyba że dane są ładowane do tabeli tymczasowej ani zmiennej tabeli.  
  
## <a name="creating-table-valued-parameter-types"></a>Tworzenie typów parametrów z wartościami przechowywanymi w tabeli  
 Parametry z wartościami przechowywanymi w tabeli są oparte na strukturach tabel o jednoznacznie określonym typie, które są zdefiniowane przy użyciu instrukcji CREATE TYPE języka Transact-SQL. Należy utworzyć typ tabeli i zdefiniować strukturę w SQL Server zanim będzie można używać parametrów z wartościami przechowywanymi w tabeli w aplikacjach klienckich. Aby uzyskać więcej informacji na temat tworzenia typów tabel, zobacz [Typy tabel zdefiniowane przez użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).  
  
 Poniższa instrukcja tworzy typ tabeli o nazwie CategoryTableType, która składa się z kolumn IDKategorii i CategoryName:  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Po utworzeniu typu tabeli można zadeklarować parametry z wartościami przechowywanymi w tabeli na podstawie tego typu. Poniższy fragment języka Transact-SQL pokazuje, jak zadeklarować parametr z wartościami przechowywanymi w tabeli w definicji procedury składowanej. Należy zauważyć, że słowo kluczowe READONLY jest wymagane do deklarowania parametru z wartościami przechowywanymi w tabeli.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modyfikowanie danych za pomocą parametrów z wartościami przechowywanymi w tabeli (Transact-SQL)  
 Parametry z wartościami przechowywanymi w tabeli mogą być używane w modyfikacjach danych opartych na zestawie, które wpływają na wiele wierszy przez wykonanie pojedynczej instrukcji. Można na przykład wybrać wszystkie wiersze w parametrze z wartościami przechowywanymi w tabeli i wstawić je do tabeli bazy danych. można też utworzyć instrukcję Update, dołączając parametr z wartościami przechowywanymi w tabeli do tabeli, która ma zostać zaktualizowana.  
  
 W poniższej instrukcji Transact-SQL UPDATE pokazano, jak używać parametru z wartościami przechowywanymi w tabeli przez dołączenie go do tabeli Kategorie. W przypadku używania parametru z wartościami przechowywanymi w tabeli i SPRZĘŻENIa w klauzuli FROM należy również zastosować alias, jak pokazano tutaj, gdzie parametr z wartościami przechowywanymi w tabeli jest aliasem "EC":  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 W tym przykładzie Transact-SQL pokazano, jak wybrać wiersze z parametru z wartościami przechowywanymi w tabeli, aby wykonać operację wstawiania w ramach jednej operacji opartej na zestawie.  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Ograniczenia parametrów z wartościami przechowywanymi w tabeli  
 Istnieją pewne ograniczenia dotyczące parametrów z wartościami przechowywanymi w tabeli:  
  
- Nie można przekazać parametrów z wartościami przechowywanymi w tabeli do [funkcji zdefiniowanych przez użytkownika CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).  
  
- Parametry z wartościami przechowywanymi w tabeli można indeksować tylko w celu obsługi ograniczeń UNIQUE lub PRIMARY KEY. SQL Server nie utrzymuje statystyk dotyczących parametrów z wartościami przechowywanymi w tabeli.  
  
- Parametry z wartościami przechowywanymi w tabeli są tylko do odczytu w kodzie Transact-SQL. Nie można zaktualizować wartości kolumn w wierszach parametru z wartościami przechowywanymi w tabeli i nie można wstawiać ani usuwać wierszy. Aby zmodyfikować dane, które są przesyłane do procedury składowanej lub sparametryzowanych instrukcji w parametrach z wartościami przechowywanymi w tabeli, należy wstawić dane do tabeli tymczasowej lub do zmiennej tabeli.  
  
- Nie można użyć instrukcji ALTER TABLE, aby zmodyfikować projekt parametrów z wartościami przechowywanymi w tabeli.  
  
## <a name="configuring-a-sqlparameter-example"></a>Konfigurowanie przykładu SqlParameter  
 <xref:System.Data.SqlClient> obsługuje wypełnianie parametrów z wartościami przechowywanymi w tabeli z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> lub <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> obiektów. Należy określić nazwę typu dla parametru z wartościami przechowywanymi w tabeli, używając właściwości <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter>. `TypeName` musi być zgodna z nazwą zgodnego typu, który został wcześniej utworzony na serwerze. Poniższy fragment kodu ilustruje sposób konfigurowania <xref:System.Data.SqlClient.SqlParameter> do wstawiania danych.  
 
W poniższym przykładzie zmienna `addedCategories` zawiera <xref:System.Data.DataTable>. Aby zobaczyć, jak jest wypełniana zmienna, zobacz przykłady w następnej sekcji, przekazując parametr z wartościami przechowywanymi w [tabeli do procedury składowanej](#passing).

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
  
 Można również użyć dowolnego obiektu pochodnego od <xref:System.Data.Common.DbDataReader> do przesyłania strumieniowego wierszy danych do parametru z wartościami przechowywanymi w tabeli, jak pokazano w tym fragmencie:  
  
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
  
## <a name="passing"></a>Przekazywanie parametru z wartościami przechowywanymi w tabeli do procedury składowanej  
 Ten przykład ilustruje sposób przekazywania danych parametrów z wartościami przechowywanymi w tabeli do procedury składowanej. Kod wyodrębnia dodane wiersze do nowego <xref:System.Data.DataTable> przy użyciu metody <xref:System.Data.DataTable.GetChanges%2A>. Następnie kod definiuje <xref:System.Data.SqlClient.SqlCommand>, ustawiając właściwość <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> na <xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlParameter> jest wypełniana przy użyciu metody <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> i <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> jest ustawiona na `Structured`. <xref:System.Data.SqlClient.SqlCommand> jest następnie wykonywany przy użyciu metody <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Przekazywanie parametru z wartościami przechowywanymi w tabeli do sparametryzowanej instrukcji SQL  
 W poniższym przykładzie pokazano, jak wstawić dane do dbo. Tabela kategorii za pomocą instrukcji INSERT z podzapytaniem SELECT, które ma parametr z wartościami przechowywanymi w tabeli jako źródło danych. Podczas przekazywania parametru z wartościami przechowywanymi w tabeli do sparametryzowanej instrukcji SQL należy określić nazwę typu dla parametru z wartościami przechowywanymi w tabeli przy użyciu nowej właściwości <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter>. Ta `TypeName` musi być zgodna z nazwą zgodnego typu, który został wcześniej utworzony na serwerze. Kod w tym przykładzie używa właściwości `TypeName`, aby odwołać się do struktury typu zdefiniowanej w dbo. CategoryTableType.  
  
> [!NOTE]
> W przypadku podania wartości dla kolumny tożsamości w parametrze z wartościami przechowywanymi w tabeli należy wydać instrukcję SET IDENTITY_INSERT dla sesji.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>Przesyłanie strumieniowe wierszy za pomocą elementu DataReader  
 Można również użyć dowolnego obiektu pochodnego od <xref:System.Data.Common.DbDataReader> do przesyłania strumieniowego wierszy danych do parametru z wartościami przechowywanymi w tabeli. Poniższy fragment kodu ilustruje pobieranie danych z bazy danych Oracle przy użyciu <xref:System.Data.OracleClient.OracleCommand> i <xref:System.Data.OracleClient.OracleDataReader>. Następnie kod konfiguruje <xref:System.Data.SqlClient.SqlCommand> do wywołania procedury składowanej z pojedynczym parametrem wejściowym. Właściwość <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> <xref:System.Data.SqlClient.SqlParameter> jest ustawiona na `Structured`. <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> przekazuje do procedury składowanej wynik `OracleDataReader` jako parametr z wartościami przechowywanymi w tabeli.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md)
- [Polecenia i parametry](../commands-and-parameters.md)
- [Parametry elementu DataAdapter](../dataadapter-parameters.md)
- [Operacje danych serwera SQL w ADO.NET](sql-server-data-operations.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
