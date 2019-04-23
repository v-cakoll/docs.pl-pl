---
title: Funkcje (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: f31f829b53160da5a043617b9aa999b398859f17
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080608"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="2ae9f-102">Funkcje (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="2ae9f-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="2ae9f-103">Jednostka SQL obsługuje funkcje zdefiniowane przez użytkownika, funkcje canonical i funkcje właściwe dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="2ae9f-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="2ae9f-104">Funkcje zdefiniowane przez użytkownika są określone w model koncepcyjny lub wbudowane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="2ae9f-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="2ae9f-105">Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2ae9f-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="2ae9f-106">Funkcje Canonical są wstępnie zdefiniowane w programie Entity Framework i powinna być obsługiwana przez dostawcę danych.</span><span class="sxs-lookup"><span data-stu-id="2ae9f-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="2ae9f-107">Polecenia SQL jednostki zakończy się niepowodzeniem, jeśli użytkownik wywołuje funkcję, która nie jest obsługiwana przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="2ae9f-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="2ae9f-108">W związku z tym funkcje canonical ogólnie zaleca się za pośrednictwem funkcji specyficznych dla magazynu, które znajdują się w przestrzeni nazw właściwe dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="2ae9f-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="2ae9f-109">Aby uzyskać więcej informacji, zobacz [funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="2ae9f-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="2ae9f-110">Program Microsoft SQL klienta zarządzanego dostawcy zawiera zestaw funkcji specyficznych dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="2ae9f-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="2ae9f-111">Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="2ae9f-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ae9f-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2ae9f-112">In This Section</span></span>  
 [<span data-ttu-id="2ae9f-113">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="2ae9f-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="2ae9f-114">Rozpoznanie przeciążenia funkcji</span><span class="sxs-lookup"><span data-stu-id="2ae9f-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="2ae9f-115">Funkcje agregujące</span><span class="sxs-lookup"><span data-stu-id="2ae9f-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ae9f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ae9f-116">See also</span></span>

- [<span data-ttu-id="2ae9f-117">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="2ae9f-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
