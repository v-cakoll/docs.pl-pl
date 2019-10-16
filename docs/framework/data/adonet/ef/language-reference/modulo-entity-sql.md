---
title: Operator (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 4bbdbe53403cfec2568cfac320fc7ab1ad2725b0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319603"
---
# <a name="modulo-entity-sql"></a>Operator (Entity SQL)
Zwraca resztę jednego wyrażenia podzieloną przez inny.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a>Argumenty  
 `dividend`  
 Wyrażenie liczbowe do podzielenia. `dividend` jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.  
  
 `divisor`  
 Wyrażenie liczbowe dzielące dywidendę przez. `divisor` jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.  
  
## <a name="result-types"></a>Typy wyników  
 EDM. Int32  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora arytmetycznego% do zwrócenia reszty jednego wyrażenia podzielonego przez inny. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
