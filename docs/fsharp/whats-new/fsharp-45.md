---
title: Co nowego w F# 4,5 — F# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w F# 4,5.
ms.date: 11/27/2019
ms.openlocfilehash: 780b33a564432aae5ec99c70ff8620988b553fd1
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644111"
---
# <a name="whats-new-in-f-45"></a>Co nowego w F# 4,5

F#4,5 dodaje wiele ulepszeń do F# języka. Wiele z tych funkcji zostało jednocześnie dodanych, aby umożliwić pisanie wydajnego kodu F# w programie, zapewniając jednocześnie bezpieczny kod. To oznacza dodanie kilku koncepcji do języka i znacznej ilości analizy kompilatora podczas korzystania z tych konstrukcji.

## <a name="get-started"></a>Wprowadzenie

F#4,5 jest dostępny we wszystkich dystrybucjach .NET Core i narzędziach programu Visual Studio. [Zacznij korzystać z F# ](../get-started/index.md) programu, aby dowiedzieć się więcej.

## <a name="span-and-byref-like-structs"></a>Struktury zakresów i ByRef

Typ <xref:System.Span%601> wprowadzony w środowisku .NET Core umożliwia reprezentowanie buforów w pamięci w sposób silnie wpisany, który jest teraz dozwolony w F# czasie od F# 4,5. W poniższym przykładzie pokazano, jak można używać funkcji działających na <xref:System.Span%601> z różnymi reprezentacjami buforów:

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

Ważnym aspektem tego jest to, że zakres i inne [struktury podobne do ByRef](../language-reference/structures.md#byreflike-structs) mają bardzo sztywną analizę statyczną wykonywaną przez kompilator, która ogranicza ich użycie w sposób nieoczekiwany. Jest to podstawowe kompromisy między wydajnością, wyrazistości i bezpieczeństwem wprowadzonym w F# 4,5.

## <a name="revamped-byrefs"></a>Odnowionych ByRef

Przed F# 4,5 wszystkie [ByRef](../language-reference/byrefs.md) w programie F# były niebezpieczne i niezdrowe w przypadku wielu aplikacji. Problemy z dźwiękiem dotyczące operacji ByRef zostały rozwiązane F# w 4,5 i została również zastosowana taka sama analiza statyczna dla struktury span i typu ByRef.

### <a name="inreft-and-outreft"></a>inref < > i outref < >

Aby przedstawić pojęcie wskaźnika zarządzanego tylko do odczytu, tylko do zapisu i odczytu/zapisu, F# 4,5 wprowadza `inref<'T>`, `outref<'T>` typy reprezentujące tylko tylko do odczytu i tylko do zapisu. Każdy z nich ma inną semantykę. Nie można na przykład zapisywać do `inref<'T>`:

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Domyślnie wnioskowanie o typie będzie ustalać zarządzane wskaźniki jako `inref<'T>`, aby były zgodne z niezmiennym charakterem F# kodu, chyba że element został już zadeklarowany jako modyfikowalny. Aby wprowadzić coś do zapisu, musisz zadeklarować typ jako `mutable` przed przekazaniem jego adresu do funkcji lub elementu członkowskiego, który manipulowanie nim. Aby dowiedzieć się więcej, zobacz [ByRef](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>Struktury tylko do odczytu

Począwszy od F# 4,5, można dodać adnotacje do struktury z <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> w taki sposób:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

Uniemożliwia to zadeklarowanie modyfikowalnego elementu członkowskiego w strukturze i emituje metadane, które umożliwiają F# i C# traktuje je jako ReadOnly, gdy są używane z zestawu. Aby dowiedzieć się więcej, zobacz [struktury tylko do odczytu](../language-reference/structures.md#readonly-structs)

## <a name="void-pointers"></a>Wskaźniki typu void

Typ `voidptr` zostanie dodany do F# 4,5, ponieważ są to następujące funkcje:

* `NativePtr.ofVoidPtr` skonwertować wskaźnik void na natywny wskaźnik int
* `NativePtr.toVoidPtr` skonwertować natywny wskaźnik int na wskaźnik typu void

Jest to przydatne w przypadku współdziałania ze składnikiem natywnym, który używa wskaźników typu void.

## <a name="the-match-keyword"></a>Słowo kluczowe `match!`

Słowo kluczowe `match!` podnosi dopasowanie do wzorca, gdy wewnątrz wyrażenia obliczeń:

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

Pozwala to skrócić kod, który często obejmuje Opcje mieszania (lub inne typy) z wyrażeniami obliczeń, takimi jak Async. Aby dowiedzieć się więcej, zobacz [Match!](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Wymagania dotyczące swobodnego rzutowania w wyrażeniach tablicowych, list i sekwencji

Mieszanie typów, gdy jedna z nich może dziedziczyć z innego wewnątrz wyrażenia Array, list i Sequence, tradycyjnie wymagało przerzutowania dowolnego typu pochodnego na typ nadrzędny z `:>` lub `upcast`. Jest to teraz swobodne:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Wyróżnianie wcięć dla wyrażeń tablicowych i listowych

Przed F# 4,5, należy nadmiernie wciąć wyrażenia tablicowe i listy, gdy są przekazane jako argumenty wywołań metod. Nie jest to już wymagane:

```fsharp
module NoExcessiveIndenting = 
    System.Console.WriteLine(format="{0}", arg = [| 
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
