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
# <a name="whats-new-in-f-45"></a><span data-ttu-id="d0fde-103">Co nowego w Języku F# 4.5</span><span class="sxs-lookup"><span data-stu-id="d0fde-103">What's new in F# 4.5</span></span>

<span data-ttu-id="d0fde-104">F# 4.5 dodaje wiele ulepszeń do języka F#.</span><span class="sxs-lookup"><span data-stu-id="d0fde-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="d0fde-105">Wiele z tych funkcji zostały dodane razem, aby umożliwić pisanie kodu efektywnego wydajności w języku F# przy jednoczesnym zapewnieniu, że ten kod jest bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="d0fde-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="d0fde-106">Oznacza to dodanie kilku pojęć do języka i znaczną ilość analizy kompilatora podczas korzystania z tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="d0fde-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="d0fde-107">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="d0fde-107">Get started</span></span>

<span data-ttu-id="d0fde-108">F# 4.5 jest dostępny we wszystkich dystrybucjach .NET Core i visual studio narzędzi.</span><span class="sxs-lookup"><span data-stu-id="d0fde-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="d0fde-109">[Zacznij korzystać z języka F#,](../get-started/index.md) aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="d0fde-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="d0fde-110">Struktury span i byref-jak</span><span class="sxs-lookup"><span data-stu-id="d0fde-110">Span and byref-like structs</span></span>

<span data-ttu-id="d0fde-111">Typ <xref:System.Span%601> wprowadzony w .NET Core umożliwia reprezentowanie buforów w pamięci w sposób silnie typizowany, który jest teraz dozwolony w języku F#, począwszy od języka F# 4.5.</span><span class="sxs-lookup"><span data-stu-id="d0fde-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="d0fde-112">W poniższym przykładzie pokazano, jak można ponownie <xref:System.Span%601> użyć funkcji działającej na różnych reprezentacjach buforu:</span><span class="sxs-lookup"><span data-stu-id="d0fde-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="d0fde-113">Ważnym aspektem jest to, że Span i inne [struktury byref-jak](../language-reference/structures.md#byreflike-structs) mają bardzo sztywną analizę statyczną wykonywaną przez kompilator, które ograniczają ich użycie w sposób, który może okazać się nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="d0fde-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="d0fde-114">Jest to podstawowy kompromis między wydajnością, wyrazistością i bezpieczeństwem, który został wprowadzony w języku F# 4.5.</span><span class="sxs-lookup"><span data-stu-id="d0fde-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="d0fde-115">Przebudowane byrefs</span><span class="sxs-lookup"><span data-stu-id="d0fde-115">Revamped byrefs</span></span>

<span data-ttu-id="d0fde-116">Przed F# 4.5 [Byrefs](../language-reference/byrefs.md) w F# były niebezpieczne i niezdrowe dla wielu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0fde-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="d0fde-117">Problemy z dźwiękiem wokół byrefs zostały rozwiązane w F# 4.5 i tej samej analizy statycznej wykonane dla rozpiętości i byref-jak structs został również zastosowany.</span><span class="sxs-lookup"><span data-stu-id="d0fde-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="d0fde-118">inref<'t> i outref<'t></span><span class="sxs-lookup"><span data-stu-id="d0fde-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="d0fde-119">Aby reprezentować pojęcie tylko do odczytu, tylko do zapisu i odczytu/zapisu `inref<'T>` `outref<'T>` wskaźnik zarządzany, F# 4.5 wprowadza , typy do reprezentowania tylko do odczytu i tylko do zapisu wskaźniki, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="d0fde-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="d0fde-120">Każdy z nich ma inną semantykę.</span><span class="sxs-lookup"><span data-stu-id="d0fde-120">Each have different semantics.</span></span> <span data-ttu-id="d0fde-121">Na przykład nie można `inref<'T>`napisać do :</span><span class="sxs-lookup"><span data-stu-id="d0fde-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="d0fde-122">Domyślnie wnioskowanie o typie wywnioskuje zarządzane wskaźniki, które `inref<'T>` są zgodne z niezmiennym charakterem kodu F#, chyba że coś zostało już zadeklarowane jako zmienne.</span><span class="sxs-lookup"><span data-stu-id="d0fde-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="d0fde-123">Aby coś zapisywalnego, należy zadeklarować typ, `mutable` jak przed przekazaniem jego adres do funkcji lub elementu członkowskiego, który manipuluje nim.</span><span class="sxs-lookup"><span data-stu-id="d0fde-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="d0fde-124">Aby dowiedzieć się więcej, zobacz [Byrefs](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="d0fde-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="d0fde-125">Struktury tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0fde-125">Readonly structs</span></span>

