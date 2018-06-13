---
title: Funkcje (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: 6c8a44a4e347ffabd665847f02bfafe267a14103
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760300"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="40d15-102">Funkcje (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="40d15-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="40d15-103">Jednostki SQL obsługuje funkcje zdefiniowane przez użytkownika, kanonicznej funkcji i funkcji specyficznych dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="40d15-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="40d15-104">Funkcje zdefiniowane przez użytkownika są określone w modelu koncepcyjnym lub wbudowany w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="40d15-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="40d15-105">Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="40d15-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="40d15-106">Canonical funkcje są wstępnie zdefiniowane w ramach jednostki i powinny być obsługiwane przez dostawcę danych.</span><span class="sxs-lookup"><span data-stu-id="40d15-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="40d15-107">Jednostki poleceń SQL zakończy się niepowodzeniem, jeśli użytkownik wywołuje funkcję, która nie jest obsługiwana przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="40d15-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="40d15-108">W związku z tym funkcje canonical ogólnie zaleca się za pośrednictwem funkcji specyficznych dla magazynu, które znajdują się w przestrzeni nazw specyficznych dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="40d15-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="40d15-109">Aby uzyskać więcej informacji, zobacz [kanonicznej funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="40d15-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="40d15-110">Microsoft SQL klienta zarządzanego dostawcy zawiera zestaw funkcji specyficznych dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="40d15-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="40d15-111">Aby uzyskać więcej informacji, zobacz [SqlClient Entity Framework funkcji](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="40d15-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40d15-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="40d15-112">In This Section</span></span>  
 [<span data-ttu-id="40d15-113">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="40d15-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="40d15-114">Rozpoznanie przeciążenia funkcji</span><span class="sxs-lookup"><span data-stu-id="40d15-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="40d15-115">Funkcje agregujące</span><span class="sxs-lookup"><span data-stu-id="40d15-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="40d15-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40d15-116">See Also</span></span>  
 [<span data-ttu-id="40d15-117">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="40d15-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
