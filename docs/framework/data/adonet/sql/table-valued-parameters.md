---
title: Parametry o wartościach tabelowych
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 2917a8d9b42d831566855271a2f2110637db586f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174475"
---
# <a name="table-valued-parameters"></a>Parametry o wartościach tabelowych
Parametry wyceniane w tabeli umożliwiają organizowanie wielu wierszy danych z aplikacji klienckiej do programu SQL Server bez konieczności wielokrotnego rund lub specjalnej logiki po stronie serwera do przetwarzania danych. Za pomocą parametrów wycenionych w tabeli można hermetyzować wiersze danych w aplikacji klienckiej i wysyłać dane do serwera za pomocą jednego parametru. Wiersze danych przychodzących są przechowywane w zmiennej tabeli, która następnie może być obsługiwana przy użyciu transact-SQL.  
  
 Wartości kolumn w parametrach wycenionych w tabeli są dostępne przy użyciu standardowych instrukcji Transact-SQL SELECT. Parametry wyceniane w tabeli są silnie wpisywane, a ich struktura jest automatycznie sprawdzana. Rozmiar parametrów wycenianych w tabeli jest ograniczony tylko przez pamięć serwera.  
  
> [!NOTE]
> Nie można zwrócić danych w parametrze wycenianym w tabeli. Parametry wyceniane w tabeli są tylko wejściowe; słowo kluczowe OUTPUT nie jest obsługiwane.  
  
 Aby uzyskać więcej informacji na temat parametrów wycenianych w tabeli, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Użyj parametrów wycenionych tabelą (aparat bazy danych)](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|W tym artykule opisano sposób tworzenia i używania parametrów wycenianych w tabeli.|  
|[Typy tabel zdefiniowane przez użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))|Opisuje typy tabel zdefiniowane przez użytkownika, które są używane do deklarowania parametrów wycenianych przez tabelę.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Przekazywanie wielu wierszy w poprzednich wersjach programu SQL Server  
 Przed wprowadzeniem parametrów wycenianych w tabeli do programu SQL Server 2008 opcje przekazywania wielu wierszy danych do procedury składowanej lub sparametryzowanego polecenia SQL były ograniczone. Deweloper może wybrać jedną z następujących opcji przekazywania wielu wierszy do serwera:  
  
- Użyj serii poszczególnych parametrów do reprezentowania wartości w wielu kolumnach i wierszach danych. Ilość danych, które mogą być przekazywane przy użyciu tej metody jest ograniczona przez liczbę dozwolonych parametrów. Procedury programu SQL Server mogą mieć co najwyżej 2100 parametrów. Logika po stronie serwera jest wymagana do zmontowanie tych poszczególnych wartości w zmiennej tabeli lub tabeli tymczasowej do przetwarzania.  
  
- Łącz wiele wartości danych w rozdzielone ciągi lub dokumenty XML, a następnie przekaż te wartości tekstowe do procedury lub instrukcji. Wymaga to, aby procedura lub instrukcja zawierała logikę niezbędną do sprawdzania poprawności struktur danych i rozdziału wartości.  
  
- Utwórz serię pojedynczych instrukcji SQL dla modyfikacji danych, które wpływają `Update` na wiele <xref:System.Data.SqlClient.SqlDataAdapter>wierszy, takich jak te utworzone przez wywołanie metody . Zmiany można przesyłać do serwera indywidualnie lub wsadowo w grupach. Jednak nawet po przesłaniu w partiach, które zawierają wiele instrukcji, każda instrukcja jest wykonywana oddzielnie na serwerze.  
  
- Użyj `bcp` programu narzędziowego <xref:System.Data.SqlClient.SqlBulkCopy> lub obiektu, aby załadować wiele wierszy danych do tabeli. Mimo że ta technika jest bardzo wydajne, nie obsługuje przetwarzania po stronie serwera, chyba że dane są ładowane do tabeli tymczasowej lub zmiennej tabeli.  
  
## <a name="creating-table-valued-parameter-types"></a>Tworzenie typów parametrów wycenianych według tabel  
 Parametry wyceniane w tabeli są oparte na silnie typizowanych strukturach tabel, które są definiowane przy użyciu instrukcji Transact-SQL CREATE TYPE. Należy utworzyć typ tabeli i zdefiniować strukturę w programie SQL Server, zanim będzie można użyć parametrów wycenionych w tabeli w aplikacjach klienckich. Aby uzyskać więcej informacji na temat tworzenia typów tabel, zobacz [Typy tabel zdefiniowane przez użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).  
  
 Następująca instrukcja tworzy typ tabeli o nazwie CategoryTableType, który składa się z kolumn CategoryID i CategoryName:  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Po utworzeniu typu tabeli można zadeklarować parametry wyceniane w tabeli na podstawie tego typu. Poniższy fragment Transact-SQL pokazuje, jak zadeklarować parametr wyceniony tabelą w definicji procedury składowanej. Należy zauważyć, że READONLY słowo kluczowe jest wymagane do deklarowania parametru wyceniony tabeli.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modyfikowanie danych za pomocą parametrów wycenianych w tabeli (Transact-SQL)  
 Parametry wyceniane w tabeli mogą być używane w modyfikacjach danych opartych na zestawie, które wpływają na wiele wierszy, wykonując pojedynczą instrukcję. Na przykład można zaznaczyć wszystkie wiersze w parametrze wycenianym w tabeli i wstawić je do tabeli bazy danych lub utworzyć instrukcję aktualizacji, łącząc parametr wyceniony tabelą z tabelą, którą chcesz zaktualizować.  
  
 Poniższa instrukcja Transact-SQL UPDATE pokazuje, jak używać parametru wycenianego przez tabelę, łącząc go z tabelą Kategorie. W przypadku użycia parametru wyceny tabeli z klauzulą JOIN w klauzuli FROM należy również alias, jak pokazano w tym miejscu, gdzie parametr wyceny tabeli jest aliasowany jako "ec":  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 W tym przykładzie Transact-SQL pokazano, jak wybrać wiersze z parametru wycenionego w tabeli, aby wykonać insert w operacji opartej na jednym zestawie.  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Ograniczenia parametrów wycenionych w tabeli  
 Istnieje kilka ograniczeń parametrów wycenianych w tabeli:  
  
