---
title: ORDER BY (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 5cffd7a696496f92ae83822faff2f08e325eea93
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="order-by-entity-sql"></a>ORDER BY (jednostka SQL)
Określa porządek sortowania używane dla obiektów zwracanych w instrukcji SELECT.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a>Argumenty  
 `order_by_expression`  
 Dowolne wyrażenie prawidłowe zapytanie, określając właściwości do sortowania. Można określić wiele wyrażeń sortowania. Taką sekwencję wyrażeń sortowania w klauzuli ORDER BY definiuje organizacji zestawu wyników posortowane.  
  
 Instrukcji COLLATE {collation_name}  
 Określa, czy można wykonać operacji ORDER BY, zgodnie z Sortowanie określone w `collation_name`. Instrukcji COLLATE ma zastosowanie tylko w przypadku wyrażenia ciągu.  
  
 ASC  
 Określa, że wartości w określonej właściwości mają być sortowane w kolejności rosnącej, od najniższej wartości do największej wartości. Domyślnie włączone.  
  
 DESC  
 Określa, że wartości w określonej właściwości mają być sortowane w kolejności malejącej, z najwyższą wartością najniższą wartość.  
  
 LIMIT `n`  
 Tylko pierwszy `n` zostaną wybrane elementy.  
  
 SKIP `n`  
 Pomija pierwszy `n` elementów.  
  
## <a name="remarks"></a>Uwagi  
 W klauzuli ORDER BY logicznie jest stosowany do wyniku klauzuli SELECT. W klauzuli ORDER BY może odwoływać się elementy na liście wyboru przy użyciu ich aliasów. W klauzuli ORDER BY, można także odwoływać inne zmienne, które są obecnie w zakresie. Jednak jeśli określono w klauzuli SELECT DISTINCT modyfikatorem klauzuli ORDER BY może odwoływać się tylko aliasy w klauzuli SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Każde wyrażenie w klauzuli ORDER BY musi zwrócić pewien typ, który można porównywać pod kątem nierówności uporządkowanych, (mniejsze lub większe niż i tak dalej). Te typy są zazwyczaj skalarne w nim elementów podstawowych, takich jak liczby, ciągi i daty. RowTypes typy można porównywać są również umożliwia porównywanie kolejności.  
  
 Jeśli kod przechodzi przez uporządkowany zestaw, innych niż dla projekcji najwyższego poziomu, dane wyjściowe nie jest gwarantowana mają ich kolejność zachowane.  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Aby mieć uporządkowanej UNION, UNION ALL, EXCEPT lub INTERSECT operację, należy użyć następującego wzorca:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Ograniczone słowa kluczowe  
 Poniższe słowa kluczowe muszą być ujęte w cudzysłów, gdy są używane w `ORDER BY` klauzuli:  
  
-   CROSS  
  
-   PEŁNA  
  
-   KLUCZ  
  
-   PO LEWEJ  
  
-   KOLEJNOŚĆ  
  
-   ZEWNĘTRZNE  
  
-   PRAWO  
  
-   WIERSZ  
  
-   WARTOŚĆ  
  
## <a name="ordering-nested-queries"></a>Porządkowanie zapytania zagnieżdżone  
 W ramach jednostki zagnieżdżone wyrażenia mogą umieszczać w dowolnym miejscu kwerendy; kolejność zapytanie zagnieżdżone nie są zachowywane.  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora ORDER BY, aby określić kolejność sortowania użyć obiektów zwracanych w instrukcji SELECT. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
