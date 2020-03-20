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
# <a name="bulk-copy-example-setup"></a>Konfiguracja przykładu kopiowania zbiorczego
Klasa <xref:System.Data.SqlClient.SqlBulkCopy> może służyć do zapisywania danych tylko w tabelach programu SQL Server. Przykłady kodu pokazane w tym temacie używają przykładowej bazy danych programu SQL Server **AdventureWorks**. Aby uniknąć zmiany istniejących tabel przykłady kodu zapisu danych do tabel, które należy utworzyć w pierwszej kolejności.  
  
 **BulkCopyDemoMatchingColumns** i **BulkCopyDemoDifferentColumns** tabele są oparte na **AdventureWorks** **Production.Products** tabeli. W przykładach kodu, które używają tych tabel, dane są dodawane z **Production.Products** tabeli do jednej z tych przykładowych tabel. **Tabela BulkCopyDemoDifferentColumns** jest używana, gdy w przykładzie pokazano sposób mapowania kolumn z danych źródłowych do tabeli docelowej; **BulkCopyDemoMatchingColumns** jest używany do większości innych próbek.  
  
 Kilka przykładów kodu zademonstrować, jak <xref:System.Data.SqlClient.SqlBulkCopy> używać jednej klasy do zapisu w wielu tabelach. Dla tych przykładów **bulkCopyDemoOrderHeader** i **BulkCopyDemoOrderDetail** tabele są używane jako tabele docelowe. Tabele te są oparte na tabelach **Sales.SalesOrderHeader** i **Sales.SalesOrderDetail** w **adventureworks**.  
  
> [!NOTE]
> Przykłady kodu **SqlBulkCopy** są dostarczane w celu wykazania składni przy użyciu **sqlbulkcopy** tylko. Jeśli tabele źródłowe i docelowe znajdują się w tym samym wystąpieniu programu `INSERT … SELECT` SQL Server, łatwiej i szybciej jest używać instrukcji Transact-SQL do kopiowania danych.  
  
## <a name="table-setup"></a>Ustawienia tabeli  
 Aby utworzyć tabele niezbędne do poprawnego uruchamiania przykładów kodu, należy uruchomić następujące instrukcje Transact-SQL w bazie danych programu SQL Server.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Operacje kopiowania masowego w programie SQL Server](bulk-copy-operations-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
