---
title: Wyrażenia obliczeń
description: Dowiedz się, jak utworzyć wygodnej składni do pisania obliczeń w F# , można sekwencyjna i połączone przy użyciu kontrolowania konstrukcje przepływów i powiązania.
ms.date: 03/15/2019
ms.openlocfilehash: 3c2abb5c6204309fc8d5215a53ce8af46c01d218
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125515"
---
# <a name="computation-expressions"></a>Wyrażenia obliczeń

Wyrażenia obliczeń w F# zapewnienia wygodnej składni pisania obliczeń, które mogą być sekwencjonowania i łączyć, używając konstrukcji przepływów sterowania i powiązania. W zależności od rodzaju wyrażenia obliczeń one można traktować jako sposób express monads, monoids, transformatory monad i applicative funktory. Jednak w przeciwieństwie do innych języków (takie jak *zapisu czy* w Haskell), nie są powiązane z jednym pozyskiwania i nie należy polegać na makr lub innych form metaprogramowanie wykonywania wygodne i kontekstowym składni.

## <a name="overview"></a>Omówienie

Obliczenia może mieć wiele form. Najczęściej używany typ wyliczenia jest jednowątkowym wykonywania, który jest łatwy do zrozumienia i modyfikować. Jednak nie wszystkie rodzaje obliczeń są tak proste jak jednowątkowe wykonywania. Oto niektóre przykłady:

* Nie deterministyczne obliczeń
* Asynchroniczne obliczenia
* Effectful obliczeń
* Generatywną obliczeń

Ogólnie rzecz biorąc, istnieją *kontekstową* obliczenia, które należy wykonać w niektórych części aplikacji. Pisanie kodu kontekstową może stanowić wyzwanie, ponieważ jest łatwy do obliczenia "przeciek" poza podanym kontekście bez abstrakcji, aby zapobiec temu. Te elementy abstrakcji są często trudne do zapisu przez siebie, co jest dlaczego F# został uogólniony sposób przeprowadzenia tak zwane **wyrażenia obliczeń**.

Wyrażenia obliczeń oferuje jednolite składni i abstrakcji model dla kodowania kontekstową obliczeń.

