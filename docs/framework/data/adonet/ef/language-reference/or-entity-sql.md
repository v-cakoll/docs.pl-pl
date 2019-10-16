---
title: '|| ORAZ (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 6437b17fe1c1277701f06988ef6c02f4caf70e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319467"
---
# <a name="-or-entity-sql"></a>|| ORAZ (Entity SQL)
Łączy dwa wyrażenia `Boolean`.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
boolean_expression OR boolean_expression  
-- or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `boolean_expression`  
 Dowolne prawidłowe wyrażenie zwracające wartość `Boolean`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`, gdy jeden z warunków jest `true`; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 LUB jest operatorem logicznym [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Służy do łączenia dwóch warunków. Gdy w instrukcji użyto więcej niż jednego operatora logicznego, operatory są oceniane po operatorze i. Można jednak zmienić kolejność obliczeń przy użyciu nawiasów.  
  
 Podwójne pionowe słupki&#124;&#124;() mają takie same funkcje jak operator or.  
  
 W poniższej tabeli przedstawiono możliwe wartości wejściowe i typy zwracane.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|OZNACZA|OZNACZA|OZNACZA|  
|`FALSE`|OZNACZA|FAŁSZ|NULL|  
|`NULL`|OZNACZA|NULL|NULL|  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora OR do łączenia dwóch wyrażeń `Boolean`. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
