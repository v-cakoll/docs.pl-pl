---
title: Literały null i wnioskowanie o typie (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 3fea03146549f3d42bf08bbd5e7ce355d25bd4eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641812"
---
# <a name="null-literals-and-type-inference-entity-sql"></a>Literały null i wnioskowanie o typie (jednostka SQL)
Literały null są zgodne z żadnym typem w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] system typów. Jednak w przypadku typu literałem o wartości null, aby był wywnioskowany poprawnie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nakłada pewne ograniczenia dotyczące użycia właściwość literal o wartości null.  
  
## <a name="typed-nulls"></a>Wpisane wartości null  
 Wpisane wartości null może służyć w dowolnym miejscu. Wnioskowanie o typie nie jest wymagana dla wpisane wartości null, ponieważ typ jest znany. Na przykład można utworzyć wartości null typu Int16 następującym kodem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstruowania:  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a>Swobodny literały Null  
 Swobodny literały null może służyć w następujących okolicznościach:  
  
- Jako argument do RZUTOWANIA lub TRAKTUJ wyrażenia. Jest to zalecany sposób tworzenia wpisane wyrażenie o wartości null.  
  
- Jako argument do metody lub funkcji. Przeciążenie standardowe reguły mają zastosowanie.  
  
- Jako jeden z argumentów do wyrażenia arytmetyczne, takie jak +, -, lub /. Drugi argument nie może być literały null, w przeciwnym razie wnioskowanie typu zerowalnego nie jest możliwe.  
  
- Jako argumenty, które mają wyrażenie logiczne (AND, OR lub nie). Wszystkie argumenty są znane jako typu Boolean.  
  
- Jako argument wyrażenia jest wartość NULL lub nie jest równa NULL.  
  
- Jako co najmniej jeden z argumentów do wyrażenia LIKE. Wszystkie argumenty powinny być ciągami.  
  
- Jako jeden lub więcej argumentów konstruktora typu o nazwie.  
  
- Jako jeden lub więcej argumentów Konstruktor multiset. Co najmniej jeden argument Pro Konstruktor multiset — musi być wyrażeniem, które nie jest literałem o wartości null.  
  
- Ponieważ co najmniej jedno z wyrażeń w wyrażeniu CASE następnie albo też. Co najmniej jedno z wyrażeń w wyrażeniu CASE następnie albo też musi być wyrażeniem innym niż literałem o wartości null.  
  
 Swobodny literały null nie można używać w innych scenariuszach. Na przykład nie mogą być używane jako argumenty konstruktorze wierszy.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
