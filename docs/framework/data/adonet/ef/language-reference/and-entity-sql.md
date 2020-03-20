---
title: '&amp;&amp;(I) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eccad616de287a39c42e986cea84dc22feec7f70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150517"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp;(I) (Jednostka SQL)
Zwraca, `true` jeśli oba `true`wyrażenia są ; w `false` inny `NULL`sposób, lub .  
  
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
 Dowolne prawidłowe wyrażenie, które zwraca wartość logiczną.  
  
## <a name="remarks"></a>Uwagi  
 Podwójne ampersandy (&&) mają taką samą funkcjonalność jak operator AND.  
  
 W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|Prawda|FAŁSZ|NULL|  
|`FALSE`|FAŁSZ|FAŁSZ|FAŁSZ|  
|`NULL`|NULL|FAŁSZ|NULL|  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki pokazuje, jak używać operatora AND. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
