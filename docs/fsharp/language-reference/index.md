---
title: Materiały referencyjne dotyczące języka F#
description: 'Informacje o F # języka funkcji z tego odwołania tokeny języka, pojęć, typów, wyrażenia i obsługiwane przez kompilator konstrukcji tematów.'
ms.date: 05/16/2016
ms.openlocfilehash: adce37ee393673b7611ad24f385c8b8106f6ce86
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141129"
---
# <a name="f-language-reference"></a>Materiały referencyjne dotyczące języka F#

Ta sekcja jest odwołanie do języka F #, wielo paradygmowym językiem programowania przeznaczonych dla platformy .NET. Język F # obsługuje modele programowania funkcjonalnego, zorientowane obiektowo i imperatywnego.

## <a name="f-tokens"></a>Tokeny języka F #

W poniższej tabeli przedstawiono tematów odwołania, które zawierają tabele słów kluczowych, symboli i literałów używane jako tokeny w języku F #.

|Tytuł|Opis|
|-----|-----------|
|[Odwołanie do słów kluczowych](keyword-reference.md)|Zawiera łącza do informacji na temat wszystkich kluczowych języka F #.|
|[Odwołanie do symboli i operatorów](symbol-and-operator-reference/index.md)|Zawiera tabelę symboli i operatorów, które są używane w języku F #.|
|[Literały](literals.md)|W tym artykule opisano składnię wartości literału w F # i jak określić informacje o typie dla literałów w F #.|

## <a name="f-language-concepts"></a>Pojęcia dotyczące języka F #

W poniższej tabeli przedstawiono dostępne, który opisano pojęcia języka tematy referencyjne.

