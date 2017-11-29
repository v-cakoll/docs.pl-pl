---
title: "MIĘDZY (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ab5c08dad5f11d968eec4efa51ff225d3cfd0fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="between-entity-sql"></a>MIĘDZY (jednostka SQL)
Określa, czy wyrażenie wynikiem jest wartość w określonym zakresie. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Między wyrażenie ma tę samą funkcję co wyrażenia języka Transact-SQL między.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie do testowania w zakresie zdefiniowane przez `begin_expression` i `end_expression`. `expression`musi być taki sam typ jak zarówno `begin_expression` i `end_expression`.  
  
 `begin_expression`  
 Dowolne prawidłowe wyrażenie. `begin_expression`musi być taki sam typ jak zarówno `expression` i `end_expression`. `begin_expression`powinna być mniejsza niż `end_expression`, else będzie zanegowane wartości zwracanej.  
  
 `end_expression`  
 Dowolne prawidłowe wyrażenie. `end_expression`musi być taki sam typ jak zarówno `expression` i `begin_expression`.  
  
 NIE  
 Określa, czy wynik BETWEEN można zanegowane.  
  
 AND  
 Działa jako symbol zastępczy, który wskazuje `expression` powinien znajdować się w zakresie wskazywanym przez `begin_expression` i `end_expression`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `expression` między zakres wskazywany przez `begin_expression` i `end_expression`; w przeciwnym razie `false`. `null`zostanie zwrócona w przypadku `expression` jest `null` lub, jeśli `begin_expression` lub `end_expression` jest `null`.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić zakres wyłącznego, należy użyć większości (>) i mniejszości (<) operatory zamiast BETWEEN.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa od operatora, aby określić, czy wyrażenie wynikiem jest wartość w określonym zakresie. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
