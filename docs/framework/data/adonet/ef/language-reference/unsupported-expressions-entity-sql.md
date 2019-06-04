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
# <a name="unsupported-expressions"></a>Nieobsługiwane wyrażenia

W tym temacie opisano wyrażeń języka Transact-SQL, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Aby uzyskać więcej informacji, zobacz [jak jednostka SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Ilościowe predykatów

Języka Transact-SQL umożliwia konstrukcje następującą postać:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)], jednak nie obsługuje takich konstrukcji. Równoważne wyrażenia może być napisana w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób:

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* — Operator

Języka Transact-SQL obsługuje korzystanie z * operatora w klauzuli SELECT, aby wskazać, czy wszystkie kolumny powinien być przekazywany się. To nie jest obsługiwana w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Jak jednostka SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
