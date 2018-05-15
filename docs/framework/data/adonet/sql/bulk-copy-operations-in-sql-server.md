---
title: Operacje kopiowania masowego w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 87373f55181742a243c60bc4b471334535d88ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="20366-102">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="20366-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="20366-103">Microsoft SQL Server zawiera popularne narzędzia wiersza polecenia o nazwie **bcp** dla szybko zbiorcze kopiowania dużych plików do tabel lub widoków w bazach danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="20366-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="20366-104"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa umożliwia pisanie kodu zarządzanego rozwiązań w zakresie podobnych możliwościach.</span><span class="sxs-lookup"><span data-stu-id="20366-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="20366-105">Istnieją inne sposoby, aby załadować dane do tabeli programu SQL Server (na przykład instrukcji INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> oferuje wydajności znaczących korzyści nad nimi.</span><span class="sxs-lookup"><span data-stu-id="20366-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="20366-106"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa może być używana do zapisu danych tylko do tabel programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="20366-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="20366-107">Jednak źródła danych nie jest ograniczony do programu SQL Server; wszystkie źródła danych może służyć, jak długo dane mogą być ładowane do <xref:System.Data.DataTable> wystąpienia lub odczytu z <xref:System.Data.IDataReader> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="20366-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="20366-108">Przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy, można wykonać:</span><span class="sxs-lookup"><span data-stu-id="20366-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
-   <span data-ttu-id="20366-109">Pojedynczy kopiowania masowego</span><span class="sxs-lookup"><span data-stu-id="20366-109">A single bulk copy operation</span></span>  
  
-   <span data-ttu-id="20366-110">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="20366-110">Multiple bulk copy operations</span></span>  
  
-   <span data-ttu-id="20366-111">Operacja kopiowania zbiorczego w ramach transakcji</span><span class="sxs-lookup"><span data-stu-id="20366-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20366-112">Korzystając z .NET Framework w wersji 1.1 lub starszy (który nie obsługuje <xref:System.Data.SqlClient.SqlBulkCopy> klasy), może zostać uruchomiony program SQL Server Transact-SQL **BULK INSERT** instrukcji przy użyciu <xref:System.Data.SqlClient.SqlCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="20366-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20366-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="20366-113">In This Section</span></span>  
 [<span data-ttu-id="20366-114">Konfiguracja przykładu kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="20366-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="20366-115">Opisuje tabele przykłady kopiowania zbiorczego i zapewnia skrypty SQL do tworzenia tabel w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="20366-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="20366-116">Pojedyncze operacje kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="20366-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="20366-117">Opis sposobu wykonywania pojedynczego zbiorczego kopię danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy i wykonać kopiowania masowego za pomocą instrukcji języka Transact-SQL i <xref:System.Data.SqlClient.SqlCommand> klasy.</span><span class="sxs-lookup"><span data-stu-id="20366-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="20366-118">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="20366-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="20366-119">Zawiera opis sposobu wykonania wielu operacji kopiowania zbiorczego danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.</span><span class="sxs-lookup"><span data-stu-id="20366-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="20366-120">Transakcja i operacje kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="20366-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="20366-121">Opisuje sposób wykonywania operacji kopiowania zbiorczego w ramach transakcji, w tym sposobu zatwierdzania lub wycofywania transakcji.</span><span class="sxs-lookup"><span data-stu-id="20366-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20366-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20366-122">See Also</span></span>  
 [<span data-ttu-id="20366-123">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="20366-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="20366-124">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="20366-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
