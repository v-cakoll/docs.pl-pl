---
title: typ znaku - odwołanie do języka C#
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a07cae6e607bb6cda965240c669c655207632298
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739066"
---
# <a name="char-c-reference"></a>char (odwołanie do języka C#)

Słowo `char` kluczowe typu jest aliasem <xref:System.Char?displayProperty=nameWithType> typu struktury .NET, który reprezentuje znak Unicode UTF-16.

|Typ|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 do U+FFFF|16 bitów|<xref:System.Char?displayProperty=nameWithType>|

Domyślną wartością `char` typu `\0`jest , czyli U + 0000.

Typ [ciągu](reference-types.md#the-string-type) reprezentuje tekst jako `char` sekwencję wartości.

## <a name="literals"></a>Literały

Można określić `char` wartość za pomocą:

- literał znakowy.
- sekwencji unicode ucieczki, `\u` po którym następuje cztery symbole szesnastkowe reprezentacji kodu znaku.
- szesnastkowej sekwencji `\x` ucieczki, po której następuje szesnastkowa reprezentacja kodu znaku.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Jak pokazano w poprzednim przykładzie, można również rzutować wartość `char` kodu znaku do odpowiedniej wartości.

> [!NOTE]
> W przypadku sekwencji unikowej Unicode należy określić wszystkie cztery cyfry szesnastkowe. Oznacza to, `\u006A` że jest prawidłową sekwencją ucieczki, podczas gdy `\u06A` i `\u6A` nie są prawidłowe.
>
> W przypadku szesnastkowej sekwencji ucieczki można pominąć zera wiodące. Oznacza to, `\x006A` `\x06A`że `\x6A` , i sekwencje ucieczki są prawidłowe i odpowiadają tej samej postaci.

## <a name="conversions"></a>Konwersje

Typ `char` jest niejawnie konwertowany na `int` `uint`następujące `long`typy `ulong` [integralne:](integral-numeric-types.md) `ushort`, , , i . Jest również niejawnie wymienialny na [wbudowane zmiennoprzecinkowe](floating-point-numeric-types.md) typy liczbowe: `float`, `double`, i `decimal`. Jest jawnie wymienialny `sbyte`na `byte`typy i `short` integralne.

Nie ma żadnych konwersji niejawnych `char` z innych typów do typu. Jednak każdy [integralny](integral-numeric-types.md) lub [zmiennoprzecinowy](floating-point-numeric-types.md) typ `char`liczbowy jest jawnie wymienialny na .

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz integralną [sekcję typów](~/_csharplang/spec/types.md#integral-types) [specyfikacji języka języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [Ciągi](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [Kodowanie znaków na platformie .NET](../../../standard/base-types/character-encoding-introduction.md)
