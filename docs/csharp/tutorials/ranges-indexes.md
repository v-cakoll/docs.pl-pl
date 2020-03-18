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
# <a name="indices-and-ranges"></a>Indeksy i zakresy

Zakresy i indeksy zapewniają zwięzłą składnię dostępu do pojedynczych elementów lub zakresów w sekwencji.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Użyj składni dla zakresów w sekwencji.
> - Zrozumienie decyzji projektowych dla początku i końca każdej sekwencji.
> - Poznaj scenariusze <xref:System.Index> dla <xref:System.Range> i typów.

## <a name="language-support-for-indices-and-ranges"></a>Obsługa językowa indeksów i zakresów

Ta obsługa języka opiera się na dwóch nowych typach i dwóch nowych operatorach:

- <xref:System.Index?displayProperty=nameWithType>reprezentuje indeks w sekwencji.
- Indeks od operatora `^`końcowego , który określa, że indeks jest względny do końca sekwencji.
- <xref:System.Range?displayProperty=nameWithType>reprezentuje podzakres sekwencji.
- Operator `..`zakresu , który określa początek i koniec zakresu jako jego operandy.

Zacznijmy od zasad indeksów. Należy wziąć `sequence`pod uwagę tablicę . Indeks `0` jest taki `sequence[0]`sam jak . Indeks `^0` jest taki `sequence[sequence.Length]`sam jak . Wyrażenie `sequence[^0]` zgłasza wyjątek, tak `sequence[sequence.Length]` jak to robi. Dla dowolnej `n`liczby `^n` indeks jest `sequence[sequence.Length - n]`taki sam jak .

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

Można pobrać ostatnie słowo `^1` z indeksem. Dodaj następujący kod poniżej inicjowania:

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Zakres określa *początek* i *koniec* zakresu. Zakresy są ekskluzywne, co oznacza, że *koniec* nie jest uwzględniony w zakresie. Zakres `[0..^0]` reprezentuje cały zakres, podobnie `[0..sequence.Length]` jak cały zakres.

Poniższy kod tworzy podzakres z napisem "szybkie", "brązowy" i "lis". Obejmuje `words[1]` ona poprzez `words[3]`. Element `words[4]` nie jest w zakresie. Dodaj następujący kod do tej samej metody. Skopiuj i wklej go u dołu interaktywnego okna.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Poniższy kod tworzy podzakres z "leniwy" i "pies". Obejmuje `words[^2]` i `words[^1]`. Indeks `words[^0]` końcowy nie jest uwzględniony. Dodaj również następujący kod:

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Poniższe przykłady tworzą zakresy, które są otwarte dla początku, końca lub obu:

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Można również zadeklarować zakresy lub indeksy jako zmienne. Zmienna może być następnie `[` `]` używana wewnątrz znaków i znaków:

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

W poniższym przykładzie przedstawiono wiele powodów tych wyborów. Zmodyfikuj `x`, `y`i `z` spróbuj różnych kombinacji. Podczas eksperymentowania należy `x` użyć wartości, `y` w których `z` jest mniejsza niż `y`, i jest mniejsza niż w przypadku prawidłowych kombinacji. Dodaj następujący kod w nowej metodzie. Wypróbuj różne kombinacje:

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Obsługa typów indeksów i zakresów

Indeksy i zakresy zapewniają jasne, zwięzłe składni, aby uzyskać dostęp do pojedynczego elementu lub podzakresu elementów w sekwencji. Wyrażenie indeksu zazwyczaj zwraca typ elementów sekwencji. Wyrażenie zakresu zazwyczaj zwraca ten sam typ sekwencji co sekwencja źródłowa.

Każdy typ, który zapewnia <xref:System.Index> [indeksatora](../programming-guide/indexers/index.md) z parametrem lub <xref:System.Range> jawnie obsługuje indeksy lub zakresy odpowiednio. Indeksator, który <xref:System.Range> przyjmuje pojedynczy parametr może zwrócić <xref:System.Span%601?displayProperty=nameWithType>inny typ sekwencji, takich jak .

Typ jest **policzalny,** jeśli `Length` ma `Count` właściwość o nazwie lub z `int`dostępnym getter emitują i typu zwracanego . Typ, który nie obsługuje jawnie indeksów lub zakresów, może zapewniać im niejawną obsługę. Aby uzyskać więcej informacji, zobacz [niejawne wsparcie indeksu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) i [niejawne zakres pomocy technicznej](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) w propozycji funkcji [notatki](~/_csharplang/proposals/csharp-8.0/ranges.md). Zakresy przy użyciu niejawnej obsługi zakresu zwracają ten sam typ sekwencji co sekwencja źródłowa.

Na przykład następujące typy .NET obsługują zarówno indeksy, <xref:System.Span%601>jak <xref:System.ReadOnlySpan%601>i zakresy: <xref:System.String>, , i . Obsługuje <xref:System.Collections.Generic.List%601> indeksy, ale nie obsługuje zakresów.

<xref:System.Array>ma bardziej zniuansowane zachowanie. Tablice o jednym wymiarze obsługują zarówno indeksy, jak i zakresy. Tablice wielowymiarowe nie. Indeksator tablicy wielowymiarowej ma wiele parametrów, a nie jeden parametr. Postrzępione tablice, nazywane również tablicą tablic, obsługują zarówno zakresy, jak i indeksatory. W poniższym przykładzie pokazano, jak iterować prostokątną podsekcję postrzępionej tablicy. Itewruje sekcję w środku, z wyłączeniem pierwszego i ostatniego trzech wierszy oraz pierwszej i dwóch ostatnich kolumn z każdego wybranego wiersza:

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a>Scenariusze dla indeksów i zakresów

Często będziesz używać zakresów i indeksów, gdy chcesz przeanalizować podzakres większej sekwencji. Nowa składnia jest jaśniejsza w czytaniu dokładnie, jaki podzakres jest zaangażowany. Funkcja `MovingAverage` lokalna <xref:System.Range> przyjmuje jako argument. Metoda następnie wylicza tylko ten zakres podczas obliczania min, max i średnia. Wypróbuj następujący kod w projekcie:

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
