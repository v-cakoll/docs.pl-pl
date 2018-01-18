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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d035f8d5616f2eb4c5a4db31857da2be0cd3d930
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="variables-entity-sql"></a><span data-ttu-id="18166-102">Zmienne (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="18166-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="18166-103">Zmienna</span><span class="sxs-lookup"><span data-stu-id="18166-103">Variable</span></span>  
 <span data-ttu-id="18166-104">Wyrażenie zmiennej jest odwołanie do wyrażenia o nazwie zdefiniowany w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="18166-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="18166-105">Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikator, zgodnie z definicją w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="18166-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="18166-106">Poniższy przykład przedstawia użycie zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="18166-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="18166-107">`c` w polu od klauzuli znajduje się definicja zmiennej.</span><span class="sxs-lookup"><span data-stu-id="18166-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="18166-108">Korzystanie z `c` wybierz w klauzuli reprezentuje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="18166-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="18166-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18166-109">See Also</span></span>  
 [<span data-ttu-id="18166-110">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="18166-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="18166-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="18166-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="18166-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="18166-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
