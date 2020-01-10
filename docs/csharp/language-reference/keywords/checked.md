---
title: Checked słowo kluczowe C# -odwołanie
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713707"
---
# <a name="checked-c-reference"></a>checked (odwołanie w C#)

Słowo kluczowe `checked` służy do jawnego włączania sprawdzania przepełnienia dla operacji arytmetycznych typu całkowitego i konwersji.

Domyślnie wyrażenie zawierające tylko stałe wartości powoduje błąd kompilatora, jeśli wyrażenie generuje wartość spoza zakresu typu docelowego. Jeśli wyrażenie zawiera jedną lub więcej wartości niestałych, kompilator nie wykrywa przepełnienia. Obliczenie wyrażenia przypisanego do `i2` w poniższym przykładzie nie powoduje błędu kompilatora.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Domyślnie te wyrażenia niestałe nie są sprawdzane w celu przepełnienia w czasie wykonywania i nie powodują wyjątków przepełnienia. W poprzednim przykładzie przedstawiono wartość-2 147 483 639 jako sumę dwóch dodatnich liczb całkowitych.

Sprawdzanie przepełnienia można włączyć przez opcje kompilatora, konfigurację środowiska lub użycie słowa kluczowego `checked`. W poniższych przykładach pokazano, jak używać wyrażenia `checked` lub bloku `checked` do wykrywania przepełnienia, który jest generowany przez poprzednią sumę w czasie wykonywania. Oba przykłady powodują wyjątek przepełnienia.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Niesprawdzone](./unchecked.md) słowo kluczowe może służyć do zapobiegania sprawdzaniu przepełnienia.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak używać `checked`, aby włączyć sprawdzanie przepełnienia w czasie wykonywania.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Checked i Unchecked](./checked-and-unchecked.md)
- [unchecked](./unchecked.md)
