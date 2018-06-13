---
title: Zmienne (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: f271ffc31875e7d94a27f4752b71bfe508fcb620
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765519"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="901d0-102">Zmienne (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="901d0-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="901d0-103">Zmienna</span><span class="sxs-lookup"><span data-stu-id="901d0-103">Variable</span></span>  
 <span data-ttu-id="901d0-104">Wyrażenie zmiennej jest odwołanie do wyrażenia o nazwie zdefiniowany w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="901d0-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="901d0-105">Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikator, zgodnie z definicją w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="901d0-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="901d0-106">Poniższy przykład przedstawia użycie zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="901d0-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="901d0-107">`c` w polu od klauzuli znajduje się definicja zmiennej.</span><span class="sxs-lookup"><span data-stu-id="901d0-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="901d0-108">Korzystanie z `c` wybierz w klauzuli reprezentuje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="901d0-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="901d0-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="901d0-109">See Also</span></span>  
 [<span data-ttu-id="901d0-110">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="901d0-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="901d0-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="901d0-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="901d0-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="901d0-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
