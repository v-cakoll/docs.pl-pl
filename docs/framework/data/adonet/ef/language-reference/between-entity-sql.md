---
title: MIĘDZY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251283"
---
# <a name="between-entity-sql"></a>MIĘDZY (Entity SQL)
Określa, czy wynikiem wyrażenia jest wartość w określonym zakresie. Wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Between ma takie same funkcje jak wyrażenie Transact-SQL między wyrażeniami.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie do przetestowania w zakresie zdefiniowanym `begin_expression` przez `end_expression`i. `expression`musi być tego samego typu co `begin_expression` i. `end_expression`  
  
 `begin_expression`  
 Dowolne prawidłowe wyrażenie. `begin_expression`musi być tego samego typu co `expression` i. `end_expression` `begin_expression`wartość nie może być `end_expression`mniejsza niż, w przeciwnym razie zwracana jest Negacja.  
  
 `end_expression`  
 Dowolne prawidłowe wyrażenie. `end_expression`musi być tego samego typu co `expression` i. `begin_expression`  
  
 NIEMOŻLIWE  
 Określa, że wynik między jest negacją.  
  
 AND  
 Działa jako symbol zastępczy, `expression` który wskazuje, że powinien znajdować `begin_expression` się `end_expression`w zakresie wskazanym przez i.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `expression` jest między zakresem wskazanym `begin_expression` przez `end_expression`i; w `false`przeciwnym razie,. `null`zostanie zwrócona, `expression` Jeśli `null` jest lub `begin_expression` Jeśli `end_expression` lub `null`jest.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić zakres wyłącznych, użyj operatorów większe niż (>) i mniejsze niż (<), a nie między.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora, aby określić, czy wynikiem wyrażenia jest wartość w określonym zakresie. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
