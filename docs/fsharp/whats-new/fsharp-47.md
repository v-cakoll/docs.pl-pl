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
# <a name="whats-new-in-f-47"></a><span data-ttu-id="5b207-103">Co nowego w Języku F# 4.7</span><span class="sxs-lookup"><span data-stu-id="5b207-103">What's new in F# 4.7</span></span>

<span data-ttu-id="5b207-104">F# 4.7 dodaje wiele ulepszeń do języka F#.</span><span class="sxs-lookup"><span data-stu-id="5b207-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="5b207-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="5b207-105">Get started</span></span>

<span data-ttu-id="5b207-106">F# 4.7 jest dostępny we wszystkich dystrybucjach .NET Core i visual studio narzędzi.</span><span class="sxs-lookup"><span data-stu-id="5b207-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="5b207-107">[Zacznij korzystać z języka F#,](../get-started/index.md) aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="5b207-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="5b207-108">Wersja językowa</span><span class="sxs-lookup"><span data-stu-id="5b207-108">Language version</span></span>

<span data-ttu-id="5b207-109">Kompilator F# 4.7 wprowadza możliwość ustawienia efektywnej wersji językowej za pośrednictwem właściwości w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="5b207-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="5b207-110">Można ustawić go na `4.6` `4.7`wartości `latest`, `preview`, , i .</span><span class="sxs-lookup"><span data-stu-id="5b207-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="5b207-111">Wartość domyślna to `latest`.</span><span class="sxs-lookup"><span data-stu-id="5b207-111">The default is `latest`.</span></span>

<span data-ttu-id="5b207-112">Jeśli ustawisz `preview`go na , kompilator uaktywnienie wszystkich funkcji podglądu F#, które są implementowane w kompilatorze.</span><span class="sxs-lookup"><span data-stu-id="5b207-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="5b207-113">Plony niejawne</span><span class="sxs-lookup"><span data-stu-id="5b207-113">Implicit yields</span></span>

<span data-ttu-id="5b207-114">Nie trzeba już stosować `yield` słowa kluczowego w tablicach, listach, sekwencjach lub wyrażeniach obliczeniowych, w których można wywnioskować typ.</span><span class="sxs-lookup"><span data-stu-id="5b207-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="5b207-115">W poniższym przykładzie oba wyrażenia `yield` wymagane instrukcji dla każdego wpisu przed F# 4.7:</span><span class="sxs-lookup"><span data-stu-id="5b207-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

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

<span data-ttu-id="5b207-116">Jeśli wprowadzisz jedno `yield` słowo kluczowe, `yield` każdy inny element musi również zostać do niego zastosowany.</span><span class="sxs-lookup"><span data-stu-id="5b207-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="5b207-117">Niejawne plony nie są aktywowane, `yield!` gdy są używane w wyrażeniu, które również używa do wykonywania czegoś takiego jak spłaszczenie sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5b207-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="5b207-118">W takich przypadkach `yield` należy nadal używać.</span><span class="sxs-lookup"><span data-stu-id="5b207-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="5b207-119">Identyfikatory symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="5b207-119">Wildcard identifiers</span></span>

<span data-ttu-id="5b207-120">W kodzie F# obejmujących klasy, identyfikator własny musi być zawsze jawne w deklaracjach elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5b207-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="5b207-121">Ale w przypadkach, gdy samoidentyfikujący się identyfikator nigdy nie jest używany, tradycyjnie konwencją było użycie podwójnego podkreślenia w celu wskazania bezimiennych samoidentyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="5b207-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="5b207-122">Możesz teraz użyć jednego znaku podkreślenia:</span><span class="sxs-lookup"><span data-stu-id="5b207-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="5b207-123">Dotyczy to również `for` pętli:</span><span class="sxs-lookup"><span data-stu-id="5b207-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="5b207-124">Relaksacje wcięcia</span><span class="sxs-lookup"><span data-stu-id="5b207-124">Indentation relaxations</span></span>

<span data-ttu-id="5b207-125">Przed F# 4.7 wymagania wcięcia dla podstawowego konstruktora i statyczne argumenty elementu członkowskiego wymagane nadmierne wcięcie.</span><span class="sxs-lookup"><span data-stu-id="5b207-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="5b207-126">Teraz wymagają one tylko jednego zakresu wcięcia:</span><span class="sxs-lookup"><span data-stu-id="5b207-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