<span data-ttu-id="d0fde-126">Począwszy od F# 4.5, można adnotować strukturę jako <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> takie:</span><span class="sxs-lookup"><span data-stu-id="d0fde-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="d0fde-127">To uniemożliwia deklarowanie elementu członkowskiego zmiennego w strukturze i emituje metadane, które umożliwia F# i C# traktować go jako tylko do odczytu, gdy używane z zestawu.</span><span class="sxs-lookup"><span data-stu-id="d0fde-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="d0fde-128">Aby dowiedzieć się więcej, zobacz [Struktury tylko do odczytu](../language-reference/structures.md#readonly-structs).</span><span class="sxs-lookup"><span data-stu-id="d0fde-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="d0fde-129">Nieważne wskaźniki</span><span class="sxs-lookup"><span data-stu-id="d0fde-129">Void pointers</span></span>

<span data-ttu-id="d0fde-130">Typ `voidptr` jest dodawany do Języka F# 4.5, podobnie jak następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="d0fde-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="d0fde-131">`NativePtr.ofVoidPtr`, aby przekonwertować wskaźnik void na macierzysty wskaźnik int</span><span class="sxs-lookup"><span data-stu-id="d0fde-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="d0fde-132">`NativePtr.toVoidPtr`, aby przekonwertować macierzysty wskaźnik int na wskaźnik void</span><span class="sxs-lookup"><span data-stu-id="d0fde-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="d0fde-133">Jest to przydatne podczas współdziałania z natywnym składnikiem, który używa wskaźników void.</span><span class="sxs-lookup"><span data-stu-id="d0fde-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="d0fde-134">Słowo kluczowe `match!`</span><span class="sxs-lookup"><span data-stu-id="d0fde-134">The `match!` keyword</span></span>

<span data-ttu-id="d0fde-135">Słowo `match!` kluczowe zwiększa dopasowanie wzorca, gdy wewnątrz wyrażenia obliczeniowego:</span><span class="sxs-lookup"><span data-stu-id="d0fde-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="d0fde-136">Dzięki temu można skrócić kod, który często obejmuje opcje mieszania (lub innych typów) z wyrażeniami obliczeniowymi, takimi jak async.</span><span class="sxs-lookup"><span data-stu-id="d0fde-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="d0fde-137">Aby dowiedzieć się więcej, zobacz [mecz!](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="d0fde-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="d0fde-138">Uproszczone wymagania dotyczące rzutowania w wyrażeniach tablicowych, listowych i sekwencji</span><span class="sxs-lookup"><span data-stu-id="d0fde-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="d0fde-139">Mieszanie typów, gdzie można dziedziczyć z innego wewnątrz tablicy, listy i sekwencji wyrażeń `:>` `upcast`tradycyjnie wymagane do upcast dowolnego typu pochodnego do jego typu nadrzędnego z lub .</span><span class="sxs-lookup"><span data-stu-id="d0fde-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="d0fde-140">Jest to teraz zrelaksowany, wykazano w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d0fde-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="d0fde-141">Wcięcie relaksacyjne dla wyrażeń tablicy i listy</span><span class="sxs-lookup"><span data-stu-id="d0fde-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="d0fde-142">Przed F# 4.5, trzeba nadmiernie wcięcia tablicy i listy wyrażeń po przekazaniu jako argumenty do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="d0fde-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="d0fde-143">Nie jest to już wymagane:</span><span class="sxs-lookup"><span data-stu-id="d0fde-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
