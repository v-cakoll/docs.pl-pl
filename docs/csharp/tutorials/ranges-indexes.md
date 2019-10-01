---
title: Eksplorowanie zakresów danych przy użyciu indeksów i zakresów
description: Ten zaawansowany Samouczek uczy się, jak eksplorować dane przy użyciu indeksów i zakresów w celu zbadania wycinków sekwencyjnego zestawu danych.
ms.date: 09/20/2019
ms.custom: mvc
ms.openlocfilehash: 1be144560d2b20bafc66cd68de0735e6dc7f0124
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699938"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="75d52-103">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="75d52-103">Indices and ranges</span></span>

<span data-ttu-id="75d52-104">Zakresy i indeksy zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75d52-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="75d52-105">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="75d52-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="75d52-106">Użyj składni dla zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75d52-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="75d52-107">Poznaj decyzje projektowe dotyczące początku i końca każdej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75d52-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="75d52-108">Poznaj scenariusze dla typów <xref:System.Index> i <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="75d52-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="75d52-109">Obsługa języków w przypadku indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="75d52-109">Language support for indices and ranges</span></span>

<span data-ttu-id="75d52-110">Ten język obsługuje dwa nowe typy i dwa nowe operatory:</span><span class="sxs-lookup"><span data-stu-id="75d52-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="75d52-111"><xref:System.Index?displayProperty=nameWithType> reprezentuje indeks w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75d52-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="75d52-112">Indeks z operatora końcowego `^`, który określa, że indeks jest względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75d52-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="75d52-113"><xref:System.Range?displayProperty=nameWithType> reprezentuje Podzakres sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75d52-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="75d52-114">Operator zakresu `..`, który określa początek i koniec zakresu jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="75d52-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="75d52-115">Zacznijmy od reguł dotyczących indeksów.</span><span class="sxs-lookup"><span data-stu-id="75d52-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="75d52-116">Rozważ użycie tablicy `sequence`.</span><span class="sxs-lookup"><span data-stu-id="75d52-116">Consider an array `sequence`.</span></span> <span data-ttu-id="75d52-117">Indeks `0` jest taki sam jak `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="75d52-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="75d52-118">Indeks `^0` jest taki sam jak `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="75d52-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="75d52-119">Należy zauważyć, że `sequence[^0]` zgłasza wyjątek, podobnie jak `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="75d52-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="75d52-120">Dla dowolnej liczby `n` indeks `^n` jest taki sam jak `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="75d52-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp
string[] words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="75d52-121">Możesz pobrać ostatni wyraz z indeksem `^1`.</span><span class="sxs-lookup"><span data-stu-id="75d52-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="75d52-122">Dodaj następujący kod poniżej inicjalizacji:</span><span class="sxs-lookup"><span data-stu-id="75d52-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="75d52-123">Zakres określa *początek* i *koniec* zakresu.</span><span class="sxs-lookup"><span data-stu-id="75d52-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="75d52-124">Zakresy są na wyłączność, co oznacza, że *koniec* nie jest uwzględniony w zakresie.</span><span class="sxs-lookup"><span data-stu-id="75d52-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="75d52-125">Zakres `[0..^0]` reprezentuje cały zakres, podobnie jak `[0..sequence.Length]` reprezentuje cały zakres.</span><span class="sxs-lookup"><span data-stu-id="75d52-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="75d52-126">Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox".</span><span class="sxs-lookup"><span data-stu-id="75d52-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="75d52-127">Zawiera `words[1]` do `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="75d52-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="75d52-128">Element `words[4]` nie należy do zakresu.</span><span class="sxs-lookup"><span data-stu-id="75d52-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="75d52-129">Dodaj następujący kod do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="75d52-129">Add the following code to the same method.</span></span> <span data-ttu-id="75d52-130">Skopiuj i wklej go u dołu okna interaktywnego.</span><span class="sxs-lookup"><span data-stu-id="75d52-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="75d52-131">Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog".</span><span class="sxs-lookup"><span data-stu-id="75d52-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="75d52-132">Obejmuje `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="75d52-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="75d52-133">Indeks końcowy `words[^0]` nie jest uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="75d52-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="75d52-134">Dodaj również następujący kod:</span><span class="sxs-lookup"><span data-stu-id="75d52-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="75d52-135">W poniższych przykładach zostały utworzone zakresy, które są otwarte dla początku, końca lub obu:</span><span class="sxs-lookup"><span data-stu-id="75d52-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="75d52-136">Można również zadeklarować zakresy lub indeksy jako zmienne.</span><span class="sxs-lookup"><span data-stu-id="75d52-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="75d52-137">Zmienna może być używana wewnątrz znaków `[` i `]`:</span><span class="sxs-lookup"><span data-stu-id="75d52-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="75d52-138">Poniższy przykład pokazuje wiele przyczyn tego wyboru.</span><span class="sxs-lookup"><span data-stu-id="75d52-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="75d52-139">Zmodyfikuj `x`, `y` i `z`, aby wypróbować różne kombinacje.</span><span class="sxs-lookup"><span data-stu-id="75d52-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="75d52-140">Podczas eksperymentowania Użyj wartości, gdzie wartość `x` jest mniejsza niż `y`, a `y` jest mniejsza niż `z` dla prawidłowych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="75d52-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="75d52-141">Dodaj następujący kod w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="75d52-141">Add the following code in a new method.</span></span> <span data-ttu-id="75d52-142">Wypróbuj różne kombinacje:</span><span class="sxs-lookup"><span data-stu-id="75d52-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="75d52-143">Obsługa typów indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="75d52-143">Type support for indices and ranges</span></span>

<span data-ttu-id="75d52-144">Jeśli typ udostępnia [indeksator](../programming-guide/indexers/index.md) z parametrem <xref:System.Index> lub <xref:System.Range>, jawnie obsługuje odpowiednio indeksy lub zakresy.</span><span class="sxs-lookup"><span data-stu-id="75d52-144">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span>

<span data-ttu-id="75d52-145">Typ jest możliwy do **zliczenia** , jeśli ma właściwość o nazwie `Length` lub `Count` z dostępną metodę pobierającą i typem zwracanym `int`.</span><span class="sxs-lookup"><span data-stu-id="75d52-145">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="75d52-146">Typ z liczbą, która nie obsługuje jawnie indeksów lub zakresów może zapewnić niejawną obsługę.</span><span class="sxs-lookup"><span data-stu-id="75d52-146">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="75d52-147">Aby uzyskać więcej informacji, zapoznaj się z sekcją obsługa niejawnych [indeksów](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) i [Obsługa niejawnego zakresu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) w artykule [propozycja funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="75d52-147">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

<span data-ttu-id="75d52-148">Na przykład następujące typy .NET obsługują zarówno indeksy, jak i zakresy: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601> i <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="75d52-148">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="75d52-149">@No__t-0 obsługuje indeksy, ale nie obsługuje zakresów.</span><span class="sxs-lookup"><span data-stu-id="75d52-149">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="75d52-150">Scenariusze dotyczące indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="75d52-150">Scenarios for indices and ranges</span></span>

<span data-ttu-id="75d52-151">Często używasz zakresów i indeksów, gdy chcesz przeprowadzić analizę podzakresu całej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75d52-151">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="75d52-152">Nowa składnia jest przejrzysta w celu dokładnego odczytywania informacji o tym, jaki jest zakres.</span><span class="sxs-lookup"><span data-stu-id="75d52-152">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="75d52-153">Funkcja lokalna `MovingAverage` przyjmuje jako argument <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="75d52-153">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="75d52-154">Następnie Metoda wylicza tylko ten zakres przy obliczaniu wartości minimalnej, maksymalnej i średniej.</span><span class="sxs-lookup"><span data-stu-id="75d52-154">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="75d52-155">Wypróbuj następujący kod w projekcie:</span><span class="sxs-lookup"><span data-stu-id="75d52-155">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="75d52-156">Ukończony kod można pobrać z repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) .</span><span class="sxs-lookup"><span data-stu-id="75d52-156">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
