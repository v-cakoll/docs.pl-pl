---
title: Zapoznaj się z zakresami danych przy użyciu indeksów i zakresy
description: W tym samouczku zaawansowane nauczy Cię do eksplorowania danych przy użyciu indeksów i zakresy do sprawdzenia wycinki sekwencyjne zestawu danych.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 118d3c9ccad98ec02195c2b5e26a2ca203990adf
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557185"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="f422f-103">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="f422f-103">Indices and ranges</span></span>

<span data-ttu-id="f422f-104">Zakresy i indeksów, które zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w <xref:System.Array>, <xref:System.Span%601>, lub <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="f422f-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="f422f-105">Te funkcje umożliwiają bardziej zwięzły, wyczyść składni dostępu do pojedynczych elementów lub szeregu elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f422f-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="f422f-106">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="f422f-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="f422f-107">Należy użyć składni dla zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f422f-107">Use the syntax for ranges in a sequence.</span></span>
> * <span data-ttu-id="f422f-108">Informacje o decyzji projektowych na początku i końcu każdego sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f422f-108">Understand the design decisions for the start and end of each sequence.</span></span>
> * <span data-ttu-id="f422f-109">Dowiedz się, scenariusze <xref:System.Index> i <xref:System.Range> typów.</span><span class="sxs-lookup"><span data-stu-id="f422f-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="f422f-110">Obsługa języka dla indeksów i zakresy</span><span class="sxs-lookup"><span data-stu-id="f422f-110">Language support for indices and ranges</span></span>

<span data-ttu-id="f422f-111">Obsługa tego języka opiera się na dwóch nowych typów i dwóch nowych operatorów.</span><span class="sxs-lookup"><span data-stu-id="f422f-111">This language support relies on two new types and two new operators.</span></span>
- <span data-ttu-id="f422f-112"><xref:System.Index?displayProperty=nameWithType> reprezentuje indeks do sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f422f-112"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="f422f-113">`^` Operatora, który określa, że indeks względem końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f422f-113">The `^` operator, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="f422f-114"><xref:System.Range?displayProperty=nameWithType> reprezentuje zakres sub sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f422f-114"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="f422f-115">Operator zakresu (`..`), która określa początek i koniec zakresu jako argumentów.</span><span class="sxs-lookup"><span data-stu-id="f422f-115">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="f422f-116">Zacznijmy od reguł dla indeksów.</span><span class="sxs-lookup"><span data-stu-id="f422f-116">Let's start with the rules for indices.</span></span> <span data-ttu-id="f422f-117">Należy wziąć pod uwagę tablicy `sequence`.</span><span class="sxs-lookup"><span data-stu-id="f422f-117">Consider an array `sequence`.</span></span> <span data-ttu-id="f422f-118">`0` Indeksu jest taka sama jak `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="f422f-118">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="f422f-119">`^0` Indeksu jest taka sama jak `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="f422f-119">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="f422f-120">Należy pamiętać, że `sequence[^0]` zgłosić wyjątek, podobnie jak `sequence[sequence.Length]` jest.</span><span class="sxs-lookup"><span data-stu-id="f422f-120">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="f422f-121">Dowolną liczbą `n`, indeks `^n` jest taka sama jak `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="f422f-121">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp-interactive
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

<span data-ttu-id="f422f-122">Możesz pobrać ostatni wyraz z `^1` indeksu.</span><span class="sxs-lookup"><span data-stu-id="f422f-122">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="f422f-123">Dodaj następujący kod poniżej inicjowania:</span><span class="sxs-lookup"><span data-stu-id="f422f-123">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="f422f-124">Określa zakres *start* i *zakończenia* zakresu.</span><span class="sxs-lookup"><span data-stu-id="f422f-124">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="f422f-125">Zakresy są wzajemnie, co oznacza *zakończenia* nie wchodzi w zakres.</span><span class="sxs-lookup"><span data-stu-id="f422f-125">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="f422f-126">Zakres `[0..^0]` reprezentuje cały zakres, podobnie jak `[0..sequence.Length]` reprezentuje cały zakres.</span><span class="sxs-lookup"><span data-stu-id="f422f-126">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="f422f-127">Poniższy kod tworzy Podzakres przy użyciu słowa "szybkie", "brown" i "fox".</span><span class="sxs-lookup"><span data-stu-id="f422f-127">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="f422f-128">Zawiera on `words[1]` za pośrednictwem `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="f422f-128">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="f422f-129">Element `words[4]` nie znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="f422f-129">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="f422f-130">Dodaj następujący kod do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="f422f-130">Add the following code to the same method.</span></span> <span data-ttu-id="f422f-131">Skopiuj i wklej go w dolnej części okna interaktywnego.</span><span class="sxs-lookup"><span data-stu-id="f422f-131">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="f422f-132">Poniższy kod tworzy Podzakres "z opóźnieniem" i "dog".</span><span class="sxs-lookup"><span data-stu-id="f422f-132">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="f422f-133">Zawiera on `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="f422f-133">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="f422f-134">Indeks końcowy `words[^0]` nie jest uwzględniona.</span><span class="sxs-lookup"><span data-stu-id="f422f-134">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="f422f-135">Dodaj następujący kod, a także:</span><span class="sxs-lookup"><span data-stu-id="f422f-135">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="f422f-136">Poniższe przykłady tworzą zakresy, które są otwarte zakończył się dla początkowego i końcowego:</span><span class="sxs-lookup"><span data-stu-id="f422f-136">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="f422f-137">Można również zadeklarować zakresów lub indeksów jako zmienne.</span><span class="sxs-lookup"><span data-stu-id="f422f-137">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="f422f-138">Następnie można użyć zmiennej w środowisku w `[` i `]` znaków:</span><span class="sxs-lookup"><span data-stu-id="f422f-138">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="f422f-139">Poniższy przykład pokazuje wiele przyczyn tych wyborów.</span><span class="sxs-lookup"><span data-stu-id="f422f-139">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="f422f-140">Modyfikowanie `x`, `y`, i `z` do wypróbowania różnych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="f422f-140">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="f422f-141">Podczas eksperymentowania, użyj wartości, w których `x` jest mniejsza niż `y`, i `y` jest mniejsza niż `z` dla ważnych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="f422f-141">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="f422f-142">Dodaj następujący kod w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="f422f-142">Add the following code in a new method.</span></span> <span data-ttu-id="f422f-143">Wypróbuj różne kombinacje:</span><span class="sxs-lookup"><span data-stu-id="f422f-143">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="f422f-144">Scenariusze dotyczące indeksów i zakresy</span><span class="sxs-lookup"><span data-stu-id="f422f-144">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="f422f-145">Często użyjesz zakresów i indeksów, które umożliwia wykonywanie niektórych analiz Podzakres całą sekwencję.</span><span class="sxs-lookup"><span data-stu-id="f422f-145">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="f422f-146">Nowa składnia jest bardziej zrozumiały w dokładnie Podzakres, jakie jest używany do odczytywania.</span><span class="sxs-lookup"><span data-stu-id="f422f-146">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="f422f-147">Funkcja lokalna `MovingAverage` przyjmuje <xref:System.Range> jako argumentem.</span><span class="sxs-lookup"><span data-stu-id="f422f-147">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="f422f-148">Metoda następnie wylicza tylko tego zakresu, podczas obliczania minimalna, maksymalna i średnia.</span><span class="sxs-lookup"><span data-stu-id="f422f-148">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="f422f-149">Wypróbuj poniższy kod w projekcie:</span><span class="sxs-lookup"><span data-stu-id="f422f-149">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="f422f-150">Możesz pobrać kompletny kod z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="f422f-150">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
