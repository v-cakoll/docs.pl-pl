---
title: Transakcje rozproszone Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c901ccf9132dc766d78efb24428b6469458a70fa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="c3fd2-102">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="c3fd2-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="c3fd2-103"><xref:System.Data.OracleClient.OracleConnection> Obiektu automatycznie rejestruje w istniejącej transakcji rozproszonej, gdy ustali, że transakcja jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="c3fd2-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="c3fd2-104">Automatyczne transakcji rejestracji występuje, gdy połączenie jest otwarte lub pobrać z puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="c3fd2-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="c3fd2-105">Auto rejestracji w istniejącej transakcji można wyłączyć, określając</span><span class="sxs-lookup"><span data-stu-id="c3fd2-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="c3fd2-106">jako parametr ciągu połączenia dla <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="c3fd2-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3fd2-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3fd2-107">See Also</span></span>  
 [<span data-ttu-id="c3fd2-108">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c3fd2-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="c3fd2-109">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="c3fd2-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
