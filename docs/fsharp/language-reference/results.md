---
title: 'Wyniki (F #)'
description: "Dowiedz się, jak używać F # \"Powoduje\" typ ułatwia pisanie kodu błędu odpornej na uszkodzenia."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a15b5cf1-9055-4481-918c-4c8a051b5829
ms.openlocfilehash: e6535b11464f5de0515c05e6678f6328f48a676a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="results"></a><span data-ttu-id="28688-104">Wyniki</span><span class="sxs-lookup"><span data-stu-id="28688-104">Results</span></span>

<span data-ttu-id="28688-105">Począwszy od 4.1 F #, Brak `Result<'T,'TFailure>` typu, który służy do pisania kodu błędu odpornej na uszkodzenia, które mogą być składane.</span><span class="sxs-lookup"><span data-stu-id="28688-105">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="28688-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="28688-106">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="28688-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28688-107">Remarks</span></span>

<span data-ttu-id="28688-108">Należy zauważyć, że typ wyniku [struktury Suma rozłączna Unii](discriminated-unions.md#struct-discriminated-unions), która jest inna funkcja wprowadzona w F # 4.1.</span><span class="sxs-lookup"><span data-stu-id="28688-108">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="28688-109">Semantykę równości strukturalnej mają zastosowanie w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="28688-109">Structural equality semantics apply here.</span></span>

<span data-ttu-id="28688-110">`Result` Typu są zwykle stosowane w monadic obsługi błędów, które jest często określany jako [programowanie zorientowane na kolei](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) w ramach społeczności F #.</span><span class="sxs-lookup"><span data-stu-id="28688-110">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="28688-111">W poniższym przykładzie trivial pokazano tej metody.</span><span class="sxs-lookup"><span data-stu-id="28688-111">The following trivial example demonstrates this approach.</span></span>

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

<span data-ttu-id="28688-112">Jak widać, jest dość proste łańcuch różne funkcje sprawdzania poprawności, jeśli wymuszone na zwrócenie ich wszystkich `Result`.</span><span class="sxs-lookup"><span data-stu-id="28688-112">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="28688-113">Pozwala to podzielić funkcji takich jak to na małe części będące jako dopuszczająca składanie potrzebnych im.</span><span class="sxs-lookup"><span data-stu-id="28688-113">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="28688-114">Ma to również wartości dodanej *wymuszania* stosowania [dopasowanie wzorca](pattern-matching.md) na końcu round weryfikacji, który włącza wymusza wyższy stopień poprawności program.</span><span class="sxs-lookup"><span data-stu-id="28688-114">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="28688-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28688-115">See Also</span></span>

[<span data-ttu-id="28688-116">Sumy rozłączne</span><span class="sxs-lookup"><span data-stu-id="28688-116">Discriminated Unions</span></span>](discriminated-unions.md)

[<span data-ttu-id="28688-117">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="28688-117">Pattern Matching</span></span>](pattern-matching.md)
