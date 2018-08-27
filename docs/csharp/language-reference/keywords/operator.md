---
title: Operator — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: c3bfada235993670bf158fe9803a09707b2b3251
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929875"
---
# <a name="operator-c-reference"></a>operator (odwołanie w C#)

Użyj `operator` — słowo kluczowe przeciążenia wbudowanym operatorem lub podać konwersja zdefiniowana przez użytkownika, w deklaracji klasy lub struktury.

## <a name="example"></a>Przykład

Poniżej znajduje się bardzo uproszczone klasę cyfry ułamkowe. Przeciąża `+` i `*` operatory przeprowadzić ułamkowe Dodawanie i mnożenie, a także operator konwersji na to, że konwertuje `Fraction` typ `double` typu.

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
