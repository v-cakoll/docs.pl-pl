---
title: Konfiguracja przykładu kopiowania zbiorczego
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 2a7c0ddef42ff56306a42288c6960987ce7f714a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918091"
---
# <a name="bulk-copy-example-setup"></a>Konfiguracja przykładu kopiowania zbiorczego
<xref:System.Data.SqlClient.SqlBulkCopy> Klasa może służyć do zapisywania danych tylko w tabelach SQL Server. Przykłady kodu przedstawione w tym temacie wykorzystują przykładową bazę danych SQL Server, **AdventureWorks**. Aby uniknąć zmiany istniejących przykładów kodu tabel, Zapisz dane w tabelach, które należy najpierw utworzyć.  
  
 Tabele **BulkCopyDemoMatchingColumns** i **BulkCopyDemoDifferentColumns** są zarówno oparte na tabeli produkcji **AdventureWorks** **. Products. produkty** . W przykładach kodu wykorzystujących te tabele dane są dodawane z tabeli **Production. Products** do jednej z tych przykładowych tabel. Tabela **BulkCopyDemoDifferentColumns** jest używana, gdy przykład ilustruje sposób mapowania kolumn z danych źródłowych do tabeli docelowej. **BulkCopyDemoMatchingColumns** jest używany dla większości innych przykładów.  
  
 Niektóre przykłady kodu przedstawiają sposób użycia jednej <xref:System.Data.SqlClient.SqlBulkCopy> klasy do zapisu w wielu tabelach. Dla tych przykładów tabele **BulkCopyDemoOrderHeader** i **BulkCopyDemoOrderDetail** są używane jako tabele docelowe. Tabele te są oparte na tabelach **Sales. SalesOrderHeader** i **Sales. SalesOrderDetail** w systemie **AdventureWorks**.  
  
> [!NOTE]
> Przykłady kodu **SqlBulkCopy** są dostarczane w celu przedstawienia składni tylko **SqlBulkCopy** . Jeśli tabele źródłowe i docelowe znajdują się w tym samym wystąpieniu SQL Server, łatwiej i szybciej można używać instrukcji języka Transact-SQL `INSERT … SELECT` do kopiowania danych.  
  
## <a name="table-setup"></a>Konfiguracja tabeli  
 Aby utworzyć tabele niezbędne do poprawnego działania przykładów kodu, należy uruchomić następujące instrukcje języka Transact-SQL w bazie danych SQL Server.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Operacje kopiowania masowego w programie SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
