---
title: Co nowego w Przewodniku po językach F# 4.7 — F#
description: Zapoznaj się z nowymi funkcjami dostępnymi w języku F# 4.7.
ms.date: 11/27/2019
ms.openlocfilehash: 7a6e744a398719bcb55d168dd700459e0b122dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185878"
---
# <a name="whats-new-in-f-47"></a>Co nowego w Języku F# 4.7

F# 4.7 dodaje wiele ulepszeń do języka F#.

## <a name="get-started"></a>Wprowadzenie

F# 4.7 jest dostępny we wszystkich dystrybucjach .NET Core i visual studio narzędzi. [Zacznij korzystać z języka F#,](../get-started/index.md) aby dowiedzieć się więcej.

## <a name="language-version"></a>Wersja językowa

Kompilator F# 4.7 wprowadza możliwość ustawienia efektywnej wersji językowej za pośrednictwem właściwości w pliku projektu:

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Można ustawić go na `4.6` `4.7`wartości `latest`, `preview`, , i . Wartość domyślna to `latest`.

Jeśli ustawisz `preview`go na , kompilator uaktywnienie wszystkich funkcji podglądu F#, które są implementowane w kompilatorze.

## <a name="implicit-yields"></a>Plony niejawne

Nie trzeba już stosować `yield` słowa kluczowego w tablicach, listach, sekwencjach lub wyrażeniach obliczeniowych, w których można wywnioskować typ. W poniższym przykładzie oba wyrażenia `yield` wymagane instrukcji dla każdego wpisu przed F# 4.7:

```fsharp
let s = seq { 1; 2; 3; 4; 5 }

let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]
```

Jeśli wprowadzisz jedno `yield` słowo kluczowe, `yield` każdy inny element musi również zostać do niego zastosowany.

Niejawne plony nie są aktywowane, `yield!` gdy są używane w wyrażeniu, które również używa do wykonywania czegoś takiego jak spłaszczenie sekwencji. W takich przypadkach `yield` należy nadal używać.

## <a name="wildcard-identifiers"></a>Identyfikatory symboli wieloznacznych

W kodzie F# obejmujących klasy, identyfikator własny musi być zawsze jawne w deklaracjach elementów członkowskich. Ale w przypadkach, gdy samoidentyfikujący się identyfikator nigdy nie jest używany, tradycyjnie konwencją było użycie podwójnego podkreślenia w celu wskazania bezimiennych samoidentyfikatorów. Możesz teraz użyć jednego znaku podkreślenia:

```fsharp
type C() =
    member _.M() = ()
```

Dotyczy to również `for` pętli:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Relaksacje wcięcia

Przed F# 4.7 wymagania wcięcia dla podstawowego konstruktora i statyczne argumenty elementu członkowskiego wymagane nadmierne wcięcie. Teraz wymagają one tylko jednego zakresu wcięcia:

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
