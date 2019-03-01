---
title: Wycinki (F#)
description: Dowiedz się więcej o tym, jak używać wycinków dla istniejących F# typów danych i jak zdefiniować własne wycinki dla innych typów danych.
ms.date: 01/22/2019
ms.openlocfilehash: 60b57d4eea40bb26dc43d8255dd933b63ac6303c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970115"
---
# <a name="slices"></a>Wycinki

W F#, wycinek jest podzbiorem typu danych. Aby można było wykonać wycinek z typem danych, typ danych należy zdefiniować `GetSlice` metody lub [wpisz rozszerzenie](type-extensions.md) to znaczy w zakresie. W tym artykule wyjaśniono, jak wykonać wycinków z istniejących F# typów i jak Definiowanie własnych.

Wycinki są podobne do [indeksatory](members/indexed-properties.md), ale zamiast reaguje pojedynczą wartość z podstawową strukturę danych, dają one wiele migawek.

F#obecnie obsługuje wewnętrzne dla dzielenie ciągów, list, tablic i tablice 2D.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Podstawowe wycinków z F# list i tablice

Najpopularniejsze typy danych, które jest podzielona na fragmenty są F# list i tablic. Poniższy przykład pokazuje, jak to zrobić przy użyciu list:

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

Wycinków tablic jest takie samo jak dzielenie listy:

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

## <a name="slicing-multidimensional-arrays"></a>Wycinków tablic wielowymiarowych

F#obsługuje tablice wielowymiarowe w F# podstawowej biblioteki. Podobnie jak w przypadku tablic jednowymiarowych wycinków tablic wielowymiarowych może być również przydatne. Jednak wprowadzenie dodatkowych wymiarów określającemu nieco składnią, można korzystać wycinki określonych wierszy i kolumn.

Poniższe przykłady pokazują, jak slice tablicę 2D:

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
printfn "%A" twobyTwo
```

F# Podstawowej biblioteki nie definiuje `GetSlice`macierzy 3W. Jeśli użytkownik chce slice tych lub innych tablic więcej wymiarów, należy zdefiniować `GetSlice` elementu członkowskiego samodzielnie.

## <a name="defining-slices-for-other-data-structures"></a>Definiowanie wycinki dla innych struktur danych

F# Podstawowej biblioteki definiuje wycinki dla ograniczony zestaw typów. Jeśli chcesz zdefiniować wycinki dla większej liczby typów danych, możesz to zrobić w definicji typu lub rozszerzenie typu.

Na przykład Oto, jak można zdefiniować wycinki dla <xref:System.ArraySegment%601> klasy umożliwiające manipulowanie danymi wygodne:

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Korzystanie ze śródwierszowaniem, aby uniknąć pakowania, jeśli to konieczne

Jeśli definiujesz wycinki dla typu, który jest faktycznie struktury, zalecamy możesz `inline` `GetSlice` elementu członkowskiego. F# Kompilatora natychmiast optymalizuje Argumenty opcjonalne, unikając dowolnych alokacji sterty w wyniku tworzenia wycinków. Jest to niezwykle ważne w przypadku tworzenia wycinków konstrukcji, takich jak <xref:System.Span%601> nie można przydzielić na stosie.

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

## <a name="see-also"></a>Zobacz także

- [Właściwości indeksowane](members/indexed-properties.md)
