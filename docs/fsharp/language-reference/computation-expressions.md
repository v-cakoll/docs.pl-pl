---
title: Wyrażenia obliczeń
description: Dowiedz się, jak utworzyć wygodną składnię do pisania obliczeń w języku F#, które mogą być sekwencjonowane i łączone przy użyciu konstrukcji przepływu sterowania i powiązań.
ms.date: 11/04/2019
ms.openlocfilehash: 55406cc12d9e6e890fe69d712f79486d23b84452
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400233"
---
# <a name="computation-expressions"></a>Wyrażenia obliczeń

Wyrażenia obliczeniowe w języku F# zapewniają wygodną składnię do pisania obliczeń, które mogą być sekwencjonowane i łączone przy użyciu konstrukcji przepływu sterowania i powiązań. W zależności od rodzaju wyrażenia obliczeniowego, można je traktować jako sposób wyrażania monads, monoidów, transformatorów monad i aplikatorów funktorów. Jednak w przeciwieństwie do innych języków (takich jak *do-notacji* w Haskell), nie są one związane z jednej abstrakcji i nie polegać na makrach lub innych form metaprogramowania, aby osiągnąć wygodne i kontekstowej składni.

## <a name="overview"></a>Omówienie

Obliczenia mogą przybrać wiele form. Najbardziej rozpowszechnioną formą obliczeń jest wykonanie jednowątkowe, które jest łatwe do zrozumienia i modyfikacji. Jednak nie wszystkie formy obliczeń są tak proste, jak wykonanie jednowątkowe. Oto niektóre przykłady:

- Obliczenia niedeterministyczne
- Obliczenia asynchroniczne
- Obliczenia o efektywnym działaniu
- Obliczenia generatywne

Ogólnie rzecz biorąc istnieją obliczenia *kontekstowe,* które należy wykonać w niektórych częściach aplikacji. Pisanie kodu kontekstowego może być trudne, ponieważ łatwo jest "przeciekać" obliczeń poza danym kontekście bez abstrakcji, aby uniemożliwić to zrobić. Te abstrakcje są często trudne do napisania samodzielnie, dlatego F# ma uogólniony sposób, aby to zrobić nazywane **wyrażenia obliczeniowe**.

Wyrażenia obliczeniowe oferują jednolity model składni i abstrakcji do kodowania obliczeń kontekstowych.

