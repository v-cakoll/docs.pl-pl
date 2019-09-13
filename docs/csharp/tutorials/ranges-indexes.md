---
title: Eksplorowanie zakresów danych przy użyciu indeksów i zakresów
description: Ten zaawansowany Samouczek uczy się, jak eksplorować dane przy użyciu indeksów i zakresów w celu zbadania wycinków sekwencyjnego zestawu danych.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 27f4b90f130345dd10517a5de78c759066afdf07
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926640"
---
# <a name="indices-and-ranges"></a>Indeksy i zakresy

Zakresy i indeksy zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w <xref:System.Array>, <xref:System.Span%601>, lub <xref:System.ReadOnlySpan%601>. Te funkcje umożliwiają bardziej zwięzłą, przejrzystą składnię w celu uzyskania dostępu do pojedynczych elementów lub zakresów elementów w sekwencji.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
>
> - Użyj składni dla zakresów w sekwencji.
> - Poznaj decyzje projektowe dotyczące początku i końca każdej sekwencji.
> - Poznaj scenariusze dla <xref:System.Index> typów i <xref:System.Range> .

## <a name="language-support-for-indices-and-ranges"></a>Obsługa języków w przypadku indeksów i zakresów

Ten język obsługuje dwa nowe typy i dwa nowe operatory.

- <xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.
- `^` Operator, który określa, że indeks jest względem końca sekwencji.
- <xref:System.Range?displayProperty=nameWithType>reprezentuje Podzakres sekwencji.
- Operator zakresu (`..`), który określa początek i koniec zakresu jako jego operandy.

Zacznijmy od reguł dotyczących indeksów. Weź pod uwagę `sequence`tablicę. Indeks jest taki sam jak `sequence[0]`. `0` Indeks jest taki sam jak `sequence[sequence.Length]`. `^0` Należy pamiętać `sequence[^0]` , że generuje wyjątek, podobnie jak `sequence[sequence.Length]` . Dla dowolnej liczby `n`indeks `^n` jest taki sam jak `sequence[sequence.Length - n]`.

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

Można pobrać ostatni wyraz z `^1` indeksem. Dodaj następujący kod poniżej inicjalizacji:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Zakres określa *początek* i *koniec* zakresu. Zakresy są na wyłączność, co oznacza, że *koniec* nie jest uwzględniony w zakresie. Zakres `[0..^0]` reprezentuje cały zakres, tak jak `[0..sequence.Length]` reprezentuje cały zakres. 

Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox". Zawiera `words[1]` .`words[3]` Element `words[4]` nie należy do zakresu. Dodaj następujący kod do tej samej metody. Skopiuj i wklej go u dołu okna interaktywnego.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog". Obejmuje `words[^2]` i .`words[^1]` Indeks `words[^0]` końcowy nie jest uwzględniony. Dodaj również następujący kod:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

W poniższych przykładach zostały utworzone zakresy, które są otwarte dla początku, końca lub obu:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Można również zadeklarować zakresy lub indeksy jako zmienne. Zmienna może być używana wewnątrz `[` znaków i: `]`

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Poniższy przykład pokazuje wiele przyczyn tego wyboru. Zmodyfikuj `x`, `y` i`z` , aby wypróbować różne kombinacje. Podczas eksperymentowania Użyj wartości, gdzie `x` jest mniejsza niż `y`i `y` jest mniejsze niż `z` w przypadku prawidłowych kombinacji. Dodaj następujący kod w nowej metodzie. Wypróbuj różne kombinacje:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Scenariusze dotyczące indeksów i zakresów

Często używasz zakresów i indeksów, gdy chcesz przeprowadzić analizę podzakresu całej sekwencji. Nowa składnia jest przejrzysta w celu dokładnego odczytywania informacji o tym, jaki jest zakres. Funkcja `MovingAverage` lokalna<xref:System.Range> przyjmuje jako argument. Następnie Metoda wylicza tylko ten zakres przy obliczaniu wartości minimalnej, maksymalnej i średniej. Wypróbuj następujący kod w projekcie:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Ukończony kod można pobrać z repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) .
