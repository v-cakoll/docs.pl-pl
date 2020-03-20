---
title: MIĘDZY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150496"
---
# <a name="between-entity-sql"></a>MIĘDZY (Entity SQL)
Określa, czy wyrażenie powoduje wartość w określonym zakresie. Wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN ma taką samą funkcjonalność jak wyrażenie Transact-SQL BETWEEN.  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie do `begin_expression` przetestowania w zakresie zdefiniowanym przez i `end_expression`. `expression`musi być tego samego `begin_expression` `end_expression`typu co oba i .  
  
 `begin_expression`  
 Dowolne prawidłowe wyrażenie. `begin_expression`musi być tego samego `expression` `end_expression`typu co oba i . `begin_expression`powinna być `end_expression`mniejsza niż wartość zwracana, w przeciwnym razie wartość zwracana zostanie zanegowana.  
  
 `end_expression`  
 Dowolne prawidłowe wyrażenie. `end_expression`musi być tego samego `expression` `begin_expression`typu co oba i .  
  
 NOT  
 Określa, że wynik BETWEEN zostać zanegowany.  
  
 AND  
 Działa jako symbol zastępczy, który wskazuje, `expression` powinien `begin_expression` `end_expression`mieszcząć się w zakresie wskazanym przez i .  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`jeżeli `expression` znajduje się między `begin_expression` zakresem wskazanym przez i `end_expression`; w `false`przeciwnym razie , . `null`zostanie zwrócona, `null` jeśli `begin_expression` `end_expression` `null` `expression` jest lub jeśli lub jest .  
  
## <a name="remarks"></a>Uwagi  
 Aby określić zakres wyłączności, należy użyć operatorów większych niż (>) i mniejszych niż (<) zamiast between.  
  
## <a name="example"></a>Przykład  
 Następująca kwerenda SQL jednostki używa operatora BETWEEN, aby ustalić, czy wyrażenie powoduje wartość w określonym zakresie. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
