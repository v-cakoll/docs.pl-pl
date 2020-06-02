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
# <a name="dataadapter-parameters"></a><span data-ttu-id="2471f-103">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="2471f-103">DataAdapter Parameters</span></span>
<span data-ttu-id="2471f-104"><xref:System.Data.Common.DbDataAdapter>Ma cztery właściwości, które są używane do pobierania danych z i aktualizowania danych do źródła danych: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> Właściwość zwraca dane ze źródła danych, a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> właściwości, i <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> są używane do zarządzania zmianami w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="2471f-104">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="2471f-105">`SelectCommand`Właściwość musi być ustawiona przed wywołaniem `Fill` metody `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="2471f-105">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="2471f-106">`InsertCommand`Właściwości, `UpdateCommand` , lub `DeleteCommand` muszą być ustawione przed `Update` `DataAdapter` wywołaniem metody, w zależności od tego, jakie zmiany zostały wprowadzone do danych w <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="2471f-106">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="2471f-107">Na przykład, jeśli dodano wiersze, `InsertCommand` należy ustawić przed wywołaniem metody `Update` .</span><span class="sxs-lookup"><span data-stu-id="2471f-107">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="2471f-108">Gdy `Update` program przetwarza wstawione, zaktualizowane lub usunięte wiersze, `DataAdapter` używa odpowiedniej `Command` właściwości do przetwarzania akcji.</span><span class="sxs-lookup"><span data-stu-id="2471f-108">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="2471f-109">Bieżące informacje o zmodyfikowanym wierszu są przesyłane do `Command` obiektu za pomocą `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2471f-109">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="2471f-110">Gdy aktualizujesz wiersz w źródle danych, wywołasz instrukcję UPDATE, która używa unikatowego identyfikatora, aby zidentyfikować wiersz w tabeli, która ma zostać zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="2471f-110">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="2471f-111">Unikatowy identyfikator jest zwykle wartością pola klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="2471f-111">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="2471f-112">Instrukcja UPDATE używa parametrów, które zawierają zarówno unikatowy identyfikator, jak i kolumny i wartości do zaktualizowania, jak pokazano w poniższej instrukcji języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="2471f-112">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="2471f-113">Składnia symboli zastępczych parametrów zależy od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2471f-113">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="2471f-114">Ten przykład przedstawia symbole zastępcze dla SQL Servergo źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2471f-114">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="2471f-115">Użyj symboli zastępczych znaku zapytania (?) <xref:System.Data.OleDb> dla <xref:System.Data.Odbc> parametrów i.</span><span class="sxs-lookup"><span data-stu-id="2471f-115">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="2471f-116">W tym Visual Basic przykładzie `CompanyName` pole jest aktualizowane z wartością `@CompanyName` parametru wiersza, gdzie jest `CustomerID` równa wartości `@CustomerID` parametru.</span><span class="sxs-lookup"><span data-stu-id="2471f-116">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="2471f-117">Parametry pobierają informacje ze zmodyfikowanego wiersza przy użyciu <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> właściwości <xref:System.Data.SqlClient.SqlParameter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2471f-117">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="2471f-118">Poniżej przedstawiono parametry poprzedniej przykładowej instrukcji UPDATE.</span><span class="sxs-lookup"><span data-stu-id="2471f-118">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="2471f-119">W kodzie założono, że zmienna `adapter` reprezentuje prawidłowy <xref:System.Data.SqlClient.SqlDataAdapter> obiekt.</span><span class="sxs-lookup"><span data-stu-id="2471f-119">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="2471f-120">`Add`Metoda `Parameters` kolekcji przyjmuje nazwę parametru, typ danych, rozmiar (jeśli ma zastosowanie do typu) i nazwę elementu <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="2471f-120">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="2471f-121">Należy zauważyć, że <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` parametr jest ustawiony na `Original` .</span><span class="sxs-lookup"><span data-stu-id="2471f-121">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="2471f-122">Gwarantuje to, że istniejący wiersz w źródle danych zostanie zaktualizowany, jeśli wartość kolumny lub kolumny identyfikacyjnej została zmieniona w zmodyfikowanym elemencie <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="2471f-122">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="2471f-123">W takim przypadku `Original` wartość wiersza byłaby zgodna z bieżącą wartością w źródle danych, a `Current` wartość wiersza będzie zawierać zaktualizowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="2471f-123">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="2471f-124">`SourceVersion` `@CompanyName` Parametr dla parametru nie jest ustawiony i używa domyślnej `Current` wartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="2471f-124">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2471f-125">Dla `Fill` operacji `DataAdapter` i `Get` metod `DataReader` , typ .NET Framework jest wywnioskowany na podstawie typu zwróconego przez dostawcę danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2471f-125">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="2471f-126">Wywnioskowane typy .NET Framework i metody dostępu dla typów danych Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowaniu typu danych w ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="2471f-126">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="2471f-127">Parameter. SourceColumn, Parameter. SourceVersion</span><span class="sxs-lookup"><span data-stu-id="2471f-127">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="2471f-128">`SourceColumn`I `SourceVersion` mogą być przekazane jako argumenty do `Parameter` konstruktora lub ustawione jako właściwości istniejącego elementu `Parameter` .</span><span class="sxs-lookup"><span data-stu-id="2471f-128">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="2471f-129">`SourceColumn`Jest nazwą z lokalizacji, w <xref:System.Data.DataColumn> <xref:System.Data.DataRow> której `Parameter` zostanie pobrana wartość.</span><span class="sxs-lookup"><span data-stu-id="2471f-129">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="2471f-130">`SourceVersion`Określa `DataRow` wersję używaną przez program `DataAdapter` do pobrania wartości.</span><span class="sxs-lookup"><span data-stu-id="2471f-130">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="2471f-131">W poniższej tabeli przedstawiono <xref:System.Data.DataRowVersion> wartości wyliczenia dostępne do użycia z `SourceVersion` .</span><span class="sxs-lookup"><span data-stu-id="2471f-131">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="2471f-132">DataRowVersion, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2471f-132">DataRowVersion Enumeration</span></span>|<span data-ttu-id="2471f-133">Opis</span><span class="sxs-lookup"><span data-stu-id="2471f-133">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="2471f-134">Parametr używa bieżącej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="2471f-134">The parameter uses the current value of the column.</span></span> <span data-ttu-id="2471f-135">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="2471f-135">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="2471f-136">Parametr używa `DefaultValue` kolumny.</span><span class="sxs-lookup"><span data-stu-id="2471f-136">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="2471f-137">Parametr używa oryginalnej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="2471f-137">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="2471f-138">Parametr używa proponowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="2471f-138">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="2471f-139">`SqlClient`Przykład kodu w następnej sekcji definiuje parametr, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> w którym `CustomerID` kolumna jest używana jako `SourceColumn` dla dwóch parametrów: `@CustomerID` ( `SET CustomerID = @CustomerID` ) i `@OldCustomerID` ( `WHERE CustomerID = @OldCustomerID` ).</span><span class="sxs-lookup"><span data-stu-id="2471f-139">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="2471f-140">Ten `@CustomerID` parametr służy do aktualizowania kolumny **CustomerID** do bieżącej wartości w `DataRow` .</span><span class="sxs-lookup"><span data-stu-id="2471f-140">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="2471f-141">W związku z tym `CustomerID` `SourceColumn` jest używany element with a `SourceVersion` `Current` .</span><span class="sxs-lookup"><span data-stu-id="2471f-141">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="2471f-142">Ten `@OldCustomerID` parametr służy do identyfikowania bieżącego wiersza w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="2471f-142">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="2471f-143">Ponieważ pasująca wartość kolumny jest znaleziona w `Original` wersji wiersza, używana jest ta sama `SourceColumn` ( `CustomerID` ) z parametrem `SourceVersion` `Original` .</span><span class="sxs-lookup"><span data-stu-id="2471f-143">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="2471f-144">Praca z parametrami SqlClient</span><span class="sxs-lookup"><span data-stu-id="2471f-144">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="2471f-145">W poniższym przykładzie pokazano, jak utworzyć <xref:System.Data.SqlClient.SqlDataAdapter> i ustawić <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> do w celu <xref:System.Data.MissingSchemaAction.AddWithKey> pobrania dodatkowych informacji o schemacie z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2471f-145">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="2471f-146"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> Ustawione właściwości,,, i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> odpowiadające im <xref:System.Data.SqlClient.SqlParameter> obiekty dodane do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2471f-146">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="2471f-147">Metoda zwraca `SqlDataAdapter` obiekt.</span><span class="sxs-lookup"><span data-stu-id="2471f-147">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="2471f-148">Symbole zastępcze parametrów OleDb</span><span class="sxs-lookup"><span data-stu-id="2471f-148">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="2471f-149">Dla <xref:System.Data.OleDb.OleDbDataAdapter> obiektów i należy <xref:System.Data.Odbc.OdbcDataAdapter> użyć symboli zastępczych znaku zapytania (?), aby zidentyfikować parametry.</span><span class="sxs-lookup"><span data-stu-id="2471f-149">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="2471f-150">Sparametryzowane instrukcje zapytania definiują, które parametry wejściowe i wyjściowe muszą zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="2471f-150">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="2471f-151">Aby utworzyć parametr, użyj `Parameters.Add` metody lub `Parameter` konstruktora, aby określić nazwę kolumny, typ danych i rozmiar.</span><span class="sxs-lookup"><span data-stu-id="2471f-151">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="2471f-152">W przypadku wewnętrznych typów danych, takich jak `Integer` , nie trzeba uwzględniać rozmiaru lub można określić rozmiar domyślny.</span><span class="sxs-lookup"><span data-stu-id="2471f-152">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="2471f-153">Poniższy przykład kodu tworzy parametry instrukcji SQL, a następnie wypełnia `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="2471f-153">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="2471f-154">Przykład OleDb</span><span class="sxs-lookup"><span data-stu-id="2471f-154">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="2471f-155">Parametry ODBC</span><span class="sxs-lookup"><span data-stu-id="2471f-155">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="2471f-156">Jeśli nazwa parametru nie jest podana dla parametru, parametr otrzymuje przyrostową domyślną nazwę parametru*N* *,* rozpoczynając od "parametr1".</span><span class="sxs-lookup"><span data-stu-id="2471f-156">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="2471f-157">Zalecamy uniknięcie konwencji nazewnictwa*N* parametrem w przypadku podania nazwy parametru, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą parametru w `ParameterCollection` .</span><span class="sxs-lookup"><span data-stu-id="2471f-157">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="2471f-158">Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2471f-158">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2471f-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2471f-159">See also</span></span>

- [<span data-ttu-id="2471f-160">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="2471f-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="2471f-161">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="2471f-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="2471f-162">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="2471f-162">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="2471f-163">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="2471f-163">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="2471f-164">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2471f-164">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="2471f-165">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2471f-165">ADO.NET Overview</span></span>](ado-net-overview.md)
