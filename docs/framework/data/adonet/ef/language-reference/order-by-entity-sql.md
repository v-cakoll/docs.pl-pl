---
title: ORDER BY (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: e691816ec3d0a66c9f43f9a13cffa26b755b3c39
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641780"
---
# <a name="order-by-entity-sql"></a>ORDER BY (jednostka SQL)
Określa porządek sortowania na obiekty zwrócone w instrukcji SELECT.  
  
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
 Dowolne wyrażenie prawidłowe zapytanie, określając właściwość do sortowania. Można określić wiele wyrażeń sortowania. Taką sekwencję wyrażeń sortowania w klauzuli ORDER BY określa organizacji zestawu posortowanego wyników.  
  
 COLLATE {collation_name}  
 Określa, czy można wykonać operacji klauzuli ORDER BY, zgodnie z sortowania określonego w `collation_name`. COLLATE ma zastosowanie tylko w przypadku wyrażenia ciągu.  
  
 ASC  
 Określa, że wartości w określonej właściwości powinny być sortowane w kolejności rosnącej, od wartości najniższej do najwyższej wartości. Domyślnie włączone.  
  
 DESC  
 Określa, że wartości w określonej właściwości powinny być sortowane w kolejności malejącej, z najwyższą wartość do najmniejszej wartości.  
  
 LIMIT `n`  
 Tylko pierwszy `n` zostaną wybrane elementy.  
  
 SKIP `n`  
 Pominie pierwszy `n` elementów.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula ORDER BY logicznie jest stosowany do wyniku klauzuli SELECT. Klauzuli ORDER BY może odwoływać się do elementów na liście wyboru przy użyciu ich aliasów. Klauzula ORDER BY może także odwoływać się inne zmienne, które są obecnie w zakresie. Jednakże jeśli określono klauzuli SELECT DISTINCT modyfikatorem klauzuli ORDER BY może odwoływać się tylko aliasów w klauzuli SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Każde wyrażenie w klauzuli ORDER BY muszą być pewnego typu, który można porównać pod kątem nierówności uporządkowanym, (mniejsze lub większe niż, i tak dalej). Te typy są zazwyczaj skalarną w nim elementów podstawowych, takich jak liczby, ciągi i daty. RowTypes porównywalnych typów są również porównywanie kolejności.  
  
 Jeśli Twój kod wykonuje iterację na uporządkowany zestaw, innego niż projekcji najwyższego poziomu, dane wyjściowe nie gwarantuje jego zamówienia zachowywane są.  
  
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
  
 Aby zostały uporządkowane UNION, UNION ALL, EXCEPT lub INTERSECT operację, należy użyć następującego wzorca:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Ograniczone słów kluczowych  
 Następujące słowa kluczowe muszą być ujęte w znaki cudzysłowu, gdy są używane w `ORDER BY` klauzuli:  
  
- CROSS  
  
- FULL  
  
- KEY  
  
- PO LEWEJ STRONIE  
  
- KOLEJNOŚĆ  
  
- ZEWNĘTRZNE  
  
- PO PRAWEJ STRONIE  
  
- ROW  
  
- WARTOŚĆ  
  
## <a name="ordering-nested-queries"></a>Określanie kolejności zapytań zagnieżdżonej  
 Platformy Entity Framework zagnieżdżone wyrażenie można umieścić w dowolnym miejscu w zapytania. kolejność zapytanie zagnieżdżone nie są zachowywane.  
  
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
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora w klauzuli ORDER BY, aby określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
