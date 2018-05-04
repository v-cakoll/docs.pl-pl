---
title: ISOF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 7aecb8e2740ffd711278bfd5735c71c2dacf9c3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="isof-entity-sql"></a>ISOF (jednostka SQL)
Określa, czy typ wyrażenia jest określonego typu lub jednego z jego podtypach.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe zapytanie wyrażenie można określić typu.  
  
 NIE  
 Negacja EDM. Wartość logiczna wynik jest programu.  
  
 TYLKO  
 Określa, że jest z zwraca `true` tylko wtedy, gdy `expression` jest typu `type` i nie wszystkie jednego jego podtypach.  
  
 `type`  
 Typ do testowania `expression` przed. Typ musi być kwalifikowana przestrzeni nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `expression` jest typu T i T jest typu podstawowego lub typu pochodnego `type`; wartość null, jeśli `expression` wartości null w czasie wykonywania, a w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenia `expression IS NOT OF (type)` i `expression IS NOT OF (ONLY type)` składniowo odpowiadające `NOT (expression IS OF (type))` i `NOT (expression IS OF (ONLY type))`odpowiednio.  
  
 W poniższej tabeli przedstawiono zachowania `IS OF` operator przez niektóre typowe i rogu wzorce. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem pobiera dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|wartość null jest typu (EntityType)|Zgłasza wyjątek|  
|wartość null jest elementów (ComplexType)|Zgłasza wyjątek|  
|wartość null jest z (RowType)|Zgłasza wyjątek|  
|TRAKTUJ (wartość null dla obiektu AS) jest typu (EntityType)|Zwraca wartość DBNull|  
|TRAKTUJ (null AS ComplexType) jest elementów (ComplexType)|Zgłasza wyjątek|  
|TRAKTUJ (null AS RowType) jest z (RowType)|Zgłasza wyjątek|  
|Obiekt EntityType jest (ENTITYTYPE)|Zwraca wartość true, false|  
|Element ComplexType jest elementów (ComplexType)|Zgłasza wyjątek|  
|JEST RowType z (RowType)|Zgłasza wyjątek|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania korzysta jest OF — operator można określić typu wyrażenia zapytania, a następnie operator TRAKTUJ można przekonwertować obiektu typu kursu do kolekcji obiektów typu OnsiteCourse. Zapytanie jest oparta na [modelu służbowe](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
