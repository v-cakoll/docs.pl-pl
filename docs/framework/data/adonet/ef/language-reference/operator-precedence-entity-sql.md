---
title: Kolejność wykonywania działań (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 722ebe5f0ec530f8c7f86e9f9901451b060903f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159136"
---
# <a name="operator-precedence-entity-sql"></a>Kolejność wykonywania działań (jednostka SQL)
Gdy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie ma wiele operatory, pierwszeństwo operatorów określa kolejność, w której operacje są wykonywane. Kolejność wykonywania może znacząco wpłynąć na wynik zapytania.  
  
 Operatory mają poziomy pierwszeństwa, pokazano w poniższej tabeli. Operator na wyższym poziomie jest oceniany przed operatorem o niższym poziomie.  
  
|Poziom|Typ operacji|Operator|  
|-----------|--------------------|--------------|  
|1|Podstawowy|`. , [] ()`|  
|2|Jednoargumentowy|`! not`|  
|3|Mnożeniowy|`* / %`|  
|4|Dodatku|`+ -`|  
|5|Szeregowanie|`< > <= >=`|  
|6|Równości|`= != <>`|  
|7|Warunkowego AND|`and &&`|  
|8|Warunkowego OR|`or &#124;&#124;`|  
  
 Gdy dwa operatory w wyrażeniu mają pierwszeństwo przed operatorem na tym samym poziomie, ich są obliczane od lewej do prawej, na podstawie ich pozycji w zapytaniu. Na przykład `x+y-z` jest oceniane jako `(x+y)-z`.  
  
 Można użyć nawiasów do zastąpienia zdefiniowane pierwszeństwo operatorów w zapytaniu. Wszystko wewnątrz nawiasów jest stosowana jako pierwsza umożliwiające uzyskanie pojedynczego wyniku przed, że wyniki mogą być używane przez dowolny operator poza nawiasami. Na przykład `x+y*z` mnoży `y` przez `z` , a następnie dodaje `x`, ale `(x+y)*z` dodaje `x` do `y` i następnie mnoży wynik przez `z`.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
