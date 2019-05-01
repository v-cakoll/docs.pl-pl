---
title: Typy danych programu SQL Server i ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 9e81e54f223d35a3db9c943edf6f9f9b24110faa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876801"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="7cdc8-102">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7cdc8-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="7cdc8-103">Program SQL Server i .NET Framework są oparte na różnych typów systemów, które może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="7cdc8-104">Aby zachować spójność danych, dla programu .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) udostępnia metody typizowane metody dostępu do pracy z danymi programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="7cdc8-105">Można używać wyliczenia w <xref:System.Data.SqlDbType> klasy, aby określić <xref:System.Data.SqlClient.SqlParameter> typów danych.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="7cdc8-106">Więcej informacji i tabelę, która opisuje mapowanie typu danych między serwerem SQL i typów danych programu .NET Framework, zobacz [mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="7cdc8-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="7cdc8-107">Program SQL Server 2008 wprowadzono nowe typy danych, które są przeznaczone do zaspokojenia potrzeb biznesowych do pracy z daty i godziny, ze strukturą, częściową strukturą i bez struktury danych.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="7cdc8-108">Te opisano w dokumentacji programu SQL Server 2008 — książki Online.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="7cdc8-109">Typy danych programu SQL Server, które są dostępne do użycia w aplikacji zależy od wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="7cdc8-110">Aby uzyskać więcej informacji zobacz odpowiedniej wersji programu SQL Server — książki Online, w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="7cdc8-111">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="7cdc8-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="7cdc8-112">Typy danych (aparat bazy danych)</span><span class="sxs-lookup"><span data-stu-id="7cdc8-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="7cdc8-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7cdc8-113">In This Section</span></span>  
 [<span data-ttu-id="7cdc8-114">Właściwość SqlTypes i zestaw danych</span><span class="sxs-lookup"><span data-stu-id="7cdc8-114">SqlTypes and the DataSet</span></span>](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 <span data-ttu-id="7cdc8-115">W tym artykule opisano obsługę typu `SqlTypes` w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="7cdc8-116">Obsługa wartości Null</span><span class="sxs-lookup"><span data-stu-id="7cdc8-116">Handling Null Values</span></span>](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 <span data-ttu-id="7cdc8-117">Pokazuje, jak pracować z przechowywanymi w trzech logiki i wartości null.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="7cdc8-118">Porównywanie identyfikatora GUID i wartości uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="7cdc8-118">Comparing GUID and uniqueidentifier Values</span></span>](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="7cdc8-119">Pokazuje, jak pracować z wartości identyfikatora GUID i unikatowy identyfikator programu SQL Server i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="7cdc8-120">Dane daty i godziny</span><span class="sxs-lookup"><span data-stu-id="7cdc8-120">Date and Time Data</span></span>](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 <span data-ttu-id="7cdc8-121">W tym artykule opisano, jak używać nowych typów daty i godziny dane wprowadzone w programie SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="7cdc8-122">Duże UDT</span><span class="sxs-lookup"><span data-stu-id="7cdc8-122">Large UDTs</span></span>](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 <span data-ttu-id="7cdc8-123">Pokazuje, jak można pobrać danych z dużą wartość typów zdefiniowanych przez użytkownika, wprowadzone w programie SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="7cdc8-124">Dane XML w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="7cdc8-124">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 <span data-ttu-id="7cdc8-125">W tym artykule opisano sposób pracy z danymi XML, pobierane z programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7cdc8-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7cdc8-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="7cdc8-127">W tym artykule opisano `DataSet` klasy i wszystkich jego składowych.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="7cdc8-128">W tym artykule opisano `SqlTypes` przestrzeni nazw i wszystkich jego składowych.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="7cdc8-129">W tym artykule opisano `SqlDbType` wyliczenia i wszyscy jej członkowie.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="7cdc8-130">W tym artykule opisano `DbType` wyliczenia i wszyscy jej członkowie.</span><span class="sxs-lookup"><span data-stu-id="7cdc8-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdc8-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cdc8-131">See also</span></span>

- [<span data-ttu-id="7cdc8-132">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="7cdc8-132">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="7cdc8-133">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="7cdc8-133">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="7cdc8-134">Parametry o wartościach tabelowych</span><span class="sxs-lookup"><span data-stu-id="7cdc8-134">Table-Valued Parameters</span></span>](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)
- [<span data-ttu-id="7cdc8-135">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="7cdc8-135">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="7cdc8-136">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7cdc8-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
