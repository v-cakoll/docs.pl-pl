---
title: PRZYPADEK (ENTITY SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58b21d3be8e13a0a2204a4fd6d355f734207c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150470"
---
# <a name="case-entity-sql"></a>PRZYPADEK (ENTITY SQL)
Ocenia zestaw `Boolean` wyrażeń w celu określenia wyniku.  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
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
 Jest symbolem zastępczym, który `Boolean_expression` wskazuje, że można użyć wielu klauzul WHEN THEN. `result_expression`  
  
 Następnie`result_expression`  
 Czy wyrażenie jest `Boolean_expression` zwracane `true`po dodaniu . `result expression`jest dowolnym prawidłowym wyrażeniem.  
  
 Innego`else_result_expression`  
 Czy wyrażenie jest zwracane, jeśli `true`żadna operacja porównania nie ma oceny . Jeśli ten argument zostanie pominięty i `true`żadna operacja porównania nie ma do tej wartości , case zwraca wartość null. `else_result_expression`jest dowolnym prawidłowym wyrażeniem. Typy danych `else_result_expression` i `result_expression` wszelkie muszą być takie same lub musi być niejawna konwersja.  
  
 Kiedy`Boolean_expression`  
 Czy `Boolean` wyrażenie jest oceniane podczas wyszukiwania formatu CASE jest używany. `Boolean_expression`jest dowolnym `Boolean` prawidłowym wyrażeniem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca najwyższy typ pierwszeństwa z zestawu `result_expression` typów w `else_result_expression`i opcjonalnym .  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sprawy przypomina wyrażenie przypadku Transact-SQL. Wyrażenie przypadku służy do wykonania serii testów warunkowych w celu określenia, które wyrażenie przyniesie odpowiedni wynik. Ta forma wyrażenia case ma zastosowanie do serii `Boolean` jednego lub więcej wyrażeń w celu określenia poprawnego wyrażenia wynikowego.  
  
 Funkcja CASE ocenia `Boolean_expression` dla każdej klauzuli WHEN w `result_expression` określonej `Boolean_expression` kolejności i `true`zwraca pierwszą, która ocenia . Pozostałe wyrażenia nie są oceniane. Jeśli `Boolean_expression` nie ma `true`żadnych obliczeń, `else_result_expression` Aparat baz danych zwraca, jeśli else klauzuli jest określony lub wartość null, jeśli nie else klauzuli jest określony.  
  
 Instrukcja CASE nie może zwrócić zestawu wielokrotnego.  
  
## <a name="example"></a>Przykład  
 Następująca kwerenda SQL jednostki używa wyrażenia `Boolean` CASE do oceny zestawu wyrażeń w celu określenia wyniku. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak wykonać kwerendę, która zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecutePrimitiveTypeQuery` argument do metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Zobacz też

- [Następnie](then-entity-sql.md)
- [Wybierz](select-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
