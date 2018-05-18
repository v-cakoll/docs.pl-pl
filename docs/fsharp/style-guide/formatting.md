---
title: 'Wytyczne Formatowani kodu języka F #'
description: 'Dowiedz się wskazówki dotyczące formatowania kodu F #.'
ms.date: 05/14/2018
ms.openlocfilehash: e5c700ca9ae3968243f11c1237b9e4b26e580dcf
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="f-code-formatting-guidelines"></a>Wskazówki dotyczące formatowania kodu języka F #

Ten artykuł zawiera wskazówki dotyczące formatowania kodu tak, aby w kodzie języka F # jest:

* Zazwyczaj są wyświetlane jako bardziej czytelne.
* Jest zgodnie z konwencjami stosowane przez formatowania narzędzia w programie Visual Studio i innych edytorów
* Podobnie jak inne kodem online

Niniejsze wytyczne dotyczą [kompletny przewodnik F # formatowania konwencje](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) przez [Phan Anh obornik](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Ogólne zasady wcięcie

F # domyślnie używa znaczącym odstępem. Poniższe wskazówki są przeznaczone do zawierają wskazówki dotyczące sposobu łatwiejszą obsługę niektóre wyzwania, które to skonfigurować.

### <a name="using-spaces"></a>Przy użyciu spacji

Gdy wymagana jest wcięcie, należy użyć spacje, tabulatory nie. Wymagana jest co najmniej jedną przestrzeń. Organizacja może utworzyć standardów kodowania, aby określić liczbę spacji dla wcięć; Typowy jest dwóch, trzech lub czterech spacji wcięcia na każdym poziomie, gdzie występuje wcięcia.

**Zalecamy 4 spacje na wcięcia.**

Inaczej mówiąc, wcięcia programów polega na subiektywne. Zmiany są dozwolone, ale jest pierwszą regułę, należy wykonać *spójności wcięcia*. Wybierz styl ogólnie akceptowanych wcięcia i korzystać z niego systematycznie w całym baza kodu.

## <a name="formatting-discriminated-union-declarations"></a>Formatowanie Suma rozłączna — deklaracje złożeń

Wcięcie `|` w definicji typu przy użyciu spacji 4:

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

Skonkretyzowanym Suma rozłączna Unii, które podzielić na wiele wierszy powinny zawierać danych zawartych w niej nowego zakresu z wcięcia:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Zamykający nawias okrągły można też w nowym wierszu:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a>Formatowanie krotek

Wystąpienia spójnej kolekcji powinna być umieszczona w nawiasach i rozdzielające przecinków wewnątrz powinno następować jednego miejsca, na przykład: `(1, 2)`, `(x, y, z)`.

Powszechnie zaakceptowany wyjątku jest, aby pominąć nawiasów w krotek dopasowywania do wzorca:

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a>Formatowanie rekordów

Może być zapisany krótkich rekordów w jednym wierszu:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Rekordy, które są dłuższe należy używać nowych wierszy dla etykiet:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Wprowadzenie do tokenu otwierania tej samej linii i token zamknięcia w nowym wierszu jest również przeprowadzać:

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

## <a name="formatting-lists-and-arrays"></a>Formatowanie list i tablic

Zapis `x :: l` odstępów wokół `::` — operator (`::` jest operator infiksu, dlatego otoczony spacjami) i `[1; 2; 3]` (`;` jest ogranicznik, dlatego następuje spacja).

Zawsze należy używać co najmniej jeden odstęp między dwa różne operatory przypominającej nawiasu klamrowego. Na przykład, pozostaw odstęp między `[` i `{`.

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

List i tablic, które podzielić na wiele wierszy wykonaj podobne reguły, tak jak rekordy:

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

## <a name="formatting-if-expressions"></a>W przypadku formatowania wyrażenia

Wcięcie warunków zależy od rozmiarów wyrażeń, które tworzą je. Jeśli `cond`, `e1` i `e2` są niewielkie, po prostu zapisanie ich w jednym wierszu:

```fsharp
if cond then e1 else e2
```

Jeśli `e1` i `cond` są niewielkie, ale `e2` jest duża:

```fsharp
if cond then e1
else
    e2
```

Jeśli `e1` i `cond` większych i `e2` jest mały:

```fsharp
if cond then
    e1
else e2
```

Jeśli wszystkie wyrażenia są duże:

```fsharp
if cond then
    e1
else
    e2
```

Wiele warunków z `elif` i `else` tworzone jest wcięcie na tym samym zakresie co `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Konstrukcje dopasowania wzorca

Użyj `|` dla każdej klauzuli dopasowania z braku wcięcia. Jeśli wyrażenie jest krótki, można użyć jednego wiersza.

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

// OK
match l with [] -> false | _ :: _ -> true
```

Jeśli wyrażenie po prawej stronie strzałkę dopasowania wzorca jest zbyt duży, przenieś go do następującego wiersza, z wcięciami krok z `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Wzorzec dopasowywania funkcje anonimowe uruchamianie przy `function`, zazwyczaj należy zbyt daleko nie wcięcia. Na przykład następujący wcięcia jeden zakres jest poprawnie:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Wzorzec dopasowany w funkcjach zdefiniowanych przez `let` lub `let rec` powinien być wcięta 4 miejsca po uruchomieniu programu `let`, nawet jeśli `function` służy słowo kluczowe:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nie zaleca się wyrównywanie strzałki.

## <a name="formatting-trywith-expressions"></a>Formatowanie try / with wyrażenia

Dopasowania wzorca w typ wyjątku powinien być wcięty na tym samym poziomie jako `with`.

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

## <a name="formatting-function-parameter-application"></a>Formatowanie aplikacji parametru funkcji

Ogólnie rzecz biorąc większość aplikacji parametru funkcji odbywa się w tym samym wierszu.

Jeśli chcesz zastosować parametry do funkcji w nowym wierszu, wcięcie je przez jeden zakres.

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

Argumenty funkcji anonimowej mogą być w następnym wierszu lub z zawieszonego `fun` wierszu argumentu:

```fsharp
// OK
let printListWithOffset a list1 =
    List.iter (fun elem ->
        printfn "%d" (a + elem)) list1

// OK, but prefer previous
let printListWithOffset a list1 =
    List.iter (
        fun elem ->
            printfn "%d" (a + elem)) list1
```

### <a name="formatting-infix-operators"></a>Operatory infiksu formatowania

Oddzielne operatory przy użyciu spacji. Są oczywiste wyjątki od tej reguły `!` i `.` operatorów.

Wyrażenia infiksu mają zestawienia w tej samej kolumnie OK:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formatowanie operatorów potoku

Potok `|>` powinien pojawiać się na początku wiersza bezpośrednio pod wyrażenie, które są obsługiwane na:

```fsharp
// OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
               |> List.ofArray
               |> List.map (fun assm -> assm.GetTypes())
               |> Array.concat
               |> List.ofArray
               |> List.map (fun t -> t.GetMethods())
               |> Array.concat

// OK, but prefer previous
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

### <a name="formatting-object-expressions-and-interfaces"></a>Formatowanie obiektu wyrażeń i interfejsów

Wyrażenia obiektów i interfejsy powinno być wyrównane tak samo jak z `member` tworzone jest wcięcie po 4 spacji.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a>Formatowanie odstępu w wyrażeniach

Unikaj nadmiarowe odstępu w wyrażeniach języka F #.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Argumenty nazwane również nie powinna mieć miejsca otaczającego `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-blank-lines"></a>Formatowanie puste wiersze

* Oddzielne najwyższego poziomu funkcji i klasy definicji dwa puste wiersze.
* Definicje metody w klasie są rozdzielone przez pojedynczy pusty wiersz.
* Dodatkowe puste wiersze może służyć (oszczędnie) do oddzielania grup powiązanych funkcji. Puste wiersze można pominąć między licznych one-liners powiązane (na przykład zestawu zastępczego implementacji).
* Użyj oszczędnie, pustych wierszy w funkcjach, aby wskazać logiczne sekcje.

## <a name="formatting-comments"></a>Formatowanie komentarzy

Ogólnie rzecz biorąc Preferuj wielu komentarzy o podwójnej precyzji ukośnika przed komentarze bloku stylu uczenia Maszynowego.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    Generally avoid these kinds of comments.
*)
```

Komentarzy wewnętrznych powinien wielką literą.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Konwencje nazewnictwa

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Użyj wartości powiązane z klasy, powiązane z wyrażenia i powiązane z wzorca i funkcji (camelcase)

Często i zaakceptowane styl F # (camelcase) na potrzeby wszystkich nazw powiązana jako zmienne lokalne lub w dopasowaniach wzorców i definicje funkcji.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Funkcje wiązaniem lokalnie w klasach też używać (camelcase).

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Użyj wartości powiązane z modułu wewnętrzne i prywatne i funkcji (camelcase)

Użyj (camelcase) dla wartości powiązane z modułu prywatne, takie jak następujące:

* Funkcje ad hoc w skryptach

* Wartości tworzących wewnętrznej implementacji modułu lub typu

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="avoid-underscores-in-names"></a>Unikaj podkreślenia w nazwach

W przeszłości niektórych bibliotek języka F # użyto podkreślenia w nazwach. Jednak nie jest już powszechnie zaakceptowaniu częściowo, ponieważ jest ona konflikt z konwencji nazewnictwa platformy .NET. Inaczej mówiąc, niektóre programistów F # przy użyciu podkreślenia znacznie, częściowo przyczyn historycznych, a na uszkodzenia i zakresie jest ważne. Należy jednak pamiętać, że styl jest często disliked przez innych użytkowników, którzy mają wybór o tym, czy z niego korzystać.

Niektóre wyjątki obejmuje współpracy z natywnego składniki, których podkreślenia są bardziej powszechne.

### <a name="use-standard-f-operators"></a>Użyj standardowych operatorów F #

Następujące operatory są zdefiniowane w standardowej biblioteki języka F # i powinna być używana zamiast funkcji definiujący odpowiedniki. Za pomocą tych operatorów jest zalecane, ponieważ sprawia kodu bardziej czytelny i idiomatyczne. Może być przystosowane do różnych idioms deweloperom tła w OCaml lub innych funkcjonalny język programowania. Poniższa lista zawiera podsumowanie zalecane operatory F #.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Throwing away a value
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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Należy użyć składni prefiks dla typów ogólnych (`Foo<T>`) zamiast składni przyrostek (`T Foo`)

F # dziedziczy zarówno przyrostek ML styl nazewnictwa typów ogólnych (na przykład `int list`) oraz prefiks styl .NET (na przykład `list<int>`). Preferowane jest styl .NET, z wyjątkiem cztery określonych typów:

1. F # list, użyj przyrostkowej formy: `int list` zamiast `list<int>`.
2. F # opcji, należy użyć przyrostkowej formy: `int option` zamiast `option<int>`.
3. Dla języka F # tablic, użyj składni nazwy `int[]` zamiast `int array` lub `array<int>`.
4. Komórki odwołań, można użyć `int ref` zamiast `ref<int>` lub `Ref<int>`.

Dla wszystkich innych typów formularz prefiks.