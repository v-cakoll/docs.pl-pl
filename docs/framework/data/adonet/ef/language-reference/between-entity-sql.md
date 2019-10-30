---
title: MIĘDZY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 611e90f362bbc0eac521e1e1998fb85200169c19
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039948"
---
# <a name="between-entity-sql"></a>MIĘDZY (Entity SQL)
Określa, czy wynikiem wyrażenia jest wartość w określonym zakresie. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] między wyrażeniem ma takie same funkcje jak wyrażenie Transact-SQL między wyrażeniami.  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie do przetestowania w zakresie zdefiniowanym przez `begin_expression` i `end_expression`. `expression` muszą być tego samego typu co `begin_expression` i `end_expression`.  
  
 `begin_expression`  
 Dowolne prawidłowe wyrażenie. `begin_expression` muszą być tego samego typu co `expression` i `end_expression`. `begin_expression` powinna być mniejsza niż `end_expression`, w przeciwnym razie wartość zwracana zostanie Negacja.  
  
 `end_expression`  
 Dowolne prawidłowe wyrażenie. `end_expression` muszą być tego samego typu co `expression` i `begin_expression`.  
  
 NIEMOŻLIWE  
 Określa, że wynik między jest negacją.  
  
 AND  
 Działa jako symbol zastępczy, który wskazuje, `expression` powinien znajdować się w zakresie wskazanym przez `begin_expression` i `end_expression`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`, jeśli `expression` jest między zakresem wskazanym przez `begin_expression` i `end_expression`; w przeciwnym razie `false`. `null` będzie zwracana, jeśli `expression` jest `null` lub jeśli `begin_expression` lub `end_expression` jest `null`.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić zakres wyłącznych, użyj operatorów większe niż (>) i mniejsze niż (<), a nie między.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora, aby określić, czy wynikiem wyrażenia jest wartość w określonym zakresie. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
