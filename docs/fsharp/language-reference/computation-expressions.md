---
title: Wyrażenia obliczeń (F#)
description: 'Dowiedz się, jak utworzyć wygodny składnię pisanie obliczenia w F # można sekwencjonowania i łączyć, używając konstrukcji przepływu sterowania i powiązania.'
ms.date: 05/16/2016
ms.openlocfilehash: a4ddb3fde284452bc901c5270551611e43742c1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="computation-expressions"></a>Wyrażenia obliczeń

Wyrażenia obliczeń w języku F # zapewniają wygodną składni zapisywania obliczenia, które mogą być sekwencjonowania i łączyć, używając konstrukcji przepływu sterowania i powiązania. One może służyć do zapewnienia wygodny składnię *monady*, funkcjonalności funkcji programowania, który może służyć do zarządzania danych, sterowania i efekty uboczne w programach funkcjonalności.


## <a name="built-in-workflows"></a>Wbudowanych przepływów pracy
Wyrażenia sekwencji są przykładem wyrażenie do obliczenia są asynchroniczne przepływy pracy i wyrażenia zapytania. Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia zapytania](query-expressions.md).

Niektóre funkcje są wspólne dla wyrażenia sekwencji i asynchroniczne przepływy pracy i zilustrowania podstawowa składnia wyrażenia obliczenia:

```fsharp
builder-name { expression }
```

Poprzednie składni Określa, że podane wyrażenie jest wyrażenie do obliczenia typu określony przez *nazwa konstruktora*. Wyrażenia obliczeń może być wbudowane przepływu pracy, takich jak `seq` lub `async`, lub może być coś należy zdefiniować. *Nazwa konstruktora* jest identyfikator wystąpienia specjalny typ znany jako *typu konstruktora*. Typ konstruktora jest typu klasy, który definiuje specjalne metody rządzących sposób fragmentów wyrażenie obliczeń, są połączone, oznacza to, że kod tej kontrolki jak wykonuje wyrażenie. Innym sposobem opisano konstruktora klasy jest powiedzieć umożliwia dostosowywanie operacji konstrukcji wiele F #, takich jak pętle i powiązania.

W wyrażeniach obliczeń dwa formularze są dostępne dla niektórych typowych konstrukcji języka. Konstrukcje variant można wywołać za pomocą! (bang) sufiks na niektórych słów kluczowych, takich jak `let!`, `do!`i tak dalej. Formach specjalne spowodować, że pewne funkcje zdefiniowana w klasie konstruktora zastąpić zwykłe zachowanie wbudowane te operacje. Formularze przypominać `yield!` formę `yield` — słowo kluczowe, które jest używane w wyrażeniach sekwencji. Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md).


## <a name="creating-a-new-type-of-computation-expression"></a>Tworzenie nowego typu — wyrażenie obliczeń
Można zdefiniować właściwości wyrażenia obliczenia tworzenie konstruktora klasy, a niektóre specjalne metody w klasie. Konstruktor klasy można opcjonalnie zdefiniować metody wymienionych w poniższej tabeli.

W poniższej tabeli opisano metody, których można użyć w klasie konstruktora przepływu pracy.


|**— Metoda**|**Typowy podpisy**|**Opis**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Wywołuje się dla `let!` i `do!` w wyrażeniach obliczeń.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Opakowuje wyrażenie do obliczenia w funkcji.|
|`Return`|`'T -> M<'T>`|Wywołuje się dla `return` w wyrażeniach obliczeń.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Wywołuje się dla `return!` w wyrażeniach obliczeń.|
|`Run`|`M<'T> -> M<'T>` lub<br /><br />`M<'T> -> 'T`|Wykonuje wyrażenie do obliczenia.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` lub<br /><br />`M<unit> * M<'T> -> M<'T>`|Wywołuje się do sekwencjonowania w wyrażeniach obliczeń.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` lub<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Wywołuje się dla `for...do` wyrażenia w wyrażeniach obliczeń.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Wywołuje się dla `try...finally` wyrażenia w wyrażeniach obliczeń.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Wywołuje się dla `try...with` wyrażenia w wyrażeniach obliczeń.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Wywołuje się dla `use` powiązania w wyrażeniach obliczeń.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Wywołuje się dla `while...do` wyrażenia w wyrażeniach obliczeń.|
|`Yield`|`'T -> M<'T>`|Wywołuje się dla `yield` wyrażenia w wyrażeniach obliczeń.|
|`YieldFrom`|`M<'T> -> M<'T>`|Wywołuje się dla `yield!` wyrażenia w wyrażeniach obliczeń.|
|`Zero`|`unit -> M<'T>`|Wywoływana dla pustego `else` gałęzi elementu `if...then` wyrażenia w wyrażeniach obliczeń.|
Wiele metod w klasie konstruktora użycia i zwracać `M<'T>` konstrukcji, która jest zazwyczaj oddzielnie zdefiniowanego typu, która charakteryzuje typu obliczenia łączonych, na przykład, `Async<'T>` dla Asynchroniczne przepływy pracy i `Seq<'T>` dla przepływów pracy w sekwencji. Podpisy tych metod umożliwiały można łączyć i zagnieżdżone ze sobą, tak, aby przepływ pracy obiektu zwróconego z jednego konstrukcji mogą zostać przekazane do następnego. Kompilator po przeanalizowaniu wyrażenie do obliczenia konwertuje wyrażenie na serię zagnieżdżonych wywołań funkcji przy użyciu metod w powyższej tabeli i kodu w wyrażeniu obliczenia.

