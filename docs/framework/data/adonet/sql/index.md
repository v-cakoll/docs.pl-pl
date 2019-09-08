---
title: SQL Server i ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: b54725fa8dbff7db82ed197f4961e773a06895e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782329"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="156ae-102">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156ae-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="156ae-103">W tej sekcji opisano funkcje i zachowania, które są specyficzne dla Dostawca danych .NET Framework dla SQL Server<xref:System.Data.SqlClient>().</span><span class="sxs-lookup"><span data-stu-id="156ae-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="156ae-104"><xref:System.Data.SqlClient>zapewnia dostęp do wersji SQL Server, które hermetyzują protokoły specyficzne dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="156ae-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="156ae-105">Funkcja dostawcy danych została zaprojektowana tak, aby była podobna do .NET Framework dostawców danych dla OLE DB, ODBC i Oracle.</span><span class="sxs-lookup"><span data-stu-id="156ae-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="156ae-106"><xref:System.Data.SqlClient>zawiera Analizator strumienia danych tabelarycznych (TDS) do bezpośredniego komunikowania się z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="156ae-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="156ae-107">Aby można było użyć dostawca danych .NET Framework na potrzeby SQL Server, aplikacja musi odwoływać się do <xref:System.Data.SqlClient> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="156ae-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="156ae-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="156ae-108">In This Section</span></span>  
 [<span data-ttu-id="156ae-109">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="156ae-109">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="156ae-110">Zawiera omówienie funkcji zabezpieczeń SQL Server i scenariuszy aplikacji do tworzenia bezpiecznych aplikacji ADO.NET, które są przeznaczone SQL Server.</span><span class="sxs-lookup"><span data-stu-id="156ae-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="156ae-111">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156ae-111">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="156ae-112">Opisuje sposób pracy z SQL Server typami danych i sposobami ich współpracy z .NET Framework typami danych.</span><span class="sxs-lookup"><span data-stu-id="156ae-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="156ae-113">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="156ae-113">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="156ae-114">Opisuje sposób pracy z danymi dużej wartości w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="156ae-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="156ae-115">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156ae-115">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="156ae-116">Opisuje sposób pracy z danymi w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="156ae-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="156ae-117">Zawiera sekcje dotyczące operacji kopiowania zbiorczego, operacji MARS, asynchronicznych i parametrów z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="156ae-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="156ae-118">Funkcje Serwera SQL i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156ae-118">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="156ae-119">Opisuje funkcje SQL Server, które są przydatne w przypadku deweloperów aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="156ae-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="156ae-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="156ae-120">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="156ae-121">Zawiera opis podstawowych bloków konstrukcyjnych, procesów i technik wymaganych do tworzenia aplikacji LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="156ae-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="156ae-122">Aby uzyskać pełną dokumentację aparatu bazy danych SQL Server, zobacz SQL Server Books Online dla używanej wersji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="156ae-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="156ae-123">Książka SQL Server online</span><span class="sxs-lookup"><span data-stu-id="156ae-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="156ae-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="156ae-124">See also</span></span>

- [<span data-ttu-id="156ae-125">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156ae-125">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="156ae-126">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156ae-126">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="156ae-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="156ae-127">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="156ae-128">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156ae-128">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="156ae-129">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156ae-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
