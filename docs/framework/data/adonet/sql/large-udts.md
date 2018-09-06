---
title: Duże UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: a57bf400288c11e5ba651515feba42437b93148f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861991"
---
# <a name="large-udts"></a><span data-ttu-id="0c1d3-102">Duże UDT</span><span class="sxs-lookup"><span data-stu-id="0c1d3-102">Large UDTs</span></span>
<span data-ttu-id="0c1d3-103">Typy zdefiniowane przez użytkownika (UDTs) umożliwiają deweloperom rozszerzenie serwera typ skalarny systemu, przechowując wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="0c1d3-104">Typów zdefiniowanych przez użytkownika może zawierać wiele elementów i może mieć zachowań, w przeciwieństwie do typów danych tradycyjnych aliasu, które składają się z jednego typu danych systemu programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c1d3-105">Należy zainstalować .NET Framework 3.5 z dodatkiem SP1 (lub nowszym) z zalet rozszerzona obsługa SqlClient duże UDT.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="0c1d3-106">Wcześniej rozszerzeń UDT nie zostały ograniczone do maksymalnie 8 kilobajtów.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="0c1d3-107">W programie SQL Server 2008 to ograniczenie zostało usunięte dla typów zdefiniowanych przez użytkownika, które formatu w <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="0c1d3-108">Aby uzyskać pełną dokumentację dla typów zdefiniowanych przez użytkownika Zobacz wersja programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="0c1d3-109">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="0c1d3-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="0c1d3-110">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="0c1d3-110">CLR User-Defined Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="0c1d3-111">Trwa pobieranie schematy UDT przy użyciu GetSchema</span><span class="sxs-lookup"><span data-stu-id="0c1d3-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="0c1d3-112"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Metody <xref:System.Data.SqlClient.SqlConnection> zwraca bazy danych informacji o schemacie w <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="0c1d3-113">Aby uzyskać więcej informacji, zobacz [kolekcje schematów programu SQL Server](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="0c1d3-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="0c1d3-114">Wartości kolumn GetSchemaTable dla typów zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="0c1d3-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="0c1d3-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metody <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.DataTable> opisującą kolumny metadanych.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="0c1d3-116">W poniższej tabeli opisano różnice w metadanych kolumn, aby uzyskać duże UDT między programu SQL Server 2005 i SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="0c1d3-117">Kolumna SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="0c1d3-117">SqlDataReader column</span></span>|<span data-ttu-id="0c1d3-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="0c1d3-118">SQL Server 2005</span></span>|<span data-ttu-id="0c1d3-119">SQL Server 2008 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="0c1d3-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="0c1d3-120">Różni się</span><span class="sxs-lookup"><span data-stu-id="0c1d3-120">Varies</span></span>|<span data-ttu-id="0c1d3-121">Różni się</span><span class="sxs-lookup"><span data-stu-id="0c1d3-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="0c1d3-122">255</span><span class="sxs-lookup"><span data-stu-id="0c1d3-122">255</span></span>|<span data-ttu-id="0c1d3-123">255</span><span class="sxs-lookup"><span data-stu-id="0c1d3-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="0c1d3-124">255</span><span class="sxs-lookup"><span data-stu-id="0c1d3-124">255</span></span>|<span data-ttu-id="0c1d3-125">255</span><span class="sxs-lookup"><span data-stu-id="0c1d3-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="0c1d3-126">Wystąpienie UDT</span><span class="sxs-lookup"><span data-stu-id="0c1d3-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="0c1d3-127">Wystąpienie UDT</span><span class="sxs-lookup"><span data-stu-id="0c1d3-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="0c1d3-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="0c1d3-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="0c1d3-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="0c1d3-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="0c1d3-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="0c1d3-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="0c1d3-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="0c1d3-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="0c1d3-132">Trzy części nazwy określonej jako *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="0c1d3-133">Różni się</span><span class="sxs-lookup"><span data-stu-id="0c1d3-133">Varies</span></span>|<span data-ttu-id="0c1d3-134">Różni się</span><span class="sxs-lookup"><span data-stu-id="0c1d3-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="0c1d3-135">Zagadnienia dotyczące SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="0c1d3-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="0c1d3-136"><xref:System.Data.SqlClient.SqlDataReader> Został rozszerzony począwszy od programu SQL Server 2008 do obsługi pobierania dużych wartości UDT.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="0c1d3-137">Jak duże UDT wartości są przetwarzane przez <xref:System.Data.SqlClient.SqlDataReader> zależy od wersji programu SQL Server, które są używane, jak również na `Type System Version` określone w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="0c1d3-138">Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="0c1d3-139">Następujące metody <xref:System.Data.SqlClient.SqlDataReader> zwróci <xref:System.Data.SqlTypes.SqlBinary> zamiast UDT po `Type System Version` jest ustawiona na program SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="0c1d3-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="0c1d3-140">Następujące metody zwraca tablicę `Byte[]` zamiast UDT po `Type System Version` jest ustawiona na program SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="0c1d3-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="0c1d3-141">Należy pamiętać, że konwersji zostały wprowadzone w bieżącej wersji programu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="0c1d3-142">Specifying SqlParameters</span><span class="sxs-lookup"><span data-stu-id="0c1d3-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="0c1d3-143">Następujące <xref:System.Data.SqlClient.SqlParameter> właściwości zostały rozszerzone do pracy z duże UDT.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="0c1d3-144">Parametr SqlParameter właściwości</span><span class="sxs-lookup"><span data-stu-id="0c1d3-144">SqlParameter Property</span></span>|<span data-ttu-id="0c1d3-145">Opis</span><span class="sxs-lookup"><span data-stu-id="0c1d3-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="0c1d3-146">Pobiera lub ustawia obiekt, który reprezentuje wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="0c1d3-147">Domyślny ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-147">The default is null.</span></span> <span data-ttu-id="0c1d3-148">Właściwość może być `SqlBinary`, `Byte[]`, lub zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="0c1d3-149">Pobiera lub ustawia obiekt, który reprezentuje wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="0c1d3-150">Domyślny ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-150">The default is null.</span></span> <span data-ttu-id="0c1d3-151">Właściwość może być `SqlBinary`, `Byte[]`, lub zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="0c1d3-152">Pobiera lub ustawia rozmiar wartości parametru, aby rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="0c1d3-153">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-153">The default value is 0.</span></span> <span data-ttu-id="0c1d3-154">Właściwość może być liczba całkowita, która reprezentuje rozmiar wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="0c1d3-155">Aby uzyskać duże UDT może być rzeczywisty rozmiar UDT albo -1 nieznany.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="0c1d3-156">Przykład pobierania danych</span><span class="sxs-lookup"><span data-stu-id="0c1d3-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="0c1d3-157">Poniższy fragment kodu przedstawia sposób pobierania dużych ilości danych UDT.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="0c1d3-158">`connectionString` Zmiennej zakłada prawidłowe połączenie z bazą danych programu SQL Server i `commandString` zmiennej zakłada poprawną instrukcją SELECT z kolumny klucza podstawowego, wymienione jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="0c1d3-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c1d3-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c1d3-159">See Also</span></span>  
 [<span data-ttu-id="0c1d3-160">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="0c1d3-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="0c1d3-161">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="0c1d3-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="0c1d3-162">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="0c1d3-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="0c1d3-163">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="0c1d3-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="0c1d3-164">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="0c1d3-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
