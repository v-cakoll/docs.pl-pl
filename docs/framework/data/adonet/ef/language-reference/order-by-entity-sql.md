---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: f3310274766ff3619604e30bfb5f5ca437cb1acd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249752"
---
# <a name="order-by-entity-sql"></a>ORDER BY (Entity SQL)
Określa kolejność sortowania używaną dla obiektów zwracanych w instrukcji SELECT.  
  
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
 Dowolne prawidłowe wyrażenie zapytania określające właściwość, według której ma zostać wykonane sortowanie. Można określić wiele wyrażeń sortowania. Sekwencja wyrażeń sortowania w klauzuli ORDER BY definiuje organizację zestawu wyników sortowania.  
  
 SORTOWANIE {collation_name}  
 Określa, że operacja ORDER BY powinna być wykonywana zgodnie z sortowaniem określonym w `collation_name`elemencie. SORTOWANIE jest stosowane tylko w przypadku wyrażeń ciągów.  
  
 ASC  
 Określa, że wartości w określonej właściwości powinny być sortowane w kolejności rosnącej, od najmniejszej wartości do najwyższej wartości. Domyślnie włączone.  
  
 DESC  
 Określa, że wartości w określonej właściwości powinny być sortowane w kolejności malejącej, od najwyższego do najniższej wartości.  
  
 GRANICE`n`  
 Tylko pierwsze `n` elementy zostaną zaznaczone.  
  
 SKIP `n`  
 Pomija pierwsze `n` elementy.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula ORDER BY jest logicznie stosowana do wyniku klauzuli SELECT. Klauzula ORDER BY może odwoływać się do elementów na liście wyboru przy użyciu ich aliasów. Klauzula ORDER BY może odwoływać się również do innych zmiennych, które są obecnie w zakresie. Jednakże jeśli klauzula SELECT została określona za pomocą modyfikatora DISTINCT, klauzula ORDER BY może odwoływać się tylko do aliasów z klauzuli SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Każde wyrażenie w klauzuli ORDER BY musi być szacowane do pewnego typu, który można porównać w przypadku uporządkowanej nierówności (mniejszej lub większej niż itd.). Te typy są ogólnie skalarnymi typami podstawowymi, takimi jak liczby, ciągi i daty. RowTypes porównywalnych typów są również uporządkowane porównywalnie.  
  
 Jeśli kod wykonuje iterację dla zestawu uporządkowanego, innego niż projekcja najwyższego poziomu, nie ma gwarancji, że jego zamówienie jest zachowywane.  
  
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
  
 Aby mieć przepustą operację UNION, UNION ALL, EXCEPT lub INTERSECT, użyj następującego wzorca:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Zastrzeżone słowa kluczowe  
 Następujące słowa kluczowe muszą być ujęte w znaki cudzysłowu, jeśli `ORDER BY` są używane w klauzuli:  
  
- CROSS  
  
- SZCZEGÓŁOWE  
  
- KEY  
  
- LEWYM  
  
- PORZĄDEK  
  
- BLASK  
  
- KLIKNIJ  
  
- ROW  
  
- WARTOŚCIAMI  
  
## <a name="ordering-nested-queries"></a>Porządkowanie zagnieżdżonych zapytań  
 W Entity Framework wyrażenie zagnieżdżone można umieścić w dowolnym miejscu zapytania; kolejność zagnieżdżonych zapytań nie jest zachowywana.  
  
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
 Poniższe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora order by, aby określić kolejność sortowania używaną dla obiektów zwracanych w instrukcji SELECT. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia zapytania](query-expressions-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [TOP](top-entity-sql.md)
