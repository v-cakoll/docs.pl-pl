---
title: Odwołanie do słowa kluczowego
description: Znajdź łącza do informacji o wszystkich słowach kluczowych języka F#.
f1_keywords:
- new_FS
- use_FS
- end_FS
- lsl_FS
- exception_FS
- asr_FS
- if_FS
- internal_FS
- default_FS
- in_FS
- lsr_FS
- open_FS
- static_FS
- assert_FS
- match_FS
- land_FS
- with_FS
- inherit_FS
- mutable_FS
- downto_FS
- false_FS
- sig_FS
- and_FS
- true_FS
- namespace_FS
- public_FS
- lxor_FS
- val_FS
- void_FS
- downcast_FS
- function_FS
- while_FS
- for_FS
- class_FS
- done_FS
- to_FS
- module_FS
- let_FS
- delegate_FS
- abstract_FS
- then_FS
- when_FS
- lazy_FS
- try_FS
- inline_FS
- do_FS
- upcast_FS
- begin_FS
- base_FS
- fun_FS
- struct_FS
- as_FS
- extern_FS
- null_FS
- lor_FS
- return_FS
- mod_FS
- private_FS
- of_FS
- or_FS
- member_FS
- type_FS
- rec_FS
- elif_FS
- override_FS
- interface_FS
- yield_FS
- else_FS
- finally_FS
- global_FS
- select_FS
- use!_FS
dev_langs:
- FSharp
ms.date: 11/04/2019
ms.openlocfilehash: 34959f471406643e85990c2c80a38a684759a7f9
ms.sourcegitcommit: b16eacb6f94a5b601882a861ad17cc5470a8d5d5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80352308"
---
# <a name="keyword-reference"></a>Odwołanie do słowa kluczowego

Ten temat zawiera łącza do informacji o wszystkich słowach kluczowych języka F#.

## <a name="f-keyword-table"></a>Tabela słów kluczowych F#

W poniższej tabeli przedstawiono wszystkie słowa kluczowe języka F# w kolejności alfabetycznej, wraz z krótkimi opisami i łączami do odpowiednich tematów, które zawierają więcej informacji.

