---
title: Nieobsługiwane wyrażenia (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: bf20bb92010d5031e973cb1cc004b6b8f13d0091
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="unsupported-expressions"></a><span data-ttu-id="f1ee2-102">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="f1ee2-102">Unsupported expressions</span></span>

<span data-ttu-id="f1ee2-103">W tym temacie opisano [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażeń, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1ee2-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="f1ee2-104">Aby uzyskać więcej informacji, zobacz [jak jednostki SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f1ee2-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="f1ee2-105">Predykaty ilościowy</span><span class="sxs-lookup"><span data-stu-id="f1ee2-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="f1ee2-106"> Umożliwia skonfigurowanie konstrukcje następującą postać:</span><span class="sxs-lookup"><span data-stu-id="f1ee2-106"> allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f1ee2-107">, jednak nie obsługuje takich konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="f1ee2-107">, however, does not support such constructs.</span></span> <span data-ttu-id="f1ee2-108">Wyrażenia równoważne mogą być napisane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f1ee2-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="f1ee2-109">\* — Operator</span><span class="sxs-lookup"><span data-stu-id="f1ee2-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="f1ee2-110"> obsługuje korzystanie z \* operatora w klauzuli SELECT, aby wskazać, że wszystkie kolumny powinien przewidywane limit. To nie jest obsługiwany w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1ee2-110"> supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="f1ee2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1ee2-111">See also</span></span>

[<span data-ttu-id="f1ee2-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f1ee2-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[<span data-ttu-id="f1ee2-113">Jak jednostka SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f1ee2-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
