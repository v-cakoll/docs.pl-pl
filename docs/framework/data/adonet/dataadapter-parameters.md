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
# <a name="dataadapter-parameters"></a><span data-ttu-id="bf69a-102">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="bf69a-102">DataAdapter Parameters</span></span>
<span data-ttu-id="bf69a-103">Ma <xref:System.Data.Common.DbDataAdapter> cztery właściwości, które są używane do pobierania danych i aktualizacji <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> danych do źródła danych: właściwość zwraca dane ze źródła danych; i <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> i właściwości są używane do zarządzania zmianami w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bf69a-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="bf69a-104">Właściwość `SelectCommand` musi być ustawiona `Fill` przed `DataAdapter`wywołaniem metody .</span><span class="sxs-lookup"><span data-stu-id="bf69a-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="bf69a-105">`UpdateCommand`Przed `InsertCommand`wywołaniem `DeleteCommand` `Update` metody `DataAdapter` wywoływania metody , lub właściwości należy ustawić, w zależności od <xref:System.Data.DataTable>tego, jakie zmiany zostały wprowadzone w danych w pliku .</span><span class="sxs-lookup"><span data-stu-id="bf69a-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="bf69a-106">Na przykład, jeśli wiersze zostały `InsertCommand` dodane, musi `Update`być ustawiona przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="bf69a-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="bf69a-107">Podczas `Update` przetwarzania wstawionego, zaktualizowanego lub `DataAdapter` usuniętego `Command` wiersza używa odpowiedniej właściwości do przetworzenia akcji.</span><span class="sxs-lookup"><span data-stu-id="bf69a-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="bf69a-108">Bieżące informacje o zmodyfikowanym wierszu `Command` są `Parameters` przekazywane do obiektu za pośrednictwem kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bf69a-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="bf69a-109">Podczas aktualizowania wiersza w źródle danych, należy wywołać UPDATE instrukcji, która używa unikatowy identyfikator do identyfikowania wiersza w tabeli, które mają być aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="bf69a-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="bf69a-110">Unikatowy identyfikator jest zazwyczaj wartością pola klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="bf69a-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="bf69a-111">Instrukcja UPDATE używa parametrów, które zawierają zarówno unikatowy identyfikator, jak i kolumny i wartości, które mają zostać zaktualizowane, jak pokazano w poniższej instrukcji Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="bf69a-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="bf69a-112">Składnia symboli zastępczych parametrów zależy od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="bf69a-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="bf69a-113">W tym przykładzie przedstawiono symbole zastępcze dla źródła danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bf69a-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="bf69a-114">Użyj symboli zastępczych i <xref:System.Data.OleDb> <xref:System.Data.Odbc> parametrów znaku zapytania (?).</span><span class="sxs-lookup"><span data-stu-id="bf69a-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="bf69a-115">W tym przykładzie `CompanyName` języka Visual Basic pole `@CompanyName` jest aktualizowane `CustomerID` o wartość parametru `@CustomerID` dla wiersza, gdzie jest równa wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="bf69a-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="bf69a-116">Parametry pobierają informacje ze zmodyfikowanego wiersza <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> przy <xref:System.Data.SqlClient.SqlParameter> użyciu właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="bf69a-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="bf69a-117">Poniżej przedstawiono parametry poprzedniej przykładowej instrukcji UPDATE.</span><span class="sxs-lookup"><span data-stu-id="bf69a-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="bf69a-118">Kod zakłada, że `adapter` zmienna <xref:System.Data.SqlClient.SqlDataAdapter> reprezentuje prawidłowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="bf69a-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="bf69a-119">Metoda `Add` `Parameters` kolekcji przyjmuje nazwę parametru, typ danych, rozmiar (jeśli dotyczy typu) i <xref:System.Data.Common.DbParameter.SourceColumn%2A> nazwę `DataTable`z .</span><span class="sxs-lookup"><span data-stu-id="bf69a-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="bf69a-120">Należy zauważyć, <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` że parametr `Original`jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="bf69a-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="bf69a-121">Gwarantuje to, że istniejący wiersz w źródle danych zostanie zaktualizowany, jeśli wartość identyfikującej kolumny lub kolumn została zmieniona w zmodyfikowanym <xref:System.Data.DataRow>pliku .</span><span class="sxs-lookup"><span data-stu-id="bf69a-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="bf69a-122">W takim przypadku `Original` wartość wiersza będzie zgodna z bieżącą `Current` wartością w źródle danych, a wartość wiersza będzie zawierać zaktualizowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="bf69a-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="bf69a-123">Dla `SourceVersion` parametru `@CompanyName` nie jest ustawiona i `Current` używa domyślnej wartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="bf69a-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf69a-124">Dla operacji `Fill` `DataAdapter` i `Get` metod `DataReader`, .NET Framework typu jest wywnioskowane z typu zwróconego z dostawcy danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf69a-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="bf69a-125">Wywnioskowane typy programu .NET Framework i metody akcesorów dla typów danych Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowaniach typów danych w ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="bf69a-125">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="bf69a-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="bf69a-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="bf69a-127">I `SourceColumn` `SourceVersion` mogą być przekazywane jako `Parameter` argumenty do konstruktora lub `Parameter`ustawić jako właściwości istniejącego .</span><span class="sxs-lookup"><span data-stu-id="bf69a-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="bf69a-128">Jest `SourceColumn` to <xref:System.Data.DataColumn> nazwa, z <xref:System.Data.DataRow> której zostanie `Parameter` pobrana wartość.</span><span class="sxs-lookup"><span data-stu-id="bf69a-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="bf69a-129">Określa `SourceVersion` `DataRow` wersję, która `DataAdapter` używa do pobierania wartości.</span><span class="sxs-lookup"><span data-stu-id="bf69a-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="bf69a-130">W poniższej <xref:System.Data.DataRowVersion> tabeli przedstawiono wartości wyliczenia dostępne do użycia z programem `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="bf69a-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="bf69a-131">Wyliczenie DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="bf69a-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="bf69a-132">Opis</span><span class="sxs-lookup"><span data-stu-id="bf69a-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="bf69a-133">Parametr używa bieżącej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="bf69a-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="bf69a-134">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="bf69a-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="bf69a-135">Parametr używa `DefaultValue` kolumny.</span><span class="sxs-lookup"><span data-stu-id="bf69a-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="bf69a-136">Parametr używa oryginalnej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="bf69a-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="bf69a-137">Parametr używa proponowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="bf69a-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="bf69a-138">Przykład `SqlClient` kodu w następnej sekcji definiuje <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> parametr, `CustomerID` w `SourceColumn` którym kolumna jest `@CustomerID` używana`SET CustomerID = @CustomerID`jako `@OldCustomerID` `WHERE CustomerID = @OldCustomerID`dla dwóch parametrów: ( ), i ( ).</span><span class="sxs-lookup"><span data-stu-id="bf69a-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="bf69a-139">Parametr `@CustomerID` służy do aktualizowania kolumny **CustomerID** do `DataRow`bieżącej wartości w pliku .</span><span class="sxs-lookup"><span data-stu-id="bf69a-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="bf69a-140">W rezultacie stosuje `CustomerID` `SourceColumn` się `SourceVersion` `Current` z a of.</span><span class="sxs-lookup"><span data-stu-id="bf69a-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="bf69a-141">Parametr `@OldCustomerID` służy do identyfikowania bieżącego wiersza w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bf69a-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="bf69a-142">Ponieważ pasująca wartość kolumny `Original` znajduje się w wersji `SourceColumn` `CustomerID`wiersza, `SourceVersion` `Original` jest używana ta sama ( ) z of.</span><span class="sxs-lookup"><span data-stu-id="bf69a-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="bf69a-143">Praca z parametrami SqlClient</span><span class="sxs-lookup"><span data-stu-id="bf69a-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="bf69a-144">W poniższym przykładzie pokazano, jak <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> utworzyć <xref:System.Data.SqlClient.SqlDataAdapter> i ustawić do w celu pobrania dodatkowych informacji o schemacie z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bf69a-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="bf69a-145">Zestaw <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>właściwości <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> odpowiadających im <xref:System.Data.SqlClient.SqlParameter> obiektów oraz <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> ich odpowiednich obiektów.</span><span class="sxs-lookup"><span data-stu-id="bf69a-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="bf69a-146">Metoda zwraca `SqlDataAdapter` obiekt.</span><span class="sxs-lookup"><span data-stu-id="bf69a-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="bf69a-147">Symbole zastępcze parametrów OleDb</span><span class="sxs-lookup"><span data-stu-id="bf69a-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="bf69a-148">W <xref:System.Data.OleDb.OleDbDataAdapter> przypadku <xref:System.Data.Odbc.OdbcDataAdapter> obiektów i należy użyć symboli zastępczych znaku zapytania (?), aby zidentyfikować parametry.</span><span class="sxs-lookup"><span data-stu-id="bf69a-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="bf69a-149">Sparametryzowane instrukcje kwerendy określają, które parametry wejściowe i wyjściowe muszą zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="bf69a-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="bf69a-150">Aby utworzyć parametr, `Parameters.Add` należy użyć `Parameter` metody lub konstruktora, aby określić nazwę kolumny, typ danych i rozmiar.</span><span class="sxs-lookup"><span data-stu-id="bf69a-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="bf69a-151">W przypadku wewnętrznych typów danych, `Integer`takich jak , nie trzeba uwzględniać rozmiaru lub można określić rozmiar domyślny.</span><span class="sxs-lookup"><span data-stu-id="bf69a-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="bf69a-152">Poniższy przykład kodu tworzy parametry instrukcji SQL, `DataSet`a następnie wypełnia plik .</span><span class="sxs-lookup"><span data-stu-id="bf69a-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="bf69a-153">Przykład OleDb</span><span class="sxs-lookup"><span data-stu-id="bf69a-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="bf69a-154">Parametry Odbc</span><span class="sxs-lookup"><span data-stu-id="bf69a-154">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="bf69a-155">Jeśli nazwa parametru nie jest podana dla parametru, parametr otrzymuje przyrostową domyślną nazwę parametru*N,* *,* zaczynając od "Parametr1".</span><span class="sxs-lookup"><span data-stu-id="bf69a-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="bf69a-156">Zaleca się unikanie konwencji nazewnictwa parametru*N* podczas podawania nazwy parametru, ponieważ podana `ParameterCollection`nazwa może kolidować z istniejącą domyślną nazwą parametru w pliku .</span><span class="sxs-lookup"><span data-stu-id="bf69a-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="bf69a-157">Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="bf69a-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf69a-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf69a-158">See also</span></span>

- [<span data-ttu-id="bf69a-159">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="bf69a-159">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="bf69a-160">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="bf69a-160">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="bf69a-161">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="bf69a-161">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="bf69a-162">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="bf69a-162">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="bf69a-163">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bf69a-163">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="bf69a-164">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bf69a-164">ADO.NET Overview</span></span>](ado-net-overview.md)
