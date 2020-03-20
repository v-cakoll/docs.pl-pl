---
title: Zmienne (entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149820"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="f6168-102">Zmienne (entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f6168-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="f6168-103">Zmienna</span><span class="sxs-lookup"><span data-stu-id="f6168-103">Variable</span></span>  
 <span data-ttu-id="f6168-104">Wyrażenie zmiennej jest odwołaniem do nazwanego wyrażenia zdefiniowanego w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f6168-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="f6168-105">Odwołanie do zmiennej [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musi być prawidłowym identyfikatorem, zgodnie z definicją w [identyfikatorach](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f6168-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="f6168-106">Poniższy przykład pokazuje użycie zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="f6168-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="f6168-107">W `c` klauzuli FROM jest definicja zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f6168-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="f6168-108">Użycie `c` w select klauzuli reprezentuje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f6168-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6168-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6168-109">See also</span></span>

- [<span data-ttu-id="f6168-110">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="f6168-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="f6168-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6168-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="f6168-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f6168-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
