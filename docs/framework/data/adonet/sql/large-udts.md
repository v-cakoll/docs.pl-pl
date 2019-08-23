---
title: Duże UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 97df0bee10440dd03f07b980589d9dda85ce121e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909880"
---
# <a name="large-udts"></a><span data-ttu-id="2519a-102">Duże UDT</span><span class="sxs-lookup"><span data-stu-id="2519a-102">Large UDTs</span></span>
<span data-ttu-id="2519a-103">Typy zdefiniowane przez użytkownika (UDTs) umożliwiają deweloperom rozbudowa systemu typu skalarnego serwera przez przechowywanie obiektów środowiska uruchomieniowego języka wspólnego (CLR) w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2519a-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="2519a-104">UDTs może zawierać wiele elementów i może mieć zachowania, w przeciwieństwie do tradycyjnych typów danych aliasów, które składają się z jednego typu danych systemu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2519a-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2519a-105">Aby skorzystać z rozszerzonej obsługi SqlClient dla dużych UDTs, należy zainstalować .NET Framework 3,5 SP1 (lub nowsze).</span><span class="sxs-lookup"><span data-stu-id="2519a-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="2519a-106">Wcześniej UDTs były ograniczone do maksymalnego rozmiaru wynoszącego 8 kilobajtów.</span><span class="sxs-lookup"><span data-stu-id="2519a-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="2519a-107">W SQL Server 2008 to ograniczenie zostało usunięte dla UDTs o formacie <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="2519a-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="2519a-108">Aby zapoznać się z pełną dokumentacją typów zdefiniowanych przez użytkownika, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2519a-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="2519a-109">**Książka SQL Server online**</span><span class="sxs-lookup"><span data-stu-id="2519a-109">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="2519a-110">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="2519a-110">CLR User-Defined Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="2519a-111">Pobieranie schematów UDT przy użyciu GetSchema</span><span class="sxs-lookup"><span data-stu-id="2519a-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="2519a-112">Metoda zwraca informacje o schemacie <xref:System.Data.DataTable>bazy danych w. <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A></span><span class="sxs-lookup"><span data-stu-id="2519a-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="2519a-113">Aby uzyskać więcej informacji, zobacz [SQL Server kolekcje schematów](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="2519a-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="2519a-114">Wartości kolumn getschemacollection dla UDTs</span><span class="sxs-lookup"><span data-stu-id="2519a-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="2519a-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metoda zwraca,<xref:System.Data.DataTable> która opisuje metadane kolumn. <xref:System.Data.SqlClient.SqlDataReader></span><span class="sxs-lookup"><span data-stu-id="2519a-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="2519a-116">W poniższej tabeli opisano różnice w metadanych kolumn dla dużych UDTs między SQL Server 2005 i SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="2519a-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="2519a-117">SqlDataReader — kolumna</span><span class="sxs-lookup"><span data-stu-id="2519a-117">SqlDataReader column</span></span>|<span data-ttu-id="2519a-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="2519a-118">SQL Server 2005</span></span>|<span data-ttu-id="2519a-119">SQL Server 2008 i nowsze</span><span class="sxs-lookup"><span data-stu-id="2519a-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="2519a-120">Różni się</span><span class="sxs-lookup"><span data-stu-id="2519a-120">Varies</span></span>|<span data-ttu-id="2519a-121">Różni się</span><span class="sxs-lookup"><span data-stu-id="2519a-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="2519a-122">255</span><span class="sxs-lookup"><span data-stu-id="2519a-122">255</span></span>|<span data-ttu-id="2519a-123">255</span><span class="sxs-lookup"><span data-stu-id="2519a-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="2519a-124">255</span><span class="sxs-lookup"><span data-stu-id="2519a-124">255</span></span>|<span data-ttu-id="2519a-125">255</span><span class="sxs-lookup"><span data-stu-id="2519a-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="2519a-126">Wystąpienie UDT</span><span class="sxs-lookup"><span data-stu-id="2519a-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="2519a-127">Wystąpienie UDT</span><span class="sxs-lookup"><span data-stu-id="2519a-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="2519a-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="2519a-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="2519a-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="2519a-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="2519a-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="2519a-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="2519a-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="2519a-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="2519a-132">Nazwa trzech części określona jako *Database. SchemaName. TypeName*.</span><span class="sxs-lookup"><span data-stu-id="2519a-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="2519a-133">Różni się</span><span class="sxs-lookup"><span data-stu-id="2519a-133">Varies</span></span>|<span data-ttu-id="2519a-134">Różni się</span><span class="sxs-lookup"><span data-stu-id="2519a-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="2519a-135">Zagadnienia dotyczące elementu SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="2519a-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="2519a-136"><xref:System.Data.SqlClient.SqlDataReader> Została rozszerzona począwszy od SQL Server 2008, aby obsługiwała pobieranie dużych wartości UDT.</span><span class="sxs-lookup"><span data-stu-id="2519a-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="2519a-137">Jak duże wartości UDT są przetwarzane przez <xref:System.Data.SqlClient.SqlDataReader> zależą od używanej wersji SQL Server, a także `Type System Version` od określonego w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="2519a-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="2519a-138">Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="2519a-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="2519a-139">Następujące metody <xref:System.Data.SqlClient.SqlDataReader> będą <xref:System.Data.SqlTypes.SqlBinary> zwracały zamiast UDT, gdy `Type System Version` ustawiono wartość SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="2519a-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="2519a-140">Następujące metody zwracają tablicę `Byte[]` zamiast UDT, `Type System Version` gdy ustawiono wartość SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="2519a-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="2519a-141">Należy zauważyć, że nie są wykonywane żadne konwersje dla bieżącej wersji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="2519a-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="2519a-142">Specifying SqlParameters</span><span class="sxs-lookup"><span data-stu-id="2519a-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="2519a-143">Następujące <xref:System.Data.SqlClient.SqlParameter> właściwości zostały rozszerzone, aby współpracować z dużymi UDTs.</span><span class="sxs-lookup"><span data-stu-id="2519a-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="2519a-144">Właściwość SqlParameter</span><span class="sxs-lookup"><span data-stu-id="2519a-144">SqlParameter Property</span></span>|<span data-ttu-id="2519a-145">Opis</span><span class="sxs-lookup"><span data-stu-id="2519a-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="2519a-146">Pobiera lub ustawia obiekt, który reprezentuje wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="2519a-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="2519a-147">Domyślny ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2519a-147">The default is null.</span></span> <span data-ttu-id="2519a-148">Właściwość może mieć wartość `SqlBinary`lub `Byte[]`być obiektem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="2519a-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="2519a-149">Pobiera lub ustawia obiekt, który reprezentuje wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="2519a-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="2519a-150">Domyślny ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2519a-150">The default is null.</span></span> <span data-ttu-id="2519a-151">Właściwość może mieć wartość `SqlBinary`lub `Byte[]`być obiektem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="2519a-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="2519a-152">Pobiera lub ustawia rozmiar wartości parametru, który ma zostać rozpoznany.</span><span class="sxs-lookup"><span data-stu-id="2519a-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="2519a-153">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="2519a-153">The default value is 0.</span></span> <span data-ttu-id="2519a-154">Właściwość może być liczbą całkowitą reprezentującą rozmiar wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="2519a-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="2519a-155">W przypadku dużych UDTs może to być rzeczywisty rozmiar UDT lub-1 dla nieznane.</span><span class="sxs-lookup"><span data-stu-id="2519a-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="2519a-156">Przykład pobierania danych</span><span class="sxs-lookup"><span data-stu-id="2519a-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="2519a-157">Poniższy fragment kodu pokazuje, jak pobrać duże dane UDT.</span><span class="sxs-lookup"><span data-stu-id="2519a-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="2519a-158">Zmienna zakłada prawidłowe połączenie z bazą danych SQL Server `commandString` , a zmienna przyjmuje prawidłową instrukcję SELECT z kolumną klucza podstawowego na liście. `connectionString`</span><span class="sxs-lookup"><span data-stu-id="2519a-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="2519a-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2519a-159">See also</span></span>

- [<span data-ttu-id="2519a-160">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="2519a-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="2519a-161">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="2519a-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="2519a-162">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="2519a-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="2519a-163">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="2519a-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="2519a-164">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2519a-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
