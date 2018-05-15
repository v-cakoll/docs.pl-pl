---
title: Nieobsługiwane wyrażenia (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: 6d1746bb51af4795f09c47f808cf9a29d0370f18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="unsupported-expressions"></a><span data-ttu-id="43dfa-102">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="43dfa-102">Unsupported expressions</span></span>

<span data-ttu-id="43dfa-103">W tym temacie opisano [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażeń, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43dfa-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="43dfa-104">Aby uzyskać więcej informacji, zobacz [jak jednostki SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="43dfa-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="43dfa-105">Predykaty ilościowy</span><span class="sxs-lookup"><span data-stu-id="43dfa-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="43dfa-106"> Umożliwia skonfigurowanie konstrukcje następującą postać:</span><span class="sxs-lookup"><span data-stu-id="43dfa-106"> allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="43dfa-107">, jednak nie obsługuje takich konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="43dfa-107">, however, does not support such constructs.</span></span> <span data-ttu-id="43dfa-108">Wyrażenia równoważne mogą być napisane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="43dfa-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal > e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="43dfa-109">\* — Operator</span><span class="sxs-lookup"><span data-stu-id="43dfa-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="43dfa-110"> obsługuje korzystanie z \* operatora w klauzuli SELECT, aby wskazać, że wszystkie kolumny powinien przewidywane limit. To nie jest obsługiwany w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43dfa-110"> supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="43dfa-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43dfa-111">See also</span></span>

[<span data-ttu-id="43dfa-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="43dfa-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[<span data-ttu-id="43dfa-113">Jak jednostka SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="43dfa-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
