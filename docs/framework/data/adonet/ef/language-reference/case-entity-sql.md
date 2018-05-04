---
title: W przypadku (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: ee878409e7698300b7bebbdac760422013f3b7de
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="case-entity-sql"></a>W przypadku (jednostka SQL)
Ocenia zestaw `Boolean` wyrażeń w celu ustalenia wyniku.  
  
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
 Jest to symbol zastępczy, która wskazuje, że wiele podczas `Boolean_expression` następnie `result_expression` klauzule można użyć.  
  
 NASTĘPNIE `result_expression`  
 Wyrażenie zwracane, gdy `Boolean_expression` daje w wyniku `true`. `result expression` Jest dowolne prawidłowe wyrażenie.  
  
 ELSE `else_result_expression`  
 Wyrażenie zwracane, jeśli żadna operacja porównania nie daje w wyniku `true`. Jeśli ten argument zostanie pominięty i żadna operacja porównania nie daje w wyniku `true`, przypadku zwraca wartość null. `else_result_expression` Jest dowolne prawidłowe wyrażenie. Typy danych `else_result_expression` oraz wszelkie `result_expression` muszą być takie same lub musi być niejawnej konwersji.  
  
 KIEDY `Boolean_expression`  
 Jest `Boolean` wyrażenia obliczonego w przypadku użycia przeszukane formatu wielkość. `Boolean_expression` nadaje się żadnym `Boolean` wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca typ najwyższy priorytet z zestawu typów w `result_expression` oraz opcjonalny `else_result_expression`.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Podobny wyrażenie case [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case wyrażenia. Wyrażenie case umożliwia upewnij serii testów warunkowego, aby określić wyrażenie, które umożliwia uzyskanie odpowiedniego wynik. Ten formularz wyrażenia case dotyczy serii jednego lub więcej `Boolean` wyrażenia, aby określić poprawne wyrażenie wynikowe.  
  
 Funkcja CASE ocenia `Boolean_expression` dla każdej klauzuli WHEN w kolejności określonej i zwraca `result_expression` pierwszego `Boolean_expression` który daje w wyniku `true`. Pozostałe wyrażenia nie są uwzględniane. Jeśli nie `Boolean_expression` daje w wyniku `true`, aparatu bazy danych zwraca `else_result_expression` Jeśli określono klauzulę ELSE, lub wartość null, jeśli nie określono żadnych klauzuli ELSE.  
  
 CASE — instrukcja nie może zwrócić zestawu wielokrotnego.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto wyrażenia CASE można obliczyć zestawu `Boolean` wyrażeń w celu ustalenia wyniku. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Zobacz też  
 [THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
