---
title: Funkcje (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: ec94a0f16fb3b836297f6675cc938a711816555b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250905"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="d7309-102">Funkcje (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d7309-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="d7309-103">Entity SQL obsługuje funkcje zdefiniowane przez użytkownika, funkcje kanoniczne i funkcje specyficzne dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d7309-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="d7309-104">Funkcje zdefiniowane przez użytkownika są określone w modelu koncepcyjnym lub wbudowane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="d7309-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="d7309-105">Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d7309-105">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="d7309-106">Funkcje kanoniczne są wstępnie zdefiniowane w Entity Framework i powinny być obsługiwane przez dostawców danych.</span><span class="sxs-lookup"><span data-stu-id="d7309-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="d7309-107">Entity SQL polecenia zakończą się niepowodzeniem, jeśli użytkownik wywoła funkcję, która nie jest obsługiwana przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="d7309-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="d7309-108">W związku z tym funkcje kanoniczne są zwykle zalecane w stosunku do funkcji specyficznych dla magazynu, które znajdują się w przestrzeni nazw specyficznej dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d7309-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="d7309-109">Aby uzyskać więcej informacji, zobacz [funkcje kanoniczne](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d7309-109">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="d7309-110">Dostawca zarządzany przez klienta programu Microsoft SQL Server udostępnia zestaw funkcji specyficznych dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d7309-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="d7309-111">Aby uzyskać więcej informacji, zobacz temat [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d7309-111">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7309-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d7309-112">In This Section</span></span>  
 [<span data-ttu-id="d7309-113">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="d7309-113">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="d7309-114">Rozpoznanie przeciążenia funkcji</span><span class="sxs-lookup"><span data-stu-id="d7309-114">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="d7309-115">Funkcje agregujące</span><span class="sxs-lookup"><span data-stu-id="d7309-115">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7309-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7309-116">See also</span></span>

- [<span data-ttu-id="d7309-117">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d7309-117">Entity SQL Overview</span></span>](entity-sql-overview.md)