Każde wyrażenie obliczeń opiera się na *konstruktora* typu. Typ Konstruktor określa operacje, które są dostępne dla wyrażenia obliczeń. Zobacz [tworzenia nowego typu z wyrażenia obliczeń](computation-expressions.md#creating-a-new-type-of-computation-expression), który przedstawia sposób tworzenia wyrażenia obliczeń niestandardowych.

### <a name="syntax-overview"></a>Omówienie składni

Wszystkie wyrażenia obliczeń mają następującą postać:

```
builder-expr { cexper }
```

gdzie `builder-expr` jest nazwą typu konstruktora, który definiuje wyrażenie obliczeń i `cexper` treści wyrażenia wyrażenia obliczeń. Na przykład `async` obliczenie wyrażenia kodu może wyglądać następująco:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Brak dostępnej specjalnych i dodatkowe składni w wyrażeniu obliczeń, jak pokazano w poprzednim przykładzie. Możliwe za pomocą wyrażenia obliczeń są następujące formy wyrażeń:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Każda z tych słów kluczowych i innymi standard F# słowa kluczowe są dostępne tylko w wyrażeniu obliczeń, jeśli zostały zdefiniowane w zapasowy typ konstruktora. Jedynym wyjątkiem jest `match!`, która sama jest sugar składni do użycia z `let!` następuje dopasowania do wzorca w wyniku.

Typ konstruktora jest obiektem, który definiuje specjalne metody, które określają sposób, w jaki fragmenty wyrażenia obliczeń są łączone; oznacza to, że jego metod kontroli zachowania wyrażenia obliczeń. Inny sposób w celu opisania klasy, Konstruktor jest powiedzieć, umożliwia dostosowywanie operacji wielu F# konstrukcje, takie jak pętle i powiązania.

### `let!`

`let!` — Słowo kluczowe wiąże nazwę wyniku wywołania do innego wyrażenia obliczeń:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Jeśli powiązać wywołanie wyrażenia obliczeń, za pomocą `let`, nie będzie można uzyskać wynik wyrażenia obliczeń. Zamiast tego możesz będzie mieć powiązana wartość *niezrealizowane* wywołanie tego wyrażenia obliczeń. Użyj `let!` powiązać z wynikiem.

`let!` jest definicją `Bind(x, f)` składowej typu konstruktora.

### `do!`

`do!` — Słowo kluczowe jest wywołanie wyrażenia obliczeń, który zwraca `unit`— takich jak typ (zdefiniowany przez `Zero` elementu członkowskiego w konstruktorze):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Aby uzyskać [asynchronicznego przepływu pracy](asynchronous-workflows.md), ten typ jest `Async<unit>`. Dla innych wyrażeń obliczeń mogą być jest typ `CExpType<unit>`.

`do!` jest definiowany przez `Bind(x, f)` składowej typu konstruktora, gdzie `f` tworzy `unit`.

### `yield`

`yield` — Słowo kluczowe jest zwracanie wartości z wyrażenia obliczeń, dzięki czemu mogą być używane jako <xref:System.Collections.Generic.IEnumerable%601>:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Podobnie jak w przypadku [yield — słowo kluczowe w języku C#](../../csharp/language-reference/keywords/yield.md), każdy element w wyrażeniu obliczeń jest uzyskane nagrania, ponieważ jest ona postanowiliśmy.

`yield` jest definiowany przez `Yield(x)` składowej typu konstruktora, gdzie `x` element umożliwiające uzyskanie ponownie.

### `yield!`

`yield!` — Słowo kluczowe jest spłaszczanie kolekcję wartości w wyrażeniu obliczeń:

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

Podczas oceny, wyrażenia obliczeń wywoływane przez `yield!` będzie mieć elementy zwróciło wstecz jeden po drugim, spłaszczanie wynik.

`yield!` jest definiowany przez `YieldFrom(x)` składowej typu konstruktora, gdzie `x` to zbiór wartości.

### `return`

`return` — Słowo kluczowe otacza wartość w polu Typ odpowiadający wyrażenia obliczeń. Oprócz wyrażenia obliczeń przy użyciu `yield`, jest używany do "complete" wyrażenia obliczeń:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` jest definiowany przez `Return(x)` składowej typu konstruktora, gdzie `x` element do opakowania.

### `return!`

`return!` — Słowo kluczowe zawiera wartość wyrażenia obliczeń i otacza wynik w typie odpowiadający wyrażenia obliczeń:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` jest definiowany przez `ReturnFrom(x)` składowej typu konstruktora, gdzie `x` jest innym wyrażeniem obliczeń.

### `match!`

Począwszy od F# 4.5, `match!` — słowo kluczowe pozwala na tekście wywołania do innego obliczenie wyrażenia i wzorzec dopasowania na jego wynik:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Podczas wywoływania wyrażeniu obliczeń z `match!`, będzie weź pod uwagę wynik wywołania, takie jak `let!`. Jest to często używane podczas wywoływania wyrażenia obliczeń, której wynikiem jest [opcjonalne](options.md).

## <a name="built-in-computation-expressions"></a>Wyrażenia obliczeń wbudowane

F# Podstawowej biblioteki definiuje trzy wyrażenia obliczeń wbudowane: [Wyrażenia sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażeniach zapytań](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Tworzenie nowego typu wyrażenia obliczeń

Można zdefiniować właściwości wyrażenia obliczeń, tworząc klasę konstruktora i definiowanie pewne specjalne metody w klasie. Klasa konstruktora Opcjonalnie można zdefiniować metody, zgodnie z opisem w poniższej tabeli.

W poniższej tabeli opisano metody, których można użyć w klasie konstruktora przepływu pracy.

|**— Metoda**|**Typowe podpisy**|**Opis**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Wywoływana dla `let!` i `do!` w wyrażenia obliczeń.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Opakowuje wyrażeniu obliczeń w funkcji.|
|`Return`|`'T -> M<'T>`|Wywoływana dla `return` w wyrażenia obliczeń.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Wywoływana dla `return!` w wyrażenia obliczeń.|
|`Run`|`M<'T> -> M<'T>` lub<br /><br />`M<'T> -> 'T`|Wykonuje wyrażenia obliczeń.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` lub<br /><br />`M<unit> * M<'T> -> M<'T>`|Wywoływana dla sekwencjonowania w wyrażenia obliczeń.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` lub<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Wywoływana dla `for...do` wyrażeń w wyrażenia obliczeń.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Wywoływana dla `try...finally` wyrażeń w wyrażenia obliczeń.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Wywoływana dla `try...with` wyrażeń w wyrażenia obliczeń.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Wywoływana dla `use` powiązania w wyrażenia obliczeń.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Wywoływana dla `while...do` wyrażeń w wyrażenia obliczeń.|
|`Yield`|`'T -> M<'T>`|Wywoływana dla `yield` wyrażeń w wyrażenia obliczeń.|
|`YieldFrom`|`M<'T> -> M<'T>`|Wywoływana dla `yield!` wyrażeń w wyrażenia obliczeń.|
|`Zero`|`unit -> M<'T>`|Wywoływana dla pusta `else` gałęzi z `if...then` wyrażeń w wyrażenia obliczeń.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Wskazuje, że wyrażenia obliczeń jest przekazywany do `Run` elementem członkowskim jak oferty. Tłumaczy je wszystkie wystąpienia elementu obliczeń w cudzysłowie.|

Wiele metod w klasie konstruktora użycia i zwracają `M<'T>` konstrukcji, która jest zwykle oddzielnie zdefiniowanego typu, który charakteryzuje rodzaju obliczeń połączone, przykładowo, `Async<'T>` asynchronicznych przepływów pracy i `Seq<'T>` w przypadku przepływów pracy sekwencji. Podpisy metody te je włączyć połączone i zagnieżdżone ze sobą, tak, aby obiekt przepływu pracy, zwracany z jedną konstrukcję może być przekazywany do następnej. Po przeanalizowaniu wyrażenia obliczeń, kompilator konwertuje wyrażenie w serii zagnieżdżonych wywołań funkcji przy użyciu metod przedstawionych w powyższej tabeli i kodu w wyrażeniu obliczeń.

Zagnieżdżone wyrażenie ma następującą postać:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

W kodzie powyżej wywołania `Run` i `Delay` są pomijane, jeśli nie są zdefiniowane w klasie Konstruktor wyrażeń obliczeń. Treść wyrażenia obliczeń, w tym miejscu są oznaczone jako `{| cexpr |}`, przetłumaczyć obejmujące metod klasy konstruktora połączeń przez tłumaczenia opisane w poniższej tabeli. Wyrażenia obliczeń `{| cexpr |}` jest zdefiniowanego cyklicznie zgodnie z ich gdzie `expr` jest F# wyrażenia i `cexpr` jest wyrażenia obliczeń.

|Wyrażenie|{1&gt;Translacja&lt;1}|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr, builder.Delay({&#124;cexpr &#124;}))</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|

W poprzedniej tabeli `other-expr` opisuje wyrażenie, które w przeciwnym razie nie został wymieniony w tabeli. Klasa konstruktora nie trzeba implementować wszystkie metody i obsługiwać wszystkich tłumaczeń wymienionych w powyższej tabeli. Te konstrukcje, które nie są implementowane nie są dostępne w wyrażenia obliczeń tego typu. Na przykład, jeśli nie chcesz obsługiwać `use` słowa kluczowego w Twojej wyrażenia obliczeń, można pominąć definicji `Use` w klasie konstruktora.

Poniższy przykład kodu pokazuje wyrażenie obliczeń hermetyzujący obliczeń serię kroków, które mogą być obliczane jeden krok w danym momencie. A Suma rozłączna typ union `OkOrException`, koduje stanu błędu wyrażenia obliczonego do tej pory. Ten przykład demonstruje kilka typowych wzorców, które można używać w swojej wyrażenia obliczeń, takich jak standardowy implementacje niektórych metod konstruktora.

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

Wyrażenia obliczeń ma typu podstawowego, który zwraca wartość wyrażenia. Typ podstawowy może reprezentować obliczony wynik lub opóźnione obliczenie, które mogą być wykonywane lub może ona dostarczać sposób do iteracji przez kolekcję określonego typu. W poprzednim przykładzie był typem podstawowym **ostatecznie**. To wyrażenie sekwencji jest typem podstawowym <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Wyrażenie zapytania, typ podstawowy jest <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Dla asynchronicznego przepływu pracy jest typem podstawowym [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). `Async` Obiekt reprezentuje pracy do wykonania do obliczania wyniku. Na przykład wywołać [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) do wykonywania obliczeń i zwracają wynik.

## <a name="custom-operations"></a>Operacje niestandardowe

Można zdefiniować niestandardowe operacja na wyrażeniu obliczeń i użyć niestandardowych operacji jako operator w wyrażeniu obliczeń. Na przykład może zawierać operatora zapytania "w" w wyrażeniu zapytania. Podczas definiowania operacji niestandardowej, należy zdefiniować wydajność i metod w wyrażeniu obliczeń. Aby zdefiniować niestandardowe działanie, umieść go w klasę konstruktora dla wyrażenia obliczeń, a następnie Zastosuj [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Ten atrybut przyjmuje ciąg jako argument, jest to nazwa, która ma być używany w niestandardowych operacji. Ta nazwa jest dostarczany do zakresu na początku otwierającym nawiasie klamrowym wyrażenia obliczeń. Dlatego nie należy używać identyfikatorów, które mają taką samą nazwę jak niestandardowe działania w tym bloku. Na przykład należy unikać stosowanie identyfikatorów, takich jak `all` lub `last` w wyrażeniach zapytań.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Rozszerzanie istniejących producenci nowe operacje niestandardowe

Jeśli masz już klasa konstruktora, jego operacje niestandardowe można rozszerzyć z poza tym konstruktora klasy. Rozszerzenia musi być zadeklarowany w modułach. Przestrzenie nazw nie może zawierać elementy członkowskie rozszerzeń z wyjątkiem w tym samym pliku i tej samej grupie deklaracji przestrzeni nazw, gdy typ jest zdefiniowany.

Poniższy przykład pokazuje rozszerzenie istniejącej `Microsoft.FSharp.Linq.QueryBuilder` klasy.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Asynchroniczne przepływy pracy](asynchronous-workflows.md)
- [Sekwencje](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Wyrażenia zapytania](query-expressions.md)
