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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 104befd25d30d050fee0a053a413b13fe6d1fc51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="1cc71-102">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="1cc71-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="1cc71-103"><xref:System.Data.OracleClient.OracleConnection> Obiektu automatycznie rejestruje w istniejącej transakcji rozproszonej, gdy ustali, że transakcja jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="1cc71-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="1cc71-104">Automatyczne transakcji rejestracji występuje, gdy połączenie jest otwarte lub pobrać z puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="1cc71-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="1cc71-105">Auto rejestracji w istniejącej transakcji można wyłączyć, określając</span><span class="sxs-lookup"><span data-stu-id="1cc71-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="1cc71-106">jako parametr ciągu połączenia dla <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="1cc71-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc71-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1cc71-107">See Also</span></span>  
 [<span data-ttu-id="1cc71-108">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1cc71-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="1cc71-109">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="1cc71-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
