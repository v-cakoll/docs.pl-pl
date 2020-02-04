---
title: Co nowego w F# 4,6 — F# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w F# 4,6.
ms.date: 11/27/2019
ms.openlocfilehash: 620c1edd8ea212fee306a02d5844b6b322808251
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980395"
---
# <a name="whats-new-in-f-46"></a>Co nowego w F# 4,6

F#4,6 dodaje wiele ulepszeń do F# języka.

## <a name="get-started"></a>Wprowadzenie

F#4,6 jest dostępny we wszystkich dystrybucjach .NET Core i narzędziach programu Visual Studio. [Zacznij korzystać z F# ](../get-started/index.md) programu, aby dowiedzieć się więcej.

## <a name="anonymous-records"></a>Rekordy anonimowe

[Rekordy anonimowe](../language-reference/anonymous-records.md) są nowym rodzajem F# typu wprowadzonym F# w 4,6. Są to proste zagregowane wartości nazwanych, które nie muszą być zadeklarowane przed użyciem. Można zadeklarować je jako struktury lub typy referencyjne. Domyślnie są to typy odwołań.

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Mogą być również zadeklarowane jako struktury dla, gdy chcesz grupować typy wartości i działają w scenariuszach z uwzględnieniem wydajności:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    struct {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Są one bardzo wydajne i mogą być używane w wielu scenariuszach. Dowiedz się więcej z [anonimowymi rekordami](../language-reference/anonymous-records.md).

## <a name="valueoption-functions"></a>Funkcje ValueOption

Typ ValueOption dodany w F# 4,5 ma teraz "parzystość funkcji powiązanej z modułem" z typem opcji. Poniżej przedstawiono niektóre z najczęściej używanych przykładów:

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> ValueNone
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> ValueSome

let reversedString = strOpt |> ValueOption.bind reverse
```

Pozwala to na użycie ValueOption, podobnie jak opcja w scenariuszach, gdzie typ wartości zwiększa wydajność.
