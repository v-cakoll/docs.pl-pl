---
title: Parametry elementu DataAdapter
description: Dowiedz się więcej o właściwościach DbDataAdapter, które zwracają dane ze źródła danych i zarządzają zmianami w źródle danych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 74b6787162b48f83a48127257dc8e23e31a859b7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286989"
---
# <a name="dataadapter-parameters"></a>Parametry elementu DataAdapter
<xref:System.Data.Common.DbDataAdapter>Ma cztery właściwości, które są używane do pobierania danych z i aktualizowania danych do źródła danych: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> Właściwość zwraca dane ze źródła danych, a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> właściwości, i <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> są używane do zarządzania zmianami w źródle danych. `SelectCommand`Właściwość musi być ustawiona przed wywołaniem `Fill` metody `DataAdapter` . `InsertCommand`Właściwości, `UpdateCommand` , lub `DeleteCommand` muszą być ustawione przed `Update` `DataAdapter` wywołaniem metody, w zależności od tego, jakie zmiany zostały wprowadzone do danych w <xref:System.Data.DataTable> . Na przykład, jeśli dodano wiersze, `InsertCommand` należy ustawić przed wywołaniem metody `Update` . Gdy `Update` program przetwarza wstawione, zaktualizowane lub usunięte wiersze, `DataAdapter` używa odpowiedniej `Command` właściwości do przetwarzania akcji. Bieżące informacje o zmodyfikowanym wierszu są przesyłane do `Command` obiektu za pomocą `Parameters` kolekcji.  
  
 Gdy aktualizujesz wiersz w źródle danych, wywołasz instrukcję UPDATE, która używa unikatowego identyfikatora, aby zidentyfikować wiersz w tabeli, która ma zostać zaktualizowana. Unikatowy identyfikator jest zwykle wartością pola klucza podstawowego. Instrukcja UPDATE używa parametrów, które zawierają zarówno unikatowy identyfikator, jak i kolumny i wartości do zaktualizowania, jak pokazano w poniższej instrukcji języka Transact-SQL.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> Składnia symboli zastępczych parametrów zależy od źródła danych. Ten przykład przedstawia symbole zastępcze dla SQL Servergo źródła danych. Użyj symboli zastępczych znaku zapytania (?) <xref:System.Data.OleDb> dla <xref:System.Data.Odbc> parametrów i.  
  
 W tym Visual Basic przykładzie `CompanyName` pole jest aktualizowane z wartością `@CompanyName` parametru wiersza, gdzie jest `CustomerID` równa wartości `@CustomerID` parametru. Parametry pobierają informacje ze zmodyfikowanego wiersza przy użyciu <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> właściwości <xref:System.Data.SqlClient.SqlParameter> obiektu. Poniżej przedstawiono parametry poprzedniej przykładowej instrukcji UPDATE. W kodzie założono, że zmienna `adapter` reprezentuje prawidłowy <xref:System.Data.SqlClient.SqlDataAdapter> obiekt.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add`Metoda `Parameters` kolekcji przyjmuje nazwę parametru, typ danych, rozmiar (jeśli ma zastosowanie do typu) i nazwę elementu <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable` . Należy zauważyć, że <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` parametr jest ustawiony na `Original` . Gwarantuje to, że istniejący wiersz w źródle danych zostanie zaktualizowany, jeśli wartość kolumny lub kolumny identyfikacyjnej została zmieniona w zmodyfikowanym elemencie <xref:System.Data.DataRow> . W takim przypadku `Original` wartość wiersza byłaby zgodna z bieżącą wartością w źródle danych, a `Current` wartość wiersza będzie zawierać zaktualizowaną wartość. `SourceVersion` `@CompanyName` Parametr dla parametru nie jest ustawiony i używa domyślnej `Current` wartości wiersza.  
  
> [!NOTE]
> Dla `Fill` operacji `DataAdapter` i `Get` metod `DataReader` , typ .NET Framework jest wywnioskowany na podstawie typu zwróconego przez dostawcę danych .NET Framework. Wywnioskowane typy .NET Framework i metody dostępu dla typów danych Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowaniu typu danych w ADO.NET](data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter. SourceColumn, Parameter. SourceVersion  
 `SourceColumn`I `SourceVersion` mogą być przekazane jako argumenty do `Parameter` konstruktora lub ustawione jako właściwości istniejącego elementu `Parameter` . `SourceColumn`Jest nazwą z lokalizacji, w <xref:System.Data.DataColumn> <xref:System.Data.DataRow> której `Parameter` zostanie pobrana wartość. `SourceVersion`Określa `DataRow` wersję używaną przez program `DataAdapter` do pobrania wartości.  
  
 W poniższej tabeli przedstawiono <xref:System.Data.DataRowVersion> wartości wyliczenia dostępne do użycia z `SourceVersion` .  
  
|DataRowVersion, Wyliczenie|Opis|  
|--------------------------------|-----------------|  
|`Current`|Parametr używa bieżącej wartości kolumny. Domyślnie włączone.|  
|`Default`|Parametr używa `DefaultValue` kolumny.|  
|`Original`|Parametr używa oryginalnej wartości kolumny.|  
|`Proposed`|Parametr używa proponowanej wartości.|  
  
 `SqlClient`Przykład kodu w następnej sekcji definiuje parametr, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> w którym `CustomerID` kolumna jest używana jako `SourceColumn` dla dwóch parametrów: `@CustomerID` ( `SET CustomerID = @CustomerID` ) i `@OldCustomerID` ( `WHERE CustomerID = @OldCustomerID` ). Ten `@CustomerID` parametr służy do aktualizowania kolumny **CustomerID** do bieżącej wartości w `DataRow` . W związku z tym `CustomerID` `SourceColumn` jest używany element with a `SourceVersion` `Current` . Ten `@OldCustomerID` parametr służy do identyfikowania bieżącego wiersza w źródle danych. Ponieważ pasująca wartość kolumny jest znaleziona w `Original` wersji wiersza, używana jest ta sama `SourceColumn` ( `CustomerID` ) z parametrem `SourceVersion` `Original` .  
  
## <a name="working-with-sqlclient-parameters"></a>Praca z parametrami SqlClient  
 W poniższym przykładzie pokazano, jak utworzyć <xref:System.Data.SqlClient.SqlDataAdapter> i ustawić <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> do w celu <xref:System.Data.MissingSchemaAction.AddWithKey> pobrania dodatkowych informacji o schemacie z bazy danych. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> Ustawione właściwości,,, i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> odpowiadające im <xref:System.Data.SqlClient.SqlParameter> obiekty dodane do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji. Metoda zwraca `SqlDataAdapter` obiekt.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Symbole zastępcze parametrów OleDb  
 Dla <xref:System.Data.OleDb.OleDbDataAdapter> obiektów i należy <xref:System.Data.Odbc.OdbcDataAdapter> użyć symboli zastępczych znaku zapytania (?), aby zidentyfikować parametry.  
  
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
  
 Sparametryzowane instrukcje zapytania definiują, które parametry wejściowe i wyjściowe muszą zostać utworzone. Aby utworzyć parametr, użyj `Parameters.Add` metody lub `Parameter` konstruktora, aby określić nazwę kolumny, typ danych i rozmiar. W przypadku wewnętrznych typów danych, takich jak `Integer` , nie trzeba uwzględniać rozmiaru lub można określić rozmiar domyślny.  
  
 Poniższy przykład kodu tworzy parametry instrukcji SQL, a następnie wypełnia `DataSet` .  
  
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
> Jeśli nazwa parametru nie jest podana dla parametru, parametr otrzymuje przyrostową domyślną nazwę parametru*N* *,* rozpoczynając od "parametr1". Zalecamy uniknięcie konwencji nazewnictwa*N* parametrem w przypadku podania nazwy parametru, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą parametru w `ParameterCollection` . Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapter](updating-data-sources-with-dataadapters.md)
- [Modyfikowanie danych za pomocą procedur składowanych](modifying-data-with-stored-procedures.md)
- [Mapowanie typu danych w ADO.NET](data-type-mappings-in-ado-net.md)
- [Omówienie ADO.NET](ado-net-overview.md)
