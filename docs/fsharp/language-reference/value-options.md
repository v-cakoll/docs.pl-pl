---
title: Opcje wartości
description: Dowiedz się F# więcej o typie opcji wartość, która jest wersją struktury typu opcji.
ms.date: 02/06/2019
ms.openlocfilehash: 4dc3f7217943345b7aaf1165fd648ab2e01bd727
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424019"
---
# <a name="value-options"></a><span data-ttu-id="0e3dd-103">Opcje wartości</span><span class="sxs-lookup"><span data-stu-id="0e3dd-103">Value Options</span></span>

<span data-ttu-id="0e3dd-104">Typ opcji wartość w jest F# używany w przypadku, gdy są utrzymywane następujące dwa sytuacje:</span><span class="sxs-lookup"><span data-stu-id="0e3dd-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="0e3dd-105">Scenariusz jest odpowiedni dla [ F# opcji](options.md).</span><span class="sxs-lookup"><span data-stu-id="0e3dd-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="0e3dd-106">Użycie struktury zapewnia korzyść wydajności w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="0e3dd-107">Nie wszystkie scenariusze z uwzględnieniem wydajności są "rozwiązane" przy użyciu struktur.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="0e3dd-108">Należy wziąć pod uwagę dodatkowy koszt kopiowania, gdy są używane zamiast typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="0e3dd-109">Jednak duże F# programy często żądają wielu opcjonalnych typów, które przepływają przez ścieżki gorąca, a w takich przypadkach struktury mogą często dać lepszą wydajność w okresie istnienia programu.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="0e3dd-110">Definicja</span><span class="sxs-lookup"><span data-stu-id="0e3dd-110">Definition</span></span>

<span data-ttu-id="0e3dd-111">Opcja Value jest definiowana jako [związek rozłącznych struktur](discriminated-unions.md#struct-discriminated-unions) , który jest podobny do typu opcji odwołania.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="0e3dd-112">Jego definicję można traktować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0e3dd-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="0e3dd-113">Opcja wartości jest zgodna z kryterium równości i porównywania strukturalnego.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="0e3dd-114">Główną różnicą jest to, że skompilowana nazwa, nazwa typu i nazwy przypadków wskazują, że jest to typ wartości.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="0e3dd-115">Korzystanie z opcji wartości</span><span class="sxs-lookup"><span data-stu-id="0e3dd-115">Using Value Options</span></span>

<span data-ttu-id="0e3dd-116">Opcje wartości są używane podobnie jak [Opcje](options.md).</span><span class="sxs-lookup"><span data-stu-id="0e3dd-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="0e3dd-117">`ValueSome` jest używany do wskazania, że wartość jest obecna, a `ValueNone` jest używana, gdy wartość nie jest obecna:</span><span class="sxs-lookup"><span data-stu-id="0e3dd-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="0e3dd-118">Podobnie jak w przypadku [opcji](options.md), Konwencja nazewnictwa dla funkcji, która zwraca `ValueOption`, to prefiks z `try`.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="0e3dd-119">Właściwości opcji wartości i metody</span><span class="sxs-lookup"><span data-stu-id="0e3dd-119">Value Option properties and methods</span></span>

<span data-ttu-id="0e3dd-120">W tej chwili istnieje jedna Właściwość opcji wartości: `Value`.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="0e3dd-121"><xref:System.InvalidOperationException> jest wywoływane, jeśli żadna wartość nie jest obecna, gdy ta właściwość jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="0e3dd-122">Funkcje opcji wartości</span><span class="sxs-lookup"><span data-stu-id="0e3dd-122">Value Option functions</span></span>

<span data-ttu-id="0e3dd-123">Obecnie istnieje jedna funkcja powiązana z modułem dla opcji wartości, `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="0e3dd-123">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="0e3dd-124">Podobnie jak w przypadku funkcji `defaultArg`, `defaultValueArg` zwraca wartość podstawową danej wartości, jeśli istnieje; w przeciwnym razie zwraca określoną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-124">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="0e3dd-125">W tej chwili nie ma żadnych innych funkcji powiązanych z modułem dla opcji wartości.</span><span class="sxs-lookup"><span data-stu-id="0e3dd-125">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e3dd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e3dd-126">See also</span></span>

- [<span data-ttu-id="0e3dd-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="0e3dd-127">Options</span></span>](options.md)