Każde wyrażenie obliczeniowe jest poparte typem *konstruktora.* Typ konstruktora definiuje operacje, które są dostępne dla wyrażenia obliczeniowego. Zobacz [Tworzenie nowego typu wyrażenia obliczeniowego](computation-expressions.md#creating-a-new-type-of-computation-expression), który pokazuje, jak utworzyć niestandardowe wyrażenie obliczeniowe.

### <a name="syntax-overview"></a>Omówienie składni

Wszystkie wyrażenia obliczeniowe mają następującą formę:

```fsharp
builder-expr { cexper }
```

gdzie `builder-expr` jest nazwa typu konstruktora, który definiuje `cexper` wyrażenie obliczeniowe i jest treścią wyrażenia wyrażenia obliczeniowego. Na przykład `async` kod wyrażenia obliczeń może wyglądać tak:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Istnieje specjalna, dodatkowa składnia dostępna w wyrażeniu obliczeniowym, jak pokazano w poprzednim przykładzie. Następujące formularze wyrażeń są możliwe z wyrażeniami obliczeniowymi:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Każde z tych słów kluczowych i inne standardowe słowa kluczowe F# są dostępne tylko w wyrażeniu obliczeniowym, jeśli zostały zdefiniowane w typie konstruktora kopii zapasowych. Jedynym wyjątkiem jest `match!`, który sam jest cukrem `let!` składniowym do wykorzystania, po którym następuje dopasowanie wzorca na wynik.

Typ konstruktora jest obiektem, który definiuje specjalne metody, które regulują sposób, w jaki fragmenty wyrażenia obliczeniowego są łączone; oznacza to, że jego metody kontrolują, jak zachowuje się wyrażenie obliczeniowe. Innym sposobem opisywania klasy konstruktora jest powiedzieć, że umożliwia dostosowanie operacji wielu konstrukcji F#, takich jak pętle i powiązania.

### `let!`

Słowo `let!` kluczowe wiąże wynik wywołania z innym wyrażeniem obliczeniowym z nazwą:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Jeśli powiążesz wywołanie z `let`wyrażeniem obliczeniowym z , nie otrzymasz wyniku wyrażenia obliczeniowego. Zamiast tego będziesz mieć powiązane wartość *niezrealizowane* wywołanie do tego wyrażenia obliczeniowego. Służy `let!` do wiązania się z wynikiem.

`let!`jest zdefiniowana `Bind(x, f)` przez element członkowski na typie konstruktora.

### `do!`

Słowo `do!` kluczowe służy do wywoływania wyrażenia `unit`obliczeniowego, które zwraca `Zero` typ podobny (zdefiniowany przez element członkowski w konstruktorze):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Dla [przepływu pracy asynchronicznego](asynchronous-workflows.md)ten typ jest `Async<unit>`. W przypadku innych wyrażeń obliczeniowych `CExpType<unit>`typ może być .

`do!`jest zdefiniowana `Bind(x, f)` przez element członkowski na typie konstruktora, gdzie `f` tworzy . `unit`

### `yield`

Słowo `yield` kluczowe służy do zwracania wartości z wyrażenia obliczeniowego, dzięki <xref:System.Collections.Generic.IEnumerable%601>czemu może być zużywana jako :

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

W większości przypadków może zostać pominięty przez obiekty wywołujące. Najczęstszym sposobem pominięcia `yield` jest `->` z operatorem:

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

W przypadku bardziej złożonych wyrażeń, które mogą dawać wiele różnych wartości i być może warunkowo, po prostu pominięcie słowa kluczowego może wykonać:

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

Podobnie jak w przypadku [yield słowa kluczowego w języku C#](../../csharp/language-reference/keywords/yield.md), każdy element w wyrażeniu obliczeń jest zwolniony z powrotem, ponieważ jest iterowany.

`yield`jest zdefiniowany `Yield(x)` przez element członkowski na typ konstruktora, gdzie `x` jest element emanować z powrotem.

### `yield!`

Słowo `yield!` kluczowe służy do spłaszczania kolekcji wartości z wyrażenia obliczeniowego:

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

Po doliczeniu wyrażenie obliczeniowe `yield!` wywoływane przez będzie miał jego elementy uzyskane z powrotem jeden po drugim, spłaszczając wynik.

`yield!`jest zdefiniowany `YieldFrom(x)` przez element członkowski na typ konstruktora, gdzie `x` jest kolekcją wartości.

W `yield` `yield!` przeciwieństwie do , musi być jawnie określony. Jego zachowanie nie jest niejawne w wyrażeniach obliczeniowych.

### `return`

Słowo `return` kluczowe zawija wartość w typie odpowiadającym wyrażeniu obliczeniowemu. Oprócz wyrażeń obliczeniowych przy użyciu `yield`, jest on używany do "ukończenia" wyrażenia obliczeniowego:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`jest zdefiniowany `Return(x)` przez element członkowski na typ konstruktora, gdzie `x` jest element do zawijania.

### `return!`

Słowo `return!` kluczowe realizuje wartość wyrażenia obliczeniowego i zawija, które powodują typ odpowiadający wyrażeniu obliczeniowemu:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`jest zdefiniowany `ReturnFrom(x)` przez element członkowski typu konstruktora, gdzie `x` jest inne wyrażenie obliczeniowe.

### `match!`

Słowo `match!` kluczowe umożliwia połączenie z innym wyrażeniem obliczeniowym i dopasowanie wzorca na jego wynik:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Podczas wywoływania wyrażenia obliczeniowego z `match!`, będzie realizować `let!`wynik wywołania, takich jak . Jest to często używane podczas wywoływania wyrażenia obliczeniowego, gdzie wynik jest [opcjonalny](options.md).

## <a name="built-in-computation-expressions"></a>Wbudowane wyrażenia obliczeniowe

Biblioteka rdzenia F# definiuje trzy wbudowane wyrażenia obliczeniowe: [wyrażenia sekwencji,](sequences.md) [asynchroniczne przepływy pracy](asynchronous-workflows.md)i [wyrażenia zapytań](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Tworzenie nowego typu wyrażenia obliczeniowego

Można zdefiniować właściwości własnych wyrażeń obliczeniowych, tworząc klasę konstruktora i definiując pewne specjalne metody w klasie. Klasa konstruktora może opcjonalnie zdefiniować metody wymienione w poniższej tabeli.

W poniższej tabeli opisano metody, które mogą być używane w klasie konstruktora przepływu pracy.

|**Metoda**|**Typowe podpisy**|**Opis**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Wywoływana `let!` `do!` i w wyrażeniach obliczeniowych.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Zawija wyrażenie obliczeniowe jako funkcję.|
|`Return`|`'T -> M<'T>`|Wywoływane `return` w wyrażeniach obliczeniowych.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Wywoływane `return!` w wyrażeniach obliczeniowych.|
|`Run`|`M<'T> -> M<'T>` lub<br /><br />`M<'T> -> 'T`|Wykonuje wyrażenie obliczeniowe.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` lub<br /><br />`M<unit> * M<'T> -> M<'T>`|Wywoływana do sekwencjonowania w wyrażeniach obliczeniowych.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` lub<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Wywoływana `for...do` dla wyrażeń w wyrażeniach obliczeniowych.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Wywoływana `try...finally` dla wyrażeń w wyrażeniach obliczeniowych.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Wywoływana `try...with` dla wyrażeń w wyrażeniach obliczeniowych.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|Wywoływana `use` do powiązań w wyrażeniach obliczeniowych.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Wywoływana `while...do` dla wyrażeń w wyrażeniach obliczeniowych.|
|`Yield`|`'T -> M<'T>`|Wywoływana `yield` dla wyrażeń w wyrażeniach obliczeniowych.|
|`YieldFrom`|`M<'T> -> M<'T>`|Wywoływana `yield!` dla wyrażeń w wyrażeniach obliczeniowych.|
|`Zero`|`unit -> M<'T>`|Wywoływana `else` do `if...then` pustych gałęzi wyrażeń w wyrażeniach obliczeniowych.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Wskazuje, że wyrażenie obliczeniowe jest `Run` przekazywane do elementu członkowskiego jako oferta. Przekłada wszystkie wystąpienia obliczeń na cytat.|

Wiele metod w klasie konstruktora `M<'T>` używać i zwracać konstrukcję, która jest zazwyczaj oddzielnie zdefiniowane typu, który charakteryzuje `Async<'T>` rodzaj obliczeń są łączone, na przykład dla asynchronicznych przepływów pracy i `Seq<'T>` sekwencji przepływów pracy. Podpisy tych metod umożliwiają ich łączenie i zagnieżdżanie ze sobą, dzięki czemu obiekt przepływu pracy zwracany z jednej konstrukcji mogą być przekazywane do następnego. Kompilator, gdy analizuje wyrażenie obliczeniowe, konwertuje wyrażenie na serię zagnieżdżonych wywołań funkcji przy użyciu metod w poprzedniej tabeli i kodu w wyrażeniu obliczeniowym.

Wyrażenie zagnieżdżone ma następującą formę:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

W powyższym kodzie `Run` wywołania i `Delay` są pomijane, jeśli nie są zdefiniowane w klasie konstruktora wyrażeń obliczeń. Treść wyrażenia obliczeniowego, o tym, o `{| cexpr |}`których określono jako , jest tłumaczona na wywołania obejmujące metody klasy konstruktora przez tłumaczenia opisane w poniższej tabeli. Wyrażenie `{| cexpr |}` obliczeniowe jest definiowane rekursywnie zgodnie z tymi tłumaczeniami, gdzie `expr` jest wyrażeniem F# i `cexpr` jest wyrażeniem obliczeniowym.

|Wyrażenie|Tłumaczenie|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

W poprzedniej `other-expr` tabeli opisano wyrażenie, które w inny sposób nie jest wymienione w tabeli. Klasa konstruktora nie musi implementować wszystkich metod i obsługiwać wszystkie tłumaczenia wymienione w poprzedniej tabeli. Te konstrukcje, które nie są implementowane nie są dostępne w wyrażeniach obliczeniowych tego typu. Na przykład jeśli nie chcesz obsługiwać `use` słowa kluczowego w wyrażeniach obliczeniowych, można `Use` pominąć definicję w klasie konstruktora.

W poniższym przykładzie kodu przedstawiono wyrażenie obliczeniowe, które hermetyzuje obliczenia jako serię kroków, które można ocenić krok po kroku. Typ unii dyskryminowanej `OkOrException`, koduje stan błędu wyrażenia, jak oceniono do tej pory. Ten kod pokazuje kilka typowych wzorców, których można użyć w wyrażeniach obliczeniowych, takich jak standardowe implementacje niektórych metod konstruktorów.

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res ->
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally
            (whileLoop
                (fun () -> ie.MoveNext())
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step
```

Wyrażenie obliczeniowe ma typ źródłowy, który zwraca wyrażenie. Typ bazowy może reprezentować obliczony wynik lub opóźnione obliczenia, które mogą być wykonywane lub może stanowić sposób iterate za pośrednictwem pewnego typu kolekcji. W poprzednim przykładzie typem bazowym był **Eventually**. Dla wyrażenia sekwencji typem <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>źródłowym jest . W przypadku wyrażenia kwerendy typem źródłowym jest <xref:System.Linq.IQueryable?displayProperty=nameWithType>. W przypadku asynchronicznego przepływu pracy [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)źródłowym typem jest . Obiekt `Async` reprezentuje pracę do wykonania w celu obliczenia wyniku. Na przykład wywołać [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) wykonać obliczenia i zwrócić wynik.

## <a name="custom-operations"></a>Operacje niestandardowe

Operację niestandardową można zdefiniować dla wyrażenia obliczeniowego i użyć operacji niestandardowej jako operatora w wyrażeniu obliczeniowym. Na przykład można dołączyć operator kwerendy w wyrażeniu kwerendy. Podczas definiowania operacji niestandardowej należy zdefiniować yield i for metody w wyrażeniu obliczeń. Aby zdefiniować operację niestandardową, umieść ją w klasie konstruktora dla wyrażenia obliczeniowego, a następnie zastosuj plik [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Ten atrybut przyjmuje ciąg jako argument, który jest nazwą, która ma być używana w operacji niestandardowej. Ta nazwa wchodzi w zakres na początku otwierającego nawias klamrowy wyrażenia obliczeniowego. W związku z tym nie należy używać identyfikatorów, które mają taką samą nazwę jak niestandardowa operacja w tym bloku. Na przykład należy unikać używania identyfikatorów, takich jak `all` lub `last` w wyrażeniach kwerendy.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Rozszerzanie istniejących konstruktorów o nowe operacje niestandardowe

Jeśli masz już klasę konstruktora, jej niestandardowe operacje można rozszerzyć spoza tej klasy konstruktora. Rozszerzenia muszą być zadeklarowane w modułach. Obszary nazw nie mogą zawierać elementów członkowskich rozszerzeń, z wyjątkiem tego samego pliku i tej samej grupy deklaracji obszaru nazw, w której zdefiniowano typ.

W poniższym przykładzie przedstawiono `Microsoft.FSharp.Linq.QueryBuilder` rozszerzenie istniejącej klasy.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka F#](index.md)
- [Asynchroniczne przepływy pracy](asynchronous-workflows.md)
- [Sekwencje](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Wyrażenia zapytania](query-expressions.md)
