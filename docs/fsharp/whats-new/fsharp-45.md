---
title: 'Co nowego w języku F # 4,5 — Przewodnik po języku f #'
description: 'Zapoznaj się z omówieniem nowych funkcji dostępnych w języku F # 4,5.'
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202354"
---
# <a name="whats-new-in-f-45"></a>Co nowego w języku F # 4,5

F # 4,5 dodaje wiele udoskonaleń do języka F #. Wiele z tych funkcji zostało jednocześnie dodanych, aby umożliwić pisanie wydajnego kodu w języku F #, a także zapewnianie, że ten kod jest bezpieczny. To oznacza dodanie kilku koncepcji do języka i znacznej ilości analizy kompilatora podczas korzystania z tych konstrukcji.

## <a name="get-started"></a>Rozpoczęcie pracy

Język F # 4,5 jest dostępny we wszystkich dystrybucjach .NET Core i narzędziach programu Visual Studio. [Rozpocznij pracę z językiem F #](../get-started/index.md) , aby dowiedzieć się więcej.

## <a name="span-and-byref-like-structs"></a>Struktury zakresów i ByRef

<xref:System.Span%601>Typ wprowadzony w środowisku .NET Core umożliwia reprezentowanie buforów w pamięci w sposób silnie określony, który jest teraz dozwolony w języku f # począwszy od f # 4,5. Poniższy przykład pokazuje, jak można wykorzystać funkcję, która działa w przypadku <xref:System.Span%601> różnych reprezentacji buforów:

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

Ważnym aspektem tego jest to, że zakres i inne [struktury podobne do ByRef](../language-reference/structures.md#byreflike-structs) mają bardzo sztywną analizę statyczną wykonywaną przez kompilator, która ogranicza ich użycie w sposób nieoczekiwany. Jest to podstawowe kompromisy między wydajnością, wyrazistości i bezpieczeństwem wprowadzonym w F # 4,5.

## <a name="revamped-byrefs"></a>Odnowionych ByRef

Przed F # 4,5, [ByRef](../language-reference/byrefs.md) w f # były niebezpieczne i niezdrowe w przypadku wielu aplikacji. Problemy z dźwiękiem dotyczące operacji ByRef zostały rozwiązane w języku F # 4,5, a także zastosowano tę samą analizę statyczną dla struktur i struktury typu ByRef.

### <a name="inreft-and-outreft"></a>inref<> i outref<>

Aby reprezentować pojęcie wskaźnika zarządzanego tylko do odczytu, tylko do zapisu i odczytu/zapisu, F # 4,5 wprowadza `inref<'T>` , `outref<'T>` typy reprezentujące jedynie wskaźniki tylko do odczytu i tylko do zapisu. Każdy z nich ma inną semantykę. Na przykład nie można zapisać w `inref<'T>` :

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Domyślnie wnioskowanie o typie będzie zgłaszać zarządzane wskaźniki jako `inref<'T>` zgodne z niezmiennym charakterem kodu języka F #, chyba że coś zostało już zadeklarowane jako mutable. Aby wprowadzić coś do zapisu, musisz zadeklarować typ jako `mutable` przed przekazaniem jego adresu do funkcji lub elementu członkowskiego, który manipulowanie nim. Aby dowiedzieć się więcej, zobacz [ByRef](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>Struktury tylko do odczytu

Począwszy od F # 4,5, można dodać adnotację do struktury w <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> taki sposób, aby:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

Uniemożliwia to zadeklarowanie modyfikowalnego elementu członkowskiego w strukturze i emituje metadane, które umożliwiają użycie języka F # i języka C# do traktowania go jako ReadOnly, gdy jest używany z zestawu. Aby dowiedzieć się więcej, zobacz [struktury tylko do odczytu](../language-reference/structures.md#readonly-structs).

## <a name="void-pointers"></a>Wskaźniki typu void

`voidptr`Typ zostanie dodany do F # 4,5, ponieważ są to następujące funkcje:

* `NativePtr.ofVoidPtr`Aby skonwertować wskaźnik void na natywny wskaźnik int
* `NativePtr.toVoidPtr`Aby skonwertować natywny wskaźnik int na wskaźnik void

Jest to przydatne w przypadku współdziałania ze składnikiem natywnym, który używa wskaźników typu void.

## <a name="the-match-keyword"></a>Słowo kluczowe `match!`

`match!`Słowo kluczowe rozszerza dopasowanie do wzorca, gdy wewnątrz wyrażenia obliczeń:

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

Mieszanie typów, gdy jedna z nich może dziedziczyć z innego wewnątrz wyrażenia Array, list i Sequence, tradycyjnie wymagało przerzutowania dowolnego typu pochodnego na jego typ nadrzędny z `:>` lub `upcast` . Jest to teraz swobodne:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Wyróżnianie wcięć dla wyrażeń tablicowych i listowych

Przed F # 4,5, należy nadmiernie wcięcia tablic i wyrażeń list, gdy są przekazane jako argumenty wywołań metod. Nie jest to już wymagane:

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
