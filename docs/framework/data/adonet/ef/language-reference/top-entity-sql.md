---
title: TOP (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 10967ac87fa8f8504dc9a6a29be99401e620085e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="top-entity-sql"></a>TOP (jednostka SQL)
Klauzula SELECT może mieć opcjonalne TOP Podklauzula następujące opcjonalne modyfikator ALL/DISTINCT. Klauzul podrzędnych TOP Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Wyrażenie liczbowe, która określa liczbę wierszy, które mają zostać zwrócone. `n`może to być literał liczbowy jednego lub jeden parametr.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenia TOP musi być jednym literałem lub jeden parametr. Jeśli używana jest literałem stałej, typ literału musi być niejawnie Awansowanie do Edm.Int64 (byte, int16, int32 lub int64 lub dowolnego typu dostawcy, który jest mapowany na typ, który jest Awansowanie do Edm.Int64) i jego wartość musi być większa lub równa zero. W przeciwnym razie zostanie wygenerowany wyjątek. Jeśli parametr jest używany jako wyrażenie, typ parametru musi być również niejawnie Awansowanie do Edm.Int64, ale nie będzie żadnych weryfikację wartości rzeczywisty parametr podczas kompilacji ponieważ wartości parametrów opóźnienia jest ograniczone.  
  
 Poniżej przedstawiono przykład stałe wyrażenie TOP:  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 Poniżej przedstawiono przykład wyrażenia TOP sparametryzowanego:  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 TOP jest deterministyczna, chyba że zapytania są sortowane. Jeśli wymagane jest deterministyczna wyników, należy użyć [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul w [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli. TOP i SKIP/LIMIT wzajemnie się wykluczają.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa góry określić górny jeden wiersz zwrócony z wyniku zapytania. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
