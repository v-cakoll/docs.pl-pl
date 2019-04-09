---
title: Zmienne (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bf6fa95e38d1eb5817fd67165b6993cbb0755fd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153585"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="baaef-102">Zmienne (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="baaef-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="baaef-103">Zmienna</span><span class="sxs-lookup"><span data-stu-id="baaef-103">Variable</span></span>  
 <span data-ttu-id="baaef-104">Wyrażenie zmiennych jest odwołaniem do nazwanego wyrażenia zdefiniowany w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="baaef-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="baaef-105">Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikator, zgodnie z definicją w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="baaef-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="baaef-106">Poniższy przykład pokazuje użycie zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="baaef-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="baaef-107">`c` w polu od klauzula jest definicją zmiennej.</span><span class="sxs-lookup"><span data-stu-id="baaef-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="baaef-108">Korzystanie z `c` wybierz w klauzuli reprezentuje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="baaef-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="baaef-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baaef-109">See also</span></span>

- [<span data-ttu-id="baaef-110">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="baaef-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [<span data-ttu-id="baaef-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="baaef-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [<span data-ttu-id="baaef-112">Przegląd języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="baaef-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
