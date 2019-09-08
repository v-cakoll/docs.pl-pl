---
title: Parametry elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 83fc3101b0eb428def6cbc446e634e9bb45de350
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785610"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="b16db-102">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="b16db-102">DataAdapter Parameters</span></span>
<span data-ttu-id="b16db-103"><xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>Ma cztery właściwości, które są używane do pobierania danych z i aktualizowania danych do źródła danych: Właściwość zwraca dane ze źródła danych, a właściwości, i są używane do zarządzania <xref:System.Data.Common.DbDataAdapter> zmiany w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="b16db-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="b16db-104">Właściwość musi być ustawiona przed `Fill` wywołaniem metody `DataAdapter`. `SelectCommand`</span><span class="sxs-lookup"><span data-stu-id="b16db-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="b16db-105">`Update` Właściwości `InsertCommand`, `UpdateCommand`, lub `DeleteCommand` musząbyć<xref:System.Data.DataTable>ustawione przed wywołaniem metody ,wzależnościodtego,jakiezmianyzostaływprowadzonedodanychw.`DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="b16db-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="b16db-106">Na przykład, jeśli dodano wiersze, `InsertCommand` należy ustawić przed wywołaniem metody. `Update`</span><span class="sxs-lookup"><span data-stu-id="b16db-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="b16db-107">Gdy `Update` programprzetwarzawstawione,`Command` zaktualizowane lub usunięte wiersze, używaodpowiedniejwłaściwościdoprzetwarzaniaakcji.`DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="b16db-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="b16db-108">Bieżące informacje o zmodyfikowanym wierszu są przesyłane do `Command` obiektu `Parameters` za pomocą kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b16db-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="b16db-109">Gdy aktualizujesz wiersz w źródle danych, wywołasz instrukcję UPDATE, która używa unikatowego identyfikatora, aby zidentyfikować wiersz w tabeli, która ma zostać zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="b16db-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="b16db-110">Unikatowy identyfikator jest zwykle wartością pola klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="b16db-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="b16db-111">Instrukcja UPDATE używa parametrów, które zawierają zarówno unikatowy identyfikator, jak i kolumny i wartości do zaktualizowania, jak pokazano w poniższej instrukcji języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b16db-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="b16db-112">Składnia symboli zastępczych parametrów zależy od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b16db-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="b16db-113">Ten przykład przedstawia symbole zastępcze dla SQL Servergo źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b16db-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="b16db-114">Użyj symboli zastępczych znaku zapytania (?) <xref:System.Data.OleDb> dla <xref:System.Data.Odbc> parametrów i.</span><span class="sxs-lookup"><span data-stu-id="b16db-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="b16db-115">W `CompanyName` tym Visual Basic przykładzie pole jest aktualizowane z wartością `@CompanyName` parametru wiersza, gdzie `CustomerID` jest równa wartości `@CustomerID` parametru.</span><span class="sxs-lookup"><span data-stu-id="b16db-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="b16db-116">Parametry pobierają informacje ze zmodyfikowanego wiersza przy użyciu <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> właściwości <xref:System.Data.SqlClient.SqlParameter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b16db-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="b16db-117">Poniżej przedstawiono parametry poprzedniej przykładowej instrukcji UPDATE.</span><span class="sxs-lookup"><span data-stu-id="b16db-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="b16db-118">W kodzie założono, że `adapter` zmienna reprezentuje prawidłowy <xref:System.Data.SqlClient.SqlDataAdapter> obiekt.</span><span class="sxs-lookup"><span data-stu-id="b16db-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="b16db-119">Metoda kolekcji przyjmuje nazwę parametru, typ danych, rozmiar (jeśli ma zastosowanie do typu) <xref:System.Data.Common.DbParameter.SourceColumn%2A> i `DataTable`nazwę elementu z. `Parameters` `Add`</span><span class="sxs-lookup"><span data-stu-id="b16db-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="b16db-120">Należy zauważyć, <xref:System.Data.Common.DbParameter.SourceVersion%2A> że `@CustomerID` parametr jest ustawiony na `Original`.</span><span class="sxs-lookup"><span data-stu-id="b16db-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="b16db-121">Gwarantuje to, że istniejący wiersz w źródle danych zostanie zaktualizowany, jeśli wartość kolumny lub kolumny identyfikacyjnej została zmieniona w zmodyfikowanym <xref:System.Data.DataRow>elemencie.</span><span class="sxs-lookup"><span data-stu-id="b16db-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="b16db-122">W takim przypadku `Original` wartość wiersza byłaby zgodna z bieżącą wartością w źródle danych, `Current` a wartość wiersza będzie zawierać zaktualizowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="b16db-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="b16db-123">Parametr dla parametru nie jest ustawiony `Current` i używa domyślnej wartości wiersza. `SourceVersion` `@CompanyName`</span><span class="sxs-lookup"><span data-stu-id="b16db-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b16db-124">`Fill` Dla operacji `DataAdapter` i`Get` metod ,typ.NETFrameworkjestwywnioskowanynapodstawietypuzwróconegoprzezdostawcędanych.NETFramework.`DataReader`</span><span class="sxs-lookup"><span data-stu-id="b16db-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="b16db-125">Wywnioskowane typy .NET Framework i metody dostępu dla typów danych Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowaniu typu danych w ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="b16db-125">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="b16db-126">Parameter. SourceColumn, Parameter. SourceVersion</span><span class="sxs-lookup"><span data-stu-id="b16db-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="b16db-127">I mogą być przekazane jako `Parameter`argumenty do konstruktoralubustawionejakowłaściwościistniejącegoelementu.`Parameter` `SourceVersion` `SourceColumn`</span><span class="sxs-lookup"><span data-stu-id="b16db-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="b16db-128">`Parameter` Jest nazwą <xref:System.Data.DataColumn> z<xref:System.Data.DataRow> lokalizacji, w której zostanie pobrana wartość. `SourceColumn`</span><span class="sxs-lookup"><span data-stu-id="b16db-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="b16db-129">Określa wersję `DataAdapter`używaną przez program do pobrania wartości. `DataRow` `SourceVersion`</span><span class="sxs-lookup"><span data-stu-id="b16db-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="b16db-130">W poniższej tabeli przedstawiono <xref:System.Data.DataRowVersion> wartości wyliczenia dostępne do użycia z. `SourceVersion`</span><span class="sxs-lookup"><span data-stu-id="b16db-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="b16db-131">DataRowVersion, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b16db-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="b16db-132">Opis</span><span class="sxs-lookup"><span data-stu-id="b16db-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="b16db-133">Parametr używa bieżącej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="b16db-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="b16db-134">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b16db-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="b16db-135">Parametr używa `DefaultValue` kolumny.</span><span class="sxs-lookup"><span data-stu-id="b16db-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="b16db-136">Parametr używa oryginalnej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="b16db-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="b16db-137">Parametr używa proponowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="b16db-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="b16db-138">`SourceColumn` <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> `CustomerID` `SET CustomerID = @CustomerID` `@CustomerID` `WHERE CustomerID = @OldCustomerID` `@OldCustomerID` Przykład kodu w następnej sekcji definiuje parametr, w którym kolumna jest używana jako dla dwóch parametrów: () i (). `SqlClient`</span><span class="sxs-lookup"><span data-stu-id="b16db-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="b16db-139">Ten `@CustomerID` parametr służy do aktualizowania kolumny **CustomerID** do `DataRow`bieżącej wartości w.</span><span class="sxs-lookup"><span data-stu-id="b16db-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="b16db-140">`CustomerID` W związku z tym `SourceColumn` `Current` jest używany element `SourceVersion` with a.</span><span class="sxs-lookup"><span data-stu-id="b16db-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="b16db-141">Ten `@OldCustomerID` parametr służy do identyfikowania bieżącego wiersza w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="b16db-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="b16db-142">Ponieważ pasująca wartość kolumny jest znaleziona w `Original` wersji wiersza, używana `Original` jest ta sama `SourceColumn` (`CustomerID`) z parametrem `SourceVersion` .</span><span class="sxs-lookup"><span data-stu-id="b16db-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="b16db-143">Praca z parametrami SqlClient</span><span class="sxs-lookup"><span data-stu-id="b16db-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="b16db-144">W poniższym przykładzie pokazano, jak utworzyć <xref:System.Data.SqlClient.SqlDataAdapter> i <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> ustawić do <xref:System.Data.MissingSchemaAction.AddWithKey> w celu pobrania dodatkowych informacji o schemacie z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b16db-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="b16db-145"><xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlParameter> Ustawione właściwości, ,<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> i odpowiadające im obiekty dodane do kolekcji. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A></span><span class="sxs-lookup"><span data-stu-id="b16db-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="b16db-146">Metoda zwraca `SqlDataAdapter` obiekt.</span><span class="sxs-lookup"><span data-stu-id="b16db-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="b16db-147">Symbole zastępcze parametrów OleDb</span><span class="sxs-lookup"><span data-stu-id="b16db-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="b16db-148">Dla obiektów <xref:System.Data.Odbc.OdbcDataAdapter> i należy użyć symboli zastępczych znaku zapytania (?), aby zidentyfikować parametry. <xref:System.Data.OleDb.OleDbDataAdapter></span><span class="sxs-lookup"><span data-stu-id="b16db-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="b16db-149">Sparametryzowane instrukcje zapytania definiują, które parametry wejściowe i wyjściowe muszą zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="b16db-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="b16db-150">Aby utworzyć parametr, użyj `Parameters.Add` metody `Parameter` lub konstruktora, aby określić nazwę kolumny, typ danych i rozmiar.</span><span class="sxs-lookup"><span data-stu-id="b16db-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="b16db-151">W przypadku wewnętrznych typów danych, takich `Integer`jak, nie trzeba uwzględniać rozmiaru lub można określić rozmiar domyślny.</span><span class="sxs-lookup"><span data-stu-id="b16db-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="b16db-152">Poniższy przykład kodu tworzy parametry instrukcji SQL, a następnie wypełnia `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b16db-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="b16db-153">Przykład OleDb</span><span class="sxs-lookup"><span data-stu-id="b16db-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="b16db-154">Parametry ODBC</span><span class="sxs-lookup"><span data-stu-id="b16db-154">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="b16db-155">Jeśli nazwa parametru nie jest podana dla parametru, parametr otrzymuje przyrostową domyślną nazwę parametru*N* *,* rozpoczynając od "parametr1".</span><span class="sxs-lookup"><span data-stu-id="b16db-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="b16db-156">Zalecamy uniknięcie konwencji nazewnictwa*N* parametrem w przypadku podania nazwy parametru, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą parametru w `ParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="b16db-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="b16db-157">Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b16db-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16db-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b16db-158">See also</span></span>

- [<span data-ttu-id="b16db-159">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="b16db-159">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="b16db-160">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="b16db-160">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b16db-161">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="b16db-161">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="b16db-162">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="b16db-162">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="b16db-163">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b16db-163">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="b16db-164">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b16db-164">ADO.NET Overview</span></span>](ado-net-overview.md)
