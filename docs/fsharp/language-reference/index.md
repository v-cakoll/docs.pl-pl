---
title: Materiały referencyjne dotyczące języka F#
description: 'Informacje o F # języka funkcji z odwołania tokeny języka, pojęcia typów, wyrażenia i tematy konstrukcja obsługiwane przez kompilator.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c25ab4a4936b532a21aed8b2b0202fec1dd7133
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566694"
---
# <a name="f-language-reference"></a>Materiały referencyjne dotyczące języka F#

Ta sekcja ma odwołanie do języka F #, język programowania modelu wielu przeznaczonych dla platformy .NET. Język F # obsługuje funkcjonalności, zorientowany obiektowo i imperatywnych modele programowania.


## <a name="f-tokens"></a>Tokeny języka F #
W poniższej tabeli przedstawiono tematów odwołania, zawierających tabele słów kluczowych, symbole i literałów używane jako tokeny w języku F #.



|Tytuł|Opis|
|-----|-----------|
|[Odwołanie do słów kluczowych](keyword-reference.md)|Zawiera linki do informacji na temat wszystkich kluczowych języka F #.|
|[Odwołanie do symboli i operatorów](symbol-and-operator-reference/index.md)|Zawiera tabelę symboli i operatory, które są używane w języku F #.|
|[Literały](literals.md)|W tym artykule opisano składnię wartości literałów w F # oraz sposobu określania informacji o typie dla literałów F #.|

## <a name="f-language-concepts"></a>Pojęcia dotyczące języka F #
W poniższej tabeli przedstawiono dostępne, który opisano pojęcia dotyczące języka tematy dokumentacji.



