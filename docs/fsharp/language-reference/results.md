---
title: Wyniki (F#)
description: Dowiedz się, jak pomóc w pisaniu kodu błędu odpornej na uszkodzenia za pomocą typów języka F# "Wynik".
ms.date: 04/24/2017
ms.openlocfilehash: a7ce2e1f6b8c6a32d99a2feaf9547c4b67b152b8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "44213043"
---
# <a name="results"></a>wyniki

Począwszy od F# 4.1, Brak `Result<'T,'TFailure>` typu, który służy do pisania kodu błędu odpornej na uszkodzenia, który może być składana.

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

Należy zauważyć, że typ wyniku [sumy Unii](discriminated-unions.md#struct-discriminated-unions), która jest inna funkcja wprowadzona w F# 4.1.  Semantyka porównania strukturalnego zgłosić się tutaj.

`Result` Typu jest zwykle używana w monadic obsługi błędów, która jest często nazywany [programowania zorientowanego na kolei](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) w ramach społeczności pasjonatów języka F#.  W poniższym przykładzie trivial pokazano tego podejścia.

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

Jak widać, jest całkiem łatwo można połączyć w łańcuch ze sobą różne funkcje sprawdzania poprawności na zwrócenie ich wszystkich wymuszenia `Result`.  Pozwala to przerwać funkcje następująco w małych fragmentów, które są jako konfigurowalna w razie potrzeby można.  Ma to również wartość dodaną *Wymuszanie* użytkowania [dopasowywania do wzorca](pattern-matching.md) na końcu podczas sprawdzania poprawności, które w chwili wymusza wyższy stopień poprawność program.

## <a name="see-also"></a>Zobacz także

- [Sumy rozłączne](discriminated-unions.md)
- [Dopasowanie do wzorca](pattern-matching.md)
