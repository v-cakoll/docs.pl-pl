---
title: Podstawy wyrażenia zapytania (LINQ w C#)
description: Wprowadza pojęcia związane z wyrażenia zapytania
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 96ef75fe702e60eaa38acef77a73a5ea7f2076f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709120"
---
# <a name="query-expression-basics"></a>Podstawowe informacje o w wyrażeniach zapytań

W tym artykule przedstawiono podstawowe pojęcia związane z wyrażenia zapytań w języku C#.

## <a name="what-is-a-query-and-what-does-it-do"></a>Co to jest zapytanie, a czego?

A *zapytania* to zbiór instrukcji w tym artykule opisano, jakie dane mają być pobranie z danego źródła danych (lub źródła) i jakie kształt i organizacji mają zwracanych danych. Zapytanie różni się od wyników, które tworzy.

Ogólnie rzecz biorąc źródło danych jest zorganizowana logicznie jako sekwencję elementów tego samego rodzaju. Na przykład w tabeli bazy danych SQL zawiera sekwencję wierszy. W pliku XML ma "kolejność" elementów XML (mimo że są one zorganizowane hierarchicznie w postaci struktury drzewiastej). Kolekcja w pamięci zawiera sekwencję obiektów.

Z punktu widzenia aplikacji określonego typu i struktury oryginalnych danych źródłowych nie jest ważna. Aplikacja zawsze widzi źródło danych jako <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601> kolekcji. Na przykład w składniku LINQ to XML, źródło danych jest widoczny jako `IEnumerable` \< <xref:System.Xml.Linq.XElement>>.

Biorąc pod uwagę tę sekwencję źródła, zapytanie może wykonaj jedną z trzy rzeczy:

- Pobrać podzbiór elementów, aby utworzyć nową sekwencję bez modyfikowania poszczególnych elementów. Zapytanie może sortowanie i grupowanie zwracanej sekwencji na różne sposoby, jak pokazano w poniższym przykładzie (przyjęto założenie, `scores` jest `int[]`):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Pobierają sekwencję elementów, jak w poprzednim przykładzie, ale przekształcanie ich pod kątem nowego typu obiektu. Na przykład zapytanie może pobierać tylko nazwiska z niektórych rekordów klientów w źródle danych. Lub może pobrać pełnego rekordu, a następnie używania jej do utworzenia innego typu obiektu w pamięci, a nawet danych XML przed wygenerowaniem sekwencji wynik końcowy. W poniższym przykładzie pokazano projekcji z `int` do `string`. Należy pamiętać, nowy typ `highScoresQuery`.

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Pobrać wartości pojedynczego wystąpienia o źródle danych, takich jak:

  - Liczba elementów, które odpowiadają określony warunek.

  - Element, który ma największą lub najmniejszą wartość.

  - Pierwszy element, który dopasowuje warunek lub Suma wartości określonej w określonym zestawie elementów. Na przykład, następujące zapytanie zwraca liczbę wyniki większy niż 80 z `scores` tablicy liczb całkowitych:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    W poprzednim przykładzie, zwróć uwagę na użycie nawiasów wokół wyrażenia zapytania przed wywołaniem do `Count` metody. Można to również wyrazić przy użyciu nowej zmiennej do przechowywania konkretnego wyniku. Ta technika jest bardziej czytelny, ponieważ zmienna, która przechowuje zapytanie utrzymuje oddzielnie od zapytania, które zapisuje wynik.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

W poprzednim przykładzie zapytanie jest wykonywane w wywołaniu `Count`, ponieważ `Count` musi iterację w wynikach w celu ustalenia liczby elementów zwracanych przez `highScoresQuery`.

## <a name="what-is-a-query-expression"></a>Co to jest wyrażenie zapytania?

A *wyrażeniu zapytania* jest zapytaniem wyrażone w składni zapytań. Wyrażenie kwerendy jest staje się konstrukcją języka. Jest tak jak dowolne inne wyrażenie i mogą być używane w dowolnym kontekście, w którym wyrażenie języka C# jest poprawna. Wyrażenie zapytania zawiera zestaw klauzul napisane w składni deklaratywnej podobne do bazy danych SQL lub XQuery. Każdej klauzuli z kolei zawiera jeden lub więcej wyrażeń języka C# i wyrażenia te same jest wyrażenie zapytania lub zawiera wyrażenie zapytania.

Wyrażenie zapytania musi zaczynać się od [z](../language-reference/keywords/from-clause.md) klauzuli i musi kończyć się znakiem [wybierz](../language-reference/keywords/select-clause.md) lub [grupy](../language-reference/keywords/group-clause.md) klauzuli. Między pierwszą `from` klauzuli i ostatnią `select` lub `group` klauzuli może zawierać co najmniej jedną z klauzul opcjonalne: [gdzie](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [sprzężenia ](../language-reference/keywords/join-clause.md), [umożliwiają](../language-reference/keywords/let-clause.md) i nawet dodatkowe [z](../language-reference/keywords/from-clause.md) klauzul. Można również użyć [do](../language-reference/keywords/into.md) — słowo kluczowe, aby umożliwić wynik `join` lub `group` klauzula, która będzie służyć jako źródło dla klauzule dodatkowe kwerendy w jednym wyrażeniu zapytania.

### <a name="query-variable"></a>Zmienna zapytania

W programie LINQ, zmienna zapytania jest jakakolwiek zmienna, która przechowuje *zapytania* zamiast *wyniki* zapytania. Dokładniej mówiąc, zmienna zapytania jest zawsze typem wyliczalny, który powoduje wygenerowanie sekwencji elementów, gdy jest powtarzana w `foreach` instrukcji lub bezpośrednie wywołanie do jego `IEnumerator.MoveNext` metody.

Poniższy przykład kodu pokazuje wyrażenie prostego zapytania z jednego źródła danych, jedną klauzulę filtrowania, jedną klauzulę szeregowania i nie przekształcania elementy źródłowe. `select` Klauzuli kończy się zapytania.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

W poprzednim przykładzie `scoreQuery` jest *zmienna zapytania* którego jest czasami określane jako po prostu *zapytania*. Zmienna kwerendy przechowuje nie danych rzeczywisty wynik, który jest generowany w `foreach` pętli. I kiedy `foreach` wykonaniu instrukcji, wyniki zapytania nie są zwracane przez zmienna zapytania `scoreQuery`. Przeciwnie, są zwracane za pośrednictwem zmiennej iteracji `testScore`. `scoreQuery` Zmiennej może być postanowiliśmy na sekundę `foreach` pętli. Te same wyniki powoduje wygenerowanie tak długo, jak ten plik ani źródła danych został zmodyfikowany.

Zmienna zapytania mogą być przechowywane zapytania, które są jest wyrażone w składni zapytań lub składnia metody lub kombinacji obu. W poniższych przykładach zarówno `queryMajorCities` i `queryMajorCities2` zmiennych kwerendy:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Z drugiej strony dwa poniższe przykłady pokazują zmiennych, które nie są zmiennych kwerendy, mimo że każdy jest inicjowany za pomocą zapytania. Nie są one zmiennych kwerendy, ponieważ są przechowywane wyniki:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Aby uzyskać więcej informacji o różnych sposobach express zapytań, zobacz [składnia zapytania i metody w technologii LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Jawne i niejawne, wpisując zmiennych zapytania

Ta dokumentacja zawiera zazwyczaj jawnego typu zmiennej zapytania aby pokazać relację typ zmiennej zapytania i [klauzuli select](../language-reference/keywords/select-clause.md). Jednak możesz również użyć [var](../language-reference/keywords/var.md) — słowo kluczowe, aby poinstruować kompilator wywnioskuje typ zmiennej zapytania (lub dowolnej zmiennej lokalnej) w czasie kompilacji. Na przykład przykład zapytania, które zostało przedstawione wcześniej w tym temacie mogą być wyrażone przy użyciu niejawnego wpisywania:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typów w składniku LINQ zapytania operacje](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

### <a name="starting-a-query-expression"></a>Uruchamianie wyrażenia zapytania

Wyrażenie zapytania musi zaczynać się od `from` klauzuli. Określa źródło danych, wraz z zmiennej zakresu. Zmienna zakresu reprezentuje każdy element w sekwencji źródłowej, jak linia sekwencji źródłowej. Zmienna zakresu jest silnie typizowane w oparciu o typ elementów w źródle danych. W poniższym przykładzie ponieważ `countries` jest tablicą `Country` obiektów, jako również jest wpisana zmienna zakresu `Country`. Ponieważ zmienna zakresu zdecydowanie jest wpisane, można użyć operatora kropki wszystkie dostępne elementy członkowskie tego typu dostępu do.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Zmienna zakresu znajduje się w zakresie aż zapytanie zostanie zakończone, przy użyciu średnika lub za pomocą *kontynuacji* klauzuli.

Wyrażenie zapytania może zawierać więcej niż jednego `from` klauzul. Użyj dodatkowych `from` klauzule podczas każdego elementu w sekwencji źródłowej jest kolekcją lub zawiera kolekcję. Na przykład załóżmy, że masz kolekcję `Country` obiektów, z których każdy zawiera zbiór `City` obiektów o nazwie `Cities`. Aby wykonać zapytanie `City` obiektów w każdym `Country`, użyj dwóch `from` klauzul, jak pokazano poniżej:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Aby uzyskać więcej informacji, zobacz [klauzuli from](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Zakończenie wyrażenia zapytania

Wyrażenie zapytania musi kończyć się albo `group` klauzuli lub `select` klauzuli.

#### <a name="group-clause"></a>group — Klauzula

Użyj `group` klauzuli, która generuje sekwencję grupy organizowane według klucza, który określisz. Klucz może być dowolnego typu danych. Na przykład, następujące zapytanie powoduje utworzenie sekwencji grupy, która zawiera co najmniej jeden `Country` obiektów i którego klucza `char` wartość.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Aby uzyskać więcej informacji na temat grupowania, zobacz [group — klauzula](../language-reference/keywords/group-clause.md).

#### <a name="select-clause"></a>select — Klauzula

Użyj `select` klauzuli do tworzenia innych typów sekwencji. Prosty `select` klauzuli po prostu tworzy sekwencję tego samego typu obiekty jako obiekty, które są zawarte w źródle danych. W tym przykładzie źródło danych zawiera `Country` obiektów. `orderby` Klauzuli sortuje tylko elementy do nowego zamówienia i `select` klauzuli wytwarza sekwencję zmieniona kolejność `Country` obiektów.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

`select` Klauzuli może służyć do przekształcania danych źródłowych sekwencji nowych typów. Ta transformacja jest również określany *projekcji*. W poniższym przykładzie `select` klauzuli *projektów* sekwencję typy anonimowe, która zawiera tylko podzbiór pól w oryginalnym elemencie. Należy pamiętać, że nowe obiekty są inicjowane za pomocą inicjatora obiektów.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Aby uzyskać więcej informacji na temat wszystkich metod, `select` można używać klauzuli przetwarzają dane źródłowe, zobacz [klauzuli select](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>Kontynuacje za pomocą "do"

Możesz użyć `into` — słowo kluczowe w `select` lub `group` klauzuli można utworzyć tymczasowego identyfikatora, która przechowuje zapytanie. W tym przypadku należy wykonać dodatkowe operacje w zapytaniu po grupowanie lub wybierz operację. W poniższym przykładzie `countries` są pogrupowane według populacji w zakresach 10 milionów. Po tych grup zostaną utworzone, dodatkowe klauzul filtru się niektóre grupy, a następnie do sortowania grupy w kolejności rosnącej kolejności. Aby wykonać te operacje dodatkowe, kontynuacja reprezentowany przez `countryGroup` jest wymagana.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Aby uzyskać więcej informacji, zobacz [do](../language-reference/keywords/into.md).

### <a name="filtering-ordering-and-joining"></a>Filtrowanie, porządkowanie i dołączania

Między rozpoczęciem `from` klauzula i zakończenie `select` lub `group` klauzuli, inne klauzule (`where`, `join`, `orderby`, `from`, `let`) są opcjonalne. Dowolne opcjonalne klauzule mogą być używane zero lub wiele razy w treść zapytania.

#### <a name="where-clause"></a>Klauzula where

Użyj `where` klauzulę, aby odfiltrować elementy ze źródła danych oparte na co najmniej jednego wyrażenia predykatu. `where` Klauzula w poniższym przykładzie zawiera jeden predykat z dwóch warunków.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>Klauzula orderby

Użyj `orderby` klauzulę, aby posortować wyniki w kolejności rosnącej lub malejącej. Można również określić, pomocniczej sortowania. Poniższy przykład sortuje podstawowego `country` obiektów przy użyciu `Area` właściwości. Następnie wykonuje dodatkowej sortowanie za pomocą `Population` właściwości.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

`ascending` — Słowo kluczowe jest opcjonalny; jest domyślny porządek sortowania, jeśli określono żadnej kolejności. Aby uzyskać więcej informacji, zobacz [klauzuli orderby](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>Klauzula join

Użyj `join` klauzuli, aby skojarzyć i/lub połączyć elementy z jednego źródła danych z elementów z innego źródła danych oparte na porównanie równości pomiędzy kluczami określony w każdym elemencie. W programie LINQ sprzężenia operacje są wykonywane w sekwencji, której elementy są różnych typów obiektów. Po dołączeniu dwóch sekwencji, należy użyć `select` lub `group` instrukcję, aby określić który element do przechowywania w sekwencji wyjścia. Można również użyć typu anonimowego do łączenia z każdego zestawu powiązanych elementów właściwości w nowy typ sekwencji wyjścia. W poniższym przykładzie `prod` obiekty, których `Category` właściwość odpowiada jednej z kategorii w `categories` tablicy ciągów. Produkty którego `Category` jest niezgodna z dowolnym ciągiem w `categories` są odfiltrowywane. `select` Instrukcji projektów nowego typu, którego właściwości są pobierane z obu `cat` i `prod`.

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Sprzężenie grupy można również wykonać, przechowując wyniki `join` operacji w zmiennej tymczasowej, za pomocą [do](../language-reference/keywords/into.md) — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [klauzuli join](../language-reference/keywords/join-clause.md).

#### <a name="let-clause"></a>Klauzula Let 

Użyj `let` klauzuli, aby przechowywać wynik wyrażenia, takie jak wywołanie metody w nowej zmiennej zakresu. W poniższym przykładzie zmienna zakresu `firstName` przechowuje pierwszego elementu w tablicy ciągów, które są zwracane przez `Split`.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Aby uzyskać więcej informacji, zobacz [let, klauzula](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Podzapytania w wyrażeniu zapytania

Sam klauzula zapytania może zawierać wyrażenie zapytania, który jest czasem nazywany *podzapytania*. Każdy podzapytania zaczyna się od jego własnej `from` klauzula, która nie musi wskazywać tego samego źródła danych w pierwszym `from` klauzuli. Na przykład poniższe zapytanie pokazuje wyrażenie zapytania, które jest używane w instrukcji select, aby pobrać wyniki operacji grupowania.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Aby uzyskać więcej informacji, zobacz [porady: wykonanie podzapytania w operacji grupowania](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania C#](../programming-guide/index.md)
- [Language Integrated Query (LINQ)](index.md)
- [Słowa kluczowe zapytania (LINQ)](../language-reference/keywords/query-keywords.md)
- [Omówienie operatorów standardowej kwerendy](../programming-guide/concepts/linq/standard-query-operators-overview.md)
