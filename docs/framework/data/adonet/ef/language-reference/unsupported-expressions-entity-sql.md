---
title: Nieobsługiwane wyrażenia (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: 956fe117eb0c59392c3999046bc70deaed268ac6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248782"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="a0451-102">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="a0451-102">Unsupported expressions</span></span>

<span data-ttu-id="a0451-103">W tym temacie opisano wyrażenia języka Transact-SQL, które nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)]są obsługiwane w programie.</span><span class="sxs-lookup"><span data-stu-id="a0451-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="a0451-104">Aby uzyskać więcej informacji, zobacz [jak Entity SQL różni się od języka Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a0451-104">For more information, see [How Entity SQL Differs from Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="a0451-105">Predykaty ilościowe</span><span class="sxs-lookup"><span data-stu-id="a0451-105">Quantified predicates</span></span>

<span data-ttu-id="a0451-106">Język Transact-SQL umożliwia konstrukcje z następującej postaci:</span><span class="sxs-lookup"><span data-stu-id="a0451-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a0451-107">Jednak program nie obsługuje takich konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="a0451-107">, however, does not support such constructs.</span></span> <span data-ttu-id="a0451-108">Równoważne wyrażenia można napisać w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a0451-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="a0451-109">\* — Operator</span><span class="sxs-lookup"><span data-stu-id="a0451-109">\* operator</span></span>

<span data-ttu-id="a0451-110">Język Transact-SQL obsługuje użycie operatora \* w klauzuli SELECT, aby wskazać, że wszystkie kolumny powinny być rzutowane. Nie jest to obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]programie.</span><span class="sxs-lookup"><span data-stu-id="a0451-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="a0451-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0451-111">See also</span></span>

- [<span data-ttu-id="a0451-112">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a0451-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="a0451-113">Jak jednostka SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a0451-113">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)
