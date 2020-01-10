---
title: Co nowego w F# 4,5 — F# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji dostępnych w F# 4,5.
ms.date: 11/27/2019
ms.openlocfilehash: b699165125d345ad783b24da8a0a994cba72d4ba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715687"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="a5583-103">Co nowego w F# 4,5</span><span class="sxs-lookup"><span data-stu-id="a5583-103">What's new in F# 4.5</span></span>

<span data-ttu-id="a5583-104">F#4,5 dodaje wiele ulepszeń do F# języka.</span><span class="sxs-lookup"><span data-stu-id="a5583-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="a5583-105">Wiele z tych funkcji zostało jednocześnie dodanych, aby umożliwić pisanie wydajnego kodu F# w programie, zapewniając jednocześnie bezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="a5583-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="a5583-106">To oznacza dodanie kilku koncepcji do języka i znacznej ilości analizy kompilatora podczas korzystania z tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="a5583-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="a5583-107">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="a5583-107">Get started</span></span>

<span data-ttu-id="a5583-108">F#4,5 jest dostępny we wszystkich dystrybucjach .NET Core i narzędziach programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5583-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="a5583-109">[Zacznij korzystać z F# ](../get-started/index.md) programu, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="a5583-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="a5583-110">Struktury zakresów i ByRef</span><span class="sxs-lookup"><span data-stu-id="a5583-110">Span and byref-like structs</span></span>

<span data-ttu-id="a5583-111">Typ <xref:System.Span%601> wprowadzony w środowisku .NET Core umożliwia reprezentowanie buforów w pamięci w sposób silnie wpisany, który jest teraz dozwolony w F# czasie od F# 4,5.</span><span class="sxs-lookup"><span data-stu-id="a5583-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="a5583-112">W poniższym przykładzie pokazano, jak można używać funkcji działających na <xref:System.Span%601> z różnymi reprezentacjami buforów:</span><span class="sxs-lookup"><span data-stu-id="a5583-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="a5583-113">Ważnym aspektem tego jest to, że zakres i inne [struktury podobne do ByRef](../language-reference/structures.md#byreflike-structs) mają bardzo sztywną analizę statyczną wykonywaną przez kompilator, która ogranicza ich użycie w sposób nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="a5583-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="a5583-114">Jest to podstawowe kompromisy między wydajnością, wyrazistości i bezpieczeństwem wprowadzonym w F# 4,5.</span><span class="sxs-lookup"><span data-stu-id="a5583-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="a5583-115">Odnowionych ByRef</span><span class="sxs-lookup"><span data-stu-id="a5583-115">Revamped byrefs</span></span>

<span data-ttu-id="a5583-116">Przed F# 4,5 wszystkie [ByRef](../language-reference/byrefs.md) w programie F# były niebezpieczne i niezdrowe w przypadku wielu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5583-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="a5583-117">Problemy z dźwiękiem dotyczące operacji ByRef zostały rozwiązane F# w 4,5 i została również zastosowana taka sama analiza statyczna dla struktury span i typu ByRef.</span><span class="sxs-lookup"><span data-stu-id="a5583-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="a5583-118">inref < > i outref < ></span><span class="sxs-lookup"><span data-stu-id="a5583-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="a5583-119">Aby przedstawić pojęcie wskaźnika zarządzanego tylko do odczytu, tylko do zapisu i odczytu/zapisu, F# 4,5 wprowadza `inref<'T>`, `outref<'T>` typy reprezentujące tylko tylko do odczytu i tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="a5583-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="a5583-120">Każdy z nich ma inną semantykę.</span><span class="sxs-lookup"><span data-stu-id="a5583-120">Each have different semantics.</span></span> <span data-ttu-id="a5583-121">Nie można na przykład zapisywać do `inref<'T>`:</span><span class="sxs-lookup"><span data-stu-id="a5583-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="a5583-122">Domyślnie wnioskowanie o typie będzie ustalać zarządzane wskaźniki jako `inref<'T>`, aby były zgodne z niezmiennym charakterem F# kodu, chyba że element został już zadeklarowany jako modyfikowalny.</span><span class="sxs-lookup"><span data-stu-id="a5583-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="a5583-123">Aby wprowadzić coś do zapisu, musisz zadeklarować typ jako `mutable` przed przekazaniem jego adresu do funkcji lub elementu członkowskiego, który manipulowanie nim.</span><span class="sxs-lookup"><span data-stu-id="a5583-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="a5583-124">Aby dowiedzieć się więcej, zobacz [ByRef](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="a5583-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="a5583-125">Struktury tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a5583-125">Readonly structs</span></span>

