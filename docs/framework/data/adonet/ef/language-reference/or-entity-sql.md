---
title: '|| ORAZ (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: c88e041638fbe6f32717ce9c4f9c2ff6fb56d803
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249774"
---
# <a name="-or-entity-sql"></a>|| ORAZ (Entity SQL)
Łączy dwa `Boolean` wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `boolean_expression`  
 Dowolne prawidłowe wyrażenie zwracające `Boolean`wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`gdy jeden z warunków jest `true`; w przeciwnym razie,. `false`  
  
## <a name="remarks"></a>Uwagi  
 Or jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorem logicznym. Służy do łączenia dwóch warunków. Gdy w instrukcji użyto więcej niż jednego operatora logicznego, operatory są oceniane po operatorze i. Można jednak zmienić kolejność obliczeń przy użyciu nawiasów.  
  
 Podwójne pionowe słupki&#124;&#124;() mają takie same funkcje jak operator or.  
  
 W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|OZNACZA|OZNACZA|OZNACZA|  
|`FALSE`|OZNACZA|FAŁSZ|NULL|  
|`NULL`|OZNACZA|NULL|NULL|  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora OR do łączenia dwóch `Boolean` wyrażeń. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
