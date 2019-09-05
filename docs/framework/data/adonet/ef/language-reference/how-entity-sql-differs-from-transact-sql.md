---
title: Czym język Entity SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 1a4bf8267ee5f036effc5f7bc91c28d1485b7612
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250862"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Czym język Entity SQL różni się od języka Transact-SQL
W tym temacie opisano różnice między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] programami i Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Obsługa dziedziczenia i relacji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]działa bezpośrednio ze schematami jednostki koncepcyjnej i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.  
  
 Podczas pracy z dziedziczeniem często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu. Ta funkcja jest dostępna [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w operatorze `oftype` [OfType](oftype-entity-sql.md) w (podobnie jak w C# sekwencjach).  
  
## <a name="support-for-collections"></a>Obsługa kolekcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje kolekcje jako jednostki pierwszej klasy. Na przykład:  
  
- Wyrażenia kolekcji są prawidłowe w `from` klauzuli.  
  
- `in`i `exists` podzapytania zostały uogólnione w celu zezwolenia na jakiekolwiek kolekcje.  
  
     Podzapytanie jest jednym rodzajem kolekcji. `e1 in e2``exists(e)` i[!INCLUDE[esql](../../../../../../includes/esql-md.md)] są konstrukcjami do wykonywania tych operacji.  
  
- Ustaw operacje, takie jak `union`, `intersect`, i `except`teraz działają na kolekcjach.  
  
- Sprzężenia działają na kolekcjach.  
  
## <a name="support-for-expressions"></a>Obsługa wyrażeń  
 Transact-SQL ma podzapytania (tabele) i wyrażenia (wiersze i kolumny).  
  
 W celu obsługi kolekcji i kolekcji zagnieżdżonych, program [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tworzy wszystkie wyrażenia. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]jest większa niż Transact-SQL — każde wyrażenie może być używane w dowolnym miejscu. Wyrażenia zapytania zawsze powodują kolekcje typów rzutowanych i mogą być używane wszędzie tam, gdzie wyrażenie kolekcji jest dozwolone. Aby uzyskać informacje o wyrażeniach języka Transact-SQL, które [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie są obsługiwane w programie, zobacz [nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md).  
  
 Wszystkie prawidłowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania są następujące:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Ujednolicone traktowanie podkwerend  
 Uwzględniając podkreślenie w tabelach, Transact-SQL wykonuje kontekstową interpretację podzapytań. Na przykład podzapytanie w `from` klauzuli jest uznawane za zestaw wielokrotny (tabelę). Ale to samo podzapytanie użyte w `select` klauzuli jest uznawane za podzapytanie skalarne. Podobnie podzapytanie użyte po lewej stronie `in` operatora jest uznawane za podzapytanie skalarne, podczas gdy po prawej stronie oczekiwana jest podzapytanie zestawu wielokrotnego.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]eliminuje te różnice. Wyrażenie ma jednolitą interpretację, która nie zależy od kontekstu, w którym jest używana. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje wszystkie podzapytania jako podzapytania zestawu wielokrotnego. Jeśli jest wymagana wartość skalarna z podzapytania, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `anyelement` zapewnia operator, który działa w kolekcji (w tym przypadku podzapytania) i wyodrębnia wartość singleton z kolekcji.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Unikanie niejawnych zarzutów dla podkwerend  
 Powiązane skutki uboczne jednolitego traktowania podzapytań są niejawną konwersją podzapytań na wartości skalarne. W języku Transact-SQL zestaw wielokrotny wierszy (z pojedynczym polem) jest niejawnie konwertowany na wartość skalarną, której typem danych jest pole.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje tego niejawnego przekształcenia. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia operator AnyElement do wyodrębnienia wartości pojedynczej z kolekcji, a `select value` także klauzulę, aby uniknąć tworzenia otoki wiersza w wyrażeniu zapytania.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Wybierz wartość: Unikanie niejawnej otoki wiersza  
 Klauzula SELECT w podzapytaniu Transact-SQL niejawnie tworzy otokę wiersza wokół elementów w klauzuli. Oznacza to, że nie możemy utworzyć kolekcji skalarnych lub obiektów. Język Transact-SQL umożliwia niejawne przekształcenie między RowType z jednym polem a wartością singleton tego samego typu danych.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]`select value` udostępnia klauzulę do pomijania konstrukcji niejawnego wiersza. W `select value` klauzuli może być określony tylko jeden element. Gdy taka klauzula jest używana, żadna otoka wiersza nie jest zbudowana wokół elementów w `select` klauzuli i można utworzyć kolekcję żądanego kształtu, na przykład:. `select value a`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia także konstruktora wierszy do konstruowania dowolnych wierszy. `select`Pobiera co najmniej jeden element w projekcji i wyniki w rekordzie danych z polami w następujący sposób:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Lewa korelacja i aliasowanie  
 W języku Transact-SQL wyrażenia w danym zakresie (pojedyncza klauzula LIKE `select` lub `from`) nie mogą odwoływać się do wyrażeń zdefiniowanych wcześniej w tym samym zakresie. Niektóre dialekty SQL (w tym Transact-SQL) obsługują ograniczone formy tych w `from` klauzuli.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]uogólniuje lewe korelacje w `from` klauzuli i traktuje je równomiernie. Wyrażenia w `from` klauzuli mogą odwoływać się do wcześniejszych definicji (definicje po lewej) w tej samej klauzuli bez potrzeby dodatkowej składni.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nakłada również dodatkowe ograniczenia dotyczące zapytań obejmujących `group by` klauzule. Wyrażenia w `select` klauzuli i `having` klauzuli takich zapytań `group by` mogą odwoływać się tylko do kluczy za pośrednictwem ich aliasów. Następująca konstrukcja jest prawidłowa w języku Transact-SQL, ale nie znajdują się w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 W tym celu w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odwoływanie się do kolumn (właściwości) tabel (Kolekcje)  
 Wszystkie odwołania do kolumn [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w elemencie muszą być kwalifikowane przy użyciu aliasu tabeli. Następująca konstrukcja (przy założeniu `a` , że jest to prawidłowa kolumna `T`tabeli) jest prawidłowa w języku Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ale nie w.  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formularz jest  
  
```  
select t.a as A from T as t  
```  
  
 Aliasy tabeli są opcjonalne w `from` klauzuli. Nazwa tabeli jest używana jako alias niejawny. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zezwala również na następujący formularz:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Nawigacja za poorednictwem obiektów  
 Język Transact-SQL używa notacji "." w celu odwoływania się do kolumn (wierszy) tabeli. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]rozszerza tę notację (zapożyczone z języków programowania) do obsługi nawigacji za pośrednictwem właściwości obiektu.  
  
 Na przykład jeśli `p` jest wyrażeniem typu Person, poniżej [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przedstawiono składnię do odwoływania się do miasta adresu tej osoby.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Brak obsługi dla *  
 Język Transact-SQL obsługuje niekwalifikowaną * składnię jako alias dla całego wiersza oraz kwalifikowaną \* składnią (t.\*) jako skrót dla pól tej tabeli. Ponadto język Transact-SQL zezwala na agregację specjalna (\*), która zawiera wartości null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje konstrukcji *. Zapytania Transact-SQL formularza `select * from T` i `select T1.* from T1, T2...` [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t1 from T1 as t1, T2 as t2...`mogą być wyrażone odpowiednio w i.`select value t from T as t` Ponadto te konstrukcje obsługują dziedziczenie (podstawienie wartości), podczas gdy `select *` warianty są ograniczone do właściwości najwyższego poziomu zadeklarowanego typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje `count(*)` agregacji. Zamiast nich należy używać słów kluczowych `count(0)`.  
  
## <a name="changes-to-group-by"></a>Zmiany w grupie według  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje aliasowanie `group by` kluczy. Wyrażenia w `select` klauzuli i `having` klauzuli muszą odwoływać się do kluczyzapośrednictwemtychaliasów.`group by` Na przykład [!INCLUDE[esql](../../../../../../includes/esql-md.md)] następująca składnia:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ... jest odpowiednikiem następującego języka Transact-SQL:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Agregacje oparte na kolekcjach  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa rodzaje agregacji.  
  
 Agregacje oparte na kolekcji działają na kolekcjach i tworzą zagregowany wynik. Mogą one występować w dowolnym miejscu zapytania i nie wymagają `group by` klauzuli. Na przykład:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje również agregacje w stylu SQL. Na przykład:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>Użycie klauzuli ORDER BY  
 Język Transact-SQL zezwala na określenie klauzul ORDER BY tylko w ramach najwyższego poziomu. Z.. Blok WHERE. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Możesz użyć zagnieżdżonego wyrażenia order by, które można umieścić w dowolnym miejscu zapytania, ale porządkowanie w zagnieżdżonym zapytaniu nie jest zachowywane.  
  
```  
-- The following query will order the results by the last name  
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
  
## <a name="identifiers"></a>Identyfikatory  
 W języku Transact-SQL porównanie identyfikatorów jest oparte na sortowaniu bieżącej bazy danych. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)]programie identyfikatory są zawsze rozróżniane bez uwzględniania wielkości liter i znaków akcentu (oznacza to, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] że odróżnia znaki akcentowane i nieakcentowane, na przykład "a" nie jest równe "ấ"). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje wersje liter, które wyglądają tak samo, ale pochodzą z różnych stron kodowych jako różne znaki. Aby uzyskać więcej informacji, zobacz [wejściowy zestaw znaków](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkcja Transact-SQL nie jest dostępna w Entity SQL  
 Poniższe funkcje języka Transact-SQL nie są dostępne w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]programie.  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obecnie nie są obsługiwane instrukcje DML (INSERT, Update i Delete).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje języka DDL w bieżącej wersji.  
  
 programowanie imperatywne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie oferuje obsługi bezwzględnego programowania, w przeciwieństwie do języka Transact-SQL. Zamiast tego użyj języka programowania.  
  
 Funkcje grupowania  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Program nie zapewnia jeszcze obsługi funkcji grupowania (na przykład CUBE, ROLLUP i GROUPING_SET).  
  
 Funkcje analityczne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie (jeszcze) zapewnia obsługę funkcji analitycznych.  
  
 Wbudowane funkcje, operatory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje podzestaw wbudowanych funkcji i operatorów języka Transact-SQL. Te operatory i funkcje mogą być obsługiwane przez dostawców głównych magazynów. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]używa funkcji specyficznych dla magazynu zadeklarowanych w manifeście dostawcy. Ponadto umożliwia zadeklarować wbudowane i zdefiniowane przez użytkownika funkcje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] magazynu do użycia. [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]  
  
 Wskazówek  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie oferuje mechanizmów dla wskazówek dotyczących zapytań.  
  
 Wsadowe wyniki zapytania  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje wsadowych wyników zapytania. Na przykład następujące są prawidłowe w języku Transact-SQL (wysyłanie jako partia):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Jednak odpowiednik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwany:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje tylko jedną instrukcję zapytania wytwarzającą wynik na polecenie.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md)
