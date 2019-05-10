---
title: Zapoznaj się z zakresami danych przy użyciu indeksów i zakresy
description: W tym samouczku zaawansowane nauczy Cię do eksplorowania danych przy użyciu indeksów i zakresy do sprawdzenia wycinki sekwencyjne zestawu danych.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 64fae4581e265d4f70b8356d5c651b4fdaca3fe9
ms.sourcegitcommit: dd3b897feb5c4ac39732bb165848e37a344b0765
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2019
ms.locfileid: "64431489"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="c647a-103">Indeksy i zakresy</span><span class="sxs-lookup"><span data-stu-id="c647a-103">Indices and ranges</span></span>

<span data-ttu-id="c647a-104">Zakresy i indeksów, które zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w <xref:System.Array>, <xref:System.Span%601>, lub <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="c647a-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="c647a-105">Te funkcje umożliwiają bardziej zwięzły, wyczyść składni dostępu do pojedynczych elementów lub szeregu elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c647a-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="c647a-106">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="c647a-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="c647a-107">Należy użyć składni dla zakresów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c647a-107">Use the syntax for ranges in a sequence.</span></span>
> * <span data-ttu-id="c647a-108">Informacje o decyzji projektowych na początku i końcu każdego sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c647a-108">Understand the design decisions for the start and end of each sequence.</span></span>
> * <span data-ttu-id="c647a-109">Dowiedz się, scenariusze <xref:System.Index> i <xref:System.Range> typów.</span><span class="sxs-lookup"><span data-stu-id="c647a-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="c647a-110">Obsługa języka dla indeksów i zakresy</span><span class="sxs-lookup"><span data-stu-id="c647a-110">Language support for indices and ranges</span></span>

<span data-ttu-id="c647a-111">Można określić indeksu **od końca** przy użyciu `^` znak przed indeksu.</span><span class="sxs-lookup"><span data-stu-id="c647a-111">You can specify an index **from the end** using the `^` character before the index.</span></span> <span data-ttu-id="c647a-112">Indeksowanie od końca zaczyna się od reguły, `0..^0` określa cały zakres.</span><span class="sxs-lookup"><span data-stu-id="c647a-112">Indexing from the end starts from the rule that `0..^0` specifies the entire range.</span></span> <span data-ttu-id="c647a-113">Aby wyliczyć całej tablicy, należy uruchomić *na pierwszy element*i Kontynuuj, dopóki nie będziesz *elementem*.</span><span class="sxs-lookup"><span data-stu-id="c647a-113">To enumerate an entire array, you start *at the first element*, and continue until you are *past the last element*.</span></span> <span data-ttu-id="c647a-114">Reakcji zachowania `MoveNext` metody na moduł wyliczający: zwraca wartość false, gdy wyliczenie przekazuje po ostatnim elemencie.</span><span class="sxs-lookup"><span data-stu-id="c647a-114">Think of the behavior of the `MoveNext` method on an enumerator: it returns false when the enumeration passes the last element.</span></span> <span data-ttu-id="c647a-115">Indeks `^0` "koniec" oznacza, że `array[array.Length]`, lub indeks, który następuje po ostatnim elemencie.</span><span class="sxs-lookup"><span data-stu-id="c647a-115">The index `^0` means "the end", `array[array.Length]`, or the index that follows the last element.</span></span> <span data-ttu-id="c647a-116">Znasz `array[2]` oznacza element "2 od samego początku".</span><span class="sxs-lookup"><span data-stu-id="c647a-116">You are familiar with `array[2]` meaning the element "2 from the start".</span></span> <span data-ttu-id="c647a-117">Teraz `array[^2]` oznacza, że element "2 od końca".</span><span class="sxs-lookup"><span data-stu-id="c647a-117">Now, `array[^2]` means the element "2 from the end".</span></span> 

<span data-ttu-id="c647a-118">Można określić **zakres** z **operatora zakresu**: `..`.</span><span class="sxs-lookup"><span data-stu-id="c647a-118">You can specify a **range** with the **range operator**: `..`.</span></span> <span data-ttu-id="c647a-119">Na przykład `0..^0` określa cały zakres tablicy: 0 od początku do, z wyłączeniem 0 od końca.</span><span class="sxs-lookup"><span data-stu-id="c647a-119">For example, `0..^0` specifies the entire range of the array: 0 from the start up to, but not including 0 from the end.</span></span> <span data-ttu-id="c647a-120">Jeden z operandów może używać "start" lub "end".</span><span class="sxs-lookup"><span data-stu-id="c647a-120">Either operand may use "from the start" or "from the end".</span></span> <span data-ttu-id="c647a-121">Ponadto można pominąć oba operandy.</span><span class="sxs-lookup"><span data-stu-id="c647a-121">Furthermore, either operand may be omitted.</span></span> <span data-ttu-id="c647a-122">Wartości domyślne to `0` dla indeksu początkowego i `^0` dla indeksu zakończenia.</span><span class="sxs-lookup"><span data-stu-id="c647a-122">The defaults are `0` for the start index, and `^0` for the end index.</span></span>

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

