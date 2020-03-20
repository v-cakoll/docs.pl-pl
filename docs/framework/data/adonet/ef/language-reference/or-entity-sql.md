---
title: '|| (LUB) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 8c93e68095a0e0ff63532f53152f166d6c3d047c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150096"
---
# <a name="-or-entity-sql"></a>|| (LUB) (Jednostka SQL)
Łączy dwa `Boolean` wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `boolean_expression`  
 Dowolne prawidłowe `Boolean`wyrażenie, które zwraca wyraz .  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`gdy którykolwiek z `true`warunków jest; w `false`przeciwnym razie , .  
  
## <a name="remarks"></a>Uwagi  
 OR jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorem logicznym. Służy do łączenia dwóch warunków. Gdy w instrukcji jest używany więcej niż jeden operator logiczny, operatory OR są oceniane po operatorach AND. Można jednak zmienić kolejność oceny przy użyciu nawiasów.  
  
 Podwójne pionowe pręty (&#124;&#124;) mają taką samą funkcjonalność jak operator OR.  
  
 W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|Prawda|Prawda|Prawda|  
|`FALSE`|Prawda|FAŁSZ|NULL|  
|`NULL`|Prawda|NULL|NULL|  
  
## <a name="example"></a>Przykład  
 Następująca kwerenda SQL jednostki używa `Boolean` operatora OR do łączenia dwóch wyrażeń. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
