---
title: Pierwszeństwo operatorów (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 2d8c78f410708fd1aa843ee8f14f7243a9f686c0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249783"
---
# <a name="operator-precedence-entity-sql"></a>Pierwszeństwo operatorów (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Gdy zapytanie ma wiele operatorów, pierwszeństwo operatorów określa kolejność wykonywania operacji. Kolejność wykonywania może znacząco wpłynąć na wynik zapytania.  
  
 Operatory mają poziomy pierwszeństwa pokazane w poniższej tabeli. Operator o wyższym poziomie jest obliczany przed operatorem o niższym poziomie.  
  
|Poziom|Typ operacji|Operator|  
|-----------|--------------------|--------------|  
|1|Podstawowy|`. , [] ()`|  
|2|Jednostk|`! not`|  
|3|Mnożeniowy|`* / %`|  
|4|Dana|`+ -`|  
|5|Szeregowanie|`< > <= >=`|  
|6|Równości|`= != <>`|  
|7|Warunkowego AND|`and &&`|  
|8|Warunkowego OR|`or &#124;&#124;`|  
  
 Gdy dwa operatory w wyrażeniu mają ten sam poziom pierwszeństwa operatora, są oceniane od lewej do prawej na podstawie ich pozycji w zapytaniu. Na przykład, `x+y-z` jest oceniane jako `(x+y)-z`.  
  
 Możesz użyć nawiasów, aby przesłonić zdefiniowane pierwszeństwo operatorów w zapytaniu. Wszystkie elementy w nawiasach są oceniane jako pierwsze w celu uzyskania pojedynczego wyniku, zanim ten wynik może być używany przez dowolny operator poza nawiasami. `x+y*z` Na przykład `x` `x` `(x+y)*z` `y` mnoży wartość `z`przez, a następnie dodaje, ale dodaje do, a następnie mnoży wynik przez `z`. `y`  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
