---
title: Zmienne (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bb8e6ebe81dacc7ec0f45fdde65b9c18cfd76789
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319202"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="c12e2-102">Zmienne (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c12e2-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="c12e2-103">Zmienna</span><span class="sxs-lookup"><span data-stu-id="c12e2-103">Variable</span></span>  
 <span data-ttu-id="c12e2-104">Wyrażenie zmiennej jest odwołaniem do nazwanego wyrażenia zdefiniowanego w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="c12e2-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="c12e2-105">Odwołanie do zmiennej musi być prawidłowym identyfikatorem [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zgodnie z definicją w [identyfikatorach](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c12e2-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c12e2-106">W poniższym przykładzie pokazano użycie zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="c12e2-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="c12e2-107">@No__t-0 w klauzuli FROM jest definicją zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c12e2-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="c12e2-108">Użycie `c` w klauzuli SELECT reprezentuje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c12e2-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="c12e2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c12e2-109">See also</span></span>

- [<span data-ttu-id="c12e2-110">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="c12e2-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="c12e2-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="c12e2-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="c12e2-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c12e2-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
