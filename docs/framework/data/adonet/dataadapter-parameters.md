---
title: Parametry elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 9954570dcf33c5eea4dcccf880de2c307de0aeca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151549"
---
# <a name="dataadapter-parameters"></a>Parametry elementu DataAdapter
Ma <xref:System.Data.Common.DbDataAdapter> cztery właściwości, które są używane do pobierania danych i aktualizacji <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> danych do źródła danych: właściwość zwraca dane ze źródła danych; i <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> i właściwości są używane do zarządzania zmianami w źródle danych. Właściwość `SelectCommand` musi być ustawiona `Fill` przed `DataAdapter`wywołaniem metody . `UpdateCommand`Przed `InsertCommand`wywołaniem `DeleteCommand` `Update` metody `DataAdapter` wywoływania metody , lub właściwości należy ustawić, w zależności od <xref:System.Data.DataTable>tego, jakie zmiany zostały wprowadzone w danych w pliku . Na przykład, jeśli wiersze zostały `InsertCommand` dodane, musi `Update`być ustawiona przed wywołaniem . Podczas `Update` przetwarzania wstawionego, zaktualizowanego lub `DataAdapter` usuniętego `Command` wiersza używa odpowiedniej właściwości do przetworzenia akcji. Bieżące informacje o zmodyfikowanym wierszu `Command` są `Parameters` przekazywane do obiektu za pośrednictwem kolekcji.  
  
 Podczas aktualizowania wiersza w źródle danych, należy wywołać UPDATE instrukcji, która używa unikatowy identyfikator do identyfikowania wiersza w tabeli, które mają być aktualizowane. Unikatowy identyfikator jest zazwyczaj wartością pola klucza podstawowego. Instrukcja UPDATE używa parametrów, które zawierają zarówno unikatowy identyfikator, jak i kolumny i wartości, które mają zostać zaktualizowane, jak pokazano w poniższej instrukcji Transact-SQL.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> Składnia symboli zastępczych parametrów zależy od źródła danych. W tym przykładzie przedstawiono symbole zastępcze dla źródła danych programu SQL Server. Użyj symboli zastępczych i <xref:System.Data.OleDb> <xref:System.Data.Odbc> parametrów znaku zapytania (?).  
  
 W tym przykładzie `CompanyName` języka Visual Basic pole `@CompanyName` jest aktualizowane `CustomerID` o wartość parametru `@CustomerID` dla wiersza, gdzie jest równa wartości parametru. Parametry pobierają informacje ze zmodyfikowanego wiersza <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> przy <xref:System.Data.SqlClient.SqlParameter> użyciu właściwości obiektu. Poniżej przedstawiono parametry poprzedniej przykładowej instrukcji UPDATE. Kod zakłada, że `adapter` zmienna <xref:System.Data.SqlClient.SqlDataAdapter> reprezentuje prawidłowy obiekt.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 Metoda `Add` `Parameters` kolekcji przyjmuje nazwę parametru, typ danych, rozmiar (jeśli dotyczy typu) i <xref:System.Data.Common.DbParameter.SourceColumn%2A> nazwę `DataTable`z . Należy zauważyć, <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` że parametr `Original`jest ustawiony na . Gwarantuje to, że istniejący wiersz w źródle danych zostanie zaktualizowany, jeśli wartość identyfikującej kolumny lub kolumn została zmieniona w zmodyfikowanym <xref:System.Data.DataRow>pliku . W takim przypadku `Original` wartość wiersza będzie zgodna z bieżącą `Current` wartością w źródle danych, a wartość wiersza będzie zawierać zaktualizowaną wartość. Dla `SourceVersion` parametru `@CompanyName` nie jest ustawiona i `Current` używa domyślnej wartości wiersza.  
  
> [!NOTE]
> Dla operacji `Fill` `DataAdapter` i `Get` metod `DataReader`, .NET Framework typu jest wywnioskowane z typu zwróconego z dostawcy danych .NET Framework. Wywnioskowane typy programu .NET Framework i metody akcesorów dla typów danych Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowaniach typów danych w ADO.NET](data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn, Parameter.SourceVersion  
 I `SourceColumn` `SourceVersion` mogą być przekazywane jako `Parameter` argumenty do konstruktora lub `Parameter`ustawić jako właściwości istniejącego . Jest `SourceColumn` to <xref:System.Data.DataColumn> nazwa, z <xref:System.Data.DataRow> której zostanie `Parameter` pobrana wartość. Określa `SourceVersion` `DataRow` wersję, która `DataAdapter` używa do pobierania wartości.  
  
 W poniższej <xref:System.Data.DataRowVersion> tabeli przedstawiono wartości wyliczenia dostępne do użycia z programem `SourceVersion`.  
  
|Wyliczenie DataRowVersion|Opis|  
|--------------------------------|-----------------|  
|`Current`|Parametr używa bieżącej wartości kolumny. Domyślnie włączone.|  
|`Default`|Parametr używa `DefaultValue` kolumny.|  
|`Original`|Parametr używa oryginalnej wartości kolumny.|  
|`Proposed`|Parametr używa proponowanej wartości.|  
  
 Przykład `SqlClient` kodu w następnej sekcji definiuje <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> parametr, `CustomerID` w `SourceColumn` którym kolumna jest `@CustomerID` używana`SET CustomerID = @CustomerID`jako `@OldCustomerID` `WHERE CustomerID = @OldCustomerID`dla dwóch parametrów: ( ), i ( ). Parametr `@CustomerID` służy do aktualizowania kolumny **CustomerID** do `DataRow`bieżącej wartości w pliku . W rezultacie stosuje `CustomerID` `SourceColumn` się `SourceVersion` `Current` z a of. Parametr `@OldCustomerID` służy do identyfikowania bieżącego wiersza w źródle danych. Ponieważ pasująca wartość kolumny `Original` znajduje się w wersji `SourceColumn` `CustomerID`wiersza, `SourceVersion` `Original` jest używana ta sama ( ) z of.  
  
## <a name="working-with-sqlclient-parameters"></a>Praca z parametrami SqlClient  
 W poniższym przykładzie pokazano, jak <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> utworzyć <xref:System.Data.SqlClient.SqlDataAdapter> i ustawić do w celu pobrania dodatkowych informacji o schemacie z bazy danych. Zestaw <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>właściwości <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> odpowiadających im <xref:System.Data.SqlClient.SqlParameter> obiektów oraz <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> ich odpowiednich obiektów. Metoda zwraca `SqlDataAdapter` obiekt.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Symbole zastępcze parametrów OleDb  
 W <xref:System.Data.OleDb.OleDbDataAdapter> przypadku <xref:System.Data.Odbc.OdbcDataAdapter> obiektów i należy użyć symboli zastępczych znaku zapytania (?), aby zidentyfikować parametry.  
  
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
  
 Sparametryzowane instrukcje kwerendy określają, które parametry wejściowe i wyjściowe muszą zostać utworzone. Aby utworzyć parametr, `Parameters.Add` należy użyć `Parameter` metody lub konstruktora, aby określić nazwę kolumny, typ danych i rozmiar. W przypadku wewnętrznych typów danych, `Integer`takich jak , nie trzeba uwzględniać rozmiaru lub można określić rozmiar domyślny.  
  
 Poniższy przykład kodu tworzy parametry instrukcji SQL, `DataSet`a następnie wypełnia plik .  
  
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
  
## <a name="odbc-parameters"></a>Parametry Odbc  
  
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
> Jeśli nazwa parametru nie jest podana dla parametru, parametr otrzymuje przyrostową domyślną nazwę parametru*N,* *,* zaczynając od "Parametr1". Zaleca się unikanie konwencji nazewnictwa parametru*N* podczas podawania nazwy parametru, ponieważ podana `ParameterCollection`nazwa może kolidować z istniejącą domyślną nazwą parametru w pliku . Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.  
  
## <a name="see-also"></a>Zobacz też

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapter](updating-data-sources-with-dataadapters.md)
- [Modyfikowanie danych za pomocą procedur składowanych](modifying-data-with-stored-procedures.md)
- [Mapowanie typu danych w ADO.NET](data-type-mappings-in-ado-net.md)
- [Omówienie ADO.NET](ado-net-overview.md)
