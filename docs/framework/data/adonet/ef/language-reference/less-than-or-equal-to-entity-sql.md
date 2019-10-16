---
title: < = (mniejsze lub równe) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: b3c8fef47b06b9fdd0a1619a9e56d3d916d9dd2d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319635"
---
# <a name="-less-than-or-equal-to-entity-sql"></a>\< = (mniejsze lub równe) (Entity SQL)
Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie ma wartość mniejszą lub równą prawemu wyrażeniu.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.  
  
## <a name="result-types"></a>Typy wyników  
 `true`, jeśli lewe wyrażenie ma wartość mniejszą lub równą prawemu wyrażeniu; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora porównania < = do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie ma wartość mniejszą lub równą prawemu wyrażeniu. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
