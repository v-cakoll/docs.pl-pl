---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 8fbca4f10a7c2c3dbaffff978a536b87d31a8df4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319428"
---
# <a name="parameters-entity-sql"></a>Parametry (Entity SQL)
Parametry są zmiennymi zdefiniowanymi poza [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zwykle za pomocą interfejsu API powiązania, który jest używany przez język hosta. Każdy parametr ma nazwę i typ. Nazwy parametrów są zdefiniowane w wyrażeniach zapytania z symbolem at (@) jako prefiksem. Pozwala to odróżnić je od nazw właściwości lub innych nazw zdefiniowanych w zapytaniu.  
  
 Interfejs API powiązania języka hosta udostępnia interfejsy API dla parametrów powiązań.  
  
## <a name="example"></a>Przykład  
  
```sql  
SELECT c   
      FROM LOB.Customers AS c   
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
