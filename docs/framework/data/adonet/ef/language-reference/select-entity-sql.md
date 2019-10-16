---
title: Wybierz (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 4142dca604c0f6dd521f45a8cadd26b9574000f0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319365"
---
# <a name="select-entity-sql"></a>Wybierz (Entity SQL)
Określa elementy zwracane przez zapytanie.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
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
 Dowolne prawidłowe wyrażenie określające liczbę pierwszych wyników do zwrócenia z zapytania, w postaci `top(expr)`.  
  
 Parametr LIMIT operatora [order by](order-by-entity-sql.md) umożliwia również wybranie pierwszych n elementów w zestawie wyników.  
  
 `aliasedExpr`  
 Wyrażenie formularza:  
  
 `expr` jako `identifier` &#124; `expr`  
  
 `expr`  
 Literał lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula SELECT jest obliczana po obliczeniu klauzul [from](from-entity-sql.md), [Group by](group-by-entity-sql.md)i [HAVING](having-entity-sql.md) . Klauzula SELECT może odwoływać się tylko do elementów aktualnie znajdujących się w zakresie (z klauzuli FROM lub z zewnętrznych zakresów). Jeśli określono klauzulę GROUP BY, klauzula SELECT może odwoływać się tylko do aliasów dla kluczy Grupuj według. Odwołania do elementów klauzuli FROM są dozwolone tylko w funkcjach agregujących.  
  
 Lista co najmniej jednego wyrażenia zapytania po słowie kluczowym SELECT jest znana jako lista wyboru lub bardziej formalnie jako projekcja. Najbardziej ogólną formą projekcji jest pojedyncze wyrażenie zapytania. Jeśli wybierzesz element członkowski `member1` z kolekcji `collection1`, utworzysz nową kolekcję wszystkich wartości `member1` dla każdego obiektu w `collection1`, jak pokazano w poniższym przykładzie.  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 Na przykład jeśli `customers` jest kolekcją typu `Customer`, który ma właściwość `Name`, która jest typu `string`, wybranie `Name` z `customers` spowoduje przekazanie kolekcji ciągów, jak pokazano w poniższym przykładzie.  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 Istnieje również możliwość użycia składni JOIN (pełna, wewnętrzna, LEFT, OUTER, ON i RIGHT). WŁĄCZONA jest wymagana dla sprzężeń wewnętrznych i jest to nAby możliwe dla sprzężeń krzyżowych.  
  
## <a name="row-and-value-select-clauses"></a>Klauzule Select z wierszami i wartościami  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje dwie warianty klauzuli SELECT. Pierwszy wariant, wybór wiersza, jest identyfikowany za pomocą słowa kluczowego SELECT i może służyć do określenia co najmniej jednej wartości, która ma zostać wyznaczony. Ponieważ otoka wierszy jest niejawnie dodawana wokół zwracanych wartości, wynik wyrażenia zapytania jest zawsze zestawem wielokrotnym wierszy.  
  
 Każde wyrażenie zapytania w wierszu wybierz musi określać alias. Jeśli alias nie zostanie określony, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować alias przy użyciu reguł generacji aliasów.  
  
 Inny wariant klauzuli SELECT, select value jest identyfikowany za pomocą słowa kluczowego SELECT VALUE. Umożliwia określenie tylko jednej wartości i nie powoduje dodania otoki wiersza.  
  
 Wybór wiersza jest zawsze można wyrazić elementu w zakresie ZAZNACZania wartości, jak pokazano w poniższym przykładzie.  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Modyfikatory All i DISTINCT  
 Oba warianty instrukcji SELECT w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zezwalają na specyfikację modyfikatora ALL lub DISTINCT. Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji utworzonej przez wyrażenie zapytania (do i włącznie z klauzulą SELECT). Jeśli modyfikator ALL jest określony, nie jest wykonywane duplikowanie eliminacji; Jest to wartość domyślna.  
  
## <a name="differences-from-transact-sql"></a>Różnice w języku Transact-SQL  
 W przeciwieństwie do języka Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje użycia argumentu * w klauzuli SELECT.  Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia zapytania do projekcji całych rekordów przez odwołanie się do aliasów kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 Poprzednie wyrażenie zapytania Transact-SQL jest wyrażone w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w następujący sposób.  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora SELECT, aby określić elementy do zwrócenia przez zapytanie. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia zapytania](query-expressions-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [TOP](top-entity-sql.md)
