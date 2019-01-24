---
title: CHAR — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: b0aaf6c0b2f614fa5ff8611407cea567da1faafb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616318"
---
# <a name="char-c-reference"></a>char (odwołanie w C#)

`char` — Słowo kluczowe jest używane do deklarowania wystąpienie <xref:System.Char?displayProperty=nameWithType> strukturę, która używa .NET Framework, który reprezentuje znak Unicode. Wartość `Char` obiekt jest wartość liczbowa 16-bitowych (numer).

 Znaki Unicode są używane do reprezentowania większość języki pisane świata.

|Typ|Zakres|Rozmiar|Typ architektury .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 do U + FFFF|Znak 16-bitowych Unicode|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

Stałe `char` typu mogą być zapisywane jako literały znakowe, szesnastkowa sekwencja unikowa lub reprezentację Unicode. Można również rzutowania kody znaków typu całkowitego. W poniższym przykładzie czterech `char` zmienne są inicjowane za pomocą takiego samego znaku `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Konwersje

A `char` mogą być niejawnie konwertowane na [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długie](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md). Jednak nie istnieją żadne niejawne konwersje z innych typów `char` typu.

<xref:System.Char?displayProperty=nameWithType> Typu udostępnia kilka metod statycznych do pracy z `char` wartości.

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- <xref:System.Char>
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)
- [Ciągi](../../../csharp/programming-guide/strings/index.md)