<span data-ttu-id="c647a-123">Indeks każdego elementu wspiera koncepcję "od rozpoczęcia" i "od końca", a zakresy są nie do końca zakresu.</span><span class="sxs-lookup"><span data-stu-id="c647a-123">The index of each element reinforces the concept of "from the start", and "from the end", and that ranges are exclusive of the end of the range.</span></span> <span data-ttu-id="c647a-124">"Start" całej tablicy jest pierwszym elementem.</span><span class="sxs-lookup"><span data-stu-id="c647a-124">The "start" of the entire array is the first element.</span></span> <span data-ttu-id="c647a-125">"Koniec" całej tablicy jest *przeszłości* po ostatnim elemencie.</span><span class="sxs-lookup"><span data-stu-id="c647a-125">The "end" of the entire array is *past* the last element.</span></span>

<span data-ttu-id="c647a-126">Możesz pobrać ostatni wyraz z `^1` indeksu.</span><span class="sxs-lookup"><span data-stu-id="c647a-126">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="c647a-127">Dodaj następujący kod poniżej inicjowania:</span><span class="sxs-lookup"><span data-stu-id="c647a-127">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="c647a-128">Poniższy kod tworzy Podzakres przy użyciu słowa "szybkie", "brown" i "fox".</span><span class="sxs-lookup"><span data-stu-id="c647a-128">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="c647a-129">Zawiera on `words[1]` za pośrednictwem `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="c647a-129">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="c647a-130">Element `words[4]` nie znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="c647a-130">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="c647a-131">Dodaj następujący kod do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="c647a-131">Add the following code to the same method.</span></span> <span data-ttu-id="c647a-132">Skopiuj i wklej go w dolnej części okna interaktywnego.</span><span class="sxs-lookup"><span data-stu-id="c647a-132">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="c647a-133">Poniższy kod tworzy Podzakres "z opóźnieniem" i "dog".</span><span class="sxs-lookup"><span data-stu-id="c647a-133">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="c647a-134">Zawiera on `words[^2]` i `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="c647a-134">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="c647a-135">Indeks końcowy `words[^0]` nie jest uwzględniona.</span><span class="sxs-lookup"><span data-stu-id="c647a-135">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="c647a-136">Dodaj następujący kod, a także:</span><span class="sxs-lookup"><span data-stu-id="c647a-136">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="c647a-137">Poniższe przykłady tworzą zakresy, które są otwarte zakończył się dla początkowego i końcowego:</span><span class="sxs-lookup"><span data-stu-id="c647a-137">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="c647a-138">Można również zadeklarować zakresów lub indeksów jako zmienne.</span><span class="sxs-lookup"><span data-stu-id="c647a-138">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="c647a-139">Następnie można użyć zmiennej w środowisku w `[` i `]` znaków:</span><span class="sxs-lookup"><span data-stu-id="c647a-139">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="c647a-140">Dwóch decyzji projektowych, które wymagają uzyskać więcej informacji można znaleźć w poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="c647a-140">The previous examples show two design decisions that require more explanation:</span></span>

- <span data-ttu-id="c647a-141">Zakresy są *wyłączne*, co oznacza element w indeksie ostatniego nie znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="c647a-141">Ranges are *exclusive*, meaning the element at the last index isn't in the range.</span></span>
- <span data-ttu-id="c647a-142">Indeks `^0` jest *koniec* kolekcji, nie *po ostatnim elemencie* w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c647a-142">The index `^0` is *the end* of the collection, not *the last element* in the collection.</span></span>

<span data-ttu-id="c647a-143">Poniższy przykład pokazuje wiele przyczyn tych wyborów.</span><span class="sxs-lookup"><span data-stu-id="c647a-143">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="c647a-144">Modyfikowanie `x`, `y`, i `z` do wypróbowania różnych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="c647a-144">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="c647a-145">Podczas eksperymentowania, użyj wartości, w których `x` jest mniejsza niż `y`, i `y` jest mniejsza niż `z` dla ważnych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="c647a-145">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="c647a-146">Dodaj następujący kod w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="c647a-146">Add the following code in a new method.</span></span> <span data-ttu-id="c647a-147">Wypróbuj różne kombinacje:</span><span class="sxs-lookup"><span data-stu-id="c647a-147">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="c647a-148">Scenariusze dotyczące indeksów i zakresy</span><span class="sxs-lookup"><span data-stu-id="c647a-148">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="c647a-149">Często użyjesz zakresów i indeksów, które umożliwia wykonywanie niektórych analiz Podzakres całą sekwencję.</span><span class="sxs-lookup"><span data-stu-id="c647a-149">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="c647a-150">Nowa składnia jest bardziej zrozumiały w dokładnie Podzakres, jakie jest używany do odczytywania.</span><span class="sxs-lookup"><span data-stu-id="c647a-150">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="c647a-151">Funkcja lokalna `MovingAverage` przyjmuje <xref:System.Range> jako argumentem.</span><span class="sxs-lookup"><span data-stu-id="c647a-151">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="c647a-152">Metoda następnie wylicza tylko tego zakresu, podczas obliczania minimalna, maksymalna i średnia.</span><span class="sxs-lookup"><span data-stu-id="c647a-152">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="c647a-153">Wypróbuj poniższy kod w projekcie:</span><span class="sxs-lookup"><span data-stu-id="c647a-153">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="c647a-154">Możesz pobrać kompletny kod z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="c647a-154">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
