---
title: Pobieranie informacji o schemacie bazy danych
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782740"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="79090-102">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="79090-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="79090-103">Uzyskiwanie informacji o schemacie z bazy danych jest realizowane przy użyciu procesu odnajdywania schematu.</span><span class="sxs-lookup"><span data-stu-id="79090-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="79090-104">Funkcja odnajdywania schematów umożliwia aplikacjom żądanie, że dostawcy zarządzani znajdą i zwracają informacje o schemacie bazy danych, znane także jako *metadane*, danej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="79090-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="79090-105">Różne elementy schematu bazy danych, takie jak tabele, kolumny i procedury składowane, są udostępniane za poorednictwem kolekcji schematów.</span><span class="sxs-lookup"><span data-stu-id="79090-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="79090-106">Każda kolekcja schematów zawiera różne informacje o schemacie specyficzne dla używanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="79090-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="79090-107">Każdy z .NET Framework dostawców zarządzanych implementuje metodę **GetSchema** w klasie **Connection** , a informacje o schemacie, które są zwracane z metody **GetSchema** , mają postać <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="79090-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="79090-108">Metoda **GetSchema** jest przeciążoną metodą, która zapewnia parametry opcjonalne do określania kolekcji schematów do zwrócenia i ograniczając ilość zwracanych informacji.</span><span class="sxs-lookup"><span data-stu-id="79090-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="79090-109">Dostawcy danych .NET Framework dla OLE DB, ODBC, Oracle i SqlClient zapewniają metodę **Getschemaing** , która zwraca element DataTable opisujący metadane kolumn elementu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="79090-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="79090-110">Dostawca danych .NET Framework dla OLE DB udostępnia również informacje o schemacie przy użyciu <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metody <xref:System.Data.OleDb.OleDbConnection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="79090-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="79090-111">Jako argumenty **GetOleDbSchemaTable** przyjmuje <xref:System.Data.OleDb.OleDbSchemaGuid> , że identyfikuje informacje o schemacie do zwrócenia i tablicę ograniczeń dla tych zwracanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="79090-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="79090-112">**GetOleDbSchemaTable** zwraca <xref:System.Data.DataTable> wypełniony z żądanymi informacjami o schemacie.</span><span class="sxs-lookup"><span data-stu-id="79090-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79090-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="79090-113">In This Section</span></span>  
 [<span data-ttu-id="79090-114">GetSchema i kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="79090-114">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="79090-115">Opisuje metodę **GetSchema** i sposób jej użycia do pobierania i ograniczania informacji schematu z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="79090-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="79090-116">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="79090-116">Schema Restrictions</span></span>  
 <span data-ttu-id="79090-117">Opisuje ograniczenia schematu, które mogą być używane z **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="79090-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="79090-118">Typowe kolekcje schematów</span><span class="sxs-lookup"><span data-stu-id="79090-118">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="79090-119">Opisuje wszystkie typowe kolekcje schematów obsługiwane przez wszystkich .NET Framework zarządzanych dostawców.</span><span class="sxs-lookup"><span data-stu-id="79090-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="79090-120">Kolekcje schematów programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="79090-120">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="79090-121">Opisuje kolekcję schematów obsługiwaną przez dostawcę .NET Framework dla SQL Server.</span><span class="sxs-lookup"><span data-stu-id="79090-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="79090-122">Kolekcje schematów Oracle</span><span class="sxs-lookup"><span data-stu-id="79090-122">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="79090-123">Opisuje kolekcję schematów obsługiwaną przez dostawcę .NET Framework dla firmy Oracle.</span><span class="sxs-lookup"><span data-stu-id="79090-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="79090-124">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="79090-124">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="79090-125">Opisuje kolekcje schematów dla sterowników ODBC.</span><span class="sxs-lookup"><span data-stu-id="79090-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="79090-126">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="79090-126">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="79090-127">Opisuje kolekcje schematów dla dostawców OLE DB.</span><span class="sxs-lookup"><span data-stu-id="79090-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="79090-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="79090-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="79090-129">Opisuje <xref:System.Data.Common.DbConnection> metodę **GetSchema** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="79090-130">Opisuje <xref:System.Data.Odbc.OdbcConnection> metodę **GetSchema** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="79090-131">Opisuje <xref:System.Data.OleDb.OleDbConnection> metodę **GetSchema** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="79090-132">Opisuje <xref:System.Data.OracleClient.OracleConnection> metodę **GetSchema** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="79090-133">Opisuje <xref:System.Data.SqlClient.SqlConnection> metodę **GetSchema** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="79090-134">Opisuje <xref:System.Data.Common.DbDataReader> metodę **getschemaing** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="79090-135">Opisuje <xref:System.Data.Odbc.OdbcDataReader> metodę **getschemaing** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="79090-136">Opisuje <xref:System.Data.OleDb.OleDbDataReader> metodę **getschemaing** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="79090-137">Opisuje <xref:System.Data.OracleClient.OracleDataReader> metodę **getschemaing** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="79090-138">Opisuje <xref:System.Data.SqlClient.SqlDataReader> metodę **getschemaing** klasy.</span><span class="sxs-lookup"><span data-stu-id="79090-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79090-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79090-139">See also</span></span>

- [<span data-ttu-id="79090-140">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="79090-140">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="79090-141">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="79090-141">ADO.NET Overview</span></span>](ado-net-overview.md)
