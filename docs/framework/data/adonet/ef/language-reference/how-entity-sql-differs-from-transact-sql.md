---
title: Czym język Entity SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 54d7a3fa8ce6e8a0aba6194bfc034eb4d47dbf60
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489926"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Czym język Entity SQL różni się od języka Transact-SQL
W tym temacie opisano różnice między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oraz języka Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Dziedziczenie i relacje obsługi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] współpracuje bezpośrednio ze schematami koncepcyjnymi encji i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.  
  
 Podczas pracy z dziedziczenia, często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu. [Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operatora w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobnie jak `oftype` w C# sekwencje) zapewnia tę funkcję.  
  
## <a name="support-for-collections"></a>Obsługa kolekcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traktuje kolekcji jako obiekty najwyższej jakości. Na przykład:  
  
- Wyrażenia kolekcji są prawidłowe w `from` klauzuli.  
  
- `in` i `exists` podzapytań mają został uogólniony, aby zezwolić na wszystkie kolekcje.  
  
     Podzapytania jest jeden rodzaj kolekcji. `e1 in e2` i `exists(e)` są [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcji wykonywać te operacje.  
  
- Ustawić operacje, takie jak `union`, `intersect`, i `except`, teraz działają w kolekcjach.  
  
- Sprzężenia działają w kolekcjach.  
  
## <a name="support-for-expressions"></a>Obsługa wyrażeń  
 Języka Transact-SQL ma podzapytań (tabele) i wyrażenia (wiersze i kolumny).  
  
 Do obsługi kolekcji i kolekcje zagnieżdżone [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sprawia, że wszystkie wyrażenia. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest bardziej konfigurowalna niż języka Transact-SQL — każde wyrażenie może być używane w dowolnym miejscu. Zapytanie wyrażenia zawsze powoduje kolekcji typów przewidywanych i mogą być używane wszędzie, gdzie jest dozwolona w wyrażeniu kolekcji. Aby uzyskać informacje o wyrażeniach języka Transact-SQL, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [nieobsługiwane wyrażenia](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).  
  
 Poniżej znajdują się wszystkie prawidłowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Jednolitego traktowania podzapytań  
 Biorąc pod uwagę jej nacisk na tabele, języka Transact-SQL wykonuje kontekstowych interpretacji podzapytania. Na przykład podzapytania w `from` klauzula jest uważany za multiset (tabela). Ale ten sam podzapytanie używane w `select` klauzula jest uważany za skalarne podzapytania. Podobnie, podzapytania używane w lewej części `in` operator jest uważany za podzapytania skalarne, a po prawej stronie powinien być multiset — podzapytanie.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] eliminuje te różnice. Wyrażenie zawiera jednolitej interpretacji, które nie są zależne od kontekstu, w którym jest używany. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] uwzględnia wszystkich podzapytaniach to zestaw wielokrotny podzapytania. Jeśli wartość skalarną z podzapytania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapewnia `anyelement` operator, który działa w kolekcji (w tym przypadku podzapytanie) i wyodrębnia wartości pojedynczego wystąpienia z kolekcji.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Unikanie niejawne Coercions dla podzapytań  
 Powiązane efekt uboczny jednolitego traktowania podzapytań jest niejawnej konwersji wartości podzapytań wartości skalarnych. W szczególności w języku Transact-SQL, multiset wierszy (z jednym polem) jest niejawnie konwertowany na wartość skalarną, której typem danych jest to, że pola.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje tego niejawne przekształcenia. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zawiera operator ANYELEMENT do wyodrębnienia pojedyncze wartości z kolekcji, a `select value` klauzulę, aby uniknąć tworzenia otoki wiersza w wyrażeniu zapytania.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Wybierz wartość: Unikanie otoki niejawne wiersza  
 Klauzula select w podzapytaniu języka Transact-SQL niejawnie tworzy otokę wierszy elementów w klauzuli. Oznacza to, że nie można utworzyć kolekcji wartości skalarnych lub obiektów. Języka Transact-SQL umożliwia niejawne wymuszenia między rowtype z jednym polem i wartości pojedynczego wystąpienia typu danych.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] udostępnia `select value` klauzuli, aby pominąć konstrukcji niejawne wiersza. Można określić tylko jeden element w `select value` klauzuli. W przypadku takich klauzuli nie otoki wiersza została zbudowana w oparciu elementów w `select` klauzuli i kolekcji żądany kształt mogą powstać, na przykład: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapewnia także Konstruktor row do utworzenia dowolnego wierszy. `select` przyjmuje jeden lub więcej elementów w projekcji i wyniki w rekordzie danych przy użyciu pól, w następujący sposób:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Lewa Korelacja i aliasów  
 W języku Transact-SQL, wyrażenia w danym zakresie (takie jak pojedyncza klauzula `select` lub `from`) nie może odwoływać się do wyrażenia zdefiniowany wcześniej w tym samym zakresie. Niektóre dialekty programu SQL Server (w tym języka Transact-SQL) obsługuje ograniczone formy w `from` klauzuli.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] stanowi uogólnienie korelacji po lewej stronie w `from` klauzuli i traktować je równomiernie. Wyrażenia w `from` klauzuli może odwoływać się definicje wcześniejsze (definicje po lewej stronie) w tej samej klauzuli bez konieczności stosowania dodatkowej składni.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] również nakłada dodatkowe ograniczenia dotyczące zapytania obejmujące `group by` klauzul. Wyrażenia w `select` klauzuli i `having` klauzuli takich zapytań może odwoływać się tylko do `group by` kluczy przy użyciu ich aliasów. Następujące konstrukcja jest nieprawidłowy w instrukcji Transact-SQL, ale nie są [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Aby to zrobić w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odwoływanie się do kolumn (właściwości) tabel (kolekcji)  
 Wszystkie odwołania do kolumn w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musi być kwalifikowana za pomocą aliasu tabeli. Następująca konstrukcja (przy założeniu, że `a` jest prawidłową kolumną tabeli `T`) jest prawidłowa w języku Transact-SQL, ale nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formularz  
  
```  
select t.a as A from T as t  
```  
  
 Aliasy tabeli są opcjonalne w `from` klauzuli. Nazwa tabeli jest używany jako alias niejawne. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Umożliwia także następującą postać:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Nawigacja za pośrednictwem obiektów  
 Używa języka Transact-SQL "." Notacja do odwoływania się do kolumn (wiersz) tabeli. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Rozszerza ten zapis (pobierają z języków programowania) do obsługi nawigacji za pomocą właściwości obiektu.  
  
 Na przykład jeśli `p` wyrażenia wpisz osobę, Oto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składni do odwoływania się do miasta adres tej osoby.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Brak obsługi *  
 Języka Transact-SQL obsługuje niekwalifikowanej * składni jako alias dla całego wiersza i kwalifikowaną \* składni (t.\*) jako skrót dla pól tej tabeli. Ponadto języka Transact-SQL umożliwia specjalnych licznik (\*) wartość zagregowaną, która zawiera wartości null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje * konstrukcji. Zapytania Transact-SQL w postaci `select * from T` i `select T1.* from T1, T2...` mogą być wyrażone w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` i `select value t1 from T1 as t1, T2 as t2...`, odpowiednio. Ponadto te konstrukcje obsługi dziedziczenia (wartość podaży), podczas gdy `select *` wariantów są ograniczone do najwyższego poziomu właściwości zadeklarowanym typem.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje `count(*)` agregacji. Zamiast nich należy używać słów kluczowych `count(0)`.  
  
## <a name="changes-to-group-by"></a>Zmiany Grupuj według  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje tworzenie aliasów dla `group by` kluczy. Wyrażenia w `select` klauzuli i `having` klauzuli musi odwoływać się do `group by` kluczy przy użyciu te aliasy. Na przykład, to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składni:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ... jest równoważne z instrukcji Transact-SQL:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Wartości zagregowane z kolekcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje dwa rodzaje wartości zagregowanych.  
  
 Agregacje związanych z kolekcjami działają w kolekcjach i tworzące zagregowany wynik. Te mogą występować w dowolnym miejscu w zapytaniu i nie wymagają `group by` klauzuli. Na przykład:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje również wartości zagregowanych SQL stylu. Na przykład:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>KOLEJNOŚĆ według użycia klauzuli  
 Języka Transact-SQL umożliwia klauzule w klauzuli ORDER BY, należy określić tylko w najwyższej wybierz... OD... GDZIE zablokować. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można używać zagnieżdżonych wyrażeń klauzuli ORDER BY i można je umieścić w dowolnym miejscu w zapytaniu, ale szeregowaniem w zapytaniu zagnieżdżone nie są zachowywane.  
  
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
 W języku Transact-SQL porównanie identyfikatorów opiera się na sortowania bieżącej bazy danych. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identyfikatory są zawsze bez uwzględniania wielkości liter i akcent poufnych (czyli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozróżnia znaki akcentowane i nieakcentowane; na przykład, "" nie jest równa "ấ"). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traktuje wersji liter, są wyświetlane takie same, które pochodzą z różne strony kodowe jako różne znaki. Aby uzyskać więcej informacji, zobacz [zestaw znaków danych wejściowych](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkcje języka Transact-SQL nie jest dostępna w jednostki SQL  
 Następujące funkcje języka Transact-SQL nie jest dostępna w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obecnie nie obsługuje instrukcji DML (Wstawianie, aktualizowanie i usuwanie).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje języka DDL w bieżącej wersji.  
  
 programowanie imperatywne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje programowanie imperatywne, w przeciwieństwie do języka Transact-SQL. Zamiast tego użyj języka programowania.  
  
 Funkcje grupowania  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jeszcze zapewniają obsługę grupowanie funkcji (na przykład moduł, pakiet ZBIORCZY i GROUPING_SET).  
  
 Funkcje analityczne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie (jeszcze) zapewnia obsługę funkcji analitycznych.  
  
 Funkcje wbudowane, operatory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje podzbiór języka Transact-SQL zawiera wbudowane funkcje i operatory. Te operatory i funkcje mogą być obsługiwane przez dostawców magazynu głównych. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] korzysta z funkcji specyficznych dla magazynu zadeklarowane w manifeście dostawcy. Ponadto [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umożliwia deklarację wbudowanych oraz istniejącego użytkownika przechowywane funkcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do użycia.  
  
 Wskazówki  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie zapewnia mechanizmy wskazówki zapytania.  
  
 Przetwarzanie wsadowe wyników zapytania  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie obsługuje przetwarzania wsadowego wyników zapytania. Na przykład Oto prawidłowe języka Transact-SQL (wysyłającym jako zadania wsadowego):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Jednak odpowiednik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwane:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje tylko jedną instrukcję zapytania zwracające wyniki dla polecenia.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Nieobsługiwane wyrażenia](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
