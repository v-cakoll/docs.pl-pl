---
title: Co to jest F#
description: Dowiedz się więcej F# na temat tego, co F# to jest język programowania i jaki jest sposób programowania. Dowiedz się więcej o zaawansowanych typach danych, funkcjach i sposobach ich dopasowania.
ms.date: 08/03/2018
ms.openlocfilehash: 3cba509f59a8e81e1a0264de7451e9d80304d768
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332733"
---
# <a name="what-is-f"></a><span data-ttu-id="fa66e-104">Co to jest F\#</span><span class="sxs-lookup"><span data-stu-id="fa66e-104">What is F\#</span></span>

<span data-ttu-id="fa66e-105">F#to funkcjonalny język programowania, dzięki któremu można łatwo pisać kod poprawny i łatwiejszy w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="fa66e-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="fa66e-106">F#Programowanie przede wszystkim obejmuje Definiowanie typów i funkcji, które są automatycznie wywnioskowane i uogólnione.</span><span class="sxs-lookup"><span data-stu-id="fa66e-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="fa66e-107">Pozwala to skupić się na domenie problemu i manipulowaniu swoimi danymi, a nie szczegółami programowania.</span><span class="sxs-lookup"><span data-stu-id="fa66e-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="fa66e-108">F#ma wiele funkcji, w tym:</span><span class="sxs-lookup"><span data-stu-id="fa66e-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="fa66e-109">Składnia uproszczona</span><span class="sxs-lookup"><span data-stu-id="fa66e-109">Lightweight syntax</span></span>
* <span data-ttu-id="fa66e-110">Domyślnie niezmienne</span><span class="sxs-lookup"><span data-stu-id="fa66e-110">Immutable by default</span></span>
* <span data-ttu-id="fa66e-111">Wnioskowanie o typie i automatyczne uogólnianie</span><span class="sxs-lookup"><span data-stu-id="fa66e-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="fa66e-112">Funkcje pierwszoklasowe</span><span class="sxs-lookup"><span data-stu-id="fa66e-112">First-class functions</span></span>
* <span data-ttu-id="fa66e-113">Zaawansowane typy danych</span><span class="sxs-lookup"><span data-stu-id="fa66e-113">Powerful data types</span></span>
* <span data-ttu-id="fa66e-114">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="fa66e-114">Pattern matching</span></span>
* <span data-ttu-id="fa66e-115">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="fa66e-115">Async programming</span></span>

<span data-ttu-id="fa66e-116">Pełny zestaw funkcji jest udokumentowany w [ F# dokumentacji języka](./language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="fa66e-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="fa66e-117">Zaawansowane typy danych</span><span class="sxs-lookup"><span data-stu-id="fa66e-117">Rich data types</span></span>

<span data-ttu-id="fa66e-118">Typy danych, takie jak [rekordy](./language-reference/records.md) i [związki rozłącznych](./language-reference/discriminated-unions.md) , umożliwiają przedstawianie złożonych danych i domen.</span><span class="sxs-lookup"><span data-stu-id="fa66e-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="fa66e-119">F#rekordy i unie rozłączne mają domyślnie wartości inne niż null, niezmienne i porównywalne, co ułatwia ich używanie.</span><span class="sxs-lookup"><span data-stu-id="fa66e-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="fa66e-120">Wymuszone poprawność przy użyciu funkcji i dopasowania do wzorca</span><span class="sxs-lookup"><span data-stu-id="fa66e-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="fa66e-121">F#funkcje są łatwe do zadeklarować i zaawansowania.</span><span class="sxs-lookup"><span data-stu-id="fa66e-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="fa66e-122">W połączeniu z [dopasowywaniem do wzorca](./language-reference/pattern-matching.md)pozwala na definiowanie zachowania, którego poprawność jest wymuszana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="fa66e-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="fa66e-123">F#funkcje są również pierwszą klasą, co oznacza, że mogą być przesyłane jako parametry i zwracane z innych funkcji.</span><span class="sxs-lookup"><span data-stu-id="fa66e-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="fa66e-124">Funkcje do definiowania operacji na obiektach</span><span class="sxs-lookup"><span data-stu-id="fa66e-124">Functions to define operations on objects</span></span>

<span data-ttu-id="fa66e-125">F#ma pełną obsługę obiektów, które są przydatnymi typami danych w przypadku konieczności mieszania danych i funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="fa66e-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="fa66e-126">F#funkcje są używane do manipulowania obiektami.</span><span class="sxs-lookup"><span data-stu-id="fa66e-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

<span data-ttu-id="fa66e-127">Zamiast pisać kod, który jest zorientowany obiektowo, w programie F#często piszesz kod, który traktuje obiekty jako inny typ danych dla funkcji do manipulowania.</span><span class="sxs-lookup"><span data-stu-id="fa66e-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="fa66e-128">Funkcje takie jak [interfejsy ogólne](./language-reference/interfaces.md), [wyrażenia obiektów](./language-reference/object-expressions.md)i rozsądne użycie [elementów członkowskich](./language-reference/members/index.md) są wspólne w większych F# programach.</span><span class="sxs-lookup"><span data-stu-id="fa66e-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fa66e-129">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fa66e-129">Next steps</span></span>

<span data-ttu-id="fa66e-130">Aby dowiedzieć się więcej na temat większego F# zestawu funkcji, zapoznaj się z [ F# przewodnikiem](tour.md).</span><span class="sxs-lookup"><span data-stu-id="fa66e-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>
