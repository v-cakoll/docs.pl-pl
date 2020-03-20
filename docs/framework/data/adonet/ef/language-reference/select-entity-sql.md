---
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: de6c497e7d781d705c68092e4a13ee07b727b2b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149912"
---
# <a name="select-entity-sql"></a>SELECT (Entity SQL)
Określa elementy zwracane przez kwerendę.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Argumenty  
 ALL  
 Określa, że duplikaty mogą pojawiać się w zestawie wyników. ALL jest wartością domyślną.  
  
 DISTINCT  
 Określa, że w zestawie wyników mogą pojawić się tylko unikatowe wyniki.  
  
 WARTOŚĆ  
 Umożliwia określenie tylko jednego elementu i nie dodaje się do otoki wiersza.  
  
 `topSubclause`  
 Każde prawidłowe wyrażenie wskazujące liczbę pierwszych wyników do zwrócenia `top(expr)`z kwerendy formularza .  
  
 Parametr LIMIT operatora [ORDER BY](order-by-entity-sql.md) umożliwia również wybranie pierwszych n elementów w zestawie wyników.  
  
 `aliasedExpr`  
 Wyrażenie formularza:  
  
 `expr`jak `identifier` &#124;`expr`  
  
 `expr`  
 Literał lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula SELECT jest oceniana po ocenie [klauzul FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md)i [HAVING.](having-entity-sql.md) Klauzula SELECT może odwoływać się tylko do elementów aktualnie w zakresie (z klauzuli FROM lub z zakresów zewnętrznych). Jeśli klauzula GROUP BY została określona, klauzula SELECT może odwoływać się tylko do aliasów dla kluczy GROUP BY. Odwoływanie się do elementów klauzuli FROM jest dozwolone tylko w funkcjach zagregowanych.  
  
 Lista co najmniej jednego wyrażenia kwerendy po słowie kluczowym SELECT jest znana jako lista select lub bardziej formalnie jako projekcja. Najbardziej ogólną formą projekcji jest wyrażenie pojedynczego zapytania. Jeśli wybierzesz `member1` element `collection1`członkowski z kolekcji, zostanie `member1` wyprodukowana nowa `collection1`kolekcja wszystkich wartości dla każdego obiektu w , jak pokazano w poniższym przykładzie.  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 Na przykład `customers` jeśli jest kolekcją `Customer` typu, `Name` który ma `string`właściwość, która jest typu, wybierając `Name` z `customers` przyniesie kolekcję ciągów, jak pokazano w poniższym przykładzie.  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 Możliwe jest również użycie składni JOIN (FULL, INNER, LEFT, OUTER, ON i RIGHT). ON jest wymagane dla sprzężeń wewnętrznych i jest nto dozwolone dla sprzężeń krzyżowych.  
  
## <a name="row-and-value-select-clauses"></a>Klauzule wyboru wierszy i wartości  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa warianty klauzuli SELECT. Pierwszy wariant, wybierz wiersz, jest identyfikowany przez select słowa kluczowego i może służyć do określenia jednej lub więcej wartości, które powinny być rzutowane. Ponieważ otoka wiersza jest niejawnie dodawany wokół zwracanych wartości, wynik wyrażenia kwerendy jest zawsze wielokrotny zestaw wierszy.  
  
 Każde wyrażenie kwerendy w wierszu wybierające musi określać alias. Jeśli nie określono aliasu,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować alias przy użyciu reguł generowania aliasu.  
  
 Inny wariant select klauzuli, wartość select, jest identyfikowany przez SELECT VALUE słowa kluczowego. Umożliwia tylko jedną wartość, która ma być określona i nie dodaje otoki wiersza.  
  
 Wybór wiersza jest zawsze wyrażony w kategoriach WARTOŚĆ SELECT, jak pokazano w poniższym przykładzie.  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a>Wszystkie i różne modyfikatory  
 Oba warianty SELECT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwiają specyfikację modyfikatora ALL lub DISTINCT. Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji produkowanej przez wyrażenie kwerendy (do klauzuli SELECT włącznie). Jeśli określono modyfikator ALL, nie jest wykonywana żadna eliminacja duplikatów; ALL jest wartością domyślną.  
  
## <a name="differences-from-transact-sql"></a>Różnice w stosunku do Transact-SQL  
 W przeciwieństwie do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact-SQL, nie obsługuje użycia * argument w SELECT klauzuli.  Zamiast tego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia kwerendom rzutowanie całych rekordów przez odwoływanie się do aliasów kolekcji z klauzuli FROM, jak pokazano w poniższym przykładzie.  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 Poprzednie wyrażenie zapytania Transact-SQL jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażone w następujący sposób.  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Przykład  
 Następująca kwerenda SQL jednostki używa select operatora, aby określić elementy, które mają być zwracane przez kwerendę. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia zapytania](query-expressions-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Do góry](top-entity-sql.md)
