---
title: Co to jest F#
description: Dowiedz się więcej F# na temat tego, co F# to jest język programowania i jaki jest sposób programowania. Dowiedz się więcej o zaawansowanych typach danych, funkcjach i sposobach ich dopasowania.
ms.date: 08/03/2018
ms.openlocfilehash: 0c576fe49fadebd68e4fc9d2b20ea8f0cb991af5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630461"
---
# <a name="what-is-f"></a>Co to jest F\#

F#to funkcjonalny język programowania, dzięki któremu można łatwo pisać kod poprawny i łatwiejszy w obsłudze.

F#Programowanie przede wszystkim obejmuje Definiowanie typów i funkcji, które są automatycznie wywnioskowane i uogólnione. Pozwala to skupić się na domenie problemu i manipulowaniu swoimi danymi, a nie szczegółami programowania.

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn "%s" greeting)

    0
```

F#ma wiele funkcji, w tym:

* Składnia uproszczona
* Domyślnie niezmienne
* Wnioskowanie o typie i automatyczne uogólnianie
* Funkcje pierwszoklasowe
* Zaawansowane typy danych
* Dopasowanie do wzorca
* Programowanie asynchroniczne

Pełny zestaw funkcji jest udokumentowany w [ F# dokumentacji języka](./language-reference/index.md).

## <a name="rich-data-types"></a>Zaawansowane typy danych

Typy danych, takie jak [rekordy](./language-reference/records.md) i [związki rozłącznych](./language-reference/discriminated-unions.md) , umożliwiają przedstawianie złożonych danych i domen.

```fsharp
// Group data with Records
type SuccessfulWithdrawal = {
    Amount: decimal
    Balance: decimal
}

type FailedWithdrawal = {
    Amount: decimal
    Balance: decimal
    IsOverdraft: bool
}

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

F#rekordy i unie rozłączne mają domyślnie wartości inne niż null, niezmienne i porównywalne, co ułatwia ich używanie.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>Wymuszone poprawność przy użyciu funkcji i dopasowania do wzorca

F#funkcje są łatwe do zadeklarować i zaawansowania. W połączeniu z [dopasowywaniem do wzorca](./language-reference/pattern-matching.md)pozwala na definiowanie zachowania, którego poprawność jest wymuszana przez kompilator.

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f" s.Amount
    | InsufficientFunds f -> printfn "Failed: balance is %f" f.Balance
    | CardExpired d -> printfn "Failed: card expired on %O" d
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

F#funkcje są również pierwszą klasą, co oznacza, że mogą być przesyłane jako parametry i zwracane z innych funkcji.

## <a name="functions-to-define-operations-on-objects"></a>Funkcje do definiowania operacji na obiektach

F#ma pełną obsługę obiektów, które są przydatnymi typami danych w przypadku konieczności mieszania danych i funkcjonalności. F#funkcje są używane do manipulowania obiektami.

```fsharp
type Set<[<EqualityConditionOn>] 'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

[<RequireQualifiedAccess>]
module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

Zamiast pisać kod, który jest zorientowany obiektowo, w programie F#często piszesz kod, który traktuje obiekty jako inny typ danych dla funkcji do manipulowania. Funkcje takie jak [interfejsy ogólne](./language-reference/interfaces.md), [wyrażenia obiektów](./language-reference/object-expressions.md)i rozsądne użycie [elementów członkowskich](./language-reference/members/index.md) są wspólne w większych F# programach.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat większego F# zestawu funkcji, zapoznaj się z [ F# przewodnikiem](tour.md).
