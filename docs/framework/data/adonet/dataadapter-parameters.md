---
title: Parametry elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 772763b5927ca845d6c2ccba50382652e410ae4f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951241"
---
# <a name="dataadapter-parameters"></a>Parametry elementu DataAdapter
<xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>Ma cztery właściwości, które są używane do pobierania danych z i aktualizowania danych do źródła danych: Właściwość zwraca dane ze źródła danych, a właściwości, i są używane do zarządzania <xref:System.Data.Common.DbDataAdapter> zmiany w źródle danych. Właściwość musi być ustawiona przed `Fill` wywołaniem metody `DataAdapter`. `SelectCommand` `Update` Właściwości `InsertCommand`, `UpdateCommand`, lub `DeleteCommand` musząbyć<xref:System.Data.DataTable>ustawione przed wywołaniem metody ,wzależnościodtego,jakiezmianyzostaływprowadzonedodanychw.`DataAdapter` Na przykład, jeśli dodano wiersze, `InsertCommand` należy ustawić przed wywołaniem metody. `Update` Gdy `Update` programprzetwarzawstawione,`Command` zaktualizowane lub usunięte wiersze, używaodpowiedniejwłaściwościdoprzetwarzaniaakcji.`DataAdapter` Bieżące informacje o zmodyfikowanym wierszu są przesyłane do `Command` obiektu `Parameters` za pomocą kolekcji.  
  
 Gdy aktualizujesz wiersz w źródle danych, wywołasz instrukcję UPDATE, która używa unikatowego identyfikatora, aby zidentyfikować wiersz w tabeli, która ma zostać zaktualizowana. Unikatowy identyfikator jest zwykle wartością pola klucza podstawowego. Instrukcja UPDATE używa parametrów, które zawierają zarówno unikatowy identyfikator, jak i kolumny i wartości do zaktualizowania, jak pokazano w poniższej instrukcji języka Transact-SQL.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> Składnia symboli zastępczych parametrów zależy od źródła danych. Ten przykład przedstawia symbole zastępcze dla SQL Servergo źródła danych. Użyj symboli zastępczych znaku zapytania (?) <xref:System.Data.OleDb> dla <xref:System.Data.Odbc> parametrów i.  
  
 W `CompanyName` tym Visual Basic przykładzie pole jest aktualizowane z wartością `@CompanyName` parametru wiersza, gdzie `CustomerID` jest równa wartości `@CustomerID` parametru. Parametry pobierają informacje ze zmodyfikowanego wiersza przy użyciu <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> właściwości <xref:System.Data.SqlClient.SqlParameter> obiektu. Poniżej przedstawiono parametry poprzedniej przykładowej instrukcji UPDATE. W kodzie założono, że `adapter` zmienna reprezentuje prawidłowy <xref:System.Data.SqlClient.SqlDataAdapter> obiekt.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 Metoda kolekcji przyjmuje nazwę parametru, typ danych, rozmiar (jeśli ma zastosowanie do typu) <xref:System.Data.Common.DbParameter.SourceColumn%2A> i `DataTable`nazwę elementu z. `Parameters` `Add` Należy zauważyć, <xref:System.Data.Common.DbParameter.SourceVersion%2A> że `@CustomerID` parametr jest ustawiony na `Original`. Gwarantuje to, że istniejący wiersz w źródle danych zostanie zaktualizowany, jeśli wartość kolumny lub kolumny identyfikacyjnej została zmieniona w zmodyfikowanym <xref:System.Data.DataRow>elemencie. W takim przypadku `Original` wartość wiersza byłaby zgodna z bieżącą wartością w źródle danych, `Current` a wartość wiersza będzie zawierać zaktualizowaną wartość. Parametr dla parametru nie jest ustawiony `Current` i używa domyślnej wartości wiersza. `SourceVersion` `@CompanyName`  
  
