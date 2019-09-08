---
title: Typy danych programu SQL Server i ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 642fe0d541aca01d6ffb2d9279c4d0fa91eadb63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780847"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="c57e1-102">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c57e1-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="c57e1-103">SQL Server i .NET Framework są oparte na różnych systemach typu, co może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="c57e1-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="c57e1-104">Aby zachować integralność danych, dostawca danych .NET Framework dla SQL Server (<xref:System.Data.SqlClient>) zapewnia metody dostępu typu Type do pracy z danymi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c57e1-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="c57e1-105">Możesz użyć wyliczeń w <xref:System.Data.SqlDbType> klasach, aby określić <xref:System.Data.SqlClient.SqlParameter> typy danych.</span><span class="sxs-lookup"><span data-stu-id="c57e1-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="c57e1-106">Aby uzyskać więcej informacji i tabelę opisującą mapowanie typu danych między SQL Server i .NET Framework typy danych, zobacz [SQL Server mapowania typów danych](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="c57e1-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="c57e1-107">SQL Server 2008 wprowadza nowe typy danych, które są przeznaczone do zaspokajania potrzeb firmy, do pracy z danymi o dacie i godzinie, ze strukturą, częściową strukturą i bez struktury.</span><span class="sxs-lookup"><span data-stu-id="c57e1-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="c57e1-108">Są one udokumentowane w SQL Server 2008 książki online.</span><span class="sxs-lookup"><span data-stu-id="c57e1-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="c57e1-109">SQL Server typy danych, które są dostępne do użycia w aplikacji, zależą od używanej wersji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c57e1-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="c57e1-110">Aby uzyskać więcej informacji, zobacz odpowiednią wersję dokumentacji SQL Server Books Online w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c57e1-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="c57e1-111">**Książka SQL Server online**</span><span class="sxs-lookup"><span data-stu-id="c57e1-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="c57e1-112">Typy danych (aparat bazy danych)</span><span class="sxs-lookup"><span data-stu-id="c57e1-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="c57e1-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c57e1-113">In This Section</span></span>  
 [<span data-ttu-id="c57e1-114">Właściwość SqlTypes i zestaw danych</span><span class="sxs-lookup"><span data-stu-id="c57e1-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="c57e1-115">Opisuje obsługę `SqlTypes` typów `DataSet`w programie.</span><span class="sxs-lookup"><span data-stu-id="c57e1-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="c57e1-116">Obsługa wartości Null</span><span class="sxs-lookup"><span data-stu-id="c57e1-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="c57e1-117">Pokazuje, jak korzystać z wartości null i logiki z trzema wartościami.</span><span class="sxs-lookup"><span data-stu-id="c57e1-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="c57e1-118">Porównywanie identyfikatora GUID i wartości uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="c57e1-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="c57e1-119">Demonstruje sposób pracy z identyfikatorami GUID i unikatowymi wartościami w SQL Server i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c57e1-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="c57e1-120">Dane daty i godziny</span><span class="sxs-lookup"><span data-stu-id="c57e1-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="c57e1-121">Opisuje sposób korzystania z nowych typów danych daty i godziny wprowadzonych w SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c57e1-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="c57e1-122">Duże UDT</span><span class="sxs-lookup"><span data-stu-id="c57e1-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="c57e1-123">Demonstruje sposób pobierania danych z UDTs dużej wartości wprowadzonych w SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c57e1-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="c57e1-124">Dane XML w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="c57e1-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="c57e1-125">Opisuje sposób pracy z danymi XML pobranymi z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c57e1-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c57e1-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c57e1-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="c57e1-127">`DataSet` Opisuje klasę i wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="c57e1-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="c57e1-128">Zawiera opis `SqlTypes` przestrzeni nazw i wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c57e1-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="c57e1-129">`SqlDbType` Opisuje Wyliczenie i wszystkie jego elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="c57e1-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="c57e1-130">`DbType` Opisuje Wyliczenie i wszystkie jego elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="c57e1-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57e1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c57e1-131">See also</span></span>

- [<span data-ttu-id="c57e1-132">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="c57e1-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="c57e1-133">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="c57e1-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="c57e1-134">Parametry o wartościach tabelowych</span><span class="sxs-lookup"><span data-stu-id="c57e1-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="c57e1-135">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="c57e1-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="c57e1-136">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c57e1-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
