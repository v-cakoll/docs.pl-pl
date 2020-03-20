---
title: Konfiguracja przykładu kopiowania zbiorczego
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 80350d112da03c00e422432ce271ca5ea3ac58ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148845"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="74819-102">Konfiguracja przykładu kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="74819-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="74819-103">Klasa <xref:System.Data.SqlClient.SqlBulkCopy> może służyć do zapisywania danych tylko w tabelach programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="74819-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="74819-104">Przykłady kodu pokazane w tym temacie używają przykładowej bazy danych programu SQL Server **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="74819-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="74819-105">Aby uniknąć zmiany istniejących tabel przykłady kodu zapisu danych do tabel, które należy utworzyć w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="74819-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="74819-106">**BulkCopyDemoMatchingColumns** i **BulkCopyDemoDifferentColumns** tabele są oparte na **AdventureWorks** **Production.Products** tabeli.</span><span class="sxs-lookup"><span data-stu-id="74819-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="74819-107">W przykładach kodu, które używają tych tabel, dane są dodawane z **Production.Products** tabeli do jednej z tych przykładowych tabel.</span><span class="sxs-lookup"><span data-stu-id="74819-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="74819-108">**Tabela BulkCopyDemoDifferentColumns** jest używana, gdy w przykładzie pokazano sposób mapowania kolumn z danych źródłowych do tabeli docelowej; **BulkCopyDemoMatchingColumns** jest używany do większości innych próbek.</span><span class="sxs-lookup"><span data-stu-id="74819-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="74819-109">Kilka przykładów kodu zademonstrować, jak <xref:System.Data.SqlClient.SqlBulkCopy> używać jednej klasy do zapisu w wielu tabelach.</span><span class="sxs-lookup"><span data-stu-id="74819-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="74819-110">Dla tych przykładów **bulkCopyDemoOrderHeader** i **BulkCopyDemoOrderDetail** tabele są używane jako tabele docelowe.</span><span class="sxs-lookup"><span data-stu-id="74819-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="74819-111">Tabele te są oparte na tabelach **Sales.SalesOrderHeader** i **Sales.SalesOrderDetail** w **adventureworks**.</span><span class="sxs-lookup"><span data-stu-id="74819-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74819-112">Przykłady kodu **SqlBulkCopy** są dostarczane w celu wykazania składni przy użyciu **sqlbulkcopy** tylko.</span><span class="sxs-lookup"><span data-stu-id="74819-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="74819-113">Jeśli tabele źródłowe i docelowe znajdują się w tym samym wystąpieniu programu `INSERT … SELECT` SQL Server, łatwiej i szybciej jest używać instrukcji Transact-SQL do kopiowania danych.</span><span class="sxs-lookup"><span data-stu-id="74819-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="74819-114">Ustawienia tabeli</span><span class="sxs-lookup"><span data-stu-id="74819-114">Table Setup</span></span>  
 <span data-ttu-id="74819-115">Aby utworzyć tabele niezbędne do poprawnego uruchamiania przykładów kodu, należy uruchomić następujące instrukcje Transact-SQL w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="74819-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="74819-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74819-116">See also</span></span>

- [<span data-ttu-id="74819-117">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="74819-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="74819-118">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="74819-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
