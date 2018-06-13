---
title: Zmienne (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: f271ffc31875e7d94a27f4752b71bfe508fcb620
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765519"
---
# <a name="variables-entity-sql"></a>Zmienne (jednostka SQL)
## <a name="variable"></a>Zmienna  
 Wyrażenie zmiennej jest odwołanie do wyrażenia o nazwie zdefiniowany w bieżącym zakresie. Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikator, zgodnie z definicją w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Poniższy przykład przedstawia użycie zmiennej w wyrażeniu. `c` w polu od klauzuli znajduje się definicja zmiennej. Korzystanie z `c` wybierz w klauzuli reprezentuje odwołanie do zmiennej.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [Parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
