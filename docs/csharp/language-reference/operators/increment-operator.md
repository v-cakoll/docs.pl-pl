---
title: ++ — Operator (odwołanie w C#)
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: b29f4f1ab00c0f8026f118cb72b090e3b728bfc5
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2018
ms.locfileid: "48030473"
---
# <a name="-operator-c-reference"></a>++ — Operator (odwołanie w C#)

Jednoargumentowy operator inkrementacji `++` zwiększa się argumentem operacji o 1. Jest obsługiwany w dwóch formach: przyrostkowego operatora inkrementacyjnego `x++`i operator inkrementacji prefiks `++x`.

## <a name="postfix-increment-operator"></a>Operator inkrementacji przyrostkowej

Wynik `x++` jest wartością `x` *przed* operacji, co ilustruje poniższy przykład:

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a>Operator inkrementacji przedrostka

Wynik `++x` jest wartością `x` *po* operacji, co ilustruje poniższy przykład:

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a>Uwagi

Operator inkrementacji jest wstępnie zdefiniowane dla wszystkich [typów całkowitych](../keywords/integral-types-table.md) (w tym [char](../keywords/char.md) typu), [typów zmiennoprzecinkowych](../keywords/floating-point-types-table.md)oraz wszelkie [wyliczenia](../keywords/enum.md) Typ.

Operand operatora inkrementacji musi być zmienną, [właściwość](../../programming-guide/classes-and-structs/properties.md) dostęp, lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) dostępu.

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `++` operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przyrostka inkrementacji i dekrementacji operatory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) i [przedrostkowe i operatory dekrementacji](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sekcje [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [--, operator](decrement-operator.md)
- [Porady: inkrementacja i dekrementacja wskaźników](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
