---
title: "Jak jednostki SQL różni się od języka Transact-SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 90c3b7d639ea6fafd570b44ee40c0567e264ea91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Jak jednostki SQL różni się od języka Transact-SQL
W tym temacie opisano różnice między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
## <a name="inheritance-and-relationships-support"></a>Dziedziczenie i relacje obsługi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]współpracuje bezpośrednio z Schematy koncepcyjne jednostki i obsługuje model koncepcyjny funkcje, takie jak dziedziczenia i relacje.  
  
 Podczas pracy z dziedziczenia, często warto wybrać wystąpienia podtypu z kolekcji wystąpień nadtypu. [Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operatora w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (podobnie jak `oftype` w sekwencjach C#) zapewnia tę funkcję.  
  
## <a name="support-for-collections"></a>Obsługa kolekcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje kolekcji jako najwyższej jakości jednostek. Na przykład:  
  
-   Wyrażenia kolekcji są prawidłowe w `from` klauzuli.  
  
-   `in`i `exists` podzapytania ma został uogólniony zezwalająca na wszystkie kolekcje.  
  
     Podzapytania jest jednego rodzaju kolekcji. `e1 in e2`i `exists(e)` są [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcji, aby wykonać te operacje.  
  
-   Ustaw operacje, takie jak `union`, `intersect`, i `except`, działał w kolekcjach.  
  
-   Sprzężenia działają w kolekcji.  
  
## <a name="support-for-expressions"></a>Obsługę wyrażeń  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]ma podzapytania (tabele) i wyrażenia (wierszy i kolumn).  
  
 Do obsługi kolekcji i zagnieżdżonych kolekcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sprawia, że wszystkie wyrażenia. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]więcej zezwala na składanie niż [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]— co wyrażenia można używać w dowolnym miejscu. Zapytanie wyrażenia zawsze powoduje kolekcji planowanego typów i mogą być używane wszędzie, gdzie jest dozwolona w wyrażeniu kolekcji. Aby uzyskać informacje o [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wyrażeń, które nie są obsługiwane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [nieobsługiwane wyrażenia](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).  
  
 Poniżej znajdują się wszystkie ważne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Jednolitego traktowania podzapytania  
 Podane jego wyróżnienia w tabelach, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] wykonuje kontekstowe interpretacja podzapytania. Na przykład podzapytania w `from` klauzuli jest traktowany jako zestaw wielokrotny (tabeli). Ale tego samego podzapytania, używane w `select` klauzuli jest traktowany jako skalarna podzapytania. Podobnie, podzapytania używane po lewej stronie `in` operator jest uznawane za podzapytania skalarne, gdy po prawej stronie powinien być podzapytania multiset —.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]eliminuje tych różnic. Wyrażenie zawiera jednolitej interpretacji, które nie są zależne od kontekstu, w którym jest używana. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]uwzględnia wszystkich podzapytaniach jako zestaw wielokrotny podzapytania. Jeśli wartość skalarną z podzapytania, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapewnia `anyelement` operator, który operuje na kolekcji (w tym przypadku podzapytanie) i wyodrębnianie pojedyncze wartości z kolekcji.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Unikanie niejawne Wymuszeniami dla zapytania podrzędne  
 Efekt uboczny pokrewne jednolitego traktowania podzapytania jest niejawnej konwersji wartości podzapytania wartości skalarnych. W szczególności w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], multiset wierszy (z jednym polem) jest niejawnie konwertowane na wartość skalarną, której typ danych jest to, że pola.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje tego niejawne przekształcenia. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera operator ANYELEMENT można wyodrębnić pojedynczą wartość z kolekcji, a `select value` klauzuli, aby uniknąć tworzenia otoka wiersza w wyrażeniu zapytania.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Wybierz wartość: Unikanie otoki niejawne wiersza  
 Klauzuli select w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] podzapytania niejawnie tworzy otokę wiersza elementów w klauzuli. Oznacza to, że nie można utworzyć kolekcji wartości skalarne lub obiektów. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]zezwala na niejawne koercja między rowtype z jednego pola i wartość singleton tego samego typu danych.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia `select value` klauzuli, aby pominąć konstrukcji niejawne wiersza. Można określić tylko jeden element w `select value` klauzuli. W przypadku takich klauzuli nie otoki wiersza jest tworzony wokół elementów w `select` klauzul i kolekcji żądanego kształtu mogą powstać, na przykład: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia również Konstruktor row do utworzenia dowolnego wierszy. `select`przyjmuje jeden lub więcej elementów w projekcji i wyników w rekordzie danych z polami, w następujący sposób:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Lewa Korelacja i aliasów  
 W [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], wyrażenia w danym zakresie (takich jak jedną klauzulę `select` lub `from`) nie może odwoływać się wyrażenia zdefiniowanego wcześniej w tym samym zakresie. Niektóre dialekty języka SQL (w tym [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) obsługuje ograniczone form w `from` klauzuli.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]stanowi uogólnienie po lewej stronie korelacji w `from` klauzuli i traktuje je jednakowo. Wyrażenia w `from` klauzuli może odwoływać się wcześniej definicje (definicje z lewej strony) w tej samej klauzuli bez konieczności stosowania dodatkowych składni.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nakłada także dodatkowe ograniczenia dotyczące zapytań `group by` klauzul. Wyrażenia w `select` klauzuli i `having` klauzuli takich zapytań może odwoływać się tylko do `group by` klucze za pomocą ich aliasów. Poniższa konstrukcja jest prawidłowa w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nie znajdują się w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Aby to zrobić w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Odwoływanie się do kolumn (właściwości) tabele (kolekcji)  
 Wszystkie odwołania do kolumn w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musi być kwalifikowany za pomocą aliasu tabeli. Poniższa konstrukcja (przy założeniu, że `a` jest prawidłową kolumnę tabeli `T`) jest nieprawidłowy w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , ale nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formularz  
  
