---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: c4c4cbf74cb17cf43e79c42ff42d1e68122fd534
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319717"
---
# <a name="isof-entity-sql"></a>ISOF (Entity SQL)
Określa, czy typ wyrażenia jest określonego typu czy jednego z jego podtypów.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie zapytania, aby określić typ.  
  
 NIEMOŻLIWE  
 Negacja modelu EDM. Wynik wartości logicznej wynosi.  
  
 JEDYN  
 Określa, że jest zwraca wartość `true` tylko wtedy, gdy `expression` jest typu `type`, a nie jednego z jego podtypów.  
  
 `type`  
 Typ, dla którego ma zostać przetestowany `expression`. Typ musi być kwalifikowaną przestrzenią nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `expression` jest typu T, a T jest typem podstawowym lub pochodnym typem `type`; wartość null, jeśli `expression` ma wartość null w czasie wykonywania; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenia `expression IS NOT OF (type)` i `expression IS NOT OF (ONLY type)` są syntaktycznie równoważne odpowiednio `NOT (expression IS OF (type))` i `NOT (expression IS OF (ONLY type))`.  
  
 W poniższej tabeli przedstawiono zachowanie operatora `IS OF` w przypadku niektórych wzorców typowych i narożnych. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:  
  
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
 Poniższe zapytanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używa operatora IS, aby określić typ wyrażenia zapytania, a następnie używa operatora Traktuj do konwersji obiektu typu kursu do kolekcji obiektów typu OnsiteCourse. Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [! code-SQL [DP EntityServices koncepcje # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp EntityServices koncepcji/TSQL/EntitySql. SQL # TREAT_ISOF)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
