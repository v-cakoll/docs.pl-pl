---
title: Literały o wartości null i wnioskowanie o typie (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: bb2d9184e17ee2a9916a731eb20eefa105a73753
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249824"
---
# <a name="null-literals-and-type-inference-entity-sql"></a>Literały o wartości null i wnioskowanie o typie (Entity SQL)
Literały null są zgodne z dowolnym typem w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] systemie typów. Jednak dla typu literału wartości null, który ma zostać wywnioskowany prawidłowo, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nakłada pewne ograniczenia dotyczące miejsca, w którym można użyć literału o wartości null.  
  
## <a name="typed-nulls"></a>Wpisane wartości null  
 Wpisane wartości null mogą być używane w dowolnym miejscu. Wnioskowanie typu nie jest wymagane dla wpisanych wartości null, ponieważ typ jest znany. Na przykład można skonstruować wartość null typu Int16 przy użyciu następującej [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcji:  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a>Bezpłatne, zmiennoprzecinkowe literały o wartości null  
 W następujących kontekstach można używać wolnych zmiennoprzecinkowych literałów null:  
  
- Jako argument do wyrażenia CAST lub TREAT. Jest to zalecany sposób tworzenia wyrażeniu o wartości null.  
  
- Jako argument metody lub funkcji. Obowiązują standardowe reguły przeciążenia.  
  
- Jako jeden z argumentów wyrażenia arytmetycznego, takiego jak +,-lub/. Pozostałe argumenty nie mogą być literałami o wartości null; w przeciwnym razie nie jest możliwe wnioskowanie o typie.  
  
- Jako dowolne argumenty wyrażenia logicznego (i, lub, lub nie). Wszystkie argumenty muszą być typu Boolean.  
  
- Jako że argument ma wartość NULL lub jest wyrażeniem niepustym.  
  
- Jako jeden lub więcej argumentów wyrażenia LIKE. Wszystkie argumenty powinny być ciągami.  
  
- Jako jeden lub więcej argumentów konstruktora nazwanego.  
  
- Jako jeden lub więcej argumentów konstruktora zestawu wielokrotnego. Co najmniej jeden argument w konstruktorze zestawów wielokrotnych musi być wyrażeniem, które nie jest literałem null.  
  
- Jako co najmniej jedno wyrażenie THEN lub ELSE w wyrażeniu CASE. Co najmniej jedno wyrażenie THEN lub ELSE w wyrażeniu CASE musi być wyrażeniem innym niż literał o wartości null.  
  
 W innych scenariuszach nie można używać żadnych zmiennoprzecinkowych literałów null. Na przykład nie mogą być używane jako argumenty konstruktora wiersza.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
