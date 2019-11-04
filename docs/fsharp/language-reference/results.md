---
title: Wyniki
description: Dowiedz się, F# jak za pomocą typu "result" napisać kod odporny na błędy.
ms.date: 04/24/2017
ms.openlocfilehash: 187aa26ccbaac7e0ec998756377bb7b0489eb1ab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424850"
---
# <a name="results"></a>Wyniki

Począwszy od F# 4,1, istnieje `Result<'T,'TFailure>` typ, którego można użyć do pisania kodu odpornego na błędy, który może składać się z.

## <a name="syntax"></a>Składnia

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>Uwagi

Należy zauważyć, że typ wyniku to [związek rozłącznych struktur](discriminated-unions.md#struct-discriminated-unions), który jest kolejną funkcją wprowadzoną w F# 4,1.  W tym miejscu są stosowane semantyka równości strukturalnej.

Typ `Result` jest zazwyczaj używany w obsłudze błędów monadic, co jest często określane jako [programowanie zorientowane na szyny](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) w F# społeczności.  Poniższy prosty przykład ilustruje to podejście.

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

Jak widać, bardzo łatwo można połączyć łańcuchowo różne funkcje walidacji, jeśli wymusimy, aby wszyscy mogli zwrócić `Result`.  Dzięki temu można rozbić funkcje podobne do małych kawałków, które są w miarę możliwości do redagowania.  Jest to również wartość dodana do *wymuszania* użycia [dopasowania wzorca](pattern-matching.md) na końcu zaokrąglenia sprawdzania poprawności, która w ten sposób wymusza wyższy stopień poprawienia programu.

## <a name="see-also"></a>Zobacz także

- [Sumy rozłączne](discriminated-unions.md)
- [Dopasowanie do wzorca](pattern-matching.md)
