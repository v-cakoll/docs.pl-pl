---
title: Pobieranie informacji o schemacie bazy danych
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 00cf0e36dd7886897c26adf50102f32892ebb18e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562707"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="1d9e1-102">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="1d9e1-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="1d9e1-103">Uzyskiwanie informacji o schemacie bazy danych odbywa się z procesem odnajdywania schematu.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="1d9e1-104">Wykrywanie schematu umożliwia aplikacjom żądanie czy zarządzanego dostawcy Znajdź i zwrócone informacje na temat schematu bazy danych, nazywane również *metadanych*, z określoną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="1d9e1-105">Elementy schematu innej bazy danych, takie jak tabele, kolumny i procedur składowanych są udostępniane za pośrednictwem kolekcje schematów.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="1d9e1-106">Każda kolekcja schemat zawiera szereg informacji o schemacie specyficzne dla używanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="1d9e1-107">Każda implementacja zarządzanego dostawcy .NET Framework **GetSchema** method in Class metoda **połączenia** klasy i informacji o schemacie, który jest zwracany z **GetSchema**metody jest dostarczany w formie <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1d9e1-108">**GetSchema** metodą jest przeciążona metoda, która zapewnia następujące parametry opcjonalne określanie kolekcji schematów, aby powrócić i ograniczając ilość zwracanych informacji.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="1d9e1-109">Podaj dostawcy danych .NET Framework dla OLE DB i ODBC, Oracle oraz SqlClient **GetSchemaTable** metodę, która zwraca DataTable opisujące kolumny metadanych **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="1d9e1-110">.NET Framework Data Provider for OLE DB udostępnia również informacje o schemacie przy użyciu <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metody <xref:System.Data.OleDb.OleDbConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="1d9e1-111">Jako argumenty **Element GetOleDbSchemaTable** przyjmuje <xref:System.Data.OleDb.OleDbSchemaGuid> określający informacji o schemacie, aby powrócić i Tablica ograniczeń na te zwracane kolumny.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="1d9e1-112">**Element GetOleDbSchemaTable** zwraca <xref:System.Data.DataTable> wypełniony informacjami żądany schemat.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d9e1-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1d9e1-113">In This Section</span></span>  
 [<span data-ttu-id="1d9e1-114">GetSchema i kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="1d9e1-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="1d9e1-115">W tym artykule opisano **GetSchema** metody i jak może służyć do pobierania i ograniczyć informacji o schemacie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="1d9e1-116">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="1d9e1-116">Schema Restrictions</span></span>  
 <span data-ttu-id="1d9e1-117">W tym artykule opisano ograniczenia schematu, które mogą być używane z **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="1d9e1-118">Typowe kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="1d9e1-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="1d9e1-119">W tym artykule opisano, wszystkie Typowe kolekcje schematów obsługiwane przez wszystkich dostawców zarządzanych w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="1d9e1-120">Kolekcje schematów programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d9e1-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="1d9e1-121">W tym artykule opisano kolekcji schematów, obsługiwany przez dostawcę .NET Framework dla programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="1d9e1-122">Kolekcje schematów Oracle</span><span class="sxs-lookup"><span data-stu-id="1d9e1-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="1d9e1-123">W tym artykule opisano kolekcji schematów, obsługiwany przez dostawcę .NET Framework dla programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="1d9e1-124">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="1d9e1-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="1d9e1-125">Opisuje kolekcje schematów dla sterowników ODBC.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="1d9e1-126">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="1d9e1-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="1d9e1-127">Opisuje kolekcje schematów dla dostawcy OLE DB.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1d9e1-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="1d9e1-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="1d9e1-129">W tym artykule opisano **GetSchema** metody <xref:System.Data.Common.DbConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="1d9e1-130">W tym artykule opisano **GetSchema** metody <xref:System.Data.Odbc.OdbcConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="1d9e1-131">W tym artykule opisano **GetSchema** metody <xref:System.Data.OleDb.OleDbConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="1d9e1-132">W tym artykule opisano **GetSchema** metody <xref:System.Data.OracleClient.OracleConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="1d9e1-133">W tym artykule opisano **GetSchema** metody <xref:System.Data.SqlClient.SqlConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="1d9e1-134">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.Common.DbDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="1d9e1-135">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.Odbc.OdbcDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="1d9e1-136">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.OleDb.OleDbDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="1d9e1-137">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.OracleClient.OracleDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="1d9e1-138">W tym artykule opisano **GetSchemaTable** metody <xref:System.Data.SqlClient.SqlDataReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9e1-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d9e1-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d9e1-139">See Also</span></span>  
 [<span data-ttu-id="1d9e1-140">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1d9e1-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="1d9e1-141">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1d9e1-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
