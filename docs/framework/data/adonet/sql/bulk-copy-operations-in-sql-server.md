---
title: Operacje kopiowania masowego w programie SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31da2fbc7dca4c0c2c077991ddec39e8979b08b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="69b95-102">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="69b95-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="69b95-103">Microsoft SQL Server zawiera popularne narzędzia wiersza polecenia o nazwie **bcp** dla szybko zbiorcze kopiowania dużych plików do tabel lub widoków w bazach danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="69b95-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="69b95-104"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa umożliwia pisanie kodu zarządzanego rozwiązań w zakresie podobnych możliwościach.</span><span class="sxs-lookup"><span data-stu-id="69b95-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="69b95-105">Istnieją inne sposoby, aby załadować dane do tabeli programu SQL Server (na przykład instrukcji INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> oferuje wydajności znaczących korzyści nad nimi.</span><span class="sxs-lookup"><span data-stu-id="69b95-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="69b95-106"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa może być używana do zapisu danych tylko do tabel programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="69b95-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="69b95-107">Jednak źródła danych nie jest ograniczony do programu SQL Server; wszystkie źródła danych może służyć, jak długo dane mogą być ładowane do <xref:System.Data.DataTable> wystąpienia lub odczytu z <xref:System.Data.IDataReader> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="69b95-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="69b95-108">Przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy, można wykonać:</span><span class="sxs-lookup"><span data-stu-id="69b95-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
-   <span data-ttu-id="69b95-109">Pojedynczy kopiowania masowego</span><span class="sxs-lookup"><span data-stu-id="69b95-109">A single bulk copy operation</span></span>  
  
-   <span data-ttu-id="69b95-110">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="69b95-110">Multiple bulk copy operations</span></span>  
  
-   <span data-ttu-id="69b95-111">Operacja kopiowania zbiorczego w ramach transakcji</span><span class="sxs-lookup"><span data-stu-id="69b95-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69b95-112">Korzystając z .NET Framework w wersji 1.1 lub starszy (który nie obsługuje <xref:System.Data.SqlClient.SqlBulkCopy> klasy), może zostać uruchomiony program SQL Server Transact-SQL **BULK INSERT** instrukcji przy użyciu <xref:System.Data.SqlClient.SqlCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="69b95-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69b95-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="69b95-113">In This Section</span></span>  
 [<span data-ttu-id="69b95-114">Instalator przykład kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="69b95-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="69b95-115">Opisuje tabele przykłady kopiowania zbiorczego i zapewnia skrypty SQL do tworzenia tabel w bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="69b95-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="69b95-116">Operacje kopiowania masowego pojedynczego</span><span class="sxs-lookup"><span data-stu-id="69b95-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="69b95-117">Opis sposobu wykonywania pojedynczego zbiorczego kopię danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy i wykonać kopiowania masowego za pomocą instrukcji języka Transact-SQL i <xref:System.Data.SqlClient.SqlCommand> klasy.</span><span class="sxs-lookup"><span data-stu-id="69b95-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="69b95-118">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="69b95-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="69b95-119">Zawiera opis sposobu wykonania wielu operacji kopiowania zbiorczego danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.</span><span class="sxs-lookup"><span data-stu-id="69b95-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="69b95-120">Transakcja i operacje kopiowania masowego</span><span class="sxs-lookup"><span data-stu-id="69b95-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="69b95-121">Opisuje sposób wykonywania operacji kopiowania zbiorczego w ramach transakcji, w tym sposobu zatwierdzania lub wycofywania transakcji.</span><span class="sxs-lookup"><span data-stu-id="69b95-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b95-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69b95-122">See Also</span></span>  
 [<span data-ttu-id="69b95-123">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69b95-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="69b95-124">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="69b95-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
