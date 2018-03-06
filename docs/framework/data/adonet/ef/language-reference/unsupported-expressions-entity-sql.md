---
title: "Nieobsługiwane wyrażenia (jednostka SQL)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-ado
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
dev_langs:
- sql
ms.openlocfilehash: 075daf0e4f0477dda50231760fbb3d990a9f8468
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
---
# <a name="unsupported-expressions"></a><span data-ttu-id="e9321-102">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="e9321-102">Unsupported expressions</span></span>

<span data-ttu-id="e9321-103">W tym temacie opisano [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażeń, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9321-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="e9321-104">Aby uzyskać więcej informacji, zobacz [jak jednostki SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e9321-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="e9321-105">Predykaty ilościowy</span><span class="sxs-lookup"><span data-stu-id="e9321-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="e9321-106">Umożliwia skonfigurowanie konstrukcje następującą postać:</span><span class="sxs-lookup"><span data-stu-id="e9321-106">allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e9321-107">, jednak nie obsługuje takich konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="e9321-107">, however, does not support such constructs.</span></span> <span data-ttu-id="e9321-108">Wyrażenia równoważne mogą być napisane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e9321-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal > e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="e9321-109">\* — Operator</span><span class="sxs-lookup"><span data-stu-id="e9321-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="e9321-110">obsługuje korzystanie z \* operatora w klauzuli SELECT, aby wskazać, że wszystkie kolumny powinien przewidywane limit. To nie jest obsługiwany w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9321-110">supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="e9321-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9321-111">See also</span></span>

[<span data-ttu-id="e9321-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e9321-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[<span data-ttu-id="e9321-113">Jak jednostka SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e9321-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
