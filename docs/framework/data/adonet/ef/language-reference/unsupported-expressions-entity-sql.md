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
# <a name="unsupported-expressions"></a>Nieobsługiwane wyrażenia

W tym temacie opisano wyrażenia języka Transact-SQL, które nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)]są obsługiwane w programie. Aby uzyskać więcej informacji, zobacz [jak Entity SQL różni się od języka Transact-SQL](how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Predykaty ilościowe

Język Transact-SQL umożliwia konstrukcje z następującej postaci:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Jednak program nie obsługuje takich konstrukcji. Równoważne wyrażenia można napisać w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] następujący sposób:

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* — Operator

Język Transact-SQL obsługuje użycie operatora * w klauzuli SELECT, aby wskazać, że wszystkie kolumny powinny być rzutowane. Nie jest to obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]programie.

## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Jak jednostka SQL różni się od języka Transact-SQL](how-entity-sql-differs-from-transact-sql.md)
