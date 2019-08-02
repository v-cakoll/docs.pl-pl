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
# <a name="slices"></a>Wycinki

W F#programie wycinek jest podzbiorem typu danych. Aby można było uzyskać wycinka z typu danych, typ danych musi definiować `GetSlice` metodę lub w rozszerzeniu [typu](type-extensions.md) , który znajduje się w zakresie. W tym artykule wyjaśniono, jak korzystać z F# wycinków z istniejących typów i jak definiować własne.

Wycinki są podobne [](./members/indexed-properties.md)do indeksatorów, ale zamiast zwracać jedną wartość z bazowej struktury danych, uzyskują wiele z nich.

F#obecnie ma wewnętrzną obsługę ciągów wycinków, list, tablic i tablic 2D.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Podstawowe cięcie z F# listami i tablicami

Najpopularniejsze typy danych, które są pofragmentowane, F# to listy i tablice. Poniższy przykład ilustruje, jak to zrobić za pomocą list:

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

Tablice odcięć są podobne do list wycinków:

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

## <a name="slicing-multidimensional-arrays"></a>Dzielenie tablic wielowymiarowych

F#obsługuje tablice wielowymiarowe w bibliotece F# podstawowej. Podobnie jak w przypadku tablic jednowymiarowych, wycinki tablic wielowymiarowych mogą być również użyteczne. Jednak wprowadzenie dodatkowych wymiarów zezwala na nieznacznie inną składnię, dzięki czemu można przyjmować plasterki określonych wierszy i kolumn.

W poniższych przykładach pokazano, jak wydzielić tablicę 2D:

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

Biblioteka F# podstawowa nie definiuje `GetSlice`dla tablic 3W. Jeśli chcesz wyrównać te lub inne tablice o większej liczbie wymiarów, musisz samodzielnie `GetSlice` zdefiniować element członkowski.

## <a name="defining-slices-for-other-data-structures"></a>Definiowanie wycinków dla innych struktur danych

Biblioteka F# podstawowa definiuje wycinki dla ograniczonego zestawu typów. Jeśli chcesz zdefiniować wycinki dla większej liczby typów danych, możesz to zrobić w samej definicji typu lub w rozszerzeniu typu.

Na przykład poniżej przedstawiono sposób definiowania wycinków <xref:System.ArraySegment%601> klasy umożliwiającej wygodne manipulowanie danymi:

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Użyj funkcji tworzenia konspektu, aby uniknąć pakowania, jeśli jest to konieczne

W przypadku definiowania wycinków dla typu, który jest w rzeczywistości strukturą, zalecamy, aby `inline` użytkownik `GetSlice` był członkiem. F# Kompilator optymalizuje argumenty opcjonalne, unikając wszelkich alokacji sterty w wyniku wycinka. Jest to istotne znaczenie dla konstrukcji wycinków, takich jak <xref:System.Span%601> , których nie można przydzielić na stercie.

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

- [Właściwości indeksowane](./members/indexed-properties.md)
