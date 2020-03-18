---
title: typ char - odwołanie do języka C#
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846525"
---
# <a name="char-c-reference"></a>char (odwołanie do języka C#)

Słowo `char` kluczowe type jest aliasem <xref:System.Char?displayProperty=nameWithType> dla typu struktury .NET, który reprezentuje znak Unicode UTF-16.

|Typ|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|Od U+0000 do U+FFFF|16 bitów|<xref:System.Char?displayProperty=nameWithType>|

Domyślną wartością `char` tego `\0`typu jest , czyli U +0000.

Typ [ciągu](reference-types.md#the-string-type) reprezentuje tekst jako `char` sekwencję wartości.

## <a name="literals"></a>Literały

Można określić `char` wartość z:

- literał postaci.
- sekwencji ucieczki Unicode, `\u` po której następuje czterosymboliczna szesnastkowa reprezentacja kodu znaku.
- sekwencji ucieczki szesnastkowej, po której następuje `\x` szesnastkowe przedstawienie kodu znaku.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Jak pokazano w poprzednim przykładzie, można również rzutować wartość `char` kodu znaku do odpowiedniej wartości.

> [!NOTE]
> W przypadku sekwencji ucieczki Unicode należy określić wszystkie cztery cyfry szesnastkowe. Oznacza to, że `\u006A` jest prawidłową sekwencją ucieczki, podczas gdy `\u06A` i `\u6A` nie są prawidłowe.
>
> W przypadku sekwencji ucieczki szesnastkowej można pominąć zera wiodące. Oznacza to, `\x006A` `\x06A`że `\x6A` sekwencje , i escape są prawidłowe i odpowiadają temu samemu znakowi.

## <a name="conversions"></a>Konwersje

Typ `char` jest niejawnie konwertowalny na następujące `int` `uint`typy `long` `ulong` [całki:](integral-numeric-types.md) `ushort`, , , i . Jest również niejawnie konwertowalny na wbudowane typy liczbowe `float` `double` `decimal` [zmiennoprzecinkowe:](floating-point-numeric-types.md) , , i . Jest jawnie konwertowalne `sbyte`do `byte`, `short` i typy integralne.

Nie ma żadnych niejawnych konwersji `char` z innych typów do typu. Jednak każdy [typ liczbowy typu integralnego](integral-numeric-types.md) lub [zmiennoprzecinkowego](floating-point-numeric-types.md) jest jawnie konwertowalny na `char`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [integralne typy](~/_csharplang/spec/types.md#integral-types) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [Ciągi](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
