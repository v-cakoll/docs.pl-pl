---
title: Parametry elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: e633c7cdd105125fc5fb595566d15cf5f5fe4e6f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845622"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="a1786-102">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="a1786-102">DataAdapter Parameters</span></span>
<span data-ttu-id="a1786-103"><xref:System.Data.Common.DbDataAdapter> Ma cztery właściwości, które są używane do pobierania danych z i aktualizować dane do źródła danych: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> właściwość zwraca dane ze źródła danych; i <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, i <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> właściwości są używane do zarządzania zmiany w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a1786-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="a1786-104">`SelectCommand` Właściwość musi być ustawiona przed wywołaniem `Fill` metody `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="a1786-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="a1786-105">`InsertCommand`, `UpdateCommand`, Lub `DeleteCommand` właściwości musi być ustawiona przed `Update` metody `DataAdapter` jest wywoływana w zależności od tego, jakie zmiany zostały wprowadzone do danych w <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a1786-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a1786-106">Załóżmy, że wiersze zostały dodane `InsertCommand` musi być ustawiona przed wywołaniem `Update`.</span><span class="sxs-lookup"><span data-stu-id="a1786-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="a1786-107">Gdy `Update` przetwarza wierszy wstawionych, zaktualizowanych lub usuniętych `DataAdapter` używa odpowiednich `Command` właściwości przetwarzania akcji.</span><span class="sxs-lookup"><span data-stu-id="a1786-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="a1786-108">Aktualne informacje na temat zmodyfikowanych wierszy jest przekazywany do `Command` obiektu za pomocą `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a1786-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="a1786-109">Po zaktualizowaniu wiersza w źródle danych, należy wywołać instrukcji UPDATE, który używa do identyfikowania wiersza w tabeli, unikatowy identyfikator aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="a1786-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table be updated.</span></span> <span data-ttu-id="a1786-110">Unikatowy identyfikator jest zazwyczaj wartość klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="a1786-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="a1786-111">Instrukcja UPDATE używa parametrów, które zawierają zarówno Unikatowy identyfikator, kolumny i wartości, które mają zostać zaktualizowane, jak pokazano w następującej instrukcji języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="a1786-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  <span data-ttu-id="a1786-112">Składnia dla symboli zastępczych parametru zależy od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a1786-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="a1786-113">W tym przykładzie przedstawiono symbole zastępcze dla źródła danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a1786-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="a1786-114">Użyj znaku zapytania (?) symbole zastępcze <xref:System.Data.OleDb> i <xref:System.Data.Odbc> parametrów.</span><span class="sxs-lookup"><span data-stu-id="a1786-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="a1786-115">W tym przykładzie Visual Basic `CompanyName` pola do zaktualizowania z wartością `@CompanyName` parametr wiersza gdzie `CustomerID` jest równa wartości `@CustomerID` parametru.</span><span class="sxs-lookup"><span data-stu-id="a1786-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="a1786-116">Parametry pobieranie informacji z przy użyciu zmodyfikowanych wierszy <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> właściwość <xref:System.Data.SqlClient.SqlParameter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a1786-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="a1786-117">Poniżej przedstawiono parametry poprzednich instrukcji UPDATE próbki.</span><span class="sxs-lookup"><span data-stu-id="a1786-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="a1786-118">Kod zakłada, że zmienna `adapter` reprezentuje prawidłowy <xref:System.Data.SqlClient.SqlDataAdapter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a1786-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="a1786-119">`Add` Metody `Parameters` kolekcji przyjmuje nazwę parametru, typ danych, rozmiaru (jeśli ma zastosowanie do typu) i nazwę <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="a1786-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="a1786-120">Należy zauważyć, że <xref:System.Data.Common.DbParameter.SourceVersion%2A> z `@CustomerID` parametr ma wartość `Original`.</span><span class="sxs-lookup"><span data-stu-id="a1786-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="a1786-121">Gwarantuje to, że istniejący wiersz w źródle danych jest aktualizowana, jeśli wartość identyfikujące kolumny lub kolumn została zmieniona w zmodyfikowanego <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="a1786-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="a1786-122">W takim przypadku `Original` wartości wiersza będzie odpowiada bieżącej wartości w źródle danych i `Current` wartości wiersza zawiera zaktualizowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="a1786-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="a1786-123">`SourceVersion` Dla `@CompanyName` parametr nie jest ustawiona i stosuje domyślną, `Current` wiersza wartości.</span><span class="sxs-lookup"><span data-stu-id="a1786-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1786-124">Dla obu `Fill` operacji `DataAdapter` i `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ jest wnioskowany z typem zwracanym z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="a1786-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the type returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="a1786-125">Wywnioskowane [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy i metody dostępu dla typów danych programu Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="a1786-125">The inferred [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="a1786-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="a1786-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="a1786-127">`SourceColumn` i `SourceVersion` mogą być przekazywane jako argumenty do `Parameter` konstruktora lub Ustaw jako właściwości istniejącego `Parameter`.</span><span class="sxs-lookup"><span data-stu-id="a1786-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="a1786-128">`SourceColumn` Nazywa się <xref:System.Data.DataColumn> z <xref:System.Data.DataRow> gdzie wartość `Parameter` zostanie pobrana.</span><span class="sxs-lookup"><span data-stu-id="a1786-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="a1786-129">`SourceVersion` Określa `DataRow` wersji, `DataAdapter` używa w celu pobrania wartości.</span><span class="sxs-lookup"><span data-stu-id="a1786-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="a1786-130">W poniższej tabeli przedstawiono <xref:System.Data.DataRowVersion> dostępne dla wartości wyliczenia za pomocą `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="a1786-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="a1786-131">Wyliczenie DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="a1786-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="a1786-132">Opis</span><span class="sxs-lookup"><span data-stu-id="a1786-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="a1786-133">Parametr używa bieżącej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="a1786-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="a1786-134">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="a1786-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="a1786-135">Używa parametru `DefaultValue` kolumny.</span><span class="sxs-lookup"><span data-stu-id="a1786-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="a1786-136">Parametr używa oryginalnej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="a1786-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="a1786-137">Parametr używa proponowana wartość.</span><span class="sxs-lookup"><span data-stu-id="a1786-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="a1786-138">`SqlClient` Przykładowy kod w następnej sekcji definiuje parametr <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> w którym `CustomerID` kolumna jest używana jako `SourceColumn` dla dwóch parametrów: `@CustomerID` (`SET CustomerID = @CustomerID`), a `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span><span class="sxs-lookup"><span data-stu-id="a1786-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="a1786-139">`@CustomerID` Parametr służy do aktualizowania **CustomerID** bieżącą wartość w kolumnie `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="a1786-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="a1786-140">W rezultacie `CustomerID` `SourceColumn` z `SourceVersion` z `Current` jest używany.</span><span class="sxs-lookup"><span data-stu-id="a1786-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="a1786-141">`@OldCustomerID` Parametr jest używany do identyfikowania bieżącego wiersza w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a1786-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="a1786-142">Ponieważ pasującej wartości w kolumnie znajduje się w `Original` wersji wiersza, w taki sam `SourceColumn` (`CustomerID`) za pomocą `SourceVersion` z `Original` jest używany.</span><span class="sxs-lookup"><span data-stu-id="a1786-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="a1786-143">Praca z parametrami SqlClient</span><span class="sxs-lookup"><span data-stu-id="a1786-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="a1786-144">Poniższy przykład przedstawia sposób tworzenia <xref:System.Data.SqlClient.SqlDataAdapter> i ustaw <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> do <xref:System.Data.MissingSchemaAction.AddWithKey> w celu pobrania dodatkowych informacji o schemacie z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a1786-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="a1786-145"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, I <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> zestaw właściwości i odpowiadające im <xref:System.Data.SqlClient.SqlParameter> obiekty dodane do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a1786-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="a1786-146">Metoda ta zwraca `SqlDataAdapter` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a1786-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="a1786-147">Symbole zastępcze parametru OLE DB</span><span class="sxs-lookup"><span data-stu-id="a1786-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="a1786-148">Aby uzyskać <xref:System.Data.OleDb.OleDbDataAdapter> i <xref:System.Data.Odbc.OdbcDataAdapter> obiektów, znaku zapytania (?) symbole zastępcze należy użyć do identyfikacji parametrów.</span><span class="sxs-lookup"><span data-stu-id="a1786-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="a1786-149">Instrukcji zapytania parametrycznego zdefiniować, które dane wejściowe i parametry wyjściowe muszą zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="a1786-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="a1786-150">Aby utworzyć parametr, należy użyć `Parameters.Add` metody lub `Parameter` konstruktora, aby określić nazwę kolumny, typ danych i rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="a1786-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="a1786-151">Dla typów danych wewnętrznych takich jak `Integer`, nie trzeba dołączać rozmiar lub można określić domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="a1786-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="a1786-152">Poniższy przykład kodu tworzy parametrów dla instrukcji języka SQL, a następnie wypełnia `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a1786-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="a1786-153">Przykład OleDb</span><span class="sxs-lookup"><span data-stu-id="a1786-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="a1786-154">Parametry ODBC</span><span class="sxs-lookup"><span data-stu-id="a1786-154">Odbc Parameters</span></span>  
  
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
>  <span data-ttu-id="a1786-155">Jeśli nie podano nazwy parametru dla parametru, parametr otrzymuje przyrostowe domyślna nazwa parametru*N* *,* począwszy od "Parametr1".</span><span class="sxs-lookup"><span data-stu-id="a1786-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="a1786-156">Firma Microsoft zaleca, aby unikać parametr*N* konwencji nazewnictwa po użytkownik poda nazwę parametru, ponieważ nazwa wprowadzona może powodować konflikt z istniejącą nazwą parametru domyślnego w `ParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="a1786-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="a1786-157">Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a1786-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1786-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1786-158">See Also</span></span>  
 [<span data-ttu-id="a1786-159">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="a1786-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="a1786-160">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="a1786-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="a1786-161">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="a1786-161">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="a1786-162">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="a1786-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="a1786-163">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a1786-163">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="a1786-164">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a1786-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
