---
title: Operator — słowo kluczowe (odwołanie w C#)
description: Dowiedz się, jak przeciążenia wbudowanym operatorem języka C#
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 1e11d7767b61becc39b1158fae9cb2abe997e4bd
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44134538"
---
# <a name="operator-c-reference"></a>operator (odwołanie w C#)

Użyj `operator` — słowo kluczowe przeciążenia wbudowanym operatorem lub podać konwersja zdefiniowana przez użytkownika, w deklaracji klasy lub struktury.

Aby przeciążyć operator na niestandardowej klasy lub struktury, musisz utworzyć Deklaracja operatora w odpowiedniego typu. Deklaracja operatora, który przeciążenia wbudowanym operatorem języka C# musi spełniać następujące reguły:

- Obejmuje zarówno `public` i `static` modyfikator.
- Zawiera on `operator X` gdzie `X` to nazwa lub symbol operatora jest przeciążony.
- Operatory jednoargumentowe mieć jeden parametr, a operatory dwuargumentowe mają dwa parametry. W każdym przypadku co najmniej jeden parametr musi być taki sam jak klasy lub struktury, która deklaruje operator.

Aby uzyskać informacje na temat definiowania operatorów konwersji, zobacz [jawne](explicit.md) i [niejawne](implicit.md) artykuły — słowo kluczowe.

Aby uzyskać omówienie, które mogą być przeciążone operatory języka C#, zobacz [operatory z możliwością przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md) artykułu.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano `Fraction` typ, który reprezentuje cyfry ułamkowe. Przeciąża `+` i `*` operatory przeprowadzić ułamkowe Dodawanie i mnożenie, a także operator konwersji na to, że konwertuje `Fraction` typ `double` typu.

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [Operatory z możliwością przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
