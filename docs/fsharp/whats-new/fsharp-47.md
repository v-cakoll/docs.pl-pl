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
# <a name="whats-new-in-f-47"></a><span data-ttu-id="7a519-103">Co nowego w F# 4,7</span><span class="sxs-lookup"><span data-stu-id="7a519-103">What's new in F# 4.7</span></span>

<span data-ttu-id="7a519-104">F#4,7 dodaje wiele ulepszeń do F# języka.</span><span class="sxs-lookup"><span data-stu-id="7a519-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="7a519-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="7a519-105">Get started</span></span>

<span data-ttu-id="7a519-106">F#4,7 jest dostępny we wszystkich dystrybucjach .NET Core i narzędziach programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a519-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="7a519-107">[Zacznij korzystać z F# ](../get-started/index.md) programu, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="7a519-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="7a519-108">Wersja językowa</span><span class="sxs-lookup"><span data-stu-id="7a519-108">Language version</span></span>

<span data-ttu-id="7a519-109">Kompilator F# 4,7 wprowadza możliwość ustawienia efektywnej wersji językowej przez właściwość w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="7a519-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="7a519-110">Można ustawić wartość `4.6`, `4.7`, `latest`i `preview`.</span><span class="sxs-lookup"><span data-stu-id="7a519-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="7a519-111">Wartość domyślna to `latest`.</span><span class="sxs-lookup"><span data-stu-id="7a519-111">The default is `latest`.</span></span>

<span data-ttu-id="7a519-112">Jeśli ustawisz ją na `preview`, kompilator będzie aktywować wszystkie F# funkcje w wersji zapoznawczej zaimplementowane w kompilatorze.</span><span class="sxs-lookup"><span data-stu-id="7a519-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="7a519-113">Niejawne implikuje</span><span class="sxs-lookup"><span data-stu-id="7a519-113">Implicit yields</span></span>

<span data-ttu-id="7a519-114">Nie trzeba już stosować słowa kluczowego `yield` w tablicach, listach, sekwencjach ani wyrażeniach obliczeń, w których można wywnioskować typ.</span><span class="sxs-lookup"><span data-stu-id="7a519-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="7a519-115">W poniższym przykładzie oba wyrażenia wymagały instrukcji `yield` dla każdego wpisu przed F# 4,7:</span><span class="sxs-lookup"><span data-stu-id="7a519-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

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

<span data-ttu-id="7a519-116">Po wprowadzeniu pojedynczego słowa kluczowego `yield`, każdy inny element musi również mieć zastosowany `yield`.</span><span class="sxs-lookup"><span data-stu-id="7a519-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="7a519-117">Niejawne implikuje nie są aktywowane, gdy są używane w wyrażeniu, które również używa `yield!`, aby wykonać coś takiego jak Spłaszcz sekwencję.</span><span class="sxs-lookup"><span data-stu-id="7a519-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="7a519-118">W tych przypadkach należy nadal używać `yield` dzisiaj.</span><span class="sxs-lookup"><span data-stu-id="7a519-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="7a519-119">Identyfikatory wieloznaczne</span><span class="sxs-lookup"><span data-stu-id="7a519-119">Wildcard identifiers</span></span>

<span data-ttu-id="7a519-120">W F# kodzie zawierającym klasy, identyfikator własny musi zawsze być jawny w deklaracjach składowych.</span><span class="sxs-lookup"><span data-stu-id="7a519-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="7a519-121">Ale w przypadkach, gdy sama identyfikator nie jest nigdy używany, ma tradycyjną Konwencję, aby użyć podwójnego podkreślenia, aby wskazać pustego samoidentyfikatory.</span><span class="sxs-lookup"><span data-stu-id="7a519-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="7a519-122">Teraz można użyć pojedynczej podkreślenia:</span><span class="sxs-lookup"><span data-stu-id="7a519-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="7a519-123">Dotyczy to również pętli `for`:</span><span class="sxs-lookup"><span data-stu-id="7a519-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="7a519-124">Złagodzenie wcięć</span><span class="sxs-lookup"><span data-stu-id="7a519-124">Indentation relaxations</span></span>

<span data-ttu-id="7a519-125">Przed F# 4,7, wymagania wcięcia dla konstruktora podstawowego i statycznych argumentów elementu członkowskiego wymagały nadmiernego wcięcia.</span><span class="sxs-lookup"><span data-stu-id="7a519-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="7a519-126">Teraz wymagany jest tylko pojedynczy zakres wcięć:</span><span class="sxs-lookup"><span data-stu-id="7a519-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
