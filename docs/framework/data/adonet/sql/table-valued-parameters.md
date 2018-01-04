---
title: Parametry przechowywanymi w tabeli
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
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ce210e1da2002fe599a3703ec90374afba843c3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="table-valued-parameters"></a>Parametry przechowywanymi w tabeli
Parametry przechowywanymi w tabeli umożliwiają łatwe do organizowania wielu wierszy danych z aplikacji klienckiej [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] bez konieczności wiele rund lub specjalną logikę po stronie serwera do przetwarzania danych. Hermetyzuj wierszy danych w aplikacji klienckiej i wysyłania danych do serwera za pomocą jednego polecenia sparametryzowane, mogą używać parametrów przechowywanymi w tabeli. Przychodzące wiersze danych są przechowywane w zmiennej tabeli, która następnie może być obsługiwany przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].  
  
 Wartości w kolumnie w parametrach przechowywanymi w tabeli jest możliwy przy użyciu standardu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji "SELECT". Parametry przechowywanymi w tabeli są silnie typizowane i ich struktury automatycznie zostanie zweryfikowany. Rozmiar parametrów przechowywanymi w tabeli jest ograniczona tylko przez ilość pamięci serwera.  
  
> [!NOTE]
>  Nie można zwrócić dane w parametrze przechowywanymi w tabeli. Parametry przechowywanymi w tabeli są tylko wejściowym; dane wyjściowe — słowo kluczowe nie jest obsługiwane.  
  
 Aby uzyskać więcej informacji na temat parametrów przechowywanymi w tabeli zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Parametry z wartościami przechowywanymi w tabeli (aparat bazy danych)](http://go.microsoft.com/fwlink/?LinkId=98363) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online|Opisuje sposób tworzenia i używania parametrów przechowywanymi w tabeli.|  
|[Zdefiniowane przez użytkownika typy tabel](http://go.microsoft.com/fwlink/?LinkId=98364) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online|W tym artykule opisano typy tabel zdefiniowanych przez użytkownika, które są używane do deklarowania parametry przechowywanymi w tabeli.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Przekazywanie wielu wierszy w poprzednich wersjach programu SQL Server  
 Przed wprowadzeniem przechowywanymi w tabeli parametrów do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, opcje przekazywania wielu wierszy danych do procedury składowanej lub sparametryzowanego polecenia SQL były ograniczone. Deweloper może wybrać spośród następujących opcji wiele wierszy może być przekazywany do serwera:  
  
-   Używanie serii poszczególnych parametrów do reprezentowania wartości w wielu kolumn i wierszy danych. Ilość danych, które mogą zostać przekazane za pomocą tej metody jest ograniczona liczba parametry są niedozwolone. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]procedury może mieć co najwyżej 2100 parametrów. Logika po stronie serwera jest wymagany do włączenia tych poszczególne wartości do zmiennej tabeli lub tabeli tymczasowej do przetwarzania.  
  
-   Powiązać wiele wartości danych do ciągów rozdzielanych lub dokumentów XML, a następnie przekazać te wartości tekstowe do instrukcji lub procedury. Wymaga to procedury lub instrukcji Dołącz logikę niezbędne do sprawdzania poprawności struktur danych oraz wydzielenia wartości.  
  
-   Utwórz serię poszczególnych instrukcji SQL dla modyfikacji danych, które mają wpływ na wiele wierszy, takich jak te utworzone przez wywołanie metody `Update` metody <xref:System.Data.SqlClient.SqlDataAdapter>. Zmiany można przesłać na serwer indywidualnie lub przetwarzane wsadowo w grupach. Jednak nawet wtedy, gdy przesłać w partiach zawierających wiele instrukcji, każda instrukcja jest wykonywana osobno na serwerze.  
  
-   Użyj `bcp` program narzędziowy lub <xref:System.Data.SqlClient.SqlBulkCopy> obiekt, aby załadować wiele wierszy danych do tabeli. Ta technika jest bardzo wydajny, nie obsługuje przetwarzania po stronie serwera, chyba że dane zostaną załadowane do tabeli tymczasowej lub zmiennej tabeli.  
  
## <a name="creating-table-valued-parameter-types"></a>Tworzenie typów parametru przechowywanymi w tabeli  
 Parametry przechowywanymi w tabeli są oparte na struktury jednoznacznie tabeli, które zdefiniowano przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji CREATE TYPE. Należy utworzyć typ tabeli i definiowania struktury w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] przed użyciem parametrów przechowywanymi w tabeli w aplikacjach klienckich. Aby uzyskać więcej informacji o tworzeniu typach tabel, zobacz [typach tabel zdefiniowanych przez użytkownika](http://go.microsoft.com/fwlink/?LinkID=98364) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] — książki Online.  
  
 Poniższa instrukcja tworzy typ tabeli o nazwie CategoryTableType składający się z identyfikatorem kategorii i CategoryName kolumn:  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Po utworzeniu tabeli można zadeklarować parametry przechowywanymi w tabeli na podstawie tego typu. Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragmentu pokazuje, jak do zadeklarowania parametru przechowywanymi w tabeli w definicji procedury składowanej. Należy pamiętać, że READONLY — słowo kluczowe jest wymagana dla deklarowaniu parametru przechowywanymi w tabeli.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modyfikowanie danych z parametrami przechowywanymi w tabeli (Transact-SQL)  
 Parametry przechowywanymi w tabeli mogą być używane w modyfikacji na podstawie zestawu danych, które mają wpływ na wiele wierszy, wykonując jednej instrukcji. Na przykład można wybrać wszystkie wiersze w parametrze przechowywanymi w tabeli i wstawić je do tabeli bazy danych lub instrukcji update można utworzyć przez dołączenie do tabeli, które chcesz zaktualizować parametru przechowywanymi w tabeli.  
  
 Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji UPDATE pokazano, jak użyć parametru przechowywanymi w tabeli przez dołączenie go do tabeli Kategorie. Gdy używasz parametru przechowywanymi w tabeli z sprzężenia w klauzuli FROM, należy również aliasu, jak pokazano w tym miejscu, gdzie parametr przechowywanymi w tabeli jest używane z aliasem jako "WE":  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 To [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] przykładzie pokazano sposób wybierania z parametrem przechowywanymi w tabeli w celu wykonania instrukcji INSERT w jednej operacji na podstawie zestawu wierszy.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Ograniczenia parametrów przechowywanymi w tabeli  
 Istnieje kilka ograniczeń dotyczących przechowywanymi w tabeli Parametry:  
  
-   Nie można przekazać parametry przechowywanymi w tabeli [funkcje zdefiniowane przez użytkownika CLR](http://msdn.microsoft.com/library/ms131077.aspx).  
  
-   Parametry przechowywanymi w tabeli mogą być indeksowane tylko do obsługi ograniczenia UNIQUE i PRIMARY KEY. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]nie przechowuje dane statystyczne dotyczące parametrów przechowywanymi w tabeli.  
  
-   Parametry przechowywanymi w tabeli są tylko do odczytu w [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kodu. Nie można zaktualizować wartości w kolumnach w wierszach parametru przechowywanymi w tabeli i nie można wstawić lub usuwania wierszy. Aby zmodyfikować dane, które są przekazywane do procedury składowanej lub sparametryzowanych instrukcji w parametrze przechowywanymi w tabeli, należy wstawić dane do tabeli tymczasowej lub zmiennej tabeli.  
  
-   Za pomocą instrukcji ALTER TABLE nie można modyfikować projektu parametry przechowywanymi w tabeli.  
  
## <a name="configuring-a-sqlparameter-example"></a>Konfigurowanie przykład SqlParameter  
 <xref:System.Data.SqlClient>obsługuje wypełnianie przechowywanymi w tabeli parametrów z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> lub <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> obiektów. Należy określić nazwę typu dla parametru przechowywanymi w tabeli, używając <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwość <xref:System.Data.SqlClient.SqlParameter>. `TypeName` Musi być zgodna z nazwą zgodne z typem wcześniej utworzony na serwerze. Poniższy fragment kodu przedstawia sposób konfigurowania <xref:System.Data.SqlClient.SqlParameter> do wstawiania danych.  
  
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
  
 Umożliwia także dowolnego obiektu pochodną <xref:System.Data.Common.DbDataReader> do wierszy strumienia danych do parametru przechowywanymi w tabeli, jak pokazano w tym fragmencie:  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a>Przekazywanie parametru przechowywanymi w tabeli do procedury składowanej  
 W tym przykładzie pokazano, jak przekazywać dane parametru przechowywanymi w tabeli do procedury składowanej. Kod wyodrębnia dodanych wierszy w nowym <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTable.GetChanges%2A> metody. Kod definiuje <xref:System.Data.SqlClient.SqlCommand>, ustawienie <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> właściwości <xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlParameter> Jest wypełniany przy użyciu <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> — metoda i <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ma ustawioną wartość `Structured`. <xref:System.Data.SqlClient.SqlCommand> Następnie jest wykonywane przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Przekazywanie parametru przechowywanymi w tabeli w instrukcji SQL sparametryzowane  
 W poniższym przykładzie pokazano, jak wstawianie danych do dbo. Kategorie tabeli za pomocą instrukcji INSERT podzapytania SELECT, który ma parametr przechowywanymi w tabeli jako źródła danych. Podczas przekazywania parametru przechowywanymi w tabeli do sparametryzowanych instrukcji SQL, należy określić nazwę typu dla parametru przechowywanymi w tabeli, używając nowego <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> właściwość <xref:System.Data.SqlClient.SqlParameter>. To `TypeName` musi być zgodna z nazwą zgodne z typem wcześniej utworzony na serwerze. W kodzie w tym przykładzie użyto `TypeName` właściwości, aby odwołać struktury typ zdefiniowany w dbo. CategoryTableType.  
  
> [!NOTE]
>  Jeśli zostanie podana wartość dla kolumny tożsamości w parametrze przechowywanymi w tabeli, należy wygenerować instrukcji USTAWIONY atrybut IDENTITY_INSERT dla sesji.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>Przesyłania strumieniowego wiersze z elementu DataReader  
 Umożliwia także dowolnego obiektu pochodną <xref:System.Data.Common.DbDataReader> do wierszy strumienia danych do parametru przechowywanymi w tabeli. Poniższy fragment kodu przedstawia pobieranie danych z bazy danych Oracle przy użyciu <xref:System.Data.OracleClient.OracleCommand> i <xref:System.Data.OracleClient.OracleDataReader>. Następnie konfiguruje kod <xref:System.Data.SqlClient.SqlCommand> można wywołać procedury składowanej z jednego parametru wejściowego. <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Właściwość <xref:System.Data.SqlClient.SqlParameter> ma ustawioną wartość `Structured`. <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Przekazuje `OracleDataReader` zestawu wyników procedury składowanej jako parametru przechowywanymi w tabeli.  
  
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
 [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Polecenia i parametry](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Parametry elementu DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Operacje danych serwera SQL w ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
