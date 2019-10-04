---
title: Czym język Entity SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e0af0a415d812337d6abf449e9ee170526c3df0c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833721"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Czym język Entity SQL różni się od języka Transact-SQL
W tym temacie opisano różnice między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Obsługa dziedziczenia i relacji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] współpracuje bezpośrednio ze schematami jednostki koncepcyjnej i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.  
  
 Podczas pracy z dziedziczeniem często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu. Ta możliwość zapewnia operator [OfType](oftype-entity-sql.md) w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobnie jak w C# przypadku sekwencji `oftype`).  
  
## <a name="support-for-collections"></a>Obsługa kolekcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traktuje kolekcje jako jednostki pierwszej klasy. Na przykład:  
  
- Wyrażenia kolekcji są prawidłowe w klauzuli `from`.  
  
- `in` i podzapytania `exists` zostały uogólnione w celu umożliwienia dowolnych kolekcji.  
  
     Podzapytanie jest jednym rodzajem kolekcji. `e1 in e2` i `exists(e)` to konstrukcje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do wykonania tych operacji.  
  
- Ustaw operacje, takie jak `union`, `intersect` i `except`, teraz działają na kolekcjach.  
  
- Sprzężenia działają na kolekcjach.  
  
## <a name="support-for-expressions"></a>Obsługa wyrażeń  
 Transact-SQL ma podzapytania (tabele) i wyrażenia (wiersze i kolumny).  
  
 Do obsługi kolekcji i kolekcji zagnieżdżonych, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] czyni wszystko wyrażeniem. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest większa niż Transact-SQL — każde wyrażenie może być używane w dowolnym miejscu. Wyrażenia zapytania zawsze powodują kolekcje typów rzutowanych i mogą być używane wszędzie tam, gdzie wyrażenie kolekcji jest dozwolone. Aby uzyskać informacje o wyrażeniach języka Transact-SQL, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md).  
  
 Wszystkie prawidłowe zapytania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są następujące:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Ujednolicone traktowanie podkwerend  
 Uwzględniając podkreślenie w tabelach, Transact-SQL wykonuje kontekstową interpretację podzapytań. Na przykład podzapytanie w klauzuli `from` jest uznawane za zestaw wielokrotny (tabelę). Ale to samo podzapytanie użyte w klauzuli `select` jest traktowane jako podzapytanie skalarne. Podobnie podzapytanie użyte po lewej stronie operatora `in` jest uznawane za podzapytanie skalarne, podczas gdy po prawej stronie oczekiwana jest podzapytanie zestawu wielokrotnego.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] eliminuje te różnice. Wyrażenie ma jednolitą interpretację, która nie zależy od kontekstu, w którym jest używana. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traktuje wszystkie podzapytania jako podzapytania zestawu wielokrotnego. Jeśli jest wymagana wartość skalarna z podzapytania, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] udostępnia operator `anyelement`, który działa w kolekcji (w tym przypadku podzapytania) i wyodrębnia wartość singleton z kolekcji.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Unikanie niejawnych zarzutów dla podkwerend  
 Powiązane skutki uboczne jednolitego traktowania podzapytań są niejawną konwersją podzapytań na wartości skalarne. W języku Transact-SQL zestaw wielokrotny wierszy (z pojedynczym polem) jest niejawnie konwertowany na wartość skalarną, której typem danych jest pole.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje tego niejawnego przekształcenia. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] udostępnia operatorowi ANYELEMENT, aby wyodrębnić wartość singleton z kolekcji, i klauzulę `select value`, aby uniknąć tworzenia otoki wiersza podczas wyrażenia zapytania.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Wybierz wartość: unikanie niejawnej otoki wiersza  
 Klauzula SELECT w podzapytaniu Transact-SQL niejawnie tworzy otokę wiersza wokół elementów w klauzuli. Oznacza to, że nie możemy utworzyć kolekcji skalarnych lub obiektów. Język Transact-SQL umożliwia niejawne przekształcenie między RowType z jednym polem a wartością singleton tego samego typu danych.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zawiera klauzulę `select value` do pomijania konstrukcji niejawnego wiersza. W klauzuli `select value` można określić tylko jeden element. Gdy taka klauzula jest używana, żadna otoka wiersza nie jest zbudowana wokół elementów w klauzuli `select`, a kolekcja żądanego kształtu może być generowana, na przykład: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] udostępnia także konstruktora wierszy do konstruowania dowolnych wierszy. `select` przyjmuje co najmniej jeden element w projekcji i wyniki w rekordzie danych z polami w następujący sposób:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Lewa korelacja i aliasowanie  
 W języku Transact-SQL wyrażenia w danym zakresie (pojedyncza klauzula, taka jak `select` lub `from`) nie może odwoływać się do wyrażeń zdefiniowanych wcześniej w tym samym zakresie. Niektóre dialekty SQL (w tym Transact-SQL) obsługują ograniczone formy tych w klauzuli `from`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] uogólniuje lewe korelacje w klauzuli `from` i traktuje je równomiernie. Wyrażenia w klauzuli `from` mogą odwoływać się do wcześniejszych definicji (definicje po lewej) w tej samej klauzuli bez potrzeby dodatkowej składni.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nakłada również dodatkowe ograniczenia dotyczące zapytań obejmujących klauzule `group by`. Wyrażenia w klauzuli `select` i klauzula `having` takich zapytań mogą odwoływać się tylko do `group by` kluczy za pomocą ich aliasów. Następująca konstrukcja jest prawidłowa w języku Transact-SQL, ale nie jest w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 W tym celu w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odwoływanie się do kolumn (właściwości) tabel (Kolekcje)  
 Wszystkie odwołania do kolumn w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] muszą być kwalifikowane przy użyciu aliasu tabeli. Następująca konstrukcja (przy założeniu, że `a` jest prawidłową kolumną tabeli `T`) jest prawidłowa w języku Transact-SQL, ale nie w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```sql  
SELECT a FROM T
```  
  
 Formularz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Aliasy tabeli są opcjonalne w klauzuli `from`. Nazwa tabeli jest używana jako alias niejawny. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia również następujące formy:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Nawigacja za poorednictwem obiektów  
 Język Transact-SQL używa notacji "." w celu odwoływania się do kolumn (wierszy) tabeli. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozszerza tę notację (zapożyczone z języków programowania) do obsługi nawigacji za pośrednictwem właściwości obiektu.  
  
 Na przykład jeśli `p` jest wyrażeniem typu Person, poniżej przedstawiono składnię [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do odwoływania się do miasta adresu tej osoby.  
  
```sql  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Brak obsługi dla *  
 Język Transact-SQL obsługuje niekwalifikowaną * składnię jako alias dla całego wiersza oraz kwalifikowaną składnię \* (t. \*) jako skrót dla pól tej tabeli. Ponadto język Transact-SQL zezwala na agregację o specjalnym liczniku (\*), która zawiera wartości null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje konstrukcji *. Zapytania Transact-SQL formularza `select * from T` i `select T1.* from T1, T2...` można wyrazić w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` i `select value t1 from T1 as t1, T2 as t2...`. Ponadto te konstrukcje obsługują dziedziczenie (podstawienie wartości), podczas gdy warianty `select *` są ograniczone do właściwości typu najwyższego poziomu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje agregacji `count(*)`. Zamiast nich należy używać słów kluczowych `count(0)`.  
  
## <a name="changes-to-group-by"></a>Zmiany w grupie według  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje aliasowanie kluczy `group by`. Wyrażenia w klauzuli `select` i klauzuli `having` muszą odwoływać się do `group by` kluczy za pomocą tych aliasów. Na przykład ta składnia [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... jest odpowiednikiem następującego języka Transact-SQL:  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Agregacje oparte na kolekcjach  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje dwa rodzaje agregacji.  
  
 Agregacje oparte na kolekcji działają na kolekcjach i tworzą zagregowany wynik. Mogą one występować w dowolnym miejscu zapytania i nie wymagają `group by` klauzuli. Na przykład:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje również agregacje w stylu SQL. Na przykład:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>Użycie klauzuli ORDER BY  
Język Transact-SQL umożliwia określenie klauzul `ORDER BY` tylko w bloku najwyższego poziomu `SELECT .. FROM .. WHERE`. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można użyć zagnieżdżonego wyrażenia `ORDER BY`, które można umieścić w dowolnym miejscu zapytania, ale porządkowanie w zagnieżdżonych zapytaniach nie jest zachowywane.  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Identyfikatory  
 W języku Transact-SQL porównanie identyfikatorów jest oparte na sortowaniu bieżącej bazy danych. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identyfikatory zawsze uwzględniają wielkość liter i znaki akcentu (oznacza to, że [!INCLUDE[esql](../../../../../../includes/esql-md.md)] różni się od znaków akcentowane i nieakcentowane, na przykład "a" nie jest równe "ấ"). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traktuje wersje liter, które wyglądają tak samo, ale pochodzą z różnych stron kodowych jako różne znaki. Aby uzyskać więcej informacji, zobacz [wejściowy zestaw znaków](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkcja Transact-SQL nie jest dostępna w Entity SQL  
 Poniższe funkcje języka Transact-SQL nie są dostępne w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obecnie nie obsługuje instrukcji DML (INSERT, Update i Delete).  
  
 JĘZYKA  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje języka DDL w bieżącej wersji.  
  
 programowanie imperatywne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje programowania bezwzględnego, w przeciwieństwie do języka Transact-SQL. Zamiast tego użyj języka programowania.  
  
 Funkcje grupowania  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie zapewnia jeszcze obsługi funkcji grupowania (na przykład CUBE, ROLLUP i GROUPING_SET).  
  
 Funkcje analityczne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie (jeszcze) zapewnia obsługę funkcji analitycznych.  
  
 Wbudowane funkcje, operatory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje podzestaw wbudowanych funkcji i operatorów języka Transact-SQL. Te operatory i funkcje mogą być obsługiwane przez dostawców głównych magazynów. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używa funkcji specyficznych dla magazynu zadeklarowanych w manifeście dostawcy. Ponadto Entity Framework umożliwia zadeklarować wbudowane i zdefiniowane przez użytkownika funkcje magazynu dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do użycia.  
  
 Wskazówek  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie oferuje mechanizmów dla wskazówek dotyczących zapytań.  
  
 Wsadowe wyniki zapytania  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje wsadowych wyników zapytania. Na przykład następujące są prawidłowe w języku Transact-SQL (wysyłanie jako partia):  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Jednak odpowiednik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwany:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje tylko jedną instrukcję kwerendy wytwarzającą wynik na polecenie.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md)