- Nie można przekazać parametrów wycenionych w tabeli do [funkcji zdefiniowanych przez użytkownika CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).  
  
- Parametry wyceniane w tabeli mogą być indeksowane tylko w celu obsługi ograniczeń UNIQUE lub PRIMARY KEY. SQL Server nie przechowuje statystyk dotyczących parametrów wycenianych w tabeli.  
  
- Parametry wyceniane w tabeli są tylko do odczytu w kodzie Transact-SQL. Nie można zaktualizować wartości kolumn w wierszach parametru wycenionego w tabeli i nie można wstawiać ani usuwać wierszy. Aby zmodyfikować dane przekazywane do procedury składowanej lub sparametryzowanej instrukcji w parametrze wycenionym w tabeli, należy wstawić dane do tabeli tymczasowej lub do zmiennej tabeli.  
  
- Nie można użyć instrukcji ALTER TABLE do modyfikowania projektu parametrów wycenianych w tabeli.  
  
## <a name="configuring-a-sqlparameter-example"></a>Konfigurowanie przykładu programu SqlParameter  
 <xref:System.Data.SqlClient>obsługuje wypełnianie parametrów wycenionych <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> w tabeli z <xref:System.Data.DataTable>obiektów <xref:System.Data.Common.DbDataReader> lub obiektów. Należy określić nazwę typu dla parametru tabeli, używając <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwości <xref:System.Data.SqlClient.SqlParameter>programu . Musi `TypeName` odpowiadać nazwie zgodnego typu wcześniej utworzonego na serwerze. Poniższy fragment kodu pokazuje, <xref:System.Data.SqlClient.SqlParameter> jak skonfigurować wstawianie danych.  

W poniższym przykładzie zmienna `addedCategories` zawiera plik <xref:System.Data.DataTable>. Aby zobaczyć, jak zmienna jest wypełniana, zobacz przykłady w następnej sekcji [Przekazywanie parametru wyceny tabeli do procedury składowanej](#passing).

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
  
 Można również użyć dowolnego obiektu <xref:System.Data.Common.DbDataReader> uzyskanego z do strumienia wierszy danych do parametru wycenionego w tabeli, jak pokazano w tym fragmencie:  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a>Przekazywanie parametru wyceny tabeli do procedury składowanej  
 W tym przykładzie pokazano, jak przekazać dane parametrów wyceniane w tabeli do procedury składowanej. Kod wyodrębnia dodane wiersze <xref:System.Data.DataTable> do nowego <xref:System.Data.DataTable.GetChanges%2A> przy użyciu metody. Następnie kod definiuje <xref:System.Data.SqlClient.SqlCommand>, ustawienie <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> właściwości <xref:System.Data.CommandType.StoredProcedure>. Wypełniana <xref:System.Data.SqlClient.SqlParameter> jest przy <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> użyciu <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> metody, `Structured`a ustawiona jest na . Następnie <xref:System.Data.SqlClient.SqlCommand> jest wykonywany przy <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> użyciu metody.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Przekazywanie parametru wyceny tabeli do sparametryzowanej instrukcji SQL  
 W poniższym przykładzie pokazano, jak wstawić dane do dbo. Tabela Kategorie przy użyciu instrukcji INSERT z podkwerendą SELECT, która ma parametr wyceniony tabelą jako źródło danych. Podczas przekazywania parametru wyceny tabeli do sparametryzowanej instrukcji SQL należy określić <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> nazwę <xref:System.Data.SqlClient.SqlParameter>typu parametru wycenionego przez tabelę przy użyciu nowej właściwości programu . Musi `TypeName` to być zgodne z nazwą zgodnego typu wcześniej utworzonego na serwerze. Kod w tym przykładzie `TypeName` używa właściwości do odwoływania się do struktury typu zdefiniowanej w dbo. Typ kategorii.  
  
> [!NOTE]
> Jeśli podasz wartość kolumny tożsamości w parametrze wycenionym w tabeli, musisz wydać instrukcję SET IDENTITY_INSERT dla sesji.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>Przesyłanie strumieniowe wierszy za pomocą czytnika danych  
 Można również użyć dowolnego obiektu <xref:System.Data.Common.DbDataReader> uzyskanego z do strumienia wierszy danych do parametru wycenionego w tabeli. Poniższy fragment kodu demonstruje pobieranie danych z <xref:System.Data.OracleClient.OracleCommand> bazy <xref:System.Data.OracleClient.OracleDataReader>danych Oracle przy użyciu i . Kod następnie konfiguruje <xref:System.Data.SqlClient.SqlCommand> wywołać procedurę składowaną z jednym parametrem wejściowym. Właściwość <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> jest <xref:System.Data.SqlClient.SqlParameter> ustawiona `Structured`na . Przekazuje <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> `OracleDataReader` zestaw wyników do procedury składowanej jako parametr wyceniony w tabeli.  
  
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
