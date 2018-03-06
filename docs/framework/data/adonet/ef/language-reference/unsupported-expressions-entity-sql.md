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
# <a name="unsupported-expressions"></a>Nieobsługiwane wyrażenia

W tym temacie opisano [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażeń, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Aby uzyskać więcej informacji, zobacz [jak jednostki SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Predykaty ilościowy

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] Umożliwia skonfigurowanie konstrukcje następującą postać:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)], jednak nie obsługuje takich konstrukcji. Wyrażenia równoważne mogą być napisane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób:

```sql
not exists(select 0 from employees as e where sal > e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* — Operator

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] obsługuje korzystanie z * operatora w klauzuli SELECT, aby wskazać, że wszystkie kolumny powinien przewidywane limit. To nie jest obsługiwany w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Zobacz także

[Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[Jak jednostka SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
