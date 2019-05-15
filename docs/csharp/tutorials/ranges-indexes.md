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
# <a name="indices-and-ranges"></a>Indeksy i zakresy

Zakresy i indeksów, które zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w <xref:System.Array>, <xref:System.Span%601>, lub <xref:System.ReadOnlySpan%601>. Te funkcje umożliwiają bardziej zwięzły, wyczyść składni dostępu do pojedynczych elementów lub szeregu elementów w sekwencji.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> * Należy użyć składni dla zakresów w sekwencji.
> * Informacje o decyzji projektowych na początku i końcu każdego sekwencji.
> * Dowiedz się, scenariusze <xref:System.Index> i <xref:System.Range> typów.

## <a name="language-support-for-indices-and-ranges"></a>Obsługa języka dla indeksów i zakresy

Obsługa tego języka opiera się na dwóch nowych typów i dwóch nowych operatorów.
- <xref:System.Index?displayProperty=nameWithType> reprezentuje indeks do sekwencji.
- `^` Operatora, który określa, że indeks względem końca sekwencji.
- <xref:System.Range?displayProperty=nameWithType> reprezentuje zakres sub sekwencji.
- Operator zakresu (`..`), która określa początek i koniec zakresu jako argumentów.

Zacznijmy od reguł dla indeksów. Należy wziąć pod uwagę tablicy `sequence`. `0` Indeksu jest taka sama jak `sequence[0]`. `^0` Indeksu jest taka sama jak `sequence[sequence.Length]`. Należy pamiętać, że `sequence[^0]` zgłosić wyjątek, podobnie jak `sequence[sequence.Length]` jest. Dowolną liczbą `n`, indeks `^n` jest taka sama jak `sequence[sequence.Length - n]`.

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

Możesz pobrać ostatni wyraz z `^1` indeksu. Dodaj następujący kod poniżej inicjowania:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Określa zakres *start* i *zakończenia* zakresu. Zakresy są wzajemnie, co oznacza *zakończenia* nie wchodzi w zakres. Zakres `[0..^0]` reprezentuje cały zakres, podobnie jak `[0..sequence.Length]` reprezentuje cały zakres. 

Poniższy kod tworzy Podzakres przy użyciu słowa "szybkie", "brown" i "fox". Zawiera on `words[1]` za pośrednictwem `words[3]`. Element `words[4]` nie znajduje się w zakresie. Dodaj następujący kod do tej samej metody. Skopiuj i wklej go w dolnej części okna interaktywnego.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Poniższy kod tworzy Podzakres "z opóźnieniem" i "dog". Zawiera on `words[^2]` i `words[^1]`. Indeks końcowy `words[^0]` nie jest uwzględniona. Dodaj następujący kod, a także:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Poniższe przykłady tworzą zakresy, które są otwarte zakończył się dla początkowego i końcowego:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Można również zadeklarować zakresów lub indeksów jako zmienne. Następnie można użyć zmiennej w środowisku w `[` i `]` znaków:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Poniższy przykład pokazuje wiele przyczyn tych wyborów. Modyfikowanie `x`, `y`, i `z` do wypróbowania różnych kombinacji. Podczas eksperymentowania, użyj wartości, w których `x` jest mniejsza niż `y`, i `y` jest mniejsza niż `z` dla ważnych kombinacji. Dodaj następujący kod w nowej metodzie. Wypróbuj różne kombinacje:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Scenariusze dotyczące indeksów i zakresy

Często użyjesz zakresów i indeksów, które umożliwia wykonywanie niektórych analiz Podzakres całą sekwencję. Nowa składnia jest bardziej zrozumiały w dokładnie Podzakres, jakie jest używany do odczytywania. Funkcja lokalna `MovingAverage` przyjmuje <xref:System.Range> jako argumentem. Metoda następnie wylicza tylko tego zakresu, podczas obliczania minimalna, maksymalna i średnia. Wypróbuj poniższy kod w projekcie:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Możesz pobrać kompletny kod z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repozytorium.
