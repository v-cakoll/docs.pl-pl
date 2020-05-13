---
title: Typ char — odwołanie w C#
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: f771626e9777deab30e798559d847615d6124e6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205776"
---
# <a name="char-c-reference"></a>char (odwołanie w C#)

`char`Słowo kluczowe type jest aliasem dla <xref:System.Char?displayProperty=nameWithType> typu struktury .NET, który reprezentuje znak Unicode UTF-16.

|Typ|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 do U + FFFF|16 bitów|<xref:System.Char?displayProperty=nameWithType>|

Wartość domyślna `char` typu to `\0` , czyli U + 0000.

`char`Typ obsługuje operatory [porównania](../operators/comparison-operators.md), [równości](../operators/equality-operators.md), [zwiększania](../operators/arithmetic-operators.md#increment-operator-)i [zmniejszania](../operators/arithmetic-operators.md#decrement-operator---) . Ponadto w przypadku `char` operandów, [arytmetyczne](../operators/arithmetic-operators.md) i [bitowe operatory logiczne](../operators/bitwise-and-shift-operators.md) wykonują operacje na odpowiednich kodach znaków i tworzą wynik `int` typu.

Typ [ciągu](reference-types.md#the-string-type) reprezentuje tekst jako sekwencję `char` wartości.

## <a name="literals"></a>Literały

Możesz określić `char` wartość przy użyciu:

- literał znakowy.
- sekwencja unikowa Unicode, która `\u` następuje po czterech symbolach szesnastkowej reprezentacji kodu znaku.
- szesnastkowa sekwencja ucieczki, `\x` po której następuje reprezentacja szesnastkowa kodu znaku.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Jak pokazano w powyższym przykładzie, można także rzutować wartość kodu znaku na odpowiadającą `char` wartość.

> [!NOTE]
> W przypadku sekwencji unikowej Unicode należy określić wszystkie cztery cyfry szesnastkowe. Oznacza to, że `\u006A` jest prawidłową sekwencją ucieczki, `\u06A` a i `\u6A` są nieprawidłowe.
>
> W przypadku szesnastkowej sekwencji ucieczki można pominąć zera wiodące. Oznacza to, że `\x006A` `\x06A` `\x6A` sekwencje, i Escape są prawidłowe i odpowiadają temu samemu znakowi.

## <a name="conversions"></a>Konwersje

`char`Typ jest niejawnie konwertowany na następujące typy [całkowite](integral-numeric-types.md) : `ushort` ,, `int` , `uint` `long` i `ulong` . Jest on również niejawnie konwertowany na wbudowane typy liczbowe [zmiennoprzecinkowe](floating-point-numeric-types.md) : `float` , `double` , i `decimal` . Jest on jawnie konwertowany na `sbyte` `byte` typy, i `short` .

Nie istnieją niejawne konwersje z innych typów do `char` typu. Jednak każdy typ liczbowy [całkowitego](integral-numeric-types.md) lub [zmiennoprzecinkowego](floating-point-numeric-types.md) jest jawnie konwertowany na `char` .

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Typy całkowite](~/_csharplang/spec/types.md#integral-types) [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [Ciągi](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [Kodowanie znaków na platformie .NET](../../../standard/base-types/character-encoding-introduction.md)
