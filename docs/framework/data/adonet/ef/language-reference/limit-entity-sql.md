---
title: LIMIT (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 24c5dd3dbe215133de98068be53ad17620ce95c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="limit-entity-sql"></a>LIMIT (jednostka SQL)
Stronicowania fizycznych można przeprowadzić za pomocą Podklauzula LIMIT w klauzuli ORDER BY. LIMIT nie umożliwia oddzielnie od klauzuli ORDER BY.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Liczba elementów, które zostaną wybrane.  
  
 Jeśli LIMIT klauzul podrzędnych wyrażenia znajduje się w klauzuli ORDER BY, zapytanie będzie można sortować według specyfikacji sortowania i wynikowa liczba wierszy zostanie ograniczony przez wyrażenie LIMIT. Na przykład LIMIT 5 ogranicza zestaw wyników do 5 wystąpień lub wierszy. LIMIT jest funkcjonalnym odpowiednikiem TOP z wyjątkiem, że LIMIT wymaga klauzuli ORDER BY obecności. POMIŃ i LIMIT można użyć niezależnie, wraz z klauzuli ORDER BY.  
  
> [!NOTE]
>  Zapytanie Sql jednostki będą uznawane za nieprawidłowe w przypadku GÓRNEGO modyfikator i klauzul podrzędnych SKIP znajduje się w jednym wyrażeniu zapytania. Zapytanie powinno ulegną, zmieniając LIMIT wyrażenie wyrażenia TOP.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora ORDER BY limit, aby określić kolejność sortowania użyć obiektów zwracanych w instrukcji SELECT. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Zobacz też  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Porady: powoduje strony za pomocą kwerendy](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [Stronicowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
