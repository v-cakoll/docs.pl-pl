---
title: Parametry elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: b8284f45d769f018655ee35a5f0b067703963634
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034492"
---
# <a name="dataadapter-parameters"></a>Parametry elementu DataAdapter
<xref:System.Data.Common.DbDataAdapter> Ma cztery właściwości, które są używane do pobierania danych z i aktualizować dane do źródła danych: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> właściwość zwraca dane ze źródła danych; i <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, i <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> właściwości są używane do zarządzania zmiany w źródle danych. `SelectCommand` Właściwość musi być ustawiona przed wywołaniem `Fill` metody `DataAdapter`. `InsertCommand`, `UpdateCommand`, Lub `DeleteCommand` właściwości musi być ustawiona przed `Update` metody `DataAdapter` jest wywoływana w zależności od tego, jakie zmiany zostały wprowadzone do danych w <xref:System.Data.DataTable>. Załóżmy, że wiersze zostały dodane `InsertCommand` musi być ustawiona przed wywołaniem `Update`. Gdy `Update` przetwarza wierszy wstawionych, zaktualizowanych lub usuniętych `DataAdapter` używa odpowiednich `Command` właściwości przetwarzania akcji. Aktualne informacje na temat zmodyfikowanych wierszy jest przekazywany do `Command` obiektu za pomocą `Parameters` kolekcji.  
  
 Po zaktualizowaniu wiersza w źródle danych, możesz wywołać instrukcji UPDATE, który używa unikatowego identyfikatora do identyfikowania wiersza w tabeli do zaktualizowania. Unikatowy identyfikator jest zazwyczaj wartość klucz podstawowy. Instrukcja UPDATE używa parametrów, które zawierają zarówno Unikatowy identyfikator, kolumny i wartości, które mają zostać zaktualizowane, jak pokazano w następującej instrukcji języka Transact-SQL.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  Składnia dla symboli zastępczych parametru zależy od źródła danych. W tym przykładzie przedstawiono symbole zastępcze dla źródła danych programu SQL Server. Użyj znaku zapytania (?) symbole zastępcze <xref:System.Data.OleDb> i <xref:System.Data.Odbc> parametrów.  
  
 W tym przykładzie Visual Basic `CompanyName` pola do zaktualizowania z wartością `@CompanyName` parametr wiersza gdzie `CustomerID` jest równa wartości `@CustomerID` parametru. Parametry pobieranie informacji z przy użyciu zmodyfikowanych wierszy <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> właściwość <xref:System.Data.SqlClient.SqlParameter> obiektu. Poniżej przedstawiono parametry poprzednich instrukcji UPDATE próbki. Kod zakłada, że zmienna `adapter` reprezentuje prawidłowy <xref:System.Data.SqlClient.SqlDataAdapter> obiektu.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add` Metody `Parameters` kolekcji przyjmuje nazwę parametru, typ danych, rozmiaru (jeśli ma zastosowanie do typu) i nazwę <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable`. Należy zauważyć, że <xref:System.Data.Common.DbParameter.SourceVersion%2A> z `@CustomerID` parametr ma wartość `Original`. Gwarantuje to, że istniejący wiersz w źródle danych jest aktualizowana, jeśli wartość identyfikujące kolumny lub kolumn została zmieniona w zmodyfikowanego <xref:System.Data.DataRow>. W takim przypadku `Original` wartości wiersza będzie odpowiada bieżącej wartości w źródle danych i `Current` wartości wiersza zawiera zaktualizowaną wartość. `SourceVersion` Dla `@CompanyName` parametr nie jest ustawiona i stosuje domyślną, `Current` wiersza wartości.  
  
> [!NOTE]
>  Dla obu `Fill` operacji `DataAdapter` i `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ jest wnioskowany z typem zwracanym z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych. Wywnioskowane [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy i metody dostępu dla typów danych programu Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn, Parameter.SourceVersion  
 `SourceColumn` i `SourceVersion` mogą być przekazywane jako argumenty do `Parameter` konstruktora lub Ustaw jako właściwości istniejącego `Parameter`. `SourceColumn` Nazywa się <xref:System.Data.DataColumn> z <xref:System.Data.DataRow> gdzie wartość `Parameter` zostanie pobrana. `SourceVersion` Określa `DataRow` wersji, `DataAdapter` używa w celu pobrania wartości.  
  
 W poniższej tabeli przedstawiono <xref:System.Data.DataRowVersion> dostępne dla wartości wyliczenia za pomocą `SourceVersion`.  
  
|Wyliczenie DataRowVersion|Opis|  
|--------------------------------|-----------------|  
|`Current`|Parametr używa bieżącej wartości kolumny. Domyślnie włączone.|  
|`Default`|Używa parametru `DefaultValue` kolumny.|  
|`Original`|Parametr używa oryginalnej wartości kolumny.|  
|`Proposed`|Parametr używa proponowana wartość.|  
  
 `SqlClient` Przykładowy kod w następnej sekcji definiuje parametr <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> w którym `CustomerID` kolumna jest używana jako `SourceColumn` dla dwóch parametrów: `@CustomerID` (`SET CustomerID = @CustomerID`), a `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`). `@CustomerID` Parametr służy do aktualizowania **CustomerID** bieżącą wartość w kolumnie `DataRow`. W rezultacie `CustomerID` `SourceColumn` z `SourceVersion` z `Current` jest używany. `@OldCustomerID` Parametr jest używany do identyfikowania bieżącego wiersza w źródle danych. Ponieważ pasującej wartości w kolumnie znajduje się w `Original` wersji wiersza, w taki sam `SourceColumn` (`CustomerID`) za pomocą `SourceVersion` z `Original` jest używany.  
  
## <a name="working-with-sqlclient-parameters"></a>Praca z parametrami SqlClient  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Data.SqlClient.SqlDataAdapter> i ustaw <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> do <xref:System.Data.MissingSchemaAction.AddWithKey> w celu pobrania dodatkowych informacji o schemacie z bazy danych. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, I <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> zestaw właściwości i odpowiadające im <xref:System.Data.SqlClient.SqlParameter> obiekty dodane do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji. Metoda ta zwraca `SqlDataAdapter` obiektu.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Symbole zastępcze parametru OLE DB  
 Aby uzyskać <xref:System.Data.OleDb.OleDbDataAdapter> i <xref:System.Data.Odbc.OdbcDataAdapter> obiektów, znaku zapytania (?) symbole zastępcze należy użyć do identyfikacji parametrów.  
  
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
  
 Instrukcji zapytania parametrycznego zdefiniować, które dane wejściowe i parametry wyjściowe muszą zostać utworzone. Aby utworzyć parametr, należy użyć `Parameters.Add` metody lub `Parameter` konstruktora, aby określić nazwę kolumny, typ danych i rozmiaru. Dla typów danych wewnętrznych takich jak `Integer`, nie trzeba dołączać rozmiar lub można określić domyślny rozmiar.  
  
 Poniższy przykład kodu tworzy parametrów dla instrukcji języka SQL, a następnie wypełnia `DataSet`.  
  
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
>  Jeśli nie podano nazwy parametru dla parametru, parametr otrzymuje przyrostowe domyślna nazwa parametru*N* *,* począwszy od "Parametr1". Firma Microsoft zaleca, aby unikać parametr*N* konwencji nazewnictwa po użytkownik poda nazwę parametru, ponieważ nazwa wprowadzona może powodować konflikt z istniejącą nazwą parametru domyślnego w `ParameterCollection`. Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [Modyfikowanie danych za pomocą procedur składowanych](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
