---
title: Podstawy wyrażeń zapytań (LINQ w języku C#)
description: Wprowadza pojęcia związane z wyrażeniami kwerend
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 83beaa82d4b4b42ff9da5230edddd391b33a0717
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173357"
---
# <a name="query-expression-basics"></a>Podstawowe informacje o wyrażeniach zapytań

W tym artykule przedstawiono podstawowe pojęcia związane z wyrażeniami kwerend w języku C#.

## <a name="what-is-a-query-and-what-does-it-do"></a>Co to jest zapytanie i co robi?

*Kwerenda* to zestaw instrukcji opisujących, jakie dane pobrać z danego źródła danych (lub źródeł) oraz jaki kształt i organizację powinny mieć zwrócone dane. Kwerenda różni się od wyników, które generuje.

Ogólnie rzecz biorąc dane źródłowe jest zorganizowana logicznie jako sekwencja elementów tego samego rodzaju. Na przykład tabela bazy danych SQL zawiera sekwencję wierszy. W pliku XML istnieje "sekwencja" elementów XML (chociaż są one zorganizowane hierarchicznie w strukturze drzewa). Kolekcja w pamięci zawiera sekwencję obiektów.

Z punktu widzenia aplikacji określony typ i struktura oryginalnych danych źródłowych nie jest ważna. Aplikacja zawsze widzi dane <xref:System.Collections.Generic.IEnumerable%601> źródłowe <xref:System.Linq.IQueryable%601> jako lub kolekcji. Na przykład w LINQ do XML dane źródłowe `IEnumerable` \< <xref:System.Xml.Linq.XElement> są widoczne jako>.

Biorąc pod uwagę tę sekwencję źródłową, kwerenda może wykonać jedną z trzech czynności:

- Pobierz podzbiór elementów, aby utworzyć nową sekwencję bez modyfikowania poszczególnych elementów. Kwerenda może następnie sortować lub grupować zwróconą sekwencję na `scores` różne `int[]`sposoby, jak pokazano w poniższym przykładzie (przyzałożeniu, że jest):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Pobierz sekwencję elementów, jak w poprzednim przykładzie, ale przekształcić je do nowego typu obiektu. Na przykład kwerenda może pobrać tylko nazwiska z niektórych rekordów klientów w źródle danych. Lub może pobrać pełny rekord, a następnie użyć go do skonstruowania innego typu obiektu w pamięci lub nawet danych XML przed wygenerowaniem końcowej sekwencji wyników. W poniższym przykładzie przedstawiono `int` projekcję od . `string` Zwróć uwagę `highScoresQuery`na nowy typ pliku .

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Pobierz wartość singleton o danych źródłowych, takich jak:

  - Liczba elementów, które pasują do pewnego warunku.

  - Element, który ma największą lub najmniejszą wartość.

  - Pierwszy element, który pasuje do warunku lub suma określonych wartości w określonym zestawie elementów. Na przykład następująca kwerenda zwraca liczbę wyników `scores` większą niż 80 z tablicy całkowitej:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    W poprzednim przykładzie należy zwrócić uwagę na użycie nawiasów wokół wyrażenia `Count` kwerendy przed wywołaniem metody. Można również wyrazić to za pomocą nowej zmiennej do przechowywania wynik betonu. Ta technika jest bardziej czytelny, ponieważ utrzymuje zmienną, która przechowuje kwerendę oddzielnie od kwerendy, która przechowuje wynik.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

W poprzednim przykładzie kwerenda jest wykonywana `Count`w `Count` wywołaniu , ponieważ musi iterate nad wynikami `highScoresQuery`w celu określenia liczby elementów zwracanych przez .

## <a name="what-is-a-query-expression"></a>Co to jest wyrażenie zapytania?

*Wyrażenie kwerendy* jest kwerendą wyrażoną w składni kwerendy. Wyrażenie zapytania jest konstrukcją języka pierwszej klasy. Jest tak jak każde inne wyrażenie i może być używany w dowolnym kontekście, w którym wyrażenie C# jest prawidłowy. Wyrażenie kwerendy składa się z zestawu klauzul zapisanych w składni deklaratywnej podobnej do SQL lub XQuery. Każda klauzula z kolei zawiera co najmniej jedno wyrażenie C#, a te wyrażenia mogą być wyrażeniem kwerendy lub zawierać wyrażenie kwerendy.

Wyrażenie kwerendy musi zaczynać się od klauzuli [from](../language-reference/keywords/from-clause.md) i musi kończyć się klauzulą [select](../language-reference/keywords/select-clause.md) lub [group.](../language-reference/keywords/group-clause.md) Między `from` pierwszą klauzulą `select` `group` a ostatnią lub klauzulą może zawierać jedną lub więcej z tych klauzul opcjonalnych: [gdzie](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [join](../language-reference/keywords/join-clause.md), [niech,](../language-reference/keywords/let-clause.md) a nawet dodatkowe [z](../language-reference/keywords/from-clause.md) klauzul. Można również użyć [do](../language-reference/keywords/into.md) słowa kluczowego, `join` `group` aby włączyć wynik lub klauzuli służyć jako źródło dodatkowych klauzul kwerendy w tym samym wyrażeniu kwerendy.

### <a name="query-variable"></a>Zmienna kwerendy

W LINQ zmiennej kwerendy jest dowolna zmienna, która przechowuje *kwerendę* zamiast *wyników* kwerendy. W szczególności zmienna kwerendy jest zawsze wyliczalny typ, który będzie generować sekwencję elementów, gdy jest iterowany w `foreach` instrukcji lub bezpośrednie wywołanie jego `IEnumerator.MoveNext` metody.

Poniższy przykład kodu przedstawia proste wyrażenie kwerendy z jednym źródłem danych, jedną klauzulą filtrowania, jedną klauzulą porządkową i bez przekształcania elementów źródłowych. Klauzula `select` kończy kwerendę.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

W poprzednim przykładzie `scoreQuery` jest *zmienna zapytania,* która jest czasami określana jako tylko *kwerenda*. Zmienna kwerendy przechowuje żadnych rzeczywistych danych `foreach` wyników, który jest produkowany w pętli. A gdy `foreach` instrukcja jest wykonywana, wyniki kwerendy `scoreQuery`nie są zwracane za pośrednictwem zmiennej kwerendy . Są one raczej zwracane za pośrednictwem zmiennej `testScore`iteracji . Zmienna `scoreQuery` może być iterowana `foreach` w drugiej pętli. Będzie produkować takie same wyniki, tak długo, jak ani ona, ani źródło danych nie został zmodyfikowany.

Zmienna kwerendy może przechowywać kwerendę wyrażoną w składni kwerendy lub składni metody lub kombinację tych dwóch. W poniższych przykładach `queryMajorCities` `queryMajorCities2` oba i są zmienne zapytania:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Z drugiej strony w poniższych dwóch przykładach przedstawiono zmienne, które nie są zmienne kwerendy, mimo że każdy jest inicjowany za pomocą kwerendy. Nie są one zmienne kwerendy, ponieważ przechowują wyniki:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Aby uzyskać więcej informacji na temat różnych sposobów wyrażania zapytań, zobacz [Składnia kwerendy i składnia metody w pliku LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Jawne i niejawne wpisywanie zmiennych zapytania

Ta dokumentacja zwykle zawiera jawny typ zmiennej kwerendy w celu wyświetlenia relacji typu między zmienną kwerendy a [klauzulą select](../language-reference/keywords/select-clause.md). Jednak można również użyć [var](../language-reference/keywords/var.md) słowa kluczowego, aby poinstruować kompilator, aby wywnioskować typ zmiennej kwerendy (lub dowolnej innej zmiennej lokalnej) w czasie kompilacji. Na przykład przykład kwerendy, który został pokazany wcześniej w tym temacie można również wyrazić za pomocą niejawnego wpisywania:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [Relacje typu w operacjach kwerend LINQ](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

### <a name="starting-a-query-expression"></a>Rozpoczynanie wyrażenia kwerendy

Wyrażenie kwerendy musi `from` zaczynać się od klauzuli. Określa źródło danych wraz ze zmienną zakresu. Zmienna zakresu reprezentuje każdy kolejny element w sekwencji źródłowej, gdy sekwencja źródłowa jest przemierzana. Zmienna zakresu jest silnie typizowany na podstawie typu elementów w źródle danych. W poniższym przykładzie, ponieważ `countries` `Country` jest tablicą obiektów, zmienna `Country`zakresu jest również wpisana jako . Ponieważ zmienna zakresu jest silnie typizona, można użyć operatora kropki, aby uzyskać dostęp do wszystkich dostępnych elementów członkowskich tego typu.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Zmienna zakresu znajduje się w zakresie, dopóki kwerenda nie zostanie zakończona średnikiem lub klauzulą *kontynuacji.*

Wyrażenie kwerendy może `from` zawierać wiele klauzul. Użyj `from` dodatkowych klauzul, gdy każdy element w sekwencji źródłowej jest sama kolekcja lub zawiera kolekcję. Załóżmy na przykład, że `Country` masz kolekcję obiektów, `City` z `Cities`których każdy zawiera kolekcję obiektów o nazwie . Aby zbadać `City` obiekty `Country`w `from` każdym z nich, należy użyć dwóch klauzul, jak pokazano poniżej:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Aby uzyskać więcej informacji, zobacz [z klauzuli](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Kończenie wyrażenia kwerendy

Wyrażenie kwerendy musi kończyć `group` się `select` klauzulą lub klauzulą.

#### <a name="group-clause"></a>group — Klauzula

Klauzula `group` służy do tworzenia sekwencji grup zorganizowanych według klucza, który określisz. Kluczem może być dowolny typ danych. Na przykład następująca kwerenda tworzy sekwencję grup, która zawiera jeden lub więcej `Country` obiektów i których klucz jest wartością. `char`

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Aby uzyskać więcej informacji na temat grupowania, zobacz [klauzulę grupy](../language-reference/keywords/group-clause.md).

#### <a name="select-clause"></a>select — Klauzula

Użyj `select` klauzuli do tworzenia wszystkich innych typów sekwencji. Prosta `select` klauzula po prostu tworzy sekwencję tego samego typu obiektów jako obiekty, które są zawarte w źródle danych. W tym przykładzie źródło `Country` danych zawiera obiekty. Klauzula `orderby` po prostu sortuje elementy `select` w nowej kolejności i klauzula `Country` tworzy sekwencję obiektów o zmianach kolejności.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

Klauzula `select` może służyć do przekształcania danych źródłowych w sekwencje nowych typów. Ta transformacja jest również nazywana *projekcją*. W poniższym przykładzie `select` klauzula *wyświetla* sekwencję typów anonimowych, która zawiera tylko podzbiór pól w oryginalnym elemencie. Należy zauważyć, że nowe obiekty są inicjowane przy użyciu inicjatora obiektów.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Aby uzyskać więcej informacji na `select` temat wszystkich sposobów, że klauzula może służyć do przekształcania danych źródłowych, zobacz [select klauzuli](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>Kontynuacje z "w"

Słowo kluczowe `into` w `select` lub `group` klauzuli można użyć do utworzenia tymczasowego identyfikatora, który przechowuje kwerendę. Należy to zrobić, gdy należy wykonać dodatkowe operacje kwerendy na kwerendzie po grupowaniu lub wybierz operację. W poniższym `countries` przykładzie są pogrupowane według populacji w zakresie 10 milionów. Po utworzeniu tych grup dodatkowe klauzule odfiltrowują niektóre grupy, a następnie sortują grupy w porządku rosnącym. Aby wykonać te dodatkowe operacje, `countryGroup` wymagana jest kontynuacja reprezentowana przez.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Aby uzyskać więcej informacji, zobacz [w](../language-reference/keywords/into.md).

### <a name="filtering-ordering-and-joining"></a>Filtrowanie, zamawianie i dołączanie

Między `from` klauzulą początkową `select` a `group` zakończeniem lub klauzulą`where` `join`wszystkie `orderby` `from`inne `let`klauzule ( , , , , ) są opcjonalne. Dowolna z klauzul opcjonalnych może być używana zero razy lub wiele razy w treści kwerendy.

#### <a name="where-clause"></a>Klauzula where

Klauzula `where` służy do filtrowania elementów z danych źródłowych na podstawie jednego lub więcej wyrażeń predykatu. Klauzula `where` w poniższym przykładzie ma jeden predykat z dwoma warunkami.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>Klauzula orderby

Użyj `orderby` klauzuli, aby posortować wyniki w kolejności rosnącej lub malejącej. Można również określić dodatkowe zamówienia sortowania. Poniższy przykład wykonuje sortowanie podstawowe `country` na obiektach przy użyciu `Area` właściwości. Następnie wykonuje sortowanie pomocnicze przy `Population` użyciu właściwości.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

Słowo `ascending` kluczowe jest opcjonalne; jest to domyślna kolejność sortowania, jeśli nie określono żadnej kolejności. Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>Klauzula join

Klauzula `join` służy do kojarzenia i/lub łączenia elementów z jednego źródła danych z elementami z innego źródła danych na podstawie porównania równości między określonymi kluczami w każdym elemencie. W LINQ operacje sprzężenia są wykonywane na sekwencje obiektów, których elementy są różne typy. Po połączeniu dwóch sekwencji należy użyć `select` `group` lub instrukcji, aby określić, który element do przechowywania w sekwencji wyjściowej. Można również użyć typu anonimowego, aby połączyć właściwości z każdego zestawu skojarzonych elementów do nowego typu dla sekwencji wyjściowej. Poniższy przykład kojarzy `prod` `Category` obiekty, których właściwość pasuje `categories` do jednej z kategorii w tablicy ciągów. Produkty, `Category` których nie pasuje `categories` do żadnego ciągu w są filtrowane. Instrukcja `select` projektuje nowy typ, którego `cat` właściwości `prod`są pobierane z obu i .

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Można również wykonać sprzężenie grupy, przechowując wyniki `join` operacji w zmiennej tymczasowej przy użyciu słowa kluczowego [Into.](../language-reference/keywords/into.md) Aby uzyskać więcej informacji, zobacz [klauzulę join .](../language-reference/keywords/join-clause.md)

#### <a name="let-clause"></a>Klauzula Let

Klauzula `let` służy do przechowywania wyniku wyrażenia, takiego jak wywołanie metody, w nowej zmiennej zakresu. W poniższym przykładzie zmienna `firstName` zakresu przechowuje pierwszy element tablicy ciągów, który jest zwracany przez `Split`.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Aby uzyskać więcej informacji, zobacz [klauzulę let](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Podkwerendy w wyrażeniu kwerendy

Klauzula kwerendy może zawierać wyrażenie kwerendy, które czasami jest określane jako *podkwerenda*. Każde podkwerenda rozpoczyna `from` się od własnej klauzuli, która `from` niemusi wskazywać na to samo źródło danych w pierwszej klauzuli. Na przykład poniższa kwerenda pokazuje wyrażenie kwerendy, który jest używany w select instrukcji, aby pobrać wyniki operacji grupowania.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Aby uzyskać więcej informacji, zobacz [Wykonywanie podkwerendy w operacji grupowania](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../programming-guide/index.md)
- [Language Integrated Query (LINQ)](index.md)
- [Słowa kluczowe zapytania (LINQ)](../language-reference/keywords/query-keywords.md)
- [Omówienie standardowych operatorów kwerend](../programming-guide/concepts/linq/standard-query-operators-overview.md)
