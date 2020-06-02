---
title: Pula połączeń
description: Dowiedz się więcej o puli połączeń, która ADO.NET używa do minimalizowania kosztów otwierania połączeń ze źródłami danych.
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: b8f89dfda7edbde14dbb5945f10f2284ac43c3d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287093"
---
# <a name="connection-pooling"></a><span data-ttu-id="81ab5-103">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="81ab5-103">Connection Pooling</span></span>
<span data-ttu-id="81ab5-104">Nawiązywanie połączenia ze źródłem danych może być czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="81ab5-104">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="81ab5-105">Aby zminimalizować koszt otwarcia połączeń, ADO.NET korzysta z techniki optymalizacji zwanej *pulą połączeń*, co minimalizuje koszt wielokrotnego otwierania i zamykania połączeń.</span><span class="sxs-lookup"><span data-stu-id="81ab5-105">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="81ab5-106">Pule połączeń są obsługiwane inaczej dla dostawców danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81ab5-106">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81ab5-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="81ab5-107">In This Section</span></span>  
 [<span data-ttu-id="81ab5-108">Buforowanie połączenia z programem SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="81ab5-108">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="81ab5-109">Zawiera omówienie puli połączeń i opisuje sposób działania puli połączeń w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="81ab5-109">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="81ab5-110">Buforowanie połączenia Oracle, OLE DB i ODBC</span><span class="sxs-lookup"><span data-stu-id="81ab5-110">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="81ab5-111">Opisuje pule połączeń dla Dostawca danych .NET Framework, OLE DB .NET Framework Dostawca danych dla ODBC oraz .NET Framework dostawca danych dla programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="81ab5-111">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ab5-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81ab5-112">See also</span></span>

- [<span data-ttu-id="81ab5-113">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="81ab5-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="81ab5-114">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="81ab5-114">ADO.NET Overview</span></span>](ado-net-overview.md)
