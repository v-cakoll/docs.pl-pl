---
title: MIĘDZY (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: cface8ab50e53f21293ad54ea6961c7e308080b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690699"
---
# <a name="between-entity-sql"></a>MIĘDZY (jednostka SQL)
Określa, czy wynikiem wyrażenia wartości w określonym zakresie. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Wyrażenie BETWEEN ma taką samą funkcjonalność jak wyrażenia języka Transact-SQL między.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie do testowania w zakres zdefiniowany przez `begin_expression` i `end_expression`. `expression` musi być taki sam jak zarówno `begin_expression` i `end_expression`.  
  
 `begin_expression`  
 Dowolne prawidłowe wyrażenie. `begin_expression` musi być taki sam jak zarówno `expression` i `end_expression`. `begin_expression` powinna być mniejsza niż `end_expression`, przeciwnym wypadku zwracana wartość będzie ujemna.  
  
 `end_expression`  
 Dowolne prawidłowe wyrażenie. `end_expression` musi być taki sam jak zarówno `expression` i `begin_expression`.  
  
 NIE  
 Określa, że wynik BETWEEN być ujemna.  
  
 AND  
 Działa jako symbol zastępczy, który wskazuje `expression` powinien być z zakresu wskazywanym przez `begin_expression` i `end_expression`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `expression` między zakres wskazywany przez `begin_expression` i `end_expression`; w przeciwnym razie `false`. `null` zostanie zwrócona, jeśli `expression` jest `null` lub jeśli `begin_expression` lub `end_expression` jest `null`.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić zakres wyłączny, użyj większe niż (>) i mniejszości (<) operatory zamiast BETWEEN.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa od operatora w celu określenia, czy wynikiem wyrażenia wartości w określonym zakresie. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
