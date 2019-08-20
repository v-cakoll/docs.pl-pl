---
title: char — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 754c04bfc3b4090906420d55d55e51606b72f187
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605951"
---
# <a name="char-c-reference"></a>char (odwołanie w C#)

Słowo kluczowe jest używane do deklarowania instancji <xref:System.Char?displayProperty=nameWithType> struktury używanej przez .NET Framework do reprezentowania znaku Unicode. `char` Wartość `Char` obiektu jest 16-bitową wartością numeryczną (porządkową).

 Znaki Unicode służą do reprezentowania większości języków pisanych na całym świecie.

|Typ|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 do U + FFFF|16-bitowy znak Unicode|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

`char` Stałe typu można zapisać jako literały znakowe, szesnastkową sekwencję ucieczki lub reprezentację Unicode. Można również rzutować kody znaków całkowitych. W poniższym przykładzie są inicjowane cztery `char` zmienne z tym samym znakiem: `X`

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Konwersje

[](../builtin-types/floating-point-numeric-types.md) [](../builtin-types/integral-numeric-types.md) [](../builtin-types/integral-numeric-types.md) [](../builtin-types/floating-point-numeric-types.md) [](../builtin-types/integral-numeric-types.md)Może być niejawnie konwertowany na UShort, int, uint, Double lub Decimal. `char` Jednak nie istnieją niejawne konwersje z innych typów do `char` typu.

Typ zawiera kilka metod statycznych do pracy z `char` wartościami. <xref:System.Char?displayProperty=nameWithType>

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Typy całkowite](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- <xref:System.Char>
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Typy całkowite](../builtin-types/integral-numeric-types.md)
- [Tabela typów wbudowanych](./built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](./implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](./explicit-numeric-conversions-table.md)
- [Typy dopuszczające wartości null](../../programming-guide/nullable-types/index.md)
- [Ciągi](../../programming-guide/strings/index.md)
