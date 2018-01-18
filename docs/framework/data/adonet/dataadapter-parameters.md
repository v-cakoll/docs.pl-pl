---
title: "Element DataAdapter parametrów"
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
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4b5cc66e1d2240450743afa8ca8aaa6efe94398d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dataadapter-parameters"></a>Element DataAdapter parametrów
<xref:System.Data.Common.DbDataAdapter> Ma cztery właściwości, które są używane do pobierania danych z danych i aktualizowanie źródła danych: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> właściwość zwraca dane ze źródła danych; i <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, i <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> właściwości są używane do zarządzania zmiany w źródle danych. `SelectCommand` Należy ustawić właściwość przed wywołaniem `Fill` metody `DataAdapter`. `InsertCommand`, `UpdateCommand`, Lub `DeleteCommand` właściwości musi być ustawiona przed `Update` metody `DataAdapter` jest wywoływana w zależności od tego, jakie zmiany wprowadzono w danych w <xref:System.Data.DataTable>. Na przykład, jeśli wiersze zostały dodane `InsertCommand` musi być ustawiona przed wywołaniem `Update`. Gdy `Update` przetwarza wierszy wstawionych, zaktualizowanych lub usuniętych `DataAdapter` używa odpowiednio `Command` właściwości do przetworzenia akcji. Bieżące informacje o zmodyfikowanych wierszy jest przekazywana do `Command` obiektu za pomocą `Parameters` kolekcji.  
  
 Podczas aktualizowania wierszy w źródle danych, należy wywołać instrukcji UPDATE, która jest używana Unikatowy identyfikator wiersza w tabeli można zaktualizować. Unikatowy identyfikator jest zwykle wartość pola klucza podstawowego. Instrukcja UPDATE używa parametrów, które zawierają zarówno Unikatowy identyfikator, kolumny i wartości do aktualizacji, jak pokazano w poniższych instrukcji języka Transact-SQL.  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  Składnia parametru symbole zastępcze zależy od źródła danych. Ten przykład przedstawia symbole zastępcze dla źródła danych programu SQL Server. Użyj symbole zastępcze znak zapytania (?) <xref:System.Data.OleDb> i <xref:System.Data.Odbc> parametrów.  
  
 W tym [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] przykład `CompanyName` jest aktualizowana wartość `@CompanyName` parametr wiersza gdzie `CustomerID` jest równa wartości `@CustomerID` parametru. Parametry pobrania informacji z przy użyciu zmodyfikowanych wierszy <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> właściwość <xref:System.Data.SqlClient.SqlParameter> obiektu. Poniżej przedstawiono parametry poprzedniej próbki instrukcji UPDATE. Kod, przy założeniu, że zmienna `adapter` reprezentuje prawidłową <xref:System.Data.SqlClient.SqlDataAdapter> obiektu.  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add` Metody `Parameters` kolekcji przyjmuje nazwę parametru, typu danych, rozmiaru (jeśli ma zastosowanie do typu), a nazwa <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable`. Zwróć uwagę, że <xref:System.Data.Common.DbParameter.SourceVersion%2A> z `@CustomerID` ustawiono parametr `Original`. Gwarantuje to, że istniejący wiersz w źródle danych został zaktualizowany, jeśli wartość identyfikacyjne kolumny lub kolumn została zmieniona w modyfikacji <xref:System.Data.DataRow>. W takim przypadku `Original` wartość wiersza czy pasuje do bieżącej wartości w źródle danych i `Current` wartość wiersza zawierałoby zaktualizowanej wartości. `SourceVersion` Dla `@CompanyName` parametru nie jest ustawiona i stosuje domyślną, `Current` wiersza wartości.  
  
> [!NOTE]
>  Dla obu `Fill` operacji `DataAdapter` i `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu jest wywnioskowany na podstawie zwrócone przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych. Wywnioskowane [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów i metod typu accessor dla typów danych Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn, Parameter.SourceVersion  
 `SourceColumn` i `SourceVersion` mogą być przekazywane jako argumenty do `Parameter` konstruktora lub Ustaw jako właściwości istniejącego `Parameter`. `SourceColumn` Jest nazwą <xref:System.Data.DataColumn> z <xref:System.Data.DataRow> gdzie wartość `Parameter` zostaną pobrane. `SourceVersion` Określa `DataRow` wersji który `DataAdapter` używane do pobierania wartości.  
  
 W poniższej tabeli przedstawiono <xref:System.Data.DataRowVersion> wartości wyliczenia są dostępne do użycia z `SourceVersion`.  
  
|DataRowVersion — wyliczenie|Opis|  
|--------------------------------|-----------------|  
|`Current`|Parametr korzysta z bieżącej wartości kolumny. Domyślnie włączone.|  
|`Default`|Używa parametru `DefaultValue` kolumny.|  
|`Original`|Parametr używa oryginalnej wartości kolumny.|  
|`Proposed`|Parametr używa proponowanej wartości.|  
  
 `SqlClient` Przykładowy kod w następnej sekcji definiuje parametru <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> w którym `CustomerID` kolumna jest używana jako `SourceColumn` dwa parametry: `@CustomerID` (`SET CustomerID = @CustomerID`), i `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`). `@CustomerID` Parametr jest używany do zaktualizowania **CustomerID** kolumny do bieżącej wartości `DataRow`. W związku z tym `CustomerID` `SourceColumn` z `SourceVersion` z `Current` jest używany.  *@OldCustomerID*  Parametr jest używany do identyfikowania bieżący wiersz w źródle danych. Ponieważ odnaleziono pasującej wartości kolumny w `Original` wersji wiersza, w taki sam `SourceColumn` (`CustomerID`) z `SourceVersion` z `Original` jest używany.  
  
## <a name="working-with-sqlclient-parameters"></a>Praca z parametrami SqlClient  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Data.SqlClient.SqlDataAdapter> i ustaw <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> do <xref:System.Data.MissingSchemaAction.AddWithKey> w celu pobrania dodatkowe informacje o schemacie z bazy danych. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, I <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> zestaw właściwości i odpowiadające <xref:System.Data.SqlClient.SqlParameter> obiekty dodane do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji. Metoda zwraca `SqlDataAdapter` obiektu.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Symbole zastępcze parametru OleDb  
 Aby uzyskać <xref:System.Data.OleDb.OleDbDataAdapter> i <xref:System.Data.Odbc.OdbcDataAdapter> obiektów, aby zidentyfikować parametrów, należy użyć symbole zastępcze znak zapytania (?).  
  
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
  
 Instrukcje zapytania parametrycznego zdefiniować, którego dane wejściowe i parametry wyjściowe muszą zostać utworzone. Aby utworzyć parametr, należy użyć `Parameters.Add` metody lub `Parameter` konstruktora, aby określić nazwę kolumny, typ danych i rozmiar. Dla typów danych wewnętrznych takich jak `Integer`, nie trzeba uwzględnić rozmiar lub można określić domyślny rozmiar.  
  
 Poniższy przykład kodu tworzy parametry instrukcji SQL i następnie wypełnia `DataSet`.  
  
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
>  Jeśli nie podano nazwy parametru dla parametru, parametr podano przyrostowe domyślną nazwę parametru*N* *,* począwszy od "Parameter1". Firma Microsoft zaleca, aby uniknąć parametr*N* konwencji nazewnictwa Jeśli podasz nazwę parametru, ponieważ nazwa wprowadzona może powodować konflikt z istniejącą nazwą parametru domyślnego w `ParameterCollection`. Jeśli podanej nazwie już istnieje, jest zwracany wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Modyfikowanie danych za pomocą procedur składowanych](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
