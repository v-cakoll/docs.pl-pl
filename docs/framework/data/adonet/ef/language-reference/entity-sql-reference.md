---
title: Odwołanie do jednostki SQL
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 9b666b83674cb2374409e321a2b715e9910bdd0e
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826645"
---
# <a name="entity-sql-reference"></a>Odwołanie do jednostki SQL

Ta sekcja zawiera artykuły odwołanie do jednostki SQL. Ten artykuł zawiera podsumowanie i grupy operatorów SQL jednostek według kategorii.

## <a name="arithmetic-operators"></a>Operatory arytmetyczne

Operatory arytmetyczne wykonywania operacji matematycznych na dwóch wyrażeniach co najmniej jeden typ danych liczbowych. W poniższej tabeli wymieniono operatory arytmetyczne jednostki SQL:

|Operator|Zastosowanie|
|--------------|---------|
|[+ (Dodaj)](add.md)|Dodatek.|
|[/ (Dzielenie)](divide-entity-sql.md)|Dzielenie.|
|[% (Modulo)](modulo-entity-sql.md)|Zwraca resztę z dzielenia.|
|[* (Mnożenie)](multiply-entity-sql.md)|Mnożenia.|
|[- (Ujemne)](negative-entity-sql.md)|Negacja.|
|[- (Odejmowanie)](subtract-entity-sql.md)|Odejmowanie.|

## <a name="canonical-functions"></a>Funkcje Canonical

Funkcje Canonical są obsługiwane przez wszystkich dostawców danych i mogą być używane przez wszystkie technologie zapytań. W poniższej tabeli wymieniono funkcje canonical:

|Funkcja|Typ|
|--------------|----------|
|[Funkcje Canonical agregacji jednostki SQL](aggregate-canonical-functions.md)|W tym artykule omówiono funkcje agregujące canonical jednostki SQL.|
|[Funkcje matematyczne Canonical](math-canonical-functions.md)|W tym artykule omówiono funkcje matematyczne jednostki SQL canonical.|
|[Funkcje ciągów Canonical](string-canonical-functions.md)|W tym artykule omówiono funkcje canonical ciągów SQL jednostki.|
|[Funkcji daty i godziny Canonical](date-and-time-canonical-functions.md)|W tym artykule omówiono funkcje canonical jednostki SQL daty i godziny.|
|[Funkcje bitowe Canonical](bitwise-canonical-functions.md)|W tym artykule omówiono bitowe funkcje canonical jednostki SQL.|
|[Inne funkcje Canonical](other-canonical-functions.md)|W tym artykule omówiono funkcje nie sklasyfikowane jako bitowe, daty/godziny, ciąg, matematyczne lub agregacji.|

## <a name="comparison-operators"></a>Operatory porównania

