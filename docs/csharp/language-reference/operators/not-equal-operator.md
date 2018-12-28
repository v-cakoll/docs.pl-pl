---
title: '! = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610180"
---
# <a name="-operator-c-reference"></a>!= — Operator (odwołanie w C#)

Operator nierówności `!=` zwraca `true` argumentów nie są równe, `false` inaczej. Dla argumentów operacji [wbudowanych typów](../keywords/built-in-types-table.md), wyrażenie `x != y` daje ten sam wynik jako wyrażenie `!(x == y)`. Aby uzyskać więcej informacji, zobacz [== — Operator](equality-comparison-operator.md) artykułu.

W poniższym przykładzie pokazano użycie `!=` operator:

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `!=` operatora. Jeśli typem przeciążenia operator nierówności `!=`, należy także przeciążyć [operatora równości](equality-comparison-operator.md) `==`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Porównywanie równości](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
