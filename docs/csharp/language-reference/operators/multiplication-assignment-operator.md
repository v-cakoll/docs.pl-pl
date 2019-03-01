---
title: '* = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967389"
---
# <a name="-operator-c-reference"></a>\*= — Operator (odwołanie w C#)

Operator przypisania mnożenia.

Usługi za pomocą wyrażenia `*=` operatora, takich jak

```csharp
x *= y
```

odpowiada wyrażeniu

```csharp
x = x * y
```

z tą różnicą, że `x` jest obliczany tylko raz.

Dla typów liczbowych [ \* operator](multiplication-operator.md) Oblicza iloczyn argumentów.

W poniższym przykładzie pokazano użycie `*=` operator:

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a>Overloadability — operator

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator mnożenia](multiplication-operator.md) `*`, operator przypisania mnożenia `*=` niejawnie jest przeciążony. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania mnożenia.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
