---
title: '|| Operator - C# odwołania'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: 079c021eb68ece097c7f644416f1e9469a82dcea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415432"
---
# <a name="-operator-c-reference"></a>Operator || (odwołanie w C#)

Operator logiczny OR warunkowe `||`, znany także jako "zwarcie" logicznego operatora OR, oblicza logiczne OR z jego [bool](../keywords/bool.md) argumentów operacji. Wynik `x || y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`. W przeciwnym razie wynikiem jest `false`. Jeśli pierwszy operand ma wartość `true`, drugi operand nie jest oceniany i wynik operacji jest `true`. Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

[Operator logiczny OR](or-operator.md) `|` oblicza również logiczne OR z jego `bool` operandów, ale zawsze ocenia oba operandy.

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika nie można przeciążyć operator logiczny OR warunkowe. Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [logiczne OR](or-operator.md) i [operatory true i false](../keywords/true-false-operators.md) w określony sposób, `||` operacji mogą być obliczane w przypadku argumentów operacji typu. Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [warunkowego operatorów logicznych](~/_csharplang/spec/expressions.md#conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [& & — operator](conditional-and-operator.md)
- [\! Operator](logical-negation-operator.md)
- [| operator](or-operator.md)
