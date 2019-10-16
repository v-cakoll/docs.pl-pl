---
title: Zmienne (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bb8e6ebe81dacc7ec0f45fdde65b9c18cfd76789
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319202"
---
# <a name="variables-entity-sql"></a>Zmienne (Entity SQL)
## <a name="variable"></a>Zmienna  
 Wyrażenie zmiennej jest odwołaniem do nazwanego wyrażenia zdefiniowanego w bieżącym zakresie. Odwołanie do zmiennej musi być prawidłowym identyfikatorem [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zgodnie z definicją w [identyfikatorach](identifiers-entity-sql.md).  
  
 W poniższym przykładzie pokazano użycie zmiennej w wyrażeniu. @No__t-0 w klauzuli FROM jest definicją zmiennej. Użycie `c` w klauzuli SELECT reprezentuje odwołanie do zmiennej.  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Zobacz także

- [Identyfikatory](identifiers-entity-sql.md)
- [Parametry](parameters-entity-sql.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
