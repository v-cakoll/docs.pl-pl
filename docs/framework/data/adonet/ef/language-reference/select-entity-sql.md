---
title: Wybierz (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 3d3564c37d8971d3261cb47acb774bd1b9f92192
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249211"
---
# <a name="select-entity-sql"></a>Wybierz (Entity SQL)
Określa elementy zwracane przez zapytanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Argumenty  
 CAŁĄ  
 Określa, czy duplikaty mogą występować w zestawie wyników. Jest to wartość domyślna.  
  
 ITP  
 Określa, że w zestawie wyników mogą występować tylko unikatowe wyniki.  
  
 WARTOŚCIAMI  
 Zezwala na określenie tylko jednego elementu i nie dodaje go do otoki wiersza.  
  
 `topSubclause`  
 Dowolne prawidłowe wyrażenie określające liczbę pierwszych wyników do zwrócenia z zapytania w formularzu `top(expr)`.  
  
 Parametr LIMIT operatora [order by](order-by-entity-sql.md) umożliwia również wybranie pierwszych n elementów w zestawie wyników.  
  
 `aliasedExpr`  
 Wyrażenie formularza:  
  
 `expr`jako `identifier` &#124;`expr`  
  
 `expr`  
 Literał lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula SELECT jest obliczana po obliczeniu klauzul [from](from-entity-sql.md), [Group by](group-by-entity-sql.md)i [HAVING](having-entity-sql.md) . Klauzula SELECT może odwoływać się tylko do elementów aktualnie znajdujących się w zakresie (z klauzuli FROM lub z zewnętrznych zakresów). Jeśli określono klauzulę GROUP BY, klauzula SELECT może odwoływać się tylko do aliasów dla kluczy Grupuj według. Odwołania do elementów klauzuli FROM są dozwolone tylko w funkcjach agregujących.  
  
 Lista co najmniej jednego wyrażenia zapytania po słowie kluczowym SELECT jest znana jako lista wyboru lub bardziej formalnie jako projekcja. Najbardziej ogólną formą projekcji jest pojedyncze wyrażenie zapytania. Wybranie elementu członkowskiego `member1` z kolekcji `collection1`spowoduje utworzenie `member1` nowej kolekcji wszystkich wartości dla każdego obiektu w `collection1`, jak pokazano w poniższym przykładzie.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Na przykład `customers` jeśli jest kolekcją typu `Customer` , który ma właściwość `Name` typu `string`, wybranie `Name` z `customers` spowoduje przekazanie kolekcji ciągów, jak pokazano w poniższym przykładzie. .  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 Istnieje również możliwość użycia składni JOIN (pełna, wewnętrzna, LEFT, OUTER, ON i RIGHT). WŁĄCZONA jest wymagana dla sprzężeń wewnętrznych i jest to nAby możliwe dla sprzężeń krzyżowych.  
  
## <a name="row-and-value-select-clauses"></a>Klauzule Select z wierszami i wartościami  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa warianty klauzuli SELECT. Pierwszy wariant, wybór wiersza, jest identyfikowany za pomocą słowa kluczowego SELECT i może służyć do określenia co najmniej jednej wartości, która ma zostać wyznaczony. Ponieważ otoka wierszy jest niejawnie dodawana wokół zwracanych wartości, wynik wyrażenia zapytania jest zawsze zestawem wielokrotnym wierszy.  
  
 Każde wyrażenie zapytania w wierszu wybierz musi określać alias. Jeśli alias nie zostanie określony,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] program podejmie próbę wygenerowania aliasu przy użyciu reguł generowania aliasów.  
  
 Inny wariant klauzuli SELECT, select value jest identyfikowany za pomocą słowa kluczowego SELECT VALUE. Umożliwia określenie tylko jednej wartości i nie powoduje dodania otoki wiersza.  
  
 Wybór wiersza jest zawsze można wyrazić elementu w zakresie ZAZNACZania wartości, jak pokazano w poniższym przykładzie.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Modyfikatory All i DISTINCT  
 Oba warianty instrukcji SELECT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w zezwalają na specyfikację modyfikatora All lub DISTINCT. Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji utworzonej przez wyrażenie zapytania (do i włącznie z klauzulą SELECT). Jeśli modyfikator ALL jest określony, nie jest wykonywane duplikowanie eliminacji; Jest to wartość domyślna.  
  
## <a name="differences-from-transact-sql"></a>Różnice w języku Transact-SQL  
 W przeciwieństwie do języka Transact [!INCLUDE[esql](../../../../../../includes/esql-md.md)] -SQL, program nie obsługuje użycia argumentu * w klauzuli select.  Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , program umożliwia zaprojektowanie całych rekordów, odwołując się do aliasów kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.  
  
```  
SELECT * FROM T1, T2  
```  
  
 Poprzednie wyrażenie zapytania Transact-SQL jest wyrażone [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora SELECT, aby określić elementy do zwrócenia przez zapytanie. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia zapytania](query-expressions-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [TOP](top-entity-sql.md)
