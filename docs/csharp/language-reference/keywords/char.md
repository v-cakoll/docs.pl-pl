---
title: char — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771800"
---
# <a name="char-c-reference"></a>char (C# odwołanie)

Słowo kluczowe typu `char` jest aliasem dla typu struktury <xref:System.Char?displayProperty=nameWithType> .NET, który reprezentuje znak Unicode UTF-16:

|Typ|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 do U + FFFF|16 bitów|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

Stałe typu `char` mogą być zapisywane jako literały znakowe, szesnastkowe sekwencje ucieczki lub reprezentację Unicode. Można również rzutować kod znaku całkowitego na odpowiadającą wartość `char`. W poniższym przykładzie cztery elementy tablicy `char` są inicjowane przy użyciu tego samego znaku `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Konwersje

Typ `char` jest niejawnie konwertowany na następujące typy [całkowite](../builtin-types/integral-numeric-types.md) : `ushort`, `int`, `uint`, `long` i `ulong`. Jest on również niejawnie konwertowany na wbudowane typy liczbowe [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) : `float`, `double` i `decimal`. Jest on jawnie konwertowany na `sbyte`, `byte` i `short` typów całkowitych.

Brak niejawnych konwersji z innych typów na typ `char`. Jednak każdy typ liczbowy [całkowitego](../builtin-types/integral-numeric-types.md) lub [zmiennoprzecinkowego](../builtin-types/floating-point-numeric-types.md) jest jawnie konwertowany do `char`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Typy całkowite](~/_csharplang/spec/types.md#integral-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Tabela typów wbudowanych](./built-in-types-table.md)
- [Ciągi](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
