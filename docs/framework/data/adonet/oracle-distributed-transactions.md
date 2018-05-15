---
title: Transakcje rozproszone Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 0e9dcb30eb1962071d7154d4bbf929871c8a12d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="2593f-102">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="2593f-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="2593f-103"><xref:System.Data.OracleClient.OracleConnection> Obiektu automatycznie rejestruje w istniejącej transakcji rozproszonej, gdy ustali, że transakcja jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="2593f-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="2593f-104">Automatyczne transakcji rejestracji występuje, gdy połączenie jest otwarte lub pobrać z puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="2593f-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="2593f-105">Auto rejestracji w istniejącej transakcji można wyłączyć, określając</span><span class="sxs-lookup"><span data-stu-id="2593f-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="2593f-106">jako parametr ciągu połączenia dla <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="2593f-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2593f-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2593f-107">See Also</span></span>  
 [<span data-ttu-id="2593f-108">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2593f-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="2593f-109">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="2593f-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
