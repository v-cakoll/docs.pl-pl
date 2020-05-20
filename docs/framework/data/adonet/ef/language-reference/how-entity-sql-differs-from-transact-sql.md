---
title: Czym język Entity SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 96e2283074b6c69e51bb7fee4d4f257cdb58d615
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615634"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Jak Entity SQL różni się od języka Transact-SQL

W tym artykule opisano różnice między Entity SQL i Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Obsługa dziedziczenia i relacji  
 Entity SQL działa bezpośrednio ze schematami jednostki koncepcyjnej i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.  
  
 Podczas pracy z dziedziczeniem często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu. Ta możliwość zapewnia operator [OfType](oftype-entity-sql.md) w Entity SQL (podobnie jak `oftype` w sekwencjach C#).  
  
## <a name="support-for-collections"></a>Obsługa kolekcji  
 Entity SQL traktuje kolekcje jako jednostki pierwszej klasy. Na przykład:  
  
- Wyrażenia kolekcji są prawidłowe w `from` klauzuli.  
  
- `in`i `exists` podzapytania zostały uogólnione w celu zezwolenia na jakiekolwiek kolekcje.  
  
     Podzapytanie jest jednym rodzajem kolekcji. `e1 in e2`i `exists(e)` są konstrukcjami Entity SQL do wykonywania tych operacji.  
  
- Ustaw operacje, takie jak `union` , `intersect` , i `except` teraz działają na kolekcjach.  
  
- Sprzężenia działają na kolekcjach.  
  
## <a name="support-for-expressions"></a>Obsługa wyrażeń  
 Transact-SQL ma podzapytania (tabele) i wyrażenia (wiersze i kolumny).  
  
 Aby zapewnić obsługę kolekcji i kolekcji zagnieżdżonych, Entity SQL wykonuje wszystkie wyrażenia. Entity SQL jest większa niż Transact-SQL — każde wyrażenie może być używane w dowolnym miejscu. Wyrażenia zapytania zawsze powodują kolekcje typów rzutowanych i mogą być używane wszędzie tam, gdzie wyrażenie kolekcji jest dozwolone. Aby uzyskać informacje o wyrażeniach języka Transact-SQL, które nie są obsługiwane w Entity SQL, zobacz [nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md).  
  
 Wszystkie prawidłowe kwerendy Entity SQL są następujące:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Ujednolicone traktowanie podkwerend  
 Uwzględniając podkreślenie w tabelach, Transact-SQL wykonuje kontekstową interpretację podzapytań. Na przykład podzapytanie w `from` klauzuli jest uznawane za zestaw wielokrotny (tabelę). Ale to samo podzapytanie użyte w `select` klauzuli jest uznawane za podzapytanie skalarne. Podobnie podzapytanie użyte po lewej stronie `in` operatora jest uznawane za podzapytanie skalarne, podczas gdy po prawej stronie oczekiwana jest podzapytanie zestawu wielokrotnego.  
  
 Entity SQL eliminuje te różnice. Wyrażenie ma jednolitą interpretację, która nie zależy od kontekstu, w którym jest używana. Entity SQL traktuje wszystkie podzapytania jako podzapytania zestawu wielokrotnego. Jeśli jest wymagana wartość skalarna z podzapytania, Entity SQL udostępnia `anyelement` operator, który działa w kolekcji (w tym przypadku podzapytania) i wyodrębnia wartość singleton z kolekcji.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Unikanie niejawnych zarzutów dla podkwerend  
 Powiązane skutki uboczne jednolitego traktowania podzapytań są niejawną konwersją podzapytań na wartości skalarne. W języku Transact-SQL zestaw wielokrotny wierszy (z pojedynczym polem) jest niejawnie konwertowany na wartość skalarną, której typem danych jest pole.  
  
 Entity SQL nie obsługuje tego niejawnego przekształcenia. Entity SQL zapewnia `ANYELEMENT` operatorowi wyodrębnienie wartości pojedynczej z kolekcji oraz `select value` klauzulę, aby uniknąć tworzenia otoki wiersza podczas wyrażenia zapytania.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Wybierz wartość: unikanie niejawnej otoki wiersza  
 Klauzula SELECT w podzapytaniu Transact-SQL niejawnie tworzy otokę wiersza wokół elementów w klauzuli. Oznacza to, że nie możemy utworzyć kolekcji skalarnych lub obiektów. Język Transact-SQL umożliwia niejawne przekształcenie między wartością `rowtype` z jednego pola a wartością singleton tego samego typu danych.  
  
 Entity SQL udostępnia `select value` klauzulę do pomijania konstrukcji niejawnego wiersza. W klauzuli może być określony tylko jeden element `select value` . Gdy taka klauzula jest używana, żadna otoka wiersza nie jest zbudowana wokół elementów w `select` klauzuli i można utworzyć kolekcję żądanego kształtu, na przykład `select value a` .  
  
 Entity SQL udostępnia także konstruktora wierszy do konstruowania dowolnych wierszy. `select`przyjmuje co najmniej jeden element w projekcji i wyniki w rekordzie danych z polami:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Lewa korelacja i aliasowanie  
 W języku Transact-SQL wyrażenia w danym zakresie (pojedyncza klauzula LIKE `select` lub `from` ) nie mogą odwoływać się do wyrażeń zdefiniowanych wcześniej w tym samym zakresie. Niektóre dialekty SQL (w tym Transact-SQL) obsługują ograniczone formy tych w `from` klauzuli.  
  
 Entity SQL uogólnia lewe korelacje w `from` klauzuli i traktuje je równomiernie. Wyrażenia w `from` klauzuli mogą odwoływać się do wcześniejszych definicji (definicje po lewej) w tej samej klauzuli bez potrzeby dodatkowej składni.  
  
 Entity SQL również nakłada dodatkowe ograniczenia dotyczące zapytań obejmujących `group by` klauzule. Wyrażenia w `select` klauzuli i `having` klauzuli takich zapytań mogą odwoływać się tylko do `group by` kluczy za pośrednictwem ich aliasów. Następująca konstrukcja jest prawidłowa w języku Transact-SQL, ale nie znajduje się w Entity SQL:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 W tym celu w Entity SQL:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odwoływanie się do kolumn (właściwości) tabel (Kolekcje)  
 Wszystkie odwołania do kolumn w Entity SQL muszą być kwalifikowane z aliasem tabeli. Następująca konstrukcja (przy założeniu, że `a` jest to prawidłowa kolumna tabeli `T` ) jest prawidłowa w języku Transact-SQL, ale nie w Entity SQL.  
  
```sql  
SELECT a FROM T
```  
  
 Formularz Entity SQL jest  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Aliasy tabeli są opcjonalne w `from` klauzuli. Nazwa tabeli jest używana jako alias niejawny. Entity SQL również zezwala na następujący formularz:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Nawigacja za poorednictwem obiektów  
 Język Transact-SQL używa notacji "." w celu odwoływania się do kolumn (wierszy) tabeli. Entity SQL rozszerza tę notację (zapożyczone z języków programowania) do obsługi nawigacji za pośrednictwem właściwości obiektu.  
  
 Na przykład jeśli `p` jest wyrażeniem typu Person, poniżej przedstawiono składnię Entity SQL do odwoływania się do miasta adresu tej osoby.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>Brak obsługi dla\*  
 Język Transact-SQL obsługuje niekwalifikowaną \* składnię jako alias dla całego wiersza oraz kwalifikowaną \* składnią (t. \* ) jako skrót dla pól tej tabeli. Ponadto język Transact-SQL zezwala na \* agregację specjalna (), która zawiera wartości null.  
  
 Entity SQL nie obsługuje konstrukcji *. Zapytania Transact-SQL formularza `select * from T` i `select T1.* from T1, T2...` mogą być wyrażone w Entity SQL `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...` odpowiednio i. Ponadto te konstrukcje obsługują dziedziczenie (podstawienie wartości), podczas gdy `select *` warianty są ograniczone do właściwości najwyższego poziomu zadeklarowanego typu.  
  
 Entity SQL nie obsługuje `count(*)` agregacji. Zamiast tego użyj polecenia cmdlet `count(0)`.  
  
## <a name="changes-to-group-by"></a>Zmiany w grupie według  
 Entity SQL obsługuje aliasowanie `group by` kluczy. Wyrażenia w `select` klauzuli i `having` klauzuli muszą odwoływać się do `group by` kluczy za pośrednictwem tych aliasów. Na przykład następująca składnia Entity SQL:  
  
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
 Entity SQL obsługuje dwa rodzaje agregacji.  
  
 Agregacje oparte na kolekcji działają na kolekcjach i tworzą zagregowany wynik. Mogą one występować w dowolnym miejscu zapytania i nie wymagają `group by` klauzuli. Na przykład:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 Entity SQL obsługuje również agregacje w stylu SQL. Na przykład:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>Użycie klauzuli ORDER BY  
Język Transact-SQL zezwala `ORDER BY` na określenie klauzul tylko w bloku najwyższego poziomu `SELECT .. FROM .. WHERE` . W Entity SQL można użyć wyrażenia zagnieżdżonego, które `ORDER BY` można umieścić w dowolnym miejscu zapytania, ale porządkowanie w zagnieżdżonych zapytaniach nie jest zachowywane.  
  
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
 W języku Transact-SQL porównanie identyfikatorów jest oparte na sortowaniu bieżącej bazy danych. W Entity SQL w identyfikatorach zawsze jest rozróżniana wielkość liter i znaki akcentu (oznacza to, że Entity SQL rozróżnia znaków akcentowane i nieakcentowane, na przykład "a" nie jest równe "ấ"). Entity SQL traktuje wersje liter, które wyglądają tak samo, ale pochodzą z różnych stron kodowych jako różne znaki. Aby uzyskać więcej informacji, zobacz [wejściowy zestaw znaków](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkcja Transact-SQL nie jest dostępna w Entity SQL  
 Poniższe funkcje języka Transact-SQL nie są dostępne w Entity SQL.  
  
 DML  
 Entity SQL obecnie nie obsługuje instrukcji DML (INSERT, Update i Delete).  
  
 JĘZYKA  
 Entity SQL nie obsługuje języka DDL w bieżącej wersji.  
  
 programowanie imperatywne  
 Entity SQL nie zapewnia obsługi bezwzględnego programowania, w przeciwieństwie do języka Transact-SQL. Zamiast tego użyj języka programowania.  
  
 Funkcje grupowania  
 Entity SQL nie zapewnia jeszcze obsługi funkcji grupowania (na przykład CUBE, ROLLUP i GROUPING_SET).  
  
 Funkcje analityczne  
 Entity SQL nie (jeszcze) zapewnia obsługę funkcji analitycznych.  
  
 Wbudowane funkcje, operatory  
 Entity SQL obsługuje podzestaw wbudowanych funkcji i operatorów języka Transact-SQL. Te operatory i funkcje mogą być obsługiwane przez dostawców głównych magazynów. Entity SQL używa funkcji specyficznych dla magazynu zadeklarowanych w manifeście dostawcy. Ponadto Entity Framework umożliwia zadeklarować wbudowane i zdefiniowane przez użytkownika funkcje magazynu, aby Entity SQL do użycia.  
  
 Wskazówek  
 Entity SQL nie oferuje mechanizmów dla wskazówek dotyczących zapytań.  
  
 Wsadowe wyniki zapytania  
 Entity SQL nie obsługuje wsadowych wyników zapytania. Na przykład następujące są prawidłowe w języku Transact-SQL (wysyłanie jako partia):  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Jednak odpowiednik Entity SQL nie jest obsługiwany:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 Entity SQL obsługuje tylko jedną instrukcję zapytania wytwarzającą wynik na polecenie.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md)
