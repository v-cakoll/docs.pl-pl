---
title: Czym język Entity SQL różni się od języka Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150234"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Czym język Entity SQL różni się od języka Transact-SQL
W tym temacie opisano [!INCLUDE[esql](../../../../../../includes/esql-md.md)] różnice między i Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Obsługa dziedziczenia i relacji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]współpracuje bezpośrednio ze schematami koncepcyjnych jednostek i obsługuje funkcje modelu koncepcyjnego, takie jak dziedziczenie i relacje.  
  
 Podczas pracy z dziedziczenia, często jest przydatne do wybierania wystąpień podtypu z kolekcji wystąpień nadtypu. [Oftype](oftype-entity-sql.md) operator [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w (podobnie jak `oftype` w sekwencje języka C#) zapewnia tę możliwość.  
  
## <a name="support-for-collections"></a>Obsługa kolekcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje kolekcje jako jednostki pierwszej klasy. Przykład:  
  
- Wyrażenia kolekcji są `from` prawidłowe w klauzuli.  
  
- `in`i `exists` podksycje zostały uogólnione, aby umożliwić wszelkie kolekcje.  
  
     Podkwerenda jest jednym z rodzajów kolekcji. `e1 in e2`i `exists(e)` są [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcje do wykonywania tych operacji.  
  
- Ustaw operacje, `union`takie `intersect`jak `except`, i , teraz działają na kolekcjach.  
  
- Sprzężenia działają na kolekcjach.  
  
## <a name="support-for-expressions"></a>Obsługa wyrażeń  
 Transact-SQL zawiera podquerie (tabele) i wyrażenia (wiersze i kolumny).  
  
 Do obsługi kolekcji i zagnieżdżonych kolekcji, sprawia, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] że wszystko wyrażenie. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]jest bardziej komponowalna niż Transact-SQL — każde wyrażenie może być używane w dowolnym miejscu. Wyrażenia kwerendy zawsze powodują kolekcje typów przewidywanych i mogą być używane wszędzie tam, gdzie wyrażenie kolekcji jest dozwolone. Aby uzyskać informacje o wyrażeniach Transact-SQL, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]programie , zobacz [Nieobsługiwalone wyrażenia](unsupported-expressions-entity-sql.md).  
  
 Oto wszystkie prawidłowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Jednolite traktowanie podkemietów  
 Biorąc pod uwagę nacisk na tabele, Transact-SQL wykonuje kontekstową interpretację podkemiewa. Na przykład podkwerendy `from` w klauzuli jest uważany za multiset (tabela). Ale ta sama podkwerenda używana w `select` klauzuli jest uważana za podkwerendę skalarną. Podobnie podkwerenda używane po lewej `in` stronie operatora jest uważany za podkwerendę skalarną, podczas gdy po prawej stronie oczekuje się, że jest podkwerendą wielozestawową.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]eliminuje te różnice. Wyrażenie ma jednolitą interpretację, która nie zależy od kontekstu, w którym jest używany. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]uważa, że wszystkie podksy podksyrii są podksygną wielozespołowe. Jeśli wartość skalarna jest pożądana [!INCLUDE[esql](../../../../../../includes/esql-md.md)] z `anyelement` podzapytania, zapewnia operator, który działa na kolekcji (w tym przypadku podkwerendy) i wyodrębnia wartość singleton z kolekcji.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Unikanie ukrytych przymusów dla podkemietów  
 Powiązanym skutkiem ubocznym jednolitego traktowania podkwery jest niejawna konwersja podkwererów do wartości skalarnych. W szczególności w transact-SQL, zestaw wielu wierszy (z jednym polem) jest niejawnie konwertowane na wartość skalarną, której typem danych jest to, że w polu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje tego ukrytego przymusu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zapewnia ANYELEMENT operator wyodrębnić wartość singleton z `select value` kolekcji i klauzuli, aby uniknąć tworzenia otoki wiersza podczas wyrażenia kwerendy.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Wybierz wartość: Unikanie niejawnego otoki wiersza  
 Klauzula select w podkwercie Transact-SQL niejawnie tworzy otokę wiersza wokół elementów w klauzuli. Oznacza to, że nie możemy tworzyć kolekcji skalarnych lub obiektów. Transact-SQL umożliwia niejawne przymusu między typem wiersza z jednym polem i wartością singleton tego samego typu danych.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera `select value` klauzulę, aby pominąć konstrukcję niejawnego wiersza. W `select value` klauzuli można określić tylko jeden element. Gdy taka klauzula jest używana, wokół elementów w `select` klauzuli nie jest skonstruowane żadne otoki wierszy, a kolekcja żądanego kształtu może być wyprodukowana, na przykład: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia również konstruktora wierszy do konstruowania dowolnych wierszy. `select`przyjmuje jeden lub więcej elementów projekcji i powoduje, że rekord danych z polami jest następujący:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Lewa korelacja i aliasowanie  
 W Transact-SQL wyrażenia w danym zakresie (pojedyncza klauzula jak `select` lub `from`) nie mogą odwoływać się do wyrażeń zdefiniowanych wcześniej w tym samym zakresie. Niektóre dialekty SQL (w tym Transact-SQL) obsługują `from` ograniczone formy tych w klauzuli.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]uogólnia lewe korelacje w klauzuli `from` i traktuje je jednolicie. Wyrażenia w `from` klauzuli można odwoływać się do wcześniejszych definicji (definicje po lewej) w tej samej klauzuli bez konieczności dodatkowej składni.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nakłada również dodatkowe ograniczenia na zapytania `group by` dotyczące klauzul. Wyrażenia w `select` klauzuli `having` i klauzuli takich zapytań `group by` mogą odwoływać się do kluczy tylko za pośrednictwem ich aliasów. Następująca konstrukcja jest prawidłowa w Transact-SQL, ale nie ma w: [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Aby to [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zrobić w:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odwoływanie się do kolumn (właściwości) tabel (kolekcje)  
 Wszystkie odwołania do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolumn muszą być kwalifikowane za pomocą aliasu tabeli. Następująca konstrukcja (przy założeniu, `a` `T`że jest prawidłową kolumną tabeli) jest prawidłowa w transact-SQL, ale nie w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```sql  
SELECT a FROM T
```  
  
 Formularz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Aliasy tabeli są `from` opcjonalne w klauzuli. Nazwa tabeli jest używana jako alias niejawny. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]pozwala również na następującą formę:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Nawigacja po obiektach  
 Transact-SQL używa notacji "." do odwoływania się do kolumn (wiersza) tabeli. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]rozszerza tę notację (zapożyczoną z języków programowania) do obsługi nawigacji za pośrednictwem właściwości obiektu.  
  
 Na przykład `p` jeśli jest wyrażeniem typu Osoba, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poniżej znajduje się składnia odwoływania się do miasta adresu tej osoby.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>Brak wsparcia dla *  
 Transact-SQL obsługuje składnię niekwalifikowaną * jako alias dla \* całego wiersza\*i składnię kwalifikowaną (t. ) jako skrót dla pól tej tabeli. Ponadto Transact-SQL pozwala na specjalną\*liczbę( ) agregacji, która zawiera wartości null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje konstrukcji *. Zapytania transact-SQL `select * from T` formularza i `select T1.* from T1, T2...` mogą być [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażone w as `select value t from T as t` i `select value t1 from T1 as t1, T2 as t2...`, odpowiednio. Ponadto te konstrukcje obsługi dziedziczenia (substytucyjność wartości), podczas gdy `select *` warianty są ograniczone do właściwości najwyższego poziomu zadeklarowanego typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje `count(*)` agregacji. Zamiast tego użyj polecenia cmdlet `count(0)`.  
  
## <a name="changes-to-group-by"></a>Zmiany w grupie według  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje aliasing `group by` klawiszy. Wyrażenia w `select` klauzuli `having` i klauzuli `group by` musi odwoływać się do kluczy za pośrednictwem tych aliasów. Na przykład [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ta składnia:  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... odpowiada następującemu transact-SQL:  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Agregaty oparte na kolekcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa rodzaje agregatów.  
  
 Agregaty oparte na kolekcji działają na kolekcjach i generują zagregowany wynik. Mogą one pojawić się w dowolnym miejscu `group by` w kwerendzie i nie wymagają klauzuli. Przykład:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje również agregacje w stylu SQL. Przykład:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY Użycie klauzuli  
Transact-SQL `ORDER BY` umożliwia klauzule, które mają `SELECT .. FROM .. WHERE` być określone tylko w głównym bloku. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można użyć wyrażenia `ORDER BY` zagnieżdżonego i może być umieszczony w dowolnym miejscu w kwerendzie, ale kolejność w kwerendzie zagnieżdżonej nie jest zachowywana.  
  
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
 W Transact-SQL porównanie identyfikatorów opiera się na sortowanie bieżącej bazy danych. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)]identyfikatorach zawsze są niewrażliwe na wielkość liter [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i akcenty (to oznacza, że rozróżnia znaki akcentowane i bez akcentu; na przykład "a" nie jest równe "ѕ"). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje wersje liter, które wyglądają tak samo, ale pochodzą z różnych stron kodowych, jak różne znaki. Aby uzyskać więcej informacji, zobacz [Input Character Set](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkcja Transact-SQL niedostępna w programie Entity SQL  
 Następująca funkcja Transact-SQL nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)]jest dostępna w programie .  
  
 Dml  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obecnie nie zapewnia obsługi instrukcji DML (wstaw, aktualizacja, usuwanie).  
  
 Ddl  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie zapewnia obsługi DDL w bieżącej wersji.  
  
 programowanie imperatywne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie zapewnia obsługi programowania imperatywowego, w przeciwieństwie do Transact-SQL. Zamiast tego użyj języka programowania.  
  
 Funkcje grupowania  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie zapewnia jeszcze obsługi funkcji grupowania (na przykład CUBE, ROLLUP i GROUPING_SET).  
  
 Funkcje analityczne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie zapewnia (jeszcze) wsparcia dla funkcji analitycznych.  
  
 Wbudowane funkcje, operatorzy  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje podzbiór wbudowanych funkcji i operatorów Transact-SQL. Te operatory i funkcje mogą być obsługiwane przez głównych dostawców sklepu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]używa funkcji specyficznych dla magazynu zadeklarowanych w manifeście dostawcy. Ponadto entity framework umożliwia zadeklarowanie wbudowanych i zdefiniowanych przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] użytkownika istniejących funkcji magazynu, do użycia.  
  
 Wskazówki  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie zapewnia mechanizmów dla wskazówek dotyczących zapytań.  
  
 Przetwarzanie wsadowe wyniki kwerendy  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje wyników kwerendy wsadowe. Na przykład następujące jest prawidłowe Transact-SQL (wysyłanie jako partia):  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Jednak odpowiednik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwany:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje tylko jedną instrukcję kwerendy powodującą wynik na polecenie.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md)
