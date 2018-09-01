---
title: Odwołanie do słowa kluczowego (F#)
description: 'Znajdź łącza do informacji na temat wszystkich słów kluczowych języka F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 18bf5f00cdd5250c0fbd503d096e5415a8b9feea
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396876"
---
# <a name="keyword-reference"></a>Odwołanie do słowa kluczowego

Ten temat zawiera łącza do informacji o wszystkich kluczowych języka F #.

## <a name="f-keyword-table"></a>Tabela F # — słowo kluczowe

W poniższej tabeli przedstawiono wszystkie F # słowa kluczowe w kolejności alfabetycznej, wraz z krótkie opisy i linki do powiązanych tematów, które zawierają więcej informacji.

|Słowo kluczowe|Łącze|Opis|
|-------|----|-----------|
|`abstract`|[Elementy członkowskie](members/index.md)<br /><br />[Klasy abstrakcyjne](abstract-classes.md)|Określa metodę, która albo nie ma implementacji w typie, w którym jest zdeklarowana lub jest wirtualny i ma domyślną implementację.|
|`and`|[`let` Powiązania](functions/let-bindings.md)<br /><br />[Elementy członkowskie](members/index.md)<br /><br />[Ograniczenia](generics/constraints.md)|Używane w wzajemnie cyklicznego powiązań w deklaracji właściwości i za pomocą wielu ograniczeń w parametrach rodzajowych.|
|`as`|[Klasy](classes.md)<br /><br />[Dopasowanie do wzorca](Pattern-Matching.md)|Umożliwia nazwij bieżący obiekt klasy obiektu. Umożliwia również nadaj nazwę całego wzorca w ciągu dopasowania do wzorca.|
|`assert`|[Asercje](assertions.md)|Używane do weryfikacji kodu podczas debugowania.|
|`base`|[Klasy](classes.md)<br /><br />[Dziedziczenie](inheritance.md)|Używane jako nazwę obiektu klasy bazowej.|
|`begin`|[Pełna składnia](verbose-syntax.md)|W składni pełne wskazuje początek bloku kodu.|
|`class`|[Klasy](classes.md)|W składni pełne wskazuje początek definicji klasy.|
|`default`|[Elementy członkowskie](members/index.md)|Wskazuje implementację metody abstrakcyjnej; używany razem z deklaracji metody abstrakcyjnej, aby utworzyć metodę wirtualną.|
|`delegate`|[Delegaci](delegates.md)|Używane do deklarowania delegata.|
|`do`|[Powiązania „do”](functions/do-bindings.md)<br /><br />[Pętle: `for...to` wyrażenia](loops-for-to-expression.md)<br /><br />[Pętle: `for...in` wyrażenia](loops-for-in-expression.md)<br /><br />[Pętle: `while...do` wyrażenia](loops-while-do-expression.md)|Używane w konstrukcji pętli lub wykonywanie kodu imperatywnego.|
|`done`|[Pełna składnia](verbose-syntax.md)|W składni pełne wskazuje koniec bloku kodu w wyrażeniu pętli.|
|`downcast`|[Rzutowanie i konwersje](casting-and-conversions.md)|Używana do konwersji do typu, które jest niżej w łańcuchu dziedziczenia.|
|`downto`|[Pętle: `for...to` wyrażenia](loops-for-to-expression.md)|W `for` wyrażenia używane w przypadku licząc w odwrotnej kolejności.|
|`elif`|[Wyrażenie warunkowe: `if...then...else`](conditional-expressions-if-then-else.md)|Używane w rozgałęzień warunkowych. Krótką formą `else if`.|
|`else`|[Wyrażenie warunkowe: `if...then...else`](conditional-expressions-if-then-else.md)|Używane w rozgałęzień warunkowych.|
|`end`|[Struktury](structures.md)<br /><br />[Sumy rozłączne](discriminated-unions.md)<br /><br />[Rekordy](records.md)<br /><br />[Rozszerzenia typu](type-extensions.md)<br /><br />[Pełna składnia](verbose-syntax.md)|W definicji typu i rozszerzeń typu wskazuje koniec sekcji definicje elementów członkowskich.<br /><br />Pełne składnię, używany do określenia koniec bloku kodu, który rozpoczyna się od `begin` — słowo kluczowe.|
|`exception`|[Obsługa wyjątków](exception-handling/index.md)<br /><br />[Typy wyjątków](exception-handling/exception-types.md)|Używane do deklarowania typ wyjątku.|
|`extern`|[Funkcje zewnętrzne](functions/external-functions.md)|Wskazuje, że element zadeklarowany programu jest zdefiniowana w innym pliku binarnego lub zestawu.|
|`false`|[Typy pierwotne](primitive-types.md)|Używane jako literału wartości logicznej.|
|`finally`|[Wyjątki: `try...finally` wyrażenia](exception-handling/the-try-finally-expression.md)|Wraz z `try` wprowadzenie bloku kodu, który jest wykonywany niezależnie od tego, czy wystąpi wyjątek.|
|`fixed`|[Stała](fixed.md)|Umożliwia "przypinając" wskaźnik na stosie, aby uniemożliwić jego bezużyteczne.|
|`for`|[Pętle: `for...to` wyrażenia](loops-for-to-expression.md)<br /><br />[Pętle: wyrażenie for...in](loops-for-in-expression.md)|Używane w konstrukcji pętli.|
|`fun`|[Wyrażenia lambda: `fun` — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md)|Używane w wyrażeniach lambda, funkcji anonimowych tzw.|
|`function`|[Wyrażenia dopasowania](match-expressions.md)<br /><br />[Wyrażenia lambda: Fun — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md)|Używane jako krótszy alternatywa dla `fun` — słowo kluczowe i `match` wyrażenia w wyrażeniu lambda, która ma dopasowania do wzorca w pojedynczy argument.|
|`global`|[Przestrzenie nazw](namespaces.md)|Można odwoływać się do przestrzeni nazw .NET najwyższego poziomu.|
|`if`|[Wyrażenie warunkowe: `if...then...else`](conditional-expressions-if-then-else.md)|Używane w konstrukcje warunkowe rozgałęziania.|
|`in`|[Pętle: wyrażenie for...in](loops-for-in-expression.md)<br /><br />[Pełna składnia](verbose-syntax.md)|Używać wyrażeń sekwencji, a w Pełna składnia wyrażenia z powiązania.|
|`inherit`|[Dziedziczenie](inheritance.md)|Można określić klasy bazowej lub interfejsu podstawowego.|
|`inline`|[Funkcje](functions/index.md)<br /><br />[Funkcje śródwierszowe](functions/inline-functions.md)|Służy do wskazania funkcja, która powinna zostać włączona bezpośrednio do kodu wywołującego.|
|`interface`|[Interfejsy](interfaces.md)|Używane do deklarowania i implementować interfejsy.|
|`internal`|[Kontrola dostępu](access-control.md)|Można określić, że element członkowski jest widoczny w zestawie, ale nie poza nim.|
|`lazy`|[Obliczenia powolne](lazy-computations.md)|Służy do określania obliczeń, który ma być wykonywane tylko wtedy, gdy wynik jest wymagana.|
|`let`|[`let` Powiązania](functions/let-bindings.md)|Służy do skojarzenia lub powiązać nazwę wartości lub funkcji.|
|`let!`|[Asynchroniczne przepływy pracy](asynchronous-workflows.md)<br /><br />[Wyrażenia obliczeń](computation-expressions.md)|Używane w Asynchroniczne przepływy pracy, aby powiązać nazwę wynik asynchroniczne obliczenie, lub inne wyrażenia obliczeń użyte do utworzenia powiązania nazwy wyniku jest typem wyliczenia.|
|`match`|[Wyrażenia dopasowania](match-expressions.md)|Używany do gałęzi przez porównanie wartości do wzorca.|
|`match!`|[Wyrażenia obliczeń](computation-expressions.md#match)|Umożliwia wbudowane wywołanie w celu dopasowania wyrażenia i wzorzec obliczeń na jego wynik.|
|`member`|[Elementy członkowskie](members/index.md)|Używane do deklarowania właściwości lub metody w typu obiektu.|
|`module`|[Moduły](modules.md)|Umożliwia skojarzenie nazwy z grupą powiązanych typów wartości i funkcji do logicznego odseparowania od innego kodu.|
|`mutable`|[Powiązania „let”](functions/let-bindings.md)|Używane do deklarowania zmiennej, oznacza to, które można zmienić wartość.|
|`namespace`|[Przestrzenie nazw](namespaces.md)|Umożliwia skojarzenie nazwy z grupą powiązanych typów i moduły, do logicznego odseparowania od innego kodu.|
|`new`|[Konstruktory](members/constructors.md)<br /><br />[Ograniczenia](generics/constraints.md)|Używane do deklarowania, zdefiniuj lub wywoływania konstruktora, który tworzy, lub który można utworzyć obiekt.<br /><br />Umożliwia również w ograniczenia parametru ogólnego wskazują, że typ musi mieć określone konstruktora.|
|`not`|[Odwołanie do symboli i operatorów](symbol-and-operator-reference/index.md)<br /><br />[Ograniczenia](generics/constraints.md)|Bez faktycznego słowem kluczowym. Jednak `not struct` w połączeniu jest używany jako ograniczenie parametru ogólnego.|
|`null`|[Wartości null](values/null-values.md)<br /><br />[Ograniczenia](generics/constraints.md)|Wskazuje brak obiektu.<br /><br />Również używany w ograniczenia parametru ogólnego.|
|`of`|[Sumy rozłączne](discriminated-unions.md)<br /><br />[Delegaci](delegates.md)<br /><br />[Typy wyjątków](exception-handling/exception-types.md)|Używane w połączenia dyskryminowanych, aby wskazać typ kategorii wartości, a w deklaracjach delegata i wyjątków.|
|`open`|[Deklaracje importowania: `open` — słowo kluczowe](import-declarations-the-open-keyword.md)|Używane, aby udostępnić zawartość przestrzeni nazw lub module bez kwalifikacji.|
|`or`|[Odwołanie do symboli i operatorów](symbol-and-operator-reference/index.md)<br /><br />[Ograniczenia](generics/constraints.md)|Używane z warunkami logiczną jako wartość logiczna `or` operatora. Odpowiednikiem "||`.<br /><br />Również używany w ograniczeniami elementu członkowskiego.|
|`override`|[Elementy członkowskie](members/index.md)|Używany do implementowania nieco inna niż wersja podstawowa metody abstrakcyjne lub wirtualne.|
|`private`|[Kontrola dostępu](access-control.md)|Ogranicza dostęp do elementu członkowskiego do kodu, w tym samym typie lub modułu.|
|`public`|[Kontrola dostępu](access-control.md)|Umożliwia dostęp do elementu członkowskiego z zewnątrz typu.|
|`rec`|[Funkcje](functions/index.md)|Służy do wskazania, że funkcja jest rekursywny.|
|`return`|[Asynchroniczne przepływy pracy](Asynchronous-Workflows.md)<br /><br />[Wyrażenia obliczeń](computation-expressions.md)|Służy do wskazania wartość do dostarczenia jako wynik wyrażenia obliczeń.|
|`return!`|[Wyrażenia obliczeń](computation-expressions.md)<br /><br />[Asynchroniczne przepływy pracy](asynchronous-workflows.md)|Służy do wskazywania wyrażenia obliczeń, gdy obliczane, zwraca wynik funkcji zawierających wyrażenia obliczeń.|
|`select`|[Wyrażenia zapytania](query-expressions.md)|Używane w wyrażeniach zapytań, aby określić, jakie pola lub kolumny do wyodrębnienia. Należy pamiętać, że jest kontekstowym słowem kluczowym, co oznacza, że nie jest faktycznie słowem zastrzeżonym, i działa jak słowem kluczowym w odpowiedniego kontekstu.|
|`static`|[Elementy członkowskie](members/index.md)|Służy do wskazania metodę lub właściwość, która może być wywołana bez wystąpienia typu lub składowej wartość, która jest udostępniona wszystkim wystąpieniom typu.|
|`struct`|[Struktury](structures.md)<br /><br />[Ograniczenia](generics/constraints.md)|Używane do deklarowania typu struktury.<br /><br />Również używany w ograniczenia parametru ogólnego.<br /><br />Używane dla zgodności OCaml w definicji modułu.|
|`then`|[Wyrażenie warunkowe: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Konstruktory](members/constructors.md)|Używane w wyrażeniach warunkowych.<br /><br />Umożliwia również wykonać efekty uboczne po konstrukcji obiektu.|
|`to`|[Pętle: `for...to` wyrażenia](loops-for-to-expression.md)|Używane w `for` pętli, aby określić zakres.|
|`true`|[Typy pierwotne](primitive-types.md)|Używane jako literału wartości logicznej.|
|`try`|[Wyjątki: Try... with — wyrażenie](exception-handling/the-try-with-expression.md)<br /><br />[Wyjątki: Try... finally — wyrażenie](exception-handling/the-try-finally-expression.md)|Umożliwia wprowadzenie bloku kodu, który może generować wyjątek. Wraz z `with` lub `finally`.|
|`type`|[Typy F#](fsharp-types.md)<br /><br />[Klasy](classes.md)<br /><br />[Rekordy](records.md)<br /><br />[Struktury](structures.md)<br /><br />[Wyliczenia](enumerations.md)<br /><br />[Sumy rozłączne](discriminated-unions.md)<br /><br />[Skróty typów](type-abbreviations.md)<br /><br />[Jednostki miary](units-of-measure.md)|Używane do deklarowania klas, rekord, struktury, złożenia dyskryminowanego, typ wyliczeniowy, jednostka miary lub — typ skrótu.|
|`upcast`|[Rzutowanie i konwersje](casting-and-conversions.md)|Używana do konwersji na typ, który znajduje się wyżej w łańcuchu dziedziczenia.|
|`use`|[Zarządzanie zasobami: `use` — słowo kluczowe](resource-management-the-use-keyword.md)|Używane zamiast `let` dla wartości, które wymagają `Dispose` wywoływana, aby zwolnić zasoby.|
|`use!`|[Wyrażenia obliczeń](computation-expressions.md)<br /><br />[Asynchroniczne przepływy pracy](asynchronous-workflows.md)|Używane zamiast `let!` Asynchroniczne przepływy pracy i inne wyrażenia obliczeń dla wartości, które wymagają `Dispose` wywoływana, aby zwolnić zasoby.|
|`val`|[Pola jawne: słowo kluczowe `val`](members/explicit-fields-the-val-keyword.md)<br /><br />[Podpisy](signatures.md)<br /><br />[Elementy członkowskie](members/index.md)|Używany w podpisie, aby wskazać wartość lub w typie, aby zadeklarować elementu członkowskiego, w ograniczonych sytuacjach.|
|`void`|[Typy pierwotne](primitive-types.md)|Wskazuje .NET `void` typu. Używany podczas współpracy z innymi językami .NET.|
|`when`|[Ograniczenia](generics/constraints.md)|Używane dla warunków logicznych (*podczas osłony*) na dopasowania do wzorca i wprowadzać Klauzula ograniczenia dla parametru typu ogólnego.|
|`while`|[Pętle: `while...do` wyrażenia](loops-while-do-expression.md)|Uvozuje Konstruktor.|
|`with`|[Wyrażenia dopasowania](match-expressions.md)<br /><br />[Wyrażenia obiektów](object-expressions.md)<br /><br />[Kopiowanie i aktualizacja wyrażeń rekordów](copy-and-update-record-expressions.md)<br /><br />[Rozszerzenia typu](type-extensions.md)<br /><br />[Wyjątki: `try...with` wyrażenia](exception-handling/the-try-with-expression.md)|Wraz z `match` słowa kluczowego w wyrażeniach dopasowania do wzorca. Również używane w wyrażeniach obiektu, wyrażeń kopiowania rekordów i rozszerzeń typu, wprowadzenie definicje elementów członkowskich oraz wprowadzenie obsługi wyjątków.|
|`yield`|[Sekwencje](sequences.md)|W wyrażeniu sekwencji służy do uzyskiwania wartości sekwencji.|
|`yield!`|[Wyrażenia obliczeń](computation-expressions.md)<br /><br />[Asynchroniczne przepływy pracy](asynchronous-workflows.md)|Używany w wyrażeniu obliczeń, można dołączyć wynik wyrażenia dane obliczenie do zbierania wyników zawierających wyrażenia obliczeń.|

Następujące generatory kodów są zastrzeżone w języku F #, ponieważ są one słów kluczowych w języku OCaml:

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

Jeśli używasz `--mlcompatibility` — opcja kompilatora, powyżej słowa kluczowe są dostępne do użycia jako identyfikatorów.

Następujące generatory kodów są zastrzeżone słowa kluczowe na przyszłe rozszerzenia języka F #:

* `atomic`
* `break`
* `checked`
* `component`
* `const`
* `constraint`
* `constructor`
* `continue`
* `eager`
* `event`
* `external`
* `functor`
* `include`
* `method`
* `mixin`
* `object`
* `parallel`
* `process`
* `protected`
* `pure`
* `sealed`
* `tailcall`
* `trait`
* `virtual`
* `volatile`

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Odwołanie do symboli i operatorów](symbol-and-operator-reference/index.md)

[Opcje kompilatora](compiler-options.md)
