---
title: '! = (Nie równa się) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 3f6f66d38eb9650e1adb06fa3ef5edbccf110374
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319510"
---
# <a name="-not-equal-to-entity-sql"></a>! = (Nie równa się) (Entity SQL)
Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie nie jest równe wyrażeniu z prawej strony. Operator! = (nie równa się) jest funkcjonalnie równoważny operatorowi > <.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.  
  
## <a name="result-types"></a>Typy wyników  
 `true`, jeśli lewe wyrażenie nie jest równe prawidłowemu wyrażeniu; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora! = do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie nie jest równe wyrażeniu z prawej strony. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
