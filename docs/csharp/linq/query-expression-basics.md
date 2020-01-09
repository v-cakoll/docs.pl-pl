---
title: Podstawowe wyrażenie zapytania (LINQ in C#)
description: Wprowadza koncepcje związane z wyrażeniami zapytań
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 5ebe2163df47c60c677d7ac911ce0f65529835eb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635863"
---
# <a name="query-expression-basics"></a>Podstawowe informacje o wyrażeniach zapytań

W tym artykule przedstawiono podstawowe pojęcia związane z wyrażeniami zapytań C#w programie.

## <a name="what-is-a-query-and-what-does-it-do"></a>Co to jest zapytanie i co robi?

*Zapytanie* jest zestawem instrukcji, które opisują, jakie dane mają być pobierane z danego źródła danych (lub źródeł) oraz jaki kształt i organizacja powinny mieć zwrócone dane. Zapytanie różni się od wyników, które generuje.

Ogólnie rzecz biorąc, dane źródłowe są zorganizowane logicznie jako sekwencja elementów tego samego rodzaju. Na przykład tabela bazy danych SQL zawiera sekwencję wierszy. W pliku XML istnieje "sekwencja" elementów XML (chociaż są one zorganizowane hierarchicznie w strukturze drzewa). Kolekcja znajdująca się w pamięci zawiera sekwencję obiektów.

Z punktu widzenia aplikacji określony typ i struktura oryginalnych danych źródłowych nie są ważne. Aplikacja zawsze widzi dane źródłowe jako kolekcje <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>. Na przykład w LINQ to XML dane źródłowe są widoczne jako `IEnumerable`\<<xref:System.Xml.Linq.XElement>>.

Po otrzymaniu tej sekwencji źródłowej zapytanie może wykonać jedną z trzech czynności:

- Pobierz podzestaw elementów, aby utworzyć nową sekwencję bez modyfikowania poszczególnych elementów. Zapytanie może następnie posortować lub zgrupować zwracaną sekwencję na różne sposoby, jak pokazano w poniższym przykładzie (Załóżmy, `scores` jest `int[]`):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Pobierz sekwencję elementów tak jak w poprzednim przykładzie, ale Przekształć je na nowy typ obiektu. Na przykład zapytanie może pobrać tylko ostatnie nazwy z określonych rekordów klienta w źródle danych. Lub może pobrać kompletny rekord, a następnie użyć go do utworzenia innego typu obiektu w pamięci lub nawet danych XML przed wygenerowaniem końcowej sekwencji wyniku. Poniższy przykład przedstawia projekcję z `int` do `string`. Zanotuj nowy typ `highScoresQuery`.

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Pobieranie pojedynczej wartości dotyczącej danych źródłowych, takich jak:

  - Liczba elementów, które pasują do określonego warunku.

  - Element, który ma największą lub najmniejszą wartość.

  - Pierwszy element, który pasuje do warunku lub suma określonych wartości w określonym zestawie elementów. Na przykład następujące zapytanie zwraca liczbę wyników większy niż 80 z tablicy `scores` Integer:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    W poprzednim przykładzie Zwróć uwagę na użycie nawiasów wokół wyrażenia zapytania przed wywołaniem metody `Count`. Można to również wyrazić przy użyciu nowej zmiennej do przechowywania konkretnego wyniku. Ta technika jest bardziej czytelna, ponieważ utrzymuje zmienną, która przechowuje zapytanie oddzielone od zapytania, które przechowuje wynik.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

W poprzednim przykładzie zapytanie jest wykonywane w wywołaniu do `Count`, ponieważ `Count` musi wykonać iterację w wynikach w celu określenia liczby elementów zwracanych przez `highScoresQuery`.

## <a name="what-is-a-query-expression"></a>Co to jest wyrażenie zapytania?

*Wyrażenie zapytania* jest zapytaniem wyrażonym w składni zapytania. Wyrażenie zapytania jest konstrukcja języka pierwszej klasy. Jest tak samo jak w przypadku innych wyrażeń i może być używane w dowolnym kontekście, w C# którym wyrażenie jest prawidłowe. Wyrażenie zapytania składa się z zestawu klauzul pisanych w składni deklaracyjnej podobnej do SQL lub XQuery. Każda klauzula z kolei zawiera jeden lub więcej C# wyrażeń, a wyrażenia te mogą być wyrażeniem zapytania lub zawierać wyrażenie zapytania.

Wyrażenie zapytania musi rozpoczynać się [od klauzuli FROM](../language-reference/keywords/from-clause.md) i musi kończyć się klauzulą [SELECT](../language-reference/keywords/select-clause.md) lub [Group](../language-reference/keywords/group-clause.md) . Między pierwszą klauzulą `from` i ostatnią klauzulą `select` lub `group` może zawierać jedną lub więcej z następujących klauzul opcjonalnych: [gdzie](../language-reference/keywords/where-clause.md), [OrderBy](../language-reference/keywords/orderby-clause.md), [Join](../language-reference/keywords/join-clause.md), [Let](../language-reference/keywords/let-clause.md) i jeszcze więcej [z](../language-reference/keywords/from-clause.md) klauzul. Można również użyć słowa kluczowego [into](../language-reference/keywords/into.md) , aby włączyć wynik klauzuli `join` lub `group`, która będzie służyć jako źródło dodatkowych klauzul zapytania w tym samym wyrażeniu zapytania.

### <a name="query-variable"></a>Zmienna zapytania

W LINQ, zmienna zapytania to jakakolwiek zmienna, która przechowuje *zapytanie* zamiast *wyników* zapytania. Dokładniej mówiąc, zmienna zapytania jest zawsze wyliczalnym typem, który będzie generować sekwencję elementów podczas powtarzania w instrukcji `foreach` lub bezpośredniego wywołania metody `IEnumerator.MoveNext`.

Poniższy przykład kodu pokazuje proste wyrażenie zapytania z jednym źródłem danych, jedną klauzulą filtrowania, jedną klauzulą porządkowania i bez transformacji elementów źródłowych. Klauzula `select` kończąca zapytanie.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

W poprzednim przykładzie `scoreQuery` jest *zmienną zapytania,* która czasami nazywa się tylko *zapytaniem*. Zmienna zapytania nie przechowuje żadnych rzeczywistych danych wynikowych, które są generowane w pętli `foreach`. A kiedy Instrukcja `foreach` jest wykonywana, wyniki zapytania nie są zwracane przez zmienną zapytania `scoreQuery`. Zamiast tego są zwracane przez zmienną iteracji `testScore`. Zmienną `scoreQuery` można powtórzyć w drugiej pętli `foreach`. Będzie on generował te same wyniki, o ile nie został zmodyfikowany ani źródło danych.

Zmienna zapytania może przechowywać zapytanie, które jest wyrażone w składni zapytania lub składni metody lub kombinacji obu. W poniższych przykładach zarówno `queryMajorCities`, jak i `queryMajorCities2` są zmiennymi zapytań:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Z drugiej strony następujące dwa przykłady pokazują zmienne, które nie są zmiennymi, nawet jeśli każda z nich została zainicjowana za pomocą zapytania. Nie są to zmienne zapytania, ponieważ przechowują wyniki:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Aby uzyskać więcej informacji na temat różnych metod ekspresowych zapytań, zobacz [składnia zapytań i składnia metod w LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Jawne i niejawne wpisywanie zmiennych zapytania

Ta dokumentacja zazwyczaj zapewnia jawny typ zmiennej zapytania w celu wyświetlenia relacji typu między zmienną zapytania a [klauzulą SELECT](../language-reference/keywords/select-clause.md). Można jednak użyć słowa kluczowego [var](../language-reference/keywords/var.md) do nakazuje kompilatorowi wywnioskowanie typu zmiennej zapytania (lub dowolnej innej zmiennej lokalnej) w czasie kompilacji. Przykładowo przykład zapytania, który został przedstawiony wcześniej w tym temacie, można również wyrazić przy użyciu niejawnego wpisywania:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach zapytań LINQ](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

### <a name="starting-a-query-expression"></a>Uruchamianie wyrażenia zapytania

Wyrażenie zapytania musi rozpoczynać się od klauzuli `from`. Określa źródło danych ze zmienną zakresu. Zmienna zakresu reprezentuje każdy kolejny element w sekwencji źródłowej, gdy trwa przechodzenie sekwencji źródłowej. Zmienna zakresu jest silnie wpisana w oparciu o typ elementów w źródle danych. W poniższym przykładzie, ponieważ `countries` jest tablicą obiektów `Country`, zmienna zakresu jest również wpisana jako `Country`. Ponieważ zmienna zakresu jest silnie wpisana, można użyć operatora kropki w celu uzyskania dostępu do dowolnych dostępnych elementów członkowskich typu.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Zmienna zakresu znajduje się w zakresie, dopóki zapytanie nie zostanie zakończone średnikiem lub z klauzulą *kontynuacji* .

Wyrażenie zapytania może zawierać wiele klauzul `from`. Użyj dodatkowych klauzul `from`, gdy każdy element w sekwencji źródłowej jest samym kolekcją lub zawiera kolekcję. Załóżmy na przykład, że masz kolekcję obiektów `Country`, z których każdy zawiera kolekcję obiektów `City` o nazwie `Cities`. Aby zbadać `City` obiektów w każdym `Country`, użyj dwóch klauzul `from`, jak pokazano poniżej:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Aby uzyskać więcej informacji, zobacz [klauzula FROM](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Kończenie wyrażenia zapytania

Wyrażenie zapytania musi kończyć się klauzulą `group` lub klauzulą `select`.

#### <a name="group-clause"></a>group — Klauzula

Użyj klauzuli `group`, aby utworzyć sekwencję grup zorganizowanych według określonego klucza. Klucz może być dowolnego typu danych. Na przykład następujące zapytanie tworzy sekwencję grup zawierającą co najmniej jeden obiekt `Country`, którego klucz jest wartością `char`.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Aby uzyskać więcej informacji na temat grupowania, zobacz [klauzula](../language-reference/keywords/group-clause.md)Group.

#### <a name="select-clause"></a>select — Klauzula

Użyj klauzuli `select`, aby utworzyć wszystkie inne typy sekwencji. Prosta klauzula `select` tylko tworzy sekwencję tego samego typu obiektów, co obiekty, które są zawarte w źródle danych. W tym przykładzie źródło danych zawiera obiekty `Country`. Klauzula `orderby` tylko sortuje elementy do nowej kolejności, a klauzula `select` tworzy sekwencję ponownie uporządkowanych obiektów `Country`.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

Klauzula `select` może służyć do przekształcania danych źródłowych na sekwencje nowych typów. Ta transformacja jest również nazywana *projekcją*. W poniższym przykładzie klauzula `select` *projektuje* sekwencję typów anonimowych, która zawiera tylko podzestaw pól w oryginalnym elemencie. Należy pamiętać, że nowe obiekty są inicjowane za pomocą inicjatora obiektów.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Aby uzyskać więcej informacji o wszystkich sposobach używania klauzuli `select` do przekształcania danych źródłowych, zobacz SELECT — [klauzula](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>Kontynuuje od "do"

Możesz użyć słowa kluczowego `into` w klauzuli `select` lub `group`, aby utworzyć tymczasowy identyfikator, który przechowuje zapytanie. Zrób to, gdy podczas operacji grupowania lub wybierania należy wykonać dodatkowe operacje zapytania dotyczące zapytania. W poniższym przykładzie `countries` są pogrupowane według populacji w zakresach 10 000 000. Po utworzeniu tych grup dodatkowe klauzule odfiltrują niektóre grupy, a następnie sortuje grupy w kolejności rosnącej. Aby wykonać te dodatkowe operacje, wymagana jest kontynuacja reprezentowana przez `countryGroup`.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Aby uzyskać więcej informacji, zobacz [do](../language-reference/keywords/into.md).

### <a name="filtering-ordering-and-joining"></a>Filtrowanie, porządkowanie i łączenie

Między klauzulą `from` początkową i końcową `select` lub `group` wszystkie pozostałe klauzule (`where`, `join`, `orderby`, `from`, `let`) są opcjonalne. Dowolne opcjonalne klauzule mogą być używane zero razy lub wiele razy w treści zapytania.

#### <a name="where-clause"></a>Klauzula where

Użyj klauzuli `where`, aby odfiltrować elementy z danych źródłowych na podstawie jednego lub większej liczby wyrażeń predykatu. Klauzula `where` w poniższym przykładzie ma jeden predykat z dwoma warunkami.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Aby uzyskać więcej informacji, zobacz [klauzula WHERE](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>Klauzula orderby

Użyj klauzuli `orderby`, aby posortować wyniki w kolejności rosnącej lub malejącej. Można również określić pomocnicze zamówienia sortowania. Poniższy przykład wykonuje sortowanie podstawowe na `country` obiektów przy użyciu właściwości `Area`. Następnie wykonuje sortowanie pomocnicze przy użyciu właściwości `Population`.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

Słowo kluczowe `ascending` jest opcjonalne; jest to domyślna kolejność sortowania, jeśli nie określono kolejności. Aby uzyskać więcej informacji, zobacz [klauzula OrderBy](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>Klauzula join

Użyj klauzuli `join`, aby skojarzyć i/lub połączyć elementy z jednego źródła danych z elementami z innego źródła danych na podstawie porównania równości między określonymi kluczami w każdym elemencie. W LINQ, operacje Join są wykonywane na sekwencjach obiektów, których elementy są różne typy. Po dołączeniu dwóch sekwencji musisz użyć instrukcji `select` lub `group`, aby określić element, który ma być przechowywany w sekwencji wyjściowej. Można również użyć typu anonimowego, aby połączyć właściwości z każdego zestawu skojarzonych elementów do nowego typu dla sekwencji wyjściowej. Poniższy przykład kojarzy `prod` obiektów, których właściwość `Category` dopasowuje jedną z kategorii w tablicy ciągów `categories`. Produkty, których `Category` nie są zgodne z żadnym ciągiem w `categories`, są odfiltrowane. Instrukcja `select` projektuje nowy typ, którego właściwości są pobierane z obu `cat` i `prod`.

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Możesz również wykonać sprzężenie grupy, przechowując wyniki operacji `join` w zmiennej tymczasowej za pomocą słowa kluczowego [into](../language-reference/keywords/into.md) . Aby uzyskać więcej informacji, zobacz [Klauzula join](../language-reference/keywords/join-clause.md).

#### <a name="let-clause"></a>Klauzula Let 

Użyj klauzuli `let` do przechowywania wyniku wyrażenia, takiego jak wywołanie metody, w nowej zmiennej zakresu. W poniższym przykładzie zmienna zakresu `firstName` przechowuje pierwszy element tablicy ciągów zwracanych przez `Split`.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Aby uzyskać więcej informacji, zobacz [klauzula Let](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Podzapytania w wyrażeniu zapytania

Klauzula zapytania może sama zawierać wyrażenie zapytania, które jest czasami określane jako *podzapytanie*. Każde podzapytanie rozpoczyna się od własnej klauzuli `from`, która nie musi wskazywać tego samego źródła danych w pierwszej klauzuli `from`. Na przykład następujące zapytanie wyświetla wyrażenie zapytania, które jest używane w instrukcji SELECT do pobierania wyników operacji grupowania.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Aby uzyskać więcej informacji, zobacz [wykonywanie podzapytania w operacji grupowania](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../programming-guide/index.md)
- [Language Integrated Query (LINQ)](index.md)
- [Słowa kluczowe zapytania (LINQ)](../language-reference/keywords/query-keywords.md)
- [Standardowe operatory zapytań — Omówienie](../programming-guide/concepts/linq/standard-query-operators-overview.md)
