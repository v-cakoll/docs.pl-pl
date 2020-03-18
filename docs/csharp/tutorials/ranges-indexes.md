---
title: Eksplorowanie zakresów danych przy użyciu indeksów i zakresów
description: Ten zaawansowany samouczek uczy eksplorowania danych przy użyciu indeksów i zakresów w celu zbadania fragmentów sekwencyjnego zestawu danych.
ms.date: 03/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 82aad968e2efc437c82a7c8250bcd108b60b09e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156497"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="6824e-103">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="6824e-103">Indices and ranges</span></span>

<span data-ttu-id="6824e-104">Zakresy i indeksy zapewniają zwięzłą składnię dostępu do pojedynczych elementów lub zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="6824e-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6824e-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="6824e-106">Użyj składni dla zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="6824e-107">Zrozumienie decyzji projektowych dla początku i końca każdej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="6824e-108">Poznaj scenariusze <xref:System.Index> dla <xref:System.Range> i typów.</span><span class="sxs-lookup"><span data-stu-id="6824e-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="6824e-109">Obsługa językowa indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="6824e-109">Language support for indices and ranges</span></span>

<span data-ttu-id="6824e-110">Ta obsługa języka opiera się na dwóch nowych typach i dwóch nowych operatorach:</span><span class="sxs-lookup"><span data-stu-id="6824e-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="6824e-111"><xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="6824e-112">Indeks od operatora `^`końcowego , który określa, że indeks jest względny do końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="6824e-113"><xref:System.Range?displayProperty=nameWithType>reprezentuje podzakres sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="6824e-114">Operator `..`zakresu , który określa początek i koniec zakresu jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="6824e-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="6824e-115">Zacznijmy od zasad indeksów.</span><span class="sxs-lookup"><span data-stu-id="6824e-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="6824e-116">Należy wziąć `sequence`pod uwagę tablicę .</span><span class="sxs-lookup"><span data-stu-id="6824e-116">Consider an array `sequence`.</span></span> <span data-ttu-id="6824e-117">Indeks `0` jest taki `sequence[0]`sam jak .</span><span class="sxs-lookup"><span data-stu-id="6824e-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="6824e-118">Indeks `^0` jest taki `sequence[sequence.Length]`sam jak .</span><span class="sxs-lookup"><span data-stu-id="6824e-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="6824e-119">Wyrażenie `sequence[^0]` zgłasza wyjątek, tak `sequence[sequence.Length]` jak to robi.</span><span class="sxs-lookup"><span data-stu-id="6824e-119">The expression `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="6824e-120">Dla dowolnej `n`liczby `^n` indeks jest `sequence[sequence.Length - n]`taki sam jak .</span><span class="sxs-lookup"><span data-stu-id="6824e-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="6824e-121">Można pobrać ostatnie słowo `^1` z indeksem.</span><span class="sxs-lookup"><span data-stu-id="6824e-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="6824e-122">Dodaj następujący kod poniżej inicjowania:</span><span class="sxs-lookup"><span data-stu-id="6824e-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="6824e-123">Zakres określa *początek* i *koniec* zakresu.</span><span class="sxs-lookup"><span data-stu-id="6824e-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="6824e-124">Zakresy są ekskluzywne, co oznacza, że *koniec* nie jest uwzględniony w zakresie.</span><span class="sxs-lookup"><span data-stu-id="6824e-124">Ranges are exclusive, meaning the *end* isn't included in the range.</span></span> <span data-ttu-id="6824e-125">Zakres `[0..^0]` reprezentuje cały zakres, podobnie `[0..sequence.Length]` jak cały zakres.</span><span class="sxs-lookup"><span data-stu-id="6824e-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="6824e-126">Poniższy kod tworzy podzakres z napisem "szybkie", "brązowy" i "lis".</span><span class="sxs-lookup"><span data-stu-id="6824e-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="6824e-127">Obejmuje `words[1]` ona poprzez `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="6824e-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="6824e-128">Element `words[4]` nie jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="6824e-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="6824e-129">Dodaj następujący kod do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="6824e-129">Add the following code to the same method.</span></span> <span data-ttu-id="6824e-130">Skopiuj i wklej go u dołu interaktywnego okna.</span><span class="sxs-lookup"><span data-stu-id="6824e-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="6824e-131">Poniższy kod tworzy podzakres z "leniwy" i "pies".</span><span class="sxs-lookup"><span data-stu-id="6824e-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="6824e-132">Obejmuje `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="6824e-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="6824e-133">Indeks `words[^0]` końcowy nie jest uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="6824e-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="6824e-134">Dodaj również następujący kod:</span><span class="sxs-lookup"><span data-stu-id="6824e-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="6824e-135">Poniższe przykłady tworzą zakresy, które są otwarte dla początku, końca lub obu:</span><span class="sxs-lookup"><span data-stu-id="6824e-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="6824e-136">Można również zadeklarować zakresy lub indeksy jako zmienne.</span><span class="sxs-lookup"><span data-stu-id="6824e-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="6824e-137">Zmienna może być następnie `[` `]` używana wewnątrz znaków i znaków:</span><span class="sxs-lookup"><span data-stu-id="6824e-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="6824e-138">W poniższym przykładzie przedstawiono wiele powodów tych wyborów.</span><span class="sxs-lookup"><span data-stu-id="6824e-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="6824e-139">Zmodyfikuj `x`, `y`i `z` spróbuj różnych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="6824e-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="6824e-140">Podczas eksperymentowania należy `x` użyć wartości, `y` w których `z` jest mniejsza niż `y`, i jest mniejsza niż w przypadku prawidłowych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="6824e-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="6824e-141">Dodaj następujący kod w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="6824e-141">Add the following code in a new method.</span></span> <span data-ttu-id="6824e-142">Wypróbuj różne kombinacje:</span><span class="sxs-lookup"><span data-stu-id="6824e-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="6824e-143">Obsługa typów indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="6824e-143">Type support for indices and ranges</span></span>

