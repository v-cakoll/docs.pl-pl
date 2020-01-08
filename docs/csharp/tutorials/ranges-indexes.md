---
title: Eksplorowanie zakresów danych przy użyciu indeksów i zakresów
description: Ten zaawansowany Samouczek uczy się, jak eksplorować dane przy użyciu indeksów i zakresów w celu zbadania wycinków sekwencyjnego zestawu danych.
ms.date: 09/20/2019
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 3d4c022ff8d6e7f260632e34d6f28277014c85c8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345631"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="a6255-103">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="a6255-103">Indices and ranges</span></span>

<span data-ttu-id="a6255-104">Zakresy i indeksy zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="a6255-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a6255-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="a6255-106">Użyj składni dla zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="a6255-107">Poznaj decyzje projektowe dotyczące początku i końca każdej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="a6255-108">Poznaj scenariusze dla typów <xref:System.Index> i <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="a6255-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="a6255-109">Obsługa języków w przypadku indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="a6255-109">Language support for indices and ranges</span></span>

<span data-ttu-id="a6255-110">Ten język obsługuje dwa nowe typy i dwa nowe operatory:</span><span class="sxs-lookup"><span data-stu-id="a6255-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="a6255-111"><xref:System.Index?displayProperty=nameWithType> reprezentuje indeks w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="a6255-112">Indeks z operatora końcowego `^`, który określa, że indeks jest względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="a6255-113"><xref:System.Range?displayProperty=nameWithType> reprezentuje Podzakres sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="a6255-114">Operator zakresu `..`, który określa początek i koniec zakresu jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="a6255-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="a6255-115">Zacznijmy od reguł dotyczących indeksów.</span><span class="sxs-lookup"><span data-stu-id="a6255-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="a6255-116">Rozważ użycie tablicy `sequence`.</span><span class="sxs-lookup"><span data-stu-id="a6255-116">Consider an array `sequence`.</span></span> <span data-ttu-id="a6255-117">Indeks `0` jest taki sam jak `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="a6255-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="a6255-118">Indeks `^0` jest taki sam jak `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="a6255-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="a6255-119">Należy zauważyć, że `sequence[^0]` generuje wyjątek, tak jak `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="a6255-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="a6255-120">Dla dowolnej liczby `n`indeks `^n` jest taka sama jak `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="a6255-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="a6255-121">Możesz pobrać ostatni wyraz z indeksem `^1`.</span><span class="sxs-lookup"><span data-stu-id="a6255-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="a6255-122">Dodaj następujący kod poniżej inicjalizacji:</span><span class="sxs-lookup"><span data-stu-id="a6255-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="a6255-123">Zakres określa *początek* i *koniec* zakresu.</span><span class="sxs-lookup"><span data-stu-id="a6255-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="a6255-124">Zakresy są na wyłączność, co oznacza, że *koniec* nie jest uwzględniony w zakresie.</span><span class="sxs-lookup"><span data-stu-id="a6255-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="a6255-125">Zakres `[0..^0]` reprezentuje cały zakres, podobnie jak `[0..sequence.Length]` reprezentuje cały zakres.</span><span class="sxs-lookup"><span data-stu-id="a6255-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="a6255-126">Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox".</span><span class="sxs-lookup"><span data-stu-id="a6255-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="a6255-127">Zawiera `words[1]` do `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="a6255-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="a6255-128">Element `words[4]` nie należy do zakresu.</span><span class="sxs-lookup"><span data-stu-id="a6255-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="a6255-129">Dodaj następujący kod do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="a6255-129">Add the following code to the same method.</span></span> <span data-ttu-id="a6255-130">Skopiuj i wklej go u dołu okna interaktywnego.</span><span class="sxs-lookup"><span data-stu-id="a6255-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="a6255-131">Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog".</span><span class="sxs-lookup"><span data-stu-id="a6255-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="a6255-132">Zawiera `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="a6255-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="a6255-133">`words[^0]` indeksu końcowego nie jest uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="a6255-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="a6255-134">Dodaj również następujący kod:</span><span class="sxs-lookup"><span data-stu-id="a6255-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="a6255-135">W poniższych przykładach zostały utworzone zakresy, które są otwarte dla początku, końca lub obu:</span><span class="sxs-lookup"><span data-stu-id="a6255-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="a6255-136">Można również zadeklarować zakresy lub indeksy jako zmienne.</span><span class="sxs-lookup"><span data-stu-id="a6255-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="a6255-137">Zmienna może być następnie używana wewnątrz `[` i `]` znaków:</span><span class="sxs-lookup"><span data-stu-id="a6255-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="a6255-138">Poniższy przykład pokazuje wiele przyczyn tego wyboru.</span><span class="sxs-lookup"><span data-stu-id="a6255-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="a6255-139">Zmodyfikuj `x`, `y`i `z`, aby wypróbować różne kombinacje.</span><span class="sxs-lookup"><span data-stu-id="a6255-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="a6255-140">Podczas eksperymentowania Użyj wartości, gdzie `x` jest mniejsza niż `y`, a `y` jest mniejsza niż `z` dla prawidłowych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="a6255-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="a6255-141">Dodaj następujący kod w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="a6255-141">Add the following code in a new method.</span></span> <span data-ttu-id="a6255-142">Wypróbuj różne kombinacje:</span><span class="sxs-lookup"><span data-stu-id="a6255-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="a6255-143">Obsługa typów indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="a6255-143">Type support for indices and ranges</span></span>

<span data-ttu-id="a6255-144">Indeksy i zakresy zapewniają jednoznaczne, zwięzłą składnię, aby uzyskać dostęp do pojedynczego elementu lub podzakresu elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-144">Indexes and ranges provide clear, concise syntax to access a single element or a sub-range of elements in a sequence.</span></span> <span data-ttu-id="a6255-145">Wyrażenie indeksu zwykle zwraca typ elementów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="a6255-146">Wyrażenie zakresu zwykle zwraca ten sam typ sekwencji co sekwencja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="a6255-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="a6255-147">Jeśli typ zawiera [indeksator](../programming-guide/indexers/index.md) z parametrem <xref:System.Index> lub <xref:System.Range>, jawnie obsługuje odpowiednio indeksy lub zakresy.</span><span class="sxs-lookup"><span data-stu-id="a6255-147">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="a6255-148">Gdy typ dostarcza indeksator, który przyjmuje jeden parametr <xref:System.Range>, może zwrócić inny typ sekwencji, taki jak <xref:System.Span%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6255-148">When the type provides an indexer that takes a single <xref:System.Range> parameter, it may choose to return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a6255-149">Typ jest możliwy do **zliczenia** , jeśli ma właściwość o nazwie `Length` lub `Count` z dostępną metodę pobierającą i typem zwracanym `int`.</span><span class="sxs-lookup"><span data-stu-id="a6255-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="a6255-150">Typ z liczbą, która nie obsługuje jawnie indeksów lub zakresów może zapewnić niejawną obsługę.</span><span class="sxs-lookup"><span data-stu-id="a6255-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="a6255-151">Aby uzyskać więcej informacji, zapoznaj się z sekcją obsługa niejawnych [indeksów](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) i [Obsługa niejawnego zakresu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) w artykule [propozycja funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="a6255-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="a6255-152">Zakresy korzystające z obsługi niejawnego zakresu zwracają ten sam typ sekwencji co sekwencja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="a6255-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="a6255-153">Na przykład następujące typy .NET obsługują zarówno indeksy, jak i zakresy: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>i <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="a6255-153">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="a6255-154"><xref:System.Collections.Generic.List%601> obsługuje indeksy, ale nie obsługuje zakresów.</span><span class="sxs-lookup"><span data-stu-id="a6255-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="a6255-155">Scenariusze dotyczące indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="a6255-155">Scenarios for indices and ranges</span></span>

<span data-ttu-id="a6255-156">Często używasz zakresów i indeksów, gdy chcesz przeprowadzić analizę podzakresu całej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6255-156">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="a6255-157">Nowa składnia jest przejrzysta w celu dokładnego odczytywania informacji o tym, jaki jest zakres.</span><span class="sxs-lookup"><span data-stu-id="a6255-157">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="a6255-158">Funkcja lokalna `MovingAverage` przyjmuje <xref:System.Range> jako argument.</span><span class="sxs-lookup"><span data-stu-id="a6255-158">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="a6255-159">Następnie Metoda wylicza tylko ten zakres przy obliczaniu wartości minimalnej, maksymalnej i średniej.</span><span class="sxs-lookup"><span data-stu-id="a6255-159">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="a6255-160">Wypróbuj następujący kod w projekcie:</span><span class="sxs-lookup"><span data-stu-id="a6255-160">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="a6255-161">Ukończony kod można pobrać z repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) .</span><span class="sxs-lookup"><span data-stu-id="a6255-161">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
