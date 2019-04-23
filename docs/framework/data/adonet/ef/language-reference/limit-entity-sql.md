---
title: LIMIT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: b267e97860a2cb071b857224455f01b73115c72d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299699"
---
# <a name="limit-entity-sql"></a>LIMIT (jednostka SQL)
Stronicowanie fizycznych można wykonać przy użyciu Podklauzula LIMIT w klauzuli ORDER BY. OGRANICZENIE nie może służyć oddzielnie od klauzuli ORDER BY.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Liczba elementów, które zostaną wybrane.  
  
 Jeśli LIMIT wyrażenia Podklauzula znajduje się w klauzuli ORDER BY, zapytania będą sortowane według specyfikacji sortowania i wynikowa liczba wierszy, zostanie nałożone przez wyrażenie LIMIT. Na przykład LIMIT 5 ograniczyć zestaw wyników do 5 wystąpień lub wiersze. LIMIT jest funkcjonalnym odpowiednikiem GÓRNEJ z wyjątkiem, że LIMIT wymaga klauzuli ORDER BY być obecne. POMIŃ i LIMIT może służyć niezależnie wraz z klauzuli ORDER BY.  
  
> [!NOTE]
>  Zapytanie Sql jednostki będą uznawane za nieprawidłowe w przypadku najważniejszych modyfikator i POMIŃ Podklauzula znajduje się w jednym wyrażeniu zapytania. Powinien zostać przepisany zapytania, zmieniając wyrażenia TOP i LIMIT wyrażenia.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora klauzuli ORDER BY limit, aby określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Zobacz także

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Instrukcje: Przejrzyj wyniki zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Stronicowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
