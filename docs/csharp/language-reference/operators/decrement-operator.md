---
title: Operator -- (odwołanie w C#)
ms.date: 11/26/2018
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 0858321d6fe192a55bc548f169c558542238a981
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153342"
---
# <a name="---operator-c-reference"></a>Operator -- (odwołanie w C#)

Jednoargumentowy operator dekrementacji `--` zmniejsza argumentem operacji o 1. Jest obsługiwany w dwóch formach: przyrostkowego operatora dekrementacyjnego `x--`i operator dekrementacji prefiksu, `--x`.

## <a name="postfix-decrement-operator"></a>Operator dekrementacji przyrostkowej

Wynik `x--` jest wartością `x` *przed* operacji, co ilustruje poniższy przykład:

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixDecrement)]

## <a name="prefix-decrement-operator"></a>Operator dekrementacji przedrostka

Wynik `--x` jest wartością `x` *po* operacji, co ilustruje poniższy przykład:

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixDecrement)]

## <a name="remarks"></a>Uwagi

Operator dekrementacji jest wstępnie zdefiniowane dla wszystkich [typów całkowitych](../keywords/integral-types-table.md) (w tym [char](../keywords/char.md) typu), [typów zmiennoprzecinkowych](../keywords/floating-point-types-table.md)oraz wszelkie [wyliczenia](../keywords/enum.md) Typ.

Argument operacji operatora dekrementacyjnego musi być zmienną, [właściwość](../../programming-guide/classes-and-structs/properties.md) dostęp, lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) dostępu.

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `--` operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przyrostka inkrementacji i dekrementacji operatory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) i [przedrostkowe i operatory dekrementacji](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sekcje [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [++, operator](increment-operator.md)
- [Porady: inkrementacja i dekrementacja wskaźników](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
