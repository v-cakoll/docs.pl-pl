---
title: Zmienne (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248690"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="23f6d-102">Zmienne (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="23f6d-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="23f6d-103">Zmienna</span><span class="sxs-lookup"><span data-stu-id="23f6d-103">Variable</span></span>  
 <span data-ttu-id="23f6d-104">Wyrażenie zmiennej jest odwołaniem do nazwanego wyrażenia zdefiniowanego w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="23f6d-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="23f6d-105">Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikatorem, zgodnie z definicją w [identyfikatorach](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="23f6d-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="23f6d-106">W poniższym przykładzie pokazano użycie zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="23f6d-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="23f6d-107">`c` W klauzuli FROM jest definicją zmiennej.</span><span class="sxs-lookup"><span data-stu-id="23f6d-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="23f6d-108">Użycie `c` w klauzuli select reprezentuje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="23f6d-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="23f6d-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23f6d-109">See also</span></span>

- [<span data-ttu-id="23f6d-110">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="23f6d-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="23f6d-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="23f6d-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="23f6d-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="23f6d-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
