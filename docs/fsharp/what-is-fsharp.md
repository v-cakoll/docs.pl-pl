---
title: 'Co to jest F #'
description: 'Dowiedz się więcej o jakie F # języka programowania i nowości programowanie F #. Więcej informacji na temat rozbudowane typy danych, funkcje i jak one współdziałają ze sobą.'
ms.date: 08/03/2018
ms.openlocfilehash: 193747f380c61a387ed79ecca6abbcd90ee74376
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43863299"
---
# <a name="what-is-f"></a>Co to jest F # #

F # to funkcjonalny język programowania, która ułatwia pisanie kodu poprawne i łatwego w utrzymaniu.

Programowanie w języku F # obejmuje głównie Definiowanie typy i funkcje, które wywnioskować typu i automatycznie uogólniony. Dzięki temu zespół nadal korzystać z domeny problemu i manipulowanie nimi swoje dane, a nie szczegóły programowania.

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

F # zawiera wiele funkcji, takich jak:

* Lightweight — Składnia
* Klasa Immutable domyślnie
* Wnioskowanie o typie i automatyczna Generalizacja
* Funkcje pierwszej klasy
* Typy danych zaawansowane
* Dopasowanie wzorca
* Programowanie asynchroniczne

Pełny zestaw funkcji są udokumentowane w artykule [dokumentacja języka F #](language-reference/index.md).

## <a name="rich-data-types"></a>Rozbudowane typy danych

Typy danych, takich jak [rekordów](language-reference/records.md) i [sumy rozłączne](language-reference/discriminated-unions.md) pozwalają reprezentują złożonych danych i domeny.

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

Rekordów F # i sumy rozłączne są inną niż null, niezmienne i porównywalnych domyślnie, dzięki czemu jest bardzo łatwa w użyciu.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>Wymuszone poprawność przy użyciu funkcji dopasowywania do wzorca

Funkcje F # są łatwe do deklarowania i Zaawansowane w praktyce. W połączeniu z [dopasowywania do wzorca](language-reference/pattern-matching.md), umożliwiają definiowanie zachowania, którego poprawność jest wymuszana przez kompilator.

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

Funkcje F # są także najwyższej jakości, co oznacza, mogą być przekazywane jako parametry i zwracane przez inne funkcje.

## <a name="functions-to-define-operations-on-objects"></a>Funkcje, aby zdefiniować operacje na obiektach

F # zawiera pełne wsparcie dla obiektów, które są typy danych przydatne, gdy potrzebujesz mieszania danych i funkcji. Funkcje F # są używane do manipulowania obiektami.

```fsharp
type Set<[<EqualityConditionOn>] ‘T when ‘T: comparison>(elements: seq<'T>) =
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

Zamiast pisania kodu, który jest zorientowana obiektowo, w języku F #, często napiszesz kod, traktuje obiekty jako inny typ danych dla funkcji do manipulowania. Funkcje, takie jak [interfejsów ogólnych](language-reference/interfaces.md), [wyrażenia obiektów](language-reference/object-expressions.md)oraz korzystać z [członków](language-reference/members/index.md) są powszechne w większych programów F #.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat większy zbiór funkcji F #, zapoznaj się z [Przewodnik po F #](tour.md).