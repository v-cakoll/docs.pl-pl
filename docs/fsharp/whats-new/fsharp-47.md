---
title: Co nowego w F# 4,7 — F# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w F# 4,7.
ms.date: 11/27/2019
ms.openlocfilehash: 203b258466cb9f1f50215ecf8884e92e7e86416b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644069"
---
# <a name="whats-new-in-f-47"></a>Co nowego w F# 4,7

F#4,7 dodaje wiele ulepszeń do F# języka.

## <a name="get-started"></a>Wprowadzenie

F#4,7 jest dostępny we wszystkich dystrybucjach .NET Core i narzędziach programu Visual Studio. [Zacznij korzystać z F# ](../get-started/index.md) programu, aby dowiedzieć się więcej.

## <a name="language-version"></a>Wersja językowa

Kompilator F# 4,7 wprowadza możliwość ustawienia efektywnej wersji językowej przez właściwość w pliku projektu:

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Można ustawić wartość `4.6`, `4.7`, `latest`i `preview`. Wartość domyślna to `latest`.

Jeśli ustawisz ją na `preview`, kompilator będzie aktywować wszystkie F# funkcje w wersji zapoznawczej zaimplementowane w kompilatorze.

## <a name="implicit-yields"></a>Niejawne implikuje

Nie trzeba już stosować słowa kluczowego `yield` w tablicach, listach, sekwencjach ani wyrażeniach obliczeń, w których można wywnioskować typ. W poniższym przykładzie oba wyrażenia wymagały instrukcji `yield` dla każdego wpisu przed F# 4,7:

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

Po wprowadzeniu pojedynczego słowa kluczowego `yield`, każdy inny element musi również mieć zastosowany `yield`.

Niejawne implikuje nie są aktywowane, gdy są używane w wyrażeniu, które również używa `yield!`, aby wykonać coś takiego jak Spłaszcz sekwencję. W tych przypadkach należy nadal używać `yield` dzisiaj.

## <a name="wildcard-identifiers"></a>Identyfikatory wieloznaczne

W F# kodzie zawierającym klasy, identyfikator własny musi zawsze być jawny w deklaracjach składowych. Ale w przypadkach, gdy sama identyfikator nie jest nigdy używany, ma tradycyjną Konwencję, aby użyć podwójnego podkreślenia, aby wskazać pustego samoidentyfikatory. Teraz można użyć pojedynczej podkreślenia:

```fsharp
type C() =
    member _.M() = ()
```

Dotyczy to również pętli `for`:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Złagodzenie wcięć

Przed F# 4,7, wymagania wcięcia dla konstruktora podstawowego i statycznych argumentów elementu członkowskiego wymagały nadmiernego wcięcia. Teraz wymagany jest tylko pojedynczy zakres wcięć:

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
