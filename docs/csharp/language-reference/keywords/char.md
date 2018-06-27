---
title: CHAR — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 4839cacfdc78abc45afc1c59652b944be4863877
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948371"
---
# <a name="char-c-reference"></a>char (odwołanie w C#)

`char` — Słowo kluczowe służy do deklarowania wystąpienia <xref:System.Char?displayProperty=nameWithType> struktury, który używa programu .NET Framework do reprezentowania znaku Unicode. Wartość `Char` obiektu jest wartością numeryczną 16-bitowych (numer).

 Znaki Unicode są używane do reprezentowania większość języków pisanych na świecie.

|Typ|Zakres|Rozmiar|Typ programu .NET Framework|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 do U + FFFF|Znak Unicode 16-bitowych|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

Stałe `char` typu mogą być zapisywane jako literały znaków, szesnastkowa sekwencja unikowa lub reprezentacja Unicode. Można również rzutować kody znaków wartości całkowitych. W poniższym przykładzie czterech `char` zmienne są inicjowane z tym samym `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Konwersje

A `char` można niejawnie przekonwertować [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md). Jednak nie istnieją żadne niejawne konwersje z innych typów do `char` typu.

<xref:System.Char?displayProperty=nameWithType> Typ zapewnia kilka metod statycznych do pracy z `char` wartości.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

<xref:System.Char>  
[Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
[Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
[Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
[Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)  
[Ciągi](../../../csharp/programming-guide/strings/index.md)