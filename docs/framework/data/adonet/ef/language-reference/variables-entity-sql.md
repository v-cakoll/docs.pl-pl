---
title: Zmienne (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248690"
---
# <a name="variables-entity-sql"></a>Zmienne (Entity SQL)
## <a name="variable"></a>Zmienna  
 Wyrażenie zmiennej jest odwołaniem do nazwanego wyrażenia zdefiniowanego w bieżącym zakresie. Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikatorem, zgodnie z definicją w [identyfikatorach](identifiers-entity-sql.md).  
  
 W poniższym przykładzie pokazano użycie zmiennej w wyrażeniu. `c` W klauzuli FROM jest definicją zmiennej. Użycie `c` w klauzuli select reprezentuje odwołanie do zmiennej.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Zobacz także

- [Identyfikatory](identifiers-entity-sql.md)
- [Parametry](parameters-entity-sql.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