<span data-ttu-id="6824e-144">Indeksy i zakresy zapewniają jasne, zwięzłe składni, aby uzyskać dostęp do pojedynczego elementu lub podzakresu elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-144">Indexes and ranges provide clear, concise syntax to access a single element or a subrange of elements in a sequence.</span></span> <span data-ttu-id="6824e-145">Wyrażenie indeksu zazwyczaj zwraca typ elementów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="6824e-146">Wyrażenie zakresu zazwyczaj zwraca ten sam typ sekwencji co sekwencja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="6824e-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="6824e-147">Każdy typ, który zapewnia <xref:System.Index> [indeksatora](../programming-guide/indexers/index.md) z parametrem lub <xref:System.Range> jawnie obsługuje indeksy lub zakresy odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6824e-147">Any type that provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="6824e-148">Indeksator, który <xref:System.Range> przyjmuje pojedynczy parametr może zwrócić <xref:System.Span%601?displayProperty=nameWithType>inny typ sekwencji, takich jak .</span><span class="sxs-lookup"><span data-stu-id="6824e-148">An indexer that takes a single <xref:System.Range> parameter may return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6824e-149">Typ jest **policzalny,** jeśli `Length` ma `Count` właściwość o nazwie lub z `int`dostępnym getter emitują i typu zwracanego .</span><span class="sxs-lookup"><span data-stu-id="6824e-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="6824e-150">Typ, który nie obsługuje jawnie indeksów lub zakresów, może zapewniać im niejawną obsługę.</span><span class="sxs-lookup"><span data-stu-id="6824e-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="6824e-151">Aby uzyskać więcej informacji, zobacz [niejawne wsparcie indeksu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) i [niejawne zakres pomocy technicznej](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) w propozycji funkcji [notatki](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="6824e-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="6824e-152">Zakresy przy użyciu niejawnej obsługi zakresu zwracają ten sam typ sekwencji co sekwencja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="6824e-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="6824e-153">Na przykład następujące typy .NET obsługują zarówno indeksy, <xref:System.Span%601>jak <xref:System.ReadOnlySpan%601>i zakresy: <xref:System.String>, , i .</span><span class="sxs-lookup"><span data-stu-id="6824e-153">For example, the following .NET types support both indices and ranges: <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="6824e-154">Obsługuje <xref:System.Collections.Generic.List%601> indeksy, ale nie obsługuje zakresów.</span><span class="sxs-lookup"><span data-stu-id="6824e-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

<span data-ttu-id="6824e-155"><xref:System.Array>ma bardziej zniuansowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6824e-155"><xref:System.Array> has more nuanced behavior.</span></span> <span data-ttu-id="6824e-156">Tablice o jednym wymiarze obsługują zarówno indeksy, jak i zakresy.</span><span class="sxs-lookup"><span data-stu-id="6824e-156">Single dimension arrays support both indices and ranges.</span></span> <span data-ttu-id="6824e-157">Tablice wielowymiarowe nie.</span><span class="sxs-lookup"><span data-stu-id="6824e-157">Multi-dimensional arrays don't.</span></span> <span data-ttu-id="6824e-158">Indeksator tablicy wielowymiarowej ma wiele parametrów, a nie jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="6824e-158">The indexer for a multi-dimensional array has multiple parameters, not a single parameter.</span></span> <span data-ttu-id="6824e-159">Postrzępione tablice, nazywane również tablicą tablic, obsługują zarówno zakresy, jak i indeksatory.</span><span class="sxs-lookup"><span data-stu-id="6824e-159">Jagged arrays, also referred to as an array of arrays, support both ranges and indexers.</span></span> <span data-ttu-id="6824e-160">W poniższym przykładzie pokazano, jak iterować prostokątną podsekcję postrzępionej tablicy.</span><span class="sxs-lookup"><span data-stu-id="6824e-160">The following example shows how to iterate a rectangular subsection of a jagged array.</span></span> <span data-ttu-id="6824e-161">Itewruje sekcję w środku, z wyłączeniem pierwszego i ostatniego trzech wierszy oraz pierwszej i dwóch ostatnich kolumn z każdego wybranego wiersza:</span><span class="sxs-lookup"><span data-stu-id="6824e-161">It iterates the section in the center, excluding the first and last three rows, and the first and last two columns from each selected row:</span></span>

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="6824e-162">Scenariusze dla indeksów i zakresów</span><span class="sxs-lookup"><span data-stu-id="6824e-162">Scenarios for indices and ranges</span></span>

<span data-ttu-id="6824e-163">Często będziesz używać zakresów i indeksów, gdy chcesz przeanalizować podzakres większej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6824e-163">You'll often use ranges and indices when you want to analyze a subrange of a larger sequence.</span></span> <span data-ttu-id="6824e-164">Nowa składnia jest jaśniejsza w czytaniu dokładnie, jaki podzakres jest zaangażowany.</span><span class="sxs-lookup"><span data-stu-id="6824e-164">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="6824e-165">Funkcja `MovingAverage` lokalna <xref:System.Range> przyjmuje jako argument.</span><span class="sxs-lookup"><span data-stu-id="6824e-165">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="6824e-166">Metoda następnie wylicza tylko ten zakres podczas obliczania min, max i średnia.</span><span class="sxs-lookup"><span data-stu-id="6824e-166">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="6824e-167">Wypróbuj następujący kod w projekcie:</span><span class="sxs-lookup"><span data-stu-id="6824e-167">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
