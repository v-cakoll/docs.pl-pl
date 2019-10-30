---
title: PRZYPADEK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 7c1e02d44c674bf262f92df1c43bec6e9f2143c5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039930"
---
# <a name="case-entity-sql"></a>PRZYPADEK (Entity SQL)
Oblicza zestaw wyrażeń `Boolean`, aby określić wynik.  
  
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
 Jest symbolem zastępczym, który wskazuje, że można używać wielu klauzul `result_expression` `Boolean_expression`.  
  
 NASTĘPNIE `result_expression`  
 Jest wyrażeniem zwracanym, gdy `Boolean_expression` oblicza `true`. `result expression` jest dowolnym prawidłowym wyrażeniem.  
  
 ELSE `else_result_expression`  
 Jest wyrażeniem zwracanym, jeśli żadna operacja porównania nie zostanie obliczona do `true`. Jeśli ten argument zostanie pominięty i żadna operacja porównania nie zostanie obliczona do `true`, przypadek zwraca wartość null. `else_result_expression` jest dowolnym prawidłowym wyrażeniem. Typy danych `else_result_expression` i wszystkie `result_expression` muszą być takie same lub muszą być niejawną konwersją.  
  
 GDY `Boolean_expression`  
 Jest wyrażeniem `Boolean` obliczanym, gdy jest używany przeszukiwany format przypadku. `Boolean_expression` jest dowolnym prawidłowym wyrażeniem `Boolean`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca typ najwyższego pierwszeństwa z zestawu typów w `result_expression` i opcjonalne `else_result_expression`.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie CASE [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przypomina wyrażenie CASE języka Transact-SQL. Wyrażenie CASE służy do tworzenia serii testów warunkowych, aby określić, które wyrażenie zwróci odpowiedni wynik. Ta forma wyrażenia case ma zastosowanie do serii co najmniej jednego wyrażenia `Boolean`, aby określić poprawne wyrażenie wyniku.  
  
 Funkcja CASE oblicza `Boolean_expression` dla każdej klauzuli WHEN w określonej kolejności i zwraca `result_expression` pierwszego `Boolean_expression`, który jest obliczany jako `true`. Pozostałe wyrażenia nie są oceniane. Jeśli żadna `Boolean_expression` nie zostanie obliczona do `true`, aparat bazy danych zwróci `else_result_expression` Jeśli określono klauzulę ELSE lub wartość null, jeśli nie określono klauzuli ELSE.  
  
 Instrukcja CASE nie może zwracać zestawu wielokrotnego.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa wyrażenia CASE do obliczenia zestawu `Boolean` wyrażeń w celu określenia wyniku. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Zobacz także

- [THEN](then-entity-sql.md)
- [SELECT](select-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
