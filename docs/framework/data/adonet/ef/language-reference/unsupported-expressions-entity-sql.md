---
title: Nieobsługiwane wyrażenia (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: af0e00f470584883b6a65b63f2650c1c359b404c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489856"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="853b7-102">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="853b7-102">Unsupported expressions</span></span>

<span data-ttu-id="853b7-103">W tym temacie opisano wyrażeń języka Transact-SQL, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="853b7-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="853b7-104">Aby uzyskać więcej informacji, zobacz [jak jednostka SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="853b7-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="853b7-105">Ilościowe predykatów</span><span class="sxs-lookup"><span data-stu-id="853b7-105">Quantified predicates</span></span>

<span data-ttu-id="853b7-106">Języka Transact-SQL umożliwia konstrukcje następującą postać:</span><span class="sxs-lookup"><span data-stu-id="853b7-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="853b7-107">, jednak nie obsługuje takich konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="853b7-107">, however, does not support such constructs.</span></span> <span data-ttu-id="853b7-108">Równoważne wyrażenia może być napisana w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="853b7-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="853b7-109">\* — Operator</span><span class="sxs-lookup"><span data-stu-id="853b7-109">\* operator</span></span>

<span data-ttu-id="853b7-110">Języka Transact-SQL obsługuje korzystanie z \* operatora w klauzuli SELECT, aby wskazać, czy wszystkie kolumny powinien być przekazywany się. To nie jest obsługiwana w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="853b7-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="853b7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="853b7-111">See also</span></span>

- [<span data-ttu-id="853b7-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="853b7-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="853b7-113">Jak jednostka SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="853b7-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
