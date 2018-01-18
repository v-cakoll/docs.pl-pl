---
title: Pobieranie informacji o schemacie bazy danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09a0ec444801d1fe2caccf9e25a68e3c6ae8f5c2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="6a13d-102">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="6a13d-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="6a13d-103">Uzyskiwanie informacji o schemacie z bazy danych odbywa się z procesem odnajdywania schematu.</span><span class="sxs-lookup"><span data-stu-id="6a13d-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="6a13d-104">Odnajdywanie schematu umożliwia aplikacjom żądanie czy zarządzanego dostawcy znaleźć i zwraca informacje dotyczące schematu bazy danych, nazywane również *metadanych*, danego bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6a13d-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="6a13d-105">Elementów schematu innej bazy danych, takich jak tabele, kolumny i procedury składowane są udostępniane za pomocą kolekcji schematu.</span><span class="sxs-lookup"><span data-stu-id="6a13d-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="6a13d-106">Każdej kolekcji schematu zawiera szereg informacji o schemacie specyficzne dla używanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="6a13d-107">Każda implementacja zarządzanego dostawcy .NET Framework **GetSchema** metody w **połączenia** klasy i informacji o schemacie, która jest zwracana z **GetSchema**metody jest dostarczany w formie <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="6a13d-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="6a13d-108">**GetSchema** metody jest przeciążona metoda, która zapewnia następujące parametry opcjonalne określanie kolekcji schematów, aby wrócić i ograniczanie ilość zwracanych informacji.</span><span class="sxs-lookup"><span data-stu-id="6a13d-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="6a13d-109">Podaj dostawców danych .NET Framework dla OLE DB, ODBC, Oracle i SqlClient **GetSchemaTable** metodę, która zwraca DataTable opisujące metadane kolumny **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="6a13d-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="6a13d-110">.NET Framework Data Provider for OLE DB przedstawia również informacje o schemacie przy użyciu <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metody <xref:System.Data.OleDb.OleDbConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6a13d-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="6a13d-111">Jako argumenty **Element GetOleDbSchemaTable** przyjmuje <xref:System.Data.OleDb.OleDbSchemaGuid> identyfikującym informacji o schemacie, aby wrócić i zwrócił tablicę ograniczeń dotyczących tych kolumn.</span><span class="sxs-lookup"><span data-stu-id="6a13d-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="6a13d-112">**Element GetOleDbSchemaTable** zwraca <xref:System.Data.DataTable> wypełnione informacjami żądany schemat.</span><span class="sxs-lookup"><span data-stu-id="6a13d-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a13d-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6a13d-113">In This Section</span></span>  
 [<span data-ttu-id="6a13d-114">GetSchema i kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="6a13d-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="6a13d-115">W tym artykule opisano **GetSchema** — metoda i jak może służyć do pobierania i ograniczanie informacji schematu z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6a13d-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="6a13d-116">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="6a13d-116">Schema Restrictions</span></span>  
 <span data-ttu-id="6a13d-117">W tym artykule opisano ograniczenia schematu, które mogą być używane z **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="6a13d-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="6a13d-118">Typowe kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="6a13d-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="6a13d-119">Zawiera opis wszystkich typowych kolekcji schematu obsługiwane przez wszystkich dostawców zarządzane w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a13d-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="6a13d-120">Kolekcje schematów programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a13d-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="6a13d-121">Opis kolekcji schematów, obsługiwane przez dostawcę .NET Framework dla programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a13d-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="6a13d-122">Kolekcje schematów Oracle</span><span class="sxs-lookup"><span data-stu-id="6a13d-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="6a13d-123">Opis kolekcji schematów, obsługiwane przez dostawcę .NET Framework dla programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="6a13d-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="6a13d-124">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="6a13d-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="6a13d-125">Opis kolekcji schematu dla sterowników ODBC.</span><span class="sxs-lookup"><span data-stu-id="6a13d-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="6a13d-126">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="6a13d-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="6a13d-127">Opis kolekcji schematu dla dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="6a13d-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6a13d-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="6a13d-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="6a13d-129">W tym artykule opisano **GetSchema** metody <xref:System.Data.Common.DbConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="6a13d-130">W tym artykule opisano **GetSchema** metody <xref:System.Data.Odbc.OdbcConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="6a13d-131">W tym artykule opisano **GetSchema** metody <xref:System.Data.OleDb.OleDbConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="6a13d-132">W tym artykule opisano **GetSchema** metody <xref:System.Data.OracleClient.OracleConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="6a13d-133">W tym artykule opisano **GetSchema** metody <xref:System.Data.SqlClient.SqlConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6a13d-134">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.Common.DbDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6a13d-135">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.Odbc.OdbcDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6a13d-136">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.OleDb.OleDbDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6a13d-137">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.OracleClient.OracleDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="6a13d-138">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.SqlClient.SqlDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a13d-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a13d-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a13d-139">See Also</span></span>  
 [<span data-ttu-id="6a13d-140">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6a13d-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="6a13d-141">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="6a13d-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
