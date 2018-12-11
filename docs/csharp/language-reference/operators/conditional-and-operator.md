---
title: '&amp;&amp; Operator - C# odwołania'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 82442f50275f21e0a0748951dc50628a8d7e11bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243599"
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; Operator (odwołanie w C#)

Operator logiczny AND warunkowe `&&`, znany także jako "zwarcie" logicznego operatora AND, oblicza operator logiczny oraz z jego [bool](../keywords/bool.md) argumentów operacji. Wynik `x && y` jest `true` Jeśli oba `x` i `y` zwrócić `true`. W przeciwnym razie wynikiem jest `false`. Jeśli pierwszy operand ma wartość `false`, drugi operand nie jest oceniany i wynik operacji jest `false`. Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

[Logicznego operatora AND](and-operator.md) `&` oblicza również operator logiczny oraz z jego `bool` operandów, ale zawsze ocenia oba operandy.

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika nie można przeciążyć operator logiczny AND warunkowe. Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [operator logiczny oraz](and-operator.md) i [operatory true i false](../keywords/true-false-operators.md) w określony sposób, `&&` operacji mogą być obliczane w przypadku argumentów operacji typu. Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [warunkowego operatorów logicznych](~/_csharplang/spec/expressions.md#conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [|| operator](conditional-or-operator.md)
- [\! operator](logical-negation-operator.md)
- [& — operator](and-operator.md)
