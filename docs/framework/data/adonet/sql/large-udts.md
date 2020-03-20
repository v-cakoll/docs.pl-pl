---
title: Duże UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: f55f6eccf3566a2391204e1ca4349ae5dff01954
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148559"
---
# <a name="large-udts"></a><span data-ttu-id="dc9fb-102">Duże UDT</span><span class="sxs-lookup"><span data-stu-id="dc9fb-102">Large UDTs</span></span>
<span data-ttu-id="dc9fb-103">Typy zdefiniowane przez użytkownika (UDTs) umożliwiają deweloperowi rozszerzenie systemu typu skalarnego serwera przez przechowywanie obiektów wspólnego środowiska wykonawczego języka (CLR) w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="dc9fb-104">UDTs może zawierać wiele elementów i może mieć zachowania, w przeciwieństwie do tradycyjnych typów danych alias, które składają się z jednego typu danych systemu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc9fb-105">Należy zainstalować .NET Framework 3.5 SP1 (lub nowsze), aby skorzystać z rozszerzonej obsługi SqlClient dla dużych UDTs.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="dc9fb-106">Wcześniej UDTs były ograniczone do maksymalnego rozmiaru 8 kilobajtów.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="dc9fb-107">W programie SQL Server 2008 to ograniczenie zostało usunięte dla <xref:Microsoft.SqlServer.Server.Format.UserDefined>UDTs, które mają format .</span><span class="sxs-lookup"><span data-stu-id="dc9fb-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="dc9fb-108">Aby uzyskać pełną dokumentację typów zdefiniowanych przez użytkownika, zobacz wersję programu SQL Server Books Online dla używanej wersji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="dc9fb-109">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="dc9fb-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="dc9fb-110">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="dc9fb-110">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="dc9fb-111">Pobieranie schematów UDT przy użyciu getschema</span><span class="sxs-lookup"><span data-stu-id="dc9fb-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="dc9fb-112">Metoda <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:System.Data.SqlClient.SqlConnection> zwraca informacje o schemacie bazy danych w pliku <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="dc9fb-113">Aby uzyskać więcej informacji, zobacz [Kolekcje schematów programu SQL Server](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="dc9fb-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="dc9fb-114">Wartości kolumny GetSchemaTable dla UDTs</span><span class="sxs-lookup"><span data-stu-id="dc9fb-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="dc9fb-115">Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> <xref:System.Data.SqlClient.SqlDataReader> zwraca, <xref:System.Data.DataTable> który opisuje metadane kolumny.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="dc9fb-116">W poniższej tabeli opisano różnice w metadanych kolumn dla dużych UDTs między SQL Server 2005 i SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="dc9fb-117">Kolumna SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="dc9fb-117">SqlDataReader column</span></span>|<span data-ttu-id="dc9fb-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="dc9fb-118">SQL Server 2005</span></span>|<span data-ttu-id="dc9fb-119">SQL Server 2008 i nowsze</span><span class="sxs-lookup"><span data-stu-id="dc9fb-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="dc9fb-120">Różna</span><span class="sxs-lookup"><span data-stu-id="dc9fb-120">Varies</span></span>|<span data-ttu-id="dc9fb-121">Różna</span><span class="sxs-lookup"><span data-stu-id="dc9fb-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="dc9fb-122">255</span><span class="sxs-lookup"><span data-stu-id="dc9fb-122">255</span></span>|<span data-ttu-id="dc9fb-123">255</span><span class="sxs-lookup"><span data-stu-id="dc9fb-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="dc9fb-124">255</span><span class="sxs-lookup"><span data-stu-id="dc9fb-124">255</span></span>|<span data-ttu-id="dc9fb-125">255</span><span class="sxs-lookup"><span data-stu-id="dc9fb-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="dc9fb-126">Wystąpienie UDT</span><span class="sxs-lookup"><span data-stu-id="dc9fb-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="dc9fb-127">Wystąpienie UDT</span><span class="sxs-lookup"><span data-stu-id="dc9fb-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="dc9fb-128">21`SqlDbType.VarBinary`( )</span><span class="sxs-lookup"><span data-stu-id="dc9fb-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="dc9fb-129">29`SqlDbType.Udt`( )</span><span class="sxs-lookup"><span data-stu-id="dc9fb-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="dc9fb-130">29`SqlDbType.Udt`( )</span><span class="sxs-lookup"><span data-stu-id="dc9fb-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="dc9fb-131">29`SqlDbType.Udt`( )</span><span class="sxs-lookup"><span data-stu-id="dc9fb-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="dc9fb-132">Nazwa trzech części określona jako *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="dc9fb-133">Różna</span><span class="sxs-lookup"><span data-stu-id="dc9fb-133">Varies</span></span>|<span data-ttu-id="dc9fb-134">Różna</span><span class="sxs-lookup"><span data-stu-id="dc9fb-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="dc9fb-135">Zagadnienia dotyczące programu SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="dc9fb-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="dc9fb-136">Został <xref:System.Data.SqlClient.SqlDataReader> rozszerzony począwszy od programu SQL Server 2008 do obsługi pobierania dużych wartości UDT.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="dc9fb-137">Jak duże wartości UDT są <xref:System.Data.SqlClient.SqlDataReader> przetwarzane przez a zależy od wersji programu SQL `Type System Version` Server, którego używasz, a także od określonych w ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="dc9fb-138">Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="dc9fb-139">Następujące metody <xref:System.Data.SqlClient.SqlDataReader> zwróci <xref:System.Data.SqlTypes.SqlBinary> zamiast UDT, gdy `Type System Version` jest ustawiona na SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="dc9fb-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="dc9fb-140">Następujące metody zwróci tablicy `Byte[]` zamiast UDT, gdy `Type System Version` jest ustawiona na SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="dc9fb-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="dc9fb-141">Pamiętaj, że dla bieżącej wersji ADO.NET nie są dokonywane żadne konwersje.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="dc9fb-142">Określanie parametrów SqlParameters</span><span class="sxs-lookup"><span data-stu-id="dc9fb-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="dc9fb-143">Następujące <xref:System.Data.SqlClient.SqlParameter> właściwości zostały rozszerzone do pracy z dużymi UDTs.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="dc9fb-144">Właściwość sqlparameter</span><span class="sxs-lookup"><span data-stu-id="dc9fb-144">SqlParameter Property</span></span>|<span data-ttu-id="dc9fb-145">Opis</span><span class="sxs-lookup"><span data-stu-id="dc9fb-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="dc9fb-146">Pobiera lub ustawia obiekt, który reprezentuje wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="dc9fb-147">Domyślny ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-147">The default is null.</span></span> <span data-ttu-id="dc9fb-148">Właściwość może `SqlBinary` `Byte[]`być , lub obiekt zarządzany.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="dc9fb-149">Pobiera lub ustawia obiekt, który reprezentuje wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="dc9fb-150">Domyślny ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-150">The default is null.</span></span> <span data-ttu-id="dc9fb-151">Właściwość może `SqlBinary` `Byte[]`być , lub obiekt zarządzany.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="dc9fb-152">Pobiera lub ustawia rozmiar wartości parametru do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="dc9fb-153">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-153">The default value is 0.</span></span> <span data-ttu-id="dc9fb-154">Właściwość może być liczebną, która reprezentuje rozmiar wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="dc9fb-155">W przypadku dużych UDT może to być rzeczywisty rozmiar UDT lub -1 dla nieznanych.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="dc9fb-156">Przykład pobierania danych</span><span class="sxs-lookup"><span data-stu-id="dc9fb-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="dc9fb-157">Poniższy fragment kodu pokazuje, jak pobrać duże dane UDT.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="dc9fb-158">Zmienna `connectionString` zakłada prawidłowe połączenie z bazą `commandString` danych programu SQL Server, a zmienna przyjmuje prawidłową instrukcję SELECT z kolumną klucza podstawowego wymienioną jako pierwsza.</span><span class="sxs-lookup"><span data-stu-id="dc9fb-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc9fb-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc9fb-159">See also</span></span>

- [<span data-ttu-id="dc9fb-160">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="dc9fb-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="dc9fb-161">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="dc9fb-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="dc9fb-162">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="dc9fb-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="dc9fb-163">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="dc9fb-163">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="dc9fb-164">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dc9fb-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
