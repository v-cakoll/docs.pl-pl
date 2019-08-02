---
title: WycinkiF#()
description: Informacje na temat używania wycinków dla istniejących F# typów danych oraz sposobu definiowania własnych wycinków dla innych typów danych.
ms.date: 01/22/2019
ms.openlocfilehash: 3067982c2b4249312c7e9365bbfb994be840911d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627146"
---
# <a name="slices"></a><span data-ttu-id="b4e96-103">Wycinki</span><span class="sxs-lookup"><span data-stu-id="b4e96-103">Slices</span></span>

<span data-ttu-id="b4e96-104">W F#programie wycinek jest podzbiorem typu danych.</span><span class="sxs-lookup"><span data-stu-id="b4e96-104">In F#, a slice is a subset of a data type.</span></span> <span data-ttu-id="b4e96-105">Aby można było uzyskać wycinka z typu danych, typ danych musi definiować `GetSlice` metodę lub w rozszerzeniu [typu](type-extensions.md) , który znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="b4e96-105">To be able to take a slice from a data type, the data type must either define a `GetSlice` method or in a [type extension](type-extensions.md) that is in scope.</span></span> <span data-ttu-id="b4e96-106">W tym artykule wyjaśniono, jak korzystać z F# wycinków z istniejących typów i jak definiować własne.</span><span class="sxs-lookup"><span data-stu-id="b4e96-106">This article explains how to take slices from existing F# types and how to define your own.</span></span>

<span data-ttu-id="b4e96-107">Wycinki są podobne [](./members/indexed-properties.md)do indeksatorów, ale zamiast zwracać jedną wartość z bazowej struktury danych, uzyskują wiele z nich.</span><span class="sxs-lookup"><span data-stu-id="b4e96-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="b4e96-108">F#obecnie ma wewnętrzną obsługę ciągów wycinków, list, tablic i tablic 2D.</span><span class="sxs-lookup"><span data-stu-id="b4e96-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="b4e96-109">Podstawowe cięcie z F# listami i tablicami</span><span class="sxs-lookup"><span data-stu-id="b4e96-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="b4e96-110">Najpopularniejsze typy danych, które są pofragmentowane, F# to listy i tablice.</span><span class="sxs-lookup"><span data-stu-id="b4e96-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="b4e96-111">Poniższy przykład ilustruje, jak to zrobić za pomocą list:</span><span class="sxs-lookup"><span data-stu-id="b4e96-111">The following example demonstrates how to do this with lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

<span data-ttu-id="b4e96-112">Tablice odcięć są podobne do list wycinków:</span><span class="sxs-lookup"><span data-stu-id="b4e96-112">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="b4e96-113">Dzielenie tablic wielowymiarowych</span><span class="sxs-lookup"><span data-stu-id="b4e96-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="b4e96-114">F#obsługuje tablice wielowymiarowe w bibliotece F# podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b4e96-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="b4e96-115">Podobnie jak w przypadku tablic jednowymiarowych, wycinki tablic wielowymiarowych mogą być również użyteczne.</span><span class="sxs-lookup"><span data-stu-id="b4e96-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="b4e96-116">Jednak wprowadzenie dodatkowych wymiarów zezwala na nieznacznie inną składnię, dzięki czemu można przyjmować plasterki określonych wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="b4e96-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="b4e96-117">W poniższych przykładach pokazano, jak wydzielić tablicę 2D:</span><span class="sxs-lookup"><span data-stu-id="b4e96-117">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

<span data-ttu-id="b4e96-118">Biblioteka F# podstawowa nie definiuje `GetSlice`dla tablic 3W.</span><span class="sxs-lookup"><span data-stu-id="b4e96-118">The F# core library does not define `GetSlice`for 3D arrays.</span></span> <span data-ttu-id="b4e96-119">Jeśli chcesz wyrównać te lub inne tablice o większej liczbie wymiarów, musisz samodzielnie `GetSlice` zdefiniować element członkowski.</span><span class="sxs-lookup"><span data-stu-id="b4e96-119">If you wish to slice those or other arrays of more dimensions, you must define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="b4e96-120">Definiowanie wycinków dla innych struktur danych</span><span class="sxs-lookup"><span data-stu-id="b4e96-120">Defining slices for other data structures</span></span>

<span data-ttu-id="b4e96-121">Biblioteka F# podstawowa definiuje wycinki dla ograniczonego zestawu typów.</span><span class="sxs-lookup"><span data-stu-id="b4e96-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="b4e96-122">Jeśli chcesz zdefiniować wycinki dla większej liczby typów danych, możesz to zrobić w samej definicji typu lub w rozszerzeniu typu.</span><span class="sxs-lookup"><span data-stu-id="b4e96-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="b4e96-123">Na przykład poniżej przedstawiono sposób definiowania wycinków <xref:System.ArraySegment%601> klasy umożliwiającej wygodne manipulowanie danymi:</span><span class="sxs-lookup"><span data-stu-id="b4e96-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(?start, ?finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="b4e96-124">Użyj funkcji tworzenia konspektu, aby uniknąć pakowania, jeśli jest to konieczne</span><span class="sxs-lookup"><span data-stu-id="b4e96-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="b4e96-125">W przypadku definiowania wycinków dla typu, który jest w rzeczywistości strukturą, zalecamy, aby `inline` użytkownik `GetSlice` był członkiem.</span><span class="sxs-lookup"><span data-stu-id="b4e96-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="b4e96-126">F# Kompilator optymalizuje argumenty opcjonalne, unikając wszelkich alokacji sterty w wyniku wycinka.</span><span class="sxs-lookup"><span data-stu-id="b4e96-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="b4e96-127">Jest to istotne znaczenie dla konstrukcji wycinków, takich jak <xref:System.Span%601> , których nie można przydzielić na stercie.</span><span class="sxs-lookup"><span data-stu-id="b4e96-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a><span data-ttu-id="b4e96-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4e96-128">See also</span></span>

- [<span data-ttu-id="b4e96-129">Właściwości indeksowane</span><span class="sxs-lookup"><span data-stu-id="b4e96-129">Indexed properties</span></span>](./members/indexed-properties.md)
