---
title: "Duże typów"
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
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6090221981c8aaa894f94ebb7910659a1dbf210c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="large-udts"></a><span data-ttu-id="3a99e-102">Duże typów</span><span class="sxs-lookup"><span data-stu-id="3a99e-102">Large UDTs</span></span>
<span data-ttu-id="3a99e-103">Typy danych zdefiniowane przez użytkownika (UDTs) umożliwiają deweloperom rozszerzyć system skalarną typu serwera, przechowując wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3a99e-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="3a99e-104">UDTs może zawierać wielu elementów i może zawierać zachowania, w przeciwieństwie do tradycyjnych alias typów danych, składające się z jednego typu danych systemu programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3a99e-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a99e-105">.NET Framework 3.5 z dodatkiem SP1 należy zainstalować (lub nowsza) przeprowadzać SqlClient ulepszoną obsługę dużych typów.</span><span class="sxs-lookup"><span data-stu-id="3a99e-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="3a99e-106">Wcześniej UDTs były ograniczone do maksymalnie rozmiar równy 8 kilobajtów.</span><span class="sxs-lookup"><span data-stu-id="3a99e-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="3a99e-107">W programie SQL Server 2008, to ograniczenie zostało usunięte w przypadku typów, które mają format <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="3a99e-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="3a99e-108">Pełną dokumentację dla typów zdefiniowanych przez użytkownika na ten temat można znaleźć w wersji SQL Server — książki online dla używanej wersji programu SQL Server są używane.</span><span class="sxs-lookup"><span data-stu-id="3a99e-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="3a99e-109">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="3a99e-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="3a99e-110">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="3a99e-110">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="3a99e-111">Trwa pobieranie przy użyciu GetSchema schematy UDT</span><span class="sxs-lookup"><span data-stu-id="3a99e-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="3a99e-112"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Metody <xref:System.Data.SqlClient.SqlConnection> zwraca bazy danych informacji o schemacie w <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="3a99e-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="3a99e-113">Aby uzyskać więcej informacji, zobacz [kolekcje schematów programu SQL Server](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="3a99e-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="3a99e-114">Wartości w kolumnie GetSchemaTable dla typów</span><span class="sxs-lookup"><span data-stu-id="3a99e-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="3a99e-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metody <xref:System.Data.SqlClient.SqlDataReader> zwraca <xref:System.Data.DataTable> opisujący metadanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="3a99e-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="3a99e-116">W poniższej tabeli opisano różnice w metadanych kolumn dla dużych UDTs między programu SQL Server 2005 i SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="3a99e-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="3a99e-117">Kolumna SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="3a99e-117">SqlDataReader column</span></span>|<span data-ttu-id="3a99e-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="3a99e-118">SQL Server 2005</span></span>|<span data-ttu-id="3a99e-119">SQL Server 2008 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="3a99e-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="3a99e-120">Zmienia się</span><span class="sxs-lookup"><span data-stu-id="3a99e-120">Varies</span></span>|<span data-ttu-id="3a99e-121">Zmienia się</span><span class="sxs-lookup"><span data-stu-id="3a99e-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="3a99e-122">255</span><span class="sxs-lookup"><span data-stu-id="3a99e-122">255</span></span>|<span data-ttu-id="3a99e-123">255</span><span class="sxs-lookup"><span data-stu-id="3a99e-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="3a99e-124">255</span><span class="sxs-lookup"><span data-stu-id="3a99e-124">255</span></span>|<span data-ttu-id="3a99e-125">255</span><span class="sxs-lookup"><span data-stu-id="3a99e-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="3a99e-126">Wystąpienie UDT</span><span class="sxs-lookup"><span data-stu-id="3a99e-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="3a99e-127">Wystąpienie UDT</span><span class="sxs-lookup"><span data-stu-id="3a99e-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="3a99e-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="3a99e-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="3a99e-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="3a99e-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="3a99e-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="3a99e-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="3a99e-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="3a99e-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="3a99e-132">Nazwa określona jako część trzech *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="3a99e-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="3a99e-133">Zmienia się</span><span class="sxs-lookup"><span data-stu-id="3a99e-133">Varies</span></span>|<span data-ttu-id="3a99e-134">Zmienia się</span><span class="sxs-lookup"><span data-stu-id="3a99e-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="3a99e-135">Zagadnienia dotyczące SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="3a99e-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="3a99e-136"><xref:System.Data.SqlClient.SqlDataReader> Został rozszerzony w programie SQL Server 2008 do obsługi pobieranie dużych wartości UDT.</span><span class="sxs-lookup"><span data-stu-id="3a99e-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="3a99e-137">Jak duże wartości UDT są przetwarzane przez <xref:System.Data.SqlClient.SqlDataReader> zależy od wersji programu SQL Server są używane, jak również na `Type System Version` określone w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="3a99e-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="3a99e-138">Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="3a99e-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="3a99e-139">Następujące metody <xref:System.Data.SqlClient.SqlDataReader> zwróci <xref:System.Data.SqlTypes.SqlBinary> zamiast UDT podczas `Type System Version` ustawiono programu SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="3a99e-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="3a99e-140">Zwraca tablicę następujących metod `Byte[]` zamiast UDT podczas `Type System Version` ustawiono programu SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="3a99e-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="3a99e-141">Należy pamiętać, że dokonano konwersji na bieżącą wersję programu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="3a99e-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="3a99e-142">Specifying SqlParameters</span><span class="sxs-lookup"><span data-stu-id="3a99e-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="3a99e-143">Następujące <xref:System.Data.SqlClient.SqlParameter> właściwości zostały rozszerzone do pracy z dużą typów.</span><span class="sxs-lookup"><span data-stu-id="3a99e-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="3a99e-144">Właściwość SqlParameter</span><span class="sxs-lookup"><span data-stu-id="3a99e-144">SqlParameter Property</span></span>|<span data-ttu-id="3a99e-145">Opis</span><span class="sxs-lookup"><span data-stu-id="3a99e-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="3a99e-146">Pobiera lub ustawia obiekt reprezentujący wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="3a99e-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="3a99e-147">Domyślny ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="3a99e-147">The default is null.</span></span> <span data-ttu-id="3a99e-148">Właściwość może być `SqlBinary`, `Byte[]`, lub zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a99e-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="3a99e-149">Pobiera lub ustawia obiekt reprezentujący wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="3a99e-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="3a99e-150">Domyślny ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="3a99e-150">The default is null.</span></span> <span data-ttu-id="3a99e-151">Właściwość może być `SqlBinary`, `Byte[]`, lub zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a99e-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="3a99e-152">Pobiera lub ustawia rozmiar wartość parametru do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="3a99e-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="3a99e-153">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="3a99e-153">The default value is 0.</span></span> <span data-ttu-id="3a99e-154">Właściwość może być liczba całkowita, która reprezentuje rozmiar wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="3a99e-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="3a99e-155">Dla dużych typów może być rzeczywisty rozmiar UDT, lub wartość -1 nieznany.</span><span class="sxs-lookup"><span data-stu-id="3a99e-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="3a99e-156">Przykład podczas pobierania danych</span><span class="sxs-lookup"><span data-stu-id="3a99e-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="3a99e-157">Poniższy fragment kodu pokazano, jak pobrać UDT dużej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="3a99e-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="3a99e-158">`connectionString` Zmienna przyjmuje prawidłowe połączenie z bazą danych programu SQL Server i `commandString` zmienna przyjmuje poprawną instrukcją SELECT z pierwszym kolumna klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="3a99e-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a99e-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a99e-159">See Also</span></span>  
 [<span data-ttu-id="3a99e-160">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="3a99e-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="3a99e-161">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="3a99e-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="3a99e-162">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="3a99e-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="3a99e-163">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="3a99e-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="3a99e-164">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="3a99e-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