> [!NOTE]
> `Fill` Dla operacji `DataAdapter` i`Get` metod ,typ.NETFrameworkjestwywnioskowanynapodstawietypuzwróconegoprzezdostawcędanych.NETFramework.`DataReader` Wywnioskowane typy .NET Framework i metody dostępu dla typów danych Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowaniu typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter. SourceColumn, Parameter. SourceVersion  
 I mogą być przekazane jako `Parameter`argumenty do konstruktoralubustawionejakowłaściwościistniejącegoelementu.`Parameter` `SourceVersion` `SourceColumn` `Parameter` Jest nazwą <xref:System.Data.DataColumn> z<xref:System.Data.DataRow> lokalizacji, w której zostanie pobrana wartość. `SourceColumn` Określa wersję `DataAdapter`używaną przez program do pobrania wartości. `DataRow` `SourceVersion`  
  
 W poniższej tabeli przedstawiono <xref:System.Data.DataRowVersion> wartości wyliczenia dostępne do użycia z. `SourceVersion`  
  
|DataRowVersion, Wyliczenie|Opis|  
|--------------------------------|-----------------|  
|`Current`|Parametr używa bieżącej wartości kolumny. Domyślnie włączone.|  
|`Default`|Parametr używa `DefaultValue` kolumny.|  
|`Original`|Parametr używa oryginalnej wartości kolumny.|  
|`Proposed`|Parametr używa proponowanej wartości.|  
  
 `SourceColumn` <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> `CustomerID` `SET CustomerID = @CustomerID` `@CustomerID` `WHERE CustomerID = @OldCustomerID` `@OldCustomerID` Przykład kodu w następnej sekcji definiuje parametr, w którym kolumna jest używana jako dla dwóch parametrów: () i (). `SqlClient` Ten `@CustomerID` parametr służy do aktualizowania kolumny **CustomerID** do `DataRow`bieżącej wartości w. `CustomerID` W związku z tym `SourceColumn` `Current` jest używany element `SourceVersion` with a. Ten `@OldCustomerID` parametr służy do identyfikowania bieżącego wiersza w źródle danych. Ponieważ pasująca wartość kolumny jest znaleziona w `Original` wersji wiersza, używana `Original` jest ta sama `SourceColumn` (`CustomerID`) z parametrem `SourceVersion` .  
  
## <a name="working-with-sqlclient-parameters"></a>Praca z parametrami SqlClient  
 W poniższym przykładzie pokazano, jak utworzyć <xref:System.Data.SqlClient.SqlDataAdapter> i <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> ustawić do <xref:System.Data.MissingSchemaAction.AddWithKey> w celu pobrania dodatkowych informacji o schemacie z bazy danych. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlParameter> Ustawione właściwości, ,<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> i odpowiadające im obiekty dodane do kolekcji. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> Metoda zwraca `SqlDataAdapter` obiekt.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Symbole zastępcze parametrów OleDb  
 Dla obiektów <xref:System.Data.Odbc.OdbcDataAdapter> i należy użyć symboli zastępczych znaku zapytania (?), aby zidentyfikować parametry. <xref:System.Data.OleDb.OleDbDataAdapter>  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =   
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =   
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =   
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 Sparametryzowane instrukcje zapytania definiują, które parametry wejściowe i wyjściowe muszą zostać utworzone. Aby utworzyć parametr, użyj `Parameters.Add` metody `Parameter` lub konstruktora, aby określić nazwę kolumny, typ danych i rozmiar. W przypadku wewnętrznych typów danych, takich `Integer`jak, nie trzeba uwzględniać rozmiaru lub można określić rozmiar domyślny.  
  
 Poniższy przykład kodu tworzy parametry instrukcji SQL, a następnie wypełnia `DataSet`.  
  
## <a name="oledb-example"></a>Przykład OleDb  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter   
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## <a name="odbc-parameters"></a>Parametry ODBC  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
> Jeśli nazwa parametru nie jest podana dla parametru, parametr otrzymuje przyrostową domyślną nazwę parametru*N* *,* rozpoczynając od "parametr1". Zalecamy uniknięcie konwencji nazewnictwa*N* parametrem w przypadku podania nazwy parametru, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą parametru w `ParameterCollection`. Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [Modyfikowanie danych za pomocą procedur składowanych](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
