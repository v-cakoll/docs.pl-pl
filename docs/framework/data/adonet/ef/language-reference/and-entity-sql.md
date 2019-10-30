---
title: '&amp;&amp; (i) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: be6e7120e6c19714f151aa38a8b9a1355de29d1a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039951"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp; (i) (Entity SQL)
Zwraca `true`, jeśli oba wyrażenia są `true`; w przeciwnym razie `false` lub `NULL`.  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
boolean_expression AND boolean_expression
```
 
lub  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `boolean_expression`  
 Dowolne prawidłowe wyrażenie zwracające wartość logiczną.  
  
## <a name="remarks"></a>Uwagi  
 Podwójne znaki "(& &) mają takie same funkcje jak operator i.  
  
 W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|OZNACZA|FAŁSZ|NULL|  
|`FALSE`|FAŁSZ|FAŁSZ|FAŁSZ|  
|`NULL`|NULL|FAŁSZ|NULL|  
  
## <a name="example"></a>Przykład  
 W poniższym zapytaniu Entity SQL pokazano, jak używać operatora i. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
