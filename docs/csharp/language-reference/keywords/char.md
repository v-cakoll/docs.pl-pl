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
ms.openlocfilehash: 63f8871926e8c279678c59a2256bef46b2ff514e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698772"
---
# <a name="char-c-reference"></a>char (odwołanie w C#)

Słowo kluczowe `char` służy do deklarowania instancji struktury <xref:System.Char?displayProperty=nameWithType> używanej przez .NET Framework do reprezentowania znaku Unicode. Wartość obiektu `Char` jest wartością 16-bitową liczbową (porządkową).

 Znaki Unicode służą do reprezentowania większości języków pisanych na całym świecie.

|Typ|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 do U + FFFF|16-bitowy znak Unicode|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

Stałe typu `char` można zapisać jako literały znakowe, szesnastkową sekwencję ucieczki lub reprezentację Unicode. Można również rzutować kody znaków całkowitych. W poniższym przykładzie cztery elementy tablicy `char` są inicjowane przy użyciu tego samego znaku `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Konwersje

@No__t-0 może być niejawnie konwertowany na [UShort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)lub [Decimal](../builtin-types/floating-point-numeric-types.md). Niejawne konwersje z innych typów nie są jednak typu `char`.

Typ <xref:System.Char?displayProperty=nameWithType> zawiera kilka metod statycznych do pracy z wartościami `char`.

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Typy całkowite](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- <xref:System.Char>
- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Typy całkowite](../builtin-types/integral-numeric-types.md)
- [Tabela typów wbudowanych](./built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](./implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](./explicit-numeric-conversions-table.md)
- [Ciągi](../../programming-guide/strings/index.md)
