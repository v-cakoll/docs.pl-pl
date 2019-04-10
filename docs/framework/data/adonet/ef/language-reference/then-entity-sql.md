---
title: A następnie (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 8d2d7f9a3a1d6ff9f25db3f19bf8f39781469f9f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305627"
---
# <a name="then-entity-sql"></a>A następnie (jednostka SQL)
Wynik w klauzuli WHEN, gdy daje w wyniku `true`.  
  
## <a name="syntax"></a>Składnia  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `when_expression`  
 Dowolne prawidłowe wyrażenie logiczne.  
  
 `then_expression`  
 Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `when_expression` daje w wyniku wartość `true`, wynik jest odpowiedni `then-expression`. Jeśli żaden z po spełnieniu warunków `else-expression` jest oceniany. Jednak w przypadku nie `else-expression`, wynikiem jest wartość null.  
  
 Aby uzyskać przykład, zobacz [przypadek](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto wyrażenia CASE można obliczyć zestawu `Boolean` wyrażenia. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Zobacz także

- [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
