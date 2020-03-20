---
title: ZAMÓWIENIE WEDŁUG (ENTITY SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150072"
---
# <a name="order-by-entity-sql"></a>ZAMÓWIENIE WEDŁUG (ENTITY SQL)
Określa kolejność sortowania używaną dla obiektów zwracanych w instrukcji SELECT.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
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
 Dowolne prawidłowe wyrażenie kwerendy określające właściwość, na której ma być sortowane. Można określić wiele wyrażeń sortowania. Sekwencja wyrażeń sortowania w klauzuli ORDER BY definiuje organizację posortowanego zestawu wyników.  
  
 SORTOWANIE {collation_name}  
 Określa, że operacja ORDER BY powinna być wykonywana `collation_name`zgodnie z sortowaniem określonym w . COLLATE ma zastosowanie tylko do wyrażeń ciągu.  
  
 ASC  
 Określa, że wartości w określonej właściwości powinny być sortowane w porządku rosnącym, od najniższej wartości do najwyższej wartości. Domyślnie włączone.  
  
 DESC  
 Określa, że wartości w określonej właściwości powinny być sortowane w porządku malejącym, od najwyższej wartości do najniższej wartości.  
  
 Limit`n`  
 Zostaną wybrane `n` tylko pierwsze elementy.  
  
 Pominąć`n`  
 Pomija pierwsze `n` elementy.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula ORDER BY jest logicznie stosowana do wyniku select klauzuli. Klauzula ORDER BY może odwoływać się do elementów na liście select przy użyciu ich aliasów. Order BY klauzula może również odwoływać się do innych zmiennych, które są obecnie w zakresie. Jednak jeśli SELECT klauzuli został określony z distinct modyfikatora, ORDER BY klauzuli może odwoływać się tylko aliasy z SELECT klauzuli.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Każde wyrażenie w klauzuli ORDER BY musi ocenić do pewnego typu, które można porównać dla uporządkowanej nierówności (mniejszej lub większej niż itd.). Te typy są zazwyczaj skalarne prymitywów, takich jak liczby, ciągi i daty. RowTypes porównywalnych typów są również kolejność porównywalne.  
  
 Jeśli kod iteruje za pomocą uporządkowanego zestawu, innego niż dla projekcji najwyższego poziomu, dane wyjściowe nie jest gwarantowana, aby jego kolejność została zachowana.  

W poniższej próbce kolejność jest gwarantowana do zachowania:

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

W następującej kwerendzie kolejność zagnieżdżonej kwerendy jest ignorowana:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Aby mieć uporządkowaną operację UNION, UNION ALL, EXCEPT lub INTERSECT, użyj następującego wzorca:  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Słowa kluczowe z ograniczeniami  
 Następujące słowa kluczowe muszą być ujęte w `ORDER BY` cudzysłów, gdy są używane w klauzuli:  
  
- Krzyż  
  
- Pełne  
  
- KEY  
  
- LEFT  
  
- Zamówienia  
  
- Zewnętrzne  
  
- RIGHT  
  
- ROW  
  
- WARTOŚĆ  
  
## <a name="ordering-nested-queries"></a>Zamawianie zapytań zagnieżdżonych  
 W ramach encji zagnieżdżone wyrażenie można umieścić w dowolnym miejscu w kwerendzie; kolejność kwerendy zagnieżdżonej nie jest zachowywana.  

Następująca kwerenda zamówi wyniki według nazwiska:  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

W następującej kwerendzie kolejność zagnieżdżonej kwerendy jest ignorowana:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Przykład  
 Następująca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kwerenda używa operatora ORDER BY do określenia kolejności sortowania używanej dla obiektów zwracanych w instrukcji SELECT. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia zapytania](query-expressions-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Pominąć](skip-entity-sql.md)
- [Limit](limit-entity-sql.md)
- [Do góry](top-entity-sql.md)
