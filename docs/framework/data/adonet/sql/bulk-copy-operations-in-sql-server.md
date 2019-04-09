---
title: Operacje kopiowania masowego w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 086b3b997cf0915be7cfa603a651eb412d52e985
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194802"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="52b18-102">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="52b18-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="52b18-103">Microsoft SQL Server zawiera popularne narzędzia wiersza polecenia o nazwie **bcp** dla szybko zbiorcze kopiowanie dużych plików do tabel lub widoków w bazach danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="52b18-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="52b18-104"><xref:System.Data.SqlClient.SqlBulkCopy> Klasy umożliwia pisanie kodu zarządzanego rozwiązania, które zapewniają podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="52b18-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="52b18-105">Istnieją inne sposoby, aby załadować dane do tabeli programu SQL Server (na przykład instrukcji INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> oferuje zalety istotnie poprawiającą wydajność, nad nimi.</span><span class="sxs-lookup"><span data-stu-id="52b18-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="52b18-106"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa może być używana w celu zapisania danych tylko do tabel programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="52b18-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="52b18-107">Jednak źródła danych nie jest ograniczony do programu SQL Server; Dowolne źródło danych może służyć, tak długo, jak długo dane mogą być ładowane do <xref:System.Data.DataTable> wystąpienia lub odczytu z <xref:System.Data.IDataReader> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="52b18-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="52b18-108">Za pomocą <xref:System.Data.SqlClient.SqlBulkCopy> klasy, można wykonać:</span><span class="sxs-lookup"><span data-stu-id="52b18-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
-   <span data-ttu-id="52b18-109">Pojedynczej zbiorczej operacji kopiowania</span><span class="sxs-lookup"><span data-stu-id="52b18-109">A single bulk copy operation</span></span>  
  
-   <span data-ttu-id="52b18-110">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="52b18-110">Multiple bulk copy operations</span></span>  
  
-   <span data-ttu-id="52b18-111">Operacji kopiowania zbiorczego, w ramach transakcji</span><span class="sxs-lookup"><span data-stu-id="52b18-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52b18-112">Korzystając z .NET Framework w wersji 1.1 lub wcześniejszej (który nie obsługuje <xref:System.Data.SqlClient.SqlBulkCopy> klasy), SQL Server Transact-SQL można wykonywać **BULK INSERT** przy użyciu instrukcji <xref:System.Data.SqlClient.SqlCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="52b18-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52b18-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="52b18-113">In This Section</span></span>  
 [<span data-ttu-id="52b18-114">Konfiguracja przykładu kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="52b18-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="52b18-115">W tym artykule opisano z tabelami używanymi w przykładach kopiowania zbiorczego i zawiera skrypty SQL do tworzenia tabel w bazie AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="52b18-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="52b18-116">Pojedyncze operacje kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="52b18-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="52b18-117">W tym artykule opisano sposób wykonywania pojedynczej zbiorczej kopię danych do wystąpienia programu SQL Server używa <xref:System.Data.SqlClient.SqlBulkCopy> klasy i sposobu wykonywania operacji kopiowania zbiorczego za pomocą instrukcji języka Transact-SQL i <xref:System.Data.SqlClient.SqlCommand> klasy.</span><span class="sxs-lookup"><span data-stu-id="52b18-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="52b18-118">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="52b18-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="52b18-119">W tym artykule opisano sposób wykonywania wiele operacji kopiowania zbiorczego danych do wystąpienia programu SQL Server przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.</span><span class="sxs-lookup"><span data-stu-id="52b18-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="52b18-120">Transakcja i operacje kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="52b18-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="52b18-121">W tym artykule opisano sposób wykonywania operacji kopiowania zbiorczego, w ramach transakcji, w tym sposobu zatwierdzania lub wycofywania transakcji.</span><span class="sxs-lookup"><span data-stu-id="52b18-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b18-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52b18-122">See also</span></span>

- [<span data-ttu-id="52b18-123">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="52b18-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="52b18-124">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="52b18-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
