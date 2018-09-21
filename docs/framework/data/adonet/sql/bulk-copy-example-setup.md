---
title: Konfiguracja przykładu kopiowania zbiorczego
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 71daf489fdf5e7e12594e798bc3ac01b1c76b027
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478191"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="61572-102">Konfiguracja przykładu kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="61572-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="61572-103"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa może być używana w celu zapisania danych tylko do tabel programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="61572-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="61572-104">Przykłady kodu, przedstawione w tym temacie Użyj przykładowej bazy danych programu SQL Server **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="61572-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="61572-105">Aby uniknąć, zmieniając istniejące tabele przykłady kodu zapisu danych do tabel, które należy najpierw utworzyć.</span><span class="sxs-lookup"><span data-stu-id="61572-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="61572-106">**BulkCopyDemoMatchingColumns** i **BulkCopyDemoDifferentColumns** tabele bazują na **AdventureWorks** **Production.Products**  tabeli.</span><span class="sxs-lookup"><span data-stu-id="61572-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="61572-107">W przykładach kodu, które używają tych tabel, dane są dodawane od **Production.Products** tabeli do jednej z tych tabel próbki.</span><span class="sxs-lookup"><span data-stu-id="61572-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="61572-108">**BulkCopyDemoDifferentColumns** tabela jest używana, gdy w przykładzie pokazano, jak mapować kolumny z danych źródłowych do tabeli docelowej; **BulkCopyDemoMatchingColumns** jest używany dla większości innych przykładów.</span><span class="sxs-lookup"><span data-stu-id="61572-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="61572-109">Kilka przykładów kodu pokazują, jak za jego pomocą <xref:System.Data.SqlClient.SqlBulkCopy> klasę umożliwiającą zapisanie z wieloma tabelami.</span><span class="sxs-lookup"><span data-stu-id="61572-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="61572-110">Dla tych przykładów **BulkCopyDemoOrderHeader** i **BulkCopyDemoOrderDetail** tabele są używane jako tabel docelowych.</span><span class="sxs-lookup"><span data-stu-id="61572-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="61572-111">Te tabele są oparte na **Sales.SalesOrderHeader** i **Sales.SalesOrderDetail** tabelach **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="61572-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61572-112">**SqlBulkCopy** podano przykłady kodu, aby zademonstrować przy użyciu składni **SqlBulkCopy** tylko.</span><span class="sxs-lookup"><span data-stu-id="61572-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="61572-113">Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze użyj instrukcji Transact-SQL `INSERT … SELECT` instrukcję, aby skopiować dane.</span><span class="sxs-lookup"><span data-stu-id="61572-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="61572-114">Ustawienia tabeli</span><span class="sxs-lookup"><span data-stu-id="61572-114">Table Setup</span></span>  
 <span data-ttu-id="61572-115">Aby utworzyć tabele wymagane w przypadku przykładów kodu, by działała poprawnie, należy uruchomić następujące instrukcje języka Transact-SQL w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="61572-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="61572-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61572-116">See Also</span></span>  
 [<span data-ttu-id="61572-117">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="61572-117">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="61572-118">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="61572-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
