---
title: Zmienne (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bf6fa95e38d1eb5817fd67165b6993cbb0755fd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879778"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="1c155-102">Zmienne (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="1c155-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="1c155-103">Zmienna</span><span class="sxs-lookup"><span data-stu-id="1c155-103">Variable</span></span>  
 <span data-ttu-id="1c155-104">Wyrażenie zmiennych jest odwołaniem do nazwanego wyrażenia zdefiniowany w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="1c155-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="1c155-105">Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikator, zgodnie z definicją w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1c155-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="1c155-106">Poniższy przykład pokazuje użycie zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="1c155-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="1c155-107">`c` w polu od klauzula jest definicją zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1c155-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="1c155-108">Korzystanie z `c` wybierz w klauzuli reprezentuje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1c155-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c155-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c155-109">See also</span></span>

- [<span data-ttu-id="1c155-110">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="1c155-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [<span data-ttu-id="1c155-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c155-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [<span data-ttu-id="1c155-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1c155-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