Zagnieżdżone wyrażenia ma następujący format:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

W kodzie powyżej wywołań `Run` i `Delay` są pomijane, jeśli nie są zdefiniowane w klasie Konstruktor wyrażeń obliczeń. Treść wyrażenia obliczeń, w tym miejscu jest oznaczona jako `{| cexpr |}`, przetłumaczyć wywołania metody konstruktora klasy obejmujące przez tłumaczeń opisane w poniższej tabeli. Wyrażenia obliczeń `{| cexpr |}` jest zdefiniowane cyklicznie zgodnie z tymi tłumaczeń gdzie `expr` wyrażenie F # i `cexpr` jest wyrażenie do obliczenia.



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
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
W poprzedniej tabeli `other-expr` opisuje wyrażenie, które w przeciwnym razie nie jest wyszczególniony w tabeli. Konstruktor klasy nie trzeba zaimplementować wszystkie metody i obsługują wszystkie tłumaczeń wymienione w powyższej tabeli. Tych konstrukcji, które nie są zaimplementowane nie są dostępne w wyrażeniach obliczeń tego typu. Na przykład, jeśli nie chcesz obsługiwać `use` — słowo kluczowe w Twojej wyrażenia obliczeń, można pominąć definicji `Use` w klasie konstruktora.

Poniższy przykład kodu pokazuje — wyrażenie obliczeń hermetyzujący obliczenia serie kroków, które mogą być obliczane krok naraz. Typ Unii Suma rozłączna — A `OkOrException`, koduje stanu błędu wyrażenia obliczonego w do tej pory. Ten kod przedstawiono kilka typowych wzorców, które można używać w sieci wyrażenia obliczeń, takich jak implementacje umożliwiającego niektóre metody konstruktora.

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
        | Done value -> NotYetDone (fun () -> func value)
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
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

Wyrażenie do obliczenia ma odpowiedni typ, który zwraca wartość wyrażenia. Typ źródłowy może reprezentować obliczona wynik lub opóźnione obliczeń, który może być wykonana lub może zapewnić sposób iterację pewien typ kolekcji. W poprzednim przykładzie, typ podstawowy został **ostatecznie**. Wyrażenia sekwencji jest typem podstawowym <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Wyrażenia zapytania jest typem podstawowym <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Asychronous przepływu pracy, jest typem podstawowym [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). `Async` Obiekt reprezentuje pracy do wykonania można obliczyć wyniku. Na przykład wywołać [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) wykonać obliczenia i zwraca wynik.

## <a name="custom-operations"></a>Operacje niestandardowe
Można zdefiniować niestandardowe operacja na wyrażeniu obliczenia i Użyj niestandardowej operacji jako operator w wyrażeniu obliczenia. Na przykład operator zapytania można uwzględnić w wyrażeniu zapytania. Podczas definiowania niestandardowych operacji, należy zdefiniować wydajność i metod w wyrażeniu obliczenia. Aby zdefiniować operacja niestandardowa, umieść ją w klasie konstruktora dla wyrażenia obliczeń, a następnie Zastosuj [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Ten atrybut ma ciąg jako argument, czyli nazwa do użycia w ramach operacji niestandardowych. Ta nazwa wchodzi w zakres na początku otwierający nawias klamrowy wyrażenia obliczenia. W związku z tym nie można używać identyfikatorów, które mają taką samą nazwę jak operacja niestandardowa w tym bloku. Na przykład, takich jak należy unikać użycia identyfikatorów `all` lub `last` w wyrażeniach zapytań.

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Asynchroniczne przepływy pracy](asynchronous-workflows.md)

[Sekwencje](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[Wyrażenia zapytania](query-expressions.md)
