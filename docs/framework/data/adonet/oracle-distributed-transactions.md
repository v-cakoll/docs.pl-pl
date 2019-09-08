---
title: Transakcje rozproszone Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 6f910f1dbbe448352c0edd5d1b80df659ac453d4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795149"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="e0629-102">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="e0629-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="e0629-103"><xref:System.Data.OracleClient.OracleConnection> Obiekt jest automatycznie zarejestrowany w istniejącej transakcji rozproszonej, jeśli określa, że transakcja jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="e0629-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="e0629-104">Automatyczne rejestracje transakcji odbywa się po otwarciu lub pobraniu połączenia z puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="e0629-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="e0629-105">Funkcję autorejestracji można wyłączyć w istniejących transakcjach, określając</span><span class="sxs-lookup"><span data-stu-id="e0629-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="e0629-106">jako parametr parametrów połączenia dla <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="e0629-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0629-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0629-107">See also</span></span>

- [<span data-ttu-id="e0629-108">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e0629-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="e0629-109">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e0629-109">ADO.NET Overview</span></span>](ado-net-overview.md)
