---
title: Zmienne (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bf6fa95e38d1eb5817fd67165b6993cbb0755fd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153585"
---
# <a name="variables-entity-sql"></a>Zmienne (jednostka SQL)
## <a name="variable"></a>Zmienna  
 Wyrażenie zmiennych jest odwołaniem do nazwanego wyrażenia zdefiniowany w bieżącym zakresie. Odwołanie do zmiennej musi być prawidłowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikator, zgodnie z definicją w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Poniższy przykład pokazuje użycie zmiennej w wyrażeniu. `c` w polu od klauzula jest definicją zmiennej. Korzystanie z `c` wybierz w klauzuli reprezentuje odwołanie do zmiennej.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Zobacz także

- [Identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [Parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
