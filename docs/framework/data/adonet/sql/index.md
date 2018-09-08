---
title: SQL Server i ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: 32fc946f46ddac63d87b7e5a3d8f7120799f7223
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178590"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="ab01d-102">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ab01d-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="ab01d-103">W tej sekcji opisano funkcji i zachowań, które są specyficzne dla dostawcy danych programu .NET Framework dla programu SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="ab01d-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="ab01d-104"><xref:System.Data.SqlClient> zapewnia dostęp do wersji programu SQL Server, który hermetyzuje protokołów określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ab01d-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="ab01d-105">Funkcje dostawcy danych programu zaprojektowano w sposób podobny do tego dostawcy danych .NET Framework dla OLE DB i ODBC, Oracle.</span><span class="sxs-lookup"><span data-stu-id="ab01d-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="ab01d-106"><xref:System.Data.SqlClient> zawiera dane tabelaryczne analizator stream (TDS) do komunikowania się bezpośrednio z programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab01d-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab01d-107">Aby użyć .NET Framework Data Provider for SQL Server, aplikacja musi odwoływać <xref:System.Data.SqlClient> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ab01d-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab01d-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ab01d-108">In This Section</span></span>  
 [<span data-ttu-id="ab01d-109">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="ab01d-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="ab01d-110">Omówienie funkcji zabezpieczeń programu SQL Server i scenariuszy aplikacji do tworzenia bezpiecznych aplikacji ADO.NET, których platformą docelową programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab01d-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="ab01d-111">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ab01d-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="ab01d-112">W tym artykule opisano sposób pracy z typami danych programu SQL Server i sposobów interakcji z typów danych programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab01d-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="ab01d-113">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="ab01d-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="ab01d-114">W tym artykule opisano sposób pracy z danymi o dużej wartości w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab01d-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="ab01d-115">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ab01d-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="ab01d-116">W tym artykule opisano sposób pracy z danymi w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab01d-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="ab01d-117">Zawiera sekcje dotyczące operacje kopiowania masowego, MARS, asynchroniczne operacje i parametry z wartościami przechowywanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ab01d-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="ab01d-118">Funkcje Serwera SQL i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ab01d-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="ab01d-119">W tym artykule opisano funkcje programu SQL Server, które są przydatne dla deweloperów aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ab01d-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="ab01d-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ab01d-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="ab01d-121">W tym artykule opisano podstawowe bloki konstrukcyjne, procesów i technik wymagane do utworzenia LINQ do SQL aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ab01d-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="ab01d-122">Aby uzyskać pełną dokumentację aparatu bazy danych programu SQL Server zobacz programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="ab01d-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="ab01d-123">SQL Server — książki Online</span><span class="sxs-lookup"><span data-stu-id="ab01d-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="ab01d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab01d-124">See Also</span></span>  
 [<span data-ttu-id="ab01d-125">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ab01d-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="ab01d-126">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ab01d-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="ab01d-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="ab01d-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="ab01d-128">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ab01d-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="ab01d-129">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ab01d-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
