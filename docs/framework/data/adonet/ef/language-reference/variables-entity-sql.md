---
title: Zmienne (entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149820"
---
# <a name="variables-entity-sql"></a>Zmienne (entity SQL)
## <a name="variable"></a>Zmienna  
 Wyrażenie zmiennej jest odwołaniem do nazwanego wyrażenia zdefiniowanego w bieżącym zakresie. Odwołanie do zmiennej [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musi być prawidłowym identyfikatorem, zgodnie z definicją w [identyfikatorach](identifiers-entity-sql.md).  
  
 Poniższy przykład pokazuje użycie zmiennej w wyrażeniu. W `c` klauzuli FROM jest definicja zmiennej. Użycie `c` w select klauzuli reprezentuje odwołanie do zmiennej.  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Zobacz też

- [Identyfikatory](identifiers-entity-sql.md)
- [Parametry](parameters-entity-sql.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
