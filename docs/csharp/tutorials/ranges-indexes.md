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
# <a name="indices-and-ranges"></a>Indeksy i zakresy

Zakresy i indeksy zapewniają zwięzłą składnię do uzyskiwania dostępu do pojedynczych elementów lub zakresów w sekwencji.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:

> [!div class="checklist"]
>
> - Użyj składni dla zakresów w sekwencji.
> - Poznaj decyzje projektowe dotyczące początku i końca każdej sekwencji.
> - Poznaj scenariusze dla typów <xref:System.Index> i <xref:System.Range>.

## <a name="language-support-for-indices-and-ranges"></a>Obsługa języków w przypadku indeksów i zakresów

Ten język obsługuje dwa nowe typy i dwa nowe operatory:

- <xref:System.Index?displayProperty=nameWithType> reprezentuje indeks w sekwencji.
- Indeks z operatora końcowego `^`, który określa, że indeks jest względem końca sekwencji.
- <xref:System.Range?displayProperty=nameWithType> reprezentuje Podzakres sekwencji.
- Operator zakresu `..`, który określa początek i koniec zakresu jako jego operandy.

Zacznijmy od reguł dotyczących indeksów. Rozważ użycie tablicy `sequence`. Indeks `0` jest taki sam jak `sequence[0]`. Indeks `^0` jest taki sam jak `sequence[sequence.Length]`. Należy zauważyć, że `sequence[^0]` generuje wyjątek, tak jak `sequence[sequence.Length]`. Dla dowolnej liczby `n`indeks `^n` jest taka sama jak `sequence[sequence.Length - n]`.

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

Możesz pobrać ostatni wyraz z indeksem `^1`. Dodaj następujący kod poniżej inicjalizacji:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Zakres określa *początek* i *koniec* zakresu. Zakresy są na wyłączność, co oznacza, że *koniec* nie jest uwzględniony w zakresie. Zakres `[0..^0]` reprezentuje cały zakres, podobnie jak `[0..sequence.Length]` reprezentuje cały zakres. 

Poniższy kod tworzy Podzakres słowami "Quick", "brązowy" i "Fox". Zawiera `words[1]` do `words[3]`. Element `words[4]` nie należy do zakresu. Dodaj następujący kod do tej samej metody. Skopiuj i wklej go u dołu okna interaktywnego.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Poniższy kod tworzy Podzakres "z opóźnieniem" i "Dog". Zawiera `words[^2]` i `words[^1]`. `words[^0]` indeksu końcowego nie jest uwzględniony. Dodaj również następujący kod:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

W poniższych przykładach zostały utworzone zakresy, które są otwarte dla początku, końca lub obu:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Można również zadeklarować zakresy lub indeksy jako zmienne. Zmienna może być następnie używana wewnątrz `[` i `]` znaków:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Poniższy przykład pokazuje wiele przyczyn tego wyboru. Zmodyfikuj `x`, `y`i `z`, aby wypróbować różne kombinacje. Podczas eksperymentowania Użyj wartości, gdzie `x` jest mniejsza niż `y`, a `y` jest mniejsza niż `z` dla prawidłowych kombinacji. Dodaj następujący kod w nowej metodzie. Wypróbuj różne kombinacje:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Obsługa typów indeksów i zakresów

Indeksy i zakresy zapewniają jednoznaczne, zwięzłą składnię, aby uzyskać dostęp do pojedynczego elementu lub podzakresu elementów w sekwencji. Wyrażenie indeksu zwykle zwraca typ elementów sekwencji. Wyrażenie zakresu zwykle zwraca ten sam typ sekwencji co sekwencja źródłowa.

Jeśli typ zawiera [indeksator](../programming-guide/indexers/index.md) z parametrem <xref:System.Index> lub <xref:System.Range>, jawnie obsługuje odpowiednio indeksy lub zakresy. Gdy typ dostarcza indeksator, który przyjmuje jeden parametr <xref:System.Range>, może zwrócić inny typ sekwencji, taki jak <xref:System.Span%601?displayProperty=nameWithType>.

Typ jest możliwy do **zliczenia** , jeśli ma właściwość o nazwie `Length` lub `Count` z dostępną metodę pobierającą i typem zwracanym `int`. Typ z liczbą, która nie obsługuje jawnie indeksów lub zakresów może zapewnić niejawną obsługę. Aby uzyskać więcej informacji, zapoznaj się z sekcją obsługa niejawnych [indeksów](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) i [Obsługa niejawnego zakresu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) w artykule [propozycja funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md). Zakresy korzystające z obsługi niejawnego zakresu zwracają ten sam typ sekwencji co sekwencja źródłowa.

Na przykład następujące typy .NET obsługują zarówno indeksy, jak i zakresy: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>i <xref:System.ReadOnlySpan%601>. <xref:System.Collections.Generic.List%601> obsługuje indeksy, ale nie obsługuje zakresów.

## <a name="scenarios-for-indices-and-ranges"></a>Scenariusze dotyczące indeksów i zakresów

Często używasz zakresów i indeksów, gdy chcesz przeprowadzić analizę podzakresu całej sekwencji. Nowa składnia jest przejrzysta w celu dokładnego odczytywania informacji o tym, jaki jest zakres. Funkcja lokalna `MovingAverage` przyjmuje <xref:System.Range> jako argument. Następnie Metoda wylicza tylko ten zakres przy obliczaniu wartości minimalnej, maksymalnej i średniej. Wypróbuj następujący kod w projekcie:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Ukończony kod można pobrać z repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) .
