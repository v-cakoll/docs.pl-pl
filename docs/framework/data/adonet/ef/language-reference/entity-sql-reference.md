---
title: Odwołanie do jednostki SQL
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 79cdf35128ac35920797060b09ff2fc5999708a7
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028022"
---
# <a name="entity-sql-reference"></a>Odwołanie do jednostki SQL

Ta sekcja zawiera artykuły odwołanie do jednostki SQL. Ten artykuł zawiera podsumowanie oraz grupy operatorów SQL jednostki według kategorii.

## <a name="arithmetic-operators"></a>Operatory arytmetyczne

Operatory arytmetyczne wykonywania operacji matematycznych na dwóch wyrażeniach co najmniej jeden typ danych liczbowych. W poniższej tabeli wymieniono operatory arytmetyczne jednostki SQL:

|Operator|Zastosowanie|
|--------------|---------|
|[+ (Dodaj)](add.md)|Dodatek.|
|[/ (Dzielenie)](divide-entity-sql.md)|Podział.|
|[% (Modulo)](modulo-entity-sql.md)|Zwraca resztę z dzielenia.|
|[* (Mnożenie)](multiply-entity-sql.md)|Mnożenia.|
|[- (Ujemne)](negative-entity-sql.md)|Negacja.|
|[- (Odejmowanie)](subtract-entity-sql.md)|Odejmowanie.|

## <a name="canonical-functions"></a>Canonical funkcji

Canonical funkcje są obsługiwane przez wszystkich dostawców danych i mogą być używane przez wszystkie technologie wykonywanie zapytania. W poniższej tabeli wymieniono funkcje kanoniczny:

|Funkcja|Typ|
|--------------|----------|
|[Canonical funkcji SQL agregacji jednostki](aggregate-canonical-functions.md)|W tym artykule omówiono kanonicznej funkcji agregujących SQL jednostki.|
|[Funkcje matematyczne Canonical](math-canonical-functions.md)|W tym artykule omówiono funkcje canonical matematyczne SQL jednostki.|
|[Funkcje ciągów Canonical](string-canonical-functions.md)|W tym artykule omówiono funkcje canonical ciągów SQL jednostki.|
|[Funkcji daty i godziny Canonical](date-and-time-canonical-functions.md)|W tym artykule omówiono kanonicznej funkcji SQL jednostek daty i godziny.|
|[Funkcje bitowe Canonical](bitwise-canonical-functions.md)|W tym artykule omówiono bitowe funkcji kanonicznej SQL jednostki.|
|[Inne funkcje Canonical](other-canonical-functions.md)|W tym artykule omówiono funkcje nie są sklasyfikowane jako bitowe, daty/godziny, ciąg, matematyczne lub agregacji.|

## <a name="comparison-operators"></a>Operatory porównania

