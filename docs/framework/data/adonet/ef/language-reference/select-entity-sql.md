---
title: Wybierz (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3123d76d5999d9f7201e1415d6bc4313f9767098
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="select-entity-sql"></a>Wybierz (jednostka SQL)
Określa elementów zwróconych przez kwerendę.  
  
## <a name="syntax"></a>Składnia  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Argumenty  
 WSZYSTKIE  
 Określa, czy duplikaty może występować w zestawie wyników. WSZYSTKO to wartość domyślna.  
  
 RÓŻNE  
 Określa, że wyniki tylko unikatowe może występować w zestawie wyników.  
  
 WARTOŚĆ  
 Zezwala na tylko jeden element, aby określić, a nie dodać otoki wiersza.  
  
 `topSubclause`  
 Prawidłowe wyrażenie, wskazującą liczbę pierwszy wyników do zwrócenia z kwerendy w postaci `top (``expr``)`.  
  
 Parametr limitu [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator umożliwia również wybrać pierwsze n elementów zestawu wyników.  
  
 `aliasedExpr`  
 Wyrażenie w postaci:  
  
 `expr`jako `identifier` &#124;`expr`  
  
 `expr`  
 Literał lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 W klauzuli SELECT jest oceniane po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), i [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) klauzule zostały ocenione. Klauzula SELECT może odwoływać się tylko do elementów aktualnie w zakresie (z klauzuli FROM lub zakresy zewnętrzne). Jeśli określono klauzuli GROUP BY klauzuli SELECT jest dozwolona tylko do odwołania aliasów dla kluczy GROUP BY. Odwołania do elementów Klauzula FROM jest dozwolony tylko w funkcjach agregujących.  
  
 Lista po słowie kluczowym wybierz co najmniej jednego wyrażenia zapytania jest znany jako lista wyboru lub więcej formalnie projekcji. Najbardziej ogólnym postaci projekcji to wyrażenie pojedynczego zapytania. W przypadku wybrania członka `member1` z kolekcji `collection1`, utworzy nową kolekcję wszystkich `member1` wartości dla każdego obiektu w `collection1`, jak pokazano w poniższym przykładzie.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Na przykład jeśli `customers` jest kolekcją typu `Customer` mający właściwość `Name` jest typu `string`, wybierając żądane `Name` z `customers` umożliwia uzyskanie kolekcji ciągów, jak pokazano w poniższym przykładzie .  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 Istnieje również możliwość użycia składni klauzuli JOIN (FULL, wewnętrzny, po lewej, zewnętrzne, ON i po prawej). ON jest wymagana do sprzężenia wewnętrzne i jest nAby dozwolone w przypadku wielu sprzężenia.  
  
## <a name="row-and-value-select-clauses"></a>Wiersz i wartość klauzule Select  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa rodzaje klauzuli SELECT. Pierwszy variant, wybierz wiersz, jest identyfikowany przez wybierz — słowo kluczowe i może służyć do określenia jednego lub więcej wartości, które należy utworzyć projekcji limit. Wynik wyrażenia zapytania, ponieważ otoki wiersza jest niejawnie dodane wokół wartości zwracane, jest zawsze multiset wierszy.  
  
 Każde wyrażenie zapytania w klauzuli select wiersz należy określić alias. Jeśli jest określony żaden alias[!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować za pomocą reguł generowania aliasu alias.  
  
 Wariant klauzuli SELECT, wybierz wartość jest identyfikowany przez SELECT VALUE — słowo kluczowe. Zezwala na tylko jedną wartość, należy określić i dodaje otoki wiersza.  
  
 Wybierz wiersz jest zawsze można wyrazić pod względem wartości wybierz, jak pokazano w poniższym przykładzie.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Wszystkie i różne modyfikatorów  
 Oba rodzaje wybierz w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zezwalaj specyfikację ALL lub modyfikator DISTINCT. Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji utworzonej przez wyrażenie kwerendy (, w tym klauzula SELECT). Jeśli wszystkie modyfikator jest określony, nie zduplikowane eliminacji jest wykonywane; WSZYSTKO to wartość domyślna.  
  
## <a name="differences-from-transact-sql"></a>Różnice języka Transact-SQL  
 W przeciwieństwie do języka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje użycia * argument w klauzuli SELECT.  Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia kwerendy projektu limit całych rekordów odwołując aliasy kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.  
  
```  
SELECT * FROM T1, T2  
```  
  
 Poprzedni [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażenie kwerendy jest wyrażona w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto operatora SELECT do określenia elementy będą zwracane przez zapytanie. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia zapytań](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [DO GÓRY](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
