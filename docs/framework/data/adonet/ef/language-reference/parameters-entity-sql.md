---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249586"
---
# <a name="parameters-entity-sql"></a>Parametry (Entity SQL)
Parametry są zmiennymi, które są [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zdefiniowane poza, zwykle za pomocą powiązania interfejsu API, który jest używany przez język hosta. Każdy parametr ma nazwę i typ. Nazwy parametrów są zdefiniowane w wyrażeniach zapytania z symbolem at (@) jako prefiksem. Pozwala to odróżnić je od nazw właściwości lub innych nazw zdefiniowanych w zapytaniu.  
  
 Interfejs API powiązania języka hosta udostępnia interfejsy API dla parametrów powiązań.  
  
## <a name="example"></a>Przykład  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
