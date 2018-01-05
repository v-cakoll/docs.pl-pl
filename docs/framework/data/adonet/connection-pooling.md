---
title: "Pula połączeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5082adda3c03bfbc40eafb174513a39fe17a3da8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="connection-pooling"></a><span data-ttu-id="566ba-102">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="566ba-102">Connection Pooling</span></span>
<span data-ttu-id="566ba-103">Połączenie ze źródłem danych może zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="566ba-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="566ba-104">Aby zminimalizować koszty otwarcia połączeń, ADO.NET używana technika optymalizacji o nazwie *puli połączeń*, który minimalizację kosztów wielokrotne otwieranie i zamykanie połączenia.</span><span class="sxs-lookup"><span data-stu-id="566ba-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="566ba-105">Pula połączeń przebiega inaczej dla dostawcy danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="566ba-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="566ba-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="566ba-106">In This Section</span></span>  
 [<span data-ttu-id="566ba-107">Buforowanie połączenia z programem SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="566ba-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="566ba-108">Zawiera omówienie puli połączeń i opisano, jak działa puli połączeń [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="566ba-108">Provides an overview of connection pooling and describes how connection pooling works in [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="566ba-109">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="566ba-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="566ba-110">W tym artykule opisano tworzenie puli połączeń dla .NET Framework Data Provider for OLE DB, .NET Framework Data Provider for ODBC i .NET Framework Data Provider for Oracle.</span><span class="sxs-lookup"><span data-stu-id="566ba-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="566ba-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="566ba-111">See Also</span></span>  
 [<span data-ttu-id="566ba-112">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="566ba-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="566ba-113">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="566ba-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