|Tytuł|Opis|
|-----|-----------|
|[Funkcje](functions/index.md)|Funkcje są podstawową jednostkę wykonywania programu w dowolnym języku programowania. Jak w innych językach funkcja F # o nazwie, może mieć parametry i argumenty podjęcia i ma treść. F # obsługuje również funkcjonalności narzędzi programistycznych, takich jak traktowanie funkcje jako wartości, przy użyciu funkcji bez nazwy w wyrażeniach kompozycja funkcji do utworzenia nowych funkcji, funkcje rozwinięte i niejawnego definiowania funkcji i częściowe Stosowanie argumentów funkcji.|
|[Typy F#](fsharp-types.md)|W tym artykule opisano typy, które są używane w F # oraz jak o nazwie i opisem typów F #.|
|[Wnioskowanie o typie](type-inference.md)|W tym artykule opisano, jak kompilator języka F # wnioskuje typy wartości, zmienne, parametrów i zwracanych wartości.|
|[Automatyczna generalizacja](generics/automatic-generalization.md)|W tym artykule opisano ogólny konstrukcji języka F #.|
|[Dziedziczenie](inheritance.md)|W tym artykule opisano dziedziczenia, która jest używana do modelowania relacji "jest a", lub subtyping w programowanie zorientowane obiektowo.|
|[Elementy członkowskie](members/index.md)|W tym artykule opisano elementy członkowskie typów obiektów języka F #.|
|[Parametry i argumenty ](Parameters-and-Arguments.md)|W tym artykule opisano obsługę języka zdefiniowanie parametrów i przekazywanie argumentów do funkcji, właściwości i metod. Zawiera informacje o sposobie przekazywane przez odwołanie.|
|[Przeładowanie operatora](operator-overloading.md)|Opisuje sposób przeciążenia operatorów arytmetycznych w klasie lub typ rekordu i na poziomie globalnym.|
|[Rzutowanie i konwersje](casting-and-conversions.md)|W tym artykule opisano obsługę konwersje typów w języku F #.|
|[Kontrola dostępu](access-control.md)|W tym artykule opisano kontroli dostępu w języku F #. Kontrola dostępu oznacza zadeklarowanie, w jaki klienci będą mogli korzystać niektóre elementy programu, takie jak typy metod, funkcje i tak dalej.|
|[Dopasowanie do wzorca](pattern-matching.md)|Opisuje wzorce, które są reguły przekształcania danych wejściowych używanych w całym języka F # do wyodrębnienia danych Porównaj z wzorcem, Rozłóż danych na elementów składowych lub wyodrębnienia informacji z danych na różne sposoby.|
|[Wzorce aktywne](active-patterns.md)|Opisuje wzorce aktywne. Wzorce aktywne umożliwiają zdefiniowanie nazwanego partycji, które należy podzielić danych wejściowych. Wzorce aktywne umożliwia dekompozycji danych w sposób dostosowany dla każdej partycji.|
|[Asercje](assertions.md)|W tym artykule opisano `assert` wyrażenie, które jest funkcja debugowania, którego można używać do testowania wyrażenia. W przypadku awarii w trybie debugowania potwierdzenia generuje okno dialogowe błędu systemu.|
|[Obsługa wyjątków](exception-handling/index.md)|Zawiera informacje o pomocy technicznej w języku F # obsługi wyjątków.|
|[Atrybuty](attributes.md)|Zawiera opis atrybutów, które umożliwiają metadanych ma być stosowany do konstrukcji programującej.|
|[Zarządzanie zasobami: `use` — słowo kluczowe](resource-management-the-use-keyword.md)|W tym artykule opisano słowa kluczowe `use` i `using`, który można kontrolować, inicjowanie i wersji zasobów|
|[Przestrzenie nazw](namespaces.md)|W tym artykule opisano obsługę przestrzeni nazw w F #. Przestrzeń nazw umożliwia organizowanie kodu w obszarach związanych z nimi funkcji umożliwiając dołączyć nazwę do grupowania elementów programu.|
|[Moduły](modules.md)|Zawiera opis modułów. Moduł F # to grupa kodzie języka F #, takie jak wartości, typu i wartości funkcji w programie F #. Grupowanie kodu w modułach pomaga zachować kodu powiązanego ze sobą oraz uniknąć konfliktów nazw w programie.|
|[Deklaracje importowania: `open` — słowo kluczowe](import-declarations-the-open-keyword.md)|Opisuje sposób `open` działa. Deklaracja importu określa modułu lub przestrzeni nazw elementów, których można odwoływać się bez korzystania z w pełni kwalifikowaną nazwę.|
|[Podpisy](signatures.md)|Opisuje podpisów i pliki sygnatur. Plik sygnatury zawiera informacje o publiczne podpisów zestawu F # program elementów, takich jak typy, obszary nazw i modułów. Może służyć do określenia dostępność tych elementów programu.|
|[Dokumentacja XML](xml-documentation.md)|W tym artykule opisano obsługę generowania pliki dokumentacji komentarze w dokumencie XML, znanej także jako potrójnym ukośnikiem komentarze. Można utworzyć dokumentacji z komentarze w kodzie języka F # tak jak w przypadku innych języków platformy .NET.|
|[Pełna składnia](verbose-syntax.md)|Opisano składnię konstrukcje F #, gdy lightweight — składnia nie jest włączone. Pełna składnia jest określane przez `#light "off"` dyrektywy w górnej części pliku kodu.|

## <a name="f-types"></a>Typy F#
W poniższej tabeli przedstawiono dostępne tematy odwołań, które opisują typy są obsługiwane przez język F #.



|Tytuł|Opis|
|-----|-----------|
|[Wartości](values/index.md)|W tym artykule opisano wartości, które są niezmienne ilości, które mają określony typ; wartości mogą być liczbami całkowitą lub zmiennoprzecinkową, znaków lub tekstu, list, sekwencji, tablic, krotek, rozłączne, rekordy, typu klasy lub wartości funkcji.|
|[Typy pierwotne](primitive-types.md)|Opisuje podstawowe typy pierwotne, które są używane w języku F #. Dla każdego typu danych umożliwia także odpowiednie typy .NET i wartości minimalną i maksymalną.|
|[Typ jednostki](unit-type.md)|W tym artykule opisano `unit` typu, który jest typem, który wskazuje brak określonej wartości; `unit` typ ma tylko jedną wartość, który działa jako symbol zastępczy, gdy żadna inna wartość istnieje lub jest wymagana.|
|[Ciągi](strings.md)|W tym artykule opisano ciągów w języku F #. `string` Typu reprezentuje niezmienne tekst sekwencję znaków Unicode. `string` alias jest `System.String` w programie .NET Framework.|
|[Krotki](tuples.md)|W tym artykule opisano spójnych kolekcji to grupy bez nazwy, ale uporządkowanych możliwie różnych typów wartości.|
|[Typy kolekcji F#](fsharp-collection-types.md)|Przegląd funkcjonalności typy kolekcji F #, łącznie z typów dla tablic, list, sekwencje (seq), map i zestawów.|
|[Listy](lists.md)|Zawiera opis listy. Na liście w F # jest uporządkowany i modyfikować szereg elementów wszystkie tego samego typu.|
|[Opcje](options.md)|Opisuje typ opcji. Opcja w języku F # jest używana, gdy wartość może lub nie istnieje. Opcja ma typu podstawowego i może utrzymywać albo wartość tego typu lub może nie mieć wartość.|
|[Sekwencje](sequences.md)|Zawiera opis sekwencji. Sekwencja jest logiczną szereg elementów tylko jeden typ. Sekwencji poszczególne elementy tylko są obliczane, jeśli jest to wymagane, więc reprezentacja może być mniejszy od liczby element literał wskazuje.|
|[Tablice](arrays.md)|W tym artykule opisano tablic. Tablice są stałym rozmiarze, liczony od zera, modyfikowalną sekwencji elementów kolejnych danych, wszystkie tego samego typu.|
|[Rekordy](records.md)|W tym artykule opisano rekordów. Rejestruje reprezentują proste agreguje nazwanych wartości, opcjonalnie z elementami członkowskimi.|
|[Sumy rozłączne](discriminated-unions.md)|Opisuje rozłączne, który zapewnia obsługę wartości, które mogą być różne przypadków, każde z nich typy i prawdopodobnie różne wartości.|
|[Wyliczenia](enumerations.md)|W tym artykule opisano wyliczenia są nazwane typy, które mają zdefiniowanego zestawu wartości. Można używać ich zamiast literały Aby bardziej czytelny i łatwy w obsłudze kodu.|
|[Komórki odwołań](reference-cells.md)|W tym artykule opisano komórki odwołań, które są lokalizacje magazynu, które umożliwiają tworzenie zmienne modyfikowalne z semantykę odwołania.|
|[Skróty typów](type-abbreviations.md)|W tym artykule opisano skróty typów, które są alternatywne nazwy dla typów.|
|[Klasy](classes.md)|W tym artykule opisano klasy, które są typy, które reprezentują obiektów, które mogą mieć właściwości, metod i zdarzeń.|
|[Struktury](structures.md)|Zawiera opis struktury, które typy obiektów compact, które może być skuteczniejsza niż klasa dla typów, które mają niewielką ilość danych i zachowania proste.|
|[Interfejsy](interfaces.md)|W tym artykule opisano interfejsów, które określają zestawy pokrewnych elementów członkowskich, które implementują innych klas.|
|[Klasy abstrakcyjne](abstract-classes.md)|Zawiera opis klas abstrakcyjnych, które są klasy, które opuszczają niektóre lub wszystkie elementy członkowskie niezaimplementowane, dzięki czemu można podać implementacji klasy pochodne.|
|[Rozszerzenia typu](type-extensions.md)|Opisuje typ rozszerzenia, które umożliwiają dodawanie nowych elementów członkowskich do typu wcześniej zdefiniowanego obiektu.|
|[Typy elastyczne](flexible-types.md)|W tym artykule opisano typy elastyczne. Adnotacja elastycznym typem jest określony wskazanie, że parametr, zmiennej lub wartość ma typ, który jest zgodny z typem, których zgodność jest określany przez położenie w hierarchii zorientowane obiektowo interfejsów lub klas.|
|[Delegaci](delegates.md)|W tym artykule opisano delegatów, które reprezentują wywołanie funkcji jako obiekt.|
|[Jednostki miary](units-of-measure.md)|Opis jednostki miary. Przestawne wartości w języku F # można skojarzyć jednostki miary, które zwykle są używane do wskazywania długość, woluminu, masa i tak dalej.|
|[Dostawcy typów](../tutorials/type-providers/index.md)|Opisuje typ zawiera i łącza do wskazówki na temat używania dostawców wbudowanych typów dostępu do baz danych i usług sieci web.|

## <a name="f-expressions"></a>Wyrażenia F #
Poniższa tabela zawiera listę tematów opisujących wyrażenia F #.

|Tytuł|Opis|
|-----|-----------|
|[Wyrażenie warunkowe: `if...then...else`](conditional-expressions-if-then-else.md)|W tym artykule opisano `if...then...else` wyrażenie, które uruchamia różnych gałęziach kodu, a także wynikiem jest wartość różne w zależności od danego wyrażenie warunkowe.|
|[Wyrażenia dopasowania](match-expressions.md)|W tym artykule opisano `match` wyrażenie zawiera rozgałęziania formant, który jest oparte na porównaniu wyrażenia z zestawem wzorców.|
|[Pętle: `for...to` wyrażenia](loops-for-to-expression.md)|W tym artykule opisano `for...to` wyrażenia, który służy do wykonywania iteracji w pętli zakres wartości zmiennej pętli.|
|[Pętle: `for...in` wyrażenia](loops-for-in-expression.md)|W tym artykule opisano `for...in` wyrażenia, konstrukcję pętli, który służy do wykonywania iteracji dopasowania wzorca w wyliczalny kolekcji, takie jak zakres wyrażenia sekwencji, listy, tablicy lub innych konstrukcji obsługuje wyliczenia.|
|[Pętle: `while...do` wyrażenia](loops-while-do-expression.md)|W tym artykule opisano `while...do` wyrażenie, które służy do wykonywania iteracji (zapętlenia) podczas testu określony warunek jest spełniony.|
|[Wyrażenia obiektów](object-expressions.md)|Opis obiektu wyrażeń, które są wyrażeń, które utworzenia nowego wystąpienia typu utworzony dynamicznie, anonimowego obiektu, który bazuje na istniejący typ podstawowy, interfejsem lub zestawu interfejsów.|
|[Obliczenia powolne](lazy-computations.md)|W tym artykule opisano obliczenia powolne, które są obliczenia, które nie są oceniane natychmiast, ale zamiast tego są oceniane, gdy wynik będzie to wymagane.|
|[Wyrażenia obliczeń](computation-expressions.md)|W tym artykule opisano wyrażenia obliczeń w języku F #, które zapewniają wygodną składni zapisywania obliczenia, które mogą być sekwencjonowania i łączyć, używając konstrukcji przepływu sterowania i powiązania. One może służyć do zapewnienia wygodny składnię *monady*, funkcjonalności funkcji programowania, który może służyć do zarządzania danych, sterowania i efekty uboczne w programach funkcjonalności. Jeden typ — wyrażenie obliczeń, asynchroniczne przepływu pracy, zapewnia obsługę obliczeń asynchronicznych i równolegle. Aby uzyskać więcej informacji, zobacz [Asynchroniczne przepływy pracy](asynchronous-workflows.md).|
|[Asynchroniczne przepływy pracy](asynchronous-workflows.md)|Asynchroniczne przepływy pracy, zawiera opis funkcji języka, która umożliwia zapisanie asynchroniczne kodu w taki sposób, który jest bliski sposób można będzie naturalnie zapisu synchronicznego kodu.|
|[Cytaty kodu](code-quotations.md)|Opisuje cytaty kodu języka funkcja, która umożliwia generowanie i pracować z wyrażenia kodu języka F # programowo.|
|[Wyrażenia zapytania](query-expressions.md)|Opisuje funkcja języka, która implementuje LINQ w F # i umożliwia pisanie zapytań dotyczących źródła danych lub kolekcji wyliczalny wyrażenia zapytania.|

## <a name="compiler-supported-constructs"></a>Konstrukcje obsługiwane przez kompilator
Poniższa tabela zawiera listę tematów opisujących specjalne konstrukcje obsługiwane przez kompilator.

|Temat|Opis|
|-----|-----------|
|[Opcje kompilatora](compiler-options.md)|Opisuje opcje wiersza polecenia kompilatora F #.|
|[Dyrektywy kompilatora](compiler-directives.md)|Opisuje procesora dyrektywy i dyrektywy kompilatora.|
|[Identyfikatory wiersza źródłowego, pliku i ścieżki](source-line-file-path-identifiers.md)|W tym artykule opisano identyfikatory `__LINE__`, `__SOURCE_DIRECTORY__` i `__SOURCE_FILE__`, które są wbudowane wartości, które umożliwiają dostęp do źródła wiersza numer, katalogu i nazwa pliku w kodzie.|

## <a name="see-also"></a>Zobacz też
[Visual F#](../index.md)
