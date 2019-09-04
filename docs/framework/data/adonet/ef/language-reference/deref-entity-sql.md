---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 10c5ecb2b44c85dccd758cc1cf63a152da045cc1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251080"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
Odwołuje się do wartości odniesienia i tworzy wynik tego odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość obiektu, do którego istnieje odwołanie.  
  
## <a name="remarks"></a>Uwagi  
 Operator DEREF odwołuje się do wartości odniesienia i tworzy wynik tego odwołania. Na `r` przykład jeśli jest odwołaniem typu ref `Deref(r)` \<T >, jest wyrażeniem `r`typu `T` , które zwraca jednostkę, do której odwołuje się. Jeśli wartość odwołania ma wartość null lub jest zawieszonego (oznacza to, że obiekt docelowy odwołania nie istnieje), wynik operatora DEREF ma wartość null.  
  
## <a name="example"></a>Przykład  
 Poniższe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora DEREF, aby usunąć odwołanie do wartości odniesienia i utworzyć wynik tego odwołania. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.  
  
2. Przekaż następujące zapytanie jako argument do metody ExecutePrimitiveTypeQuery:  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)
