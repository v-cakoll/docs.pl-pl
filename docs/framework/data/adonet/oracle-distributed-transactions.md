---
title: Transakcje rozproszone Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 4af1c98818f1929850c5ae78892c64993a93d4d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116220"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="c5e97-102">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="c5e97-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="c5e97-103"><xref:System.Data.OracleClient.OracleConnection> Obiektu pozyskuje automatycznie w ramach istniejącej transakcji rozproszonej, gdy ustali, że jest aktywna transakcja.</span><span class="sxs-lookup"><span data-stu-id="c5e97-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="c5e97-104">Rejestracja automatyczna transakcja występuje, gdy połączenie jest otwarte lub pobierane z puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="c5e97-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="c5e97-105">Funkcja automatycznego rejestracji w istniejących transakcji można wyłączyć, określając</span><span class="sxs-lookup"><span data-stu-id="c5e97-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="c5e97-106">jako parametr ciągu połączenia dla <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="c5e97-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e97-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5e97-107">See also</span></span>

- [<span data-ttu-id="c5e97-108">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5e97-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="c5e97-109">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="c5e97-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
