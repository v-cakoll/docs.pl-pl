---
title: Zmienne (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 551b6d6feab6829c9a2f6f2e89e1918acf463411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="variables-entity-sql"></a><span data-ttu-id="87c8d-102">Zmienne (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="87c8d-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="87c8d-103">Zmienna</span><span class="sxs-lookup"><span data-stu-id="87c8d-103">Variable</span></span>  
 <span data-ttu-id="87c8d-104">Wyrażenie zmiennej jest odwołanie do wyrażenia o nazwie zdefiniowany w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="87c8d-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="87c8d-105">Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikator, zgodnie z definicją w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="87c8d-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="87c8d-106">Poniższy przykład przedstawia użycie zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="87c8d-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="87c8d-107">`c` w polu od klauzuli znajduje się definicja zmiennej.</span><span class="sxs-lookup"><span data-stu-id="87c8d-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="87c8d-108">Korzystanie z `c` wybierz w klauzuli reprezentuje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="87c8d-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="87c8d-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87c8d-109">See Also</span></span>  
 [<span data-ttu-id="87c8d-110">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="87c8d-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="87c8d-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="87c8d-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="87c8d-112">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="87c8d-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