|Słowo kluczowe|Link|Opis|
|-------|----|-----------|
|`abstract`|[Elementy członkowskie](./members/index.md)<br /><br />[Klasy abstrakcyjne](abstract-classes.md)|Wskazuje metodę, która albo nie ma implementacji w typie, w którym jest zadeklarowany lub jest wirtualny i ma domyślną implementację.|
|`and`|[`let`Powiązania](./functions/let-bindings.md)<br /><br />[Rekordy](records.md)<br /><br />[Elementy członkowskie](./members/index.md)<br /><br />[Ograniczenia](./generics/constraints.md)|Używane w wzajemnie cyklicznych powiązań i rekordów, w deklaracjach właściwości i z wieloma ograniczeniami parametrów ogólnych.|
|`as`|[Klasy](classes.md)<br /><br />[Dopasowanie wzorca](Pattern-Matching.md)|Służy do nadawanie bieżącemu obiektowi klasy nazwy obiektu. Używany również do nadania nazwy całemu wzorcowi w dopasowanym wzorcu.|
|`assert`|[Asercje](assertions.md)|Służy do weryfikowania kodu podczas debugowania.|
|`base`|[Klasy](classes.md)<br /><br />[Dziedziczenie](inheritance.md)|Używany jako nazwa obiektu klasy podstawowej.|
|`begin`|[Pełna składnia](verbose-syntax.md)|W pełnej składni wskazuje początek bloku kodu.|
|`class`|[Klasy](classes.md)|W składni pełnej wskazuje początek definicji klasy.|
|`default`|[Elementy członkowskie](./members/index.md)|Wskazuje implementację metody abstrakcyjnej; używane razem z deklaracją metody abstrakcyjnej w celu utworzenia metody wirtualnej.|
|`delegate`|[Delegaty](delegates.md)|Służy do deklarowania delegata.|
|`do`|[Powiązania „do”](./functions/do-bindings.md)<br /><br />[Pętle: `for...to` Wyrażenie](loops-for-to-expression.md)<br /><br />[Pętle: `for...in` Wyrażenie](loops-for-in-expression.md)<br /><br />[Pętle: `while...do` Wyrażenie](loops-while-do-expression.md)|Używane w konstrukcji pętli lub do wykonywania kodu imperatywu.|
|`done`|[Pełna składnia](verbose-syntax.md)|W składni pełnej wskazuje koniec bloku kodu w wyrażeniu pętli.|
|`downcast`|[Rzutowanie i konwersje](casting-and-conversions.md)|Służy do konwersji do typu, który jest niższy w łańcuchu dziedziczenia.|
|`downto`|[Pętle: `for...to` Wyrażenie](loops-for-to-expression.md)|W `for` wyrażeniu używanym podczas liczenia w odwrotnej kolejności.|
|`elif`|[Wyrażenia warunkowe:`if...then...else`](conditional-expressions-if-then-else.md)|Używane w rozgałęzieniach warunkowych. Krótka `else if`forma .|
|`else`|[Wyrażenia warunkowe:`if...then...else`](conditional-expressions-if-then-else.md)|Używane w rozgałęzieniach warunkowych.|
|`end`|[Struktury](structures.md)<br /><br />[Sumy rozłączne](discriminated-unions.md)<br /><br />[Rekordy](records.md)<br /><br />[Rozszerzenia typu](type-extensions.md)<br /><br />[Pełna składnia](verbose-syntax.md)|W definicjach typów i rozszerzeniach typów wskazuje koniec sekcji definicji elementów członkowskich.<br /><br />W składni pełnej, służy do określenia końca bloku kodu, który `begin` rozpoczyna się od słowa kluczowego.|
|`exception`|[Obsługa wyjątków](./exception-handling/index.md)<br /><br />[Typy wyjątków](./exception-handling/exception-types.md)|Służy do deklarowania typu wyjątku.|
|`extern`|[Funkcje zewnętrzne](./functions/external-functions.md)|Wskazuje, że zadeklarowany element programu jest zdefiniowany w innym pliku binarnym lub zestawie.|
|`false`|[Typy pierwotne](basic-types.md)|Używany jako literał logiczny.|
|`finally`|[Wyjątki: `try...finally` Wyrażenie](./exception-handling/the-try-finally-expression.md)|Używane razem `try` z wprowadzeniem bloku kodu, który wykonuje niezależnie od tego, czy wystąpi wyjątek.|
|`fixed`|[Stałe](fixed.md)|Służy do "pin" wskaźnik na stosie, aby zapobiec jego śmieci zebrane.|
|`for`|[Pętle: `for...to` Wyrażenie](loops-for-to-expression.md)<br /><br />[Pętle: wyrażenie for...in](loops-for-in-expression.md)|Używane w konstrukcjach pętli.|
|`fun`|[Wyrażenia Lambda: `fun` Słowo kluczowe](./functions/lambda-expressions-the-fun-keyword.md)|Używane w wyrażeniach lambda, znanych również jako funkcje anonimowe.|
|`function`|[Wyrażenia dopasowania](match-expressions.md)<br /><br />[Wyrażenia Lambda: Zabawne słowo kluczowe](./functions/lambda-expressions-the-fun-keyword.md)|Używany jako krótsza `fun` alternatywa `match` dla słowa kluczowego i wyrażenie w wyrażeniu lambda, który ma wzorzec pasujący do pojedynczego argumentu.|
|`global`|[Namespaces](namespaces.md)|Służy do odwoływania się do obszaru nazw platformy .NET najwyższego poziomu.|
|`if`|[Wyrażenia warunkowe:`if...then...else`](conditional-expressions-if-then-else.md)|Używane w konstrukcjach rozgałęziania warunkowego.|
|`in`|[Pętle: wyrażenie for...in](loops-for-in-expression.md)<br /><br />[Pełna składnia](verbose-syntax.md)|Używane do wyrażeń sekwencji i, w pełnej składni, do oddzielania wyrażeń od powiązań.|
|`inherit`|[Dziedziczenie](inheritance.md)|Służy do określania klasy podstawowej lub interfejsu podstawowego.|
|`inline`|[Funkcje](./functions/index.md)<br /><br />[Funkcje wbudowane](./functions/inline-functions.md)|Służy do wskazania funkcji, która powinna być zintegrowana bezpośrednio z kodem wywołującego.|
|`interface`|[Interfejsy](interfaces.md)|Służy do deklarowania i implementowania interfejsów.|
|`internal`|[Kontrola dostępu](access-control.md)|Służy do określania, że element członkowski jest widoczny wewnątrz zestawu, ale nie poza nim.|
|`lazy`|[Wyrażenia z opóźnionym obliczaniem](lazy-expressions.md)|Służy do określania wyrażenia, które ma być wykonywane tylko wtedy, gdy potrzebny jest wynik.|
|`let`|[`let`Powiązania](./functions/let-bindings.md)|Służy do kojarzenia lub powiązania nazwy z wartością lub funkcją.|
|`let!`|[Asynchroniczne przepływy pracy](asynchronous-workflows.md)<br /><br />[Wyrażenia obliczeń](computation-expressions.md)|Używane w asynchronicznych przepływach pracy do powiązania nazwy z wynikiem obliczeń asynchronicznych lub, w innych wyrażeniach obliczeniowych, używanych do powiązania nazwy z wynikiem, który jest typem obliczeń.|
|`match`|[Wyrażenia dopasowania](match-expressions.md)|Służy do rozgałęzienia przez porównanie wartości ze wzorcem.|
|`match!`|[Wyrażenia obliczeń](computation-expressions.md#match)|Służy do wbudowanego wywołania wyrażenia obliczeń i wzorca zgodnego z jego wynikiem.|
|`member`|[Elementy członkowskie](./members/index.md)|Służy do deklarowania właściwości lub metody w typie obiektu.|
|`module`|[Moduły](modules.md)|Służy do kojarzenia nazwy z grupą powiązanych typów, wartości i funkcji, aby logicznie oddzielić ją od innego kodu.|
|`mutable`|[Powiązania „let”](./functions/let-bindings.md)|Służy do deklarowania zmiennej, czyli wartości, którą można zmienić.|
|`namespace`|[Namespaces](namespaces.md)|Służy do skojarzenia nazwy z grupą powiązanych typów i modułów, aby logicznie oddzielić ją od innego kodu.|
|`new`|[Konstruktorów](./members/constructors.md)<br /><br />[Ograniczenia](./generics/constraints.md)|Służy do deklarowania, definiowania lub wywoływania konstruktora, który tworzy lub który może utworzyć obiekt.<br /><br />Używany również w ogólnych ograniczeń parametrów, aby wskazać, że typ musi mieć pewien konstruktor.|
|`not`|[Odwołanie do symboli i operatorów](./symbol-and-operator-reference/index.md)<br /><br />[Ograniczenia](./generics/constraints.md)|W rzeczywistości nie jest to słowo kluczowe. Jednak `not struct` w połączeniu jest używany jako ograniczenie parametru ogólnego.|
|`null`|[Wartości null](./values/null-values.md)<br /><br />[Ograniczenia](./generics/constraints.md)|Wskazuje brak obiektu.<br /><br />Używany również w ogólnych ograniczeniach parametrów.|
|`of`|[Sumy rozłączne](discriminated-unions.md)<br /><br />[Delegaty](delegates.md)<br /><br />[Typy wyjątków](./exception-handling/exception-types.md)|Używane w związkach dyskryminowanych do wskazywania typu kategorii wartości oraz w deklaracjach delegata i wyjątków.|
|`open`|[Deklaracje importu: słowo `open` kluczowe](import-declarations-the-open-keyword.md)|Służy do udostępniania zawartości obszaru nazw lub modułu bez kwalifikacji.|
|`or`|[Odwołanie do symboli i operatorów](./symbol-and-operator-reference/index.md)<br /><br />[Ograniczenia](./generics/constraints.md)|Używany z warunkami logicznymi `or` jako operator logiczny. Odpowiednik `||`.<br /><br />Używany również w ograniczeniach członkowskich.|
|`override`|[Elementy członkowskie](./members/index.md)|Służy do implementowania wersji metody abstrakcyjnej lub wirtualnej, która różni się od wersji podstawowej.|
|`private`|[Kontrola dostępu](access-control.md)|Ogranicza dostęp do elementu członkowskiego do kodu w tym samym typie lub module.|
|`public`|[Kontrola dostępu](access-control.md)|Umożliwia dostęp do elementu członkowskiego spoza typu.|
|`rec`|[Funkcje](./functions/index.md)|Służy do wskazania, że funkcja jest cykliczna.|
|`return`|[Asynchroniczne przepływy pracy](Asynchronous-Workflows.md)<br /><br />[Wyrażenia obliczeń](computation-expressions.md)|Służy do wskazania wartości do podania w wyniku wyrażenia obliczeń.|
|`return!`|[Wyrażenia obliczeń](computation-expressions.md)<br /><br />[Asynchroniczne przepływy pracy](asynchronous-workflows.md)|Służy do wskazania wyrażenia obliczeń, które po ocenie zapewnia wynik zawierającego wyrażenie obliczeniowe.|
|`select`|[Wyrażenia zapytania](query-expressions.md)|Używane w wyrażeniach kwerendy do określania pól lub kolumn do wyodrębnienia. Należy zauważyć, że jest to kontekstowe słowo kluczowe, co oznacza, że w rzeczywistości nie jest słowem zastrzeżonym i działa tylko jak słowo kluczowe w odpowiednim kontekście.|
|`static`|[Elementy członkowskie](./members/index.md)|Służy do wskazania metody lub właściwości, które mogą być wywoływane bez wystąpienia typu lub elementu członkowskiego wartości, który jest współużytkowane przez wszystkie wystąpienia typu.|
|`struct`|[Struktury](structures.md)<br /><br /> [Krotki](tuples.md)<br/><br/>[Ograniczenia](./generics/constraints.md)|Służy do deklarowania typu struktury.<br /><br/>Służy do określania krotki struktury.<br/><br />Używany również w ogólnych ograniczeniach parametrów.<br /><br />Używane do zgodności OCaml w definicjach modułów.|
|`then`|[Wyrażenia warunkowe:`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Konstruktorów](./members/constructors.md)|Używane w wyrażeniach warunkowych.<br /><br />Również do wykonywania skutków ubocznych po budowie obiektu.|
|`to`|[Pętle: `for...to` Wyrażenie](loops-for-to-expression.md)|Używane `for` w pętlach do wskazania zakresu.|
|`true`|[Typy pierwotne](basic-types.md)|Używany jako literał logiczny.|
|`try`|[Wyjątki: try...with — Wyrażenie](./exception-handling/the-try-with-expression.md)<br /><br />[Wyjątki: try...finally — Wyrażenie](./exception-handling/the-try-finally-expression.md)|Służy do wprowadzenia bloku kodu, który może generować wyjątek. Używane razem `with` `finally`z lub .|
|`type`|[Typy F#](fsharp-types.md)<br /><br />[Klasy](classes.md)<br /><br />[Rekordy](records.md)<br /><br />[Struktury](structures.md)<br /><br />[Wyliczenia](enumerations.md)<br /><br />[Sumy rozłączne](discriminated-unions.md)<br /><br />[Skróty typów](type-abbreviations.md)<br /><br />[Jednostki miary](units-of-measure.md)|Służy do deklarowania klasy, rekordu, struktury, unii dyskryminowanej, typu wyliczenia, jednostki miary lub skrótu typu.|
|`upcast`|[Rzutowanie i konwersje](casting-and-conversions.md)|Służy do konwersji do typu, który jest wyższy w łańcuchu dziedziczenia.|
|`use`|[Zarządzanie zasobami: słowo `use` kluczowe](resource-management-the-use-keyword.md)|Używane zamiast `let` dla wartości, `Dispose` które wymagają wywołania do wolnych zasobów.|
|`use!`|[Wyrażenia obliczeń](computation-expressions.md)<br /><br />[Asynchroniczne przepływy pracy](asynchronous-workflows.md)|Używane zamiast `let!` w asynchronicznych przepływów pracy i innych wyrażeń obliczeniowych dla wartości, które wymagają `Dispose` wywołania wolnych zasobów.|
|`val`|[Pola jawne: słowo kluczowe `val`](./members/explicit-fields-the-val-keyword.md)<br /><br />[Podpisy](signature-files.md)<br /><br />[Elementy członkowskie](./members/index.md)|Używane w podpisie, aby wskazać wartość lub w typie do deklarowania elementu członkowskiego, w ograniczonych sytuacjach.|
|`void`|[Typy pierwotne](basic-types.md)|Wskazuje typ .NET. `void` Używane podczas współpracy z innymi językami platformy .NET.|
|`when`|[Ograniczenia](./generics/constraints.md)|Używane dla warunków logicznych *(gdy osłony)* na dopasowanie wzorca i wprowadzenie klauzuli ograniczenia dla parametru typu ogólnego.|
|`while`|[Pętle: `while...do` Wyrażenie](loops-while-do-expression.md)|Wprowadza konstrukcję pętli.|
|`with`|[Wyrażenia dopasowania](match-expressions.md)<br /><br />[Wyrażenia obiektów](object-expressions.md)<br /><br />[Kopiowanie i aktualizacja wyrażeń rekordów](copy-and-update-record-expressions.md)<br /><br />[Rozszerzenia typu](type-extensions.md)<br /><br />[Wyjątki: `try...with` Wyrażenie](./exception-handling/the-try-with-expression.md)|Używane razem `match` ze słowem kluczowym w wyrażeniach dopasowywania wzorców. Używane również w wyrażeniach obiektów, wyrażeń kopiowania rekordów i rozszerzenia typu, aby wprowadzić definicje elementów członkowskich i wprowadzić programy obsługi wyjątków.|
|`yield`|[Listy,](lists.md) [tablice,](arrays.md) [sekwencje](sequences.md)|Używane w wyrażeniu listy, tablicy lub sekwencji do tworzenia wartości sekwencji. Zazwyczaj można pominąć, ponieważ jest niejawna w większości sytuacji.|
|`yield!`|[Wyrażenia obliczeń](computation-expressions.md)<br /><br />[Asynchroniczne przepływy pracy](asynchronous-workflows.md)|Używane w wyrażeniu obliczeniowym do dołączania wyniku danego wyrażenia obliczeniowego do kolekcji wyników dla zawierającego wyrażenie obliczeniowe.|

Następujące tokeny są zarezerwowane w języku F#, ponieważ są słowami kluczowymi w języku OCaml:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

Jeśli używasz `--mlcompatibility` opcji kompilatora, powyższe słowa kluczowe są dostępne do użycia jako identyfikatory.

Następujące tokeny są zarezerwowane jako słowa kluczowe dla przyszłego rozszerzenia języka F#:

- `atomic`
- `break`
- `checked`
- `component`
- `const`
- `constraint`
- `constructor`
- `continue`
- `eager`
- `event`
- `external`
- `functor`
- `include`
- `method`
- `mixin`
- `object`
- `parallel`
- `process`
- `protected`
- `pure`
- `sealed`
- `tailcall`
- `trait`
- `virtual`
- `volatile`

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka F#](index.md)
- [Odwołanie do symboli i operatorów](./symbol-and-operator-reference/index.md)
- [Opcje kompilatora](compiler-options.md)
