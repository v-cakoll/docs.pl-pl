---
title: 'Wyniki (F #)'
description: 'Dowiedz się, jak używać F # "Powoduje" typ ułatwia pisanie kodu błędu odpornej na uszkodzenia.'
ms.date: 04/24/2017
ms.openlocfilehash: 432e420ba7c2005caa46250dde82c2c67c9d3ae3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="results"></a>Wyniki

Począwszy od 4.1 F #, Brak `Result<'T,'TFailure>` typu, który służy do pisania kodu błędu odpornej na uszkodzenia, które mogą być składane.

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

Należy zauważyć, że typ wyniku [struktury Suma rozłączna Unii](discriminated-unions.md#struct-discriminated-unions), która jest inna funkcja wprowadzona w F # 4.1.  Semantykę równości strukturalnej mają zastosowanie w tym miejscu.

`Result` Typu są zwykle stosowane w monadic obsługi błędów, które jest często określany jako [programowanie zorientowane na kolei](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) w ramach społeczności F #.  W poniższym przykładzie trivial pokazano tej metody.

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

Jak widać, jest dość proste łańcuch różne funkcje sprawdzania poprawności, jeśli wymuszone na zwrócenie ich wszystkich `Result`.  Pozwala to podzielić funkcji takich jak to na małe części będące jako dopuszczająca składanie potrzebnych im.  Ma to również wartości dodanej *wymuszania* stosowania [dopasowanie wzorca](pattern-matching.md) na końcu round weryfikacji, który włącza wymusza wyższy stopień poprawności program.

## <a name="see-also"></a>Zobacz też

[Sumy rozłączne](discriminated-unions.md)

[Dopasowanie do wzorca](pattern-matching.md)
