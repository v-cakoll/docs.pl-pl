---
title: 'Wskazówki dotyczące formatowania kodu F #'
description: 'Dowiedz się, wskazówki dotyczące formatowania kodu F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 0d7d2d1771710db55bf990f3a06079b2aec48fd7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858008"
---
# <a name="f-code-formatting-guidelines"></a>Wskazówki dotyczące formatowania kodu F #

Ten artykuł zawiera wskazówki dotyczące formatowania kodu, aby Twój kod F #:

* Zazwyczaj są wyświetlane jako bardziej czytelne.
* Jest zgodna z konwencjami stosowane przez formatowanie narzędzi w programie Visual Studio i innych edytorów
* Podobnie jak inny kod w trybie online

Te wytyczne są oparte na [kompletny przewodnik po F # konwencje dotyczące formatowania](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) przez [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Ogólne reguły dotyczące wcięć

F # domyślnie używa istotnych białych. Poniższe wskazówki są przeznaczone do zapewnienia wskazówek dotyczących tego, jak łatwiejszą obsługę niektóre wyzwania, które może to powodować.

### <a name="using-spaces"></a>Przy użyciu miejsc do magazynowania

Gdy wymagana jest wcięcia, należy użyć miejsca do magazynowania, nie karty. Wymagane jest co najmniej jedną spację. Twoja organizacja może tworzyć norm kodowania, aby określić liczbę miejsc do magazynowania na potrzeby wcięć; Typowe jest dwóch, trzech lub czterech spacji wcięcia na każdym poziomie, w którym występuje wcięcia.

**Firma Microsoft zaleca 4 odstępów na znak wcięcia.**

Inaczej mówiąc, wcięcia programy polega na subiektywnej. Różnice są dozwolone, ale jest pierwszą regułę, należy wykonać *spójności wcięcia*. Wybierz powszechnie akceptowane styl wcięcia i systematycznie używane w całej bazie kodu.

## <a name="formatting-blank-lines"></a>Formatowanie puste wiersze

* Oddzielne najwyższego poziomu funkcji i klas definicje z dwóch pustych wierszy.
* Definicje metody wewnątrz klasy są oddzielone pojedynczy pusty wiersz.
* Dodatkowe puste wiersze, które mogą (rzadko) używane do oddzielania grup pokrewnych funkcji. Puste wiersze mogą być pominięte między wiele powiązanych one-liners (na przykład set fikcyjne implementacje).
* Użyj rzadko, puste wiersze w funkcji, aby wskazać logiczne sekcje.

## <a name="formatting-comments"></a>Formatowanie komentarze

Zazwyczaj preferują wielu komentarzy podwójnego ukośnika, za pośrednictwem komentarze bloku stylu uczenia Maszynowego.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Komentarze w tekście powinien wielką literą.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Konwencje nazewnictwa

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Użyj camelCase dla wartości powiązane z klasy, powiązane z wyrażenia i powiązane z wzorca i funkcji

Powszechne jest wprowadzanie i zaakceptowane F # stylu camelCase dla wszystkich nazw powiązany jako zmienne lokalne lub dopasowania do wzorca i definicje funkcji.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Funkcje lokalnie granicę w klasach należy również użyć camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Użyj camelCase dla funkcji publicznych powiązanych z modułu

Gdy funkcja powiązane z modułu jest częścią publicznego interfejsu API, powinna korzystać camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Użyj camelCase dla wartości powiązane z modułu wewnętrzne i prywatne i funkcji

Użyj camelCase dla wartości powiązane z modułu prywatne, takie jak następujące:

* Funkcje ad hoc w skryptach

* Tworzących wewnętrzną implementację modułu lub typu wartości

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Użyj camelCase dla parametrów

Wszystkie parametry powinny używać camelCase zgodnie z konwencjami nazewnictwa platformy .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Użyj PascalCase dla modułów

Wszystkie moduły (najwyższego poziomu wewnętrznej, prywatne i zagnieżdżone) powinny używać PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>PascalCase na użytek deklaracji typów, elementów członkowskich i etykiety

Klasy, interfejsy, struktury, wyliczenia, delegatów, rekordy i sumy rozłączne powinny mieć wszystkie nazwę z PascalCase. Członków w ramach typów i etykiet rekordów i sumy rozłączne należy również użyć PascalCase.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Użyj PascalCase dla konstrukcji na wewnętrzne dla oprogramowania .NET

Przestrzenie nazw, wyjątki, zdarzenia i projekt /`.dll` nazwy należy również użyć PascalCase. Nie tylko jest to, że zużycie z innymi językami .NET bardziej naturalnych dla konsumentów, również jest ona zgodna z konwencjami nazewnictwa platformy .NET, które mogą wystąpić.

### <a name="avoid-underscores-in-names"></a>Należy unikać podkreślenia w nazwach

W przeszłości niektórych bibliotek F # używanych podkreślenia w nazwach. Jednak to się nie są już powszechnie akceptowane, częściowo, ponieważ ona jest niezgodna z konwencjami nazewnictwa platformy .NET. Inaczej mówiąc, niektórych programistów języka F # użyj podkreślenia intensywnie, częściowo ze względów historycznych, a na uszkodzenia i przestrzegania jest ważne. Należy jednak pamiętać, że styl jest często disliked przez innych użytkowników, którzy mają możliwość wyboru o tym, czy z niego korzystać.

Niektóre wyjątki obejmuje współdziałanie z składnikami macierzystymi, gdzie są bardzo popularne znaki podkreślenia.

### <a name="use-standard-f-operators"></a>Użyj standardowych operatorów F #

Następujące operatory są zdefiniowane w standardowej bibliotece języka F # i powinny być używane zamiast zdefiniowanie odpowiedniki. Korzystanie z tych operatorów jest zalecane, ponieważ sprawia kod bardziej czytelne i idiomatyczną. Deweloperów z doświadczeniem w OCaml lub innych funkcjonalny język programowania może być przyzwyczajeni do różnych idiomy. Poniższa lista zawiera podsumowanie zalecanych operatory języka F #.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Użyj składni prefiks dla typów ogólnych (`Foo<T>`) zamiast składni przyrostka (`T Foo`)

F # dziedziczy zarówno przyrostkowe ML styl nazewnictwa typów ogólnych (na przykład `int list`) oraz prefiks stylu .NET (na przykład `list<int>`). Preferuj styl .NET, z wyjątkiem czterech określonych typów:

1. Dla listy języka F #, należy użyć formy przyrostkowe: `int list` zamiast `list<int>`.
2. Opcje F #, można użyć w przyrostkowej formy: `int option` zamiast `option<int>`.
3. Dla tablic F #, należy użyć składni nazwy `int[]` zamiast `int array` lub `array<int>`.
4. Komórki odwołań, można użyć `int ref` zamiast `ref<int>` lub `Ref<int>`.

W przypadku wszystkich innych typów formularz prefiks.

## <a name="formatting-tuples"></a>Formatowanie krotki

Wystąpienia krotki powinien być ujęty w nawiasy i ograniczająca przecinkami w ramach powinno następować pojedyncza spacja, na przykład: `(1, 2)`, `(x, y, z)`.

Przyjęto często pominąć nawiasów w krotek dopasowywanie do wzorców:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a>Formatowanie Suma rozłączna deklaracje złożeń

Zwiększ wcięcie `|` w definicji typu spacjami 4:

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

## <a name="formatting-discriminated-unions"></a>Formatowanie rekord z wariantami

Utworzona Suma rozłączna Unii, które podzielone między wiele wierszy, powinien zapewnić zawartymi danymi nowego zakresu z wcięciem:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Nawias zamykający mogą być także w nowym wierszu:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Formatowanie deklaracje rekordu

Zwiększ wcięcie `{` w typie definicji przez 4 spacji i umożliwia rozpoczęcie listy pól w tym samym wierszu:

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

Wprowadzanie tokenu otwierania na tym samym wierszu i token zamknięcia w nowym wierszu jest również dobrym rozwiązaniem, ale należy pamiętać, że należy użyć [Pełna składnia](../language-reference/verbose-syntax.md) do definiowania elementów członkowskich ( `with` — słowo kluczowe):

```fsharp
//  OK, but verbose syntax required
type PostalAddress = { 
    Address: string
    City: string
    Zip: string
} with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
```

## <a name="formatting-records"></a>Formatowanie rekordów

Krótkie rekordy mogą być napisane w jednym wierszu:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Rekordy, które są dłuższe należy używać nowych wierszy dla etykiet:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Wprowadzanie tokenu otwierania na tym samym wierszu i token zamknięcia w nowym wierszu jest również dobrym rozwiązaniem:

```fsharp
let rainbow = {
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
```

Te same zasady mają zastosowanie dla elementów listy i tablicy.

## <a name="formatting-lists-and-arrays"></a>Formatowanie, list i tablice

Zapis `x :: l` zawierające spacje wokół `::` — operator (`::` jest operator wrostkowe, dlatego otoczony spacjami) i `[1; 2; 3]` (`;` to ogranicznik, dlatego następuje spacja).

Zawsze należy używać co najmniej jedną spację między dwa różne operatory podobne do nawiasu klamrowego. Na przykład, pozostaw odstęp między `[` i `{`.

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

Listy i tablic, które podzielone między wiele wierszy wykonaj regułę podobne jak rekordy:

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a>Jeśli formatowania wyrażeń

Wcięcie warunkowych zależy od wielkości wyrażeń, które je tworzą. Jeśli `cond`, `e1` i `e2` krótki, po prostu zostaną zapisane w jednym wierszu:

```fsharp
if cond then e1 else e2
```

Jeśli `cond`, `e1` lub `e2` dłużej, ale nie wiele wierszy:

```fsharp
if cond
then e1
else e2
```

Jeśli dowolne wyrażenie z wielowierszowym:

```fsharp
if cond then
    e1
else
    e2
```

Wiele warunkowych z `elif` i `else` tworzone jest wcięcie na tym samym zakresie co `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Konstrukcje dopasowywania wzorca

Użyj `|` dla każdej klauzuli dopasowania z wcięciem nie. Jeśli wyrażenie jest krótki, można rozważyć użycie pojedynczy wiersz, jeśli każdy Podwyrażenie również jest proste.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Jeśli wyrażenie po prawej stronie strzałkę dopasowania wzorca jest zbyt duży, przenieś go do następujący wiersz z wcięciami jeden krok z `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Dopasowanie z funkcjami anonimowymi uruchomienie wzorca `function`, powinien ogólnie nie twórz wcięcie zbyt daleko. Na przykład następujący wcięcia jeden zakres jest w dobrym stanie:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Dopasowanie do wzorca w funkcje zdefiniowane przez `let` lub `let rec` powinien być z wcięciami 4 spacji po uruchomieniu programu `let`nawet wtedy, gdy `function` słowo kluczowe jest używane:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nie zaleca się dopasowanie strzałki.

## <a name="formatting-trywith-expressions"></a>Spróbuj formatowania / przy użyciu wyrażeń

Powinien być wcięty dopasowania do wzorca w typ wyjątku, w tym samym poziomie co `with`.

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

## <a name="formatting-function-parameter-application"></a>Formatowanie aplikacji parametru — funkcja

Ogólnie rzecz biorąc większość funkcji parametr aplikacji odbywa się w tym samym wierszu.

Jeśli chcesz zastosować parametrów do funkcji w nowym wierszu wcięcie je przez jeden zakres.

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

Te same wytyczne mają zastosowanie w przypadku wyrażenia lambda jako argumenty funkcji. Jeżeli treść wyrażenia lambda, jednostka może mieć innego wiersza, zawiera tylko przez jeden zakres

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

Jednakże jeśli treść wyrażenia lambda jest więcej niż jeden wiersz, należy wziąć pod uwagę, uwzględniając ją w to oddzielna funkcja zamiast konstrukcję wielowierszowe stosowane jako pojedynczy argument do funkcji.

### <a name="formatting-infix-operators"></a>Formatowanie operatory wrostkowe

Oddzielne operatory spacjami. Oczywiste wyjątki od tej reguły są `!` i `.` operatorów.

Wyrażenia wrostkowe są OK oferty na tej samej kolumnie:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formatowanie operatorów potoku

Potok `|>` operatory powinny przechodzić poniżej wyrażeń działają na.

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

### <a name="formatting-modules"></a>Formatowanie modułów

Kod w lokalnym module musi być wcięty względem modułu, ale nie powinien być wcięty kodu w module najwyższego poziomu. Nie masz elementy Namespace wcięcia.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Wyrażenia obiektów formatowania i interfejsy

Wyrażenia obiektów i interfejsy, które powinno być wyrównane tak samo jak przy użyciu `member` tworzone jest wcięcie po 4 miejsc do magazynowania.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Formatowanie biały znak w wyrażeniach

Należy unikać nadmiarowe biały znak w wyrażeniach języka F #.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Argumenty nazwane również nie powinny mieć miejsca wokół `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
