---
title: Operacje kopiowania masowego w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: efa13eb1633fce3b59040ef8da79dba0f6ea81d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918061"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="9b474-102">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="9b474-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="9b474-103">Microsoft SQL Server obejmuje popularne narzędzie wiersza polecenia o nazwie **BCP** , aby szybko skopiować duże pliki do tabel lub widoków w bazach danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9b474-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="9b474-104"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa umożliwia pisanie rozwiązań kodu zarządzanego, które zapewniają podobną funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="9b474-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="9b474-105">Istnieją inne sposoby ładowania danych do tabeli SQL Server (na przykład instrukcje INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> oferują one znaczącą wydajność.</span><span class="sxs-lookup"><span data-stu-id="9b474-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="9b474-106"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa może służyć do zapisywania danych tylko w tabelach SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9b474-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="9b474-107">Ale źródło danych nie jest ograniczone do SQL Server; można użyć dowolnego źródła danych, o ile dane mogą zostać załadowane do <xref:System.Data.DataTable> wystąpienia lub odczytane <xref:System.Data.IDataReader> za pomocą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9b474-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="9b474-108">Korzystając z <xref:System.Data.SqlClient.SqlBulkCopy> klasy, można wykonać następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9b474-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="9b474-109">Pojedyncza operacja kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="9b474-109">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="9b474-110">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="9b474-110">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="9b474-111">Operacja kopiowania zbiorczego w ramach transakcji</span><span class="sxs-lookup"><span data-stu-id="9b474-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b474-112">W przypadku używania .NET Framework w wersji 1,1 lub starszej (która nie <xref:System.Data.SqlClient.SqlBulkCopy> obsługuje klasy) można wykonać SQL Server instrukcji języka Transact-SQL **BULK INSERT** przy użyciu <xref:System.Data.SqlClient.SqlCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9b474-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b474-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9b474-113">In This Section</span></span>  
 [<span data-ttu-id="9b474-114">Konfiguracja przykładu kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="9b474-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="9b474-115">Opisuje tabele używane w przykładowych kopiach zbiorczych i udostępnia skrypty SQL do tworzenia tabel w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9b474-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="9b474-116">Pojedyncze operacje kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="9b474-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="9b474-117">Opisuje, jak wykonać pojedynczą zbiorczą kopię danych w wystąpieniu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy i jak wykonać operację kopiowania zbiorczego za pomocą instrukcji języka Transact-SQL <xref:System.Data.SqlClient.SqlCommand> i klasy.</span><span class="sxs-lookup"><span data-stu-id="9b474-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="9b474-118">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="9b474-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="9b474-119">Opisuje sposób wykonywania wielu operacji zbiorczych kopiowania danych do wystąpienia SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.</span><span class="sxs-lookup"><span data-stu-id="9b474-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="9b474-120">Transakcja i operacje kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="9b474-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="9b474-121">Opisuje sposób wykonywania operacji kopiowania zbiorczego w ramach transakcji, w tym metody zatwierdzania lub wycofywania transakcji.</span><span class="sxs-lookup"><span data-stu-id="9b474-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b474-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b474-122">See also</span></span>

- [<span data-ttu-id="9b474-123">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b474-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="9b474-124">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="9b474-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
