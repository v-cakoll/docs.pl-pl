---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3b746a82f72fc7f42f9d91ddd0a7d6f4f86ac0bb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250574"
---
# <a name="isof-entity-sql"></a>ISOF (Entity SQL)
Określa, czy typ wyrażenia jest określonego typu czy jednego z jego podtypów.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie zapytania, aby określić typ.  
  
 NIEMOŻLIWE  
 Negacja modelu EDM. Wynik wartości logicznej wynosi.  
  
 JEDYN  
 Określa, że jest zwraca `true` tylko wtedy `expression` , gdy jest `type` typu, a nie dowolnego jednego z jego podtypów.  
  
 `type`  
 Typ do przetestowania `expression` . Typ musi być kwalifikowaną przestrzenią nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `expression` parametr jest typu T i T jest typem podstawowym lub `type`typem pochodnym; null, jeśli `expression` ma wartość null w czasie wykonywania; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenia `expression IS NOT OF (type)` i `expression IS NOT OF (ONLY type)` są syntaktycznie równoważne z `NOT (expression IS OF (type))` i `NOT (expression IS OF (ONLY type))`, odpowiednio.  
  
 W poniższej tabeli przedstawiono zachowanie `IS OF` operatora w przypadku niektórych wzorców typowych i narożnych. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|wartość zerowa jest typu (EntityType)|Generuje|  
|wartość zerowa jest równa (ComplexType)|Generuje|  
|wartość zerowa jest równa (RowType)|Generuje|  
|Traktuj (wartość null jako element EntityType) to (EntityType)|Zwraca wartość DBNull|  
|Traktuj (wartość null jako ComplexType) to (ComplexType)|Generuje|  
|Traktuj (wartość null AS RowType) to (RowType)|Generuje|  
|Typ EntityType to (EntityType)|Zwraca wartość PRAWDA/FAŁSZ|  
|ComplexType jest typu (ComplexType)|Generuje|  
|RowType jest (RowType)|Generuje|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora is, aby określić typ wyrażenia zapytania, a następnie używa operatora Traktuj do konwersji obiektu typu kursu do kolekcji obiektów typu OnsiteCourse. Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
