---
title: Parametry (entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: e1bb633f7f7c7908a5f424991f20a5cd89aee5aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150017"
---
# <a name="parameters-entity-sql"></a>Parametry (entity SQL)
Parametry są zmienne, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]które są zdefiniowane na zewnątrz, zwykle za pośrednictwem powiązania interfejsu API, który jest używany przez język hosta. Każdy parametr ma nazwę i typ. Nazwy parametrów są definiowane w wyrażeniach kwerendy z symbolem at (@) jako prefiksem. To odróżnia je od nazw właściwości lub innych nazw, które są zdefiniowane w kwerendzie.  
  
 Interfejs API powiązania języka hosta udostępnia interfejsy API dla parametrów powiązania.  
  
## <a name="example"></a>Przykład  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
