---
title: Wycinki (F#)
description: Dowiedz się więcej o tym, jak używać wycinków dla istniejących F# typów danych i jak zdefiniować własne wycinki dla innych typów danych.
ms.date: 01/22/2019
ms.openlocfilehash: 1d8bb029ad18c8853ab58888959967ed279fb368
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61926000"
---
# <a name="slices"></a><span data-ttu-id="4036a-103">Wycinki</span><span class="sxs-lookup"><span data-stu-id="4036a-103">Slices</span></span>

<span data-ttu-id="4036a-104">W F#, wycinek jest podzbiorem typu danych.</span><span class="sxs-lookup"><span data-stu-id="4036a-104">In F#, a slice is a subset of a data type.</span></span> <span data-ttu-id="4036a-105">Aby można było wykonać wycinek z typem danych, typ danych należy zdefiniować `GetSlice` metody lub [wpisz rozszerzenie](type-extensions.md) to znaczy w zakresie.</span><span class="sxs-lookup"><span data-stu-id="4036a-105">To be able to take a slice from a data type, the data type must either define a `GetSlice` method or in a [type extension](type-extensions.md) that is in scope.</span></span> <span data-ttu-id="4036a-106">W tym artykule wyjaśniono, jak wykonać wycinków z istniejących F# typów i jak Definiowanie własnych.</span><span class="sxs-lookup"><span data-stu-id="4036a-106">This article explains how to take slices from existing F# types and how to define your own.</span></span>

<span data-ttu-id="4036a-107">Wycinki są podobne do [indeksatory](members/indexed-properties.md), ale zamiast reaguje pojedynczą wartość z podstawową strukturę danych, dają one wiele migawek.</span><span class="sxs-lookup"><span data-stu-id="4036a-107">Slices are similar to [indexers](members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="4036a-108">F#obecnie obsługuje wewnętrzne dla dzielenie ciągów, list, tablic i tablice 2D.</span><span class="sxs-lookup"><span data-stu-id="4036a-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="4036a-109">Podstawowe wycinków z F# list i tablice</span><span class="sxs-lookup"><span data-stu-id="4036a-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="4036a-110">Najpopularniejsze typy danych, które jest podzielona na fragmenty są F# list i tablic.</span><span class="sxs-lookup"><span data-stu-id="4036a-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="4036a-111">Poniższy przykład pokazuje, jak to zrobić przy użyciu list:</span><span class="sxs-lookup"><span data-stu-id="4036a-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="4036a-112">Wycinków tablic jest takie samo jak dzielenie listy:</span><span class="sxs-lookup"><span data-stu-id="4036a-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="4036a-113">Wycinków tablic wielowymiarowych</span><span class="sxs-lookup"><span data-stu-id="4036a-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="4036a-114">F#obsługuje tablice wielowymiarowe w F# podstawowej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4036a-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="4036a-115">Podobnie jak w przypadku tablic jednowymiarowych wycinków tablic wielowymiarowych może być również przydatne.</span><span class="sxs-lookup"><span data-stu-id="4036a-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="4036a-116">Jednak wprowadzenie dodatkowych wymiarów określającemu nieco składnią, można korzystać wycinki określonych wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="4036a-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="4036a-117">Poniższe przykłady pokazują, jak slice tablicę 2D:</span><span class="sxs-lookup"><span data-stu-id="4036a-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="4036a-118">F# Podstawowej biblioteki nie definiuje `GetSlice`macierzy 3W.</span><span class="sxs-lookup"><span data-stu-id="4036a-118">The F# core library does not define `GetSlice`for 3D arrays.</span></span> <span data-ttu-id="4036a-119">Jeśli użytkownik chce slice tych lub innych tablic więcej wymiarów, należy zdefiniować `GetSlice` elementu członkowskiego samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="4036a-119">If you wish to slice those or other arrays of more dimensions, you must define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="4036a-120">Definiowanie wycinki dla innych struktur danych</span><span class="sxs-lookup"><span data-stu-id="4036a-120">Defining slices for other data structures</span></span>

<span data-ttu-id="4036a-121">F# Podstawowej biblioteki definiuje wycinki dla ograniczony zestaw typów.</span><span class="sxs-lookup"><span data-stu-id="4036a-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="4036a-122">Jeśli chcesz zdefiniować wycinki dla większej liczby typów danych, możesz to zrobić w definicji typu lub rozszerzenie typu.</span><span class="sxs-lookup"><span data-stu-id="4036a-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="4036a-123">Na przykład Oto, jak można zdefiniować wycinki dla <xref:System.ArraySegment%601> klasy umożliwiające manipulowanie danymi wygodne:</span><span class="sxs-lookup"><span data-stu-id="4036a-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="4036a-124">Korzystanie ze śródwierszowaniem, aby uniknąć pakowania, jeśli to konieczne</span><span class="sxs-lookup"><span data-stu-id="4036a-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="4036a-125">Jeśli definiujesz wycinki dla typu, który jest faktycznie struktury, zalecamy możesz `inline` `GetSlice` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="4036a-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="4036a-126">F# Kompilatora natychmiast optymalizuje Argumenty opcjonalne, unikając dowolnych alokacji sterty w wyniku tworzenia wycinków.</span><span class="sxs-lookup"><span data-stu-id="4036a-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="4036a-127">Jest to niezwykle ważne w przypadku tworzenia wycinków konstrukcji, takich jak <xref:System.Span%601> nie można przydzielić na stosie.</span><span class="sxs-lookup"><span data-stu-id="4036a-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4036a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4036a-128">See also</span></span>

- [<span data-ttu-id="4036a-129">Właściwości indeksowane</span><span class="sxs-lookup"><span data-stu-id="4036a-129">Indexed properties</span></span>](members/indexed-properties.md)
