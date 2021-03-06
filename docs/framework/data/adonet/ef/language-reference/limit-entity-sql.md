---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 275b22686c6c932b2a9e4b20973ac07e99d47e14
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319629"
---
# <a name="limit-entity-sql"></a>LIMIT (Entity SQL)
Stronicowanie fizyczne można wykonać za pomocą klauzuli LIMIT w klauzuli ORDER BY. Nie można użyć limitu niezależnie od klauzuli ORDER BY.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Liczba elementów, które zostaną wybrane.  
  
 Jeśli Podklauzula wyrażenia limitu jest obecna w klauzuli ORDER BY, zapytanie zostanie posortowane zgodnie z specyfikacją sortowania, a wynikowa liczba wierszy zostanie ograniczona przez wyrażenie limitu. Na przykład LIMIT 5 ograniczy wynik do 5 wystąpień lub wierszy. LIMIT jest funkcjonalnie równoważny z GÓRNą opcją, ponieważ LIMIT wymaga obecności klauzuli ORDER BY. Nie można używać pominięcia i limitu niezależnie od klauzuli ORDER BY.  
  
> [!NOTE]
> Zapytanie SQL jednostki zostanie uznane za nieprawidłowe, jeśli w tym samym wyrażeniu zapytania występuje modyfikator TOP i SKIP sub. Zapytanie powinno być ponownie zapisywane przez zmianę wyrażenia TOP na wyrażenie OGRANICZAjące.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora ORDER BY z LIMITem, aby określić kolejność sortowania używaną dla obiektów zwracanych w instrukcji SELECT. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LIMIT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#limit)]  
  
## <a name="see-also"></a>Zobacz także

- [ORDER BY](order-by-entity-sql.md)
- [Instrukcje: Strona za poorednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Stronicowanie](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
