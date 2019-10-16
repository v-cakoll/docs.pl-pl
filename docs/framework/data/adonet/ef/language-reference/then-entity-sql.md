---
title: NASTĘPNIE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: ba01a978c53b58f7e6c1ac9bc42a97277ac64bbc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319283"
---
# <a name="then-entity-sql"></a>NASTĘPNIE (Entity SQL)
Wynik klauzuli WHEN, gdy ma ona wartość `true`.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `when_expression`  
 Dowolne prawidłowe wyrażenie logiczne.  
  
 `then_expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `when_expression` szacuje się na wartość `true`, wynik jest odpowiadającą `then-expression`. Jeśli żaden z warunków nie zostanie spełniony, zostanie obliczona wartość `else-expression`. Jednakże jeśli nie ma `else-expression`, wynik ma wartość null.  
  
 Aby zapoznać się z przykładem, zobacz [wielkość liter](case-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa wyrażenia CASE do obliczenia zestawu wyrażeń `Boolean`. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a>Zobacz także

- [CASE](case-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
