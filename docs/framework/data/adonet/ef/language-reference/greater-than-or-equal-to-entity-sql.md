---
title: '>= (Większe lub równe) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 9e1d7e92097713ebdaf15523a5f99f98ed8be0b3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833744"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a>> = (większe lub równe) (Entity SQL)
Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie ma wartość większą lub równą prawemu wyrażeniu.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.  
  
## <a name="result-types"></a>Typy wyników  
 `true`, jeśli lewe wyrażenie ma wartość większą lub równą prawemu wyrażeniu; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora porównania > = do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie ma wartość większą lub równą prawemu wyrażeniu. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
