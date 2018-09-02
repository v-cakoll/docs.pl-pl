---
title: ISOF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: dbea0c3a0087c88bf5ffda7b921764b8a0f9f21d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465450"
---
# <a name="isof-entity-sql"></a>ISOF (jednostka SQL)
Określa, czy typ wyrażenia jest określonego typu lub jednego z jego podtypy.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie w celu określenia rodzaju.  
  
 NIE  
 Neguje EDM. Wartość logiczną wyniku jest programu.  
  
 TYLKO  
 Określa, że jest z zwraca `true` tylko wtedy, gdy `expression` typu `type` i nie wszystkie z jedną jego podtypy.  
  
 `type`  
 Typ do przetestowania `expression` względem. Typ musi być kwalifikowana przez obszar nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `expression` jest typu T i T jest typu podstawowego lub typem pochodnym `type`; wartość null, jeśli `expression` jest wartość null w czasie wykonywania; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenia `expression IS NOT OF (type)` i `expression IS NOT OF (ONLY type)` są składniowo równoważne `NOT (expression IS OF (type))` i `NOT (expression IS OF (ONLY type))`, odpowiednio.  
  
 W poniższej tabeli przedstawiono zachowania `IS OF` operatora przez niektóre typowe i rogu wzorce. Wszystkie wyjątki są zgłaszane po stronie klienta, przed wywołaniem pobiera dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|wartość null jest z (typu jednostki)|Zgłasza wyjątek|  
|wartość null jest z (ComplexType)|Zgłasza wyjątek|  
|wartość null jest z (RowType)|Zgłasza wyjątek|  
|TRAKTUJ (wartość null dla obiektu AS) jest typu (EntityType)|Zwraca wartość DBNull|  
|TRAKTUJ (o wartości null ComplexType AS) jest z (ComplexType)|Zgłasza wyjątek|  
|TRAKTUJ (o wartości null RowType AS) jest z (RowType)|Zgłasza wyjątek|  
|Obiekt EntityType jest z typu (jednostki)|Zwraca wartość PRAWDA/FAŁSZ|  
|JEST ComplexType z (ComplexType)|Zgłasza wyjątek|  
|JEST RowType z (RowType)|Zgłasza wyjątek|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora jest OF można określić typu wyrażenia zapytania, a następnie używa operatora TRAKTUJ można przekonwertować obiektu typu kursu do kolekcji obiektów typu OnsiteCourse. Zapytanie jest oparty na [modelu School](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