Operatory porównania są zdefiniowane dla następujących typów: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` , `DateTimeOffset`. Promocja typu niejawnego występuje operandy przed zastosowaniem operatora porównania. Operatory porównania zawsze zwracać wartości logiczne. Gdy co najmniej jeden z operandów jest `null`, wynik jest `null`.

Równość i nierówność, które są zdefiniowane dla dowolnego typu obiektu, który ma tożsamości, takie jak `Boolean` typu. Inne niż podstawowego obiektów przy użyciu tożsamości są traktowane jako równe, jeśli użytkownicy udostępniają pliki tej samej tożsamości. W poniższej tabeli wymieniono operatory porównania jednostki SQL:

|Operator|Opis|
|--------------|-----------------|
|[= (Równa się)](equals-entity-sql.md)|Porównanie równości dwóch wyrażeń.|
|[> (Większe niż)](greater-than-entity-sql.md)|Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość większą niż wyrażenie prawej krawędzi.|
|[>= (Większe niż lub równe)](greater-than-or-equal-to-entity-sql.md)|Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi.|
|[JEST \[NIE\] O WARTOŚCI NULL](isnull-entity-sql.md)|Określa, czy wyrażenie zapytania o wartości null.|
|[< (Mniejsze niż)](less-than-entity-sql.md)|Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość mniejszą niż wyrażenie prawej krawędzi.|
|[<= (Mniejsze niż lub równe)](less-than-or-equal-to-entity-sql.md)|Porównuje dwa wyrażenia, aby ustalić, czy lewe wyrażenie ma wartość mniejszą niż lub równe wyrażenie prawej krawędzi.|
|[\[NIE\] BETWEEN](between-entity-sql.md)|Określa, czy wynikiem wyrażenia wartości w określonym zakresie.|
|[\!= (Nie równa się)](not-equal-to-entity-sql.md)|Porównuje dwa wyrażenia w celu określenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi.|
|[\[NIE\] NP.](like-entity-sql.md)|Określa, czy dany ciąg znaków pasuje do określonego wzorca.|

## <a name="logical-and-case-expression-operators"></a>Operatory wyrażeń logicznych i wielkości liter

Operatory logiczne przetestować prawdziwość tego warunku. Wyrażenie CASE obliczenie zestawu wyrażeń logicznych w celu określenia wyniku. W poniższej tabeli wymieniono operatory wyrażeń logicznych i wielkości liter:

|Operator|Opis|
|--------------|-----------------|
|[& & (Operator logiczny oraz)](and-entity-sql.md)|Operatora logicznego AND.|
|[\! (Logiczne NOT)](not-entity-sql.md)|Logiczne NOT.|
|[&#124;&#124;(Operator logiczny lub)](or-entity-sql.md)|Logiczne OR.|
|[CASE](case-entity-sql.md)|Obliczenie zestawu wyrażeń logicznych w celu określenia wyniku.|
|[THEN](then-entity-sql.md)|Wynik [podczas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387119(v=vs.100)) klauzuli, gdy jest spełniony.|

## <a name="query-operators"></a>Operatory zapytań

Operatory zapytań są używane do definiowania wyrażeń zapytania, które zwracają dane jednostki. W poniższej tabeli wymieniono operatory zapytań:

|Operator|Zastosowanie|
|--------------|---------|
|[FROM](from-entity-sql.md)|Określa kolekcję, która jest używana w [wybierz](select-entity-sql.md) instrukcji.|
|[GROUP BY](group-by-entity-sql.md)|Określa grupy, do których obiektów, które zwróconych przez zapytanie ([wybierz](select-entity-sql.md)) wyrażenie, które mają być umieszczone.|
|[GroupPartition](grouppartition-entity-sql.md)|Zwraca kolekcję wartości argumentu, przewidywany wyłączanie partycji grupy, do którego odnosi się agregacji.|
|[HAVING](having-entity-sql.md)|Określa warunek wyszukiwania dla grupy lub agregacji.|
|[LIMIT](limit-entity-sql.md)|Używane z [ORDER BY](order-by-entity-sql.md) klauzuli, która wykonano, fizyczne stronicowania.|
|[ORDER BY](order-by-entity-sql.md)|Określa porządek sortowania, która jest używana na obiekty zwrócone w [wybierz](select-entity-sql.md) instrukcji.|
|[SELECT](select-entity-sql.md)|Określa elementy w projekcji, które są zwracane przez zapytanie.|
|[SKIP](skip-entity-sql.md)|Używane z [ORDER BY](order-by-entity-sql.md) klauzuli, która wykonano, fizyczne stronicowania.|
|[TOP](top-entity-sql.md)|Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania.|
|[WHERE](where-entity-sql.md)|Warunkowo filtruje danych zwracanych przez zapytanie.|

## <a name="reference-operators"></a>Odwołanie do operatorów

Odwołanie jest wskaźnikiem logiczne (z kluczem obcym) do określonej jednostki w zestawie określonej jednostki. Jednostka SQL obsługuje następujące operatory do konstruowania, dekonstruować i nawigowanie po odwołania:

|Operator|Zastosowanie|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Tworzy odwołania do jednostki w zestawie jednostek.|
|[DEREF](deref-entity-sql.md)|Wyłuskań, wartość odniesienia i generuje wyłuskania wynik tego obiektu.|
|[KEY](key-entity-sql.md)|Wyodrębnia klucz referencyjnego lub wyrażenie jednostki.|
|[NAVIGATE](navigate-entity-sql.md)|Pozwala na przechodzenie przez relację typu jeden jednostki do innej|
|[REF](ref-entity-sql.md)|Zwraca odwołanie do wystąpienia jednostki.|

## <a name="set-operators"></a>Operatory zestawu

Jednostka SQL oferuje różne operacje bogaty zestaw. Obejmuje to podobne do operatorów języka Transact-SQL, takich jak UNION, INTERSECT i EXCEPT, operatorów i EXISTS. Jednostka SQL obsługuje również operatory wyeliminowania zduplikowanych (SET), członkostwo w testowania (ruch PRZYCHODZĄCY) i sprzężenia (POŁĄCZ). W poniższej tabeli wymieniono operatory zestawów jednostek SQL:

|Operator|Zastosowanie|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Wyodrębnia element z kolekcji wielowartościowych.|
|[EXCEPT](except-entity-sql.md)|Zwraca kolekcję wszystkie unikatowe wartości w wyrażeniu zapytania do lewego operandu EXCEPT, które również nie są zwracane po prawej stronie operandu EXCEPT wyrażenia zapytania.|
|[\[NIE\] EXISTS](exists-entity-sql.md)|Określa, czy kolekcja jest pusta.|
|[FLATTEN](flatten-entity-sql.md)|Konwertuje kolekcję spłaszczonych kolekcją kolekcji.|
|[\[NIE\] W](in-entity-sql.md)|Określa, czy wartość pasuje do dowolnej wartości w kolekcji.|
|[INTERSECT](intersect-entity-sql.md)|Zwraca kolekcję różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej stronie operandu INTERSECT.|
|[OVERLAPS](overlaps-entity-sql.md)|Określa, czy dwie kolekcje mają wspólne elementy.|
|[SET](set-entity-sql.md)|Używana do konwersji kolekcji obiektów do zestawu, reaguje nową kolekcję z wszystkie zduplikowane usunięte elementy.|
|[UNION](union-entity-sql.md)|Scala wyniki dwóch lub więcej zapytań w jednej kolekcji.|

## <a name="type-operators"></a>Operatory typu

Jednostka SQL udostępnia operacje, które zezwala na typ wyrażenia (wartość) skonstruowane, zapytania i modyfikować. W poniższej tabeli wymieniono operatory, które są używane do pracy z typami:

|Operator|Zastosowanie|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Konwertuje wyrażenie jednego typu danych do innego.|
|[COLLECTION](collection-entity-sql.md)|Używane w [funkcja](function-entity-sql.md) operację, aby zadeklarować kolekcją typów jednostek lub złożonych typów.|
|[JEST \[NIE\] OF](isof-entity-sql.md)|Określa, czy typ wyrażenia jest określonego typu lub jednego z jego podtypy.|
|[OFTYPE](oftype-entity-sql.md)|Zwraca kolekcję obiektów z wyrażenie zapytania, które jest określonego typu.|
|[Konstruktor typu nazwanego](named-type-constructor-entity-sql.md)|Używane do tworzenia wystąpień typów jednostek lub złożonych typów.|
|[MULTISET](multiset-entity-sql.md)|Tworzy wystąpienie zestawu wielokrotnego na podstawie listy wartości.|
|[ROW](row-entity-sql.md)|Tworzy rekordy anonimowe, strukturalnie wpisane z co najmniej jedną wartość.|
|[TREAT](treat-entity-sql.md)|Traktuje obiektu określonego typu podstawowego, jako obiekt określonego typu pochodnego.|

## <a name="other-operators"></a>Inne operatory

W poniższej tabeli wymieniono innych operatorów jednostki SQL:

|Operator|Zastosowanie|
|--------------|---------|
|[+ (Łączenie ciągów)](string-concatenation-entity-sql.md)|Umożliwia łączenie ciągów w języku SQL jednostki.|
|[. (Dostęp do elementu członkowskiego)](member-access-entity-sql.md)|Umożliwia dostęp do wartości właściwości lub pola wystąpienia typu modelu koncepcyjnego strukturalnych.|
|[-- (Komentarz)](comment-entity-sql.md)|Dodawać komentarze do jednostki SQL.|
|[FUNCTION](function-entity-sql.md)|Definiuje wbudowanej funkcji, która może być wykonywana w kwerendzie SQL jednostki.|

## <a name="see-also"></a>Zobacz także

- [Jednostki języka SQL](entity-sql-language.md)
