---
title: Wskazówki dotyczące formatowania kodu F#
description: Poznaj wskazówki dotyczące formatowania kodu języka F#.
ms.date: 11/04/2019
ms.openlocfilehash: dd48380a90ee92b2c1edaaabc116fa1cd8010390
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102492"
---
# <a name="f-code-formatting-guidelines"></a>Wskazówki dotyczące formatowania kodu F#

Ten artykuł zawiera wskazówki dotyczące formatowania kodu, tak aby kod języka F# był:

* Bardziej czytelne
* Zgodnie z konwencjami stosowanymi przez narzędzia formatowania w programie Visual Studio i innych edytorach
* Podobne do innych kodów online

Wytyczne te są oparte na [kompleksowym przewodniku po konwencjach formatowania F#](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) [autorstwa Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Ogólne zasady wcięci

F# domyślnie używa znacznych odstępów. Poniższe wytyczne mają na celu zapewnienie wskazówek, jak żonglować niektórymi wyzwaniami, które może narzucić.

### <a name="using-spaces"></a>Korzystanie z przestrzeni

Jeśli wymagane jest wcięcie, należy użyć spacji, a nie kart. Wymagana jest co najmniej jedna przestrzeń. Organizacja może tworzyć standardy kodowania, aby określić liczbę spacji do użycia do wcięci; dwie, trzy lub cztery spacje wcięci na każdym poziomie, na którym występuje wcięcie jest typowe.

**Zalecamy cztery spacje na wcięcie.**

To powiedzia się, wcięcie programów jest kwestią subiektywną. Odmiany są OK, ale pierwszą zasadą, którą należy przestrzegać, jest *spójność wcięcia*. Wybierz ogólnie akceptowany styl wcięci i używaj go systematycznie w całej bazie kodu.

## <a name="formatting-white-space"></a>Formatowanie odstępu

F# jest czuły na białe przesiewowe. Chociaż większość semantyki z białych spacji są objęte prawidłowym wcięciem, istnieje kilka innych rzeczy do rozważenia.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Operatory formatowania w wyrażeniach arytmetycznych

Zawsze używaj odstępu wokół binarnych wyrażeń arytmetycznych:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Operatory `-` dwuary powinny być zawsze natychmiast następuje wartość, którą negują:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Dodawanie znaku odstępu po `-` operatorze może prowadzić do zamieszania dla innych.

Podsumowując, ważne jest, aby zawsze:

* Operatory binarne surround z odstępem
* Nigdy nie ma spływu białym po operatorze bezemisowym

Szczególnie ważne są wytyczne dotyczące operatora arytmetycznego binarnego. Nieoczynienie `-` otoczyć operatora binarnego w połączeniu z pewnymi opcjami formatowania może prowadzić do interpretacji go jako dwuarchiwa. `-`

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Otaczanie niestandardowej definicji operatora z białymi znakami

Zawsze używaj odstępu do otaczania definicji operatora:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Dla dowolnego niestandardowego operatora, który rozpoczyna się `*` i który ma więcej niż jeden znak, należy dodać biały znak na początku definicji, aby uniknąć niejednoznaczności kompilatora. Z tego powodu zaleca się po prostu otoczyć definicje wszystkich operatorów z jednym znakiem odstępu.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Strzałki parametrów funkcji otoczyć z białymi znakami

Podczas definiowania podpisu funkcji należy użyć `->` odstępu wokół symbolu:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Argumenty funkcji surround z odstępem

Podczas definiowania funkcji należy użyć odstępu wokół każdego argumentu.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a>Umieszczanie parametrów w nowym wierszu dla długich definicji elementów członkowskich

Jeśli masz bardzo długą definicję elementu członkowskiego, umieść parametry w nowych wierszach i wcięj je jednym zakresem.

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

Dotyczy to również konstruktorów:

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>Wpisz adnotacje

#### <a name="right-pad-function-argument-type-annotations"></a>Adnotacje typu argumentu funkcji panelu prawego

Podczas definiowania argumentów z adnotacjami `:` typu należy używać odstępu za symbolem:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Adnotacje typu surround z odstępem

W funkcji let-bound lub adnotacji typu wartości (typ zwracany w przypadku funkcji) należy użyć odstępu przed i po symbolu: `:`

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>Formatowanie pustych wierszy

* Oddziel definicje funkcji najwyższego poziomu i klas dwoma pustymi wierszami.
* Definicje metod wewnątrz klasy są oddzielone pojedynczą pustą linią.
* Dodatkowe puste wiersze mogą być używane (oszczędnie) do oddzielnych grup powiązanych funkcji. Puste wiersze mogą być pominięte między kilka powiązanych one-liners (na przykład zestaw implementacji manekina).
* W funkcjach należy oszczędnie wskazywać sekcje logiczne pustymi wierszami w funkcjach.

## <a name="formatting-comments"></a>Formatowanie komentarzy

Ogólnie preferuje wiele komentarzy z podwójnym ukośnikiem nad komentarzami blokowym w stylu ML.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Komentarze w komentarzach powinny być pisane kapitułą pierwszej litery.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Konwencje nazewnictwa

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Użyj camelCase dla wartości i funkcji związanych z klasą, wyrażeniami i wzorcem

Jest to typowe i akceptowane F# styl używać camelCase dla wszystkich nazw związanych jako zmienne lokalne lub w dopasowywanie wzorca i definicje funkcji.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Lokalnie związane funkcje w klasach należy również użyć camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Użyj camelCase do funkcji publicznych związanych z modułem

Gdy funkcja związana z modułem jest częścią publicznego interfejsu API, należy użyć camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Użyj camelCase dla wewnętrznych i prywatnych wartości i funkcji związanych z modułem

Użyj camelCase dla prywatnych wartości związanych z modułem, w tym następujące:

* Funkcje ad hoc w skryptach

* Wartości tworzące wewnętrzną implementację modułu lub typu

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Użyj camelCase dla parametrów

Wszystkie parametry powinny używać camelCase zgodnie z konwencjami nazewnictwa .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Użyj PascalCase dla modułów

Wszystkie moduły (najwyższego poziomu, wewnętrzne, prywatne, zagnieżdżone) powinny używać PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>PascalCase służy do oznaczania deklaracji typów, elementów członkowskich i etykiet

Klasy, interfejsy, struktury, wyliczenia, delegatów, rekordy i dyskryminowane związki powinny być nazwane pascalcase. Członkowie w ramach typów i etykiet dla rekordów i dyskryminowanych związków powinny również używać PascalCase.

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>PascalCase używa konstrukcji wewnętrznych do platformy .NET

Obszary nazw, wyjątki, zdarzenia i`.dll` nazwy projektu/ powinny również używać PascalCase. Nie tylko to sprawiają, że zużycie z innych języków platformy .NET jest bardziej naturalne dla konsumentów, jest również zgodne z konwencjami nazewnictwa .NET, które mogą wystąpić.

### <a name="avoid-underscores-in-names"></a>Unikaj podkreśleń w nazwach

Historycznie niektóre biblioteki Języka F# używały podkreśleń w nazwach. Jednak nie jest to już powszechnie akceptowane, częściowo dlatego, że ściera się z konwencjami nazewnictwa .NET. To powiedziawia, że niektórzy programiści F# używają podkreśla mocno, częściowo ze względów historycznych, a tolerancja i szacunek jest ważne. Należy jednak pamiętać, że styl jest często nielubiany przez innych, którzy mają wybór, czy go używać.

Jeden wyjątek obejmuje współdziałanie ze składnikami macierzystymi, gdzie podkreślenia są wspólne.

### <a name="use-standard-f-operators"></a>Użyj standardowych operatorów Języka F#

Następujące operatory są zdefiniowane w bibliotece standardowej języka F# i powinny być używane zamiast definiowania odpowiedników. Korzystanie z tych operatorów jest zalecane, ponieważ ma tendencję do kodu bardziej czytelny i idiomatyczny. Deweloperzy z tła w OCaml lub inny funkcjonalny język programowania mogą być przyzwyczajeni do różnych idiomów. Poniższa lista zawiera podsumowanie zalecanych operatorów języka F#.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Użyj składni prefiksu`Foo<T>`dla generycznych ( )`T Foo`zamiast składni poprawek ( )

F# dziedziczy zarówno postfix STYL ML nazewnictwa `int list`typów ogólnych (na przykład), jak również `list<int>`prefiks .NET style (na przykład). Preferuj styl .NET, z wyjątkiem pięciu określonych typów:

1. W przypadku list F# użyj `int list` formularza `list<int>`postfix: zamiast .
2. W przypadku opcji języka F# `int option` użyj `option<int>`formularza postfix: zamiast .
3. W przypadku opcji wartości języka F#użyj formularza postfix: `int voption` zamiast `voption<int>`.
4. W przypadku tablic F# użyj nazwy `int[]` składni, a nie `int array` lub `array<int>`.
5. W przypadku komórek `int ref` referencyjnych należy użyć zamiast `ref<int>` lub `Ref<int>`.

W przypadku wszystkich innych typów należy użyć formularza prefiksu.

## <a name="formatting-tuples"></a>Krotek formatowania

Wystąpienie krotki powinno być w nawiasie, a po rozdzielającym przecinkach w nim `(1, 2)`powinno `(x, y, z)`następować pojedyncza spacja, na przykład: , .

Jest powszechnie akceptowane pominąć nawiasy w dopasowywania wzorów krotek:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Jest również powszechnie akceptowane pominąć nawiasy, jeśli krotka jest zwracana wartość funkcji:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

Podsumowując, preferuj nawiasy wystąpienia spójnej strony, ale podczas korzystania z krotek do dopasowywania wzorców lub wartości zwracanej, jest uważany za w porządku, aby uniknąć nawiasów.

## <a name="formatting-discriminated-union-declarations"></a>Formatowanie dyskryminowanych deklaracji związków zawodowych

Wcięcie `|` w definicji typu przez cztery spacje:

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a>Formatowanie dyskryminowanych związków

Wystąpienia dyskryminowanych związków, które podzielone na wiele wierszy powinny nadać zawartym danym nowy zakres z wcięciem:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Nawias zamykający może również znajdować się w nowym wierszu:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Formatowanie deklaracji rekordów

Wcięcie `{` w definicji typu przez cztery spacje i rozpoczęcie listy pól w tym samym wierszu:

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

Umieszczenie tokenu otwarcia w nowym wierszu i token zamknięcia w nowym wierszu jest korzystne, jeśli deklarujesz implementacje interfejsu lub członków w rekordzie:

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>Formatowanie rekordów

Krótkie rekordy mogą być zapisywane w jednym wierszu:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Rekordy, które są dłuższe, powinny używać nowych wierszy dla etykiet:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Umieszczenie tokenu otwarcia w nowym wierszu, zawartość z kartami w jednym zakresie i token zamknięcia w nowym wierszu jest preferowane, jeśli:

* Przenoszenie rekordów w kodzie z różnymi zakresami wcięci
* Wprowadzenie ich do funkcji

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

Te same reguły mają zastosowanie do elementów listy i tablicy.

## <a name="formatting-copy-and-update-record-expressions"></a>Formatowanie wyrażeń rekordu kopiowania i aktualizowania

Wyrażenie rekordu kopiowania i aktualizacji jest nadal rekordem, więc obowiązują podobne wytyczne.

Krótkie wyrażenia mogą zmieścić się w jednym wierszu:

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

Dłuższe wyrażenia powinny używać nowych wierszy:

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Podobnie jak w przypadku wskazówek dotyczących rekordu, można poświęcić oddzielne wiersze dla nawiasów klamrowych i wcięcie jednego zakresu po prawej stronie za pomocą wyrażenia. W niektórych szczególnych przypadkach, takich jak zawijanie wartości z opcjonalnym bez nawiasów, może być konieczne utrzymanie nawiasu w jednym wierszu:

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a>Formatowanie list i tablic

Pisz `x :: l` z spacjami wokół `::` operatora (`::` jest operatorem infix, stąd otoczony spacjami).

Lista i tablice zadeklarowane w jednym wierszu powinny mieć spację po nawiasie otwierającym i przed nawiasem zamykającym:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Zawsze należy używać co najmniej jednej spacji między dwoma różnymi operatorami przypominającymi nawiasy klamrowe. Na przykład pozostaw `[` spację `{`między a a .

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

Te same wytyczne dotyczą list lub tablic krotek.

Listy i tablice podzielone na wiele wierszy są zgodne z podobną regułą jak rekordy:

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

I podobnie jak w rekordach, deklarowanie nawiasów otwierających i zamykających na własnej linii ułatwi przenoszenie kodu i tworzenie rurociągów do funkcji.

Podczas generowania tablic i list programowo `do ... yield` preferuj, `->` gdy zawsze jest generowana wartość:

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

Starsze wersje języka F# wymagane `yield` określania w sytuacjach, gdy dane mogą być generowane warunkowo lub mogą być kolejne wyrażenia do oceny. Preferuj pominięcie tych `yield` słów kluczowych, chyba że musisz skompilować ze starszą wersją języka F#:

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

W niektórych `do...yield` przypadkach, może pomóc w czytelności. Przypadki te, choć subiektywne, powinny być brane pod uwagę.

## <a name="formatting-if-expressions"></a>Formatowanie, jeśli wyrażenia

Wcięcie warunkowości zależy od rozmiarów wyrażeń, które je tworzą. Jeśli `cond` `e1` , `e2` i są krótkie, po prostu napisz je w jednym wierszu:

```fsharp
if cond then e1 else e2
```

Jeśli albo `cond` `e1` , `e2` lub są dłuższe, ale nie wieloliniowe:

```fsharp
if cond
then e1
else e2
```

Jeśli którekolwiek z wyrażeń jest wielowierszowe:

```fsharp
if cond then
    e1
else
    e2
```

Wiele warunków z `elif` `else` i są wcięciami `if`w tym samym zakresie co:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Konstrukcje dopasowywania wzorców

Użyj `|` a dla każdej klauzuli dopasowania bez wcięci. Jeśli wyrażenie jest krótkie, można rozważyć użycie pojedynczego wiersza, jeśli każde wyrażenie podrzędne jest również proste.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Jeśli wyrażenie po prawej stronie strzałki dopasowania wzorca jest zbyt duże, przenieś go `match` / `|`do następującego wiersza, wciętego o jeden krok od .

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Dopasowywanie wzorców funkcji `function`anonimowych, począwszy od , na ogół nie powinno wcięcie zbyt daleko. Na przykład wcięcie jednego zakresu w następujący sposób jest w porządku:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Dopasowywanie wzorca `let rec` w funkcjach zdefiniowanych przez `let` `let` lub `function` powinny być wcięte cztery spacje po rozpoczęciu , nawet jeśli używane jest słowo kluczowe:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nie zaleca się wyrównywania strzałek.

## <a name="formatting-trywith-expressions"></a>Formatowanie try/z wyrażeniami

Dopasowanie wzorca na typie wyjątku powinno być `with`wcięcie na tym samym poziomie co .

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>Aplikacja parametrów funkcji formatowania

Ogólnie rzecz biorąc większość aplikacji parametr funkcji odbywa się w tym samym wierszu.

Jeśli chcesz zastosować parametry do funkcji w nowym wierszu, wcięj je według jednego zakresu.

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

Te same wytyczne dotyczą wyrażeń lambda jako argumentów funkcji. Jeśli treść wyrażenia lambda, obiekt może mieć inny wiersz, wcięcie przez jeden zakres

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

Jeśli jednak treść wyrażenia lambda jest więcej niż jeden wiersz, należy wziąć pod uwagę faktoringu go do oddzielnej funkcji, a nie mają wielowierszowej konstrukcji stosowane jako pojedynczy argument do funkcji.

### <a name="formatting-infix-operators"></a>Formatowanie operatorów infix

Oddziel operatory według spacji. Oczywiste wyjątki od tej `!` `.` reguły są i operatorów.

Wyrażenia Infix są ok do linii w tej samej kolumnie:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formatowanie operatorów potoków

Operatorzy potoku `|>` powinny przejść pod wyrażenia, na których działają.

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a>Moduły formatowania

Kod w module lokalnym musi być wcięcie względem modułu, ale kod w module najwyższego poziomu nie powinny być wcięcie. Elementy obszaru nazw nie muszą być wcięciowe.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Formatowanie wyrażeń i interfejsów obiektów

Wyrażenia i interfejsy obiektów powinny być wyrównane `member` w taki sam sposób, jak wcięcie po czterech spacjach.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Formatowanie odstępu w wyrażeniach

Unikaj obcych odstępów w wyrażeniach Języka F#.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Nazwane argumenty nie powinny `=`również mieć miejsca wokół :

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Atrybuty formatowania

[Atrybuty](../language-reference/attributes.md) są umieszczane nad konstrukcją:

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a>Formatowanie atrybutów parametrów

Atrybuty można również umieszczać na parametrach. W takim przypadku umieść następnie w tym samym wierszu co parametr i przed nazwą:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Formatowanie wielu atrybutów

Gdy wiele atrybutów są stosowane do konstrukcji, która nie jest parametrem, powinny być umieszczone w taki sposób, że istnieje jeden atrybut na wiersz:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Po zastosowaniu do parametru, muszą one znajdować się `;` w tej samej linii i oddzielone separatorem.

## <a name="formatting-literals"></a>Formatowanie literałów

[Literały F#](../language-reference/literals.md) używające atrybutu `Literal` powinny umieszczać atrybut we własnym wierszu i używać nazewnictwa PascalCase:

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Należy unikać umieszczania atrybutu w tym samym wierszu co wartość.
