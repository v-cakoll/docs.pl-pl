---
title: PRZYPADEK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 79544f4180313a008669c56c4f2740c889043c6d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251252"
---
# <a name="case-entity-sql"></a>PRZYPADEK (Entity SQL)
Oblicza zestaw `Boolean` wyrażeń, aby określić wynik.  
  
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
 Jest symbolem zastępczym, który wskazuje `Boolean_expression` , `result_expression` że można użyć wielu klauzule then.  
  
 NASTĘPNIE`result_expression`  
 Jest wyrażeniem zwracanym `Boolean_expression` podczas obliczania. `true` `result expression`jest dowolnym prawidłowym wyrażeniem.  
  
 ELSE `else_result_expression`  
 Jest wyrażeniem zwracanym, jeśli nie zostanie obliczona `true`żadna operacja porównania. Jeśli ten argument zostanie pominięty i żadna operacja porównania nie zostanie obliczona do `true`, przypadek zwraca wartość null. `else_result_expression`jest dowolnym prawidłowym wyrażeniem. Typy `else_result_expression` danych i any `result_expression` muszą być takie same lub muszą być niejawną konwersją.  
  
 CZASIE`Boolean_expression`  
 `Boolean` Jest wyrażeniem obliczanym, gdy jest używany przeszukiwany format wielkości liter. `Boolean_expression`jest dowolnym prawidłowym `Boolean` wyrażeniem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca typ najwyższego pierwszeństwa z zestawu typów w `result_expression` i opcjonalne. `else_result_expression`  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Case przypomina wyrażenie CASE języka Transact-SQL. Wyrażenie CASE służy do tworzenia serii testów warunkowych, aby określić, które wyrażenie zwróci odpowiedni wynik. Ta forma wyrażenia case ma zastosowanie do serii co najmniej jednego `Boolean` wyrażenia, aby określić poprawne wyrażenie wyniku.  
  
 Funkcja Case oblicza `Boolean_expression` dla każdej klauzuli when w określonej kolejności i zwraca `result_expression` `true`pierwszy `Boolean_expression` , który jest obliczany. Pozostałe wyrażenia nie są oceniane. Jeśli żaden `Boolean_expression` z `true`nich nie jest wynikiem, aparat bazy danych `else_result_expression` zwraca wartość, jeśli określono klauzulę else lub wartość null, jeśli nie określono klauzuli else.  
  
 Instrukcja CASE nie może zwracać zestawu wielokrotnego.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa wyrażenia case do obliczenia zestawu `Boolean` wyrażeń w celu określenia wyniku. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.  
  
2. Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Zobacz także

- [THEN](then-entity-sql.md)
- [SELECT](select-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
