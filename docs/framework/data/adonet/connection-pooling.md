---
title: Pula połączeń
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: 28a1036f377326b5f1fdfafa1eaffd8a47bc05bc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139634"
---
# <a name="connection-pooling"></a><span data-ttu-id="ec99c-102">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="ec99c-102">Connection Pooling</span></span>
<span data-ttu-id="ec99c-103">Łączenie ze źródłem danych może zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="ec99c-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="ec99c-104">Aby zminimalizować koszty otwarcia połączeń, ADO.NET wykorzystuje technikę optymalizacji, o nazwie *buforowanie połączeń*, które minimalizuje koszty wielokrotnym otwieraniem i zamykaniem połączeń.</span><span class="sxs-lookup"><span data-stu-id="ec99c-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="ec99c-105">Pula połączeń różni się dla dostawcy danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec99c-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec99c-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ec99c-106">In This Section</span></span>  
 [<span data-ttu-id="ec99c-107">Buforowanie połączenia z programem SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ec99c-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="ec99c-108">Zawiera omówienie buforowanie połączeń, a w tym artykule opisano, jak działa buforowanie połączeń w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ec99c-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="ec99c-109">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="ec99c-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="ec99c-110">W tym artykule opisano tworzenie puli połączeń dla .NET Framework Data Provider for OLE DB dla programu .NET Framework Data Provider for ODBC i .NET Framework Data Provider for Oracle.</span><span class="sxs-lookup"><span data-stu-id="ec99c-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec99c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec99c-111">See Also</span></span>  
 [<span data-ttu-id="ec99c-112">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ec99c-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="ec99c-113">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ec99c-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
