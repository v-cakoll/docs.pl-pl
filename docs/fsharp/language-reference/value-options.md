---
title: 'Opcje wartości (F #)'
description: 'Więcej informacji na temat typu wartości opcja F #, który jest wersja struktury typu opcji.'
ms.date: 06/16/2018
ms.openlocfilehash: 4c255cbbcfd9cb480230de09cd370a401c87343a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527586"
---
# <a name="value-options"></a><span data-ttu-id="c180f-103">Opcje wartości</span><span class="sxs-lookup"><span data-stu-id="c180f-103">Value Options</span></span>

<span data-ttu-id="c180f-104">Typ wartości opcji w F # jest używany podczas przechowywania następujących dwóch przypadkach:</span><span class="sxs-lookup"><span data-stu-id="c180f-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="c180f-105">Scenariusz jest odpowiedni dla [opcja F #](options.md).</span><span class="sxs-lookup"><span data-stu-id="c180f-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="c180f-106">Za pomocą struktury zapewnia korzyści wydajności, w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="c180f-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="c180f-107">Nie wszystkie scenariusze wrażliwego na wydajność to "rozwiązane" przy użyciu struktury.</span><span class="sxs-lookup"><span data-stu-id="c180f-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="c180f-108">Należy wziąć pod uwagę dodatkowych kosztów kopiowania podczas korzystania z nich zamiast typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="c180f-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="c180f-109">Jednak duże F # programy często tworzy wiele opcjonalne typy, które będą działać przy użyciu ścieżek krytycznych, ponieważ struktury czasami może przynieść lepiej ogólną wydajność przez cały okres istnienia programu.</span><span class="sxs-lookup"><span data-stu-id="c180f-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, because structs can sometimes yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="c180f-110">Definicja</span><span class="sxs-lookup"><span data-stu-id="c180f-110">Definition</span></span>

<span data-ttu-id="c180f-111">Wartość opcji jest zdefiniowany jako [sumy Unii](discriminated-unions.md#struct-discriminated-unions) jest podobny do typu opcja odwołania:</span><span class="sxs-lookup"><span data-stu-id="c180f-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpValueOption`1")>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone: 'T voption
    | ValueSome: 'T -> 'T voption

    member Value : 'T

and 'T voption = ValueOption<'T>
```

<span data-ttu-id="c180f-112">Wartość opcji jest zgodny ze strukturalnego równości i porównania.</span><span class="sxs-lookup"><span data-stu-id="c180f-112">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="c180f-113">Główną różnicą jest to, że skompilowanych nazwa, nazwa typu i wielkości liter nazwy wskazać, że jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="c180f-113">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="c180f-114">Za pomocą opcji wartość</span><span class="sxs-lookup"><span data-stu-id="c180f-114">Using Value Options</span></span>

<span data-ttu-id="c180f-115">Podobnie jak używane są opcje wartość [opcje](options.md).</span><span class="sxs-lookup"><span data-stu-id="c180f-115">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="c180f-116">`ValueSome` Służy do wskazywania, czy wartość jest obecna, a `ValueNone` jest używany, gdy nie jest wartością:</span><span class="sxs-lookup"><span data-stu-id="c180f-116">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="c180f-117">Podobnie jak w przypadku [opcje](options.md), Konwencja nazewnictwa dla funkcji, która zwraca `ValueOption` jest poprzedzić go `try`.</span><span class="sxs-lookup"><span data-stu-id="c180f-117">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="c180f-118">Wartość opcji właściwości i metody</span><span class="sxs-lookup"><span data-stu-id="c180f-118">Value Option properties and methods</span></span>

<span data-ttu-id="c180f-119">W tej chwili jest jedną właściwość dla opcji wartości: `Value`.</span><span class="sxs-lookup"><span data-stu-id="c180f-119">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="c180f-120"><xref:System.InvalidOperationException> Jest wywoływane, jeśli wartość nie jest obecna, gdy ta właściwość zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="c180f-120">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="c180f-121">Wartość opcji funkcji</span><span class="sxs-lookup"><span data-stu-id="c180f-121">Value Option functions</span></span>

<span data-ttu-id="c180f-122">Obecnie jest jedną funkcję powiązane z modułu dla opcji wartości `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="c180f-122">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

<span data-ttu-id="c180f-123">Podobnie jak w przypadku `defaultArg` funkcji `defaultValueArg` zwraca podstawową wartość danej opcji wartość, jeśli istnieje; w przeciwnym razie zwraca określoną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="c180f-123">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="c180f-124">W tej chwili nie istnieją żadnych funkcji powiązanych z modułu dla opcji wartości.</span><span class="sxs-lookup"><span data-stu-id="c180f-124">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="c180f-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c180f-125">See also</span></span>

[<span data-ttu-id="c180f-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="c180f-126">Options</span></span>](options.md)