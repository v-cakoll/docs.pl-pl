---
title: typ znaku — C# odwołanie
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: ab49b8cbddac2569d6063a5f312105bef3033e84
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552302"
---
# <a name="char-c-reference"></a>char (C# odwołanie)

Słowo kluczowe typu `char` jest aliasem dla typu struktury <xref:System.Char?displayProperty=nameWithType> .NET, który reprezentuje znak Unicode UTF-16.

|Typ|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 do U + FFFF|16 bitów|<xref:System.Char?displayProperty=nameWithType>|

Wartość domyślna typu `char` to `\0`, to oznacza, U + 0000.

Typ [String](reference-types.md#the-string-type) reprezentuje tekst jako sekwencję wartości `char`.

## <a name="literals"></a>Literały

Możesz określić wartość `char` przy użyciu:

- literał znakowy.
- sekwencja unikowa Unicode, która jest `\u` po którym następuje dwusymbolowa reprezentacja kodu znaku w postaci szesnastkowej.
- szesnastkowa sekwencja ucieczki, która jest `\x` po której następuje reprezentacja szesnastkowa kodu znaku.

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

Jak pokazano w powyższym przykładzie, można także rzutować wartość kodu znaku na odpowiadającą wartość `char`.

> [!NOTE]
> W przypadku sekwencji unikowej Unicode należy określić wszystkie cztery cyfry szesnastkowe. Oznacza to, że `\u006A` jest prawidłową sekwencją ucieczki, podczas gdy `\u06A` i `\u6A` są nieprawidłowe.
>
> W przypadku szesnastkowej sekwencji ucieczki można pominąć zera wiodące. Oznacza to, że `\x006A`, `\x06A`i `\x6A` sekwencje ucieczki są prawidłowe i odpowiadają temu samemu znakowi.

## <a name="conversions"></a>Konwersje

Typ `char` jest niejawnie konwertowany na następujące typy [całkowite](integral-numeric-types.md) : `ushort`, `int`, `uint`, `long`i `ulong`. Jest on również niejawnie konwertowany na wbudowane typy liczbowe [zmiennoprzecinkowe](floating-point-numeric-types.md) : `float`, `double`i `decimal`. Jest on jawnie konwertowany na `sbyte`, `byte`i `short` typów całkowitych.

Brak niejawnych konwersji z innych typów na typ `char`. Jednak każdy typ liczbowy [całkowitego](integral-numeric-types.md) lub [zmiennoprzecinkowego](floating-point-numeric-types.md) jest jawnie konwertowany do `char`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Typy całkowite](~/_csharplang/spec/types.md#integral-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Tabela typów wbudowanych](../keywords/built-in-types-table.md)
- [Ciągi](../../programming-guide/strings/index.md)
