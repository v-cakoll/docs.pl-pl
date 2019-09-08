---
title: Pula połączeń
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: c431011cf57fd9ef79c2f0a099ab1080116c571f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786711"
---
# <a name="connection-pooling"></a><span data-ttu-id="70e70-102">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="70e70-102">Connection Pooling</span></span>
<span data-ttu-id="70e70-103">Nawiązywanie połączenia ze źródłem danych może być czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="70e70-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="70e70-104">Aby zminimalizować koszt otwarcia połączeń, ADO.NET korzysta z techniki optymalizacji zwanej *pulą połączeń*, co minimalizuje koszt wielokrotnego otwierania i zamykania połączeń.</span><span class="sxs-lookup"><span data-stu-id="70e70-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="70e70-105">Pule połączeń są obsługiwane inaczej dla dostawców danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70e70-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70e70-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="70e70-106">In This Section</span></span>  
 [<span data-ttu-id="70e70-107">Buforowanie połączenia z programem SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="70e70-107">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="70e70-108">Zawiera omówienie puli połączeń i opisuje sposób działania puli połączeń w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="70e70-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="70e70-109">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="70e70-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="70e70-110">Opisuje pule połączeń dla Dostawca danych .NET Framework, OLE DB .NET Framework Dostawca danych dla ODBC oraz .NET Framework dostawca danych dla programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="70e70-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e70-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70e70-111">See also</span></span>

- [<span data-ttu-id="70e70-112">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="70e70-112">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="70e70-113">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="70e70-113">ADO.NET Overview</span></span>](ado-net-overview.md)
