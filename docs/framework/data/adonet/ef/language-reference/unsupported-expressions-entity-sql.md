---
title: "Nieobsługiwane wyrażenia (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c18c726a962d9a29a3dace1ebd5c2073637bb4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unsupported-expressions-entity-sql"></a><span data-ttu-id="55270-102">Nieobsługiwane wyrażenia (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="55270-102">Unsupported Expressions (Entity SQL)</span></span>
<span data-ttu-id="55270-103">W tym temacie opisano [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażeń, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55270-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="55270-104">Aby uzyskać więcej informacji, zobacz [jak jednostki SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="55270-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>  
  
## <a name="quantified-predicates"></a><span data-ttu-id="55270-105">Predykaty ilościowy</span><span class="sxs-lookup"><span data-stu-id="55270-105">Quantified Predicates</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="55270-106">Umożliwia skonfigurowanie konstrukcje następującą postać:</span><span class="sxs-lookup"><span data-stu-id="55270-106"> allows constructs of the following form:</span></span>  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="55270-107">, jednak nie obsługuje takich konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="55270-107">, however, does not support such constructs.</span></span> <span data-ttu-id="55270-108">Wyrażenia równoważne mogą być napisane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="55270-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## <a name="-operator"></a><span data-ttu-id="55270-109">* — Operator</span><span class="sxs-lookup"><span data-stu-id="55270-109">* Operator</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="55270-110">obsługuje korzystanie z * operatora w klauzuli SELECT, aby wskazać, że wszystkie kolumny powinien przewidywane limit. To nie jest obsługiwany w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55270-110"> supports the use of the * operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55270-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55270-111">See Also</span></span>  
 [<span data-ttu-id="55270-112">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="55270-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="55270-113">Jak jednostki SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="55270-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