|Tytuł|Opis|
|-----|-----------|
|[Funkcje](functions/index.md)|Funkcje są podstawową jednostką wykonywanie programu w dowolnym języku programowania. Tak jak w innych językach funkcja języka F # o nazwie, mogą mieć parametry i argumenty take i ma treść. F # obsługuje również konstrukcji programowania funkcjonalnego, takich jak traktowanie funkcje jako wartości, przy użyciu funkcji bez nazwy w wyrażeniach kompozycja funkcji w celu utworzenia nowych funkcji, funkcje rozwinięte i definicję niejawną funkcji za pomocą częściowego Stosowanie argumentów funkcji.|
|[Typy F#](fsharp-types.md)|W tym artykule opisano typy, które są używane w F # oraz jak o nazwie i opisem typów F #.|
|[Wnioskowanie o typie](type-inference.md)|W tym artykule opisano, jak kompilator F # wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.|
|[Automatyczna generalizacja](generics/automatic-generalization.md)|W tym artykule opisano ogólny konstrukcji języka F #.|
|[Dziedziczenie](inheritance.md)|W tym artykule opisano dziedziczenie, który służy do modelowania relacji "jest a", lub subtyping w programowanie zorientowane obiektowo.|
|[Elementy członkowskie](members/index.md)|W tym artykule opisano elementy członkowskie obiektu typów F #.|
|[Parametry i argumenty](Parameters-and-Arguments.md)|W tym artykule opisano obsługę języka, aby Definiowanie parametrów i przekazanie argumentów do funkcji, metody i właściwości. Zawiera informacje dotyczące sposobu przekazywania według odwołania.|
|[Przeładowanie operatora](operator-overloading.md)|W tym artykule opisano sposób przeciążania operatorów arytmetycznych w klasie lub typie rekordu oraz na poziomie globalnym.|
|[Rzutowanie i konwersje](casting-and-conversions.md)|W tym artykule opisano obsługę konwersje typów języka F #.|
|[Kontrola dostępu](access-control.md)|W tym artykule opisano kontroli dostępu w języku F #. Kontrola dostępu oznacza, że deklarowania, w jaki klienci będą mogli korzystać z niektórych elementów programów, takich jak typy, metody, funkcje i tak dalej.|
|[Dopasowanie do wzorca](pattern-matching.md)|W tym artykule opisano wzorce, które są regułami dotyczącymi przekształcania danych wejściowych, które są używane w całym języku F #, aby wyodrębnić dane porównania z wzorcem, rozkładania danych do części składowych lub wyodrębnienia informacji z danych na różne sposoby.|
|[Wzorce aktywne](active-patterns.md)|W tym artykule opisano wzorców. Aktywne wzorce umożliwiają zdefiniowanie nazwanych partycji, które należy podzielić dane wejściowe. Wzorce aktywne służy do rozkładania danych w sposób dostosowany dla każdej partycji.|
|[Asercje](assertions.md)|W tym artykule opisano `assert` wyrażenie, które jest funkcją debugowania, można użyć w celu przetestowania wyrażenia. W przypadku awarii w trybie debugowania potwierdzenie generuje okno dialogowe błędu systemu.|
|[Obsługa wyjątków](exception-handling/index.md)|Zawiera informacje o pomocy technicznej w języku F # obsługi wyjątków.|
|[Atrybuty](attributes.md)|W tym artykule opisano atrybuty, które umożliwiają metadanych, które mają być stosowane do konstrukcji programowania.|
|[Zarządzanie zasobami: `use` — słowo kluczowe](resource-management-the-use-keyword.md)|W tym artykule opisano kluczowe `use` i `using`, które kontrolują, inicjowanie i zwolnienia zasobów|
|[Przestrzenie nazw](namespaces.md)|W tym artykule opisano obsługę przestrzeni nazw w języku F #. Przestrzeń nazw umożliwia organizowanie kodu w obszarach powiązane funkcje, dzięki któremu można dołączyć nazwę do grupowania elementów programu.|
|[Moduły](modules.md)|W tym artykule opisano modułów. Moduł F # to grupa kodzie języka F #, takie jak wartości, typy i wartości funkcji, w programie F #. Grupowanie kodu w modułach pomaga zachować kod pokrewny ze sobą oraz uniknąć konfliktów nazw w programie.|
|[Deklaracje importowania: `open` — słowo kluczowe](import-declarations-the-open-keyword.md)|W tym artykule opisano sposób `open` działa. Deklaracja importu określa modułu lub przestrzeni nazw elementów, których możesz odwoływać się bez korzystania z w pełni kwalifikowanej nazwy.|
|[Podpisy](signatures.md)|W tym artykule opisano podpisów i plików sygnatur. Plik podpisu zawiera informacje o podpisów publicznych zestawu elementów języka F # programów, takich jak typy, przestrzenie nazw i moduły. Może służyć do określenia dostępności te elementy programu.|
|[Dokumentacja XML](xml-documentation.md)|W tym artykule opisano obsługę generowania pliki komentarzy dokumentacji XML, znany także jako Potrójna kreska ułamkowa komentarze dokumentacji. Może tworzyć dokumentację z komentarzy kodu w języku F #, podobnie jak w innych językach .NET.|
|[Pełna składnia](verbose-syntax.md)|W tym artykule opisano składnię konstrukcje F # gdy lightweight — składnia nie jest włączone. Pełna składnia jest wskazywany przez `#light "off"` dyrektywę w górnej części pliku kodu.|

## <a name="f-types"></a>Typy F#

W poniższej tabeli przedstawiono dostępne tematy referencyjne, które opisują typy obsługiwane przez język F #.

|Tytuł|Opis|
|-----|-----------|
|[Wartości](values/index.md)|W tym artykule opisano wartości, które są niezmienne ilości, które mają określony typ; wartości mogą być liczb zmiennoprzecinkowych typu całkowitego lub zmiennoprzecinkowego, znaki lub tekst, list, sekwencji, tablice, krotek, związki dyskryminowane, rekordy, typy klas lub wartości funkcji.|
|[Typy podstawowe](basic-types.md)|W tym artykule opisano podstawowe typy podstawowe, które są używane w języku F #. Dla każdego typu danych zapewnia również odpowiednie typy .NET i minimalne i maksymalne wartości.|
|[Typ jednostki](unit-type.md)|W tym artykule opisano `unit` typ, który jest typem, który wskazuje brak określonej wartości; `unit` typ ma tylko jedną wartość, która działa jako symbolu zastępczego, gdy żadna inna wartość istnieje lub jest wymagana.|
|[Ciągi](strings.md)|Opisuje ciągi w języku F #. `string` Typu reprezentuje niezmienny tekst, jako sekwencja znaków Unicode. `string` jest aliasem dla `System.String` w .NET Framework.|
|[Krotki](tuples.md)|W tym artykule opisano krotek, której to grupy bez nazwy, ale uporządkowane wartości prawdopodobnie różnych typów.|
|[Typy kolekcji F#](fsharp-collection-types.md)|Przegląd funkcjonalności typy kolekcji F #, w tym typów dla tablic, list, sekwencji (seq), map i zestawów.|
|[Listy](lists.md)|W tym artykule opisano listy. Na liście w F # jest uporządkowany i niezmienne szereg elementów wszystkie tego samego typu.|
|[Opcje](options.md)|Opisuje typ opcji. Opcja w języku F # jest używana, gdy wartość może lub nie istnieje. Opcja ma podstawowy typ i może albo przechowują wartość tego typu i nie może mieć wartość.|
|[Sekwencje](sequences.md)|W tym artykule opisano sekwencji. Sekwencja jest logiczną szereg elementów jeden typ. Sekwencji poszczególne elementy tylko są obliczane, w razie potrzeby, dlatego reprezentacji może być mniejszy niż liczba literal — element wskazuje.|
|[Tablice](arrays.md)|W tym artykule opisano tablic. Tablice są stałym rozmiarze, zaczynający się od zera, mutable sekwencji kolejnych elementów danych, wszystkie tego samego typu.|
|[Rekordy](records.md)|W tym artykule opisano rekordów. Rekordy reprezentują prostych wartości zagregowanych nazwanych wartości opcjonalnie wraz z elementów członkowskich.|
|[Sumy rozłączne](discriminated-unions.md)|W tym artykule opisano związki dyskryminowane, które zapewnia obsługę wartości, które mogą być jednym z wielu przypadków nazwanych, każdy z potencjalnie różnych wartości i typów.|
|[Wyliczenia](enumerations.md)|W tym artykule opisano wyliczenia są nazywane typami, które mają zdefiniowanego zestawu wartości. Można je zamiast literałów wprowadzić kod bardziej czytelny i łatwy w obsłudze.|
|[Komórki odwołań](reference-cells.md)|W tym artykule opisano komórki odwołań, które są lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych z semantyką odwołań.|
|[Skróty typów](type-abbreviations.md)|W tym artykule opisano skróty typów, które są alternatywne nazwy dla typów.|
|[Klasy](classes.md)|W tym artykule opisano klasy, które są typy, które reprezentują obiektów, które mogą mieć właściwości, metod i zdarzeń.|
|[Struktury](structures.md)|W tym artykule opisano struktur, które są wybierane compact, które mogą być bardziej efektywne niż klasę dla typów, które mają niewielką ilość danych i prostego zachowanie.|
|[Interfejsy](interfaces.md)|W tym artykule opisano interfejsy, które określają zestawów powiązanych elementów członkowskich, które implementują innych klas.|
|[Klasy abstrakcyjne](abstract-classes.md)|W tym artykule opisano klasy abstrakcyjnej, które są klasami, które opuszczają niektórych lub wszystkich elementów członkowskich niezaimplementowane, tak aby implementacji może być udostępniane przez klasy pochodne.|
|[Rozszerzenia typu](type-extensions.md)|Opisuje typ rozszerzenia, które pozwalają na dodawanie nowych członków do typu obiektu zdefiniowanego wcześniej.|
|[Typy elastyczne](flexible-types.md)|W tym artykule opisano typy elastyczne. Adnotacja elastycznym typem jest określony wskazanie, że parametr, zmienna lub wartość ma typ, który jest zgodny z typem, w którym zgodność jest określana przez pozycji w hierarchii zorientowane obiektowo, klas lub interfejsów.|
|[Delegaci](delegates.md)|W tym artykule opisano delegatów, które reprezentują wywołania funkcji jako obiekt.|
|[Jednostki miary](units-of-measure.md)|W tym artykule opisano jednostki miary. Wartości zmiennoprzecinkowych w języku F # mogą mieć skojarzone jednostki miary, które są zwykle używane w celu wskazania, długość, woluminu, urządzeń pamięci masowej i tak dalej.|
|[Dostawcy typów](../tutorials/type-providers/index.md)|Opisuje typ zapewnia i zawiera łącza do przewodników na dostęp do baz danych i usług sieci web za pomocą wbudowanych dostawców typów.|

## <a name="f-expressions"></a>Wyrażeń języka F #

Poniższa tabela zawiera listę tematów, które opisują wyrażeń języka F #.

|Tytuł|Opis|
|-----|-----------|
|[Wyrażenie warunkowe: `if...then...else`](conditional-expressions-if-then-else.md)|W tym artykule opisano `if...then...else` wyrażenie, które uruchamia gałęziami kodu i oblicza również innej wartości w zależności od tego, wyrażenie logiczne, biorąc pod uwagę.|
|[Wyrażenia dopasowania](match-expressions.md)|W tym artykule opisano `match` wyrażenie zawiera rozgałęziania formant, który jest oparty na porównaniu wyrażenia zestaw wzorców.|
|[Pętle: `for...to` wyrażenia](loops-for-to-expression.md)|W tym artykule opisano `for...to` wyrażenia, który jest używany do wykonywania iteracji w pętli zakresu wartości zmiennej pętli.|
|[Pętle: `for...in` wyrażenia](loops-for-in-expression.md)|W tym artykule opisano `for...in` wyrażenia, konstrukcja pętli, która jest używana do wykonywania iteracji dopasowania wzorca w wyliczalny kolekcji, takie jak wyrażenie zakresu, sekwencji, lista, tablicy lub innej konstrukcji, który obsługuje wyliczenia.|
|[Pętle: `while...do` wyrażenia](loops-while-do-expression.md)|W tym artykule opisano `while...do` wyrażenie, które służy do przeprowadzania iteracji wykonywanie (pętli), gdy spełniony jest warunek określony test.|
|[Wyrażenia obiektów](object-expressions.md)|W tym artykule opisano wyrażeń obiektów, które są wyrażeniami, które tworzenie nowych wystąpień typu utworzony dynamicznie, anonimowy obiekt, który jest oparty na istniejących typu podstawowego, interfejs lub zestawu interfejsów.|
|[Obliczenia powolne](lazy-computations.md)|W tym artykule opisano obliczenia powolne, będące obliczenia, które nie są oceniane natychmiast, ale zamiast tego są oceniane, gdy wynik będzie to wymagane.|
|[Wyrażenia obliczeń](computation-expressions.md)|W tym artykule opisano wyrażenia obliczeń F #, które zapewniają wygodnej składni pisania obliczeń, które mogą być sekwencjonowania i łączyć, używając konstrukcji przepływów sterowania i powiązania. Może służyć do zapewnienia wygodnej składni dla *monads*, funkcjonalności funkcji programowania, który może służyć do zarządzania danych, kontroli i efekty uboczne w programach funkcjonalności. Jeden typ wyrażenia obliczeń, asynchronicznego przepływu pracy, zapewnia obsługę asynchronicznych i równoległych obliczeń. Aby uzyskać więcej informacji, zobacz [Asynchroniczne przepływy pracy](asynchronous-workflows.md).|
|[Asynchroniczne przepływy pracy](asynchronous-workflows.md)|Asynchroniczne przepływy pracy, zawiera opis funkcji języka, umożliwiająca napisania kodu asynchronicznego w sposób, który jest bardzo zbliżona sposób można napisać naturalnie synchroniczny kod.|
|[Cytaty kodu](code-quotations.md)|W tym artykule opisano cytaty kodu funkcji języka, który umożliwia generowanie i pracować programowo z wyrażeń kodu języka F #.|
|[Wyrażenia zapytania](query-expressions.md)|W tym artykule opisano wyrażenia zapytań funkcji języka, implementuje LINQ języka F #, która umożliwia tworzenie zapytań dotyczących źródła danych lub kolekcji wyliczalny.|

## <a name="compiler-supported-constructs"></a>Konstrukcje obsługiwane przez kompilator

Poniższa tabela zawiera listę tematów opisujących konstrukcje obsługiwane przez kompilator specjalnych.

|Temat|Opis|
|-----|-----------|
|[Opcje kompilatora](compiler-options.md)|W tym artykule opisano opcje wiersza polecenia dla kompilatora F #.|
|[Dyrektywy kompilatora](compiler-directives.md)|Opis procesora dyrektywy i dyrektywy kompilatora.|
|[Identyfikatory wiersza źródłowego, pliku i ścieżki](source-line-file-path-identifiers.md)|W tym artykule opisano identyfikatory `__LINE__`, `__SOURCE_DIRECTORY__` i `__SOURCE_FILE__`, które są wbudowane wartości, które umożliwiają dostęp do źródła wiersza numer, katalogów i plików nazwy w kodzie.|

## <a name="see-also"></a>Zobacz także

- [Visual F#](../index.md)
