---
title: Pula połączeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3cc97ec0681e58facd30e3dbbb74001676a6e451
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="connection-pooling"></a><span data-ttu-id="9f619-102">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="9f619-102">Connection Pooling</span></span>
<span data-ttu-id="9f619-103">Połączenie ze źródłem danych może zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="9f619-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="9f619-104">Aby zminimalizować koszty otwarcia połączeń, ADO.NET używana technika optymalizacji o nazwie *puli połączeń*, który minimalizację kosztów wielokrotne otwieranie i zamykanie połączenia.</span><span class="sxs-lookup"><span data-stu-id="9f619-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="9f619-105">Pula połączeń przebiega inaczej dla dostawcy danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f619-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f619-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9f619-106">In This Section</span></span>  
 [<span data-ttu-id="9f619-107">Buforowanie połączenia z programem SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="9f619-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="9f619-108">Zawiera omówienie puli połączeń i opisano, jak działa puli połączeń w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9f619-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="9f619-109">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="9f619-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="9f619-110">W tym artykule opisano tworzenie puli połączeń dla .NET Framework Data Provider for OLE DB, .NET Framework Data Provider for ODBC i .NET Framework Data Provider for Oracle.</span><span class="sxs-lookup"><span data-stu-id="9f619-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f619-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f619-111">See Also</span></span>  
 [<span data-ttu-id="9f619-112">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9f619-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="9f619-113">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="9f619-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
