---
title: Co nowego w Przewodniku po językach F# 4.5 — F#
description: Zapoznaj się z nowymi funkcjami dostępnymi w języku F# 4.5.
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186135"
---
# <a name="whats-new-in-f-45"></a>Co nowego w Języku F# 4.5

F# 4.5 dodaje wiele ulepszeń do języka F#. Wiele z tych funkcji zostały dodane razem, aby umożliwić pisanie kodu efektywnego wydajności w języku F# przy jednoczesnym zapewnieniu, że ten kod jest bezpieczny. Oznacza to dodanie kilku pojęć do języka i znaczną ilość analizy kompilatora podczas korzystania z tych konstrukcji.

## <a name="get-started"></a>Wprowadzenie

F# 4.5 jest dostępny we wszystkich dystrybucjach .NET Core i visual studio narzędzi. [Zacznij korzystać z języka F#,](../get-started/index.md) aby dowiedzieć się więcej.

## <a name="span-and-byref-like-structs"></a>Struktury span i byref-jak

Typ <xref:System.Span%601> wprowadzony w .NET Core umożliwia reprezentowanie buforów w pamięci w sposób silnie typizowany, który jest teraz dozwolony w języku F#, począwszy od języka F# 4.5. W poniższym przykładzie pokazano, jak można ponownie <xref:System.Span%601> użyć funkcji działającej na różnych reprezentacjach buforu:

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

Ważnym aspektem jest to, że Span i inne [struktury byref-jak](../language-reference/structures.md#byreflike-structs) mają bardzo sztywną analizę statyczną wykonywaną przez kompilator, które ograniczają ich użycie w sposób, który może okazać się nieoczekiwany. Jest to podstawowy kompromis między wydajnością, wyrazistością i bezpieczeństwem, który został wprowadzony w języku F# 4.5.

## <a name="revamped-byrefs"></a>Przebudowane byrefs

Przed F# 4.5 [Byrefs](../language-reference/byrefs.md) w F# były niebezpieczne i niezdrowe dla wielu aplikacji. Problemy z dźwiękiem wokół byrefs zostały rozwiązane w F# 4.5 i tej samej analizy statycznej wykonane dla rozpiętości i byref-jak structs został również zastosowany.

### <a name="inreft-and-outreft"></a>inref<'t> i outref<'t>

Aby reprezentować pojęcie tylko do odczytu, tylko do zapisu i odczytu/zapisu `inref<'T>` `outref<'T>` wskaźnik zarządzany, F# 4.5 wprowadza , typy do reprezentowania tylko do odczytu i tylko do zapisu wskaźniki, odpowiednio. Każdy z nich ma inną semantykę. Na przykład nie można `inref<'T>`napisać do :

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Domyślnie wnioskowanie o typie wywnioskuje zarządzane wskaźniki, które `inref<'T>` są zgodne z niezmiennym charakterem kodu F#, chyba że coś zostało już zadeklarowane jako zmienne. Aby coś zapisywalnego, należy zadeklarować typ, `mutable` jak przed przekazaniem jego adres do funkcji lub elementu członkowskiego, który manipuluje nim. Aby dowiedzieć się więcej, zobacz [Byrefs](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>Struktury tylko do odczytu

Począwszy od F# 4.5, można adnotować strukturę jako <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> takie:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

To uniemożliwia deklarowanie elementu członkowskiego zmiennego w strukturze i emituje metadane, które umożliwia F# i C# traktować go jako tylko do odczytu, gdy używane z zestawu. Aby dowiedzieć się więcej, zobacz [Struktury tylko do odczytu](../language-reference/structures.md#readonly-structs).

## <a name="void-pointers"></a>Nieważne wskaźniki

Typ `voidptr` jest dodawany do Języka F# 4.5, podobnie jak następujące funkcje:

* `NativePtr.ofVoidPtr`, aby przekonwertować wskaźnik void na macierzysty wskaźnik int
* `NativePtr.toVoidPtr`, aby przekonwertować macierzysty wskaźnik int na wskaźnik void

Jest to przydatne podczas współdziałania z natywnym składnikiem, który używa wskaźników void.

## <a name="the-match-keyword"></a>Słowo kluczowe `match!`

Słowo `match!` kluczowe zwiększa dopasowanie wzorca, gdy wewnątrz wyrażenia obliczeniowego:

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

Dzięki temu można skrócić kod, który często obejmuje opcje mieszania (lub innych typów) z wyrażeniami obliczeniowymi, takimi jak async. Aby dowiedzieć się więcej, zobacz [mecz!](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Uproszczone wymagania dotyczące rzutowania w wyrażeniach tablicowych, listowych i sekwencji

Mieszanie typów, gdzie można dziedziczyć z innego wewnątrz tablicy, listy i sekwencji wyrażeń `:>` `upcast`tradycyjnie wymagane do upcast dowolnego typu pochodnego do jego typu nadrzędnego z lub . Jest to teraz zrelaksowany, wykazano w następujący sposób:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Wcięcie relaksacyjne dla wyrażeń tablicy i listy

Przed F# 4.5, trzeba nadmiernie wcięcia tablicy i listy wyrażeń po przekazaniu jako argumenty do wywołania metody. Nie jest to już wymagane:

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