Operatory porównania są definiowane dla następujących typów: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` , `DateTimeOffset`. Promocja typu niejawnego występuje operandy przed zastosowaniem operator porównania. Operatory porównania yield zawsze wartościami logicznymi. Gdy co najmniej jeden z argumentów jest `null`, wynikiem jest `null`.

Równości i nierówności są definiowane dla dowolnego typu obiektu, który ma tożsamość, takich jak `Boolean` typu. Niepierwotne obiekty o tożsamości są traktowane jako równe, jeśli mają tej samej tożsamości. W poniższej tabeli wymieniono operatory porównania jednostki SQL:

|Operator|Opis|
|--------------|-----------------|
|[= (Równa się)](equals-entity-sql.md)|Porównuje równość dwóch wyrażeń.|
|[> (Większe niż)](greater-than-entity-sql.md)|Porównuje dwa wyrażenia w celu określenia, czy wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie.|
|[>= (Większe niż lub równe)](greater-than-or-equal-to-entity-sql.md)|Porównuje dwa wyrażenia, aby sprawdzić, czy po lewej stronie wyrażenia jest wartość większa niż lub równa prawe wyrażenie.|
|[IS &#91;NOT&#93; NULL](isnull-entity-sql.md)|Określa, czy wyrażenie kwerendy jest null.|
|[< (Mniejsze niż)](less-than-entity-sql.md)|Porównuje dwa wyrażenia w celu określenia, czy wyrażenie po lewej stronie ma wartość mniejszą niż prawe wyrażenie.|
|[<= (Mniejsze niż lub równe)](less-than-or-equal-to-entity-sql.md)|Porównuje dwa wyrażenia, aby określić, czy wyrażenie po lewej stronie ma wartość mniejszą niż lub równe prawe wyrażenie.|
|[&#91;NOT&#93; BETWEEN](between-entity-sql.md)|Określa, czy wyrażenie wynikiem jest wartość w określonym zakresie.|
|[\!= (Nie równa się)](not-equal-to-entity-sql.md)|Porównuje dwa wyrażenia, aby określić, czy po lewej stronie wyrażenia nie jest równa prawe wyrażenie.|
|[&#91;NOT&#93; LIKE](like-entity-sql.md)|Określa, czy dany ciąg znaków jest zgodna z określonym wzorcem.|

## <a name="logical-and-case-expression-operators"></a>Operatory logiczne i case wyrażenia

Operatory logiczne sprawdzić prawdy warunku. Wyrażenie CASE ocenia zestaw wyrażeń logicznych w celu ustalenia wyniku. W poniższej tabeli wymieniono operatorów logicznych i wielkość wyrażenia:

|Operator|Opis|
|--------------|-----------------|
|[&& (Logiczne i)](and-entity-sql.md)|Operatora logicznego AND.|
|[\! (NEGACJA)](not-entity-sql.md)|NEGACJA.|
|[&#124;&#124;(Logiczne lub)](or-entity-sql.md)|Operatora logicznego OR.|
|[CASE](case-entity-sql.md)|Ocenia zestaw wyrażeń logicznych w celu ustalenia wyniku.|
|[THEN](then-entity-sql.md)|Wynik [podczas](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998) klauzuli gdy zwraca wartość true.|

## <a name="query-operators"></a>Operatory zapytań

Operatory zapytań są używane do definiowania wyrażenia zapytania, które zwracają dane jednostki. W poniższej tabeli wymieniono operatorów zapytań:

|Operator|Zastosowanie|
|--------------|---------|
|[FROM](from-entity-sql.md)|Określa kolekcję, która jest używana w [wybierz](select-entity-sql.md) instrukcje.|
|[GROUP BY](group-by-entity-sql.md)|Określa grupę, do których obiektów które zwróconych przez kwerendę ([wybierz](select-entity-sql.md)) zostaną umieszczone wyrażenia.|
|[GroupPartition](grouppartition-entity-sql.md)|Zwraca kolekcję wartości argumentu, przewidywane wyłączanie partycji grupy, do którego odnosi się agregacji.|
|[HAVING](having-entity-sql.md)|Określa warunek wyszukiwania dla grupy lub agregacja.|
|[LIMIT](limit-entity-sql.md)|Używane z [ORDER BY](order-by-entity-sql.md) klauzuli, aby wykonał stronicowania fizycznych.|
|[ORDER BY](order-by-entity-sql.md)|Określa porządek sortowania, jaka jest używana na obiekty zwrócone w [wybierz](select-entity-sql.md) instrukcji.|
|[SELECT](select-entity-sql.md)|Określa elementy w projekcji, z którego są zwracane przez zapytanie.|
|[SKIP](skip-entity-sql.md)|Używane z [ORDER BY](order-by-entity-sql.md) klauzuli, aby wykonał stronicowania fizycznych.|
|[TOP](top-entity-sql.md)|Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania.|
|[WHERE](where-entity-sql.md)|Warunkowe filtrów danych zwracanych przez zapytanie.|

## <a name="reference-operators"></a>Odwołanie do operatorów

Odwołanie ma postać wskaźnika logiczne (klucz obcy) do określonej jednostki w zestawie określonej jednostki. Jednostki SQL obsługuje następujące operatory utworzenia deconstruct i przejdź do odwołania:

|Operator|Zastosowanie|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Tworzy odwołania do jednostki w zestawie jednostek.|
|[DEREF](deref-entity-sql.md)|Wyłuskań wartość odniesienia i daje w wyniku tego usunąć odwołania do.|
|[KEY](key-entity-sql.md)|Wyodrębnia klucza referencyjnego lub wyrażenie jednostki.|
|[NAVIGATE](navigate-entity-sql.md)|Umożliwia przejście przez relację typu jeden jednostki do innego|
|[REF](ref-entity-sql.md)|Zwraca odwołanie do wystąpienia jednostki.|

## <a name="set-operators"></a>Operatory zestawów

Jednostki SQL zawiera różne operacje zaawansowany zestaw. Obejmuje to podobne do operatorów języka Transact-SQL, takich jak UNION, INTERSECT i EXCEPT, operatorów i EXISTS. Jednostki SQL obsługuje również operatory wyeliminowania zduplikowanych (SET), członkostwo testowania (ruch PRZYCHODZĄCY) i sprzężeń (połączenie). W poniższej tabeli wymieniono operatory zestawów jednostek SQL:

|Operator|Zastosowanie|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Wyodrębnia element z kolekcji wielowartościowych.|
|[EXCEPT](except-entity-sql.md)|Zwraca kolekcję wszystkie unikatowe wartości w wyrażeniu kwerendy do lewego operandu EXCEPT, który również nie są zwracane po prawej stronie argument EXCEPT wyrażenia zapytania.|
|[&#91;NOT&#93; EXISTS](exists-entity-sql.md)|Określa, czy kolekcja jest pusta.|
|[FLATTEN](flatten-entity-sql.md)|Konwertuje kolekcję spłaszczonych kolekcją kolekcji.|
|[&#91;NOT&#93; IN](in-entity-sql.md)|Określa, czy wartość odpowiada wartości w kolekcji.|
|[INTERSECT](intersect-entity-sql.md)|Zwraca kolekcję różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej krawędzi argument INTERSECT.|
|[OVERLAPS](overlaps-entity-sql.md)|Określa, czy dwie kolekcje mają wspólne elementy.|
|[SET](set-entity-sql.md)|Umożliwia przekonwertowanie kolekcji obiektów do zestawu przez reaguje nowej kolekcji z wszystkie zduplikowane elementy usunięte.|
|[UNION](union-entity-sql.md)|Łączy wyniki dwóch lub więcej kwerend w jednej kolekcji.|

## <a name="type-operators"></a>Operatory typu

Jednostki SQL zawiera operacje, które dopuszcza typu wyrażenia (wartość) utworzone, proszeni i manipulowanie. W poniższej tabeli wymieniono operatory, które są używane do pracy z typów:

|Operator|Zastosowanie|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Konwertuje wyrażenie jednego typu danych na inny.|
|[COLLECTION](collection-entity-sql.md)|Używane w [funkcja](function-entity-sql.md) operację, aby zadeklarować zbiór typy jednostek i typów złożonych.|
|[IS &#91;NOT&#93; OF](isof-entity-sql.md)|Określa, czy typ wyrażenia jest określonego typu lub jednego z jego podtypach.|
|[OFTYPE](oftype-entity-sql.md)|Zwraca kolekcję obiektów z wyrażenia zapytania, który jest określonego typu.|
|[Konstruktor typu nazwanego](named-type-constructor-entity-sql.md)|Używany do tworzenia wystąpień typów jednostek i typów złożonych.|
|[MULTISET](multiset-entity-sql.md)|Tworzy wystąpienie zestaw wielokrotny na podstawie listy wartości.|
|[ROW](row-entity-sql.md)|Tworzy rekordy anonimowe, strukturę typu z co najmniej jedną wartość.|
|[TREAT](treat-entity-sql.md)|Traktuje obiektu określonego typu podstawowego jako obiekt określonego typu pochodnego.|

## <a name="other-operators"></a>Inne operatory

W poniższej tabeli wymieniono operatorów innych jednostek SQL:

|Operator|Zastosowanie|
|--------------|---------|
|[+ (Łączenie ciągów)](string-concatenation-entity-sql.md)|Używany do ciągów w programie SQL jednostki.|
|[. (Dostęp do elementu członkowskiego)](member-access-entity-sql.md)|Używane do uzyskania dostępu do wartości właściwości lub pola wystąpienia typu strukturalnego modelu koncepcyjnego.|
|[-- (Komentarz)](comment-entity-sql.md)|Dołącz komentarze SQL jednostki.|
|[FUNCTION](function-entity-sql.md)|Definiuje funkcję śródwierszową, które mogą być wykonywane w kwerendzie SQL jednostki.|

## <a name="see-also"></a>Zobacz także

[Jednostki języka SQL](entity-sql-language.md)