<span data-ttu-id="a5583-126">Począwszy od F# 4,5, można dodać adnotacje do struktury z <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> w taki sposób:</span><span class="sxs-lookup"><span data-stu-id="a5583-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="a5583-127">Uniemożliwia to zadeklarowanie modyfikowalnego elementu członkowskiego w strukturze i emituje metadane, które umożliwiają F# i C# traktuje je jako ReadOnly, gdy są używane z zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5583-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="a5583-128">Aby dowiedzieć się więcej, zobacz [struktury tylko do odczytu](../language-reference/structures.md#readonly-structs).</span><span class="sxs-lookup"><span data-stu-id="a5583-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="a5583-129">Wskaźniki typu void</span><span class="sxs-lookup"><span data-stu-id="a5583-129">Void pointers</span></span>

<span data-ttu-id="a5583-130">Typ `voidptr` zostanie dodany do F# 4,5, ponieważ są to następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="a5583-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="a5583-131">`NativePtr.ofVoidPtr` skonwertować wskaźnik void na natywny wskaźnik int</span><span class="sxs-lookup"><span data-stu-id="a5583-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="a5583-132">`NativePtr.toVoidPtr` skonwertować natywny wskaźnik int na wskaźnik typu void</span><span class="sxs-lookup"><span data-stu-id="a5583-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="a5583-133">Jest to przydatne w przypadku współdziałania ze składnikiem natywnym, który używa wskaźników typu void.</span><span class="sxs-lookup"><span data-stu-id="a5583-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="a5583-134">Słowo kluczowe `match!`</span><span class="sxs-lookup"><span data-stu-id="a5583-134">The `match!` keyword</span></span>

<span data-ttu-id="a5583-135">Słowo kluczowe `match!` podnosi dopasowanie do wzorca, gdy wewnątrz wyrażenia obliczeń:</span><span class="sxs-lookup"><span data-stu-id="a5583-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="a5583-136">Pozwala to skrócić kod, który często obejmuje Opcje mieszania (lub inne typy) z wyrażeniami obliczeń, takimi jak Async.</span><span class="sxs-lookup"><span data-stu-id="a5583-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="a5583-137">Aby dowiedzieć się więcej, zobacz [Match!](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="a5583-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="a5583-138">Wymagania dotyczące swobodnego rzutowania w wyrażeniach tablicowych, list i sekwencji</span><span class="sxs-lookup"><span data-stu-id="a5583-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="a5583-139">Mieszanie typów, gdy jedna z nich może dziedziczyć z innego wewnątrz wyrażenia Array, list i Sequence, tradycyjnie wymagało przerzutowania dowolnego typu pochodnego na typ nadrzędny z `:>` lub `upcast`.</span><span class="sxs-lookup"><span data-stu-id="a5583-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="a5583-140">Jest to teraz swobodne:</span><span class="sxs-lookup"><span data-stu-id="a5583-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="a5583-141">Wyróżnianie wcięć dla wyrażeń tablicowych i listowych</span><span class="sxs-lookup"><span data-stu-id="a5583-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="a5583-142">Przed F# 4,5, należy nadmiernie wciąć wyrażenia tablicowe i listy, gdy są przekazane jako argumenty wywołań metod.</span><span class="sxs-lookup"><span data-stu-id="a5583-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="a5583-143">Nie jest to już wymagane:</span><span class="sxs-lookup"><span data-stu-id="a5583-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting = 
    System.Console.WriteLine(format="{0}", arg = [| 
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
