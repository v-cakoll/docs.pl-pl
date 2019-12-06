---
title: Opcje wartości
description: Dowiedz się F# więcej o typie opcji wartość, która jest wersją struktury typu opcji.
ms.date: 12/04/2019
ms.openlocfilehash: 0e9882ab4acdf2757705ef6022516d3572d87ef2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837119"
---
# <a name="value-options"></a><span data-ttu-id="206c2-103">Opcje wartości</span><span class="sxs-lookup"><span data-stu-id="206c2-103">Value Options</span></span>

<span data-ttu-id="206c2-104">Typ opcji wartość w jest F# używany w przypadku, gdy są utrzymywane następujące dwa sytuacje:</span><span class="sxs-lookup"><span data-stu-id="206c2-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="206c2-105">Scenariusz jest odpowiedni dla [ F# opcji](options.md).</span><span class="sxs-lookup"><span data-stu-id="206c2-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="206c2-106">Użycie struktury zapewnia korzyść wydajności w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="206c2-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="206c2-107">Nie wszystkie scenariusze z uwzględnieniem wydajności są "rozwiązane" przy użyciu struktur.</span><span class="sxs-lookup"><span data-stu-id="206c2-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="206c2-108">Należy wziąć pod uwagę dodatkowy koszt kopiowania, gdy są używane zamiast typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="206c2-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="206c2-109">Jednak duże F# programy często żądają wielu opcjonalnych typów, które przepływają przez ścieżki gorąca, a w takich przypadkach struktury mogą często dać lepszą wydajność w okresie istnienia programu.</span><span class="sxs-lookup"><span data-stu-id="206c2-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="206c2-110">Definicja</span><span class="sxs-lookup"><span data-stu-id="206c2-110">Definition</span></span>

<span data-ttu-id="206c2-111">Opcja Value jest definiowana jako [związek rozłącznych struktur](discriminated-unions.md#struct-discriminated-unions) , który jest podobny do typu opcji odwołania.</span><span class="sxs-lookup"><span data-stu-id="206c2-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="206c2-112">Jego definicję można traktować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="206c2-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="206c2-113">Opcja wartości jest zgodna z kryterium równości i porównywania strukturalnego.</span><span class="sxs-lookup"><span data-stu-id="206c2-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="206c2-114">Główną różnicą jest to, że skompilowana nazwa, nazwa typu i nazwy przypadków wskazują, że jest to typ wartości.</span><span class="sxs-lookup"><span data-stu-id="206c2-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="206c2-115">Korzystanie z opcji wartości</span><span class="sxs-lookup"><span data-stu-id="206c2-115">Using Value Options</span></span>

<span data-ttu-id="206c2-116">Opcje wartości są używane podobnie jak [Opcje](options.md).</span><span class="sxs-lookup"><span data-stu-id="206c2-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="206c2-117">`ValueSome` jest używany do wskazania, że wartość jest obecna, a `ValueNone` jest używana, gdy wartość nie jest obecna:</span><span class="sxs-lookup"><span data-stu-id="206c2-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

<span data-ttu-id="206c2-118">Podobnie jak w przypadku [opcji](options.md), Konwencja nazewnictwa dla funkcji, która zwraca `ValueOption`, to prefiks z `try`.</span><span class="sxs-lookup"><span data-stu-id="206c2-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="206c2-119">Właściwości opcji wartości i metody</span><span class="sxs-lookup"><span data-stu-id="206c2-119">Value Option properties and methods</span></span>

<span data-ttu-id="206c2-120">W tej chwili istnieje jedna Właściwość opcji wartości: `Value`.</span><span class="sxs-lookup"><span data-stu-id="206c2-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="206c2-121"><xref:System.InvalidOperationException> jest wywoływane, jeśli żadna wartość nie jest obecna, gdy ta właściwość jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="206c2-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="206c2-122">Funkcje opcji wartości</span><span class="sxs-lookup"><span data-stu-id="206c2-122">Value Option functions</span></span>

<span data-ttu-id="206c2-123">Moduł `ValueOption` w FSharp. Core zawiera funkcje równoważne do modułu `Option`.</span><span class="sxs-lookup"><span data-stu-id="206c2-123">The `ValueOption` module in FSharp.Core contains equivalent functionality to the `Option` module.</span></span> <span data-ttu-id="206c2-124">Istnieje kilka różnic nazw, takich jak `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="206c2-124">There are a few differences in name, such as `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="206c2-125">Działa tak samo jak `defaultArg` w module `Option`, ale działa w zamian opcji Value.</span><span class="sxs-lookup"><span data-stu-id="206c2-125">This acts just like `defaultArg` in the `Option` module, but operates on a Value Option instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="206c2-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="206c2-126">See also</span></span>

- [<span data-ttu-id="206c2-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="206c2-127">Options</span></span>](options.md)
