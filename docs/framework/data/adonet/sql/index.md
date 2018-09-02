---
title: SQL Server i ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: 32fc946f46ddac63d87b7e5a3d8f7120799f7223
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423081"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="8c4e3-102">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c4e3-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="8c4e3-103">W tej sekcji opisano funkcji i zachowań, które są specyficzne dla dostawcy danych programu .NET Framework dla programu SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="8c4e3-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="8c4e3-104"><xref:System.Data.SqlClient> zapewnia dostęp do wersji programu SQL Server, który hermetyzuje protokołów określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="8c4e3-105">Funkcje dostawcy danych programu zaprojektowano w sposób podobny do tego dostawcy danych .NET Framework dla OLE DB i ODBC, Oracle.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="8c4e3-106"><xref:System.Data.SqlClient> zawiera dane tabelaryczne analizator stream (TDS) do komunikowania się bezpośrednio z programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c4e3-107">Aby użyć .NET Framework Data Provider for SQL Server, aplikacja musi odwoływać <xref:System.Data.SqlClient> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c4e3-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8c4e3-108">In This Section</span></span>  
 [<span data-ttu-id="8c4e3-109">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="8c4e3-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="8c4e3-110">Omówienie funkcji zabezpieczeń programu SQL Server i scenariuszy aplikacji do tworzenia bezpiecznych aplikacji ADO.NET, których platformą docelową programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="8c4e3-111">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c4e3-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="8c4e3-112">W tym artykule opisano sposób pracy z typami danych programu SQL Server i sposobów interakcji z typów danych programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="8c4e3-113">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="8c4e3-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="8c4e3-114">W tym artykule opisano sposób pracy z danymi o dużej wartości w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="8c4e3-115">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c4e3-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="8c4e3-116">W tym artykule opisano sposób pracy z danymi w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="8c4e3-117">Zawiera sekcje dotyczące operacje kopiowania masowego, MARS, asynchroniczne operacje i parametry z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="8c4e3-118">Funkcje Serwera SQL i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c4e3-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="8c4e3-119">W tym artykule opisano funkcje programu SQL Server, które są przydatne dla deweloperów aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="8c4e3-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8c4e3-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="8c4e3-121">W tym artykule opisano podstawowe bloki konstrukcyjne, procesów i technik wymagane do utworzenia LINQ do SQL aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="8c4e3-122">Aby uzyskać pełną dokumentację aparatu bazy danych programu SQL Server zobacz programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="8c4e3-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="8c4e3-123">SQL Server — książki Online</span><span class="sxs-lookup"><span data-stu-id="8c4e3-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="8c4e3-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c4e3-124">See Also</span></span>  
 [<span data-ttu-id="8c4e3-125">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c4e3-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="8c4e3-126">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c4e3-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="8c4e3-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="8c4e3-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="8c4e3-128">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c4e3-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="8c4e3-129">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="8c4e3-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
