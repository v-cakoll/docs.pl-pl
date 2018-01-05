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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e42f6ef0f2416822f42d2c73032631965b9bb097
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="8b3bd-102">Element DataAdapter parametrów</span><span class="sxs-lookup"><span data-stu-id="8b3bd-102">DataAdapter Parameters</span></span>
<span data-ttu-id="8b3bd-103"><xref:System.Data.Common.DbDataAdapter> Ma cztery właściwości, które są używane do pobierania danych z danych i aktualizowanie źródła danych: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> właściwość zwraca dane ze źródła danych; i <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, i <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> właściwości są używane do zarządzania zmiany w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="8b3bd-104">`SelectCommand` Należy ustawić właściwość przed wywołaniem `Fill` metody `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="8b3bd-105">`InsertCommand`, `UpdateCommand`, Lub `DeleteCommand` właściwości musi być ustawiona przed `Update` metody `DataAdapter` jest wywoływana w zależności od tego, jakie zmiany wprowadzono w danych w <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="8b3bd-106">Na przykład, jeśli wiersze zostały dodane `InsertCommand` musi być ustawiona przed wywołaniem `Update`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="8b3bd-107">Gdy `Update` przetwarza wierszy wstawionych, zaktualizowanych lub usuniętych `DataAdapter` używa odpowiednio `Command` właściwości do przetworzenia akcji.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="8b3bd-108">Bieżące informacje o zmodyfikowanych wierszy jest przekazywana do `Command` obiektu za pomocą `Parameters` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="8b3bd-109">Podczas aktualizowania wierszy w źródle danych, należy wywołać instrukcji UPDATE, która jest używana Unikatowy identyfikator wiersza w tabeli można zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table be updated.</span></span> <span data-ttu-id="8b3bd-110">Unikatowy identyfikator jest zwykle wartość pola klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="8b3bd-111">Instrukcja UPDATE używa parametrów, które zawierają zarówno Unikatowy identyfikator, kolumny i wartości do aktualizacji, jak pokazano w poniższych instrukcji języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  <span data-ttu-id="8b3bd-112">Składnia parametru symbole zastępcze zależy od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="8b3bd-113">Ten przykład przedstawia symbole zastępcze dla źródła danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="8b3bd-114">Użyj symbole zastępcze znak zapytania (?) <xref:System.Data.OleDb> i <xref:System.Data.Odbc> parametrów.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="8b3bd-115">W tym [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] przykład `CompanyName` jest aktualizowana wartość `@CompanyName` parametr wiersza gdzie `CustomerID` jest równa wartości `@CustomerID` parametru.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-115">In this [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="8b3bd-116">Parametry pobrania informacji z przy użyciu zmodyfikowanych wierszy <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> właściwość <xref:System.Data.SqlClient.SqlParameter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="8b3bd-117">Poniżej przedstawiono parametry poprzedniej próbki instrukcji UPDATE.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="8b3bd-118">Kod, przy założeniu, że zmienna `adapter` reprezentuje prawidłową <xref:System.Data.SqlClient.SqlDataAdapter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="8b3bd-119">`Add` Metody `Parameters` kolekcji przyjmuje nazwę parametru, typu danych, rozmiaru (jeśli ma zastosowanie do typu), a nazwa <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="8b3bd-120">Zwróć uwagę, że <xref:System.Data.Common.DbParameter.SourceVersion%2A> z `@CustomerID` ustawiono parametr `Original`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="8b3bd-121">Gwarantuje to, że istniejący wiersz w źródle danych został zaktualizowany, jeśli wartość identyfikacyjne kolumny lub kolumn została zmieniona w modyfikacji <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="8b3bd-122">W takim przypadku `Original` wartość wiersza czy pasuje do bieżącej wartości w źródle danych i `Current` wartość wiersza zawierałoby zaktualizowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="8b3bd-123">`SourceVersion` Dla `@CompanyName` parametru nie jest ustawiona i stosuje domyślną, `Current` wiersza wartości.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b3bd-124">Dla obu `Fill` operacji `DataAdapter` i `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu jest wywnioskowany na podstawie zwrócone przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the type returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="8b3bd-125">Wywnioskowane [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów i metod typu accessor dla typów danych Microsoft SQL Server, OLE DB i ODBC są opisane w [mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="8b3bd-125">The inferred [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="8b3bd-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="8b3bd-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="8b3bd-127">`SourceColumn` i `SourceVersion` mogą być przekazywane jako argumenty do `Parameter` konstruktora lub Ustaw jako właściwości istniejącego `Parameter`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="8b3bd-128">`SourceColumn` Jest nazwą <xref:System.Data.DataColumn> z <xref:System.Data.DataRow> gdzie wartość `Parameter` zostaną pobrane.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="8b3bd-129">`SourceVersion` Określa `DataRow` wersji który `DataAdapter` używane do pobierania wartości.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="8b3bd-130">W poniższej tabeli przedstawiono <xref:System.Data.DataRowVersion> wartości wyliczenia są dostępne do użycia z `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="8b3bd-131">DataRowVersion — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8b3bd-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="8b3bd-132">Opis</span><span class="sxs-lookup"><span data-stu-id="8b3bd-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="8b3bd-133">Parametr korzysta z bieżącej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="8b3bd-134">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="8b3bd-135">Używa parametru `DefaultValue` kolumny.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="8b3bd-136">Parametr używa oryginalnej wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="8b3bd-137">Parametr używa proponowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="8b3bd-138">`SqlClient` Przykładowy kod w następnej sekcji definiuje parametru <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> w którym `CustomerID` kolumna jest używana jako `SourceColumn` dwa parametry: `@CustomerID` (`SET CustomerID = @CustomerID`), i `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span><span class="sxs-lookup"><span data-stu-id="8b3bd-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="8b3bd-139">`@CustomerID` Parametr jest używany do zaktualizowania **CustomerID** kolumny do bieżącej wartości `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="8b3bd-140">W związku z tym `CustomerID` `SourceColumn` z `SourceVersion` z `Current` jest używany.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="8b3bd-141"> *@OldCustomerID*  Parametr jest używany do identyfikowania bieżący wiersz w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-141">The *@OldCustomerID* parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="8b3bd-142">Ponieważ odnaleziono pasującej wartości kolumny w `Original` wersji wiersza, w taki sam `SourceColumn` (`CustomerID`) z `SourceVersion` z `Original` jest używany.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="8b3bd-143">Praca z parametrami SqlClient</span><span class="sxs-lookup"><span data-stu-id="8b3bd-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="8b3bd-144">Poniższy przykład przedstawia sposób tworzenia <xref:System.Data.SqlClient.SqlDataAdapter> i ustaw <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> do <xref:System.Data.MissingSchemaAction.AddWithKey> w celu pobrania dodatkowe informacje o schemacie z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="8b3bd-145"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, I <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> zestaw właściwości i odpowiadające <xref:System.Data.SqlClient.SqlParameter> obiekty dodane do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="8b3bd-146">Metoda zwraca `SqlDataAdapter` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="8b3bd-147">Symbole zastępcze parametru OleDb</span><span class="sxs-lookup"><span data-stu-id="8b3bd-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="8b3bd-148">Aby uzyskać <xref:System.Data.OleDb.OleDbDataAdapter> i <xref:System.Data.Odbc.OdbcDataAdapter> obiektów, aby zidentyfikować parametrów, należy użyć symbole zastępcze znak zapytania (?).</span><span class="sxs-lookup"><span data-stu-id="8b3bd-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="8b3bd-149">Instrukcje zapytania parametrycznego zdefiniować, którego dane wejściowe i parametry wyjściowe muszą zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="8b3bd-150">Aby utworzyć parametr, należy użyć `Parameters.Add` metody lub `Parameter` konstruktora, aby określić nazwę kolumny, typ danych i rozmiar.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="8b3bd-151">Dla typów danych wewnętrznych takich jak `Integer`, nie trzeba uwzględnić rozmiar lub można określić domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="8b3bd-152">Poniższy przykład kodu tworzy parametry instrukcji SQL i następnie wypełnia `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="8b3bd-153">Przykład OleDb</span><span class="sxs-lookup"><span data-stu-id="8b3bd-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="8b3bd-154">Parametry ODBC</span><span class="sxs-lookup"><span data-stu-id="8b3bd-154">Odbc Parameters</span></span>  
  
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
>  <span data-ttu-id="8b3bd-155">Jeśli nie podano nazwy parametru dla parametru, parametr podano przyrostowe domyślną nazwę parametru*N* *,* począwszy od "Parameter1".</span><span class="sxs-lookup"><span data-stu-id="8b3bd-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="8b3bd-156">Firma Microsoft zaleca, aby uniknąć parametr*N* konwencji nazewnictwa Jeśli podasz nazwę parametru, ponieważ nazwa wprowadzona może powodować konflikt z istniejącą nazwą parametru domyślnego w `ParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="8b3bd-157">Jeśli podanej nazwie już istnieje, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8b3bd-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3bd-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b3bd-158">See Also</span></span>  
 [<span data-ttu-id="8b3bd-159">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="8b3bd-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="8b3bd-160">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="8b3bd-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="8b3bd-161">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="8b3bd-161">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="8b3bd-162">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="8b3bd-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="8b3bd-163">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8b3bd-163">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="8b3bd-164">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="8b3bd-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
