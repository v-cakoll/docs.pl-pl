---
title: Konfiguracja przykładu kopiowania zbiorczego
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: ac09ed85315aee7c6b29952916088ebe6e301eb9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794419"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="a041d-102">Konfiguracja przykładu kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="a041d-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="a041d-103"><xref:System.Data.SqlClient.SqlBulkCopy> Klasa może służyć do zapisywania danych tylko w tabelach SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a041d-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="a041d-104">Przykłady kodu przedstawione w tym temacie wykorzystują przykładową bazę danych SQL Server, **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="a041d-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="a041d-105">Aby uniknąć zmiany istniejących przykładów kodu tabel, Zapisz dane w tabelach, które należy najpierw utworzyć.</span><span class="sxs-lookup"><span data-stu-id="a041d-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="a041d-106">Tabele **BulkCopyDemoMatchingColumns** i **BulkCopyDemoDifferentColumns** są zarówno oparte na tabeli produkcji **AdventureWorks** **. Products. produkty** .</span><span class="sxs-lookup"><span data-stu-id="a041d-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="a041d-107">W przykładach kodu wykorzystujących te tabele dane są dodawane z tabeli **Production. Products** do jednej z tych przykładowych tabel.</span><span class="sxs-lookup"><span data-stu-id="a041d-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="a041d-108">Tabela **BulkCopyDemoDifferentColumns** jest używana, gdy przykład ilustruje sposób mapowania kolumn z danych źródłowych do tabeli docelowej. **BulkCopyDemoMatchingColumns** jest używany dla większości innych przykładów.</span><span class="sxs-lookup"><span data-stu-id="a041d-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="a041d-109">Niektóre przykłady kodu przedstawiają sposób użycia jednej <xref:System.Data.SqlClient.SqlBulkCopy> klasy do zapisu w wielu tabelach.</span><span class="sxs-lookup"><span data-stu-id="a041d-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="a041d-110">Dla tych przykładów tabele **BulkCopyDemoOrderHeader** i **BulkCopyDemoOrderDetail** są używane jako tabele docelowe.</span><span class="sxs-lookup"><span data-stu-id="a041d-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="a041d-111">Tabele te są oparte na tabelach **Sales. SalesOrderHeader** i **Sales. SalesOrderDetail** w systemie **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="a041d-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a041d-112">Przykłady kodu **SqlBulkCopy** są dostarczane w celu przedstawienia składni tylko **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="a041d-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="a041d-113">Jeśli tabele źródłowe i docelowe znajdują się w tym samym wystąpieniu SQL Server, łatwiej i szybciej można używać instrukcji języka Transact-SQL `INSERT … SELECT` do kopiowania danych.</span><span class="sxs-lookup"><span data-stu-id="a041d-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="a041d-114">Konfiguracja tabeli</span><span class="sxs-lookup"><span data-stu-id="a041d-114">Table Setup</span></span>  
 <span data-ttu-id="a041d-115">Aby utworzyć tabele niezbędne do poprawnego działania przykładów kodu, należy uruchomić następujące instrukcje języka Transact-SQL w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a041d-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a041d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a041d-116">See also</span></span>

- [<span data-ttu-id="a041d-117">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="a041d-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="a041d-118">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a041d-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
