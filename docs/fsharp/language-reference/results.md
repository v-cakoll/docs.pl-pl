---
title: 'Wyniki (F #)'
description: 'Dowiedz się, jak używać F # "Powoduje" typ ułatwia pisanie kodu błędu odpornej na uszkodzenia.'
ms.date: 04/24/2017
ms.openlocfilehash: 432e420ba7c2005caa46250dde82c2c67c9d3ae3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563011"
---
# <a name="results"></a><span data-ttu-id="42084-103">Wyniki</span><span class="sxs-lookup"><span data-stu-id="42084-103">Results</span></span>

<span data-ttu-id="42084-104">Począwszy od 4.1 F #, Brak `Result<'T,'TFailure>` typu, który służy do pisania kodu błędu odpornej na uszkodzenia, które mogą być składane.</span><span class="sxs-lookup"><span data-stu-id="42084-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="42084-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="42084-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="42084-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42084-106">Remarks</span></span>

<span data-ttu-id="42084-107">Należy zauważyć, że typ wyniku [struktury Suma rozłączna Unii](discriminated-unions.md#struct-discriminated-unions), która jest inna funkcja wprowadzona w F # 4.1.</span><span class="sxs-lookup"><span data-stu-id="42084-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="42084-108">Semantykę równości strukturalnej mają zastosowanie w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="42084-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="42084-109">`Result` Typu są zwykle stosowane w monadic obsługi błędów, które jest często określany jako [programowanie zorientowane na kolei](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) w ramach społeczności F #.</span><span class="sxs-lookup"><span data-stu-id="42084-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="42084-110">W poniższym przykładzie trivial pokazano tej metody.</span><span class="sxs-lookup"><span data-stu-id="42084-110">The following trivial example demonstrates this approach.</span></span>

```fsharp
// Define a simple type which has fields that can be validated
type Request = 
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult 
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() = 
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="42084-111">Jak widać, jest dość proste łańcuch różne funkcje sprawdzania poprawności, jeśli wymuszone na zwrócenie ich wszystkich `Result`.</span><span class="sxs-lookup"><span data-stu-id="42084-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="42084-112">Pozwala to podzielić funkcji takich jak to na małe części będące jako dopuszczająca składanie potrzebnych im.</span><span class="sxs-lookup"><span data-stu-id="42084-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="42084-113">Ma to również wartości dodanej *wymuszania* stosowania [dopasowanie wzorca](pattern-matching.md) na końcu round weryfikacji, który włącza wymusza wyższy stopień poprawności program.</span><span class="sxs-lookup"><span data-stu-id="42084-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="42084-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42084-114">See Also</span></span>

[<span data-ttu-id="42084-115">Sumy rozłączne</span><span class="sxs-lookup"><span data-stu-id="42084-115">Discriminated Unions</span></span>](discriminated-unions.md)

[<span data-ttu-id="42084-116">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="42084-116">Pattern Matching</span></span>](pattern-matching.md)
