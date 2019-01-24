---
title: TOP (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 6ed20ea372314421e4855b1c1ad761c87bf461b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702564"
---
# <a name="top-entity-sql"></a>TOP (jednostka SQL)
Klauzula SELECT może mieć opcjonalny Podklauzula TOP następujące opcjonalny modyfikator właściwy ALL/DISTINCT. Podklauzula TOP Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Wyrażenie liczbowe, która określa liczbę wierszy do zwrócenia. `n` może to być literał liczbowy jednego lub jeden parametr.  
  
## <a name="remarks"></a>Uwagi  
 Najważniejsze wyrażenie musi być literał liczbowy jednego lub jeden parametr. Jeśli używany jest literałem stałej, typ literału musi być niejawnie Awansowanie do Edm.Int64 (byte, int16, int32 lub int64 lub dowolny typ dostawcy, który mapuje do typu, który jest Awansowanie do Edm.Int64), a jego wartość musi być większa lub równa zero. W przeciwnym razie zostanie wygenerowany wyjątek. Jeśli parametr jest używany jako wyrażenia, typ parametru musi być również niejawnie Awansowanie do Edm.Int64, ale nie będzie nie nastąpi sprawdzanie poprawności wartości rzeczywisty parametr podczas kompilacji ponieważ wartości parametrów opóźnienia jest ograniczone.  
  
 Oto przykład wyrażenie stałe GÓRNY:  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 Oto przykład wyrażenia TOP sparametryzowanego:  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 Górna jest deterministyczna, chyba że zapytania są sortowane. Jeśli potrzebujesz deterministyczne wynik, użyj [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul w [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli. TOP i SKIP/LIMIT wzajemnie się wykluczają.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa u góry określić najważniejsze jeden wiersz ma być zwracany z wyniku zapytania. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a>Zobacz także
- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
