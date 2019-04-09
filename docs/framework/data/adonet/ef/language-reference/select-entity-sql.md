---
title: Wybierz (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: f5bc3b795eb20551abda2104c2f399c8da10a962
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136022"
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
 ALL  
 Określa, czy duplikaty może znajdować się w zestawie wyników. WSZYSTKO jest ustawieniem domyślnym.  
  
 DISTINCT  
 Określa, że tylko unikatowe wyniki może znajdować się w zestawie wyników.  
  
 WARTOŚĆ  
 Zezwala na tylko jeden element ma być określony i nie powoduje dodania na otokę wiersza.  
  
 `topSubclause`  
 Dowolne prawidłowe wyrażenie, wskazującą liczbę pierwszych wyników do zwrócenia z zapytania w postaci `top(expr)`.  
  
 Parametr limitu [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator umożliwia także wybrać pierwsze n elementów zestawu wyników.  
  
 `aliasedExpr`  
 Wyrażenie formularza:  
  
 `expr` as `identifier` &#124; `expr`  
  
 `expr`  
 Literał lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula SELECT jest oceniane po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), i [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) klauzule zostały ocenione. Klauzula SELECT może odwoływać się tylko do elementów aktualnie w zakresie (z klauzuli FROM lub zakresy zewnętrznych). Jeśli określono klauzuli GROUP BY w klauzuli SELECT jest dozwolona tylko k odkazu aliasów dla kluczy GROUP BY. Odwołania do elementów Klauzula FROM jest dozwolona tylko w funkcjach agregujących.  
  
 Listę po słowie kluczowym wybierz co najmniej jednego wyrażenia kwerendy jest określany jako listy wyboru lub bardziej formalnie projekcji. Najbardziej ogólną postaci projekcji jest wyrażeniem pojedynczego zapytania. Jeśli wybierzesz członka `member1` z kolekcji `collection1`, generuje nowy zbiór wszystkich `member1` wartości dla każdego obiektu w `collection1`, jak pokazano w poniższym przykładzie.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Na przykład jeśli `customers` jest kolekcją typów `Customer` zawierający właściwości `Name` jest typu `string`, wybierając opcję `Name` z `customers` przyniesie to zbiór ciągów, jak pokazano w poniższym przykładzie .  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 Użytkownik może również użyć składni klauzuli JOIN (pełnej, wewnętrzne, po lewej stronie, zewnętrzne, ON i po prawej stronie). ON jest wymagana dla sprzężenia wewnętrzne i jest nAby dozwolone w przypadku wielu sprzężenia.  
  
## <a name="row-and-value-select-clauses"></a>Wiersz i klauzule wybierz wartość  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje dwa warianty klauzuli SELECT. Pierwszy typ variant, wybierz wiersz jest identyfikowane za pomocą słowa kluczowego wybierz i może służyć do określenia co najmniej jednej wartości, które powinien być przekazywany się. Wynik wyrażenia zapytania, ponieważ wokół wartości zwracanych niejawnie dodaniu otoki wiersza jest zawsze multiset wierszy.  
  
 Każde wyrażenie zapytania, wybierz wiersz w należy określić alias. Jeśli brak aliasu jest określony,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje go wygenerować aliasem, za pomocą reguł generowania aliasu.  
  
 Wariant klauzuli SELECT, wybierz wartość, jest identyfikowany przez SELECT VALUE — słowo kluczowe. Umożliwia ona tylko jedną wartość, należy określić i nie powoduje dodania otoki wiersza.  
  
 Wybierz wiersz jest zawsze można wyrazić pod względem wybierz wartości, jak pokazano w poniższym przykładzie.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Wszystkie i różne modyfikatorów  
 Oba warianty wybór w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] specyfikacji wszystkie lub modyfikator DISTINCT. Jeśli modyfikator DISTINCT jest określony, duplikaty są eliminowane z kolekcji, generowane przez wyrażenie zapytania (, w tym klauzula SELECT). Jeśli wszystkie modyfikator jest określony, nie zduplikowane odbywa się eliminacji; WSZYSTKO jest ustawieniem domyślnym.  
  
## <a name="differences-from-transact-sql"></a>Różnice w języku Transact-SQL  
 W przeciwieństwie do języka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje korzystanie z * argument w klauzuli SELECT.  Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia zapytania do projektu się całych rekordów, odwołując się do aliasów kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.  
  
```  
SELECT * FROM T1, T2  
```  
  
 Poprzedni [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażenie kwerendy jest będzie wyrażana [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa wybierz operator, określić elementy, które mają zostać zwrócone przez zapytanie. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia kwerend](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