```  
select t.a as A from T as t  
```  
  
 Aliasy tabeli są opcjonalne w `from` klauzuli. Nazwa tabeli jest używana jako alias niejawnej. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Umożliwia również następującą postać:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Nawigację obiektów  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]używa "." notation dla odwołania do kolumny (wiersz) tabeli. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Rozszerza ten element notation (pobierają z języków programowania) do obsługi nawigacji za pomocą właściwości obiektu.  
  
 Na przykład jeśli `p` jest wyrażenie wpisz osobę, Oto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składnię odwołujące się do miasta adres tej osoby.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Brak obsługi *  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]obsługuje niekwalifikowane * składni jako alias dla całego wiersza i kwalifikowaną \* składni (t.\*) jako skrót do pól w tej tabeli. Ponadto [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] umożliwia specjalne Count (\*) wartość zagregowaną, która zawiera wartości null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje * konstrukcji. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]zapytania w postaci `select * from T` i `select T1.* from T1, T2...` mogą być wyrażone w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jako `select value t from T as t` i `select value t1 from T1 as t1, T2 as t2...`odpowiednio. Ponadto tych konstrukcji obsługi dziedziczenia (wartość podaży), podczas gdy `select *` wariantów są ograniczone do najwyższego poziomu właściwości deklarowanego typu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje `count(*)` agregacji. Zamiast nich należy używać słów kluczowych `count(0)`.  
  
## <a name="changes-to-group-by"></a>Zmiany Grupuj według  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje aliasów z `group by` kluczy. Wyrażenia w `select` klauzuli i `having` klauzuli musi odwoływać się do `group by` klucze za pomocą tych aliasów. Na przykład to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] składni:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 .. jest standardem odpowiednikiem następujące [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Agreguje opartego na kolekcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa rodzaje wartości zagregowanych.  
  
 Agregacje opartego na kolekcji działać na kolekcje i utworzenia wyniku zagregowanych. Te mogą występować w dowolnym miejscu w zapytaniu i nie wymagają `group by` klauzuli. Na przykład:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje również wartości zagregowanych SQL stylu. Na przykład:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY — klauzula użycia  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]zezwala na klauzule ORDER BY określić tylko w najwyższej wybierz... Z... GDZIE bloku. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] można używać zagnieżdżonych Wyrażenie ORDER BY i można je umieścić w dowolnym miejscu w zapytaniu, ale szeregowaniem w zapytaniu zagnieżdżone nie są zachowywane.  
  
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
 W [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identyfikator porównania jest oparta na sortowanie bieżącej bazy danych. W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identyfikatory są zawsze bez uwzględniania wielkości liter i akcent poufnych (to znaczy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rozróżnia znaki akcentowane i formami; na przykład "" nie jest równa "ấ"). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje wersji liter wyglądają tak samo, które pochodzą z różnych kodowe jako różne znaki. Aby uzyskać więcej informacji, zobacz [zestaw znaków wprowadzania](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funkcje języka Transact-SQL nie jest dostępna w jednostce SQL  
 Następujące [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] funkcja nie jest dostępna w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obecnie nie zapewnia obsługi dla instrukcji DML (Wstawianie, aktualizowanie i usuwanie).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie zapewnia obsługi dla języka DDL w bieżącej wersji.  
  
 Programowanie imperatywne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie zapewnia obsługi imperatywnych programowania, w odróżnieniu od [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Zamiast tego użyj języka programowania.  
  
 Grupowanie funkcji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie jeszcze zapewnia obsługę do grupowania funkcji (na przykład, CUBE, ROLLUP i GROUPING_SET).  
  
 Funkcje analityczne  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie (jeszcze) zapewniają obsługę funkcji analitycznych.  
  
 Funkcje wbudowane operatory  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje podzbiór [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]przez wbudowane funkcje i operatory. Te operatory i funkcje są mogą być obsługiwane przez dostawców magazynu głównych. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]korzysta z funkcji specyficznych dla magazynu zadeklarowane w manifeście dostawcy. Ponadto [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umożliwia zadeklarować wbudowanych i zdefiniowanych przez użytkownika istniejących magazynu funkcji, dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do użycia.  
  
 Wskazówki  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie zapewnia mechanizmy wskazówki zapytania.  
  
 Przetwarzanie wsadowe wyników zapytania  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nie obsługuje przetwarzanie wsadowe wyników zapytania. Na przykład poniżej przedstawiono prawidłowe [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (wysyłania jako plik wsadowy):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Jednak odpowiednikiem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest obsługiwana:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje tylko jedną instrukcję zapytanie zwracające w wyniku na polecenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Nieobsługiwane wyrażenia](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
