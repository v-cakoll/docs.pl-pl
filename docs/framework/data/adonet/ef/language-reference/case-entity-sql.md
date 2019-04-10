---
title: W przypadku (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: e44f48d040fc77bf702759be0c53a618cd84f9fc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334890"
---
# <a name="case-entity-sql"></a>W przypadku (jednostka SQL)
Obliczenie zestawu `Boolean` wyrażenia do obliczenia wyniku.  
  
## <a name="syntax"></a>Składnia  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Jest symbolem zastępczym, która wskazuje, że wiele podczas `Boolean_expression` następnie `result_expression` klauzule można użyć.  
  
 THEN `result_expression`  
 Wyrażenie zwracane, gdy `Boolean_expression` daje w wyniku `true`. `result expression` Jest dowolnym prawidłowym wyrażeniem.  
  
 ELSE `else_result_expression`  
 Wyrażenie zwracane, jeśli żadna operacja porównania nie daje w wyniku `true`. Jeśli ten argument zostanie pominięty, a żadna operacja porównania, które daje w wyniku `true`, przypadek zwraca wartość null. `else_result_expression` Jest dowolnym prawidłowym wyrażeniem. Typy danych `else_result_expression` oraz wszelką `result_expression` musi być taka sama lub musi być niejawną konwersję.  
  
 KIEDY `Boolean_expression`  
 Jest `Boolean` wyrażenia obliczonego stosowania wyszukiwanych format wielkości liter. `Boolean_expression` jest dowolne, prawidłowe `Boolean` wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca typ najwyższy priorytet z zestawu typów w `result_expression` i opcjonalną `else_result_expression`.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Przypomina wyrażenia case [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] zamierzone, Zapisz wyrażenia. Wyrażenie case umożliwia wprowadzając szereg testów warunkowych, aby określić wyrażenie, które umożliwia uzyskanie odpowiednich wyników. Ta forma wyrażenia case dotyczy serii co najmniej jednego `Boolean` wyrażenia, aby określić poprawne wyrażenie wynikowe.  
  
 Funkcja CASE ocenia `Boolean_expression` dla każdej klauzuli WHEN w kolejności określonej, a następnie zwraca `result_expression` pierwszego `Boolean_expression` która daje w wyniku `true`. Pozostałe wyrażenia nie są sprawdzane. Jeśli nie `Boolean_expression` daje w wyniku `true`, aparat bazy danych zwraca `else_result_expression` Jeśli określono klauzulę ELSE, lub wartość null, jeśli określono żadnej klauzuli ELSE.  
  
 CASE — instrukcja nie może zwrócić zestawu wielokrotnego.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto wyrażenia CASE można obliczyć zestawu `Boolean` wyrażenia w celu określenia wyniku. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Zobacz także

- [THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)
- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
