---
title: Operator || (odwołanie w C#)
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: a391078372e4ec0a3882bed4515733adedffb547
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "42925543"
---
# <a name="-operator-c-reference"></a>Operator || (odwołanie w C#)

Operator logiczny OR warunkowe `||`, znany także jako "zwarcie" logicznego operatora OR, oblicza logiczne OR z jego [bool](../keywords/bool.md) argumentów operacji. Wynik `x || y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`. W przeciwnym razie wynikiem jest `false`. Jeśli pierwszy operand ma wartość `true`, drugi operand nie jest oceniany i wynik operacji jest `true`. Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

[Operator logiczny OR](or-operator.md) `|` oblicza również logiczne OR z jego `bool` operandów, ale zawsze ocenia oba operandy.

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika nie można przeciążyć operator logiczny OR warunkowe. Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [logiczne OR](or-operator.md), [true](../keywords/true-operator.md), i [false](../keywords/false-operator.md) operatorów w określony sposób, `||` operacja może zostać obliczone dla Operandy typu. Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [warunkowego operatorów logicznych](~/_csharplang/spec/expressions.md#conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [& & — operator](conditional-and-operator.md)
- [! operator](logical-negation-operator.md)
- [| operator](or-operator.md)
