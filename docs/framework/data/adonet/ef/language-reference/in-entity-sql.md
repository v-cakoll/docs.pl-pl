---
title: W (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: e46db63600b6baa03697615a2f5eb9240f55d15e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833694"
---
# <a name="in-entity-sql"></a>W (Entity SQL)
Określa, czy wartość jest zgodna z dowolną wartością w kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `value`  
 Dowolne prawidłowe wyrażenie zwracające wartość do dopasowania.  
  
 NIEMOŻLIWE  
 Określa, że wynik `Boolean` jest negacji.  
  
 `expression`  
 Dowolne prawidłowe wyrażenie zwracające kolekcję do przetestowania w celu dopasowania. Wszystkie wyrażenia muszą być tego samego typu lub wspólnego typu podstawowego lub pochodnego jako `value`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`, jeśli wartość zostanie znaleziona w kolekcji; wartość null, jeśli wartość jest równa null lub kolekcja ma wartość null; w przeciwnym razie `false`. Użycie nie jest w wyniku negacji wyników w.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora IN, aby określić, czy wartość pasuje do dowolnej wartości w kolekcji. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
